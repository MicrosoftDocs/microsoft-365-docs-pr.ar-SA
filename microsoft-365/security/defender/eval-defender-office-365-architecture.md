---
title: مراجعة متطلبات البنية ومفاهيم التخطيط Microsoft Defender لـ Office 365
description: سيساعدك الرسم التخطيطي التقني Microsoft Defender لـ Office 365 في Microsoft 365 Defender على فهم الهوية في Microsoft 365 قبل إنشاء مختبر تجريبي أو بيئة تجريبية.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1002b03a0ebb3940d544343476045d52e8209273
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749935"
---
# <a name="review-microsoft-defender-for-office-365-architecture-requirements-and-key-concepts"></a>مراجعة متطلبات البنية Microsoft Defender لـ Office 365 والمفاهيم الرئيسية


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 1 من 3](eval-defender-office-365-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender لـ Office 365. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-office-365-overview.md).

قبل تمكين Defender لـ Office 365، تأكد من فهمك للبنية ويمكن أن تفي بالمتطلبات. تصف هذه المقالة البنية والمفاهيم الرئيسية والمتطلبات الأساسية التي يجب أن تلبيها بيئة Exchange Online الخاصة بك.

## <a name="understand-the-architecture"></a>فهم البنية

يوضح الرسم التخطيطي التالي بنية الأساس ل Microsoft Defender ل Office، والتي يمكن أن تتضمن بوابة SMTP تابعة لجهة خارجية أو تكامل محلي. تتطلب سيناريوهات التوافق المختلط (أي علب بريد الإنتاج محليا وعلى الإنترنت) تكوينات أكثر تعقيدا ولا تغطيها هذه المقالة أو إرشادات التقييم.

:::image type="content" source="../../media/defender/m365-defender-office-architecture.png" alt-text="بنية Microsoft Defender لـ Office 365" lightbox="../../media/defender/m365-defender-office-architecture.png":::

يصف الجدول التالي هذا الرسم التوضيحي.

|الاتصال  |الوصف  |
|---------|---------|
|1     | يقوم الخادم المضيف للمرسل الخارجي عادة بإجراء بحث DNS عام عن سجل MX، والذي يوفر الخادم الهدف لترحيل الرسالة.  يمكن أن تكون هذه الإحالة إما Exchange Online (EXO) مباشرة أو بوابة SMTP التي تم تكوينها لترحيل مقابل EXO.  |
|2     | Exchange Online Protection يتفاوض ويتحقق من صحة الاتصال الوارد ويفحص رؤوس الرسائل والمحتوى لتحديد النهج الإضافية أو وضع العلامات أو المعالجة المطلوبة.  |
|3     | يتكامل Exchange Online مع Microsoft Defender لـ Office 365 لتوفير حماية أكثر تقدما من التهديدات والتخفيف من حدتها ومعالجتها. |
|4     | تتم معالجة الرسالة غير الضارة أو المحظورة أو المعزولة وتسليمها إلى المستلم في EXO حيث يتم تقييم تفضيلات المستخدم المتعلقة بالبريد غير الهام أو قواعد علبة البريد أو الإعدادات الأخرى وتشغيلها. |
|5     | يمكن تمكين التكامل مع Active Directory محلي باستخدام Azure AD Connect لمزامنة العناصر والحسابات الممكنة للبريد وتوفيرها إلى Azure Active Directory وفي نهاية المطاف Exchange Online. |
|6     | عند دمج بيئة محلية، يتم تشجيع استخدام خادم Exchange للإدارة والإدارة المدعومة للسمات والإعدادات والتكوينات المتعلقة بالبريد |
|7     | Microsoft Defender لـ Office 365 مشاركة الإشارات إلى Microsoft 365 Defender للكشف الموسع والاستجابة (XDR).|

التكامل المحلي شائع ولكنه اختياري. إذا كانت بيئتك سحابية فقط، فإن هذه الإرشادات ستعمل أيضا نيابة عنك.

## <a name="understand-key-concepts"></a>فهم المفاهيم الرئيسية

حدد الجدول التالي المفاهيم الرئيسية التي من المهم فهمها عند تقييم MDO وتكوينه ونشره.


