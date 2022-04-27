---
title: نهج توافق الجهاز Microsoft 365 لبيئة اختبار المؤسسة
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: استخدم دليل مختبر الاختبار هذا لإضافة نهج توافق جهاز Intune إلى Microsoft 365 لبيئة اختبار المؤسسة.
ms.openlocfilehash: 3037ca846fe74fb8de51c78799e69c510821a034
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099444"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>نهج توافق الجهاز Microsoft 365 لبيئة اختبار المؤسسة

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

تصف هذه المقالة كيفية إضافة نهج توافق جهاز Intune للأجهزة Windows 10 Microsoft 365 Apps for enterprise إلى Microsoft 365 لبيئة اختبار المؤسسة.

تتضمن إضافة نهج توافق جهاز Intune مرحلتين:
- [المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة 2: إنشاء نهج توافق الجهاز للأجهزة Windows 10](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة

إذا كنت ترغب في تكوين نهج MAM بطريقة خفيفة الوزن فقط مع الحد الأدنى من المتطلبات، فاتبع الإرشادات في [التكوين الأساسي الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت ترغب في تكوين نهج MAM في مؤسسة محاكاة، فاتبع الإرشادات في [المصادقة التمريرية](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار الترخيص التلقائي وعضوية المجموعة بيئة اختبار المؤسسة المحاكاة، والتي تتضمن محاكاة إنترانت متصلة بالإنترنت ومزامنة الدليل لمجموعة خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار الترخيص التلقائي وعضوية المجموعة وتجربة ذلك في بيئة تمثل مؤسسة نموذجية.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>المرحلة 2: إنشاء نهج توافق الجهاز للأجهزة Windows 10

في هذه المرحلة، يمكنك إنشاء نهج توافق الجهاز للأجهزة Windows 10. تستخدم هذه المرحلة Microsoft Intune [ومركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) لإضافة مجموعة وإنشاء نهج توافق.

1. انتقل إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com)، وسجل الدخول إلى اشتراك مختبر الاختبار Microsoft 365 باستخدام حساب المسؤول العام، وحدد <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">مركز إدارة إدارة نقاط النهاية</a>.

    إذا كانت هناك رسالة مشابهة **لرسالة لم تقم بتمكين إدارة الجهاز بعد** ، فحدد Intune كمرجع إدارة أجهزة الهواتف المحمولة. للحصول على الخطوات [المحددة، راجع تعيين هيئة إدارة الأجهزة المحمولة](/mem/intune/fundamentals/mdm-authority-set).

    يركز مركز إدارة إدارة نقاط النهاية على إدارة الأجهزة وإدارة التطبيقات. للحصول على جولة في مركز الإدارة هذا، راجع [البرنامج التعليمي: معاينة Intune في إدارة نقاط النهاية من Microsoft](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. في **المجموعات**، أضف **Microsoft 365** جديدة أو مجموعة **أمان** باسم **مستخدمي جهاز Windows 10 المدارة**، مع نوع **عضوية معين**. في الخطوات التالية، ستقوم بتعيين نهج التوافق الخاص بك إلى هذه المجموعة. 

    للحصول على الخطوات المحددة، للحصول على معلومات حول **Microsoft 365** أو مجموعات **الأمان**، راجع [إضافة مجموعات لتنظيم المستخدمين والأجهزة](/mem/intune/fundamentals/groups-add).

3. في **الأجهزة**، قم بإنشاء نهج توافق Windows 10. قم بتعيين هذا النهج إلى مجموعة **مستخدمي الأجهزة المدارة Windows 10** التي أنشأتها.

    في النهج الخاص بك، يمكنك حظر كلمات المرور البسيطة، وتتطلب جدار حماية، وتتطلب تشغيل خدمة Microsoft Defender Antimalware، وأكثر من ذلك. يتضمن نهج التوافق عادة الإعدادات الأساسية، أو الحد الأدنى الذي يجب أن يحتوي عليه كل جهاز.

    للحصول على الخطوات المحددة، للحصول على معلومات حول إعدادات التوافق المتوفرة التي يمكنك تكوينها، راجع [استخدام نهج التوافق لتعيين قواعد للأجهزة التي تديرها](/mem/intune/protect/device-compliance-get-started).

عند الانتهاء، لديك نهج توافق الجهاز لاختبار الأعضاء في مجموعة **مستخدمي الأجهزة Windows 10 المدارة**.
  
## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وقدرات إضافية لإدارة أجهزة المحمول](m365-enterprise-test-lab-guides.md#mobile-device-management) في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md).
  
[تسجيل أجهزة iOS وAndroid في Microsoft 365 لبيئة اختبار المؤسسة](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
