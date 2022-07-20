---
title: إعداد الأجهزة المحمولة
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: كيفية إعداد الأجهزة المدارة
ms.openlocfilehash: a4298bcdc284f1957a1afa73cbc7ae8e3f15e7d1
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894998"
---
# <a name="set-up-managed-devices"></a>إعداد الأجهزة المحمولة

الجهاز "المدار" هو الجهاز الذي يخضع لتحكم وتراقبه المؤسسة، ومن ثم يتم تحديثه بشكل منتظم وآمن. وجود أجهزة تحت السيطرة المدارة هو هدف بالغ الأهمية. للتحكم في هذه الأجهزة، قم بتسجيلها في إدارة الأجهزة باستخدام Microsoft Intune وAzure Active Directory، وكلاهما مضمن مع Microsoft Business Premium.

1. إعداد نهج حماية الجهاز والبيانات في [معالج الإعداد](../business/set-up.md).

2. توصيل الكمبيوتر ب [Azure Active Directory](../business/set-up-windows-devices.md) باستخدام اسم المستخدم وكلمة المرور ل Microsoft 365. 

## <a name="enroll-devices-in-intune"></a>تسجيل الأجهزة في Intune

1. انتقل إلى مركز إدارة Microsoft إدارة نقاط النهاية ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. حدد **الأجهزة** > **المسجلة**. 

   :::image type="content" source="media/m365bp-endpoint-manager-enroll-devices.png" alt-text="استخدم Microsoft إدارة نقاط النهاية لتسجيل الأجهزة."::: 

3. اتبع إرشادات تسجيل الجهاز المحددة أدناه.

### <a name="for-windows-enrollment"></a>لتسجيل Windows:

1. حدد **تسجيل Windows** >  Windows. 

2. من أساليب التسجيل المدرجة، حدد **التسجيل التلقائي**.

### <a name="for-ios-enrollment"></a>لتسجيل iOS:

1. حدد تسجيل **iOS** > **iOS**.

2. من قائمة النهج، حدد نهجا للاطلاع على تفاصيله.

3. حدد **"خصائص** " لإدارة النهج.

4. حدد **"Settings** > **System Security** " وقم بتكوين تفاصيل الأمان في Intune.

5. انظر إلى ملفات تعريف التكوين. 

6. إنشاء ملف تعريف ودفعه إلى الأجهزة في مؤسستك، حسب الحاجة.

### <a name="for-android-enrollment"></a>لتسجيل Android:

1. حدد **تسجيل Android** >  Android.

2. اختر **Google Play المدار** وامنح Microsoft الإذن لإرسال المعلومات إلى Google.

## <a name="next-objective"></a>الهدف التالي

استخدم الإرشادات التالية [لإلحاق الأجهزة بقدرات Defender for Business](m365bp-onboard-devices-mdb.md).

