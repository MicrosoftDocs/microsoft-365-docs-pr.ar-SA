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
description: 'ملخص: Office 365 الاتصال بالإنترنت. يجب أن تكون نقاط النهاية أدناه قابلة للوصول للعملاء الذين يستخدمون Office 365، بما في ذلك سحابة القطاع الحكومي (سحابة القطاع الحكومي).'
hideEdit: true
ms.openlocfilehash: 04522b211056b1d7c6feba08dd97fc3a2d33451a
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634856"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>نطاقات عناوين IP وعناوين URL في Office 365

Office 365 الاتصال بالإنترنت. يجب أن تكون نقاط النهاية أدناه قابلة للوصول للعملاء الذين يستخدمون Office 365، بما في ذلك سحابة القطاع الحكومي (سحابة القطاع الحكومي).
  
*Office 365 حول العالم (+سحابة القطاع الحكومي)* \| Office 365 التي يتم تشغيلها بواسطة [21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| Office 365 [Government سحابة القطاع الحكومي High](microsoft-365-u-s-government-gcc-high-endpoints.md) \|

|ملاحظات|تنزيل|استخدام |
|---|---|---|
|**التحديث الأخير:** 03/28/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [تغيير اشتراك السجل](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**تنزيل:** كل الوجهات المطلوبة والاختيارية في [قائمة واحدة بتنسيق JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) .|**الاستخدام:** ملفات [PAC الوكيلة](managing-office-365-endpoints.md#pacfiles)|
|

ابدأ [بإدارة Office 365](managing-office-365-endpoints.md) نقاط النهاية لفهم توصياتنا لإدارة اتصال الشبكة باستخدام هذه البيانات. يتم تحديث بيانات نقاط النهاية حسب الحاجة في بداية كل شهر باستخدام عناوين IP وعناوين URL جديدة يتم نشرها قبل 30 يوما من أن تكون نشطا. يسمح هذا للعملاء الذين ليس لديهم تحديثات تلقائية بعد لإكمال عملياتهم قبل أن يكون الاتصال الجديد مطلوبا. قد يتم أيضا تحديث نقاط النهاية خلال الشهر إذا لزم الأمر لمعالجة تصاعدات الدعم أو الأحداث الأمنية أو متطلبات التشغيل الفورية الأخرى. يتم إنشاء كل البيانات المعروضة على هذه الصفحة أدناه من خدمات الويب المستندة إلى REST. إذا كنت تستخدم برنامج نصي أو جهاز شبكة للوصول إلى هذه البيانات، يجب الانتقال إلى خدمة [ويب مباشرة](microsoft-365-ip-web-service.md) .

تسرد بيانات نقطة النهاية أدناه متطلبات الاتصال من جهاز المستخدم Office 365. للحصول على تفاصيل حول عناوين IP المستخدمة لاتصالات الشبكة من Microsoft إلى شبكة عملاء، تسمى أحيانا اتصالات الشبكة المختلطة أو اتصالات الشبكة [](additional-office365-ip-addresses-and-urls.md) الواردة، راجع نقاط النهاية الإضافية للحصول على مزيد من المعلومات.

يتم تجميع نقاط النهاية في أربع مناطق خدمة تمثل أحمال العمل الأساسية الثلاثة، كما يتم تجميع مجموعة من الموارد المشتركة. يمكن استخدام المجموعات لاقتران تدفقات حركة المرور بتطبيق معين، ولكن نظرا إلى أن الميزات غالبا ما تستهلك نقاط النهاية عبر أحمال عمل متعددة، لا يمكن استخدام هذه المجموعات بفعالية لتقييد الوصول.

أعمدة البيانات المعروضة هي:

- **المعرف**: رقم المعرف للصف، المعروف أيضا ب مجموعة نقاط النهاية. هذا المرجع هو نفسه المرجع بواسطة خدمة الويب الخاصة بتعيين نقطة النهاية.

- **الفئة**: إظهار ما إذا كانت مجموعة نقاط النهاية مصنفة ك "تحسين" أو "السماح" أو "افتراضي". يمكنك قراءة هذه الفئات والإرشادات الخاصة بإدارتها في فئات نقاط [Office 365 نقاط النهاية الجديدة](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). يسرد هذا العمود أيضا مجموعات نقاط النهاية المطلوبة للحصول على اتصال الشبكة. بالنسبة إلى مجموعات نقاط النهاية غير المطلوبة لاتصال الشبكة، نوفر ملاحظات في هذا الحقل للإشارة إلى الوظائف التي قد تكون مفقودة إذا تم حظر مجموعة نقاط النهاية. إذا كنت تستبعد منطقة خدمة كاملة، فإن مجموعات نقاط النهاية المدرجة كما تقتضي الحاجة لا تتطلب اتصالا.

- **ER**: هذه هي **"نعم**" إذا كانت مجموعة نقاط النهاية معتمدة عبر Azure ExpressRoute مع Office 365 التوجيه. يحاذي مجتمع BGP الذي يتضمنبادات المسار المعروضة منطقة الخدمة المدرجة. عندما يكون **ER لا،** فهذا يعني أن ExpressRoute غير معتمد في مجموعة نقاط النهاية هذه. ومع ذلك، يجب عدم افتراض أنه لا يتم الإعلان عن أي مسارات مجموعة نقاط نهاية تكون فيها ER **لا**.

- **العناوين**: تسرد أسماء مجالات FQDN أو أحرف البدل ونطاقات عناوين IP لمجموعة نقاط النهاية. لاحظ أن نطاق عنوان IP بتنسيق CIDR وقد يتضمن العديد من عناوين IP الفردية في الشبكة المحددة.

- **المنافذ**: تسرد منافذ TCP أو UDP التي يتم دمجها مع العناوين لتشكيل نقطة نهاية الشبكة. قد تلاحظ بعض التكرار في نطاقات عناوين IP حيث توجد منافذ مختلفة مدرجة.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> للحصول على توصيات Yammer عناوين IP وعناوين URL، راجع استخدام عناوين IP ذات التعليمات البرمجية Yammer [غير](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592) مستحسن على المدونة Yammer.

## <a name="related-topics"></a>مواضيع ذات صلة

[نقاط النهاية الإضافية غير المضمنة في عنوان IP Office 365 URL وخدمة URL على الويب](additional-office365-ip-addresses-and-urls.md)

[إدارة نقاط نهاية Office 365](managing-office-365-endpoints.md)

[نقاط Microsoft Stream نقاط النهاية العامة](/stream/network-overview#general-microsoft-stream-endpoints)
  
[مراقبة Microsoft 365 الاتصال](./monitor-connectivity.md)

[مجموعة CA الجذر و CA الوسيطة على نظام التطبيق الخاص ب جهة خارجية](../compliance/encryption-office-365-certificate-chains.md)
  
[اتصال العميل](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[شبكات تسليم المحتوى](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[نطاقات IP والعلامات الخاصة ب Microsoft Azure – السحابة العامة](https://www.microsoft.com/download/details.aspx?id=56519)

[نطاقات IP والعلامات الخاصة ب Microsoft Azure – Us Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063)

[نطاقات IP والعلامات الخاصة ب Microsoft Azure – China Cloud](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Microsoft Public IP Space](https://www.microsoft.com/download/details.aspx?id=53602)

[سجل رقم المنفذ "اسم الخدمة" و"بروتوكول النقل"](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
