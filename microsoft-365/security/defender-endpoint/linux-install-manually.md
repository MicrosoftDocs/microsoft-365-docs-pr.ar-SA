---
title: نشر Microsoft Defender لنقطة النهاية على Linux يدويا
ms.reviewer: ''
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Linux يدويا من سطر الأوامر.
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
ms.openlocfilehash: a0f499a08288735d5f0d75e7111ec0b6360908a8
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664513"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>نشر Microsoft Defender لنقطة النهاية على Linux يدويا

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


تصف هذه المقالة كيفية نشر Microsoft Defender لنقطة النهاية على Linux يدويا. يتطلب النشر الناجح إكمال كافة المهام التالية:

  - [المتطلبات الأساسية ومتطلبات النظام](#prerequisites-and-system-requirements)
  - [تكوين مستودع برامج Linux](#configure-the-linux-software-repository)
    - [RHEL والمتغيرات (CentOS و Fedora وOracle Linux وAmazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES والمتغيرات](#sles-and-variants)
    - [أنظمة Ubuntu و Debian](#ubuntu-and-debian-systems)
  - [تثبيت التطبيق](#application-installation)
  - [تنزيل حزمة الإلحاق](#download-the-onboarding-package)
  - [تكوين العميل](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع [Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md) لوصف المتطلبات الأساسية ومتطلبات النظام لإصدار البرنامج الحالي.

> [!WARNING]
> تتطلب ترقية نظام التشغيل إلى إصدار رئيسي جديد بعد تثبيت المنتج إعادة تثبيت المنتج. تحتاج إلى [إلغاء تثبيت](linux-resources.md#uninstall) Defender لنقطة النهاية الموجودة على Linux، وترقية نظام التشغيل، ثم إعادة تكوين Defender لنقطة النهاية على Linux باتباع الخطوات أدناه.

## <a name="configure-the-linux-software-repository"></a>تكوين مستودع برامج Linux

يمكن نشر Defender لنقطة النهاية على Linux من إحدى القنوات التالية (الموضح أدناه ب *[channel]*): *insider-fast* أو *insider-slow* أو *prod*. تتوافق كل قناة من هذه القنوات مع مستودع برامج Linux. تتوفر أدناه إرشادات لتكوين جهازك لاستخدام أحد هذه المستودعات.

يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك ومعدل تكرارها. الأجهزة في *insider-fast* هي أول الأجهزة التي تتلقى التحديثات والميزات الجديدة، متبوعة لاحقا *ببطء مشتركي Insider* وأخيرا بال *prod*.

من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، يوصى بتكوين بعض الأجهزة في مؤسستك لاستخدام *مشتركي insider بسرعة* أو *بطيء من الداخل*.

> [!WARNING]
> يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم بإلغاء تثبيت الحزمة الموجودة، وأعد تكوين جهازك لاستخدام القناة الجديدة، واتبع الخطوات الواردة في هذا المستند لتثبيت الحزمة من الموقع الجديد.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL والمتغيرات (CentOS و Fedora وOracle Linux وAmazon Linux 2)

- قم بالتثبيت `yum-utils` إذا لم يتم تثبيته بعد:

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > التوزيع والإصدار الخاصين بك، وتحديد الإدخال الأقرب (حسب الرئيسي، ثم الثانوي) له ضمن `https://packages.microsoft.com/config/rhel/`.

    استخدم الجدول التالي لمساعدتك على إرشادك في تحديد موقع الحزمة:

    <br>

    ****

    |إصدار & Distro|حزمه|
    |---|---|
    |بالنسبة إلى RHEL/Centos/Oracle 8.0-8.5|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |ل RHEL/Centos/Oracle 7.2-7.9 & Amazon Linux 2 |<https://packages.microsoft.com/config/rhel/7/[channel].repo>|
    |بالنسبة إلى RHEL/Centos 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|
    |ل Fedora 33|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |ل Fedora 34|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    في الأوامر التالية، استبدل *[version]* و *[channel]* بالمعلومات التي حددتها:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > استخدم الأمر hostnamectl لتحديد المعلومات المتعلقة بالنظام بما في ذلك الإصدار *[version]*.

    على سبيل المثال، إذا كنت تقوم بتشغيل CentOS 7 وتريد نشر Defender لنقطة النهاية على Linux من قناة *prod* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    أو إذا كنت ترغب في استكشاف ميزات جديدة على الأجهزة المحددة، فقد ترغب في نشر Microsoft Defender لنقطة النهاية على Linux إلى قناة *insider-fast*:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- تثبيت المفتاح العام ل Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES والمتغيرات

> [!NOTE]
> التوزيع والإصدار الخاصين بك، وتحديد الإدخال الأقرب (حسب الرئيسي، ثم الثانوي) له ضمن `https://packages.microsoft.com/config/sles/`.

   في الأوامر التالية، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > استخدم أمر SPident لتحديد المعلومات ذات الصلة بالنظام بما في ذلك الإصدار *[version].*

   على سبيل المثال، إذا كنت تقوم بتشغيل SLES 12 وترغب في نشر Microsoft Defender لنقطة النهاية على Linux من قناة *prod*:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- تثبيت المفتاح العام ل Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>أنظمة Ubuntu و Debian

- قم بالتثبيت `curl` إذا لم يتم تثبيته بعد:

    ```bash
    sudo apt-get install curl
    ```

- قم بالتثبيت `libplist-utils` إذا لم يتم تثبيته بعد:

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> التوزيع والإصدار الخاصين بك، وتحديد الإدخال الأقرب (حسب الرئيسي، ثم الثانوي) له ضمن `https://packages.microsoft.com/config/[distro]/`.

   في الأمر أدناه، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > استخدم الأمر hostnamectl لتحديد المعلومات المتعلقة بالنظام بما في ذلك الإصدار *[version]*.

   على سبيل المثال، إذا كنت تقوم بتشغيل Ubuntu 18.04 وترغب في نشر Microsoft Defender لنقطة النهاية على Linux من قناة *prod*:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- تثبيت تكوين المستودع:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    على سبيل المثال، إذا اخترت قناة *prod* :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- `gpg` تثبيت الحزمة إذا لم تكن مثبتة بالفعل:

    ```bash
    sudo apt-get install gpg
    ```

  إذا `gpg` لم يكن متوفرا، فثبت `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- تثبيت المفتاح العام ل Microsoft GPG:

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- تثبيت برنامج تشغيل https إذا لم يكن موجودا بالفعل:

    ```bash
    sudo apt-get install apt-transport-https
    ```

- تحديث بيانات تعريف المستودع:

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>تثبيت التطبيق

- RHEL والمتغيرات (CentOS وOracle Linux):

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > إذا كان لديك عدة مستودعات Microsoft تم تكوينها على جهازك، يمكنك أن تكون محددا بشأن المستودع الذي تريد تثبيت الحزمة منه. يوضح المثال التالي كيفية تثبيت الحزمة من القناة `production` إذا كان لديك `insiders-fast` أيضا قناة المستودع التي تم تكوينها على هذا الجهاز. قد يحدث هذا الموقف إذا كنت تستخدم منتجات Microsoft متعددة على جهازك. استنادا إلى توزيع الخادم وإصداره، قد يختلف الاسم المستعار للمستودع عن الاسم المستعار الموجود في المثال التالي.

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
    > إذا كان لديك عدة مستودعات Microsoft تم تكوينها على جهازك، يمكنك أن تكون محددا بشأن المستودع الذي تريد تثبيت الحزمة منه. يوضح المثال التالي كيفية تثبيت الحزمة من القناة `production` إذا كان لديك `insiders-fast` أيضا قناة المستودع التي تم تكوينها على هذا الجهاز. قد يحدث هذا الموقف إذا كنت تستخدم منتجات Microsoft متعددة على جهازك.

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
    > إذا كان لديك عدة مستودعات Microsoft تم تكوينها على جهازك، يمكنك أن تكون محددا بشأن المستودع الذي تريد تثبيت الحزمة منه. يوضح المثال التالي كيفية تثبيت الحزمة من القناة `production` إذا كان لديك `insiders-fast` أيضا قناة المستودع التي تم تكوينها على هذا الجهاز. قد يحدث هذا الموقف إذا كنت تستخدم منتجات Microsoft متعددة على جهازك.

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

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الإلحاق

قم بتنزيل حزمة الإلحاق من مدخل Microsoft 365 Defender.

> [!IMPORTANT]
> إذا فاتتك هذه الخطوة، فسيعرض أي أمر تم تنفيذه رسالة تحذير تشير إلى أن المنتج غير مرخص. `mdatp health` يقوم الأمر أيضا بإرجاع قيمة .`false`

1. في مدخل Microsoft 365 Defender، انتقل إلى **نقاط النهاية الإعدادات > > إدارة الأجهزة > الإلحاق**.
2. في القائمة المنسدلة الأولى، حدد **Linux Server** كنظام تشغيل. في القائمة المنسدلة الثانية، حدد **البرنامج النصي المحلي** كأسلوب نشر.
3. حدد **تنزيل حزمة الإلحاق**. احفظ الملف WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux.png" alt-text="تنزيل حزمة إلحاق في مدخل Microsoft 365 Defender" lightbox="images/portal-onboarding-linux.png":::

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
    > في البداية جهاز العميل غير مقترن بمؤسسة وسمة *orgId* فارغة.

    ```bash
    mdatp health --field org_id
    ```

2. تشغيل MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > لتشغيل هذا الأمر، يجب أن يكون لديك `python`  أو `python3` مثبتا على الجهاز استنادا إلى disto والإصدار. إذا لزم الأمر، فراجع [التعليمات خطوة بخطوة لتثبيت Python على Linux](https://opensource.com/article/20/4/install-python-linux).
    
    إذا كنت تقوم بتشغيل RHEL 8.x أو Ubuntu 20.04 أو أعلى، فستحتاج إلى استخدام `python3`.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    بالنسبة لبقية الفرق والإصدارات، ستحتاج إلى استخدام `python`.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. تحقق من أن الجهاز مقترن الآن بمؤسستك ويبلغ عن معرف مؤسسة صالح:

    ```bash
    mdatp health --field org_id
    ```

4. تحقق من الحالة الصحية للمنتج عن طريق تشغيل الأمر التالي. تشير القيمة المرجعة إلى `1` أن المنتج يعمل كما هو متوقع:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > عندما يبدأ المنتج لأول مرة، فإنه يقوم بتنزيل أحدث تعريفات مكافحة البرامج الضارة. قد يستغرق ذلك بضع دقائق اعتمادا على اتصال الشبكة. خلال هذا الوقت، يقوم الأمر أعلاه بإرجاع قيمة .`false` يمكنك التحقق من حالة تحديث التعريف باستخدام الأمر التالي:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > يرجى ملاحظة أنك قد تحتاج أيضا إلى تكوين وكيل بعد إكمال التثبيت الأولي. راجع [تكوين Defender لنقطة النهاية على Linux لاكتشاف الوكيل الثابت: تكوين ما بعد التثبيت](linux-static-proxy-configuration.md#post-installation-configuration).

5. قم بتشغيل اختبار الكشف عن AV للتحقق من أن الجهاز تم إلحاقه بشكل صحيح وإعداد التقارير إلى الخدمة. نفذ الخطوات التالية على الجهاز الذي تم إلحاقه حديثا:

    - تأكد من تمكين الحماية في الوقت الحقيقي (يشار إليها بنتيجة `1` تشغيل الأمر التالي):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      إذا لم يتم تمكينه، فنفذ الأمر التالي:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - افتح نافذة Terminal ونفذ الأمر التالي:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - يجب عزل الملف بواسطة Defender لنقطة النهاية على Linux. استخدم الأمر التالي لإدراج كافة التهديدات المكتشفة:

        ```bash
        mdatp threat list
        ```

6. قم بتشغيل اختبار الكشف عن الكشف التلقائي والاستجابة على النقط النهائية ومحاكاة الكشف للتحقق من أن الجهاز تم إلحاقه بشكل صحيح وإعداد التقارير إلى الخدمة. نفذ الخطوات التالية على الجهاز الذي تم إلحاقه حديثا:

    - تحقق من ظهور خادم Linux الملحق في Microsoft 365 Defender. إذا كان هذا هو أول إلحاق للجهاز، فقد يستغرق الأمر ما يصل إلى 20 دقيقة حتى يظهر.

    - قم بتنزيل [ملف البرنامج النصي](https://aka.ms/LinuxDIY) واستخراجه إلى خادم Linux المضمن وتشغيل الأمر التالي: `./mde_linux_edr_diy.sh`

    - بعد بضع دقائق، يجب رفع الكشف في Microsoft 365 Defender.

    - انظر إلى تفاصيل التنبيه والمخطط الزمني للجهاز ونفذ خطوات التحقيق النموذجية.

## <a name="installer-script"></a>البرنامج النصي للمثبت

بدلا من ذلك، يمكنك استخدام [برنامج نصي bash للمثبت](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) التلقائي المتوفر في [مستودع GitHub العام](https://github.com/microsoft/mdatp-xplat/).
يحدد البرنامج النصي التوزيع والإصدار، ويبسط تحديد المستودع الصحيح، ويقوم بإعداد الجهاز لسحب أحدث حزمة، ويجمع بين خطوات تثبيت المنتج والإلحاق.

```bash
> ./mde_installer.sh --help
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

راجع [مشاكل تثبيت السجل](linux-resources.md#log-installation-issues) للحصول على مزيد من المعلومات حول كيفية العثور على السجل الذي تم إنشاؤه تلقائيا بواسطة المثبت عند حدوث خطأ.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>كيفية الترحيل من Insiders-Fast إلى قناة الإنتاج

1. إلغاء تثبيت إصدار "قناة Insider-Fast" من Defender لنقطة النهاية على Linux.

    ```bash
    sudo yum remove mdatp
    ```

1. تعطيل Defender لنقطة النهاية على مستودع Insiders-Fast Linux

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > يجب أن يظهر الإخراج "packages-microsoft-com-fast-prod".

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. إعادة نشر Microsoft Defender لنقطة النهاية على Linux باستخدام "قناة الإنتاج".

## <a name="uninstallation"></a>الغاء التثبيت

راجع [إلغاء التثبيت](linux-resources.md#uninstall) للحصول على تفاصيل حول كيفية إزالة Defender لنقطة النهاية على Linux من أجهزة العميل.

## <a name="see-also"></a>راجع أيضًا

- [التحقق من مشاكل صحة الوكيل](health-status.md)
