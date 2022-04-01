---
title: مراجعة متطلبات البنية ومفاهيم التخطيط ل Microsoft Defender Office 365
description: سيساعدك الرسم التخطيطي التقني ل Microsoft Defender Office 365 Microsoft 365 Defender على فهم الهوية في Microsoft 365 قبل إنشاء المعمل التجريبي أو بيئة الإصدار التجريبي.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 49acb346be872c870f1ae52024963680e6631363
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63579675"
---
# <a name="review-microsoft-defender-for-office-365-architecture-requirements-and-key-concepts"></a>مراجعة Microsoft Defender Office 365 متطلبات البنية الأساسية والمفاهيم الأساسية


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 1 من 3](eval-defender-office-365-overview.md) في عملية إعداد بيئة التقييم ل Microsoft Defender Office 365. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-office-365-overview.md).

قبل تمكين Defender Office 365، تأكد من فهم البنية ويمكنها تلبية المتطلبات. تصف هذه المقالة البنية والمفاهيم الأساسية والمتطلبات الأساسية التي يجب أن تلبيها Exchange Online البيئة.

## <a name="understand-the-architecture"></a>فهم البنية

يوضح الرسم التخطيطي التالي بنية الأساس ل Microsoft Defender Office، والذي يمكن أن يتضمن بوابة SMTP أو تكاملا في الموقع المحلي. تتطلب سيناريوهات المشاركة المختلطة (أي علب بريد الإنتاج سواء كانت في الموقع المحلي أو عبر الإنترنت) تكوينات أكثر تعقيدا ولا يتم تناولها في هذه المقالة أو إرشادات التقييم.

![تصميم Microsoft Defender Office 365.](../../media/defender/m365-defender-office-architecture.png)

يصف الجدول التالي هذا الرسم التوضيحي.

|الاستدعاء  |الوصف  |
|---------|---------|
|1     | يقوم الخادم المضيف للمرسل الخارجي عادة بإجراء عملية البحث عن DNS عامة لسجل MX، الذي يوفر الخادم الهدف لترحيل الرسالة.  يمكن أن تكون هذه Exchange Online (EXO) مباشرة أو بوابة SMTP تم تكوينها للترحيل مقابل EXO.  |
|2     | Exchange Online Protection يتفاوض ويتحقق من صحة الاتصال الوارد ويفحص رؤوس الرسائل ومحتوياتها لتحديد النهج أو العلامات أو المعالجة الإضافية المطلوبة.  |
|3     | Exchange Online دمجها مع Microsoft Defender Office 365 توفير المزيد من الحماية المتقدمة من المخاطر وتخفيفها وتكيفها. |
|4     | تتم معالجة الرسالة غير الضارة أو المحظورة أو المعزولة وتسليمها إلى المستلم في EXO حيث يتم تقييم تفضيلات المستخدم المتعلقة بالبريد الإلكتروني غير الهام أو قواعد علبة البريد أو الإعدادات الأخرى وتشغلها. |
|5     | يمكن تمكين التكامل مع Active Directory المحلي باستخدام Azure AD الاتصال لمزامنة الكائنات والحسابات التي تم تمكين البريد لها وتوفيرها إلى Azure Active Directory وفي النهاية Exchange Online. |
|6     | عند دمج بيئة المحلية، يتم التشجيع بشدة على استخدام خادم Exchange لإدارة وإدارة السمات والإعدادات والتكوينات ذات الصلة بالبريد |
|7     | يشارك Microsoft Defender Office 365 إشارات Microsoft 365 Defender للكشف والاستجابة الموسعة (XDR).|

التكامل المحلي شائع ولكنه اختياري. إذا كانت بيئتك سحابية فقط، فإن هذه الإرشادات ستعمل أيضا معك.

## <a name="understand-key-concepts"></a>فهم المفاهيم الأساسية

حدد الجدول التالي المفاهيم الأساسية التي من المهم فهمها عند تقييم MDO وتكوينه ونشره.


