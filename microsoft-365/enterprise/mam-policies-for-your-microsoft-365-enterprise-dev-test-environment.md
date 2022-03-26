---
title: سياسات توافق الأجهزة لبيئة Microsoft 365 اختبار المؤسسة
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: استخدم دليل Test Lab هذا لإضافة سياسات توافق أجهزة Intune Microsoft 365 بيئة اختبار المؤسسة.
ms.openlocfilehash: ec73211a21e9e064b729b93d9e88b7c5c69b21fe
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566687"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>سياسات توافق الأجهزة لبيئة Microsoft 365 اختبار المؤسسة

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

تصف هذه المقالة كيفية إضافة نهج توافق جهاز Intune للأجهزة Windows 10 والأجهزة Microsoft 365 Apps for enterprise إلى Microsoft 365 اختبار المؤسسة.

تتضمن إضافة نهج توافق جهاز Intune مرحلتين:
- [المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة الثانية: إنشاء نهج توافق الأجهزة للأجهزة Windows 10 الأجهزة](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة

إذا كنت تريد تكوين سياسات MAM بطريقة خفيفة فقط باستخدام الحد الأدنى من المتطلبات، فاتبع الإرشادات الموجودة في [تكوين الأساس الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت تريد تكوين سياسات MAM في مؤسسة محاكاة، فاتبع الإرشادات الواردة في [المصادقة المرورية](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار الترخيص التلقائي وعضوية المجموعة بيئة اختبار المؤسسة المحاكاة، التي تتضمن إنترانت محاكاة متصلة بالإنترنت ومزامنة الدليل الغابات خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار الترخيص التلقائي وعضوية المجموعة واختباره في بيئة تمثل مؤسسة نموذجية.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>المرحلة الثانية: إنشاء نهج توافق الأجهزة للأجهزة Windows 10 الأجهزة

في هذه المرحلة، يمكنك إنشاء نهج توافق الأجهزة للأجهزة Windows 10 الأجهزة. تستخدم هذه المرحلة Microsoft Intune مركز إدارة إدارة نقاط النهاية من Microsoft لإضافة مجموعة [](https://go.microsoft.com/fwlink/?linkid=2109431) وإنشاء نهج توافق.

1. انتقل [إلى مركز مسؤولي Microsoft 365،](https://admin.microsoft.com) سجل الدخول إلى اشتراكك في Microsoft 365 الاختبار باستخدام حساب المسؤول العام، وحدد إدارة نقاط النهاية <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">مركز الإدارة</a>.

    إذا تم عرض رسالة مماثلة  لرسالة لم تقم بتمكين إدارة الأجهزة بعد، فحدد Intune كمرجع MDM. للحصول على الخطوات المحددة، راجع [تعيين هيئة إدارة أجهزة المحمول](/mem/intune/fundamentals/mdm-authority-set).

    يركز إدارة نقاط النهاية إدارة التطبيق على إدارة الأجهزة وإدارة التطبيقات. للحصول على جولة في مركز الإدارة هذا، راجع [البرنامج التعليمي: معاينة Intune في](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) إدارة نقاط النهاية من Microsoft.

2. في **المجموعات**، أضف **مجموعة أمان Microsoft 365** أو مجموعة أمان جديدة  **Windows 10** مستخدمو الأجهزة المدارة، مع **نوع العضوية المعينة**. في الخطوات التالية، ستعين نهج التوافق لهذه المجموعة. 

    للحصول على الخطوات المحددة، للحصول على معلومات Microsoft 365  أو مجموعات الأمان،  راجع [إضافة مجموعات لتنظيم المستخدمين والأجهزة](/mem/intune/fundamentals/groups-add).

3. في **الأجهزة**، أنشئ Windows 10 التوافق. قم بتعيين هذا **النهج إلى مجموعة** مستخدمي الأجهزة المدارة Windows 10 التي أنشأتها.

    في نهجك، يمكنك حظر كلمات المرور البسيطة، أو طلب جدار حماية، أو طلب تشغيل خدمة الحماية من البرامج الضارة من Microsoft Defender، والمزيد. يتضمن نهج التوافق عادة الإعدادات الأساسية أو الحد الأدنى الذي يجب أن يتضمنه كل جهاز.

    للحصول على الخطوات المحددة، للحصول على معلومات حول إعدادات التوافق المتوفرة التي يمكنك تكوينها، راجع استخدام سياسات التوافق لتعيين قواعد للأجهزة [التي تديرها](/mem/intune/protect/device-compliance-get-started).

عند الانتهاء، يكون لديك نهج توافق الجهاز لاختبار الأعضاء في مجموعة مستخدمي الأجهزة **المدارة** Windows 10 الأجهزة.
  
## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات وإمكانيات](m365-enterprise-test-lab-guides.md#mobile-device-management) إدارة أجهزة المحمول الإضافية في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md).
  
[تسجيل أجهزة iOS وAndroid في Microsoft 365 بيئة اختبار المؤسسة](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
