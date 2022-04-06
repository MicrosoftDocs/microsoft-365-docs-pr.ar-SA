---
title: الكشف عن نقطة النهاية والاستجابة لها في وضع الحظر
description: التعرف على الكشف عن تهديدات نقاط النهاية والرد عليها في وضع الحظر
keywords: Microsoft Defender لنقطة النهاية، mde، الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، حظر الوضع السلبي
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.date: 03/18/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 6e6bf499ab348d05cba237fa69b205cb495dccb0
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681051"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>الكشف عن نقطة النهاية والاستجابة (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>ما هو الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر؟

[يوفر الكشف](overview-endpoint-detection-response.md) عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر حماية إضافية من الأعمال الضارة عندما برنامج الحماية من الفيروسات من Microsoft Defender منتج الحماية من الفيروسات الأساسي وهو قيد التشغيل في الوضع غير النشط. الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر في الكواليس من أجل معالجة الأعمال الضارة التي تم اكتشافها بواسطة الكشف التلقائي والاستجابة على النقط النهائية أخرى. من المحتمل أن يكون منتج الحماية من الفيروسات الأساسي غير التابع ل Microsoft قد فات مثل هذه التحف. بالنسبة للأجهزة التي برنامج الحماية من الفيروسات من Microsoft Defender على أنها برنامج الحماية من الفيروسات الأساسي، يوفر الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر طبقة إضافية من الدفاع من خلال السماح برنامج الحماية من الفيروسات من Microsoft Defender إجراءات تلقائية حول عمليات الكشف السلوكية الكشف التلقائي والاستجابة على النقط النهائية الخرق.

> [!IMPORTANT]
> الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر كل الحماية المتوفرة عند برنامج الحماية من الفيروسات من Microsoft Defender في الوقت الحقيقي. لن تعمل كل الميزات التي تعتمد برنامج الحماية من الفيروسات من Microsoft Defender أن تكون حل الحماية من الفيروسات النشط، بما في ذلك الأمثلة الرئيسية التالية:
>
> - لا تتوفر الحماية في الوقت الحقيقي، بما في ذلك الفحص عند الوصول، عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. لمعرفة المزيد حول إعدادات نهج الحماية في الوقت الحقيقي، راجع تمكين برنامج الحماية من الفيروسات من Microsoft Defender **[الحماية دائما](configure-real-time-protection-microsoft-defender-antivirus.md)**.
>
> - لا تتوفر **[ميزات مثل](network-protection.md)** قواعد **[](attack-surface-reduction.md)** الحد من سطح الشبكة والحد من الهجمات إلا برنامج الحماية من الفيروسات من Microsoft Defender تشغيلها في الوضع النشط.
>
> من المتوقع أن يوفر حل الحماية من الفيروسات غير التابع ل Microsoft هذه الإمكانات.

الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر مع [المخاطر & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md). سيحصل فريق الأمان في مؤسستك على توصية أمان [](tvm-security-recommendation.md) الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر إذا لم يتم تمكينه بالفعل.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="توصية حول تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر.":::

> [!TIP]
> للحصول على أفضل حماية، تأكد من **[نشر Microsoft Defender لخط أساسيات نقطة النهاية](configure-machines-security-baseline.md)**.

## <a name="what-happens-when-something-is-detected"></a>ماذا يحدث عند اكتشاف شيء ما؟

عند الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، والكشف عن حركة ضارة، يمنع Microsoft Defender لنقطة النهاية هذه الأداة ويديرها. سيشاهد فريق عمليات الأمان حالة الكشف على أنها "تم **الحظر**" أو "[](respond-machine-alerts.md#check-activity-details-in-action-center)منع" في مركز الإجراءات، مدرجة ك إجراءات مكتملة.

تعرض الصورة التالية مثيلا للبرامج غير المرغوب فيها التي تم الكشف عنها الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر عن شيء ما.":::


## <a name="enable-edr-in-block-mode"></a>تمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر

