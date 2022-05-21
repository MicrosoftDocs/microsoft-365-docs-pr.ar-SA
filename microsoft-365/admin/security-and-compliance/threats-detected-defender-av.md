---
title: التهديدات التي كشف عنها برنامج الحماية من الفيروسات من Microsoft Defender
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: تعرف على كيفية حماية برنامج الحماية من الفيروسات من Microsoft Defender أجهزتك Windows من تهديدات البرامج، مثل الفيروسات والبرامج الضارة وبرامج التجسس.
ms.openlocfilehash: 796edb343745e19267f901b736ca19217b0e4f01
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65620911"
---
# <a name="overview-of-threat-protection-by-microsoft-defender-antivirus"></a>نظرة عامة على الحماية من التهديدات بواسطة برنامج الحماية من الفيروسات من Microsoft Defender

يحمي برنامج الحماية من الفيروسات من Microsoft Defender أجهزتك Windows من تهديدات البرامج، مثل الفيروسات والبرامج الضارة وبرامج التجسس.

- تنتشر الفيروسات عادة عن طريق إرفاق التعليمات البرمجية الخاصة بها بملفات أخرى على جهازك أو شبكتك ويمكن أن تتسبب في عمل البرامج المصابة بشكل غير صحيح.
- تتضمن البرامج الضارة الملفات والتطبيقات والتعليمات البرمجية الضارة التي يمكن أن تسبب ضررا وتعطيل الاستخدام العادي للأجهزة. أيضا، يمكن للبرامج الضارة السماح بالوصول غير المصرح به، واستخدام موارد النظام، وسرقة كلمات المرور ومعلومات الحساب، وتأمين خروجك من الكمبيوتر وطلب الفدية، والمزيد.
- تجمع برامج التجسس البيانات، مثل نشاط استعراض الويب، وترسل البيانات إلى الخوادم البعيدة.
 
لتوفير الحماية من التهديدات، يستخدم برنامج الحماية من الفيروسات من Microsoft Defender عدة أساليب. تتضمن هذه الأساليب الحماية المقدمة من السحابة، والحماية في الوقت الحقيقي، وتحديثات الحماية المخصصة.

- تساعد الحماية التي توفرها السحابة على توفير الكشف شبه الفوري عن التهديدات الجديدة والناشئة ومنعها.
- يستخدم المسح المستمر مراقبة سلوك الملفات والعمليات والتقنيات الأخرى (المعروفة أيضا باسم *الحماية في الوقت الحقيقي*).
- تستند تحديثات الحماية المخصصة إلى التعلم الآلي وتحليل البيانات الضخمة البشرية والآلية والبحث المتعمق في مقاومة التهديدات. 

لمعرفة المزيد حول البرامج الضارة برنامج الحماية من الفيروسات من Microsoft Defender، راجع المقالات التالية: 

