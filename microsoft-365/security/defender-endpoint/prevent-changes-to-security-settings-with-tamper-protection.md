---
title: حماية إعدادات الأمان باستخدام الحماية من العبث
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: استخدم الحماية من العبث لمنع التطبيقات الضارة من تغيير إعدادات الأمان المهمة.
keywords: البرامج الضارة، والمدافع، ومكافحة الفيروسات، والحماية من العبث
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.technology: mde
ms.date: 04/07/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: bcdf933de412a8141f0abc208f06cc55609f12c5
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788931"
---
# <a name="protect-security-settings-with-tamper-protection"></a>حماية إعدادات الأمان باستخدام الحماية من العبث

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

تتوفر الحماية من العبث بالأجهزة التي تقوم بتشغيل أحد الإصدارات التالية من Windows:

- Windows 11
- Windows 11 Enterprise متعددة الجلسات 
- Windows 10
- Windows 10 Enterprise متعددة الجلسات
- Windows Server 2022
- Windows Server 2019
- Windows Server، الإصدار 1803 أو أحدث
- Windows Server 2016‏
- Windows Server 2012 R2

> [!NOTE]
> تتوفر الحماية من العبث في Windows Server 2012 R2 للأجهزة التي تم إلحاقها باستخدام حزمة الحلول الموحدة الحديثة. لمزيد من المعلومات، راجع [إلحاق خوادم Windows بخدمة Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/configure-server-endpoints).


## <a name="overview"></a>نظرة عامة

أثناء بعض أنواع الهجمات الإلكترونية، تحاول الجهات الفاعلة السيئة تعطيل ميزات الأمان، مثل الحماية من الفيروسات، على أجهزتك. ترغب الجهات الفاعلة السيئة في تعطيل ميزات الأمان الخاصة بك لتسهيل الوصول إلى بياناتك، أو لتثبيت البرامج الضارة، أو استغلال بياناتك وهويتك وأجهزتك بطريقة أخرى. تساعد الحماية من العبث بالبيانات على منع حدوث هذه الأنواع من الأشياء. مع الحماية من العبث، يتم منع التطبيقات الضارة من اتخاذ إجراءات مثل:

- تعطيل الحماية من الفيروسات والتهديدات
- تعطيل الحماية في الوقت الحقيقي
- إيقاف تشغيل مراقبة السلوك
- تعطيل برنامج مكافحة الفيروسات (مثل IOfficeAntivirus (IOAV))
- تعطيل الحماية المقدمة من السحابة
- إزالة تحديثات التحليل الذكي للأمان
- تعطيل الإجراءات التلقائية على التهديدات المكتشفة

### <a name="how-it-works"></a>كيفية عملها

تعمل الحماية من العبث بشكل أساسي على تأمين برنامج الحماية من الفيروسات من Microsoft Defender إلى قيمها الآمنة والافتراضية، وتمنع تغيير إعدادات الأمان من خلال التطبيقات والأساليب مثل:

- تكوين الإعدادات في "محرر السجل" على جهازك Windows
- تغيير الإعدادات من خلال أوامر PowerShell cmdlets
- تحرير إعدادات الأمان أو إزالتها من خلال نهج المجموعة

لا تمنعك الحماية من العبث بالبيانات من عرض إعدادات الأمان. ولا تؤثر الحماية من العبث في كيفية تسجيل تطبيقات مكافحة الفيروسات غير التابعة ل Microsoft في تطبيق أمن Windows. إذا كانت مؤسستك تستخدم Windows 10 Enterprise E5، فلن يتمكن المستخدمون الفرديون من تغيير إعداد الحماية من العبث؛ في هذه الحالات، تتم إدارة الحماية من العبث من قبل فريق الأمان.

### <a name="what-do-you-want-to-do"></a>ماذا تريد أن تفعل؟

