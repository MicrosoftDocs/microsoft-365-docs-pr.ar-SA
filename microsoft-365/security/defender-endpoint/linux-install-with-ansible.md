---
title: نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Ansible
ms.reviewer: ''
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Ansible.
keywords: microsoft, defender, Microsoft Defender لنقطة النهاية, linux, installation, deploy, deploy, uninstall,ible, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
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
ms.openlocfilehash: 57f0687fce422f26b76fc8b98a06ce0566f90f60
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476060"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-ansible"></a>نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Ansible

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

تصف هذه المقالة كيفية نشر Defender for Endpoint على Linux باستخدام Ansible. يتطلب النشر الناجح إكمال كل المهام التالية:

- [تنزيل حزمة الboarding](#download-the-onboarding-package)
- [إنشاء ملفات YAML غير قابلة للطي](#create-ansible-yaml-files)
- [النشر](#deployment)
- [المراجع](#references)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع الصفحة [الرئيسية Defender for Endpoint على Linux](microsoft-defender-endpoint-linux.md) للحصول على وصف للمتطلبات الأساسية ومتطلبات النظام الخاصة بالإصدار الحالي للبرنامج.

بالإضافة إلى ذلك، بالنسبة للنشر غير القابل للانتشار، يجب أن تكون على دراية بمهام الإدارة غير القابلة للطي، وأن تكون قابلا للتكوين، وأن تعرف كيفية نشر دفاتر التشغيل والمهام. يمكن الوصول إلى العديد من الطرق لإكمال المهمة نفسها. تفترض هذه الإرشادات توفر الوحدات النمطية القابلة للطي المعتمدة، مثل *apt* و *unarchive* للمساعدة في نشر الحزمة. قد تستخدم مؤسستك سير عمل مختلفا. راجع وثائق ["غير قابلة للطي"](https://docs.ansible.com/) للحصول على التفاصيل.

- يجب تثبيت Ansible على كمبيوتر واحد على الأقل (يسمي Ansible هذا العقدة عنصر التحكم).
- يجب تكوين SSH لحساب مسؤول بين عقدة التحكم وكل العقد المدارة (الأجهزة التي سيتم تثبيت Defender for Endpoint عليها)، ويوصى بتكوينها باستخدام مصادقة المفتاح العمومي.
- يجب تثبيت البرنامج التالي على كل العقد المدارة:
  - مجعد
  - python-apt

- يجب إدراج كل العقد المدارة في التنسيق التالي في `/etc/ansible/hosts` الملف أو الملف ذي الصلة:

    ```bash
    [servers]
    host1 ansible_ssh_host=10.171.134.39
    host2 ansible_ssh_host=51.143.50.51
    ```

- اختبار Ping:

    ```bash
    ansible -m ping all
    ```

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الboarding

قم بتنزيل حزمة المحتوى من مدخل Microsoft 365 Defender:

1. في Microsoft 365 Defender، انتقل إلى الإعدادات > نقاط النهاية > **إدارة الأجهزة > التكوين**.
2. في القائمة المنسدلة الأولى، حدد **Linux Server** كنمع التشغيل. في القائمة المنسدلة الثانية، حدد **أداة إدارة تكوين Linux المفضلة** لديك كطريقة نشر.
3. حدد **تنزيل حزمة التكهيل**. احفظ الملف WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="الخيار &quot;تنزيل حزمة التكهيل&quot;" lightbox="images/portal-onboarding-linux-2.png":::

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

## <a name="create-ansible-yaml-files"></a>إنشاء ملفات YAML غير قابلة للطي

إنشاء مهمة فرعية أو ملفات الدور التي تساهم في مصنف أو مهمة.

- إنشاء مهمة التهيئة، : `onboarding_setup.yml`

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

- أضف مستودع ومفتاح Defender لنقطة النهاية، `add_apt_repo.yml`:

    يمكن نشر Defender for Endpoint على Linux من إحدى القنوات التالية (المشار إلى ذلك أدناه ب *[قناة]*): *insiders-fast* أو *insiders-slow* أو *prod*. تتوافق كل قناة من هذه القنوات مع مستودع برامج Linux.

    يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك وتكرارها. الأجهزة في *insiders-fast* هي الأجهزة الأولى التي تتلقى التحديثات والميزات الجديدة، يليها *لاحقا insiders-slow* وأخيرا ب *prod*.

    من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، من المستحسن تكوين بعض الأجهزة في المؤسسة لاستخدام *insiders-fast* أو *insiders-slow*.

    > [!WARNING]
    > يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم ب إلغاء تثبيت الحزمة الموجودة، ثم إعادة تكوين الجهاز لاستخدام القناة الجديدة، واتبع الخطوات الموجودة في هذا المستند لتثبيت الحزمة من الموقع الجديد.

    لاحظ التوزيع والإصدار الخاص بك وحدد أقرب إدخال له ضمن `https://packages.microsoft.com/config/[distro]/`.

    في الأوامر التالية، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها.

    > [!NOTE]
    > في حالة Oracle Linux و Amazon Linux 2، استبدل *[distro]* ب "rhel".

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

- قم بإنشاء تثبيت غير قابل للطي و إلغاء تثبيت ملفات YAML.

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

    - بالنسبة للتوزيعات المستندة إلى dnf، استخدم ملف YAML التالي:

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

## <a name="deployment"></a>النشر

يمكنك الآن تشغيل ملفات المهام ضمن `/etc/ansible/playbooks/` الدليل ذي الصلة أو ضمنه.

- التثبيت:

    ```bash
    ansible-playbook /etc/ansible/playbooks/install_mdatp.yml -i /etc/ansible/hosts
    ```

> [!IMPORTANT]
> عند بدء تشغيل المنتج للمرة الأولى، يتم تنزيل أحدث تعريفات مكافحة البرامج الضارة. قد يستغرق هذا الأمر بضع دقائق، وهذا يتوقف على اتصالك بالإنترنت.

- التحقق من الصحة/التكوين:

    ```bash
    ansible -m shell -a 'mdatp connectivity test' all
    ```
    ```bash
    ansible -m shell -a 'mdatp health' all
    ```

- إزالة التثبيت:

    ```bash
    ansible-playbook /etc/ansible/playbooks/uninstall_mdatp.yml -i /etc/ansible/hosts
    ```

## <a name="log-installation-issues"></a>مشاكل تثبيت السجل

راجع [مشاكل تثبيت السجل](linux-resources.md#log-installation-issues) للحصول على مزيد من المعلومات حول كيفية العثور على السجل الذي تم إنشاؤه تلقائيا الذي أنشأه المثبت عند حدوث خطأ.

## <a name="operating-system-upgrades"></a>ترقيات نظام التشغيل

عند ترقية نظام التشغيل إلى إصدار رئيسي جديد، يجب أولا إلغاء تثبيت Defender ل Endpoint على Linux، وتثبيت الترقية، وأخيرا إعادة تكوين Defender ل Endpoint على Linux على جهازك.

## <a name="references"></a>المراجع

- [إضافة مستودعات YUM أو إزالتها](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/yum_repository_module.html)

- [إدارة الحزم باستخدام إدارة حزمة dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)

- [إضافة مستودعات APT وإزالتها](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_repository_module.html)

- [إدارة حزم apt](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)

## <a name="see-also"></a>راجع أيضًا
- [التحقق من مشاكل صحة الوكيل](health-status.md)
