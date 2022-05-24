---
title: مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux
ms.reviewer: ''
description: يصف كيفية تثبيت Microsoft Defender لنقطة النهاية واستخدامها على Linux.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، linux، التثبيت، التوزيع، إلغاء التثبيت، الدمى، ansible، linux، redhat، ubuntu، debian، sles، suse، centos
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
ms.openlocfilehash: 825605f932b3732ba27af7ec95160f34959356b0
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648316"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يصف هذا الموضوع كيفية تثبيت Microsoft Defender لنقطة النهاية على Linux وتكوينها وتحديثها واستخدامها.

> [!CAUTION]
> من المحتمل أن يؤدي تشغيل منتجات حماية نقطة النهاية الأخرى إلى جانب Microsoft Defender لنقطة النهاية على Linux إلى مشاكل في الأداء وتأثيرات جانبية غير متوقعة. إذا كانت حماية نقطة النهاية غير التابعة ل Microsoft متطلبا مطلقا في بيئتك، فلا يزال بإمكانك الاستفادة بأمان من وظيفة Defender لنقطة النهاية على Linux الكشف التلقائي والاستجابة على النقط النهائية بعد تكوين وظيفة الحماية من الفيروسات للتشغيل في [الوضع السلبي](linux-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>كيفية تثبيت Microsoft Defender لنقطة النهاية على Linux

تتضمن Microsoft Defender لنقطة النهاية لنظام Linux قدرات مكافحة البرامج الضارة الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية). 


### <a name="prerequisites"></a>المتطلبات الأساسية

