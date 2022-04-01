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
description: تعرف على برنامج الحماية من الفيروسات من Microsoft Defender حماية أجهزة Windows من تهديدات البرامج، مثل الفيروسات والبرامج الضارة وبرامج التجسس.
ms.openlocfilehash: c11ce9a2f38f1ecb7f47cd5b74e710d92c8ffbe0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579712"
---
# <a name="threats-detected-by-microsoft-defender-antivirus"></a>التهديدات التي كشف عنها برنامج الحماية من الفيروسات من Microsoft Defender

برنامج الحماية من الفيروسات من Microsoft Defender حماية أجهزة Windows من تهديدات البرامج، مثل الفيروسات والبرامج الضارة وبرامج التجسس.

- تنتشر الفيروسات عادة عن طريق إرفاق التعليمات البرمجية الخاصة بها بملفات أخرى على جهازك أو شبكتك ويمكن أن تتسبب في عمل البرامج المصابة بشكل غير صحيح.
- تتضمن البرامج الضارة الملفات الضارة والتطبيقات التعليمات البرمجية التي يمكن أن تسبب تلفا وتعطل الاستخدام العادي للأجهزة. علاوة على ذلك، يمكن للبرامج الضارة السماح بالوصول غير المصرح به واستخدام موارد النظام وسرقة كلمات المرور ومعلومات الحساب وقفل الكمبيوتر لديك وطلب فدية والمزيد.
- تجمع برامج التجسس البيانات، مثل نشاط استعراض الويب، وترسل البيانات إلى خوادم بعيدة.
 
لتوفير الحماية من المخاطر، برنامج الحماية من الفيروسات من Microsoft Defender استخدام أساليب متعددة. تتضمن هذه الأساليب الحماية التي يتم توفيرها من السحابة والحماية في الوقت الحقيقي وتحديثات الحماية المخصصة.

- تساعد الحماية التي يتم توفيرها في السحابة على توفير الكشف الفوري عن التهديدات الجديدة والناشئة وحظرها.
- تستخدم عملية المسح المستمر مراقبة الملفات وسلوك العملية وتقنيات أخرى (تعرف أيضا بالحماية *في الوقت الحقيقي*).
- تستند تحديثات الحماية المخصصة إلى التعلم الآلي وتحليل البيانات الكبيرة البشرية والآلية وأبحاث معمقة حول المقاومة للتهديدات. 

لمعرفة المزيد حول البرامج الضارة برنامج الحماية من الفيروسات من Microsoft Defender، راجع المقالات التالية: 

