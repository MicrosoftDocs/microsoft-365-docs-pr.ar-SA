---
title: نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Puppet
ms.reviewer: ''
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Puppet.
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
ms.openlocfilehash: 9fe38f8bec7ca99d9c1828126382c8f70a22fa3a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014575"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Puppet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

تصف هذه المقالة كيفية نشر Defender لنقطة النهاية على Linux باستخدام Puppet. يتطلب النشر الناجح إكمال كافة المهام التالية:

- [تنزيل حزمة الإلحاق](#download-the-onboarding-package)
- [إنشاء بيان Puppet](#create-a-puppet-manifest)
- [نشر](#deployment)
- [التحقق من حالة الإلحاق](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

 للحصول على وصف للمتطلبات الأساسية ومتطلبات النظام لإصدار البرنامج الحالي، راجع [Defender الرئيسي لنقطة النهاية على صفحة Linux](microsoft-defender-endpoint-linux.md).

بالإضافة إلى ذلك، لنشر Puppet، تحتاج إلى أن تكون على دراية بمهام إدارة Puppet، وأن تكون Puppet مكونة، وتعرف كيفية توزيع الحزم. يحتوي Puppet على العديد من الطرق لإكمال نفس المهمة. تفترض هذه التعليمات توفر وحدات Puppet المدعومة، مثل *apt* للمساعدة في نشر الحزمة. قد تستخدم مؤسستك سير عمل آخر. راجع [وثائق Puppet](https://puppet.com/docs) للحصول على التفاصيل.

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الإلحاق

قم بتنزيل حزمة الإلحاق من مدخل Microsoft 365 Defender:

1. في مدخل Microsoft 365 Defender، انتقل إلى **نقاط النهاية الإعدادات > > إدارة الأجهزة > الإلحاق**.
2. في القائمة المنسدلة الأولى، حدد **Linux Server** كنظام تشغيل. في القائمة المنسدلة الثانية، حدد **أداة إدارة تكوين Linux المفضلة** لديك كأسلوب توزيع.
3. حدد **تنزيل حزمة الإلحاق**. احفظ الملف WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="خيار تنزيل الحزمة التي تم إلحاقها" lightbox="images/portal-onboarding-linux-2.png":::

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

## <a name="create-a-puppet-manifest"></a>إنشاء بيان Puppet

تحتاج إلى إنشاء بيان Puppet لنشر Defender لنقطة النهاية على Linux إلى الأجهزة التي يديرها خادم Puppet. يستخدم هذا المثال الوحدات النمطية *apt* *وyumrepo* المتوفرة من puppetlabs، ويفترض أن الوحدات النمطية قد تم تثبيتها على خادم Puppet الخاص بك.

قم بإنشاء المجلدات *install_mdatp/الملفات* install_mdatp */manifests* ضمن مجلد الوحدات النمطية لتثبيت Puppet الخاص بك. يقع هذا المجلد عادة في */etc/puppetlabs/code/environments/production/modules* على خادم Puppet الخاص بك. انسخ ملف mdatp_onboard.json الذي تم إنشاؤه أعلاه إلى مجلد *install_mdatp/files* . إنشاء *init.pp* الملف الذي يحتوي على إرشادات النشر:

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

يمكن نشر Defender لنقطة النهاية على Linux من إحدى القنوات التالية (الموضح أدناه ب *[channel]*): *insider-fast* أو *insider-slow* أو *prod*. تتوافق كل قناة من هذه القنوات مع مستودع برامج Linux.

يحدد اختيار القناة نوع التحديثات التي يتم تقديمها لجهازك ومعدل تكرارها. الأجهزة في *insider-fast* هي أول الأجهزة التي تتلقى التحديثات والميزات الجديدة، متبوعة لاحقا *ببطء مشتركي Insider* وأخيرا بال *prod*.

من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، يوصى بتكوين بعض الأجهزة في مؤسستك لاستخدام *مشتركي insider بسرعة* أو *بطيء من الداخل*.

> [!WARNING]
> يتطلب تبديل القناة بعد التثبيت الأولي إعادة تثبيت المنتج. لتبديل قناة المنتج: قم بإلغاء تثبيت الحزمة الموجودة، وأعد تكوين جهازك لاستخدام القناة الجديدة، واتبع الخطوات الواردة في هذا المستند لتثبيت الحزمة من الموقع الجديد.

لاحظ التوزيع والإصدار الخاصين بك وحدد أقرب إدخال له ضمن `https://packages.microsoft.com/config/[distro]/`.

في الأوامر أدناه، استبدل *[distro]* و *[version]* بالمعلومات التي حددتها:

> [!NOTE]
> في حالة RedHat وOracle Linux وAmazon Linux 2 وCentOS 8، استبدل *[distro]* ب 'rhel'.

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
        $release = $channel ? {
        'prod' => $facts['os']['distro']['codename']
        default => $channel
        }
            apt::source { 'microsoftpackages' :
                location => "https://packages.microsoft.com/${distro}/${version}/prod",
                release  =>  $release,
                repos    => 'main',
                key      => {
                    'id'     => 'BC528686B50D79E339D3721CEB3E94ADBE1229CF',
                    'server' => 'keyserver.ubuntu.com',
                },
            }
        }
        'RedHat' : {
            yumrepo { 'microsoftpackages' :
                baseurl  => "https://packages.microsoft.com/${distro}/${version}/${channel}",
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

## <a name="deployment"></a>نشر

تضمين البيان أعلاه في site.pp ملف:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```

```Output
node "default" {
    include install_mdatp
}
```

تقوم أجهزة العامل المسجلة باستقصاءات خادم Puppet Server بشكل دوري وتثبيت ملفات تعريف ونهج تكوين جديدة بمجرد اكتشافها.

## <a name="monitor-puppet-deployment"></a>مراقبة توزيع Puppet

على جهاز العامل، يمكنك أيضا التحقق من حالة الإلحاق عن طريق تشغيل:

```bash
mdatp health
```

```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **مرخص**: هذا يؤكد أن الجهاز مرتبط بمؤسستك.

- **orgId**: هذا هو معرف مؤسسة Defender for Endpoint.

## <a name="check-onboarding-status"></a>التحقق من حالة الإلحاق

يمكنك التحقق من أن الأجهزة قد تم إلحاقها بشكل صحيح عن طريق إنشاء برنامج نصي. على سبيل المثال، يتحقق البرنامج النصي التالي من الأجهزة المسجلة للحصول على حالة الإلحاق:

```bash
mdatp health --field healthy
```

يطبع `1` الأمر أعلاه إذا تم إلحاق المنتج ويعمل كما هو متوقع.

> [!IMPORTANT]
> عندما يبدأ المنتج لأول مرة، فإنه يقوم بتنزيل أحدث تعريفات مكافحة البرامج الضارة. اعتمادا على اتصالك بالإنترنت، قد يستغرق ذلك بضع دقائق. خلال هذا الوقت، يقوم الأمر أعلاه بإرجاع قيمة .`0`

إذا لم يكن المنتج سليما، فإن رمز الخروج (الذي يمكن التحقق منه `echo $?`) يشير إلى المشكلة:

- 1 إذا لم يتم إلحاق الجهاز بعد.
- 3 إذا تعذر تأسيس الاتصال بالبرنامج الخفي.

## <a name="log-installation-issues"></a>مشاكل تثبيت السجل

 لمزيد من المعلومات حول كيفية العثور على السجل الذي تم إنشاؤه تلقائيا بواسطة المثبت عند حدوث خطأ، راجع [مشاكل تثبيت السجل](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>ترقيات نظام التشغيل

عند ترقية نظام التشغيل إلى إصدار رئيسي جديد، يجب أولا إلغاء تثبيت Defender لنقطة النهاية على Linux، وتثبيت الترقية، وأخيرا إعادة تكوين Defender لنقطة النهاية على Linux على جهازك.

## <a name="uninstallation"></a>الغاء التثبيت

إنشاء وحدة *نمطية remove_mdatp* مشابهة *install_mdatp* مع المحتويات التالية في *init.pp* ملف:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
