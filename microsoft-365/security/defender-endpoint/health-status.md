---
title: التحقق من مشاكل صحة الوكيل
description: تعرف على القيم التي يتم إرجاعها عند تشغيل الأمر "صحة mdatp"
keywords: mdatp health, command, health, status, command, onboarding status
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 13407c78f89058efe15ed0f5d8f23272716e0237
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63574298"
---
# <a name="investigate-agent-health-issues"></a>التحقق من مشاكل صحة الوكيل

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

يوفر الجدول التالي معلومات حول القيم التي يتم إرجاعها عند تشغيل `mdatp health` الأمر والأوصاف المناظرة لها.

<br>

****

|القيمة|الوصف|
|---|---|
|automatic_definition_update_enabled|True إذا تم تمكين تحديثات تعريف برنامج الحماية من الفيروسات التلقائية، فخلاف ذلك خطأ.|
|cloud_automatic_sample_submission_consent|مستوى الإرسال النموذجي الحالي. يمكن أن تكون إحدى القيم التالية: <ul><li>**بلا**: لا يتم إرسال أي عينات مريبة إلى Microsoft.</li><li>**خزينة**: يتم تلقائيا إرسال العينات المريبة التي لا تحتوي على معلومات تعريف شخصية (PII). هذه هي القيمة الافتراضية لهذا الإعداد.</li><li>**الكل**: يتم إرسال جميع العينات المريبة إلى Microsoft.</li></ul>|
|cloud_diagnostic_enabled|True إذا تم تمكين تجميع البيانات التشخيصية الاختيارية، فخلاف ذلك خطأ. لمزيد من المعلومات المتعلقة ب Defender for Endpoint ومنتجات وخدمات أخرى مثل برنامج الحماية من الفيروسات من Microsoft Defender و Windows، راجع [بيان خصوصية Microsoft](https://go.microsoft.com/fwlink/?linkid=827576).|
|cloud_enabled|True إذا تم تمكين الحماية التي يتم تسليمها من السحابة، وإلا فخلاف ذلك.|
|conflicting_applications|قائمة التطبيقات التي قد تكون متضاربة مع Microsoft Defender لنقطة النهاية. تتضمن هذه القائمة، على ألا تقتصر على، منتجات الأمان الأخرى والتطبيقات الأخرى المعروفة بالتسبب في مشاكل التوافق.|
|definitions_status|حالة تعريفات برنامج الحماية من الفيروسات.|
|definitions_updated|تاريخ آخر تحديث لتعريف برنامج الحماية من الفيروسات وتاريخه.|
|definitions_updated_minutes_ago|عدد الدقائق منذ آخر تحديث لتعريف برنامج الحماية من الفيروسات.|
|definitions_version|إصدار تعريف برنامج الحماية من الفيروسات.|
|edr_client_version|إصدار عميل الكشف التلقائي والاستجابة على النقط النهائية الذي يتم تشغيله على الجهاز.|
|edr_configuration_version|الكشف التلقائي والاستجابة على النقط النهائية تكوين.|
|edr_device_tags|قائمة العلامات المقترنة بجهاز.|
|edr_group_ids|"معرّف المجموعة" المقترن به الجهاز.|
|edr_machine_id|معرف الجهاز المستخدم في Microsoft 365 Defender.|
|engine_version|إصدار محرك الحماية من الفيروسات.|
|صحة جيدة|True إذا كان المنتج سليما، وإلا فخلاف ذلك.|
|مرخص|True إذا كان الجهاز مستأجرا، فخلاف ذلك خطأ.|
|log_level|مستوى السجل الحالي للمنتج.|
|machine_guid|معرف جهاز فريد يستخدمه مكون الحماية من الفيروسات.|
|network_protection_status|حالة مكون حماية الشبكة (macOS فقط). يمكن أن تكون إحدى القيم التالية: <ul><li>**بدء -** حماية الشبكة تبدأ</li><li>**failed_to_start** - لا يمكن بدء حماية الشبكة بسبب خطأ</li><li>**تم** البدء - يتم تشغيل حماية الشبكة حاليا على الجهاز</li><li>**إعادة التشغيل** - يتم حاليا إعادة تشغيل حماية الشبكة</li><li>**الإيقاف** - توقف حماية الشبكة</li><li>**متوقف** - حماية الشبكة غير قيد التشغيل</li></ul>|
|org_id|المؤسسة التي تم تشغيل الجهاز فيها. إذا لم يتم بعد تشغيل الجهاز في أي مؤسسة، فهذا يعني أن عملية الطباعة هذه غير متوفرة. لمزيد من المعلومات حول التكوين، راجع [Onboard إلى Microsoft Defender ل Endpoint](onboarding.md).|
|passive_mode_enabled|True إذا تم تعيين مكون الحماية من الفيروسات للتشغيل في الوضع غير النشط، فخلاف ذلك خطأ.|
|product_expiration|التاريخ والوقت الذي يصل فيه إصدار المنتج الحالي إلى نهاية الدعم.|
|real_time_protection_available|True إذا كان مكون الحماية في الوقت الحقيقي سليما، وإلا فخلاف ذلك.|
|real_time_protection_enabled|True إذا تم تمكين الحماية من الفيروسات في الوقت الحقيقي، فخلاف ذلك خطأ.|
|real_time_protection_subsystem|النظام الفرعي المستخدم لخدمة الحماية في الوقت الحقيقي. إذا كانت الحماية في الوقت الحقيقي لا تعمل كما هو متوقع، فيطبع هذا غير متوفر.|
|release_ring|حلقة الإصدار. لمزيد من المعلومات، راجع [حلقات النشر](deployment-rings.md).|
|