- [فهم البرامج الضارة & التهديدات الأخرى](/windows/security/threat-protection/intelligence/understanding-malware)
- [كيف تحدد Microsoft البرامج الضارة والتطبيقات التي قد تكون غير مرغوب فيها](/windows/security/threat-protection/intelligence/criteria)
- [حماية الجيل التالي في Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>ماذا يحدث عند استخدام حل الحماية من الفيروسات غير التابع ل Microsoft؟ 

برنامج الحماية من الفيروسات من Microsoft Defender هو جزء من نظام التشغيل ويتم تمكينه على الأجهزة التي تعمل Windows 10. ومع ذلك، إذا كنت تستخدم حل الحماية من الفيروسات غير التابع ل Microsoft ولا تستخدم [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)، برنامج الحماية من الفيروسات من Microsoft Defender تنتقل تلقائيا إلى وضع التعطيل.  

عندما تكون في وضع التعطيل، لا يزال بإمكان المستخدمين والعملاء استخدام برنامج الحماية من الفيروسات من Microsoft Defender لإجراء عمليات المسح المجدولة أو عند الطلب لتحديد التهديدات؛ ومع ذلك، لن يعود برنامج الحماية من الفيروسات من Microsoft Defender:

- يتم استخدامها كتطبيق الحماية من الفيروسات الافتراضي.
- فحص الملفات بشكل نشط بحثا عن التهديدات.
- معالجة التهديدات أو حلها.

إذا قمت بإلغاء تثبيت حل الحماية من الفيروسات غير التابع ل Microsoft، فسينتقل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا إلى الوضع النشط لحماية أجهزة Windows من التهديدات.

> [!TIP]
> - إذا كنت تستخدم Microsoft 365، ففكر في استخدام برنامج الحماية من الفيروسات من Microsoft Defender كحل الحماية من الفيروسات الأساسي. يمكن أن يوفر التكامل حماية أفضل. راجع [الأفضل معا: برنامج الحماية من الفيروسات من Microsoft Defender Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - تأكد من تحديث برنامج الحماية من الفيروسات من Microsoft Defender، حتى لو كنت تستخدم حل الحماية من الفيروسات غير Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>ما يجب توقعه عند الكشف عن التهديدات

عند اكتشاف التهديدات بواسطة برنامج الحماية من الفيروسات من Microsoft Defender، تحدث الأشياء التالية:

- يتلقى المستخدمون [إعلامات في Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- يتم سرد عمليات الكشف في [تطبيق أمن Windows](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) على صفحة **محفوظات الحماية**.  
- إذا قمت [بتأمين أجهزة Windows 10](../setup/secure-win-10-pcs.md) [وتسجيلها في Intune](/mem/intune/enrollment/windows-enrollment-methods)، وكان لدى مؤسستك 800 جهاز أو أقل مسجلة، فسترى عمليات الكشف عن التهديدات والرؤى في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> على صفحة **"التهديدات ومكافحة الفيروسات**"، والتي يمكنك الوصول إليها من **برنامج الحماية من الفيروسات من Microsoft Defender** البطاقة على الصفحة **الرئيسية** (أو من جزء التنقل عن طريق تحديد **HealthThreats** >  & مكافحة الفيروسات).

    إذا كان لدى مؤسستك أكثر من 800 جهاز مسجل في Intune، فستتم مطالبتك بعرض عمليات الكشف عن التهديدات والرؤى من [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) بدلا من صفحة **التهديدات ومكافحة الفيروسات**.
 
    > [!NOTE]
    > يتم نشر بطاقة **برنامج الحماية من الفيروسات من Microsoft Defender** **وصفحة التهديدات والحماية من الفيروسات** على مراحل، لذلك قد لا يكون لديك حق الوصول الفوري إليها.

في معظم الحالات، لا يحتاج المستخدمون إلى اتخاذ أي إجراء إضافي. بمجرد اكتشاف ملف أو برنامج ضار على جهاز، برنامج الحماية من الفيروسات من Microsoft Defender حظره ومنع تشغيله. بالإضافة إلى ذلك، تتم إضافة التهديدات المكتشفة حديثا إلى محرك الحماية من الفيروسات والبرامج الضارة بحيث تتم حماية الأجهزة والمستخدمين الآخرين أيضا.  

إذا كان هناك إجراء يحتاج المستخدم إلى اتخاذه، مثل الموافقة على إزالة ملف ضار، فسيرى ذلك في الإعلام الذي يتلقاه. لمعرفة المزيد حول الإجراءات التي يتخذها برنامج الحماية من الفيروسات من Microsoft Defender بالنيابة عن المستخدم، أو الإجراءات التي قد يحتاج المستخدمون إلى اتخاذها، راجع [محفوظات الحماية](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). لمعرفة كيفية إدارة عمليات الكشف عن التهديدات كمحترف/مسؤول في تكنولوجيا المعلومات، راجع [مراجعة التهديدات المكتشفة واتخاذ إجراء](../../business-premium/m365bp-review-threats-take-action.md).

لمعرفة المزيد حول التهديدات المختلفة، تفضل بزيارة <a href="https://www.microsoft.com/wdsi/threats" target="_blank">موقع التحليل الذكي لمخاطر الأمان من Microsoft Threats</a>، حيث يمكنك تنفيذ الإجراءات التالية: 

- عرض المعلومات الحالية حول أهم التهديدات.
- عرض أحدث التهديدات لمنطقة معينة.
- ابحث في موسوعة التهديد عن تفاصيل حول تهديد معين.

## <a name="related-content"></a>المحتويات ذات الصلة

[تأمين أجهزة Windows](/misc/m365bp-secure-windows-devices) (مقالة)\
[تقييم برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (مقالة)\
[كيفية تشغيل الحماية من الفيروسات في الوقت الحقيقي والحماية من الفيروسات التي توفرها السحابة](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) (مقالة)\
[كيفية تشغيل برنامج الحماية من الفيروسات من Microsoft Defender واستخدامها من تطبيق أمن Windows](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (المقال)\
[كيفية تشغيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (مقالة)\
[كيفية تحديث تعريفات الحماية من الفيروسات](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (مقالة)\
[كيفية إرسال البرامج الضارة وغير الضارة إلى Microsoft للتحليل](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (مقالة)