- الوصول إلى مدخل Microsoft 365 Defender
- توزيع Linux باستخدام [مدير النظام](https://systemd.io/)

  >[!NOTE]
  >يدعم توزيع Linux باستخدام مدير النظام، باستثناء RHEL/CentOS 6.x كلا من SystemV و Upstart.

- خبرة على مستوى المبتدئين في البرمجة النصية ل Linux و BASH
- الامتيازات الإدارية على الجهاز (في حالة النشر اليدوي)

> [!NOTE]
> Microsoft Defender لنقطة النهاية على عامل Linux مستقل عن [عامل OMS](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). يعتمد Microsoft Defender لنقطة النهاية على مسار بيانات تتبع الاستخدام المستقل الخاص به.


### <a name="installation-instructions"></a>إرشادات التثبيت

هناك العديد من الأساليب وأدوات النشر التي يمكنك استخدامها لتثبيت وتكوين Microsoft Defender لنقطة النهاية على Linux.

بشكل عام، تحتاج إلى اتخاذ الخطوات التالية:

- تأكد من أن لديك اشتراك Microsoft Defender لنقطة النهاية.
- نشر Microsoft Defender لنقطة النهاية على Linux باستخدام إحدى أساليب النشر التالية:
  - أداة سطر الأوامر:
    - [النشر اليدوي](linux-install-manually.md)
  - أدوات إدارة الجهات الخارجية:
    - [النشر باستخدام أداة إدارة تكوين Puppet](linux-install-with-puppet.md)
    - [النشر باستخدام أداة إدارة تكوين Ansible](linux-install-with-ansible.md)
    - [النشر باستخدام أداة إدارة تكوين Chef](linux-deploy-defender-for-endpoint-with-chef.md)

إذا واجهت أي فشل في التثبيت، فراجع [استكشاف أخطاء التثبيت وإصلاحها في Microsoft Defender لنقطة النهاية على Linux](linux-support-install.md).

> [!NOTE]
> لا يتم اعتماد تثبيت Microsoft Defender لنقطة النهاية في أي موقع آخر غير مسار التثبيت الافتراضي. 

### <a name="system-requirements"></a>متطلبات النظام

- توزيعات خادم Linux المدعومة وإصدارات x64 (AMD64/EM64T) x86_64:

  - Red Hat Enterprise Linux 6.7 أو أعلى
  - Red Hat Enterprise Linux 7.2 أو أعلى
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 أو أعلى 
  - CentOS 7.2 أو أعلى
  - Ubuntu 16.04 LTS أو LTS أعلى
  - Debian 9 أو أعلى
  - SUSE Linux Enterprise Server 12 أو أعلى
  - Oracle Linux 7.2 أو أعلى
  - Oracle Linux 8.x
  - Amazon Linux 2
  - Fedora 33 أو أعلى

    > [!NOTE]
    > التوزيعات والإصدارات غير المدرجة بشكل صريح غير معتمدة (حتى لو كانت مشتقة من التوزيعات المدعومة رسميا).

- قائمة بإصدارات النواة المدعومة
  - الحد الأدنى لإصدار kernel 3.10.0-327 (لجميع توزيعات Linux المدعومة المذكورة أعلاه باستثناء Red Hat Enterprise Linux 6 وCentOS 6)
  - `fanotify` يجب تمكين خيار النواة
  - Red Hat Enterprise Linux 6 وCentOS 6:
    - ل 6.7: 2.6.32-573.*
    - ل 6.8: 2.6.32-642.*
    - ل 6.9: 2.6.32-696.* (باستثناء 2.6.32-696.el6.x86_64)
    - بالنسبة إلى 6.10: 2.6.32.754.2.1.el6.x86_64 إلى 2.6.32-754.43.1:
    
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
       - 2.6.32-754.47.1.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64

 > [!NOTE]
 > بعد إصدار نسخة حزمة جديد، يتم تقليل الدعم للإصدارين السابقين إلى الدعم التقني فقط. يتم توفير الإصدارات الأقدم من تلك المذكورة في هذا القسم لدعم الترقية التقنية فقط.


  > [!CAUTION]
  > تشغيل Defender لنقطة النهاية على Linux جنبا إلى جنب مع حلول الأمان الأخرى `fanotify`المستندة إلى غير مدعوم. يمكن أن يؤدي إلى نتائج غير متوقعة، بما في ذلك تعليق نظام التشغيل.

- مساحة القرص: 1 غيغابايت

- /opt/microsoft/mdatp/sbin/wdavdaemon يتطلب إذنا قابلا للتنفيذ. لمزيد من المعلومات، راجع "التأكد من أن البرنامج الخفي لديه إذن قابل للتنفيذ" في [استكشاف مشكلات التثبيت وإصلاحها Microsoft Defender لنقطة النهاية على Linux](/microsoft-365/security/defender-endpoint/linux-support-install).

- الذاكرات الأساسية: 2 كحد أدنى، 4 مفضل

- الذاكرة: 1 غيغابايت كحد أدنى، 4 مفضل

    > [!NOTE]
    > يرجى التأكد من أن لديك مساحة حرة على القرص في /var.

- يوفر الحل حاليا حماية في الوقت الحقيقي لأنواع نظام الملفات التالية:

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

بعد تمكين الخدمة، قد تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح بالاتصالات الصادرة بينها وبين نقاط النهاية.

- يجب تمكين إطار عمل التدقيق (`auditd`).

  > [!NOTE]
  > ستتم إضافة `audit.log`أحداث النظام التي تم التقاطها بواسطة القواعد المضافة إلى `/etc/audit/rules.d/` (s) وقد تؤثر على تدقيق المضيف وجمع المصدر. سيتم وضع علامة على الأحداث التي تمت إضافتها بواسطة Microsoft Defender لنقطة النهاية على Linux باستخدام `mdatp` المفتاح.

### <a name="configuring-exclusions"></a>تكوين الاستثناءات

عند إضافة استثناءات إلى برنامج الحماية من الفيروسات من Microsoft Defender، يجب أن تكون على دراية [بأخطاء الاستبعاد الشائعة برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>اتصالات الشبكة

يسرد جدول البيانات التالي القابل للتنزيل الخدمات وعناوين URL المقترنة بها التي يجب أن تكون شبكتك قادرة على الاتصال بها. يجب التأكد من عدم وجود قواعد جدار حماية أو تصفية شبكة من شأنها رفض الوصول إلى عناوين URL هذه. إذا كان هناك، فقد تحتاج إلى إنشاء قاعدة *سماح* خاصة بها.

<br>

****

|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|Microsoft Defender لنقطة النهاية قائمة URL للعملاء التجاريين| جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender لنقطة النهاية قائمة URL ل Gov/سحابة القطاع الحكومي/DoD | جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

> [!NOTE]
> للحصول على قائمة URL أكثر تحديدا، راجع [تكوين إعدادات الاتصال بالإنترنت والوكيل](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

يمكن ل Defender لنقطة النهاية اكتشاف خادم وكيل باستخدام أساليب الاكتشاف التالية:

- وكيل شفاف
- تكوين وكيل ثابت يدوي

إذا كان وكيل أو جدار حماية يمنع حركة المرور المجهولة، فتأكد من السماح بنسبة استخدام الشبكة المجهولة في عناوين URL المدرجة مسبقا. بالنسبة للوكلاء الشفافين، لا توجد حاجة إلى تكوين إضافي ل Defender لنقطة النهاية. بالنسبة للوكيل الثابت، اتبع الخطوات الواردة في [تكوين الوكيل الثابت اليدوي](linux-static-proxy-configuration.md).

> [!WARNING]
> لا يتم دعم PAC وWPAD والوكلاء المصادق عليهم. تأكد من استخدام وكيل ثابت أو وكيل شفاف فقط.
>
> كما أن فحص SSL واعتراض الوكلاء غير مدعومين لأسباب أمنية. تكوين استثناء لفحص SSL والخادم الوكيل الخاص بك لتمرير البيانات مباشرة من Defender لنقطة النهاية على Linux إلى عناوين URL ذات الصلة دون اعتراض. لن تسمح إضافة شهادة اعتراضك إلى المتجر العمومي با اعتراضها.

للحصول على خطوات استكشاف الأخطاء وإصلاحها، راجع [استكشاف مشكلات الاتصال السحابي وإصلاحها Microsoft Defender لنقطة النهاية على Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>كيفية تحديث Microsoft Defender لنقطة النهاية على Linux

تنشر Microsoft تحديثات البرامج بانتظام لتحسين الأداء والأمان وتقديم ميزات جديدة. لتحديث Microsoft Defender لنقطة النهاية على Linux، راجع [نشر تحديثات Microsoft Defender لنقطة النهاية على Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>كيفية تكوين Microsoft Defender لنقطة النهاية على Linux

تتوفر إرشادات حول كيفية تكوين المنتج في بيئات المؤسسة في [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>يمكن أن تؤثر التطبيقات الشائعة Microsoft Defender لنقطة النهاية

يمكن أن تواجه أحمال عمل الإدخال/الإخراج العالية من تطبيقات معينة مشكلات في الأداء عند تثبيت Microsoft Defender لنقطة النهاية. وتشمل هذه التطبيقات لسيناريوهات المطور مثل Jenkins وJira، وأحمال عمل قاعدة البيانات مثل OracleDB وPostgres. إذا واجهت انخفاض الأداء، ففكر في تعيين استثناءات للتطبيقات الموثوق بها، مع وضع [أخطاء الاستبعاد الشائعة برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) في الاعتبار. للحصول على إرشادات إضافية، ضع في اعتبارك الوثائق الاستشارية المتعلقة باستثناءات الحماية من الفيروسات من تطبيقات الجهات الخارجية.

## <a name="resources"></a>الموارد

- لمزيد من المعلومات حول التسجيل أو إلغاء التثبيت أو مواضيع أخرى، راجع ["الموارد](linux-resources.md)".
