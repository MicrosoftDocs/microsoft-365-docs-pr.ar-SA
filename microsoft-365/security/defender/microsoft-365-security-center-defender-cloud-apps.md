---
title: Microsoft Defender for Cloud Apps في Microsoft 365 Defender (معاينة)
description: تعرف على التغييرات من Microsoft Defender for Cloud Apps إلى Microsoft 365 Defender
keywords: بدء استخدام Microsoft 365 Defender، Microsoft Defender for Cloud Apps
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 05/03/2022
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 2cd146cfb0fe9b6af10f562bbf6eb00bc5bf9a3d
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078394"
---
# <a name="microsoft-defender-for-cloud-apps-in-microsoft-365-defender-preview"></a>Microsoft Defender for Cloud Apps في Microsoft 365 Defender (معاينة)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Cloud Apps](/defender-cloud-apps/)

أصبح Microsoft Defender for Cloud Apps الآن جزءا من Microsoft 365 Defender. يسمح مدخل Microsoft 365 Defender لمسؤولي الأمان بتنفيذ مهام الأمان الخاصة بهم في موقع واحد. سيؤدي ذلك إلى تبسيط مهام سير العمل، وإضافة وظائف خدمات Microsoft 365 Defender الأخرى. ستكون Microsoft 365 Defender هي الصفحة الرئيسية لمراقبة الأمان وإدارته عبر هويات Microsoft وبياناتها وأجهزتها وتطبيقاتها وبنيتك الأساسية.

سيتمكن محللو SOC من فرز جميع أحمال العمل Microsoft 365 Defender والتحقيق فيها والبحث فيها، بما في ذلك تطبيقات السحابة.
ستستمر تنبيهات Defender for Cloud Apps في الظهور في قائمة انتظار الحوادث وقوائم انتظار التنبيهات في Microsoft 365 Defender، ولكن الآن مع المحتوى ذي الصلة داخل صفحات التنبيه المتوفرة في مدخل Microsoft 365 Defender، بتنسيق موحد مع التعديلات المناسبة لكل نوع من التنبيهات.

ألق نظرة على Microsoft 365 Defender في <https://security.microsoft.com>.

تعرف على المزيد حول المزايا: [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md).

## <a name="quick-reference"></a>مرجع سريع

تسرد الصورة والجدول أدناه التغييرات في التنقل بين Microsoft Defender for Cloud Apps Microsoft 365 Defender.

> [!NOTE]
> لم يتم ترحيل بعض الصفحات بعد ويجب الوصول إليها من مدخل Defender for Cloud Apps.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender.png" alt-text="المواقع الجديدة في مدخل Microsoft 365 Defender" lightbox="../../media/defender-cloud-apps-m365-defender.png":::

| Defender for Cloud Apps | Microsoft 365 Defender |
|---------|---------|
| لوحة معلومات Cloud Discover | تطبيقات السحابة -> اكتشاف السحابة |
| التطبيقات المكتشفة | علامة التبويب على صفحة Cloud Discovery |
| الموارد المكتشفة | علامة التبويب على صفحة Cloud Discovery |
| عناوين IP | علامة التبويب على صفحة Cloud Discovery |
| المستخدمون | علامة التبويب على صفحة Cloud Discovery |
| الاجهزه | علامة التبويب على صفحة Cloud Discovery |
| كتالوج تطبيق السحابة |  تطبيقات السحابة -> كتالوج تطبيقات السحابة |
| إنشاء تقرير لقطة Cloud Discovery | في صفحة Cloud Discovery، ضمن Actions |
| سجل النشاط | تطبيقات السحابة -> سجل النشاط |
| الملفات | المتبقية في مدخل Defender for Cloud Apps |
| المستخدمون والحسابات | الأصول -> الهويات |
| تكوين الأمان | المتبقية في مدخل Defender for Cloud Apps |
| وضع أمان الهوية | [تقييمات الوضع الأمني للهوية في Microsoft Defender for Identity](/defender-for-identity/isp-overview) |
| تطبيقات OAuth | تطبيقات السحابة -> تطبيقات OAuth |
| التطبيقات المتصلة | المتبقية في مدخل Defender for Cloud Apps |

> [!NOTE]
> تتوفر تجربة Defender for Cloud Apps الجديدة في مدخل Microsoft 365 Defender حاليا لجميع المستخدمين المفصلين في [إدارة وصول المسؤول](/defender-cloud-apps/manage-admins)، باستثناء المستخدمين الذين لديهم الأدوار المحددة في [أدوار المسؤول المضمنة في Defender for Cloud Apps](/defender-cloud-apps/manage-admins#built-in-admin-roles-in-defender-for-cloud-apps).

## <a name="whats-changed"></a>ما الذي تم تغييره

تعرف على التغييرات التي تأتي مع تكامل Defender for Cloud Apps و Microsoft 365 Defender.

### <a name="global-search"></a>البحث العمومي

يتضمن البحث العام في Microsoft 365 Defender (باستخدام شريط البحث في أعلى الصفحة) الآن كيانا إضافيا قابلا للبحث: يسمح لك بالبحث عن التطبيقات المتصلة في Defender for Cloud Apps.

:::image type="content" source="../../media/global-search-apps.png" alt-text="البحث عن التطبيقات المتصلة.":::

### <a name="assets-and-identities"></a>الأصول والهويات

كجزء من إنشاء قسم **أصول** مخصص يمتد عبر تجربة Microsoft 365 Defender بأكملها، يتم إعادة تصنيف قسم **المستخدمين والحسابات** في Defender for Cloud Apps كقسم **الهويات**. لا يتوقع إجراء أي تغييرات على الوظائف.

## <a name="related-information"></a>المعلومات ذات الصلة

- [Microsoft 365 Defender](microsoft-365-defender.md)
