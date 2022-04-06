---
title: نشر Microsoft Defender لنقطة النهاية على Linux يدويا
ms.reviewer: ''
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Linux يدويا من سطر الأوامر.
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
ms.openlocfilehash: 4d66dad57fa7b045062a0300327b76030c33dfab
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468160"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>نشر Microsoft Defender لنقطة النهاية على Linux يدويا

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


تصف هذه المقالة كيفية نشر Microsoft Defender لنقطة النهاية على Linux يدويا. يتطلب النشر الناجح إكمال كل المهام التالية:

  - [المتطلبات الأساسية ومتطلبات النظام](#prerequisites-and-system-requirements)
  - [تكوين مستودع برامج Linux](#configure-the-linux-software-repository)
    - [RHEL والمتغيرات (CentOS و Fedora و Oracle Linux و Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES والمتغيرات](#sles-and-variants)
    - [أنظمة Ubuntu و Debian](#ubuntu-and-debian-systems)
  - [تثبيت التطبيق](#application-installation)
  - [تنزيل حزمة الboarding](#download-the-onboarding-package)
  - [تكوين العميل](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع Microsoft Defender لنقطة النهاية [على Linux](microsoft-defender-endpoint-linux.md) للحصول على وصف للمتطلبات الأساسية ومتطلبات النظام للإصدار الحالي للبرنامج.

> [!WARNING]
> تتطلب ترقية نظام التشغيل إلى إصدار رئيسي جديد بعد تثبيت المنتج إعادة تثبيت المنتج. تحتاج إلى إلغاء [](linux-resources.md#uninstall) تثبيت Defender for Endpoint الموجود على Linux، وترقية نظام التشغيل، ثم إعادة تكوين Defender ل Endpoint على Linux باتباع الخطوات أدناه.

## <a name="configure-the-linux-software-repository"></a>تكوين مستودع برامج Linux

يمكن نشر Defender for Endpoint على Linux من إحدى القنوات التالية (المشار إلى ذلك أدناه ب *[قناة]*): *insiders-fast* أو *insiders-slow* أو *prod*. تتوافق كل قناة من هذه القنوات مع مستودع برامج Linux. يتم توفير إرشادات لتكوين جهازك لاستخدام أحد هذه المستودعات أدناه.

يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك وتكرارها. الأجهزة في *insiders-fast* هي الأجهزة الأولى التي تتلقى التحديثات والميزات الجديدة، يليها *لاحقا insiders-slow* وأخيرا ب *prod*.

من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، من المستحسن تكوين بعض الأجهزة في المؤسسة لاستخدام *insiders-fast* أو *insiders-slow*.

> [!WARNING]
> يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم ب إلغاء تثبيت الحزمة الموجودة، ثم إعادة تكوين الجهاز لاستخدام القناة الجديدة، واتبع الخطوات الموجودة في هذا المستند لتثبيت الحزمة من الموقع الجديد.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL والمتغيرات (CentOS و Fedora و Oracle Linux و Amazon Linux 2)

- تثبيت `yum-utils` إذا لم يكن مثبتا بعد:

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > التوزيع والإصدار، وحدد أقرب إدخال (حسب الرئيسي، ثم ثانوي) له ضمن `https://packages.microsoft.com/config/rhel/`.

    استخدم الجدول التالي لمساعدتك على إرشادك في تحديد موقع الحزمة:

    <br>

    ****

    |إصدار & Distro|الحزمة|
    |---|---|
    |ل RHEL/Centos/Oracle 8.0-8.5|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |ل RHEL/Centos/Oracle 7.2-7.9 & Amazon Linux 2 |<https://packages.microsoft.com/config/rhel/7/[channel].repo>|
    |ل RHEL/Centos 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|
    |بالنسبة إلى Fedora 33|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |بالنسبة إلى Fedora 34|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    في الأوامر التالية، استبدل *[الإصدار]* و *[القناة]* بالمعلومات التي حددتها:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > استخدم الأمر hostnamectl لتحديد المعلومات ذات الصلة للنظام بما في ذلك الإصدار *[الإصدار]*.

    على سبيل المثال، إذا كنت تقوم بتشغيل CentOS 7 وتريد نشر Defender for Endpoint على Linux من *قناة prod* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    أو إذا كنت ترغب في استكشاف الميزات الجديدة على الأجهزة المحددة، فقد ترغب في نشر Microsoft Defender لنقطة النهاية Linux إلى *قناة insiders fast*:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- تثبيت المفتاح العام Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES والمتغيرات

> [!NOTE]
> التوزيع والإصدار، وحدد أقرب إدخال (حسب الرئيسي، ثم ثانوي) له ضمن `https://packages.microsoft.com/config/sles/`.

   في الأوامر التالية، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > استخدم الأمر SPident لتحديد المعلومات ذات الصلة للنظام بما في ذلك الإصدار *[الإصدار]*.

   على سبيل المثال، إذا كنت تقوم بتشغيل SLES 12 وترغب في نشر Microsoft Defender لنقطة النهاية على Linux من قناة *prod*:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- تثبيت المفتاح العام Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>أنظمة Ubuntu و Debian

- تثبيت `curl` إذا لم يكن مثبتا بعد:

    ```bash
    sudo apt-get install curl
    ```

- تثبيت `libplist-utils` إذا لم يكن مثبتا بعد:

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> التوزيع والإصدار، وحدد أقرب إدخال (حسب الرئيسي، ثم ثانوي) له ضمن `https://packages.microsoft.com/config/[distro]/`.

   في الأمر أدناه، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > استخدم الأمر hostnamectl لتحديد المعلومات ذات الصلة للنظام بما في ذلك الإصدار *[الإصدار]*.

   على سبيل المثال، إذا كنت تقوم بتشغيل Ubuntu 18.04 وترغب في نشر Microsoft Defender لنقطة النهاية على Linux من *قناة prod*:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- تثبيت تكوين المستودع:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    على سبيل المثال، إذا اخترت *قناة prod* :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- تثبيت الحزمة `gpg` إذا لم تكن مثبتة بالفعل:

    ```bash
    sudo apt-get install gpg
    ```

  إذا `gpg` لم يكن متوفرا، فثبت `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- تثبيت المفتاح العام Microsoft GPG:

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- ثبت برنامج تشغيل https إذا لم يكن موجودا بالفعل:

    ```bash
    sudo apt-get install apt-transport-https
    ```

- تحديث بيانات تعريف المستودع:

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>تثبيت التطبيق

- RHEL والمتغيرات (CentOS و Oracle Linux):

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > إذا كان لديك عدة مستودعات Microsoft تم تكوينها على جهازك، يمكنك أن تكون محددا بشأن المستودع الذي تريد تثبيت الحزمة منه. يوضح المثال التالي كيفية تثبيت الحزمة من `production` `insiders-fast` القناة إذا تم أيضا تكوين قناة المستودع على هذا الجهاز. قد يحدث هذا الوضع إذا كنت تستخدم منتجات Microsoft متعددة على جهازك. قد يختلف الاسم المستعار للمستودع عن الاسم المستعار للمستودع في المثال التالي، وذلك استنادا إلى توزيع الخادم والإصدار الذي تم إصداره منه.

    ```bash
    # list all repositories
    yum repolist
    ```

    ```Output
    ...
    packages-microsoft-com-prod               packages-microsoft-com-prod        316
    packages-microsoft-com-prod-insiders-fast packages-microsoft-com-prod-ins      2
    ...
    ```

    ```bash
    # install the package from the production repository
    sudo yum --enablerepo=packages-microsoft-com-prod install mdatp
    ```

- SLES والمتغيرات:

    ```bash
    sudo zypper install mdatp
    ```

    > [!NOTE]
    > إذا كان لديك عدة مستودعات Microsoft تم تكوينها على جهازك، يمكنك أن تكون محددا بشأن المستودع الذي تريد تثبيت الحزمة منه. يوضح المثال التالي كيفية تثبيت الحزمة من `production` `insiders-fast` القناة إذا تم أيضا تكوين قناة المستودع على هذا الجهاز. قد يحدث هذا الوضع إذا كنت تستخدم منتجات Microsoft متعددة على جهازك.

    ```bash
    zypper repos
    ```

    ```Output
    ...
    #  | Alias | Name | ...
    XX | packages-microsoft-com-insiders-fast | microsoft-insiders-fast | ...
    XX | packages-microsoft-com-prod | microsoft-prod | ...
    ...

    ```

    ```bash
    sudo zypper install packages-microsoft-com-prod:mdatp
    ```

- نظام Ubuntu و Debian:

    ```bash
    sudo apt-get install mdatp
    ```

    > [!NOTE]
    > إذا كان لديك عدة مستودعات Microsoft تم تكوينها على جهازك، يمكنك أن تكون محددا بشأن المستودع الذي تريد تثبيت الحزمة منه. يوضح المثال التالي كيفية تثبيت الحزمة من `production` `insiders-fast` القناة إذا تم أيضا تكوين قناة المستودع على هذا الجهاز. قد يحدث هذا الوضع إذا كنت تستخدم منتجات Microsoft متعددة على جهازك.

    ```bash
    cat /etc/apt/sources.list.d/*
    ```

    ```Output
    deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod insiders-fast main
    deb [arch=amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod bionic main
    ```

    ```bash
    sudo apt -t bionic install mdatp
    ```

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الboarding

قم بتنزيل حزمة التكهيل من Microsoft 365 Defender المدخل.

> [!IMPORTANT]
> إذا فاتتك هذه الخطوة، فإن أي أمر يتم تنفيذه سيعرض رسالة تحذير تشير إلى أن المنتج غير مرخص. كما يرجع `mdatp health` الأمر قيمة `false`.

1. في Microsoft 365 Defender، انتقل إلى الإعدادات > نقاط النهاية > إدارة الأجهزة > **التكوين**.
2. في القائمة المنسدلة الأولى، حدد **Linux Server** كنمع التشغيل. في القائمة المنسدلة الثانية، حدد **برنامج نصي محلي** كطريقة نشر.
3. حدد **تنزيل حزمة التكهيل**. احفظ الملف WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux.png" alt-text="تنزيل حزمة التكهيل في مدخل Microsoft 365 Defender" lightbox="images/portal-onboarding-linux.png":::

4. من موجه الأوامر، تحقق من أن لديك الملف، واستخرج محتويات الأرشيف:

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

## <a name="client-configuration"></a>تكوين العميل

1. انسخ MicrosoftDefenderATPOnboardingLinuxServer.py إلى الجهاز الهدف.

    > [!NOTE]
    > في البداية، لم يكن جهاز العميل مقترن بمنظمة وكانت السمة *orgId* فارغة.

    ```bash
    mdatp health --field org_id
    ```

2. تشغيل MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > لتشغيل هذا الأمر، يجب أن `python` `python3` يكون لديك أو مثبتة على الجهاز استنادا إلى disto والإصدار. إذا لزم الأمر، راجع [الإرشادات خطوة بخطوة لتثبيت Python على Linux](https://opensource.com/article/20/4/install-python-linux).
    
    إذا كنت تقوم بتشغيل 8.x أو Ubuntu 20.04 أو أعلى، ستحتاج إلى استخدام `python3`.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    بالنسبة للإصدارات والإصدارات المتبقية، ستحتاج إلى استخدام `python`.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. تحقق من أن الجهاز مقترن الآن بمنظمتك ويقرر معرف مؤسسة صالحا:

    ```bash
    mdatp health --field org_id
    ```

4. تحقق من حالة صحة المنتج عن طريق تشغيل الأمر التالي. قيمة مرجعة تشير `1` إلى أن المنتج يعمل كما هو متوقع:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > عند بدء تشغيل المنتج للمرة الأولى، يتم تنزيل أحدث تعريفات مكافحة البرامج الضارة. قد يستغرق ذلك ما يصل إلى بضع دقائق استنادا إلى اتصال الشبكة. خلال هذه الفترة، يرجع الأمر أعلاه قيمة `false`. يمكنك التحقق من حالة تحديث التعريف باستخدام الأمر التالي:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > تجدر الإشارة إلى أنك قد تحتاج أيضا إلى تكوين وكيل بعد إكمال التثبيت الأولي. راجع [تكوين Defender ل Endpoint على Linux لاكتشاف الوكيل الثابت: تكوين ما بعد التثبيت](linux-static-proxy-configuration.md#post-installation-configuration).

5. يمكنك تشغيل اختبار الكشف عن AV للتحقق من أن الجهاز مدرج بشكل صحيح ويبل ى الخدمة. تنفيذ الخطوات التالية على الجهاز المعين حديثا:

    - تأكد من تمكين الحماية في الوقت الحقيقي ( `1` تشير إلى ذلك نتيجة من تشغيل الأمر التالي):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      إذا لم يتم تمكينه، فنفذ الأمر التالي:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - افتح نافذة المحطة الطرفية ونفذ الأمر التالي:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - يجب أن يكون الملف معزولا بواسطة Defender for Endpoint على Linux. استخدم الأمر التالي لتضمين جميع التهديدات التي تم الكشف عنها:

        ```bash
        mdatp threat list
        ```

6. يمكنك تشغيل الكشف التلقائي والاستجابة على النقط النهائية الكشف عن البيانات ومحاكاة عملية الكشف للتحقق من أن الجهاز تم إعداد تقاريره إلى الخدمة بشكل صحيح. تنفيذ الخطوات التالية على الجهاز المعين حديثا:

    - تحقق من ظهور خادم Linux الملوح في Microsoft 365 Defender. إذا كان هذا هو أول إعداد للجهاز، فقد يستغرق ظهوره ما يصل إلى 20 دقيقة.

    - قم بتنزيل ملف [البرنامج النصي واستخراجه](https://aka.ms/LinuxDIY) إلى خادم Linux تم تثبيته وتشغيل الأمر التالي: `./mde_linux_edr_diy.sh`

    - بعد بضع دقائق، يجب رفع الكشف في Microsoft 365 Defender.

    - أطلع على تفاصيل التنبيه والميول الزمنية للجهاز، وانجز خطوات التحقيق النموذجية.

## <a name="installer-script"></a>البرنامج النصي "المثبت"

بدلا من ذلك، يمكنك استخدام برنامج نصي [bash](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) للمثبت التلقائي تم [توفيره في مستودع GitHub العام](https://github.com/microsoft/mdatp-xplat/).
يحدد البرنامج النصي التوزيع والإصدار، ويبسط تحديد المستودع الصحيح، ويعد الجهاز لسحب الحزمة الأخيرة، ويجمع خطوات تثبيت المنتج والتركيب.

```bash
❯ ./mde_installer.sh --help
usage: basename ./mde_installer.sh [OPTIONS]
Options:
-c|--channel      specify the channel from which you want to install. Default: insiders-fast
-i|--install      install the product
-r|--remove       remove the product
-u|--upgrade      upgrade the existing product
-o|--onboard      onboard/offboard the product with <onboarding_script>
-p|--passive-mode set EPP to passive mode
-t|--tag          set a tag by declaring <name> and <value>. ex: -t GROUP Coders
-m|--min_req      enforce minimum requirements
-w|--clean        remove repo from package manager for a specific channel
-v|--version      print out script version
-h|--help         display help
```

اقرأ المزيد [هنا](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).

## <a name="log-installation-issues"></a>مشاكل تثبيت السجل

راجع [مشاكل تثبيت السجل](linux-resources.md#log-installation-issues) للحصول على مزيد من المعلومات حول كيفية العثور على السجل الذي تم إنشاؤه تلقائيا الذي أنشأه المثبت عند حدوث خطأ.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>كيفية الترحيل من Insiders-Fast إلى قناة الإنتاج

1. إلغاء تثبيت إصدار "قناة Insiders-Fast" من Defender for Endpoint على Linux.

    ```bash
    sudo yum remove mdatp
    ```

1. تعطيل Defender for Endpoint على Linux Insiders-Fast repo

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > يجب أن يظهر الإخراج "packages-microsoft-com-fast-prod".

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. إعادة نشر Microsoft Defender لنقطة النهاية على Linux باستخدام "قناة الإنتاج".

## <a name="uninstallation"></a>إلغاء التثبيت

راجع [إلغاء التثبيت للحصول](linux-resources.md#uninstall) على تفاصيل حول كيفية إزالة Defender for Endpoint على Linux من أجهزة العميل.

## <a name="see-also"></a>راجع أيضًا

- [التحقق من مشاكل صحة الوكيل](health-status.md)
