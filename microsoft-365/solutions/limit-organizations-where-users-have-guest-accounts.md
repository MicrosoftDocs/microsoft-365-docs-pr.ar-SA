---
title: تقييد المؤسسات التي يمكن للمستخدمين الحصول على حسابات الضيوف فيها
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: تعرف على كيفية تحديد المؤسسات التي يمكن للمستخدمين لديك الحصول على حسابات الضيوف فيها.
ms.openlocfilehash: 00db14560c491461435e41e30c106c2554d9ad61
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/22/2022
ms.locfileid: "66857181"
---
# <a name="limit-organizations-where-users-can-have-guest-accounts"></a>تقييد المؤسسات التي يمكن للمستخدمين الحصول على حسابات الضيوف فيها

بشكل افتراضي، يمكن لمؤسسات Microsoft 365 وAzure Active Directory الأخرى دعوة المستخدمين للمشاركة في مؤسستهم كضيوف. يشمل ذلك دعوتهم إلى فرق في Microsoft Team ومواقع SharePoint ومشاركة الملفات والمجلدات الفردية معهم.

إذا كنت تريد فقط أن يشارك المستخدمون كضيوف مع مؤسسات معينة، يمكنك تحديد هذه المؤسسات في إعدادات الوصول عبر المستأجرين عبر Azure Active Directory [لتعاون B2B](/azure/active-directory/external-identities/what-is-b2b).

> [!NOTE]
> قد تستغرق التغييرات التي يتم إجراؤها على إعدادات الوصول عبر المستأجرين ساعتين حتى يتم تفعيلها.

## <a name="set-the-default-b2b-collaboration-settings-to-block-users-from-being-guests"></a>تعيين إعدادات تعاون B2B الافتراضية لمنع المستخدمين من أن يكونوا ضيوفا

نظرا لتمكين المشاركة كضيوف بشكل افتراضي، فإن تقييد مشاركة الضيف في مؤسسات معينة يتطلب حظر تعاون B2B الصادر بشكل افتراضي.

لحظر تعاون B2B الصادر بشكل افتراضي
1. سجل الدخول إلى [Azure Active Directory](https://aad.portal.azure.com) باستخدام حساب مسؤول глобальный администратор أو مسؤول الأمان.
1. Select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. حدد علامة التبويب **الإعدادات الافتراضية** .
1. ضمن **إعدادات الوصول الصادر**، حدد **تحرير الإعدادات الافتراضية الصادرة**.
1. حدد علامة التبويب **تعاون B2B** وعلامة التبويب **"المستخدمون والمجموعات** ".
1. ضمن **حالة Access**، اختر **"حظر الوصول**".
1. حدد علامة تبويب **الوصول الخارجي** .
1. ضمن **حالة Access**، اختر **"حظر الوصول**".
1. حدد **حفظ**.
1. أغلق جزء **الإعدادات الافتراضية** .

## <a name="add-an-organization"></a>إضافة مؤسسة

بعد ذلك، أضف المؤسسات حيث تريد السماح للمستخدمين بالتعاون كضيوف في قائمة الوصول عبر المستأجرين Azure AD.

لإضافة مؤسسة
1. In [Azure Active Directory](https://aad.portal.azure.com), select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. حدد **إعدادات المؤسسة**.
1. حدد **"إضافة مؤسسة**".
1. في الجزء **"إضافة مؤسسة** "، اكتب اسم المجال الكامل (أو معرف المستأجر) للمؤسسة.
1. حدد المؤسسة في نتائج البحث، ثم حدد **"إضافة**".
1. تظهر المؤسسة في قائمة **إعدادات المؤسسة** .

في هذه المرحلة، يتم توريث كافة إعدادات الوصول لهذه المؤسسة من إعداداتك الافتراضية.

## <a name="configure-the-organizations-outbound-setting-to-allow-all-users"></a>تكوين الإعداد الصادر للمؤسسة للسماح لكافة المستخدمين

بمجرد إضافة المؤسسة، تحتاج إلى تحديث الإعدادات الصادرة للمؤسسة للسماح بإضافة مستخدمي تعاون B2B كضيوف. قم بذلك لكل مؤسسة حيث تريد السماح بإضافة المستخدمين كضيوف.

للسماح للمستخدمين بضيوف تعاون B2B في مؤسسة
1. In [Azure Active Directory](https://aad.portal.azure.com), select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. حدد ارتباط الوصول الصادر للمؤسسة التي تريد تعديلها.
1. في علامة التبويب **تعاون B2B** ، اختر **"تخصيص الإعدادات**".
1. ضمن **حالة Access**، اختر **"السماح بالوصول**".
1. ضمن **Target**، اختر السماح لكافة المستخدمين.
1. حدد **"Save** and close the **Outbound access settings blade** ".

## <a name="related-topics"></a>المواضيع ذات الصلة

[نظرة عامة على الاتصال المباشر B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[تكوين إعدادات الوصول عبر المستأجرين للاتصال المباشر B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[تقييد الأشخاص الذين يمكن دعوتهم من قبل مؤسسة](limit-invitations-from-specific-organization.md)

[تقييد المشاركة مع الضيوف لتقتصر على مؤسسات معينة](limit-guest-sharing-to-specific-organization.md)