> [!IMPORTANT]
> بدءا من إصدار النظام الأساسي 4.18.2202.X، يمكنك الآن تعيين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر لاستهداف مجموعات أجهزة معينة باستخدام Intune CSPs. يمكنك الاستمرار في تعيين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر على نطاق المستأجر في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل</a>. الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر بشكل أساسي للأجهزة التي تعمل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي (يتم تثبيت حل برنامج الحماية من الفيروسات غير Microsoft ونشط على الجهاز). 

> [!TIP]
> تأكد من [تلبية](#requirements-for-edr-in-block-mode) المتطلبات قبل تشغيل الكشف التلقائي والاستجابة على النقط النهائية وضع الحظر.

### <a name="security-portal"></a>مدخل الأمان 

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) ثم سجل الدخول.

2. اختر **الإعدادات** \> **نقاط النهاية** \> **العامة** \> **المتقدمة**.

3. قم بالتمرير لأسفل، ثم قم الكشف التلقائي والاستجابة على النقط النهائية **تمكين التنقل في وضع الحظر**.

### <a name="intune"></a>Intune

لإنشاء نهج مخصص في Intune، راجع نشر OMA-URIs لاستهداف [CSP من خلال Intune](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune)، ومقارنة مع الموقع

للحصول على مزيد من المعلومات حول Defender CSP المستخدم الكشف التلقائي والاستجابة على النقط النهائية وضع الحظر، راجع "تكوين/سلبية" ضمن [Defender CSP](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>متطلبات الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر

يسرد الجدول التالي متطلبات الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر:

|المتطلب|التفاصيل|
|---|---|
|الأذونات|يجب تعيين دور المسؤول العام أو مسؤول الأمان في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). لمزيد من المعلومات، راجع [الأذونات الأساسية](basic-permissions.md).|
|نظام التشغيل|يجب أن تعمل الأجهزة على أحد الإصدارات التالية من Windows: <br/>- Windows 11 <br/>- Windows 10 (كل الإصدارات)<br/>- Windows Server 2022 <br/>- Windows Server 2019<br/>- Windows Server أو الإصدار 1803 أو الأحدث<br/>- Windows Server 2016 Windows Server 2012 R2 (باستخدام حل العميل الموحد [الجديد](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview))<sup>[[1](#fn1)]</sup>  |
|Microsoft Defender لنقطة النهاية|يجب أن تكون الأجهزة مجهزه في Defender لنقطة النهاية. راجع المقالات التالية: <br/>- [الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية](minimum-requirements.md)<br/>- [الأجهزة المجهزة وتكوين قدرات نقطة النهاية ل Microsoft Defender](onboard-configure.md)<br/>- [إعادة Windows إلى خدمة Defender for Endpoint](configure-server-endpoints.md)<br/>- [وظائف Windows Server 2012 R2 و2016 الجديدة في الحل الموحد الحديث (معاينة)](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) |
|برنامج الحماية من الفيروسات من Microsoft Defender|يجب أن يكون برنامج الحماية من الفيروسات من Microsoft Defender الأجهزة مثبتة ومفعلة في الوضع النشط أو الوضع السلبي. [تأكد برنامج الحماية من الفيروسات من Microsoft Defender في وضع نشط أو غير نشط](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|الحماية التي يتم تسليمها من السحابة|برنامج الحماية من الفيروسات من Microsoft Defender تكوين مثل هذه الحماية التي يتم [تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md).|
|برنامج الحماية من الفيروسات من Microsoft Defender أساسي|يجب أن تكون الأجهزة م تاريخا. لتأكيد الأمر، باستخدام PowerShell، يمكنك تشغيل أمر cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) كمسؤول. في **السطر AMProductVersion** ، يجب أن ترى **4.18.2001.10** أو أعلى. <p> لمعرفة المزيد، [راجع إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).|
|برنامج الحماية من الفيروسات من Microsoft Defender جديد|يجب أن تكون الأجهزة م تاريخا. لتأكيد الأمر، باستخدام PowerShell، يمكنك تشغيل أمر cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) كمسؤول. في **السطر AMEngineVersion** ، يجب أن ترى **1.1.16700.2** أو أعلى. <p> لمعرفة المزيد، [راجع إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) راجع [هل الكشف التلقائي والاستجابة على النقط النهائية وضع الحظر المعتمد على Windows Server 2016 Windows Server 2012 R2؟](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> للحصول على أفضل قيمة حماية، تأكد من تكوين حل الحماية من الفيروسات لتلقي التحديثات العادية والميزات الأساسية، ومن تكوين [استثناءاتك](configure-exclusions-microsoft-defender-antivirus.md). الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر الاستثناءات المعرفة برنامج الحماية من الفيروسات من Microsoft Defender، وليس المؤشرات المعرفة ل Microsoft Defender لنقطة النهاية.[](manage-indicators.md)

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>هل يمكنني تحديد استثناءات الكشف التلقائي والاستجابة على النقط النهائية وضع الحظر؟

في حالة الحصول على خطأ موجب، يمكنك إرسال الملف لتحليله في التحليل الذكي لمخاطر الأمان من Microsoft [الإرسال](https://www.microsoft.com/en-us/wdsi/filesubmission).

يمكنك أيضا تعريف استثناء برنامج الحماية من الفيروسات من Microsoft Defender. راجع [تكوين الاستثناءات والتحقق من صحتها برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>هل أحتاج إلى تشغيل الكشف التلقائي والاستجابة على النقط النهائية وضع الحظر إذا كان برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة؟

الغرض الأساسي من الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر هو إعادة معالجة اكتشافات ما بعد الخرق التي فاتها منتج برنامج الحماية من الفيروسات من Microsoft. ومع ذلك، نوصي بإبقاء الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر قيد التشغيل، سواء كان برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع السلبي أو في الوضع النشط.

- عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر طبقة أخرى من الدفاع مع Microsoft Defender لنقطة النهاية.

- عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط، لا يوفر الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر فحصا إضافيا، ولكنه يسمح برنامج الحماية من الفيروسات من Microsoft Defender إجراءات تلقائية حول عمليات الكشف السلوكية الكشف التلقائي والاستجابة على النقط النهائية الخرق.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>هل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر على حماية المستخدم من الفيروسات؟

الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر على الحماية من الفيروسات التي يتم تشغيلها من قبل جهة خارجية على أجهزة المستخدمين. الكشف التلقائي والاستجابة على النقط النهائية يعمل في وضع الحظر إذا فات حل الحماية من الفيروسات الأساسي شيئا ما، أو إذا كان هناك الكشف بعد الخرق. الكشف التلقائي والاستجابة على النقط النهائية العمل في وضع الحظر تماما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط، باستثناء الكشف التلقائي والاستجابة على النقط النهائية  في وضع الحظر، تقوم أيضا بحظر التحف الضارة أو السلوكيات التي يتم اكتشافها وتمنعها.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>لماذا أحتاج إلى برنامج الحماية من الفيروسات من Microsoft Defender آخر الواصلين؟

نظرا برنامج الحماية من الفيروسات من Microsoft Defender الكشف عن العناصر الضارة و إصلاحها، فمن المهم إبقاها مواكبا للمعاينة. لكي الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر بفعالية، فإنه يستخدم أحدث نماذج تعلم الأجهزة والكشف السلوكي و التحليلات. تعمل [مجموعة الإمكانات Defender لنقطة](microsoft-defender-endpoint.md) النهاية بطريقة متكاملة. للحصول على أفضل قيمة حماية، يجب برنامج الحماية من الفيروسات من Microsoft Defender مواظب عليها. راجع [إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>لماذا نحتاج إلى الحماية السحابية (الخرائط)؟

الحماية السحابية مطلوبة ل تشغيل الميزة على الجهاز. تسمح الحماية السحابية [ل Defender for Endpoint](microsoft-defender-endpoint.md) بتسليم أحدث وأعظم حماية استنادا إلى معلومات الأمان العمق والعمق لدينا، إلى جانب نماذج التعلم السلوكية ونماذج تعلم الأجهزة.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>ما الفرق بين الوضعين النشط وغير النشط؟

بالنسبة لنقاط النهاية التي Windows 10 أو Windows 11 أو Windows Server أو الإصدار 1803 أو الإصدارات الأحدث أو Windows Server 2019 أو Windows Server 2022 عند برنامج الحماية من الفيروسات من Microsoft Defender  في الوضع النشط، يتم استخدامه ك برنامج الحماية من الفيروسات الأساسي على الجهاز. عند التشغيل في الوضع السلبي، برنامج الحماية من الفيروسات من Microsoft Defender منتج الحماية من الفيروسات الأساسي. في هذه الحالة، لا يتم معالجة التهديدات برنامج الحماية من الفيروسات من Microsoft Defender في الوقت الحقيقي.

> [!NOTE]
> برنامج الحماية من الفيروسات من Microsoft Defender تشغيل الجهاز في الوضع السلبي فقط عندما يكون الجهاز مدرجا في Microsoft Defender ل Endpoint.

لمزيد من المعلومات، [راجع برنامج الحماية من الفيروسات من Microsoft Defender التوافق](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>كيف يمكنني تأكيد وجود برنامج الحماية من الفيروسات من Microsoft Defender نشط أو غير نشط؟

لتأكيد ما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في وضع نشط أو غير نشط، يمكنك استخدام موجه الأوامر أو PowerShell على جهاز يعمل Windows.

|الأسلوب|الإجراء|
|---|---|
|PowerShell|1. حدد قائمة البدء، `PowerShell`وابدأ الكتابة ، ثم افتح Windows PowerShell في النتائج.<br/><br/>2. اكتب `Get-MpComputerStatus`.<br/><br/>3. في قائمة النتائج، في الصف **AMRunningMode** ، ابحث عن إحدى القيم التالية:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>لمعرفة المزيد، راجع [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|موجه الأوامر|1. حدد قائمة البدء، وابدأ `Command Prompt`الكتابة ، ثم افتح Windows موجه الأوامر في النتائج.<br/><br/>2. اكتب `sc query windefend`.<br/><br/>3. في قائمة النتائج، في صف **STATE** ، تأكد من تشغيل الخدمة. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>كيف يمكنني تأكيد تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر مع برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط؟

يمكنك استخدام PowerShell لتأكيد تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط.

1. حدد قائمة البدء، وابدأ الكتابة `PowerShell`، ثم افتح Windows PowerShell في النتائج.

2. اكتب `Get-MPComputerStatus|select AMRunningMode`.

3. تأكد من عرض النتيجة `EDR Block Mode`، .

   > [!TIP]
   > إذا برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط، سترى بدلا `Normal` من `EDR Block Mode`. لمعرفة المزيد، راجع [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>هل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر مدعوما على Windows Server 2016 Windows Server 2012 R2؟

إذا برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع السلبي، الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر معتمدا للإصدارات التالية من Windows:

- Windows 11
- Windows 10 (كل الإصدارات)
- Windows Server أو الإصدار 1803 أو الأحدث 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016 Windows Server 2012 R2 (باستخدام [حل العميل الموحد الجديد](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview))

باستخدام حل [](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) العميل الموحد الجديد ل Windows Server 2016 و Windows Server 2012 R2، يمكنك تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر إما في الوضع غير النشط أو في الوضع النشط.

> [!NOTE]
> Windows Server 2016 و Windows Server 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows Onboard](configure-server-endpoints.md) لكي تعمل هذه الميزة. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>ما مقدار الوقت الذي يستغرقه تعطيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر؟

إذا اخترت تعطيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، فقد يستغرق تعطيل هذه الإمكانية ما يصل إلى 30 دقيقة من النظام.

## <a name="see-also"></a>راجع أيضًا

- [مدونة المجتمع التقني: تقديم الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر: إيقاف الهجمات في مساراتها](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)
