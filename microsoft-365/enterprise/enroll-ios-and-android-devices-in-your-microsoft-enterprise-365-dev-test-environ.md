---
title: تسجيل أجهزة iOS/iPadOS وAndroid في Microsoft 365 لبيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: استخدم دليل مختبر الاختبار هذا لتسجيل الأجهزة في بيئة اختبار Microsoft 365 وإدارتها عن بعد.
ms.openlocfilehash: 5cefabf6b995754f6febe117776ad2de97443df0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092922"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>تسجيل أجهزة iOS وAndroid في Microsoft 365 لبيئة اختبار المؤسسة

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

تصف هذه المقالة كيفية تسجيل واختبار قدرات إدارة الأجهزة المحمولة الأساسية لأجهزة iOS/iPadOS وAndroid في Microsoft 365 لبيئة اختبار المؤسسة.

يتضمن تسجيل أجهزة iOS/iPadOS وAndroid في بيئة الاختبار ثلاث مراحل:
- [المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة الثانية: تسجيل أجهزة iOS/iPadOS وAndroid](#phase-2-enroll-your-ios-and-android-devices)
- [المرحلة 3: إدارة أجهزة iOS/iPadOS وAndroid عن بعد](#phase-3-manage-your-ios-and-android-devices-remotely)

![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة

إذا كنت ترغب في تسجيل أجهزة iOS/iPadOS وAndroid بطريقة خفيفة مع الحد الأدنى من المتطلبات، فاتبع الإرشادات في [التكوين الأساسي الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت تريد تسجيل أجهزة iOS/iPadOS وAndroid في مؤسسة محاكاة، فاتبع الإرشادات الواردة في [مصادقة المرور](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار الترخيص التلقائي وعضوية المجموعة بيئة اختبار المؤسسة المحاكاة، والتي تتضمن محاكاة إنترانت متصلة بالإنترنت ومزامنة الدليل لمجموعة خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار الترخيص التلقائي وعضوية المجموعة، ويمكنك تجربته في بيئة تمثل مؤسسة نموذجية.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>المرحلة الثانية: تسجيل أجهزة iOS وAndroid

إذا كنت تفكر في حل إدارة أجهزة المحمول (MDM) لإدارة أجهزتك، يمكنك استخدام Microsoft Intune. عند العمل مع أي موفر MDM، بما في ذلك Intune، يتم "تسجيل الأجهزة". عند التسجيل، يتلقون الميزات والإعدادات التي تقوم بتكوينها. 

في Intune، هناك بعض الطرق لتسجيل أجهزة iOS/iPadOS وAndroid. يمكنك اختيار خيار التسجيل الذي يعمل بشكل أفضل لمؤسستك. لمزيد من المعلومات والإرشادات، راجع المقالات التالية:

- [دليل النشر: تسجيل أجهزة iOS وiPadOS في Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [دليل النشر: تسجيل أجهزة Android في Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

إذا كنت جاهزا لاستخدام Intune لإدارة الأجهزة، وتريد بعض الإرشادات، فقد تساعدك المعلومات التالية:

- [نظرة عامة على إدارة الأجهزة](/mem/intune/fundamentals/what-is-device-management)
- [البرنامج التعليمي: معاينة Intune في إدارة نقاط النهاية من Microsoft](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [دليل النشر: الإعداد أو الانتقال إلى Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>المرحلة 3: إدارة أجهزة iOS وAndroid عن بعد

يوفر Microsoft Intune ميزة إعادة تعيين رمز المرور والقفل عن بعد. إذا فقد شخص ما جهازه، يمكنك تأمين الجهاز عن بعد. إذا نسي شخص ما رمز المرور الخاص به، يمكنك إعادة تعيينه عن بعد.

- لتأمين جهاز يعمل بنظام التشغيل iOS/iPadOS أو Android عن بعد، راجع [أجهزة التأمين عن بعد باستخدام Intune](/mem/intune/remote-actions/device-remote-lock).
- لإعادة تعيين رمز المرور عن بعد، راجع [إعادة تعيين رمز مرور الجهاز أو إزالته في Intune](/mem/intune/remote-actions/device-passcode-reset).

بالنسبة للمهام الإضافية التي يمكنك تشغيلها عن بعد، راجع [إجراءات الجهاز المتوفرة](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وقدرات إضافية لإدارة أجهزة المحمول](m365-enterprise-test-lab-guides.md#mobile-device-management) في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>انظر أيضاً

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)
  
[نهج توافق الجهاز Microsoft 365 لبيئة اختبار المؤسسة](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)
