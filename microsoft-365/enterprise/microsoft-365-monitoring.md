---
title: مراقبة Microsoft 365
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
description: استخدم مراقبة Microsoft 365 للحصول على معلومات حول الحوادث أو النصائح في Microsoft 365.
ms.openlocfilehash: 47f54859d7dd0973814a0ad9229a902bddcb8587
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824839"
---
# <a name="learn-about-microsoft-365-monitoring"></a>التعرف على مراقبة Microsoft 365

يمكنك استخدام لوحات المعلومات في [مركز مسؤولي Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) لمراقبة صحة خدمات Microsoft المختلفة لاشتراك Microsoft 365 الخاص بمؤسستك. بدأت هذه الإمكانية في البداية مع Exchange Online والآن تم توسيعها إلى خدمات Microsoft أخرى مثل Microsoft Teams Microsoft 365 Apps والمزيد من الخدمة في المستقبل. توفر لك المراقبة معلومات حول الحوادث والنصائح التي يتم جمعها في هذه الفئات:

- **البنية الأساسية**. يتم الكشف عن المشكلة في البنية الأساسية Microsoft 365 التي تمتلكها Microsoft لتوفير تحديثات منتظمة وحل المشكلة. على سبيل المثال، لا يمكن للمستخدمين الوصول إلى Exchange Online بسبب مشاكل تتعلق Exchange أو غيرها من البنية الأساسية السحابية Microsoft 365.

- **البنية الأساسية لجهة خارجية**. يتم الكشف عن المشكلة في البنية الأساسية لجهة خارجية التي تعتمد عليها مؤسستك وتتطلب إجراء من مؤسستك لحلها. على سبيل المثال، يتم تقييد معاملات مصادقة المستخدم بواسطة موفر خدمة الرمز المميز للأمان (STS) التابع لجهة خارجية الذي يمنع المستخدمين من الاتصال Exchange Online.

- **البنية الأساسية للعملاء**. يتم الكشف عن المشكلة في البنية الأساسية لمؤسستك وتتطلب إجراء من مؤسستك لحلها. على سبيل المثال، لا يمكن للمستخدمين الوصول إلى Exchange Online لأنهم غير قادرين على الحصول على رمز مصادقة مميز من موفر STS الذي تستضيفه مؤسستك بسبب شهادة منتهية الصلاحية.

فيما يلي مثال على صفحة **Service health** في مركز مسؤولي Microsoft 365، والتي تتوفر في **Health** >  **Service health** لسيناريوهات المؤسسة وسيناريوهات [حساب الأولوية](../admin/setup/priority-accounts.md).

