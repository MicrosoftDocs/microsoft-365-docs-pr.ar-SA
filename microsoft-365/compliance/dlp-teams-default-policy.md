---
title: تعرف على نهج DLP الافتراضي في Microsoft Teams (معاينة)
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
ms.openlocfilehash: 5c3a5a116da90a41abcc459808e83176dc750fe1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624212"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>تعرّف على نهج منع فقدان البيانات الافتراضي في Microsoft Teams (معاينة)

تم توسيع [قدرات تفادي فقدان البيانات في Microsoft Purview](dlp-learn-about-dlp.md) لتشمل رسائل الدردشة والقنوات في Microsoft Teams، بما في ذلك رسائل القناة الخاصة. كجزء من هذا الإصدار، أنشأنا نهج DLP افتراضيا لعملاء Microsoft Teams لأول مرة <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">في مدخل التوافق في Microsoft Purview</a>.

## <a name="licensing"></a>الترخيص

للحصول على معلومات الترخيص الكاملة ل DLP في Microsoft Teams، راجع [حماية البيانات: منع فقدان البيانات ل Teams](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>ماذا يفعل النهج الافتراضي؟

يتعقب نهج DLP الافتراضي ل Teams جميع أرقام بطاقات الائتمان المشتركة داخليا وخارجيا مع المؤسسة. يتم تشغيل هذا النهج بشكل افتراضي لكافة مستخدمي المستأجر. لا ينشئ أي تلميحات نهج للمستخدمين النهائيين ولكنه ينشئ حدث تنبيه، كما أنه يشغل بريدا إلكترونيا منخفض الخطورة إلى المسؤول (مضاف في النهج). يمكن للمسؤول عرض الأنشطة وتحرير تفاصيل النهج عن طريق تسجيل الدخول إلى مركز التوافق.

يمكن للمسؤولين عرض هذا النهج في صفحة [نهج منع فقدان البيانات > مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com/compliancesettings).


> [!div class="mx-imgBorder"]
> ![نهج DLP الافتراضي ل Teams.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>تحرير النهج الافتراضي أو حذفه

[لتحرير النهج الافتراضي للحصول على أداء أفضل أو لحذفه](create-test-tune-dlp-policy.md#tune-a-dlp-policy)، ما عليك سوى استخدام حساب مع أذونات **DLP Compliance Management**. لمزيد من المعلومات، راجع [الأذونات](create-test-tune-dlp-policy.md#permissions).

