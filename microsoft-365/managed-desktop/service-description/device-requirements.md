---
title: متطلبات الجهاز
description: ملخص الحد الأدنى لمتطلبات الأجهزة والبرامج للأجهزة للعمل مع Microsoft Managed Desktop
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 957203829bfcfeb36696a1a4c34888938712b471
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572208"
---
# <a name="device-requirements"></a>متطلبات الجهاز

يقيم Microsoft Managed Desktop بشكل منتظم متطلبات الجهاز لتضمينها في الخدمة. تصف هذه المقالة متطلبات الأجهزة والبرامج التي يجب أن يلبيها الجهاز لكي يعمل مع Microsoft Managed Desktop.

يمكنك مراجعة قائمة بأجهزة معينة تمت الموافقة على استخدامها بالفعل استنادا إلى هذه المتطلبات. التصفية لسطح المكتب المدار من Microsoft في صفحة التسوق [Windows Pro العمل](https://www.microsoft.com/en-us/windows/business/devices).

> [!NOTE]
> يمكن أن تتغير هذه المتطلبات في أي وقت، ولكننا سنقدم إشعارا لمدة 30 يوما بأي تغييرات في متطلبات الأجهزة. يتم وضع علامة على المتطلبات التي تم تغييرها مؤخرا ب <b>\*</b>.

## <a name="check-hardware-requirements"></a>التحقق من متطلبات الأجهزة

إلى جانب مراجعة مواصفات الجهاز، يمكنك أيضا استخدام مدقق تقييم الجهوزية [](../get-ready/readiness-assessment-downloadable.md) القابل للتنزيل للتحقق من أن الجهاز يلبي المتطلبات الضرورية.

تعمل هذه الأداة أيضا على التحقق من إعدادات الشبكة ونقاط النهاية الضرورية لكي تعمل الخدمة.

## <a name="minimum-requirements"></a>الحد الأدنى للمتطلبات

للتسجيل في Microsoft Managed Desktop، يجب أن يلبي الجهاز كل هذه المتطلبات أو يتجاوزها.

### <a name="manufacturer"></a>الشركة المصنعة

يجب أن يكون الجهاز قد تم تصنيعه بواسطة إحدى الشركات المصنعة هذه:

- Dell
- HP
- Lenovo
- Microsoft

> [!NOTE]
> في 01 مارس 2022، يجب أن تكون الأجهزة المدارة بواسطة Microsoft Managed Desktop معتمدة من قبل الشركة الأصلية.<br><br>اعمل مع OEM لمعرفة متى ستصل الأجهزة في ملف أعمالك إلى نهاية العمر العمري. سيكون العملاء مسؤولين عن ضمان استبدال الأجهزة قبل انتهاء العمر العمري. سيستمر إدارة أي أجهزة تقع خارج دعم الشركة الأصلية بواسطة Microsoft Managed Desktop، ولكن قد يكون الدعم لهذه الأجهزة محدودا لأنها معرضة لخطر مشاكل الأمان والأداء التي قد لا يتم تخفيفها من خلال خدمتنا.
</b>

### <a name="installed-software"></a>البرامج المثبتة

يجب أن يكون هذا البرنامج م تثبيتا مسبقا على الجهاز:

- <b>\*</b>Windows 10 أو Windows 11: Enterprise أو Pro أو Pro Workstation.
- إصدار 64 بت من Microsoft 365 Apps ل Enterprise.
- جميع برامج تشغيل الأجهزة القابلة للتطبيق.

### <a name="physical-features"></a>الميزات الفعلية

يجب أن تكون لدى الأجهزة هذه الإمكانات:

- تم تمكين التشغيل الآمن ل UEFI.
- وحدة النظام الأساسي الموثوق بها 2.0.
- قادر على الأمان المستند إلى الظاهرية.
- [تكامل التعليمات البرمجية المحمية بواسطة Hypervisor](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) والمدعم بواسطة BIOS.

لمزيد من المعلومات حول هذه الإمكانات والتقنيات المتعلقة بها التي تستخدمها الخدمة، راجع [تقنيات سطح المكتب المدار من Microsoft](../intro/technologies.md).

> [!NOTE]
>- ARM المعالجات غير معتمدة.
>- <b>\*</b>Windows 11 متطلبات [أجهزة إضافية](/windows/whats-new/windows-11-requirements).

يجب أن تفي الأجهزة بالحدود التالية للتخزين والذاكرة أو تتجاوزها:

- يجب أن يكون محرك أقراص التشغيل من أي نوع آخر غير القرص الثابت. على سبيل المثال، محركات أقراص SSD وNVMe و eMMC كلها خيارات صالحة.
- يجب أن يكون محرك الأقراص الذي يتم تشغيله سعة 128 غيغابايت على الأقل.
- يجب أن تساوي ذاكرة الجهاز الداخلية (RAM) 8 غيغابايت أو تتجاوزها.

إذا تم الجهاز بعد 1 يوليو 2020، يجب أن يكون لديه أيضا كاميرا IR أو قارئ بصمات الأصابع أو كليهما، وذلك لدعم [Windows Hello.](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security)

## <a name="recommended-features"></a>الميزات المستحسنة

سيكون لدى المستخدمين تجربة أفضل بكثير إذا اخترت الأجهزة التي تحتوي على هذه الميزات:

- إما معالج Intel vPro-platform أو معالج AMD Ryzen Pro.
- محرك أقراص التشغيل من نوع SSD مع سعة 256 غيغابايت على الأقل.
- ذاكرة الجهاز الداخلية (RAM) التي لا يقل عددها عن 16 غيغابايت.
- دعم الاستعداد الحديث.
- الجهاز من نوع الكمبيوتر الشخصي الآمن.
- يدعم Kernel DMA Protection.
