---
title: تمكين القنوات المشتركة مع كافة المؤسسات الخارجية
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
description: تعرف على كيفية تمكين القنوات المشتركة مع جميع مؤسسات Microsoft 365 وAzure Active Directory الأخرى.
ms.openlocfilehash: 601bfaa825afdaf9ec5addb4b7c7e21804b07cb7
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/22/2022
ms.locfileid: "66857182"
---
# <a name="enable-shared-channels-with-all-external-organizations"></a>تمكين القنوات المشتركة مع كافة المؤسسات الخارجية

بينما يتم تمكين مشاركة القنوات المشتركة خارجيا بشكل افتراضي في Teams، يجب أيضا تكوين إعدادات الوصول عبر المستأجرين في Azure Active Directory [للاتصال المباشر B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview) لمشاركة قناة خارجيا. بشكل افتراضي، يتم تعيين هذه الإعدادات لحظر كافة المؤسسات.

يمكنك تغيير الإعدادات الافتراضية للاتصال المباشر B2B للسماح لكافة المؤسسات. يسمح هذا للمستخدمين بالتعاون في القنوات المشتركة دون الحاجة إلى إنشاء تكوين منفصل لكل مؤسسة تريد التعاون معها. (لاحظ أن المؤسسات التي تتعاون معها سيتعين عليها أيضا تكوين إعدادات الاتصال المباشر ل B2B.)

إذا لم يكن لدى مؤسستك متطلبات لتقييد التعاون مع المؤسسات الأخرى، فإن تمكين جميع المؤسسات بشكل افتراضي يمكن أن يوفر لك الوقت والتعقيد في إدارة كل مؤسسة على حدة.

> [!NOTE]
> قد تستغرق التغييرات التي يتم إجراؤها على إعدادات الوصول عبر المستأجرين ساعتين حتى يتم تفعيلها.

## <a name="allow-users-to-invite-people-in-other-organizations-to-participate-in-shared-channels"></a>السماح للمستخدمين بدعوة أشخاص في مؤسسات أخرى للمشاركة في القنوات المشتركة

يمكنك السماح للمستخدمين بدعوة أشخاص من مؤسسات أخرى لاستخدام الموارد المشتركة - مثل القنوات المشتركة في Teams - بشكل افتراضي.

للسماح للمستخدمين بدعوة المشاركين في الاتصال المباشر B2B بشكل افتراضي
1. سجل الدخول إلى [Azure Active Directory](https://aad.portal.azure.com) باستخدام حساب مسؤول глобальный администратор أو مسؤول الأمان.
1. Select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. في علامة التبويب **"إعدادات افتراضية** "، ضمن **إعدادات الوصول الوارد**، حدد **"تحرير الإعدادات الافتراضية الواردة**".
1. حدد علامة تبويب **الاتصال المباشر B2B** .
1. ضمن علامة التبويب **"المستخدمون والمجموعات** "، ضمن **حالة Access**، اختر **"السماح بالوصول**".
1. ضمن علامة التبويب **"تطبيقات خارجية** "، ضمن **حالة Access**، اختر **"السماح بالوصول**".
1. حدد **حفظ**.
1. حدد علامة التبويب **"إعدادات الثقة** ".
1. اختر ما إذا كنت تريد الوثوق بالمصادقة متعددة العوامل أو الأجهزة المتوافقة أو الأجهزة المختلطة Azure AD المنضمة من مؤسسات أخرى.
1. حدد **حفظ**.
1. أغلق جزء **الإعدادات الافتراضية** .

## <a name="allow-users-to-participate-in-shared-channels-in-other-organizations"></a>السماح للمستخدمين بالمشاركة في القنوات المشتركة في مؤسسات أخرى

يمكنك السماح للمستخدمين بالوصول إلى الموارد التي تستضيفها مؤسسة خارجية - مثل القنوات المشتركة في Teams - بشكل افتراضي.

للسماح للمستخدمين بالوصول إلى الموارد من مؤسسات أخرى بشكل افتراضي
1. In [Azure Active Directory](https://aad.portal.azure.com), select **External Identities**, and then select **Cross-tenant access settings (preview)**.
1. في علامة التبويب **"إعدادات افتراضية** "، ضمن **إعدادات الوصول الصادر**، حدد **"تحرير الإعدادات الافتراضية الصادرة**".
1. حدد علامة تبويب **الاتصال المباشر B2B** .
1. ضمن علامة التبويب **"المستخدمون والمجموعات** "، ضمن **حالة Access**، اختر **"السماح بالوصول**".
1. ضمن علامة التبويب **"تطبيقات خارجية** "، ضمن **حالة Access**، اختر **"السماح بالوصول**".
1. حدد **حفظ**.
1. أغلق جزء **الإعدادات الافتراضية** .

## <a name="related-topics"></a>المواضيع ذات الصلة

[نظرة عامة على الاتصال المباشر B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[تكوين إعدادات الوصول عبر المستأجرين للاتصال المباشر B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

