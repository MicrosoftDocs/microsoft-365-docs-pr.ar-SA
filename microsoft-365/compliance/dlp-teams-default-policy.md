---
title: تعرف على نهج منع فقدان البيانات الافتراضي في Microsoft Teams (معاينة)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: تعرف على نهج منع فقدان البيانات الافتراضي في Microsoft Teams
ms.openlocfilehash: 61443cdfdc116e9c25d9dad24c968876ae5d0349
ms.sourcegitcommit: db2ed146b46ade9ea62eed9cb8efff5fea7a35e6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/26/2022
ms.locfileid: "64481353"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>تعرف على نهج منع فقدان البيانات الافتراضي في Microsoft Teams (معاينة)

[تم توسيع إمكانات](dlp-learn-about-dlp.md) منع فقدان البيانات لتتضمن Microsoft Teams رسائل الدردشة والقنوات، بما في ذلك رسائل القناة الخاصة. وكجزء من هذا الإصدار، قمنا بإنشاء نهج DLP افتراضي Microsoft Teams للعملاء لأول مرة <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365.</a>

## <a name="licensing"></a>الترخيص

للحصول على معلومات الترخيص الكاملة ل DLP في Microsoft Teams، راجع حماية البيانات[: منع فقدان البيانات Teams](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>ما الذي يقوم به النهج الافتراضي؟

يتعقب نهج DLP الافتراضي Teams كل أرقام بطاقات الائتمان المشتركة داخليا وخارجيا إلى المؤسسة. يتم بشكل افتراضي تعيين هذا النهج لجميع مستخدمي المستأجر. ولا ينشئ أي تلميحات نهج للمستخدمين، ولكنه ينشئ حدث تنبيه ويشغل أيضا رسالة بريد إلكتروني منخفضة الخطورة إلى المسؤول (مضاف في النهج). يمكن للمسؤول عرض الأنشطة وتحرير تفاصيلها من خلال تسجيل الدخول إلى مركز التوافق.

يمكن للمسؤولين عرض هذا النهج في مركز التوافق [>](https://compliance.microsoft.com/compliancesettings) نهج منع فقدان البيانات.


> [!div class="mx-imgBorder"]
> ![نهج Teams DLP الافتراضي.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>تحرير النهج الافتراضي أو حذفه

لتحرير [النهج الافتراضي للحصول على أداء أفضل أو لحذفه](create-test-tune-dlp-policy.md#tune-a-dlp-policy)، ما عليك سوى استخدام حساب مع أذونات **إدارة توافق DLP** . لمزيد من المعلومات، راجع [الأذونات](create-test-tune-dlp-policy.md#permissions).

