---
title: تسجيل أجهزة iOS/iPadOS وAndroid Microsoft 365 بيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: استخدم دليل Test Lab هذا لتسجيل الأجهزة في Microsoft 365 الاختبار وإدارتها عن بعد.
ms.openlocfilehash: 7610348febcc8c2054c50d7f7a6f1433e9b62306
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63565865"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>تسجيل أجهزة iOS وAndroid في Microsoft 365 بيئة اختبار المؤسسة

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

تصف هذه المقالة كيفية تسجيل واختبار قدرات إدارة أجهزة المحمول الأساسية لأجهزة iOS/iPadOS وAndroid في Microsoft 365 بيئة اختبار المؤسسة.

يتضمن تسجيل أجهزة iOS/iPadOS وAndroid في بيئة الاختبار ثلاث مراحل:
- [المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة الثانية: تسجيل أجهزة iOS/iPadOS وAndroid](#phase-2-enroll-your-ios-and-android-devices)
- [المرحلة 3: إدارة أجهزة iOS/iPadOS وAndroid عن بعد](#phase-3-manage-your-ios-and-android-devices-remotely)

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة

إذا كنت تريد تسجيل أجهزة iOS/iPadOS وAndroid بطريقة خفيفة بالحد الأدنى من المتطلبات، فاتبع الإرشادات في [تكوين الأساس الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت تريد تسجيل أجهزة iOS/iPadOS وAndroid في مؤسسة محاكاة، فاتبع الإرشادات الواردة في [مصادقة المرور](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار الترخيص التلقائي وعضوية المجموعة بيئة اختبار المؤسسة المحاكاة، التي تتضمن إنترانت محاكاة متصلة بالإنترنت ومزامنة الدليل الغابات خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار الترخيص التلقائي وعضوية المجموعة، كما يمكنك تجربته في بيئة تمثل مؤسسة نموذجية.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>المرحلة الثانية: تسجيل أجهزة iOS وAndroid

إذا كنت تفكر في حل إدارة أجهزة المحمول (MDM) لإدارة أجهزتك، يمكنك استخدام Microsoft Intune. عند العمل مع أي موفر MDM، بما في ذلك Intune، يتم "تسجيل" الأجهزة. عند التسجيل، يتلقون الميزات والإعدادات التي تقوم بتكوينها. 

في Intune، هناك بعض الطرق لتسجيل أجهزة iOS/iPadOS وAndroid. يمكنك اختيار خيار التسجيل الذي يعمل بشكل أفضل لمنظمتك. لمزيد من المعلومات والإرشادات، راجع المقالات التالية:

- [دليل النشر: تسجيل أجهزة iOS وiPadOS في Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [دليل النشر: تسجيل أجهزة Android في Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

إذا كنت جاهزا لاستخدام Intune لإدارة الأجهزة، وتريد بعض الإرشادات، فقد تساعدك المعلومات التالية:

- [نظرة عامة حول إدارة الأجهزة](/mem/intune/fundamentals/what-is-device-management)
- [البرنامج التعليمي: معاينة Intune في إدارة نقاط النهاية من Microsoft](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [دليل النشر: الإعداد أو الانتقال إلى Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>المرحلة الثالثة: إدارة أجهزة iOS وAndroid عن بعد

Microsoft Intune ميزة التأمين عن بعد وإعادة تعيين رمز المرور. إذا فقد أحد الأشخاص جهازه، يمكنك تأمين الجهاز عن بعد. إذا نسي أحد الأشخاص رمز المرور الخاص به، يمكنك إعادة تعيينه عن بعد.

- لقفل جهاز iOS/iPadOS أو Android عن بعد، راجع تأمين الأجهزة عن بعد [باستخدام Intune](/mem/intune/remote-actions/device-remote-lock).
- لإعادة تعيين رمز المرور عن بعد، راجع إعادة تعيين رمز مرور الجهاز أو إزالته [في Intune](/mem/intune/remote-actions/device-passcode-reset).

للحصول على مهام إضافية يمكنك تشغيلها عن بعد، راجع [إجراءات الجهاز المتوفرة](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات وإمكانيات](m365-enterprise-test-lab-guides.md#mobile-device-management) إدارة أجهزة المحمول الإضافية في بيئة الاختبار.

## <a name="see-also"></a>انظر أيضاً

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)
  
[سياسات توافق الأجهزة لبيئة Microsoft 365 اختبار المؤسسة](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)
