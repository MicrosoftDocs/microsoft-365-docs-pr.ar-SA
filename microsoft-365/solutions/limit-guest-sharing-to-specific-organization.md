---
title: تقييد المشاركة مع الضيوف لتقتصر على مؤسسات معينة
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
description: تعرف على كيفية قصر مشاركة الضيف على Azure AD معينة أو مؤسسات Microsoft 365.
ms.openlocfilehash: 75cfe739e1cdde2e0bd959382b2444487ea726be
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/22/2022
ms.locfileid: "66857186"
---
# <a name="limit-guest-sharing-to-specific-organizations"></a>تقييد المشاركة مع الضيوف لتقتصر على مؤسسات معينة

بشكل افتراضي، يمكن للمستخدمين دعوة أشخاص من خارج المؤسسة كضيوف. يشمل ذلك دعوتهم إلى فرق في Microsoft Team ومواقع SharePoint ومشاركة الملفات والمجلدات الفردية معهم.

إذا كنت تريد فقط أن يقوم المستخدمون بدعوة ضيوف من مؤسسات معينة، يمكنك تحديد هذه المؤسسات في إعدادات الوصول عبر المستأجرين عبر Azure Active Directory [لتعاون B2B](/azure/active-directory/external-identities/what-is-b2b).

## <a name="configure-cross-tenant-access-settings"></a>تكوين إعدادات الوصول عبر المستأجرين

الخطوة الأولى في الحد من مشاركة الضيف هي تغيير الإعدادات الافتراضية في Azure AD إعدادات الوصول عبر المستأجرين لحظر دعوة الضيوف بشكل افتراضي. ثم يمكنك السماح بدعوة الضيوف لمؤسسات معينة.

> [!NOTE]
> قد تستغرق التغييرات التي يتم إجراؤها على إعدادات الوصول عبر المستأجرين ساعتين حتى يتم تفعيلها.

### <a name="set-the-default-b2b-collaboration-settings-to-block-inviting-guests"></a>تعيين إعدادات تعاون B2B الافتراضية لحظر دعوة الضيوف

نظرا لتمكين دعوة الضيوف بشكل افتراضي، فإن تحديد دعوات الضيوف إلى مؤسسات معينة يتطلب حظر تعاون B2B الوارد بشكل افتراضي.

لحظر تعاون B2B الوارد بشكل افتراضي
1. سجل الدخول إلى [Azure Active Directory](https://aad.portal.azure.com) باستخدام حساب مسؤول глобальный администратор أو مسؤول الأمان.
1. Select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. حدد علامة التبويب **الإعدادات الافتراضية** .
1. ضمن **إعدادات الوصول الوارد**، حدد **"تحرير الإعدادات الافتراضية الواردة**".
1. حدد علامة التبويب **تعاون B2B** وعلامة التبويب **"المستخدمون والمجموعات** ".
1. ضمن **حالة Access**، اختر **"حظر الوصول**".
1. حدد علامة تبويب **الوصول الخارجي** .
1. ضمن **حالة Access**، اختر **"حظر الوصول**".
1. حدد **حفظ**.
1. أغلق جزء **الإعدادات الافتراضية** .

### <a name="add-the-organization-where-you-want-to-allow-guest-invitations"></a>إضافة المؤسسة حيث تريد السماح بدعوة الضيوف

بعد ذلك، أضف المؤسسات حيث تريد السماح للمستخدمين بدعوة الضيوف إلى قائمة الوصول عبر المستأجرين Azure AD.

لإضافة مؤسسة
1. In [Azure Active Directory](https://aad.portal.azure.com), select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. حدد **إعدادات المؤسسة**.
1. حدد **"إضافة مؤسسة**".
1. في الجزء **"إضافة مؤسسة** "، اكتب اسم المجال الكامل (أو معرف المستأجر) للمؤسسة.
1. حدد المؤسسة في نتائج البحث، ثم حدد **"إضافة**".
1. تظهر المؤسسة في قائمة **إعدادات المؤسسة** .

في هذه المرحلة، يتم توريث كافة إعدادات الوصول لهذه المؤسسة من إعداداتك الافتراضية.

### <a name="configure-inbound-settings-for-the-organization-to-allow-all-users"></a>تكوين الإعدادات الواردة للمؤسسة للسماح لكافة المستخدمين

بمجرد إضافة المؤسسة، تحتاج إلى تحديث الإعدادات الواردة للمؤسسة للسماح بدعوة مستخدمي تعاون B2B كضيوف. قم بذلك لكل مؤسسة حيث تريد السماح للمستخدمين بأن يكونوا قادرين على دعوة الضيوف.

1. In [Azure Active Directory](https://aad.portal.azure.com), select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. حدد ارتباط الوصول الوارد للمؤسسة التي تريد تعديلها.
1. في علامة التبويب **تعاون B2B** ، اختر **"تخصيص الإعدادات**".
1. ضمن **حالة Access**، اختر **"السماح بالوصول**".
1. ضمن **Target**، اختر السماح لكافة المستخدمين.
1. حدد **"Save** and close the **Outbound access settings blade** ".

## <a name="turn-off-one-time-passcode-authentication"></a>إيقاف تشغيل مصادقة رمز المرور لمرة واحدة

حتى بعد تقييد تعاون B2B مع مؤسسات معينة، لا يزال بإمكان الأشخاص مشاركة الملفات والمجلدات مع أشخاص في مؤسسات أخرى - لن يتم منحهم حساب ضيف في دليلك.

إذا كنت ترغب في منع المشاركة بالكامل مع المؤسسات الأخرى، يجب تعطيل ميزة رمز المرور لمرة واحدة في Azure AD. سيؤدي ذلك إلى منع الأشخاص من خارج مؤسستك من إرسال رمز مرور لمرة واحدة للمصادقة إلى الملفات أو المجلدات المشتركة.

لتعطيل ميزة رمز المرور لمرة واحدة للبريد الإلكتروني
1. سجل الدخول إلى [Azure-Portal](https://portal.azure.com/) كمسؤول عام Azure AD.
1. في جزء التنقل، حدد **Azure Active Directory**.
1. حدد **الهويات** >  الخارجية **كافة موفري الهوية**.
1. حدد **رمز المرور "بريد إلكتروني لمرة واحدة**"، ثم ضمن **"البريد الإلكتروني" رمز المرور لمرة واحدة للضيوف**، حدد **"تعطيل رمز المرور لمرة واحدة للبريد الإلكتروني" للضيوف** (أو **"لا** " إذا تم تمكين الميزة مسبقا أو تعطيلها أو الاشتراك فيها أثناء المعاينة).
1. حدد **حفظ**.

## <a name="related-topics"></a>المواضيع ذات الصلة

[نظرة عامة على الاتصال المباشر B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[تكوين إعدادات الوصول عبر المستأجرين للاتصال المباشر B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[تقييد الأشخاص الذين يمكن دعوتهم من قبل مؤسسة](limit-invitations-from-specific-organization.md)

[تقييد المؤسسات التي يمكن للمستخدمين الحصول على حسابات الضيوف فيها](limit-organizations-where-users-have-guest-accounts.md)