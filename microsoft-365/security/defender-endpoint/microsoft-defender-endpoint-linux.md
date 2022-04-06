---
title: Microsoft Defender ل Endpoint على Linux
ms.reviewer: ''
description: يصف كيفية تثبيت Microsoft Defender ل Endpoint واستخدامه على Linux.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، التثبيت، النشر، إزالة التثبيت، المهى، قابل للأكل، linux، redhat، ubuntu، debian، sles، suse، centos
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 805f857a95fab03f8356c5162db1509122e7250a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680809"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender ل Endpoint على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يصف هذا الموضوع كيفية تثبيت Microsoft Defender لنقطة النهاية في Linux وتكوينه وتحديثه واستخدامه.

> [!CAUTION]
> من المرجح أن يؤدي تشغيل منتجات حماية نقاط نهاية أخرى من جهة خارجية إلى جانب Microsoft Defender for Endpoint على Linux إلى مشاكل في الأداء وتأثيرات جانبية غير متوقعة. إذا كانت الحماية من نقطة نهاية غير Microsoft من المتطلبات المطلقة في بيئتك، يمكنك مع ذلك الاستفادة من وظيفة Defender for Endpoint على Linux الكشف التلقائي والاستجابة على النقط النهائية بأمان بعد تكوين وظيفة الحماية من الفيروسات للتشغيل في الوضع "غير [النشط](linux-preferences.md#enforcement-level-for-antivirus-engine)".

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>كيفية تثبيت Microsoft Defender ل Endpoint على Linux

يتضمن Microsoft Defender ل Endpoint for Linux قدرات مكافحة البرامج الضارة الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية). 


### <a name="prerequisites"></a>المتطلبات الأساسية

