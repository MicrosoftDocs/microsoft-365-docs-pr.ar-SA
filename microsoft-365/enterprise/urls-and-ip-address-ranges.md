---
title: نطاقات عناوين IP وعناوين URL في Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/28/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'ملخص: يتطلب Office 365 الاتصال بالإنترنت. يجب أن تكون نقاط النهاية أدناه قابلة للوصول للعملاء الذين يستخدمون خطط Office 365، بما في ذلك سحابة القطاع الحكومي (GCC).'
hideEdit: true
ms.openlocfilehash: 04522b211056b1d7c6feba08dd97fc3a2d33451a
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: HT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634856"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>نطاقات عناوين IP وعناوين URL في Office 365

يتطلب Office 365 الاتصال بالإنترنت. يجب أن تكون نقاط النهاية أدناه قابلة للوصول للعملاء الذين يستخدمون خطط Office 365، بما في ذلك سحابة القطاع الحكومي (GCC).
  
*Office 365 حول العالم (+GCC)*\|[Office 365 المشغل بواسطة 21 Vianet](urls-and-ip-address-ranges-21vianet.md)\|[Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md)\|[Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md)\|

|ملاحظات|تنزيل|استخدام |
|---|---|---|
|**آخر تحديث:** 03/28/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [اشتراك في سجلّ التغييرات](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**التنزيل:** كل الوجهات المطلوبة والاختيارية في قائمة [تنسيق JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) واحدة.|**استخدام:** وكيلنا [ملفات PAC](managing-office-365-endpoints.md#pacfiles)|
|

ابدأ ب [إدارة نقاط نهاية Office 365](managing-office-365-endpoints.md) لفهم توصياتنا لإدارة اتصال الشبكة باستخدام هذه البيانات. يتم تحديث بيانات نقاط النهاية كما تقتضي الحاجة في بداية كل شهر باستخدام عناوين IP وعناوين URL الجديدة المنشورة قبل 30 يوما من تنشيطها. يسمح هذا للعملاء الذين ليس لديهم تحديثات تلقائية حتى الآن بإكمال عملياتهم قبل أن يكون الاتصال الجديد مطلوبا. قد يتم أيضا تحديث نقاط النهاية خلال الشهر إذا لزم الأمر لمعالجة تصعيد الدعم أو أحداث الأمان أو المتطلبات التشغيلية الفورية الأخرى. يتم إنشاء كافة البيانات المعروضة في هذه الصفحة أدناه من خدمات ويب المستندة إلى REST. إذا كنت تستخدم برنامج نصي أو جهاز شبكة للوصول إلى هذه البيانات، فيجب الانتقال إلى [خدمة ويب](microsoft-365-ip-web-service.md) مباشرة.

تسرد بيانات نقطة النهاية أدناه متطلبات الاتصال من جهاز المستخدم إلى Office 365. للحصول على تفاصيل حول عناوين IP المستخدمة لاتصالات الشبكة من Microsoft إلى شبكة عملاء، تسمى أحيانا اتصالات الشبكة المختلطة أو الواردة، راجع [نقاط النهاية الإضافية](additional-office365-ip-addresses-and-urls.md) للحصول على مزيد من المعلومات.

يتم تجميع نقاط النهاية في أربع ميادين خدمة تمثل أحجام العمل الأساسية الثلاثة ومجموعة من الموارد المشتركة. قد يتم استخدام المجموعات لإقران تدفقات استخدام الشبكة بتطبيق معين، ولكن نظرا لأن الميزات غالبا ما تستهلك نقاط النهاية عبر أحجام عمل متعددة، فلا يمكن استخدام هذه المجموعات بفعالية لتقييد الوصول.

أعمدة البيانات المعروضة هي:

- **معرف**: رقم معرف الصف، المعروف أيضا بمجموعة نقاط النهاية. هذا المعرف هو نفسه الذي يتم إرجاعه بواسطة خدمة ويب لمجموعة نقاط النهاية.

- **الفئة** : تظهر ما إذا كانت مجموعة نقاط النهاية مصنفة ك "تحسين" أو "سماح" أو "افتراضي". يمكنك قراءة هذه الفئات وإرشادات إدارتها في [فئات نقاط نهاية Office 365 الجديدة](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). يسرد هذا العمود أيضا مجموعات نقاط النهاية المطلوبة للاتصال بالشبكة. بالنسبة لمجموعات نقاط النهاية غير المطلوبة للاتصال بالشبكة، نوفر ملاحظات في هذا الحقل للإشارة إلى الوظائف التي قد تكون مفقودة إذا تم حظر مجموعة نقاط النهاية. إذا كنت تقوم باستبعاد منطقة خدمة بأكملها، فإن مجموعات نقاط النهاية المدرجة كمطلوبة لا تتطلب الاتصال.

- **ER** : هذا **نعم** إذا كانت مجموعة نقاط النهاية مدعومة عبر Azure ExpressRoute مع بادئات مسار Office 365. يتوافق مجتمع BGP الذي يتضمن بادئات المسار المعروضة مع منطقة الخدمة المدرجة. عندما تكون ER **لا**، فهذا يعني أن ExpressRoute غير معتمد لمجموعة نقاط النهاية هذه. ومع ذلك، لا يجب افتراض أنه لم يتم الإعلان عن مسارات لمجموعة نقاط نهاية حيث يكون ER **لا**.

- **عناوين**: تسرد أسماء مجالات FQDN أو أحرف البدل ونطاقات عناوين IP لمجموعة نقاط النهاية. لاحظ أن نطاق عنوان IP يكون بتنسيق CIDR وقد يتضمن العديد من عناوين IP الفردية في الشبكة المحددة.

- **المنافذ**: يسرد منافذ TCP أو UDP التي تم دمجها مع العناوين لتكوين نقطة نهاية الشبكة. قد تلاحظ وجود بعض التكرارات في نطاقات عناوين IP حيث توجد منافذ مختلفة مدرجة.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> للحصول على توصيات حول عناوين IP في Yammer وعناوين URL، راجع [استخدام عناوين IP المرمزة برمجيا لـ Yammer غير مستحسن](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592) على مدونة Yammer.

## <a name="related-topics"></a>المواضيع ذات الصلة

[نقاط النهاية الإضافية غير مضمنة في عنوان IP ل Office 365 وعنوان موقع ويب](additional-office365-ip-addresses-and-urls.md)

[إدارة نقاط نهاية Office 365](managing-office-365-endpoints.md)

[نقاط نهاية Microsoft Stream العامة](/stream/network-overview#general-microsoft-stream-endpoints)
  
[مراقبة اتصال Microsoft 365](./monitor-connectivity.md)

[شهادات الجذر وحزمة الشهادات المتوسطة على نظام تطبيقات الخارجي](../compliance/encryption-office-365-certificate-chains.md)
  
[اتصال العميل](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[شبكات تسليم المحتوى](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[نطاقات IP لـ Microsoft Azure وعلامات الخدمة – السحابة العامة](https://www.microsoft.com/download/details.aspx?id=56519)

[نطاقات IP وعلامات – الخدمة في Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=57063) السحابة الحكومية الأمريكية

[نطاقات IP وعلامات الخدمة في Microsoft Azure – السحابية في الصين](https://www.microsoft.com/download/details.aspx?id=57062) 
  
[ مساحة IP العامة في Microsoft ](https://www.microsoft.com/download/details.aspx?id=53602)

[سجل رقم منفذ بروتوكول النقل واسم الخدمة](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
