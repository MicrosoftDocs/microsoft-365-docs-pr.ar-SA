---
title: عرض التقارير لمنع فقدان البيانات
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/7/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: استخدم تقارير DLP في Office 365 لعرض عدد تطابقات نهج DLP أو تجاوزها أو الإيجابيات الخاطئة ومعرفة ما إذا كانت تتجه لأعلى أو لأسفل مع مرور الوقت.
ms.openlocfilehash: b264a0e0b76397be99d7586ac793dac501b6672e
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011599"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>عرض التقارير لمنع فقدان البيانات

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

بعد إنشاء نهج منع فقدان بيانات Microsoft Purview (DLP)، ستحتاج إلى التحقق من أنها تعمل كما تريد وتساعدك على البقاء متوافقا. باستخدام تقارير DLP في مدخل توافق Microsoft Purview، يمكنك عرض:

- **تطابقات نهج DLP** يعرض هذا التقرير عدد تطابقات نهج DLP بمرور الوقت. يمكنك تصفية التقرير حسب التاريخ أو الموقع أو النهج أو الإجراء. يمكنك استخدام هذا التقرير من أجل:

  - يمكنك ضبط نهج DLP أو تحسينها أثناء تشغيلها في وضع الاختبار. يمكنك عرض القاعدة المحددة التي تطابق المحتوى.

  - ركز على فترات زمنية محددة وفهم أسباب الارتفاعات والاتجاهات.

  - اكتشف العمليات التجارية التي تنتهك نهج DLP الخاصة بمؤسستك.

  - فهم أي تأثير تجاري لنهج DLP من خلال رؤية الإجراءات التي يتم تطبيقها على المحتوى.

  - تحقق من التوافق مع نهج DLP محدد من خلال إظهار أي تطابقات لهذا النهج.

  - عرض قائمة بأفضل المستخدمين وتكرار المستخدمين الذين يساهمون في الحوادث في مؤسستك.

  - عرض قائمة بأفضل أنواع المعلومات الحساسة في مؤسستك.

- **أحداث DLP** يعرض هذا التقرير أيضا تطابقات النهج بمرور الوقت، مثل تقرير مطابقة النهج. ومع ذلك، يعرض تقرير مطابقة النهج التطابقات على مستوى القاعدة؛ على سبيل المثال، إذا تطابقت رسالة بريد إلكتروني مع ثلاث قواعد مختلفة، يعرض تقرير مطابقة النهج ثلاثة عناصر سطر مختلفة. وعلى النقيض من ذلك، يعرض تقرير الحوادث التطابقات على مستوى العنصر؛ على سبيل المثال، إذا تطابقت رسالة بريد إلكتروني مع ثلاث قواعد مختلفة، يعرض تقرير الحوادث عنصر سطر واحد لهذا الجزء من المحتوى.

  نظرا إلى أن عدد التقارير مجمع بشكل مختلف، فإن تقرير مطابقة النهج أفضل لتحديد التطابقات مع قواعد محددة وضبط نهج DLP. يعد تقرير الحوادث أفضل لتحديد أجزاء معينة من المحتوى التي تشكل مشكلة لنهج DLP الخاصة بك.

- **الإيجابيات والتجاوزات الخاطئة ل DLP** إذا كان نهج DLP يسمح للمستخدمين بتجاوزه أو الإبلاغ عن إيجابية خاطئة، يعرض هذا التقرير عدد هذه المثيلات بمرور الوقت. يمكنك تصفية التقرير حسب التاريخ أو الموقع أو النهج. يمكنك استخدام هذا التقرير من أجل:

  - يمكنك ضبط نهج DLP أو تحسينها من خلال رؤية النهج التي تتحمل عددا كبيرا من الإيجابيات الخاطئة.

  - عرض التبريرات التي يقدمها المستخدمون عند حل تلميح نهج عن طريق تجاوز النهج.

  - اكتشف أين تتعارض نهج DLP مع العمليات التجارية الصالحة من خلال تكبد عدد كبير من عمليات تجاوز المستخدم.

يمكن أن تعرض جميع تقارير DLP بيانات من آخر فترة زمنية مدتها أربعة أشهر. قد تستغرق أحدث البيانات ما يصل إلى 24 ساعة لتظهر في التقارير.

يمكنك العثور على هذه التقارير في **لوحة معلومات** **تقارير مدخل** \> \> الامتثال ل Microsoft Purview.

![يتطابق نهج DLP مع التقرير.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)

## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>عرض الضبط المرسل من قبل مستخدم لتجاوز

إذا كان نهج DLP يسمح للمستخدمين بتجاوزه، يمكنك استخدام تقرير الإيجابية الزائفة والتجاوز لعرض النص الذي أرسله المستخدمون في تلميح النهج.

![حقل الضبط في تفاصيل تقرير النتائج الإيجابية والتجاوزية الخاطئة ل DLP.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)

## <a name="take-action-on-insights-and-recommendations"></a>اتخاذ إجراء بشأن الرؤى والتوصيات

يمكن أن تعرض التقارير نتائج التحليلات والتوصيات حيث يمكنك النقر فوق أيقونة التحذير الأحمر للاطلاع على تفاصيل حول المشكلات المحتملة واتخاذ إجراء بديل محتمل.

![النقر فوق أيقونة نتائج التحليلات للاطلاع على التفاصيل والإجراءات التي يجب اتخاذها.](../media/51782036-7299-4960-8175-75c2b1637159.png)

## <a name="permissions-for-dlp-reports"></a>أذونات لتقارير DLP

لعرض تقارير DLP في مركز التوافق & الأمان، يجب تعيين ما يلي:

- دور **قارئ الأمان** في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات دور "إدارة المؤسسة" و"قارئ الأمان" في مركز إدارة Exchange.

- **دور View-only DLP Compliance Management** في Security & Compliance Center. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات أدوار مسؤول التوافق وإدارة المؤسسة ومسؤول الأمان وقارئ الأمان في مركز التوافق & الأمان.

- **دور المستلمين للعرض فقط** في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات دور إدارة التوافق وإدارة المؤسسة View-Only في مركز إدارة Exchange.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>البحث عن cmdlets لتقارير DLP

لاستخدام أوامر cmdlets الخاصة بتقارير DLP، نفذ الخطوات التالية:

1. [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. استخدم أوامر cmdlets التالية:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
   - [Get-DlpSiDetectionsReport](/powershell/module/exchange/get-dlpsidetectionsreport)

ومع ذلك، تحتاج تقارير DLP إلى سحب البيانات من جميع Microsoft 365، بما في ذلك Exchange Online. لهذا السبب، تتوفر أوامر cmdlets التالية لتقارير DLP في Exchange Online Powershell. لاستخدام cmdlets لتقارير DLP هذه، نفذ الخطوات التالية:

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. استخدم أوامر cmdlets التالية:

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-MailDetailDlpPolicyReport](/powershell/module/exchange/get-maildetaildlppolicyreport)