- الوصول إلى مدخل Microsoft 365 Defender
- توزيع Linux باستخدام [إدارة](https://systemd.io/) النظام
- تجربة المستوى المبتدئ في البرمجة النصية ل Linux وBASH
- الامتيازات الإدارية على الجهاز (في حالة النشر اليدوي)

> [!NOTE]
> إن وكيل Microsoft Defender for Endpoint على Linux مستقل عن [وكيل OMS](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). يعتمد Microsoft Defender ل Endpoint على خط أنابيب بيانات التكليف المستقل الخاص به.


### <a name="installation-instructions"></a>إرشادات التثبيت

هناك العديد من الأساليب وأدوات النشر التي يمكنك استخدامها لتثبيت Microsoft Defender ل Endpoint وتكوينه على Linux.

بشكل عام، تحتاج إلى اتخاذ الخطوات التالية:

- تأكد من أن لديك اشتراك Microsoft Defender ل Endpoint.
- نشر Microsoft Defender ل Endpoint على Linux باستخدام إحدى أساليب النشر التالية:
  - أداة سطر الأوامر:
    - [النشر اليدوي](linux-install-manually.md)
  - أدوات الإدارة الخاصة ب جهة خارجية:
    - [النشر باستخدام أداة إدارة تكوين "النشر"](linux-install-with-puppet.md)
    - [النشر باستخدام أداة إدارة التكوين غير القابل للطي](linux-install-with-ansible.md)
    - [النشر باستخدام أداة إدارة تكوين Chef](linux-deploy-defender-for-endpoint-with-chef.md)

إذا واجهت أي حالات فشل في التثبيت، فجرب استكشاف مشاكل التثبيت وإصلاحها في [Microsoft Defender for Endpoint على Linux](linux-support-install.md).

> [!NOTE]
> لا يتم دعم تثبيت Microsoft Defender لنقطة النهاية في أي موقع آخر غير مسار التثبيت الافتراضي. 

### <a name="system-requirements"></a>متطلبات النظام

- توزيعات خوادم Linux المدعومة والإصدارات x64 (AMD64/EM64T):

  - Red Hat Enterprise Linux 6.7 أو أعلى
  - Red Hat Enterprise Linux 7.2 أو أعلى
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 أو أعلى 
  - CentOS 7.2 أو أعلى
  - Ubuntu 16.04 LTS أو LTS الأعلى
  - Debian 9 أو أعلى
  - SUSE Linux Enterprise Server 12 أو أعلى
  - Oracle Linux 7.2 أو أعلى
  - Oracle Linux 8.x
  - Amazon Linux 2
  - Fedora 33 أو أعلى

    > [!NOTE]
    > التوزيعات والإصدارات غير المدرجة بشكل صريح غير معتمدة (حتى لو كانت مشتقة من التوزيعات المعتمدة رسميا).

- قائمة إصدارات kernel المعتمدة
  - Red Hat Enterprise Linux 6 و CentOS 6:
    - ل 6.7: 2.6.32-573.*
    - ل 6.8: 2.6.32-642.*
    - ل 6.9: 2.6.32-696.*
    - ل 6.10: 2.6.32.754.2.1.el6.x86_64 إلى 2.6.32-754.41.2:
    
       - 2.6.32-754.10.1.el6.x86_64
       - 2.6.32-754.11.1.el6.x86_64
       - 2.6.32-754.12.1.el6.x86_64
       - 2.6.32-754.14.2.el6.x86_64
       - 2.6.32-754.15.3.el6.x86_64
       - 2.6.32-754.17.1.el6.x86_64
       - 2.6.32-754.18.2.el6.x86_64
       - 2.6.32-754.2.1.el6.x86_64
       - 2.6.32-754.22.1.el6.x86_64
       - 2.6.32-754.23.1.el6.x86_64
       - 2.6.32-754.24.2.el6.x86_64
       - 2.6.32-754.24.3.el6.x86_64
       - 2.6.32-754.25.1.el6.x86_64
       - 2.6.32-754.27.1.el6.x86_64
       - 2.6.32-754.28.1.el6.x86_64
       - 2.6.32-754.29.1.el6.x86_64
       - 2.6.32-754.29.2.el6.x86_64
       - 2.6.32-754.3.5.el6.x86_64
       - 2.6.32-754.30.2.el6.x86_64
       - 2.6.32-754.33.1.el6.x86_64
       - 2.6.32-754.35.1.el6.x86_64
       - 2.6.32-754.39.1.el6.x86_64
       - 2.6.32-754.41.2.el6.x86_64
       - 2.6.32-754.43.1.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64


    > [!NOTE]
    > بعد إصدار إصدار حزمة جديدة، يتم تقليل دعم الإصدارين السابقين إلى الدعم التقني فقط. يتم توفير الإصدارات الأقدم من تلك المدرجة في هذا القسم لدعم الترقية التقنية فقط.

  - بالنسبة لباقي التوزيعات المعتمدة، الحد الأدنى المطلوب من إصدار kernel هو 3.10.0-327

- آلية موفر الأحداث
  - Red Hat Enterprise Linux 6 و CentOS 6: `Talpa` حل مستند إلى وحدة kernel النمطية
  - بالنسبة لباقي التوزيعات المعتمدة: `Fanotify`
    - يجب `fanotify` تمكين خيار النواة

      > [!CAUTION]
      > إن تشغيل Defender ل Endpoint على Linux جنبا إلى جنب مع حلول `fanotify`الأمان المستندة إلى أخرى غير معتمد. يمكن أن يؤدي ذلك إلى نتائج غير متوقعة، بما في ذلك تعليق نظام التشغيل.

- مساحة القرص: 1 غيغابايت

- /opt/microsoft/mdatp/sbin/wdavdaemon يتطلب إذن قابل للتنفيذ. للحصول على مزيد من المعلومات، راجع "التأكد من أن daemon لديها إذن قابل للتنفيذ" في استكشاف مشاكل تثبيت [Microsoft Defender for Endpoint على Linux وإصلاحها](/microsoft-365/security/defender-endpoint/linux-support-install).

- Cores: 2 minimum, 4 المفضلة

- الذاكرة: 1 غيغابايت كحد أدنى، 4 مفضلة

    > [!NOTE]
    > الرجاء التأكد من أن لديك مساحة قرص مجانية في /var.

- يوفر الحل حاليا الحماية في الوقت الحقيقي لأنواع أنظمة الملفات التالية:

  - `btrfs`
  - `ecryptfs`
  - `ext2`
  - `ext3`
  - `ext4`
  - `fuse`
  - `fuseblk`
  - `jfs`
  - `nfs`
  - `overlay`
  - `ramfs`
  - `reiserfs`
  - `tmpfs`
  - `udf`
  - `vfat`
  - `xfs`

بعد تمكين الخدمة، قد تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح للاتصالات الصادرة بينها وبين نقاط النهاية.

- يجب تمكين إطار عمل التدقيق (`auditd`).

  > [!NOTE]
  > ستضيف أحداث النظام التي تم التقاطها بواسطة القواعد المضافة `/etc/audit/rules.d/` `audit.log`إلى (القواعد) وقد تؤثر على تدقيق المضيف ومجموعة عمليات التحويل إلى أعلى. سيتم وضع علامة على الأحداث التي تمت إضافتها بواسطة Microsoft Defender ل Endpoint على Linux باستخدام `mdatp` المفتاح.

### <a name="configuring-exclusions"></a>تكوين الاستثناءات

عند إضافة استثناءات إلى برنامج الحماية من الفيروسات من Microsoft Defender، يجب أن تنتبه إلى أخطاء الاستثناء [الشائعة برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>اتصالات الشبكة

يسرد جدول البيانات القابل للتنزيل التالي الخدمات وقوائم URL المقترنة بها التي يجب أن تتمكن شبكتك من الاتصال بها. يجب أن تضمن عدم وجود جدار حماية أو قواعد لتصفية الشبكة من شأنها رفض الوصول إلى عناوين URL هذه. إذا كان هناك، فقد تحتاج إلى إنشاء قاعدة *السماح* لهم بشكل خاص.

<br>

****


|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|قائمة URL ل Microsoft Defender لنقطة النهاية للعملاء التجاريين | جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| قائمة URL ل Microsoft Defender لنقطة النهاية لعملاء Gov/سحابة القطاع الحكومي/DoD| جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|


> [!NOTE]
> للحصول على قائمة URL أكثر تحديدا، راجع تكوين إعدادات اتصال الإنترنت [والوكيل](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

يمكن ل Defender for Endpoint اكتشاف خادم وكيل باستخدام أساليب الاكتشاف التالية:

- وكيل شفاف
- تكوين وكيل ثابت يدوي

إذا كان الوكيل أو جدار الحماية يمنع حركة مرور مجهولة، فتأكد من أن حركة المرور المجهولة مسموح بها في عناوين URL المدرجة سابقا. بالنسبة إلى المحترفين الشفافين، لا حاجة إلى تكوين إضافي ل Defender لنقطة النهاية. بالنسبة للوكيل الثابت، اتبع الخطوات في [تكوين الوكيل الثابت يدويا](linux-static-proxy-configuration.md).

> [!WARNING]
> PAC و WPAD و وكلاء المصادقة غير معتمدين. تأكد من استخدام وكيل ثابت أو وكيل شفاف فقط.
>
> كما أن فحص SSL وتكويلات التقاطع غير معتمدة أيضا لأسباب تتعلق بالأمن. قم بتكوين استثناء لفحص SSL وخادم الوكيل الخاص بك لتمرير البيانات مباشرة من Defender for Endpoint على Linux إلى عناوين URL ذات الصلة دون أي اعتراض. لن تسمح إضافة شهادة التقاطع إلى المتجر العام بالتقاطع.

للحصول على خطوات استكشاف الأخطاء وإصلاحها، راجع استكشاف مشاكل الاتصال السحابي وإصلاحها ل [Microsoft Defender ل Endpoint على Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>كيفية تحديث Microsoft Defender لنقطة النهاية على Linux

تنشر Microsoft تحديثات البرامج بشكل منتظم لتحسين الأداء والأمان وتقديم ميزات جديدة. لتحديث Microsoft Defender ل Endpoint على Linux، يمكنك الرجوع إلى [نشر تحديثات ل Microsoft Defender ل Endpoint على Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>كيفية تكوين Microsoft Defender ل Endpoint على Linux

تتوفر إرشادات حول كيفية تكوين المنتج في بيئات المؤسسات في تعيين التفضيلات ل [Microsoft Defender ل Endpoint على Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>يمكن أن تؤثر التطبيقات الشائعة ل Microsoft Defender لنقطة النهاية

يمكن أن تواجه أحمال العمل عالية I/O من تطبيقات معينة مشاكل في الأداء عند تثبيت Microsoft Defender ل Endpoint. وتتضمن هذه التطبيقات تطبيقات لسيناريوهات المطور مثل ينكنس وجيرا، وأحمال عمل قاعدة البيانات مثل OracleDB و Postgres. إذا كنت تواجه انخفاض الأداء، ف ضع في اعتبارك تعيين استثناءات للتطبيقات الموثوق بها، مع وضع أخطاء الاستثناء [الشائعة برنامج الحماية من الفيروسات من Microsoft Defender في الاعتبار](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus). للحصول على إرشادات إضافية، يجب التفكير في الوثائق الاستشارية المتعلقة باستثناءات الحماية من الفيروسات من تطبيقات  الأطراف الخارجية.

## <a name="resources"></a>الموارد

- لمزيد من المعلومات حول التسجيل أو إلغاء تثبيته أو مواضيع أخرى، راجع [الموارد](linux-resources.md).