|لتنفيذ هذه المهمة...|راجع هذا المقطع...|
|---|---|
|إدارة الحماية من العبث عبر المستأجر <p> استخدام مدخل Microsoft 365 Defender لتشغيل الحماية من العبث أو إيقاف تشغيلها|[إدارة الحماية من العبث بمؤسستك باستخدام Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|ضبط إعدادات الحماية من العبث في مؤسستك <p> استخدم Intune (إدارة نقاط النهاية من Microsoft) لتشغيل الحماية من العبث أو إيقاف تشغيلها. يمكنك تكوين الحماية من العبث ببعض المستخدمين أو كلهم باستخدام هذا الأسلوب.|[إدارة الحماية من العبث بمؤسستك باستخدام إدارة نقاط النهاية من Microsoft](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|تشغيل الحماية من العبث (أو إيقاف تشغيل) لمؤسستك باستخدام Configuration Manager|[إدارة الحماية من العبث بمؤسستك باستخدام إرفاق المستأجر مع Configuration Manager، الإصدار 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|تشغيل الحماية من العبث بجهاز فردي (أو إيقاف تشغيله)|[إدارة الحماية من العبث بالبيانات على جهاز فردي](#manage-tamper-protection-on-an-individual-device)|
|عرض تفاصيل حول محاولات العبث بالأجهزة|[عرض معلومات حول محاولات العبث](#view-information-about-tampering-attempts)|
|مراجعة توصيات الأمان|[مراجعة توصيات الأمان](#review-your-security-recommendations)|
|مراجعة قائمة الأسئلة المتداولة (الأسئلة المتداولة)|[استعراض الأسئلة المتداولة](#view-information-about-tampering-attempts)|

## <a name="potential-dependency-on-cloud-protection"></a>الاعتماد المحتمل على حماية السحابة  
  
اعتمادا على الأسلوب أو أداة الإدارة التي تستخدمها لتمكين الحماية من العبث، قد يكون هناك تبعية على [الحماية التي توفرها السحابة](cloud-protection-microsoft-defender-antivirus.md) ويشار إليها أيضا باسم حماية السحابة، أو خدمة الحماية المتقدمة من Microsoft (MAPS).

يوفر الجدول التالي تفاصيل حول الأساليب والأدوات والتبعيات.

| كيفية تمكين الحماية من العبث | الاعتماد على حماية السحابة |
|---|---|
|Microsoft Intune|لا|
|Microsoft Endpoint Configuration Manager مع إرفاق المستأجر|لا|
|مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))|نعم|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>إدارة الحماية من العبث بمؤسستك باستخدام مدخل Microsoft 365 Defender

يمكن تشغيل الحماية من العبث بالمستأجر أو إيقاف تشغيله باستخدام مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). فيما يلي بعض النقاط التي يجب وضعها في الاعتبار:

- حاليا، يتم تشغيل خيار إدارة الحماية من العبث في مدخل Microsoft 365 Defender بشكل افتراضي لعمليات النشر الجديدة. بالنسبة إلى عمليات النشر الحالية، تتوفر الحماية من العبث بالبيانات على أساس الاشتراك. للاشتراك، في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، اختر **الإعدادات** \> **Endpoints** **Advanced features** \> \> **Advanced Protection**.
- عند استخدام مدخل Microsoft 365 Defender لإدارة الحماية من العبث، لن تحتاج إلى استخدام Intune أو أسلوب إرفاق المستأجر.
- عند إدارة الحماية من العبث في مدخل Microsoft 365 Defender، يتم تطبيق الإعداد على نطاق المستأجر، مما يؤثر على جميع أجهزتك التي تعمل Windows 10، Windows 10 Enterprise جلسات متعددة، Windows 11، Windows 11 Enterprise  Windows Server 2012 R2 أو Windows Server 2016 أو Windows Server 2019 أو Windows Server 2022 متعددة الجلسات. لضبط الحماية من العبث (مثل الحماية من العبث ببعض الأجهزة ولكن مع إيقاف تشغيلها للآخرين)، استخدم [إما إدارة نقاط النهاية من Microsoft](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) أو [Configuration Manager مع إرفاق المستأجر](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006).
- إذا كانت لديك بيئة مختلطة، فإن إعدادات الحماية من العبث التي تم تكوينها في Intune لها الأسبقية على الإعدادات التي تم تكوينها في مدخل Microsoft 365 Defender.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>متطلبات إدارة الحماية من العبث في مدخل Microsoft 365 Defender

- يجب أن يكون لديك [الأذونات المناسبة المعينة](/microsoft-365/security/defender-endpoint/assign-portal-access) ، مثل المسؤول العام أو مسؤول الأمان أو عمليات الأمان.

- يجب أن تقوم أجهزة Windows بتشغيل أحد الإصدارات التالية من Windows:
  
  - Windows 11
  - Windows 11 Enterprise متعددة الجلسات 
  - Windows 10
  - Windows 10 Enterprise متعددة الجلسات
  - Windows Server 2022
  - Windows Server 2019
  - Windows Server، الإصدار 1803 أو أحدث
  - Windows Server 2016‏
  - Windows Server 2012 R2

لمزيد من المعلومات حول الإصدارات، راجع [Windows 10 معلومات الإصدار](/windows/release-health/release-information).

- يجب إلحاق أجهزتك [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/onboarding).
- يجب أن تستخدم أجهزتك إصدار `4.18.2010.7` النظام الأساسي لمكافحة البرامج الضارة (أو أعلى) وإصدار `1.1.17600.5` محرك مكافحة البرامج الضارة (أو أعلى). ([إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).)
- يجب تشغيل [الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md).

> [!NOTE]
> عند تمكين الحماية من العبث عبر مدخل Microsoft 365 Defender، تكون الحماية المقدمة من السحابة مطلوبة، بحيث يمكن التحكم في الحالة الممكنة للحماية من العبث.  
> بدءا من تحديث نوفمبر 2021 (إصدار `4.18.2111.5`النظام الأساسي)، إذا لم يتم تشغيل الحماية المقدمة من السحابة لجهاز ويتم تشغيل الحماية من العبث في مدخل Microsoft 365 Defender، فسيتم تشغيل الحماية المقدمة من السحابة تلقائيا لهذا الجهاز إلى جانب الحماية من العبث.   

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>تشغيل الحماية من العبث (أو إيقاف تشغيلها) في مدخل Microsoft 365 Defender

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="تشغيل الحماية من العبث في مدخل Microsoft 365 Defender" lightbox="../../media/mde-turn-tamperprotectionon.png":::

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. اختر **الإعدادات** \> **نقاط النهاية**.

3. انتقل إلى **الميزات المتقدمة** **العامة**\>، ثم قم بتشغيل الحماية من العبث.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>إدارة الحماية من العبث بمؤسستك باستخدام إدارة نقاط النهاية من Microsoft

إذا كانت مؤسستك تستخدم إدارة نقاط النهاية من Microsoft (MEM)، فيمكنك تشغيل (أو إيقاف تشغيل) الحماية من العبث بمؤسستك في مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). استخدم Intune عندما تريد ضبط إعدادات الحماية من العبث. على سبيل المثال، إذا كنت تريد تمكين الحماية من العبث في بعض الأجهزة، ولكن ليس كلها، فاستخدم Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>متطلبات إدارة الحماية من العبث في إدارة نقاط النهاية

- يجب إلحاق أجهزتك [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/onboarding).
- يجب أن يكون لديك [الأذونات المناسبة المعينة](/microsoft-365/security/defender-endpoint/assign-portal-access) ، مثل المسؤول العام أو مسؤول الأمان أو عمليات الأمان.
- تستخدم مؤسستك [إدارة نقاط النهاية من Microsoft لإدارة الأجهزة](/mem/endpoint-manager-getting-started). (إدارة نقاط النهاية من Microsoft (MEM) مطلوبة؛ يتم تضمين MEM في Microsoft 365 E3/E5، Enterprise Mobility + Security E3/E5، Microsoft 365 Business Premium، Microsoft 365 F1/F3، Microsoft 365  G3/G5 الحكومية، وتراخيص التعليم المقابلة.)
- يجب أن تكون أجهزة Windows قيد التشغيل Windows 11 أو Windows 10 [1709](/windows/release-health/status-windows-10-1709) أو [1803](/windows/release-health/status-windows-10-1803) أو [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) أو أحدث. (لمزيد من المعلومات حول الإصدارات، راجع [Windows 10 معلومات الإصدار](/windows/release-health/release-information).)
- يجب أن تستخدم الأمان Windows مع تحديث [معلومات الأمان](https://www.microsoft.com/wdsi/definitions) إلى الإصدار 1.287.60.0 (أو أعلى).
- يجب أن تستخدم أجهزتك إصدار النظام الأساسي 4.18.1906.3 (أو أعلى) وإصدار `1.1.15500.X` محرك مكافحة البرامج الضارة (أو أعلى). ([إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).)

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>تشغيل الحماية من العبث (أو إيقاف تشغيلها) في إدارة نقاط النهاية من Microsoft

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="تشغيل الحماية من العبث باستخدام Intune" lightbox="images/turnontamperprotectinmem.png":::

1. في [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى **Endpoint security** \> **Antivirus**، ثم اختر **+ Create Policy**.

   - في قائمة **النظام الأساسي**، حدد **Windows 10 والإي وقت لاحق**.
   - في قائمة **"ملف التعريف**"، حدد **تجربة أمن Windows**.

2. إنشاء ملف تعريف يتضمن الإعداد التالي:

    - **تمكين الحماية من العبث لمنع تعطيل Microsoft Defender: تمكين**

3. تعيين ملف التعريف إلى مجموعة واحدة أو أكثر.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>إدارة الحماية من العبث بمؤسستك باستخدام Configuration Manager، الإصدار 2006

إذا كنت تستخدم [الإصدار 2006 من Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006)، يمكنك إدارة إعدادات الحماية من العبث بالبيانات على Windows 10، Windows 10 Enterprise متعددة الجلسات، Windows 11، Windows 11 Enterprise متعددة الجلسات، Windows  Server 2012 R2 و Windows Server 2016 و Windows Server 2019 و Windows Server 2022 باستخدام أسلوب يسمى *إرفاق المستأجر*. يتيح لك إرفاق المستأجر مزامنة أجهزة Configuration Manager المحلية فقط في مركز إدارة إدارة نقاط النهاية من Microsoft، ثم تقديم نهج تكوين أمان نقطة النهاية إلى المجموعات المحلية & الأجهزة.

> [!NOTE]
> يمكن استخدام الإجراء لتوسيع الحماية من العبث بالأجهزة التي تعمل Windows 10، Windows 10 Enterprise متعددة الجلسات، Windows 11، Windows 11 Enterprise متعددة الجلسات، Windows Server 2019، Windows Server 2022. تأكد من مراجعة المتطلبات الأساسية والمعلومات الأخرى في الموارد المذكورة في هذا الإجراء. بالنسبة Windows Server 2012 R2 الذي يقوم بتشغيل [الإصدار 2203 من Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2203) للحل الحديث والموحد.

1. إعداد إرفاق المستأجر. لمعرفة المزيد، راجع [بدء الاستخدام: إنشاء نهج أمان نقطة النهاية ونشرها من مركز الإدارة](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. في [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى **Endpoint security** \> **Antivirus**، ثم اختر **+ Create Policy**.

   - في قائمة **النظام الأساسي**، حدد **Windows 10، Windows 11، وخادم Windows (ConfigMgr).**
   - في قائمة **"ملف التعريف"**، حدد **تجربة أمن Windows (معاينة).**

3. نشر النهج إلى مجموعة أجهزتك.

#### <a name="need-help-with-this-method"></a>هل تحتاج إلى مساعدة في هذا الأسلوب؟

راجع الموارد التالية:

- [الإعدادات لملف تعريف تجربة أمن Windows في Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [مدونة المجتمع التقني: الإعلان عن الحماية من العبث بالعملاء Configuration Manager Tenant Attach](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>إدارة الحماية من العبث بالبيانات على جهاز فردي

> [!NOTE]
> تحاول كتل الحماية من العبث بتعديل إعدادات برنامج الحماية من الفيروسات من Microsoft Defender من خلال السجل.
>
> للمساعدة في التأكد من أن الحماية من العبث لا تتداخل مع منتجات الأمان غير التابعة ل Microsoft أو البرامج النصية لتثبيت المؤسسة التي تعدل هذه الإعدادات، انتقل إلى **أمن Windows** وتحديث **معلومات الأمان** إلى الإصدار 1.287.60.0 أو الإصدارات الأحدث. (راجع [تحديثات معلومات الأمان](https://www.microsoft.com/wdsi/definitions).) بمجرد إجراء هذا التحديث، تستمر الحماية من العبث بحماية إعدادات التسجيل، وتحاول السجلات تعديلها دون إرجاع الأخطاء.

إذا كنت مستخدما منزليا، أو لم تكن خاضعا لإعدادات يديرها فريق أمان، يمكنك استخدام تطبيق أمن Windows لإدارة الحماية من العبث بالبيانات. يجب أن يكون لديك أذونات المسؤول المناسبة على جهازك لتغيير إعدادات الأمان، مثل الحماية من العبث بالبيانات.

إليك ما تراه في تطبيق أمن Windows:

:::image type="content" source="images/tamperprotectionturnedon.png" alt-text="تشغيل الحماية من العبث Windows 10 Home" lightbox="images/tamperprotectionturnedon.png":::

1. حدد **"ابدأ**"، وابدأ بكتابة *"الأمان*". في نتائج البحث، حدد **أمن Windows**.

2. حدد إعدادات الحماية \> من **الفيروسات & الفيروسات** **& التهديدات**.

3. تعيين **"الحماية من العبث"** إلى **"تشغيل** " أو **"إيقاف تشغيل**".

## <a name="are-you-using-windows-server-2012-r2-2016-or-windows-version-1709-1803-or-1809"></a>هل تستخدم Windows Server 2012 R2 أو 2016 أو Windows الإصدار 1709 أو 1803 أو 1809؟

إذا كنت تستخدم Windows Server 2012 R2 باستخدام الحل الموحد الحديث، Windows Server 2016 أو Windows 10 الإصدار 1709 أو 1803 أو [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019)، فلن ترى **الحماية من العبث** في تطبيق أمن Windows. بدلا من ذلك، يمكنك استخدام PowerShell لتحديد ما إذا كانت الحماية من العبث ممكنة.

على Windows Server 2016، لن يعكس تطبيق الإعدادات بدقة حالة الحماية في الوقت الحقيقي عند تمكين الحماية من العبث.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>استخدام PowerShell لتحديد ما إذا كانت الحماية من العبث والحماية في الوقت الحقيقي قيد التشغيل

1. افتح تطبيق Windows PowerShell.

2. استخدم [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell cmdlet.

3. في قائمة النتائج، ابحث عن `IsTamperProtected` أو `RealTimeProtectionEnabled`. (القيمة *الحقيقية* تعني تمكين الحماية من العبث.)

## <a name="view-information-about-tampering-attempts"></a>عرض معلومات حول محاولات العبث

تشير محاولات العبث عادة إلى هجمات إلكترونية أكبر. تحاول الجهات الفاعلة السيئة تغيير إعدادات الأمان كطريقة للاستمرار والبقاء دون الكشف. إذا كنت جزءا من فريق الأمان في مؤسستك، يمكنك عرض معلومات حول مثل هذه المحاولات، ثم اتخاذ الإجراءات المناسبة للتخفيف من التهديدات.

عند الكشف عن محاولة العبث، يتم رفع تنبيه في [مدخل Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/portal-overview) ([https://security.microsoft.com](https://security.microsoft.com)).

:::image type="content" source="images/tamperattemptalert.png" alt-text="مدخل Microsoft 365 Defender" lightbox="images/tamperattemptalert.png":::

باستخدام [قدرات التتبع الكشف عن تهديدات نقاط النهاية والرد عليها](overview-endpoint-detection-response.md) [والمتقدمة](advanced-hunting-overview.md) في Microsoft Defender لنقطة النهاية، يمكن لفريق عمليات الأمان التحقيق في مثل هذه المحاولات ومعالجتها.

## <a name="review-your-security-recommendations"></a>مراجعة توصيات الأمان

تتكامل الحماية من العبث مع قدرات [إدارة المخاطر & الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md) . تتضمن [توصيات الأمان](tvm-security-recommendation.md) التأكد من تشغيل الحماية من العبث. على سبيل المثال، يمكنك البحث عن *العبث.* في النتائج، يمكنك تحديد **"تشغيل الحماية من العبث"** لمعرفة المزيد وتشغيله.

:::image type="content" source="images/tamperprotectsecurityrecos.png" alt-text="تشغيل الحماية من العبث في مدخل مركز حماية Microsoft Defender" lightbox="images/tamperprotectsecurityrecos.png":::

لمعرفة المزيد حول إدارة الثغرات الأمنية & المخاطر، راجع [رؤى لوحة المعلومات - إدارة المخاطر والثغرات الأمنية](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>ما هي إصدارات Windows التي يمكنني تكوين الحماية من العبث بها؟

- Windows 11
- Windows 11 Enterprise متعددة الجلسات
- Windows 10 OS [1709](/windows/release-health/status-windows-10-1709) أو [1803](/windows/release-health/status-windows-10-1803) أو [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) أو أحدث مع [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint).
- Windows 10 Enterprise متعددة الجلسات
  
إذا كنت تستخدم Configuration Manager، الإصدار 2006، مع إرفاق المستأجر، يمكن توسيع الحماية من العبث بالإنترنت إلى Windows Server 2012 R2، Windows Server 2016، Windows Server 2019، Windows Server 2022. See [Tenant attach: Create and deploy endpoint security Antivirus policy from the admin center (preview)](/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>هل ستؤثر الحماية من العبث بتسجيل الحماية من الفيروسات غير من Microsoft في تطبيق أمن Windows؟

لا. ستستمر عروض الحماية من الفيروسات غير الخاصة ب Microsoft في التسجيل في تطبيق أمن Windows.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>ماذا يحدث إذا لم تكن برنامج الحماية من الفيروسات من Microsoft Defender نشطة على جهاز؟

سيتم تشغيل الأجهزة التي تم إلحاقها Microsoft Defender لنقطة النهاية برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل. في هذه الحالات، ستستمر الحماية من العبث في حماية الخدمة وميزاتها.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>كيف أعمل تشغيل الحماية من العبث أو إيقاف تشغيلها؟

إذا كنت مستخدما منزليا، فراجع [إدارة الحماية من العبث بالبيانات على جهاز فردي](#manage-tamper-protection-on-an-individual-device).

إذا كنت مؤسسة تستخدم [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint)، يجب أن تكون قادرا على إدارة الحماية من العبث في Intune على غرار كيفية إدارة ميزات حماية نقطة النهاية الأخرى. راجع المقاطع التالية من هذه المقالة:

- [إدارة الحماية من العبث باستخدام إدارة نقاط النهاية من Microsoft](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [إدارة الحماية من العبث باستخدام مدخل Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>كيف يؤثر تكوين الحماية من العبث في Intune على كيفية إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة؟

لا ينطبق نهج المجموعة على الحماية من العبث. يتم تجاهل التغييرات التي تم إجراؤها على إعدادات برنامج الحماية من الفيروسات من Microsoft Defender عند تشغيل الحماية من العبث.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>إذا استخدمنا Microsoft Intune لتكوين الحماية من العبث، فهل ينطبق ذلك على المؤسسة بأكملها فقط؟

لديك المرونة في تكوين الحماية من العبث بالبيانات باستخدام Intune. يمكنك استهداف مؤسستك بأكملها، أو تحديد أجهزة ومجموعات مستخدمين معينة.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>هل يمكنني تكوين الحماية من العبث باستخدام Microsoft Endpoint Configuration Manager؟

إذا كنت تستخدم إرفاق المستأجر، يمكنك استخدام Microsoft Endpoint Configuration Manager. راجع الموارد التالية:

- [إدارة الحماية من العبث بمؤسستك باستخدام Configuration Manager، الإصدار 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [مدونة المجتمع التقني: الإعلان عن الحماية من العبث بالعملاء Configuration Manager Tenant Attach](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>لدي تسجيل E3 Windows. هل يمكنني استخدام تكوين الحماية من العبث في Intune؟

حاليا، لا يتوفر تكوين الحماية من العبث في Intune إلا للعملاء الذين لديهم [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>ماذا يحدث إذا حاولت تغيير إعدادات Microsoft Defender لنقطة النهاية في Intune، Microsoft Endpoint Configuration Manager، Windows Management Instrumentation عند تمكين الحماية من العبث على جهاز؟

لن تتمكن من تغيير الميزات المحمية بواسطة الحماية من العبث؛ يتم تجاهل طلبات التغيير هذه.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>أنا عميل مؤسسة. هل يمكن للمسؤولين المحليين تغيير الحماية من العبث على أجهزتهم؟

لا. لا يمكن للمسؤولين المحليين تغيير إعدادات الحماية من العبث أو تعديلها.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>ماذا يحدث إذا كان جهازي مضمنا مع Microsoft Defender لنقطة النهاية ثم ينتقل إلى حالة خارج الطائرة؟

إذا تم إيقاف تشغيل جهاز من Microsoft Defender لنقطة النهاية، يتم تشغيل الحماية من العبث، وهي الحالة الافتراضية للأجهزة غير المدارة.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>إذا تغيرت حالة الحماية من العبث، هل يتم عرض التنبيهات في مدخل Microsoft 365 Defender؟

نعم. يظهر التنبيه في [https://security.microsoft.com](https://security.microsoft.com) إطار **التنبيهات**.

يمكن لفريق عمليات الأمان أيضا استخدام استعلامات التتبع، مثل المثال التالي:

`AlertInfo|where Title == "Tamper Protection bypass"`

[عرض معلومات حول محاولات العبث](#view-information-about-tampering-attempts).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [المساعدة في تأمين أجهزة الكمبيوتر Windows باستخدام Endpoint Protection Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [الحصول على نظرة عامة على Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint)
- [معاً بشكل أفضل: برنامج الحماية من الفيروسات من Microsoft Defender Microsoft Defender لنقطة النهاية](why-use-microsoft-defender-antivirus.md)
