---
title: Microsoft 365 متعدد المواقع الجغرافية
ms.reviewer: anfra
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: في هذه المقالة، تعرف على كيفية توسيع حالة حضورك في Microsoft 365 إلى مناطق جغرافية متعددة باستخدام Microsoft 365 Multi-Geo.
ms.openlocfilehash: 154082785b71be8fbba55e00e2df8a1a3eacb500
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490199"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 متعدد المواقع الجغرافية

باستخدام Microsoft 365 Multi-Geo، يمكن لمؤسستك توسيع وجودها في Microsoft 365 إلى مناطق جغرافية متعددة و/أو بلدان داخل المستأجر الحالي. تواصل مع فريق حساب Microsoft الخاص بك للتسجيل في شركتك متعددة الجنسيات ل Microsoft 365 Multi-Geo.
  
باستخدام Microsoft 365 Multi-Geo، يمكنك توفير وتخزين البيانات الثابتة في المواقع الجغرافية التي اخترتها لتلبية متطلبات موقع البيانات، وفي الوقت نفسه إطلاق تجارب الإنتاجية الحديثة العالمية الخاصة بك إلى القوى العاملة لديك.

للحصول على مقدمة فيديو حول Microsoft 365 Multi-Geo، راجع [SharePoint Online OneDrive Multi-Geo للتحكم في مكان وجود بياناتك](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>بنية متعددة المناطق الجغرافية

في بيئة متعددة المناطق الجغرافية، يتكون مستأجر Microsoft 365 من موقع مركزي (حيث تم توفير اشتراكك في Microsoft 365 في الأصل) وموقع قمر صناعي واحد أو أكثر. في مستأجر متعدد المناطق الجغرافية، يتم إتقان المعلومات حول المواقع الجغرافية والمجموعات ومعلومات المستخدم في Azure Active Directory (Azure AD). نظرا لأن معلومات المستأجر الخاص بك تتقن مركزيا وتتزامن مع كل موقع جغرافي، فإن المشاركة والتجارب التي يشارك فيها أي شخص من شركتك تحتوي على وعي عالمي.

![لقطة شاشة لخريطة متعددة المناطق الجغرافية من مركز إدارة SharePoint.](../media/multi-geo-world-map.png)

لاحظ أن Microsoft 365 Multi-Geo غير مصمم لتحسين الأداء، فقد تم تصميمه لتلبية متطلبات موقع البيانات. للحصول على معلومات حول تحسين الأداء ل Microsoft 365، راجع [تخطيط الشبكة وضبط الأداء ل Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) أو اتصل بمجموعة الدعم.

## <a name="terminology"></a>المصطلحات

فيما يلي المصطلحات الرئيسية المستخدمة في وصف Microsoft 365 Multi-Geo:

- **الموقع المركزي** - الموقع الجغرافي حيث تم توفير المستأجر الخاص بك في الأصل.
- **المسؤول الجغرافي** - مسؤول يمكنه إدارة موقع أو أكثر من مواقع الأقمار الصناعية المحددة.
- **الرمز الجغرافي** - رمز مكون من ثلاثة أحرف لموقع جغرافي معين.
- **الموقع الجغرافي** - موقع جغرافي يمكن استخدامه في مستأجر متعدد المناطق الجغرافية لاستضافة البيانات، بما في ذلك علب بريد Exchange ومواقع OneDrive وSharePoint.
- **موقع البيانات المفضل (PDL)** – خاصية مستخدم معينة من قبل المسؤول تشير إلى الموقع الجغرافي حيث يجب توفير علبة بريد Exchange وOneDrive للمستخدمين. تحدد PDL أيضا مكان توفير مواقع SharePoint التي تم إنشاؤها بواسطة المستخدم.
- **موقع القمر الصناعي** - المواقع الجغرافية حيث يتم تمكين أحمال عمل Microsoft 365 المدركة جغرافيا (SharePoint وOneDrive وExchange) في مستأجر متعدد المناطق الجغرافية.
- **المستأجر** – تمثيل المؤسسة في Microsoft 365 الذي يتضمن عادة مجالا واحدا أو أكثر مقترنا به (على سبيل المثال، contoso.com).

## <a name="licensing"></a>الترخيص

يتوفر Microsoft 365 Multi-Geo كوظيفة إضافية لخطط اشتراك Microsoft 365 التالية لعملاء اتفاقية Enterprise مع ما لا يقل عن 250 مقعد Microsoft 365 في المستأجر الخاص بهم، وما لا يقل عن 5٪ من هذه المقاعد باستخدام المناطق الجغرافية المتعددة. يجب أن تكون تراخيص اشتراك المستخدم على نفس اتفاقية Enterprise مثل تراخيص الخدمات الجغرافية المتعددة. الرجاء الاتصال بفريق حساب Microsoft للحصول على التفاصيل.

- Microsoft 365 F1 أو F3 أو E3 أو E5
- Office 365 F3 أو E1 أو E3 أو E5
- Exchange Online الخطة 1 أو الخطة 2
- OneDrive for Business الخطة 1 أو الخطة 2
- الخطة 1 أو الخطة 2 في SharePoint Online

إذا تم تعيين ترخيص لمستخدم وتمت إزالته لاحقا، يتم وضع بيانات دردشة مستخدم Teams في قائمة الانتظار ليتم نقلها مرة أخرى إلى الموقع المركزي. لم يتم نقل بيانات SharePoint وExchange.

## <a name="microsoft-365-multi-geo-availability"></a>توفر Microsoft 365 Multi-Geo

يتوفر Microsoft 365 Multi-Geo حاليا في هذه المناطق والبلدان:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>بدء الاستخدام

اتبع هذه الخطوات لبدء الاستخدام الجغرافي المتعدد:

1. اعمل مع فريق حسابك لإضافة _الإمكانات متعددة المناطق الجغرافية في خطة خدمة Microsoft 365_ . سوف ترشدك لإضافة عدد التراخيص المطلوبة. تتوفر ميزة Multi-Geo لعملاء EA الذين لديهم ما لا يقل عن 250 اشتراك Microsoft 365.

   قبل أن تتمكن من البدء في استخدام Microsoft 365 Multi-Geo، تحتاج Microsoft إلى تكوين مستأجر Exchange Online للحصول على دعم متعدد المناطق الجغرافية. يتم تشغيل عملية التكوين هذه لمرة واحدة بعد طلب *الإمكانات متعددة المناطق الجغرافية في خطة خدمة Microsoft 365* وتظهر التراخيص في المستأجر الخاص بك. ستتلقى إعلامات خاصة بحمل العمل في [مركز رسائل Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) بمجرد أن يكمل المستأجر عملية التكوين لكل حمل عمل، وقد تبدأ بعد ذلك في تكوين قدرات Microsoft 365 Multi-Geo واستخدامها. يختلف الوقت المطلوب لتكوين مستأجر للدعم متعدد المناطق الجغرافية من مستأجر إلى مستأجر، ولكن ينتهي معظم المستأجرين في غضون شهر بعد استلام تراخيص الميزات. قد يتطلب المستأجرون الأكبر أو الأكثر تعقيدا المزيد من الوقت لإكمال عملية التكوين. يرجى الاتصال بفريق حسابك للحصول على تفاصيل حول المستأجر المحدد إذا كنت بحاجة إليه.

2. اقرأ [تخطيط بيئتك متعددة المناطق الجغرافية](plan-for-multi-geo.md).

3. تعرف على [إدارة بيئة متعددة المناطق الجغرافية](administering-a-multi-geo-environment.md) [وكيف سيختبر المستخدمون البيئة](multi-geo-user-experience.md).

4. عندما تكون جاهزا لإعداد Microsoft 365 Multi-Geo، [قم بتكوين المستأجر الخاص بك للجغرافيا المتعددة](multi-geo-tenant-configuration.md).

5. [إعداد البحث](configure-search-for-multi-geo.md).

## <a name="see-also"></a>راجع أيضًا

[Multi-Geo in Exchange Online وOneDrive](https://Aka.ms/GoMultiGeo)

[الإمكانات متعددة المناطق الجغرافية في OneDrive وSharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[قدرات جغرافية متعددة في Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[تجربة Teams في بيئة متعددة المناطق الجغرافية](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
