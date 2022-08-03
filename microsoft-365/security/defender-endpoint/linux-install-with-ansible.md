---
title: توزيع Microsoft Defender لنقطة النهاية على Linux باستخدام Ansible
ms.reviewer: ''
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Ansible.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، linux، التثبيت، التوزيع، إلغاء التثبيت، الدمى، ansible، linux، redhat، ubuntu، debian، sles، suse، centos، fedora، amazon linux 2
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e35510960818472ccf82ffab0c3cb3016f49907a
ms.sourcegitcommit: d7193ee954c01c4172e228d25b941026c8d92d30
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/02/2022
ms.locfileid: "67175147"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-ansible"></a>توزيع Microsoft Defender لنقطة النهاية على Linux باستخدام Ansible

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

تصف هذه المقالة كيفية نشر Defender لنقطة النهاية على Linux باستخدام Ansible. يتطلب النشر الناجح إكمال كافة المهام التالية:

- [تنزيل حزمة الإلحاق](#download-the-onboarding-package)
- [إنشاء ملفات Ansible YAML](#create-ansible-yaml-files)
- [نشر](#deployment)
- [مراجع](#references)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع [Defender الرئيسي لنقطة النهاية على صفحة Linux للحصول على](microsoft-defender-endpoint-linux.md) وصف للمتطلبات الأساسية ومتطلبات النظام لإصدار البرنامج الحالي.

بالإضافة إلى ذلك، بالنسبة إلى نشر Ansible، يجب أن تكون على دراية بمهام إدارة Ansible، وأن يكون Ansible مكونا، وتعرف كيفية نشر أدلة المبادئ والمهام. يحتوي Ansible على العديد من الطرق لإكمال نفس المهمة. تفترض هذه التعليمات توفر وحدات Ansible المدعومة، مثل *apt* وغير *أرشفة* للمساعدة في نشر الحزمة. قد تستخدم مؤسستك سير عمل آخر. راجع [وثائق Ansible](https://docs.ansible.com/) للحصول على التفاصيل.

- يجب تثبيت Ansible على كمبيوتر واحد على الأقل (يستدعي Ansible عقدة التحكم هذه).
- يجب تكوين SSH لحساب مسؤول بين عقدة التحكم وجميع العقد المدارة (الأجهزة التي سيتم تثبيت Defender لنقطة النهاية عليها)، ويوصى بتكوينها باستخدام مصادقة المفتاح العام.
- يجب تثبيت البرنامج التالي على كافة العقد المدارة:
  - حليقه
  - python-apt

- يجب إدراج كافة العقد المدارة بالتنسيق التالي في `/etc/ansible/hosts` الملف أو الملف ذي الصلة:

    ```bash
    [servers]
    host1 ansible_ssh_host=10.171.134.39
    host2 ansible_ssh_host=51.143.50.51
    ```

- اختبار Ping:

    ```bash
    ansible -m ping all
    ```

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الإلحاق

قم بتنزيل حزمة الإلحاق من مدخل Microsoft 365 Defender:

1. في مدخل Microsoft 365 Defender، انتقل إلى **الإعدادات > نقاط النهاية > إدارة الأجهزة > الإلحاق**.
2. في القائمة المنسدلة الأولى، حدد **Linux Server** كنظام تشغيل. في القائمة المنسدلة الثانية، حدد **أداة إدارة تكوين Linux المفضلة** لديك كأسلوب توزيع.
3. حدد **تنزيل حزمة الإلحاق**. احفظ الملف WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="الخيار &quot;تنزيل حزمة الإلحاق&quot;" lightbox="images/portal-onboarding-linux-2.png":::

4. من موجه الأوامر، تحقق من أن لديك الملف. استخراج محتويات الأرشيف:

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-ansible-yaml-files"></a>إنشاء ملفات Ansible YAML

إنشاء مهمة فرعية أو ملفات أدوار تساهم في دليل المبادئ أو المهمة.

- إنشاء مهمة الإلحاق، `onboarding_setup.yml`:

    ```bash
    - name: Create MDATP directories
      file:
        path: /etc/opt/microsoft/mdatp/
        recurse: true
        state: directory
        mode: 0755
        owner: root
        group: root

    - name: Register mdatp_onboard.json
      stat:
        path: /etc/opt/microsoft/mdatp/mdatp_onboard.json
      register: mdatp_onboard

    - name: Extract WindowsDefenderATPOnboardingPackage.zip into /etc/opt/microsoft/mdatp
      unarchive:
        src: WindowsDefenderATPOnboardingPackage.zip
        dest: /etc/opt/microsoft/mdatp
        mode: 0600
        owner: root
        group: root
      when: not mdatp_onboard.stat.exists
    ```

- إضافة مستودع ومفتاح Defender لنقطة النهاية، `add_apt_repo.yml`:

    يمكن نشر Defender لنقطة النهاية على Linux من إحدى القنوات التالية (الموضح أدناه ب *[channel]*): *insider-fast* أو *insider-slow* أو *prod*. تتوافق كل قناة من هذه القنوات مع مستودع برامج Linux.

    يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك ومعدل تكرارها. الأجهزة في *insider-fast* هي أول الأجهزة التي تتلقى التحديثات والميزات الجديدة، متبوعة لاحقا *ببطء مشتركي Insider* وأخيرا بال *prod*.

    من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، يوصى بتكوين بعض الأجهزة في مؤسستك لاستخدام *مشتركي insider بسرعة* أو *بطيء من الداخل*.

    > [!WARNING]
    > يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم بإلغاء تثبيت الحزمة الموجودة، وأعد تكوين جهازك لاستخدام القناة الجديدة، واتبع الخطوات الواردة في هذا المستند لتثبيت الحزمة من الموقع الجديد.

    لاحظ التوزيع والإصدار الخاصين بك وحدد أقرب إدخال له ضمن `https://packages.microsoft.com/config/[distro]/`.

    في الأوامر التالية، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها.

    > [!NOTE]
    > في حالة Oracle Linux وAmazon Linux 2، استبدل *[distro]* ب "rhel". بالنسبة إلى Amazon Linux 2، استبدل *[version]* ب "7". بالنسبة لاستخدام Oracle، استبدل *[version]* بإصدار Oracle Linux.

  ```bash
  - name: Add Microsoft APT key
    apt_key:
      url: https://packages.microsoft.com/keys/microsoft.asc
      state: present
    when: ansible_os_family == "Debian"

  - name: Add Microsoft apt repository for MDATP
    apt_repository:
      repo: deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/[distro]/[version]/prod [codename] main
      update_cache: yes
      state: present
      filename: microsoft-[channel]
    when: ansible_os_family == "Debian"

  - name: Add Microsoft DNF/YUM key
    rpm_key:
      state: present
      key: https://packages.microsoft.com/keys/microsoft.asc
    when: ansible_os_family == "RedHat"

  - name: Add  Microsoft yum repository for MDATP
    yum_repository:
      name: packages-microsoft-[channel]
      description: Microsoft Defender for Endpoint
      file: microsoft-[channel]
      baseurl: https://packages.microsoft.com/[distro]/[version]/[channel]/ 
      gpgcheck: yes
      enabled: Yes
    when: ansible_os_family == "RedHat"
  ```

- إنشاء تثبيت Ansible وإلغاء تثبيت ملفات YAML.

    - بالنسبة للتوزيعات المستندة إلى apt، استخدم ملف YAML التالي:

        ```bash
        cat install_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_apt_repo.yml
            - name: Install MDATP
              apt:
                name: mdatp
                state: latest
                update_cache: yes
        ```

        ```bash
        cat uninstall_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              apt:
                name: mdatp
                state: absent
        ```

    - بالنسبة إلى التوزيعات المستندة إلى dnf، استخدم ملف YAML التالي:

        ```bash
        cat install_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_yum_repo.yml
            - name: Install MDATP
              dnf:
                name: mdatp
                state: latest
                enablerepo: packages-microsoft-[channel]
        ```

        ```bash
        cat uninstall_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              dnf:
                name: mdatp
                state: absent
        ```

## <a name="deployment"></a>نشر

الآن قم بتشغيل ملفات المهام ضمن `/etc/ansible/playbooks/` أو الدليل ذي الصلة.

- تركيب:

    ```bash
    ansible-playbook /etc/ansible/playbooks/install_mdatp.yml -i /etc/ansible/hosts
    ```

> [!IMPORTANT]
> عندما يبدأ المنتج لأول مرة، فإنه يقوم بتنزيل أحدث تعريفات مكافحة البرامج الضارة. اعتمادا على اتصالك بالإنترنت، قد يستغرق ذلك بضع دقائق.

- التحقق من الصحة/التكوين:

    ```bash
    ansible -m shell -a 'mdatp connectivity test' all
    ```
    ```bash
    ansible -m shell -a 'mdatp health' all
    ```

- إلغاء التثبيت:

    ```bash
    ansible-playbook /etc/ansible/playbooks/uninstall_mdatp.yml -i /etc/ansible/hosts
    ```

## <a name="log-installation-issues"></a>مشاكل تثبيت السجل

راجع [مشاكل تثبيت السجل](linux-resources.md#log-installation-issues) للحصول على مزيد من المعلومات حول كيفية العثور على السجل الذي تم إنشاؤه تلقائيا بواسطة المثبت عند حدوث خطأ.

## <a name="operating-system-upgrades"></a>ترقيات نظام التشغيل

عند ترقية نظام التشغيل إلى إصدار رئيسي جديد، يجب أولا إلغاء تثبيت Defender لنقطة النهاية على Linux، وتثبيت الترقية، وأخيرا إعادة تكوين Defender لنقطة النهاية على Linux على جهازك.

## <a name="references"></a>مراجع

- [إضافة مستودعات YUM أو إزالتها](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/yum_repository_module.html)

- [إدارة الحزم باستخدام مدير حزم dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)

- [إضافة مستودعات APT وإزالتها](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_repository_module.html)

- [إدارة حزم apt](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)

## <a name="see-also"></a>راجع أيضًا
- [التحقق من مشاكل صحة الوكيل](health-status.md)
