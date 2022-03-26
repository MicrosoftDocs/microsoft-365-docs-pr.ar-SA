---
title: نشر Microsoft Defender لنقطة النهاية على Linux مع "مهى"
ms.reviewer: ''
description: تصف هذه المقالة كيفية نشر Microsoft Defender ل Endpoint على Linux باستخدام "مهى".
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، التثبيت، النشر، إزالة التثبيت، الملل، غير مقبول، linux، redhat، ubuntu، debian، sles، suse، centos، fedora، amazon linux 2
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
ms.openlocfilehash: 305dd74d31f3cbbf07db23f8de89b2b57fe52326
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63571524"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>نشر Microsoft Defender لنقطة النهاية على Linux مع "مهى"

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

تصف هذه المقالة كيفية نشر Defender for Endpoint على Linux باستخدام "مهى". يتطلب النشر الناجح إكمال كل المهام التالية:

- [تنزيل حزمة الboarding](#download-the-onboarding-package)
- [إنشاء بيان "مهين"](#create-a-puppet-manifest)
- [النشر](#deployment)
- [التحقق من حالة الboarding](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

 للحصول على وصف للمتطلبات الأساسية ومتطلبات النظام الخاصة بالإصدار الحالي للبرنامج، راجع صفحة [Defender الرئيسية ل Endpoint على Linux](microsoft-defender-endpoint-linux.md).

بالإضافة إلى ذلك، بالنسبة إلى نشر "نشر النشر"، يجب أن تكون على دراية بمهام إدارة "النشر"، وأن تكون "نشرة" قد تم تكوينها، وأن تعرف كيفية نشر الحزم. تكثر طرق إكمال المهمة نفسها من خلال العملية العملية. تفترض هذه الإرشادات توفر الوحدات النمطية المدعمة "للدماء"، مثل *apt* للمساعدة في نشر الحزمة. قد تستخدم مؤسستك سير عمل مختلفا. راجع وثائق ["مهى"](https://puppet.com/docs) للحصول على التفاصيل.

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الboarding

قم بتنزيل حزمة المحتوى من مدخل Microsoft 365 Defender:

1. في Microsoft 365 Defender، انتقل إلى الإعدادات > نقاط النهاية > **إدارة الأجهزة > التكوين**.
2. في القائمة المنسدلة الأولى، حدد **Linux Server** كنمع التشغيل. في القائمة المنسدلة الثانية، حدد **أداة إدارة تكوين Linux المفضلة** لديك كطريقة نشر.
3. حدد **تنزيل حزمة التكهيل**. احفظ الملف WindowsDefenderATPOnboardingPackage.zip.

    ![Microsoft 365 Defender شاشة المدخل.](images/portal-onboarding-linux-2.png)

4. من موجه الأوامر، تحقق من أن لديك الملف. 

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
5. استخراج محتويات الأرشيف.
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>إنشاء بيان "مهى"

أنت بحاجة إلى إنشاء بيان "مخدم" لنشر Defender for Endpoint على Linux على الأجهزة المدارة بواسطة خادم "مخدم". يستخدم هذا المثال *الوحدات النمطية ل apt* *وyumrepo* المتوفرة منlabs، ويفترض أن الوحدات النمطية قد تم تثبيتها على خادم "المخدم".

قم بإنشاء المجلدات install_mdatp */الملفات* *install_mdatp/البيانات* ضمن مجلد الوحدات النمطية من تثبيت "نواة". يقع هذا المجلد عادة في */etc/environmentslabs/code/environments/production/modules* على خادم "المخدم". انسخ mdatp_onboard.json التي تم إنشاؤها أعلاه إلى *install_mdatp/الملفات* . إنشاء *init.pp* الملف الذي يحتوي على إرشادات النشر:

```bash
pwd
```
```Output
/etc/puppetlabs/code/environments/production/modules
```

```bash
tree install_mdatp
```
```Output
install_mdatp
├── files
│   └── mdatp_onboard.json
└── manifests
    └── init.pp
```

### <a name="contents-of-install_mdatpmanifestsinitpp"></a>محتويات `install_mdatp/manifests/init.pp`

يمكن نشر Defender for Endpoint على Linux من إحدى القنوات التالية (المشار إلى ذلك أدناه ب *[قناة]*): *insiders-fast* أو *insiders-slow* أو *prod*. تتوافق كل قناة من هذه القنوات مع مستودع برامج Linux.

يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك وتكرارها. الأجهزة في *insiders-fast* هي الأجهزة الأولى التي تتلقى التحديثات والميزات الجديدة، يليها *لاحقا insiders-slow* وأخيرا ب *prod*.

من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، من المستحسن تكوين بعض الأجهزة في المؤسسة لاستخدام *insiders-fast* أو *insiders-slow*.

> [!WARNING]
> يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم ب إلغاء تثبيت الحزمة الموجودة، ثم إعادة تكوين الجهاز لاستخدام القناة الجديدة، واتبع الخطوات الموجودة في هذا المستند لتثبيت الحزمة من الموقع الجديد.

لاحظ التوزيع والإصدار الخاص بك وحدد أقرب إدخال له ضمن `https://packages.microsoft.com/config/[distro]/`.

في الأوامر أدناه، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها:

> [!NOTE]
> في حالة RedHat و Oracle Linux و Amazon Linux 2 و CentOS 8، استبدل *[distro]* ب 'rhel'.

```puppet
# Puppet manifest to install Microsoft Defender for Endpoint on Linux.
# @param channel The release channel based on your environment, insider-fast or prod.
# @param distro The Linux distribution in lowercase. In case of RedHat, Oracle Linux, Amazon Linux 2, and CentOS 8, the distro variable should be 'rhel'.
# @param version The Linux distribution release number, e.g. 7.4.

class install_mdatp (
$channel = 'insiders-fast',
$distro = undef,
$version = undef
){
    case $::osfamily {
        'Debian' : {
            apt::source { 'microsoftpackages' :
                location => "https://packages.microsoft.com/config/${distro}/${version}/prod",
                release  => $channel,
                repos    => 'main',
                key      => {
                    'id'     => 'BC528686B50D79E339D3721CEB3E94ADBE1229CF',
                    'server' => 'keyserver.ubuntu.com',
                },
            }
        }
        'RedHat' : {
            yumrepo { 'microsoftpackages' :
                baseurl  => "https://packages.microsoft.com/config/${distro}/${version}/${channel}",
                descr    => "packages-microsoft-com-prod-${channel}",
                enabled  => 1,
                gpgcheck => 1,
                gpgkey   => 'https://packages.microsoft.com/keys/microsoft.asc'
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }

    case $::osfamily {
        /(Debian|RedHat)/: {
            file { ['/etc/opt', '/etc/opt/microsoft', '/etc/opt/microsoft/mdatp']:
                ensure => directory,
                owner  => root,
                group  => root,
                mode   => '0755'
            }

            file { '/etc/opt/microsoft/mdatp/mdatp_onboard.json':
                source  => 'puppet:///modules/install_mdatp/mdatp_onboard.json',
                owner   => root,
                group   => root,
                mode    => '0600',
                require => File['/etc/opt/microsoft/mdatp']
            }

            package { 'mdatp':
                ensure  => 'installed',
                require => File['/etc/opt/microsoft/mdatp/mdatp_onboard.json']
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }
}
```

## <a name="deployment"></a>النشر

تضمين البيان أعلاه في موقعك.pp ملف:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```
```Output
node "default" {
    include install_mdatp
}
```

تقوم أجهزة الوكيل المسجلين بشكل دوري باستطلاع رأي Server وثبت ملفات تعريف ونهج تكوين جديدة بمجرد اكتشافها.

## <a name="monitor-puppet-deployment"></a>مراقبة نشر "نشر مهين"

على جهاز الوكيل، يمكنك أيضا التحقق من حالة التكميل عن طريق تشغيل:

```bash
mdatp health
```
```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **مرخص**: هذا الأمر يؤكد أن الجهاز مرتبط بمنظمتك.

- **orgId**: هذا هو معرف مؤسسة Defender for Endpoint.

## <a name="check-onboarding-status"></a>التحقق من حالة الboarding

يمكنك التحقق من أن الأجهزة تم تشغيلها بشكل صحيح عن طريق إنشاء برنامج نصي. على سبيل المثال، يتحقق البرنامج النصي التالي من الأجهزة التي تم تسجيلها للحصول على حالة الالتحاق:

```bash
mdatp health --field healthy
```

يطبع الأمر أعلاه `1` إذا كان المنتج في الحافظة وكان يعمل كما هو متوقع.

> [!IMPORTANT]
> عند بدء تشغيل المنتج للمرة الأولى، يتم تنزيل أحدث تعريفات مكافحة البرامج الضارة. قد يستغرق هذا الأمر بضع دقائق، وهذا يتوقف على اتصالك بالإنترنت. خلال هذه الفترة، يرجع الأمر أعلاه قيمة `0`.

إذا لم يكن المنتج سليما، فإن رمز الخروج (الذي يمكن `echo $?`التحقق منه) يشير إلى المشكلة:

- 1 إذا لم يتم تشغيل الجهاز بعد.
- 3 إذا كان الاتصال بالداهمة غير منشأ.

## <a name="log-installation-issues"></a>مشاكل تثبيت السجل

 لمزيد من المعلومات حول كيفية البحث عن السجل الذي تم إنشاؤه تلقائيا الذي تم إنشاؤه بواسطة المثبت عند حدوث خطأ، راجع [مشاكل تثبيت السجل](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>ترقيات نظام التشغيل

عند ترقية نظام التشغيل إلى إصدار رئيسي جديد، يجب أولا إلغاء تثبيت Defender ل Endpoint على Linux، وتثبيت الترقية، وأخيرا إعادة تكوين Defender ل Endpoint على Linux على جهازك.

## <a name="uninstallation"></a>إلغاء التثبيت

إنشاء وحدة *نمطية remove_mdatp* *مماثلة install_mdatp مع* المحتويات التالية في *init.pp* ملف:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