- [فهم البرامج الضارة & المخاطر الأخرى](/windows/security/threat-protection/intelligence/understanding-malware)
- [كيفية تحديد Microsoft للبرامج الضارة والتطبيقات التي يحتمل أن تكون غير مرغوب فيها](/windows/security/threat-protection/intelligence/criteria)
- [حماية الجيل التالي في Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>ماذا يحدث عند استخدام حل برنامج الحماية من الفيروسات غير Microsoft؟ 

برنامج الحماية من الفيروسات من Microsoft Defender هو جزء من نظام التشغيل وممكن على الأجهزة التي تعمل Windows 10. ومع ذلك، إذا كنت تستخدم حل برنامج الحماية من الفيروسات غير Microsoft ولا تستخدم [Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)، برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا إلى وضع المعطل.  

عند العمل في وضع المعطل، لا يزال بإمكان المستخدمين والعملاء استخدام برنامج الحماية من الفيروسات من Microsoft Defender عمليات الفحص المجدولة أو عند الطلب لتحديد التهديدات؛ ومع ذلك، لن برنامج الحماية من الفيروسات من Microsoft Defender بعد ذلك:

- يمكن استخدامه ك تطبيق الحماية من الفيروسات الافتراضي.
- قم بمسح الملفات ضوئيا بشكل نشط من أجل التهديدات.
- معالجة التهديدات أو حلها.

إذا قمت ب إلغاء تثبيت حل مكافحة الفيروسات برنامج الحماية من الفيروسات من Microsoft Defender Microsoft، برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا إلى الوضع النشط لحماية أجهزة Windows من التهديدات.

> [!TIP]
> - إذا كنت تستخدم Microsoft 365، فنظر في استخدام برنامج الحماية من الفيروسات من Microsoft Defender كحل أساسي لمكافحة الفيروسات. يمكن أن يوفر التكامل حماية أفضل. راجع [معا بشكل أفضل: برنامج الحماية من الفيروسات من Microsoft Defender Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - تأكد من برنامج الحماية من الفيروسات من Microsoft Defender حتى لو كنت تستخدم حل برنامج الحماية من الفيروسات من Microsoft.

## <a name="what-to-expect-when-threats-are-detected"></a>ما يجب توقعه عند اكتشاف التهديدات

عند اكتشاف التهديدات من قبل برنامج الحماية من الفيروسات من Microsoft Defender، تحدث الأمور التالية:

- يتلقى [المستخدمون الإعلامات في Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- يتم سرد الاكتشافات في تطبيق أمن Windows [على](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) **صفحة محفوظات** الحماية.  
- إذا قمت بتأمين أجهزة [Windows 10](../setup/secure-win-10-pcs.md) الخاصة بك ثم سجلتها في [Intune](/mem/intune/enrollment/windows-enrollment-methods)، وكان لديك 800 جهاز أو أقل مسجلا، سترى عمليات الكشف عن المخاطر والأفكار الدقيقة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>  **على صفحة التهديدات وفيروسات الفيروسات، والتي يمكنك الوصول إليها من برنامج الحماية من الفيروسات من Microsoft Defender** على الصفحة **الرئيسية** (أو من جزء التنقل عن طريق تحديد **HealthThreats** >  & antivirus).

    إذا كانت مؤسستك لديها أكثر من 800 جهاز مسجل في Intune، فسوف يتم مطالبتك لعرض الكشف عن المخاطر والأفكار الدقيقة من [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) بدلا من صفحة التهديدات و مكافحة **الفيروسات.**
 
    > [!NOTE]
    > يتم **برنامج الحماية من الفيروسات من Microsoft Defender** الصفحة "التهديدات"  و"الحماية من الفيروسات" على مراحل، لذلك قد لا يكون لديك حق الوصول الفوري إليها.

في معظم الحالات، لا يحتاج المستخدمون إلى اتخاذ أي إجراء آخر. بمجرد اكتشاف ملف أو برنامج ضار على جهاز، برنامج الحماية من الفيروسات من Microsoft Defender حظره ومنع تشغيله. بالإضافة إلى ذلك، تضاف التهديدات التي تم الكشف عنها حديثا إلى محرك الحماية من الفيروسات والحماية من البرامج الضارة بحيث تكون الأجهزة والمستخدمين الآخرين محميين أيضا.  

إذا كان هناك إجراء يحتاج المستخدم إلى اتخاذه، مثل الموافقة على إزالة ملف ضار، فسوف يظهر ذلك في الإعلام الذي يتلقاه. لمعرفة المزيد حول الإجراءات برنامج الحماية من الفيروسات من Microsoft Defender التي يتخذها المستخدم بالنيابة عن المستخدم، أو الإجراءات التي قد يحتاج المستخدمون إلى اتخاذها، راجع [محفوظات الحماية](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). للتعرف على كيفية إدارة عمليات الكشف عن المخاطر كمحترف/مسؤول في إدارة المعلومات، راجع مراجعة التهديدات التي تم الكشف عنها [واتخاذ إجراء](review-threats-take-action.md).

لمعرفة المزيد حول التهديدات المختلفة، تفضل <a href="https://www.microsoft.com/wdsi/threats" target="_blank">بزيارة</a> موقع التحليل الذكي لمخاطر الأمان من Microsoft المخاطر، حيث يمكنك تنفيذ الإجراءات التالية: 

- عرض المعلومات الحالية حول التهديدات القصوى.
- عرض التهديدات الأخيرة التي تواجه منطقة معينة.
- ابحث في الموسوعة الخاصة بالخطر عن تفاصيل حول خطر معين.

## <a name="related-content"></a>المحتوى ذي الصلة

[تأمين Windows (](/misc/m365bp-secure-windows-devices)مقالة)\
[تقييم برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (مقالة)\
[كيفية تشغيل الحماية من الفيروسات في الوقت الحقيقي](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) والحماية من الفيروسات التي يتم تسليمها من السحابة (مقالة)\
[كيفية تشغيل برنامج الحماية من الفيروسات من Microsoft Defender من تطبيق أمن Windows (](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus)مقالة)\
[كيفية تشغيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام "نهج المجموعة"](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (مقالة)\
[كيفية تحديث تعريفات برنامج الحماية من الفيروسات](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (مقالة)\
[كيفية إرسال البرامج الضارة وغير الضارة إلى Microsoft لتحليلها](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (مقالة)