|مفهوم  |الوصف |معلومات إضافية  |
|---------|---------|---------|
|Exchange Online Protection      |    Exchange Online Protection (EOP) هي خدمة التصفية المستندة إلى السحابة التي تساعد على حماية مؤسستك من البريد الإلكتروني العشوائي والبرامج الضارة. يتم تضمين EOP في جميع تراخيص Microsoft 365 التي تتضمن Exchange Online.     |   [نظرة عامة على Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md)      |
|الحماية من البرامج الضارة     |    المؤسسات التي لها علب بريد في EXO محمية تلقائيا من البرامج الضارة.     |  [الحماية من البرامج الضارة في EOP](../office-365-security/anti-malware-protection.md)       |
|الحماية من البريد العشوائي     |   تتم حماية المؤسسات التي لها علب بريد في EXO تلقائيا من نهج البريد غير الهام والبريد العشوائي.      |  [الحماية من البريد العشوائي في EOP](../office-365-security/anti-spam-protection.md)       |
|الحماية من التصيد الاحتيالي |  يوفر MDO حماية أكثر تقدما ضد التصيد الاحتيالي المتعلقة بالتصيد الاحتيالي الرمح، والثمالة، وفيروسات الفدية الضارة، وغيرها من الأنشطة الضارة.   | [حماية إضافية من التصيد الاحتيالي في Microsoft Defender لـ Office 365](../office-365-security/anti-phishing-protection.md)   |
|الحماية من تزييف الهوية     |   يتضمن EOP ميزات للمساعدة في حماية مؤسستك من المرسلين المخادعة (المخادعة).      |   [الحماية من الانتحال في EOP](../office-365-security/anti-spoofing-protection.md)      |
|مرفقات آمنة     |   توفر "المرفقات الآمنة" طبقة حماية إضافية باستخدام بيئة ظاهرية للتحقق من المرفقات في رسائل البريد الإلكتروني و"إزالتها" قبل تسليمها.      |   [المرفقات الآمنة في Microsoft Defender لـ Office 365](../office-365-security/safe-attachments.md)      |
|المرفقات الآمنة ل SharePoint وOneDrive وMicrosoft Teams     |    بالإضافة إلى ذلك، توفر "المرفقات الآمنة" ل SharePoint وOneDrive وMicrosoft Teams طبقة حماية إضافية للملفات التي تم تحميلها إلى مستودعات التخزين السحابية.     |  [المرفقات الآمنة لـ SharePoint وOneDrive وMicrosoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md)       |
|الارتباطات الآمنة     | تعد "الارتباطات الآمنة" ميزة توفر مسح URL وإعادة كتابته داخل رسائل البريد الإلكتروني الواردة وتوفر التحقق من هذه الارتباطات قبل تسليمها أو النقر فوقها.        |   [الارتباطات الآمنة في Microsoft Defender لـ Office 365](../office-365-security/safe-links.md)      |
|    |         |         |

للحصول على معلومات أكثر تفصيلا حول الإمكانات المضمنة في Microsoft Defender ل Office، راجع [وصف الخدمة Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

## <a name="review-architecture-requirements"></a>مراجعة متطلبات البنية
يفترض تقييم MDO الناجح أو الإصدار التجريبي للإنتاج المتطلبات المسبقة التالية:
- جميع علب بريد المستلمين موجودة حاليا في Exchange Online.
- يحل سجل MX العام مباشرة إلى EOP أو بوابة SMTP تابعة لجهة خارجية تقوم بعد ذلك بترحيل البريد الإلكتروني الخارجي الوارد مباشرة إلى EOP.
- تم تكوين مجال بريدك الإلكتروني الأساسي على أنه *موثوق به* في Exchange Online.
- لقد نجحت في نشر وتكوين *حظر Edge المستند إلى الدليل* (DBEB) حسب الاقتضاء. لمزيد من المعلومات، راجع ["استخدام Directory-Based حظر Edge" لرفض الرسائل المرسلة إلى مستلمين غير صالحين](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

> [!IMPORTANT]
> إذا لم تكن هذه المتطلبات قابلة للتطبيق أو كنت لا تزال في سيناريو تعايش مختلط، فقد يتطلب تقييم Microsoft Defender لـ Office 365 تكوينات أكثر تعقيدا أو تقدما لا تغطيها هذه الإرشادات بشكل كامل.

## <a name="siem-integration"></a>تكامل إدارة معلومات الأمان والأحداث

يمكنك دمج Microsoft Defender لـ Office 365 مع Microsoft Sentinel لتحليل أحداث الأمان بشكل أكثر شمولا عبر مؤسستك وإنشاء أدلة مبادئ للاستجابة الفعالة والفورية. لمزيد من المعلومات، راجع [تنبيهات الاتصال من Microsoft Defender لـ Office 365](/azure/sentinel/connect-office-365-advanced-threat-protection).

يمكن أيضا دمج Microsoft Defender لـ Office 365 في حلول أخرى لإدارة معلومات الأمان والأحداث (SIEM) باستخدام [واجهة برمجة تطبيقات إدارة النشاط Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

## <a name="next-steps"></a>الخطوات التالية

الخطوة 2 من 3: [تمكين بيئة التقييم Microsoft Defender لـ Office 365](eval-defender-office-365-enable-eval.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender لـ Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md) 
