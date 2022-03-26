---
title: Microsoft 365 الجغرافيا المتعددة
ms.reviewer: adwood
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
description: في هذه المقالة، تعرف على كيفية توسيع Microsoft 365 الجغرافيا المتعددة مع Microsoft 365 الجغرافيا المتعددة.
ms.openlocfilehash: 5122979fc79ce9aebe542a80ed614e7dcad70d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568978"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 الجغرافيا المتعددة

باستخدام Microsoft 365 Multi-Geo، يمكن لمنظمتك توسيع Microsoft 365 الجغرافيا المتعددة و/أو البلدان ضمن نطاق المستأجر الحالي. التواصل مع فريق حساب Microsoft الخاص بك من أجل التسجيل في شركتك متعددة القوميات Microsoft 365 Multi-Geo.
  
باستخدام Microsoft 365 الجغرافيا المتعددة، يمكنك توفير البيانات وتخزينها في المواقع الجغرافية التي اخترتها لتلبية متطلبات الإقامة الخاصة بالبيانات، وفي الوقت نفسه إلغاء تأمين طرحك العام لتجارب الإنتاجية الحديثة للقوى العاملة لديك.

للحصول على مقدمة فيديو Microsoft 365 Multi-Geo، راجع SharePoint عبر الإنترنت [OneDrive Multi-Geo للتحكم في مكان وجود بياناتك](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>هندسة متعددة الجغرافيا

في بيئة Multi-Geo، يتكون Microsoft 365 المستأجر الخاص بك من موقع مركزي (حيث تم توفير اشتراكك في Microsoft 365 في الأصل) وموقع أقمار صناعية واحد أو أكثر. في المستأجر الجغرافي المتعدد، يتم إتقان المعلومات حول المواقع الجغرافية والمجموعات ومعلومات المستخدم في Azure Active Directory (Azure AD). نظرا لأن معلومات المستأجر الخاصة بك يتم إتقانها مركزيا ومزامنتها في كل موقع جغرافي، فإن المشاركة والتجارب التي يشارك فيها أي شخص من شركتك تحتوي على الوعي العام.

![لقطة شاشة لخريطة متعددة الجغرافيا من SharePoint إدارة الموقع.](../media/multi-geo-world-map.png)

تجدر الإشارة Microsoft 365 لم يتم تصميم Multi-Geo لتحسين الأداء، بل تم تصميمه لتلبية متطلبات الإقامة الخاصة بالبيانات. للحصول على معلومات حول تحسين الأداء Microsoft 365، راجع تخطيط الشبكة [وتحسين](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) الأداء Microsoft 365 أو الاتصال ب مجموعة الدعم.

## <a name="terminology"></a>المصطلحات

فيما يلي المصطلحات الأساسية المستخدمة في وصف Microsoft 365 الجغرافيا المتعددة:

- **الموقع المركزي** - الموقع الجغرافي حيث تم توفير المستأجر في الأصل.
- **مسؤول الموقع** الجغرافي - مسؤول يمكنه إدارة موقع واحد أو أكثر من مواقع الأقمار الصناعية المحددة.
- **التعليمات** البرمجية الجغرافية - رمز من ثلاثة حروف لموقع جغرافي معين.
- **الموقع الجغرافي** – موقع جغرافي يمكن استخدامه في مستأجر متعدد المواقع الجغرافية لاستضافة البيانات، بما في ذلك Exchange علب البريد OneDrive SharePoint المواقع.
- **موقع البيانات المفضل (PDL)** – خاصية مستخدم تم تعيينها من قبل المسؤول تشير إلى موقع الموقع الجغرافي الذي Exchange علبة البريد OneDrive المستخدمين. يحدد PDL أيضا SharePoint المواقع التي أنشأها المستخدم.
- **موقع القمر** الصناعي – يتم تمكين المواقع الجغرافية التي Microsoft 365 الجغرافيا (SharePoint و OneDrive و Exchange) في مستأجر متعدد الجغرافيا.
- **المستأجر** – تمثيل المؤسسة في Microsoft 365 يكون عادة فيه مجال واحد أو أكثر مقترن بها (على سبيل المثال، contoso.com).

## <a name="licensing"></a>الترخيص

Microsoft 365 تتوفر Multi-Geo كعناية إضافية لخطط اشتراك Microsoft 365 التالية لعملاء اتفاقية Enterprise مع ما لا يقل عن 250 Microsoft 365 مقعد في المستأجر، وما لا يقل عن 5٪ من تلك المقاعد باستخدام الموقع الجغرافي المتعدد. يجب أن تكون تراخيص اشتراك المستخدمين في نفس اتفاقية Enterprise تراخيص الخدمات الجغرافية المتعددة. يرجى الاتصال بفريق حساب Microsoft للحصول على التفاصيل.

- Microsoft 365 F1 أو F3 أو E3 أو E5
- Office 365 F3 أو E1 أو E3 أو E5
- Exchange Online الخطة 1 أو الخطة 2
- OneDrive for Business الخطة 1 أو الخطة 2
- SharePoint عبر الإنترنت الخطة 1 أو الخطة 2

إذا تم تعيين ترخيص لمستخدم وأزيل في وقت لاحق، Teams بيانات دردشة المستخدم في قائمة الانتظار لنقلها مرة أخرى إلى الموقع المركزي. SharePoint نقل Exchange البيانات.

## <a name="microsoft-365-multi-geo-availability"></a>Microsoft 365 متعدد الجغرافيا

Microsoft 365 Multi-Geo حاليا في هذه المناطق والبلدان:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>بدء الاستخدام

اتبع هذه الخطوات للبدء باستخدام الموقع الجغرافي المتعدد:

1. العمل مع فريق حسابك لإضافة القدرات الجغرافية المتعددة _في Microsoft 365_ الخدمة. وسترشدك لإضافة عدد التراخيص المطلوبة. تتوفر ميزة Multi-Geo لعملاء EA مع ما لا يقل عن 250 Microsoft 365 اشتراك.

   قبل أن تتمكن من بدء استخدام Microsoft 365 الجغرافيا المتعددة، تحتاج Microsoft إلى تكوين Exchange Online المستأجر الخاص بك للحصول على دعم متعدد الجغرافيا. يتم تشغيل عملية التكوين هذه مرة واحدة بعد طلب "قدرات متعددة الجغرافيا" في Microsoft 365 الخدمة وتظهر التراخيص في المستأجر. ستتلقى إعلامات خاصة بأحمال العمل في مركز رسائل [Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) بمجرد أن يكمل المستأجر عملية التكوين لكل حمل عمل عمل، ومن ثم قد تبدأ في تكوين قدرات Microsoft 365 الجغرافيا المتعددة واستخدامها. يختلف الوقت المطلوب لتكوين مستأجر لدعم Multi-Geo من مستأجر إلى مستأجر، ولكن ينتهي معظم المستأجرين في غضون شهر بعد استلام تراخيص الميزات. قد يتطلب المستأجرون الأكبر أو الأكثر تعقيدا مزيدا من الوقت لإكمال عملية التكوين. يرجى الاتصال بفريق حسابك للحصول على تفاصيل حول المستأجر المحدد الذي تحتاج إلى ذلك.

2. اقرأ [تخطيط بيئتك الجغرافية المتعددة](plan-for-multi-geo.md).

3. تعرف على [كيفية إدارة بيئة متعددة الجغرافيا](administering-a-multi-geo-environment.md) [وكيفية تجربة المستخدمين لها](multi-geo-user-experience.md).

4. عندما تكون جاهزا لإعداد موقع Microsoft 365 الجغرافيا المتعددة، قم [بتكوين المستأجر الخاص بك لعدد الجغرافيا](multi-geo-tenant-configuration.md).

5. [إعداد البحث](configure-search-for-multi-geo.md).

## <a name="see-also"></a>راجع أيضًا

[Multi-Geo في Exchange Online OneDrive](https://Aka.ms/GoMultiGeo)

[قدرات متعددة الجغرافيا في OneDrive SharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[قدرات متعددة الجغرافيا في Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[Teams في بيئة متعددة الجغرافيا](/microsoftteams/teams-experience-o365odb-spo-multi-geo)