|المفهوم  |الوصف |معلومات إضافية  |
|---------|---------|---------|
|Exchange Online Protection      |    Exchange Online Protection (EOP) هي خدمة التصفية المستندة إلى السحابة التي تساعد على حماية مؤسستك من رسائل البريد الإلكتروني غير المرغوب فيها والبرامج الضارة. يتم تضمين EOP في Microsoft 365 التراخيص التي تتضمن Exchange Online.     |   [Exchange Online Protection عامة](../office-365-security/exchange-online-protection-overview.md)      |
|الحماية من البرامج الضارة     |    تكون المؤسسات التي بها علب بريد في EXO محمية تلقائيا من البرامج الضارة.     |  [الحماية من البرامج الضارة في EOP](../office-365-security/anti-malware-protection.md)       |
|الحماية من البريد العشوائي     |   يتم حماية المؤسسات التي بها علب بريد في EXO تلقائيا من سياسات البريد العشوائي والبريد العشوائي.      |  [الحماية من البريد العشوائي في EOP](../office-365-security/anti-spam-protection.md)       |
|الحماية من التصيد الاحتيالي |  يوفر MDO المزيد من الحماية المتقدمة لمكافحة التصيد الاحتيالي ذات الصلة بالتصيد الاحتيالي وصيد whaling والفدية الضارة وغيرها من الأنشطة الضارة.   | [حماية إضافية من التصيد الاحتيالي في Microsoft Defender Office 365](../office-365-security/anti-phishing-protection.md)   |
|الحماية من ال انتحال     |   يتضمن EOP ميزات للمساعدة في حماية مؤسستك من المرسلين المنتحلين (التزييف).      |   [الحماية من ال انتحال في EOP](../office-365-security/anti-spoofing-protection.md)      |
|خزينة المرفقات     |   خزينة المرفقات طبقة حماية إضافية باستخدام بيئة ظاهرية للتحقق من المرفقات و"إقحامها" في رسائل البريد الإلكتروني قبل تسليمها.      |   [خزينة المرفقات في Microsoft Defender Office 365](../office-365-security/safe-attachments.md)      |
|خزينة مرفقات SharePoint OneDrive و Microsoft Teams     |    بالإضافة إلى ذلك، خزينة مرفقات SharePoint و OneDrive و Microsoft Teams طبقة إضافية من الحماية للملفات التي تم تحميلها إلى مستودعات التخزين السحابية.     |  [خزينة المرفقات SharePoint OneDrive و Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md)       |
|الارتباطات الآمنة     | خزينة الارتباطات هي ميزة توفر مسح URL وإعادة كتابته ضمن رسائل البريد الإلكتروني الواردة وتوفر التحقق من هذه الارتباطات قبل تسليمها أو النقر فوقها.        |   [خزينة ارتباطات في Microsoft Defender Office 365](../office-365-security/safe-links.md)      |
|    |         |         |

للحصول على مزيد من المعلومات المفصلة حول الإمكانات المضمنة مع Microsoft Defender Office، راجع [Microsoft Defender للحصول](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) على Office 365 الخدمة.

## <a name="review-architecture-requirements"></a>مراجعة متطلبات البنية
تفترض التجربة الناجحة لتقييم MDO أو إنتاجه المتطلبات الأساسية التالية:
- كل علب بريد المستلمين في Exchange Online.
- يتم حل سجل MX العام مباشرة إلى EOP أو بوابة SMTP من جهة خارجية التي تنقل بعد ذلك البريد الإلكتروني الخارجي الوارد مباشرة إلى EOP.
- يتم تكوين مجال البريد الإلكتروني الأساسي *ك موثوق في* Exchange Online.
- لقد قمت بنشر ميزة "حظر Edge المستند إلى الدليل *" (* DBEB) وتكوينها بنجاح كما هو مناسب. لمزيد من المعلومات، راجع [استخدام Directory-Based Edge لرفض الرسائل المرسلة إلى مستلمين غير صالحين](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

> [!IMPORTANT]
> إذا كانت هذه المتطلبات غير قابلة للتطبيق أو إذا كنت لا تزال في سيناريو تعايش مختلط، فإن تقييم Microsoft Defender ل Office 365 قد يتطلب تكوينات أكثر تعقيدا أو تقدما لم يتم تناولها بالكامل في هذه الإرشادات.

## <a name="siem-integration"></a>تكامل SIEM

يمكنك دمج Microsoft Defender for Office 365 مع Microsoft Sentinel لتحليل أحداث الأمان عبر مؤسستك بشكل أكثر شمولية، فضلا عن إنشاء دفاتر تشغيل للاستجابة الفورية والفعالة. لمزيد من المعلومات، [راجع الاتصال تنبيهات من Microsoft Defender Office 365](/azure/sentinel/connect-office-365-advanced-threat-protection).

يمكن أيضا Office 365 Microsoft Defender for Office 365 في حلول إدارة أحداث ومعلومات الأمان الأخرى (SIEM) باستخدام Office 365 [API لإدارة النشاط](/office/office-365-management-api/office-365-management-activity-api-reference).

## <a name="next-steps"></a>الخطوات التالية

الخطوة 2 من 3: [تمكين بيئة التقييم ل Microsoft Defender Office 365](eval-defender-office-365-enable-eval.md)

العودة إلى نظرة عامة حول [تقييم Microsoft Defender Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md) 