![صفحة Service health في مركز مسؤولي Microsoft 365.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

سيتم تحديد **المشاكل في مؤسستك** واستخدامها من خلال المراقبة على مستوى المؤسسة ومراقبة الحساب ذات الأولوية.

تشير قيمة عمود **"الصحة**" ضمن **"المشاكل" في مؤسستك** إلى ما إذا كانت البنية الأساسية لمؤسستك أو برامج الجهات الخارجية تؤثر على تجربة حماية الخدمة لمستخدمي مؤسستك و/أو حسابات الأولوية في Exchange Online. تتطلب الاستشارات أو الحوادث حل الإجراءات الخاصة بك.

تشير قيمة العمود **Health** ضمن **حماية خدمة Microsoft** إلى أن الخدمة سليمة أو تحتوي على استشارات أو حوادث استنادا إلى خدمات السحابة التي تحتفظ بها Microsoft.

فيما يلي مثال على صفحة المراقبة Exchange Online في مركز مسؤولي Microsoft 365 التي تعرض حالة سيناريوهات الحساب على مستوى المؤسسة والأولوية المتوفرة من **Health** >  **Service health** >  **Exchange Online**.

![سيناريوهات على مستوى المؤسسة لمراقبة Exchange Online.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

باستخدام صفحة قائمة السيناريو، يمكنك معرفة ما إذا كانت خدمة Microsoft سليمة أم لا وما إذا كانت هناك أي حوادث أو استشارات مقترنة. على سبيل المثال، من خلال مراقبة Exchange Online، يمكنك النظر في حالة الخدمة لسيناريوهات بريد إلكتروني محددة وعرض إشارات قريبة من الوقت الحقيقي لتحديد التأثير حسب السيناريو على مستوى المؤسسة. يمكنك أيضا رؤية حالة سيناريوهات حساب الأولوية، إذا كانت متوفرة.

## <a name="requirements-for-monitoring"></a>متطلبات المراقبة

تم تمكين هذه المعاينة للعملاء الذين يستوفون المتطلبات التالية:

- يجب أن يكون لدى مؤسستك عدد تراخيص يبلغ 5000 على الأقل من منتج واحد أو مجموعة من هذه المنتجات: Office 365 E3 أو Microsoft 365 E3 أو Office 365 E5 أو Microsoft 365 E5.

   على سبيل المثال، يمكن أن يكون لدى مؤسستك 3000 ترخيص Office 365 E3 و2500 Microsoft 365 E5، لإجمالي 5500 ترخيص من المنتجات المؤهلة.

- يجب أن يكون لدى مؤسستك ما لا يقل عن 50 مستخدما نشطا شهريا لخدمات Microsoft 365 أساسية واحدة أو أكثر، والتي تتضمن Microsoft Teams، OneDrive for Business، SharePoint Online، Exchange Online، Office تطبيقات.

- يمكن لأي دور مع أذونات مستوى لوحة معلومات حماية الخدمة الوصول إلى المراقبة Exchange Online. للحصول على مزيد من المعلومات، اطلع على [كيفية التحقق من حالة خدمة Microsoft 365](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>مراقبة إضافية خدمات Microsoft

كما يتم تمكين المراقبة الخاصة بخدمتها خدمات Microsoft التالية. حدد الارتباط المقابل لمعرفة المزيد حول مراقبة تلك الخدمة.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [تطبيقات Microsoft 365](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>إرسال ملاحظات إلينا

هناك طريقتان يمكنك من خلالهما تقديم الملاحظات:

- استخدم الخيار **"تقديم ملاحظات**" المتوفر في كل صفحة من صفحات مركز مسؤولي Microsoft 365.

- إرسال ملاحظات باستخدام **هل هذا المنشور مفيد؟ ارتباط لحادث أو استشارة معينة.

  !["هل هذا المنشور مفيد؟" ارتباط لحادث أو استشارة معينة.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. لماذا لا أرى ارتباط "عرض" ضمن عمود المراقبة التنظيمية في مركز مسؤولي Microsoft 365 داخل "حماية الخدمة"؟

أولا، تأكد من تمكين مركز الإدارة الجديد على الصفحة **الرئيسية** [مركز مسؤولي Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

ثم تأكد من تلبية كل من المتطلبات التالية:

- يجب أن يكون لدى مؤسستك عدد تراخيص لا يقل عن 5000، من منتج واحد أو مجموعة من هذه المنتجات: Office 365 E3 أو Microsoft 365 E3 أو Office 365 E5 أو Microsoft 365 E5.

- يجب أن يكون لدى مؤسستك ما لا يقل عن 50 مستخدما نشطا شهريا لخدمات Microsoft 365 أساسية واحدة أو أكثر، والتي تتضمن Microsoft Teams، OneDrive for Business، SharePoint Online، Exchange Online، Office تطبيقات.

إذا انخفض عدد التراخيص لمؤسستك إلى أقل من 5000 مستخدم وكان عدد المستخدمين النشطين الشهري أقل من 50 مستخدما في الخدمات الأساسية، فلن يتم تمكين مراقبة Exchange Online حتى يتم استيفاء هذه المتطلبات.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. هل ستكون هناك سيناريوهات مراقبة أخرى للخدمات الأخرى في المستقبل؟

نعم. لدينا بعض الخدمات الإضافية في المعاينة العامة الآن. سنواصل العمل على توسيع البصمة لتشمل خدمات أخرى.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. ما هي خطة التوفر العام لهذه التجربة؟

خطة Microsoft هي جمع ملاحظاتك حول تجربة المعاينة ثم تحديد خطتنا للتوفر العام.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. هل هذه ميزة مجانية (مضمنة) أم مدفوعة (إضافية)؟

هذه ميزة مجانية تتوفر في المعاينة ولا تتوفر إلا للعملاء الذين يستوفون المتطلبات الواردة في السؤال 1. لا يوجد خيار مدفوع لتلقي هذا المحتوى.

### <a name="5-how-do-i-provide-feedback"></a>5. كيف أعمل تقديم ملاحظات؟

للحصول على ملاحظات عامة، استخدم أيقونة **"تقديم الملاحظات** " في الزاوية السفلية اليسرى من صفحة المراقبة.

للحصول على ملاحظات حول الحوادث أو النصائح، استخدم **هل هذا المنشور مفيد؟ الارتباط.

### <a name="6-are-there-any-privacy-concerns"></a>6. هل هناك أي مخاوف بشأن الخصوصية؟

تركز المراقبة على بيانات تعريف الخدمة ولا تتم مراقبة محتوى المستخدم.
