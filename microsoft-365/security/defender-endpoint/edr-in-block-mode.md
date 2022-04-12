---
title: الكشف عن نقطة النهاية والاستجابة لها في وضع الحظر
description: التعرف على الكشف عن تهديدات نقاط النهاية والرد عليها في وضع الحظر
keywords: Microsoft Defender لنقطة النهاية، mde، الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، حظر الوضع الخامل
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
ms.date: 04/04/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 655681820633b0f53ba29de49052690018cab1e7
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783700"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>الكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>ما هو الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر؟

يوفر [الكشف عن نقطة النهاية والاستجابة](overview-endpoint-detection-response.md) (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر حماية إضافية من البيانات الاصطناعية الضارة عندما لا يكون برنامج الحماية من الفيروسات من Microsoft Defender هو منتج الحماية من الفيروسات الأساسي ويعمل في الوضع الخامل. يعمل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر خلف الكواليس لمعالجة البيانات الاصطناعية الضارة التي تم اكتشافها بواسطة قدرات الكشف التلقائي والاستجابة على النقط النهائية. قد يكون منتج الحماية من الفيروسات الأساسي غير الخاص ب Microsoft قد فوت هذه البيانات الاصطناعية. بالنسبة للأجهزة التي تعمل برنامج الحماية من الفيروسات من Microsoft Defender كمكافحة فيروسات أساسية، يوفر الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر طبقة إضافية من الدفاع من خلال السماح برنامج الحماية من الفيروسات من Microsoft Defender اتخاذ إجراءات تلقائية بشأن عمليات الكشف عن الكشف التلقائي والاستجابة على النقط النهائية السلوكية بعد الخرق.

> [!IMPORTANT]
> لا يوفر الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر كافة الحماية المتوفرة عند تمكين الحماية برنامج الحماية من الفيروسات من Microsoft Defender في الوقت الحقيقي. لن تعمل جميع الميزات التي تعتمد على برنامج الحماية من الفيروسات من Microsoft Defender لتكون حل الحماية من الفيروسات النشط، بما في ذلك الأمثلة الرئيسية التالية:
>
> - لا تتوفر الحماية في الوقت الحقيقي، بما في ذلك المسح الضوئي عند الوصول، عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل. لمعرفة المزيد حول إعدادات نهج الحماية في الوقت الحقيقي، راجع **[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية دائما وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)**.
>
> - تتوفر ميزات مثل **[حماية الشبكة](network-protection.md)** **[وقواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)** فقط عند تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط.
>
> من المتوقع أن يوفر حل الحماية من الفيروسات غير التابع ل Microsoft هذه الإمكانات.

يتم دمج الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر مع [& إدارة الثغرات الأمنية التهديد](next-gen-threat-and-vuln-mgt.md). سيحصل فريق الأمان في مؤسستك على [توصية أمان](tvm-security-recommendation.md) لتشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر إذا لم يكن ممكنا بالفعل.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="التوصية بتشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر" lightbox="images/edrblockmode-TVMrecommendation.png":::

> [!TIP]
> للحصول على أفضل حماية، تأكد من **[نشر Microsoft Defender لنقطة النهاية الأساسات](configure-machines-security-baseline.md)**.

## <a name="what-happens-when-something-is-detected"></a>ماذا يحدث عند اكتشاف شيء ما؟

عند تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، واكتشاف بيانات اصطناعية ضارة، Microsoft Defender لنقطة النهاية حظر هذه البيانات الاصطناعية ومعالجتها. سيرى فريق عمليات الأمان حالة الكشف على أنها **محظورة** أو **ممنوعة** في [مركز الصيانة](respond-machine-alerts.md#check-activity-details-in-action-center)، مدرجة كإجراءات مكتملة.

تعرض الصورة التالية مثيلا للبرامج غير المرغوب فيها التي تم اكتشافها وحظرها من خلال الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر:

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="الكشف عن طريق الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر" lightbox="images/edr-in-block-mode-detection.png":::


## <a name="enable-edr-in-block-mode"></a>تمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر

> [!IMPORTANT]
> بدءا من إصدار النظام الأساسي 4.18.2202.X، يمكنك الآن تعيين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر لاستهداف مجموعات أجهزة معينة باستخدام Intune CSPs. يمكنك الاستمرار في تعيين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر على مستوى المستأجر في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>. يوصى الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر بشكل أساسي للأجهزة التي تعمل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل (يتم تثبيت حل مكافحة الفيروسات غير التابع ل Microsoft ونشط على الجهاز). 

> [!TIP]
> تأكد من استيفاء [المتطلبات](#requirements-for-edr-in-block-mode) قبل تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر.

### <a name="security-portal"></a>مدخل الأمان 

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) وسجل الدخول.

2. اختر **الإعدادات** \> **الميزات المتقدمة** **العامة** \> **لنقاط** \> النهاية.

3. قم بالتمرير لأسفل، ثم قم بتشغيل **تمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر**.

### <a name="intune"></a>Intune

لإنشاء نهج مخصص في Intune، راجع [Deploy OMA-URIs لاستهداف CSP من خلال Intune، ومقارنة بالأماكن المحلية](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

لمزيد من المعلومات حول Defender CSP المستخدم الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، راجع "Configuration/PassiveRemediation" ضمن [Defender CSP](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>متطلبات الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر

يسرد الجدول التالي متطلبات الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر:

|شرط|التفاصيل|
|---|---|
|الأذونات|يجب أن يكون لديك دور المسؤول العام أو مسؤول الأمان المعين في [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). لمزيد من المعلومات، راجع [الأذونات الأساسية](basic-permissions.md).|
|نظام التشغيل|يجب أن تكون الأجهزة قيد التشغيل أحد الإصدارات التالية من Windows: <br/>- Windows 11 <br/>- Windows 10 (كافة الإصدارات)<br/>- Windows Server 2022 <br/>- Windows Server 2019<br/>- Windows Server، الإصدار 1803 أو الأحدث<br/>- Windows Server 2016 و Windows Server 2012 R2 (مع [حل العميل الموحد الجديد](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))<sup>[[1](#fn1)]</sup>  |
|Microsoft Defender for Endpoint|يجب إلحاق الأجهزة ب Defender لنقطة النهاية. راجع المقالات التالية: <br/>- [الحد الأدنى من متطلبات Microsoft Defender لنقطة النهاية](minimum-requirements.md)<br/>- [إلحاق الأجهزة وتكوين قدرات Microsoft Defender لنقطة النهاية](onboard-configure.md)<br/>- [إلحاق خوادم Windows بخدمة Defender for Endpoint](configure-server-endpoints.md)<br/>- [وظائف Windows Server 2012 R2 و2016 الجديدة في الحل الموحد الحديث (معاينة)](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) |
|برنامج الحماية من الفيروسات من Microsoft Defender|يجب برنامج الحماية من الفيروسات من Microsoft Defender تثبيت الأجهزة وتشغيلها إما في الوضع النشط أو الوضع السلبي. [تأكد من برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الخامل](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|الحماية المقدمة من السحابة|يجب تكوين برنامج الحماية من الفيروسات من Microsoft Defender بحيث [يتم تمكين الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md).|
|النظام الأساسي برنامج الحماية من الفيروسات من Microsoft Defender|يجب أن تكون الأجهزة محدثة. للتأكيد، باستخدام PowerShell، قم بتشغيل [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) cmdlet كمسؤول. في سطر **AMProductVersion** ، يجب أن تشاهد **4.18.2001.10** أو أعلى. <p> لمعرفة المزيد، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).|
|محرك برنامج الحماية من الفيروسات من Microsoft Defender|يجب أن تكون الأجهزة محدثة. للتأكيد، باستخدام PowerShell، قم بتشغيل [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) cmdlet كمسؤول. في سطر **AMEngineVersion** ، يجب أن تشاهد **1.1.16700.2** أو أعلى. <p> لمعرفة المزيد، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) هل [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر معتمدة على Windows Server 2016 و Windows Server 2012 R2؟](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> للحصول على أفضل قيمة حماية، تأكد من تكوين حل الحماية من الفيروسات لتلقي التحديثات العادية والميزات الأساسية، ومن [تكوين الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md) الخاصة بك. تحترم الكشف التلقائي والاستجابة على النقط النهائية في وضع الكتلة الاستثناءات التي تم تعريفها برنامج الحماية من الفيروسات من Microsoft Defender، ولكن ليس [المؤشرات](manage-indicators.md) التي تم تعريفها ل Microsoft Defender لنقطة النهاية.

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>هل يمكنني تحديد استثناءات الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر؟

في حال حصولك على نتيجة إيجابية خاطئة، يمكنك إرسال الملف للتحليل في [موقع إرسال التحليل الذكي لمخاطر الأمان من Microsoft](https://www.microsoft.com/en-us/wdsi/filesubmission).

يمكنك أيضا تحديد استثناء برنامج الحماية من الفيروسات من Microsoft Defender. راجع [تكوين الاستثناءات والتحقق من صحتها لإجراء عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>هل أحتاج إلى تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر إذا كان لدي برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل على الأجهزة؟

الغرض الأساسي من الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر هو معالجة عمليات الكشف بعد الاختراق التي فاتها منتج الحماية من الفيروسات غير التابع ل Microsoft. هناك حد أدنى من الفائدة في تمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط، لأنه من المتوقع أن تلتقط الحماية في الوقت الحقيقي عمليات الكشف وتعالجها أولا. نوصي بتمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر على نقاط النهاية حيث يعمل Microsoft Defender for Antivirus في الوضع السلبي. يمكن معالجة عمليات الكشف الكشف التلقائي والاستجابة على النقط النهائية تلقائيا بواسطة [حماية PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) أو عن طريق [التحقيق التلقائي & قدرات المعالجة](automated-investigations.md) في وضع الحظر.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>هل سيؤثر الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر على الحماية من الفيروسات الخاصة بالمستخدم؟

لا يؤثر الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر على الحماية من الفيروسات من الجهات الخارجية التي تعمل على أجهزة المستخدمين. يعمل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر إذا يفتقد حل الحماية من الفيروسات الأساسي إلى شيء ما، أو إذا كان هناك اكتشاف ما بعد الاختراق. تعمل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر تماما مثل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، باستثناء ذلك الكشف التلقائي والاستجابة على النقط النهائية  في وضع الحظر أيضا يحظر ويعالج البيانات الاصطناعية الضارة أو السلوكيات التي تم اكتشافها.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>لماذا أحتاج إلى تحديث برنامج الحماية من الفيروسات من Microsoft Defender؟

نظرا لأن برنامج الحماية من الفيروسات من Microsoft Defender يكشف عن العناصر الضارة ويعالجها، فمن المهم إبقائه محدثا. لكي تكون الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر فعالة، فإنها تستخدم أحدث نماذج تعلم الجهاز والكشف السلوكي والاستقصاء. يعمل مكدس القدرات [Defender لنقطة النهاية](microsoft-defender-endpoint.md) بطريقة متكاملة. للحصول على أفضل قيمة حماية، يجب أن تبقى برنامج الحماية من الفيروسات من Microsoft Defender محدثة. راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>لماذا نحتاج إلى حماية السحابة (MAPS)؟

هناك حاجة إلى حماية السحابة لتشغيل الميزة على الجهاز. تسمح حماية [السحابة ل Defender لنقطة النهاية](microsoft-defender-endpoint.md) بتقديم أحدث وأكبر حماية استنادا إلى اتساع وعمق التحليل الذكي للأمان، بالإضافة إلى نماذج التعلم السلوكية والجهاز.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>ما الفرق بين الوضع النشط والسالب؟

بالنسبة لنقاط النهاية التي تعمل Windows 10 أو Windows 11 أو Windows Server أو الإصدار 1803 أو إصدار أحدث أو Windows Server 2019 أو Windows Server 2022 عند برنامج الحماية من الفيروسات من Microsoft Defender  في الوضع النشط، يتم استخدامه كمكافحة الفيروسات الأساسية على الجهاز. عند التشغيل في الوضع الخامل، برنامج الحماية من الفيروسات من Microsoft Defender ليس منتج الحماية من الفيروسات الأساسي. في هذه الحالة، لا تتم معالجة التهديدات من خلال برنامج الحماية من الفيروسات من Microsoft Defender في الوقت الحقيقي.

> [!NOTE]
> يمكن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل فقط عند إلحاق الجهاز Microsoft Defender لنقطة النهاية.

لمزيد من المعلومات، راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>كيف أعمل تأكيد برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الخامل؟

لتأكيد ما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع النشط أو الخامل، يمكنك استخدام موجه الأوامر أو PowerShell على جهاز يعمل Windows.

|الاسلوب|الاجراء|
|---|---|
|PowerShell|1. حدد قائمة البدء، وابدأ الكتابة`PowerShell`، ثم افتح Windows PowerShell في النتائج.<br/><br/>2. اكتب `Get-MpComputerStatus`.<br/><br/>3. في قائمة النتائج، في صف **AMRunningMode** ، ابحث عن إحدى القيم التالية:<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>لمعرفة المزيد، راجع [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|موجه الأوامر|1. حدد قائمة البدء وابدأ الكتابة`Command Prompt`، ثم افتح موجه الأوامر Windows في النتائج.<br/><br/>2. اكتب `sc query windefend`.<br/><br/>3. في قائمة النتائج، في صف **STATE** ، تأكد من تشغيل الخدمة. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>كيف أعمل تأكيد تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر مع برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي؟

يمكنك استخدام PowerShell لتأكيد تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر مع تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل.

1. حدد قائمة البدء، وابدأ الكتابة`PowerShell`، ثم افتح Windows PowerShell في النتائج.

2. اكتب `Get-MPComputerStatus|select AMRunningMode`.

3. تأكد من عرض النتيجة، `EDR Block Mode`، .

   > [!TIP]
   > إذا كان برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط، فسترى `Normal` بدلا من `EDR Block Mode`. لمعرفة المزيد، راجع [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>هل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر معتمد على Windows Server 2016 وserver Windows 2012 R2؟

إذا كان برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع النشط أو الوضع الخامل، فإن الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر مدعوم بالإصدارات التالية من Windows:

- Windows 11
- Windows 10 (كافة الإصدارات)
- Windows Server، الإصدار 1803 أو الأحدث 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016 و Windows Server 2012 R2 (مع [حل العميل الموحد الجديد](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))

باستخدام [حل العميل الموحد الجديد](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) لخادم Windows 2016 وخادم Windows 2012 R2، يمكنك تشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر إما في الوضع السلبي أو الوضع النشط.

> [!NOTE]
> يجب إلحاق Windows Server 2016 وخادم Windows 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows](configure-server-endpoints.md) الملحقة لكي تعمل هذه الميزة. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>كم من الوقت يستغرق تعطيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر؟

إذا اخترت تعطيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، فقد يستغرق النظام ما يصل إلى 30 دقيقة لتعطيل هذه الإمكانية.

## <a name="see-also"></a>راجع أيضًا

- [مدونة المجتمع التقني: تقديم الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر: إيقاف الهجمات في مساراتها](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)
