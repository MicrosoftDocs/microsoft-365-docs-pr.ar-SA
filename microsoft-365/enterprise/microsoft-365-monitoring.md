---
title: Microsoft 365 مراقبة
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: mediumn
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: استخدم Microsoft 365 المعلومات للحصول على معلومات حول الأحداث أو استشارات في Microsoft 365.
ms.openlocfilehash: 2d78bcae258730e1b48c7d6cc77fa5ae2b200b07
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520797"
---
# <a name="learn-about-microsoft-365-monitoring"></a>التعرف على Microsoft 365 المراقبة

يمكنك استخدام لوحات المعلومات في مركز مسؤولي Microsoft 365 لمراقبة [](https://go.microsoft.com/fwlink/p/?linkid=2024339) حالة خدمات Microsoft مختلفة لاشتراك Microsoft 365 مؤسستك. بدأت هذه الإمكانية في Exchange Online، والآن يتم توسيعها إلى خدمات Microsoft أخرى مثل Microsoft Teams Microsoft 365 Apps والمزيد من الخدمات في المستقبل. توفر لك المراقبة معلومات حول الأحداث والاستشارات التي يتم تجميعها في هذه الفئات:

- **البنية الأساسية**. يتم اكتشاف المشكلة في Microsoft 365 الأساسية التي تملكها Microsoft لتوفير تحديثات منتظمة وحل المشكلة. على سبيل المثال، لا يمكن للمستخدمين الوصول إلى Exchange Online بسبب مشاكل تتعلق Exchange أو أي Microsoft 365 سحابية أخرى.

- **البنية الأساسية الخاصة ب جهة خارجية**. يتم اكتشاف المشكلة في البنية الأساسية التابعة لأي جهة خارجية حيث اتخذت مؤسستك تبعية وتتطلب اتخاذ إجراء من مؤسستك لحلها. على سبيل المثال، يتم كبح معاملات مصادقة المستخدمين بواسطة موفر خدمة رمز أمان مميز (STS) جهة خارجية يمنع المستخدمين من الاتصال Exchange Online.

- **البنية الأساسية للعملاء**. يتم اكتشاف المشكلة في البنية الأساسية لمنظمتك وتتطلب اتخاذ إجراء من مؤسستك لحلها. على سبيل المثال، لا يمكن للمستخدمين الوصول إلى Exchange Online نظرا لعدم تمكنهم من الحصول على رمز مصادقة مميز من موفر STS المستضاف بواسطة مؤسستك بسبب شهادة منتهية الصلاحية.

فيما يلي مثال لصفحة Service health في  مركز مسؤولي Microsoft 365 المتوفرة في **Health** >  **Service health** لسيناريوهات المؤسسة وسيناريوهات [حساب](../admin/setup/priority-accounts.md) الأولوية.

![الصفحة Service health في مركز مسؤولي Microsoft 365.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**سيتم تحديد المشاكل** في مؤسستك وسيستخدمها مراقبة على مستوى المؤسسة ومراقبة حساب الأولوية.

تشير قيمة عمود "حالة" ضمن  المشاكل في مؤسستك إلى ما إذا كانت البنية الأساسية لم مؤسستك أو برامج الأطراف الخارجية تؤثر على تجربة حالة الخدمة لمستخدمي مؤسستك و/أو حسابات الأولوية في Exchange Online. تتطلب استشارات أو أحداث إجراءاتك لحلها.

تشير قيمة عمود **"الصحة** " ضمن "صحة خدمة **Microsoft** " إلى أن الخدمة سليمة أو أن لها استشارات أو أحداث استنادا إلى الخدمات السحابية التي تحافظ عليها Microsoft.

فيما يلي مثال لصفحة مراقبة Exchange Online في مركز مسؤولي Microsoft 365 تعرض حالة سيناريوهات حساب على مستوى المؤسسة والأولوية المتوفرة من **health** >  **Service health** >  **Exchange Online**.

![سيناريوهات على مستوى المؤسسة Exchange Online المراقبة.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

باستخدام صفحة قائمة السيناريوهات، يمكنك معرفة ما إذا كانت خدمة Microsoft سليمة أم لا وما إذا كانت هناك أي أحداث أو استشارات مقترنة. على سبيل المثال، باستخدام Exchange Online، يمكنك الاطلاع على حالة الخدمة لسيناريوهات بريد إلكتروني معينة وعرض إشارات في الوقت الحقيقي تقريبا لتحديد تأثير السيناريو على مستوى المؤسسة. يمكنك أيضا الاطلاع على حالة سيناريوهات حساب الأولوية، إذا كانت متوفرة.

## <a name="requirements-for-monitoring"></a>متطلبات المراقبة

يتم تمكين هذه المعاينة للعملاء الذين يلبيون المتطلبات التالية:

- تحتاج مؤسستك إلى الحصول على عدد تراخيص لا يقل عن 5000 ترخيص من واحد أو مجموعة من هذه المنتجات: Office 365 E3 أو Microsoft 365 E3 أو Office 365 E5 أو Microsoft 365 E5.

   على سبيل المثال، يمكن أن تملك مؤسستك 3000 ترخيص Office 365 E3 و2500 Microsoft 365 E5، لإجمالي 5500 ترخيص من المنتجات المؤهلة.

- تحتاج مؤسستك إلى أن يكون لديها 50 مستخدما نشطا شهريا على الأقل لخدمات Microsoft 365 أساسية واحدة أو أكثر، بما في ذلك Microsoft Teams و OneDrive for Business و SharePoint عبر الإنترنت و Exchange Online و Office التطبيقات.

- يمكن لأي دور مع أذونات "لوحة معلومات صحة الخدمة" الوصول إلى Exchange Online المراقبة. للحصول على مزيد من المعلومات، اطلع على [كيفية التحقق من حالة خدمة Microsoft 365](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>مراقبة إضافية خدمات Microsoft

يتم أيضا تمكين المراقبة الخاصة بالخدمة للمراقبة التالية خدمات Microsoft. حدد الارتباط المناظر لمعرفة المزيد حول مراقبة تلك الخدمة.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [تطبيقات Microsoft 365](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>إرسال ملاحظاتك إلينا

هناك طريقتان لتقديم الملاحظات:

- استخدم الخيار **تقديم ملاحظات** متوفرا على كل صفحة من صفحات مركز مسؤولي Microsoft 365.

- إرسال ملاحظات باستخدام **هل هذا المنشور مفيد؟ ارتباط لحادث أو استشارات معينة.

  !["هل هذا المنشور مفيد؟" ارتباط لحادث أو استشارات معينة.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. لماذا لا يمكنني رؤية ارتباط "عرض" ضمن عمود مراقبة المؤسسة في مركز مسؤولي Microsoft 365 حالة الخدمة؟

أولا، تأكد من تمكين مركز الإدارة الجديد على الصفحة **الرئيسية** [مركز مسؤولي Microsoft 365.](https://go.microsoft.com/fwlink/p/?linkid=2024339)

بعد ذلك، تأكد من تلبية كل من المتطلبات التالية:

- تحتاج مؤسستك إلى الحصول على عدد تراخيص لا يقل عن 5000 ترخيص، من واحد أو مجموعة من هذه المنتجات: Office 365 E3 أو Microsoft 365 E3 أو Office 365 E5 أو Microsoft 365 E5.

- تحتاج مؤسستك إلى أن يكون لديها 50 مستخدما نشطا شهريا على الأقل لخدمات Microsoft 365 أساسية واحدة أو أكثر، بما في ذلك Microsoft Teams و OneDrive for Business و SharePoint عبر الإنترنت و Exchange Online و Office التطبيقات.

إذا كان عدد التراخيص لمنظمتك أقل من 5000 مستخدم وكان عدد المستخدمين النشطين الشهريين أقل من 50 مستخدما في الخدمات الأساسية، فلن يتم تمكين مراقبة Exchange Online إلا بعد تلبية هذه المتطلبات.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. هل سيكون هناك سيناريوهات مراقبة أخرى لخدمات أخرى في المستقبل؟

نعم. لدينا الآن بعض الخدمات الأخرى في المعاينة العامة. سنستمر في العمل على توسيع نطاق العمل ليشمل خدمات أخرى.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. ما هي خطة التوفر العام لهذه التجربة؟

خطة Microsoft هي تجميع ملاحظاتك حول تجربة المعاينة ثم تحديد خطتنا للتوفر العام.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. هل هذه ميزة مجانية (مضمنة) أو مدفوعة (إضافية)؟

هذه ميزة مجانية في المعاينة ومتوفرة فقط للعملاء الذين يلبيون المتطلبات المذكورة في السؤال 1. لا يوجد خيار مدفوع لتلقي هذا المحتوى.

### <a name="5-how-do-i-provide-feedback"></a>5. كيف أعمل تقديم ملاحظات؟

للحصول على ملاحظات عامة، استخدم الأيقونة **تقديم ملاحظات** في الزاوية السفلية اليسرى من صفحة المراقبة.

للحصول على ملاحظات حول الأحداث أو النصائح، استخدم **هل هذا المنشور مفيد؟ ارتباط.

### <a name="6-are-there-any-privacy-concerns"></a>6. هل هناك أي مشاكل تتعلق بالخصوصية؟

يركز المراقبة على بيانات تعريف الخدمة ولا يتم مراقبة محتوى المستخدم.
