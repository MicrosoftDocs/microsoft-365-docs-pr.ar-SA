---
title: قدرات متعددة الجغرافيا في Microsoft Teams
ms.reviewer: daro
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
description: تعرف على كيفية Teams مع Microsoft 365 الجغرافيا المتعددة.
ms.openlocfilehash: 0315a9ff0429c5e00c662bd7345a3b6a39a591c3
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63571738"
---
# <a name="multi-geo-capabilities-in-microsoft-teams"></a>قدرات متعددة الجغرافيا في Microsoft Teams

تمكن قدرات "الجغرافيا Teams" Teams تخزين بيانات الدردشة في موقع جغرافي محدد. تتكون بيانات الدردشة من رسائل الدردشة، بما في ذلك الرسائل الخاصة ورسائل القناة والصور المستخدمة في الدردشات.

Teams موقع البيانات المفضلة (PDL) للمستخدمين والمجموعات لتحديد مكان تخزين البيانات. إذا لم يتم تعيين PDL أو إذا كان غير صالح، يتم تخزين البيانات في الموقع المركزي للمستأجر.

> [!NOTE]
> تم طرح قدرات متعددة الجغرافيا Teams في يوليو 2021. سيتم ترحيل رسائل الدردشة والقناة تلقائيا إلى الموقع الجغرافي الصحيح خلال أرباع السنة القليلة القادمة. وستعالج أي تغييرات PDL جديدة بعد أن يكمل المستأجر المزامنة الأولية، وستبقى تغييرات PDL الجديدة بعد ذلك في قائمة الانتظار وستعالج بالترتيب الذي يتم تلقيه.

## <a name="user-chat"></a>دردشة المستخدم

تتضمن دردشة المستخدم رسائل اجتماع واحد إلى واحد، ورسالة واحد إلى كثير، ورسائل اجتماعات خاصة.

عند إنشاء مستخدم جديد، يقوم Teams بقراءة PDL الخاص به وتخزين كل بيانات الدردشة الخاصة به في هذا الموقع الجغرافي.

بالنسبة للمستخدمين  الموجودين، إذا قام أحد المسؤولين بإضافة PDL أو تعديله لمستخدم، تضاف بيانات الدردشة الخاصة بهذا المستخدم إلى قائمة انتظار الترحيل لنقلها إلى الموقع الجغرافي المحدد.

يستند موقع التخزين لدردشة واحد إلى واحد أو واحد إلى أكثر إلى PDL للشخص الذي أنشأ الدردشة. إذا تم تغيير PDL الخاص بهذا المستخدم، سيتم ترحيل الدردشة إلى الموقع الجغرافي الجديد. يستند موقع تخزين دردشة الاجتماع إلى PDL لمنظم الاجتماع.

للعثور على الموقع الحالي لبيانات المستخدم Teams الاتصال Teams [PowerShell](/powershell/module/teams/connect-microsoftteams) وتشغيل الأمر التالي:

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

## <a name="channel-messages"></a>رسائل القناة

تحتوي Microsoft 365 المجموعة على موقع البيانات المفضل (PDL) الذي يشير إلى الموقع الجغرافي حيث سيتم تخزين البيانات ذات الصلة. Teams يستخدم هذا البرنامج PDL للمجموعة المقترنة بكل فريق لتحديد مكان تخزين بيانات مراسلة القناة لهذا الفريق. يشمل ذلك القنوات الخاصة والدردشة التي تحدث في اجتماع قناة.

عندما ينشئ مستخدم فريقا جديدا، يحدد PDL الخاص بهذا المستخدم ما تم تعيينه ل PDL Microsoft 365 المجموعة. يحدد PDL المجموعة مكان تخزين بيانات هذا الفريق. إذا تم تغيير PDL الخاص بهذا المستخدم في وقت لاحق، لن يتم تغيير PDL الخاص بهذه المجموعة.

بالنسبة للفرق الموجودة، إذا أضاف أحد المسؤولين أو عدل PDL لمجموعة Microsoft 365 التي دعمت فريقا، تضاف بيانات مراسلة القناة الخاصة بهذا الفريق إلى قائمة انتظار الترحيل لنقلها إلى الموقع الجغرافي المحدد.

يؤدي تغيير PDL الخاص Microsoft 365 المجموعة إلى Teams البيانات المطلوب ترحيلها إلى الموقع المحدد. ومع ذلك، لا يؤدي ذلك إلى ترحيل SharePoint أو الملفات المقترنة بالمجموعة تلقائيا. يجب نقل الموقع بشكل منفصل باتباع الإجراءات في نقل موقع SharePoint [إلى موقع جغرافي آخر](/microsoft-365/enterprise/move-sharepoint-between-geo-locations). تأكد من القيام بكل من الخطوات لتجنب Teams البيانات SharePoint مجموعة واحدة في مواقع مختلفة.

للعثور على الموقع الحالي لبيانات الفريق، اتصل Teams [PowerShell](/powershell/module/teams/connect-microsoftteams) ثم قم بتشغيل الأمر التالي:

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

## <a name="user-experience"></a>أسلوب عمل المستخدم

Teams تكون Multi-Geo سلسة للمستخدم. بمجرد تغيير PDL لمستخدم أو مجموعة، سيتم وضع البيانات الخاصة بها في قائمة الانتظار ل الترحيل، وستحدث عملية الترحيل تلقائيا بدون أي تأثير على المستخدم أو عميل Teams الخاص به حتى لو كان نشطا أثناء حدوث الترحيل.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 المستأجر متعدد الجغرافيا](/microsoft-365/enterprise/multi-geo-tenant-configuration)

[إدارة بيئة متعددة الجغرافيا](administering-a-multi-geo-environment.md)

[إدارة علب Exchange Online البريد في بيئة متعددة الجغرافيا](administering-exchange-online-multi-geo.md)
