---
title: سطح المكتب المدار من Microsoft و ITIL
description: ربط أطوار ITIL بمعلومات ومقالات سطح المكتب المدار من Microsoft
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق، ITISM
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b9984e308b6681512297e484817f95206283385e
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/13/2022
ms.locfileid: "63567114"
---
# <a name="microsoft-managed-desktop-and-itil"></a>سطح المكتب المدار من Microsoft و ITIL

يجد العديد من المؤسسات أنه من القيم أن يتم تنظيم خدماتها الخاصة ب IT على طول خط نموذج خدمة IT Service (ITM) رسمي، مثل [ITIL](https://www.axelos.com/best-practice-solutions/itil). 

يمكن Microsoft Managed Desktop مؤسستك من الامتثال للعديد من الجوانب الأساسية لنماذج ITSM ذات الطابع الرسمي. باستخدام ITIL كمثال، تساعدك هذه المقالة على رؤية الاتصالات بين مراحل ITIL الشائعة وعملياتها وميزات سطح المكتب المدارة المكافئة ل Microsoft، حيثما ينطبق ذلك. تنطبق هذه المعلومات فقط على جزء سطح المكتب المدار من Microsoft في مؤسستك.

لمزيد من الشمولية حول ITIL ومراحله ومراحل عمله، راجع الوثائق [الخاصة به](https://www.axelos.com/best-practice-solutions/itil).


## <a name="service-design"></a>تصميم الخدمة

يرتبط هذا الجدول بمراحل ITIL وعملياته الأساسية بميزات سطح المكتب المدار من Microsoft، مع ارتباطات إلى وثائقنا للحصول على التفاصيل:



|عملية ITIL |الوصف  |الوثائق |
|---------|---------|---------|
|الإدارة على مستوى الخدمة     | يتم تحديد أوقات الاستجابة لطلبات دعم المسؤول والحوادث.  |  [دعم المسؤول لسطح المكتب المدار من Microsoft](working-with-managed-desktop/admin-support.md)  |
|إدارة كتالوج الخدمة     | يتم الاحتفاظ بوصف الخدمة الذي يفصيل مكونات الخدمة صحيحا مع حالة الخدمة، ويتوفر لجميع العملاء الحاليين والمهتمين.<br><br>المتطلبات الأساسية المفصلة لفهم ما هو مطلوب لتشغيل الخدمة.  | - [وصف خدمة سطح المكتب المدار من Microsoft](service-description/index.md)<br><br>- [الاستعداد للتسجيل في Microsoft Managed Desktop](get-ready/index.md)  |
|إدارة أمان المعلومات     | معلومات الأمان، بما في ذلك أمان المعلومات للخدمة.<br><br> سياسات متعلقة بالامن ومعلومات أخرى حول كيفية تكوين الأجهزة.   | - [الأمان في Microsoft Managed Desktop](service-description/security.md)<br><br>- [تكوين الجهاز](service-description/device-policies.md)  |
|إدارة التوفر     |  يوازن Microsoft Managed Desktop المسؤولية مع مؤسستك لضمان توفر الخدمة.<br><br>يمكن للمسؤولين والمستخدمين الوصول إلى الدعم المعني في حالة وجود مشاكل في الخدمة أو التوفر. | - [عمليات ومراقبة سطح المكتب المدار من Microsoft](service-description/operations-and-monitoring.md)<br><br>- [دعم المسؤول لسطح المكتب المدار من Microsoft](working-with-managed-desktop/admin-support.md)<br>- [الحصول على تعليمات للمستخدمين](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>انتقال الخدمة


|عملية ITIL |الوصف  |الوثائق |
|---------|---------|---------|
|إدارة التغيير     | توازن معرف من المسؤولية، نظرة عامة حول العملية، والأنواع ذات الصلة بإدارة التغيير المتوفرة.  | [عمليات ومراقبة سطح المكتب المدار من Microsoft](service-description/operations-and-monitoring.md#change-management) |
|إدارة الإصدار والنشر     |  يدير Microsoft Managed Desktop التحديثات للأجهزة التي تم تسجيلها في الخدمة.  | [كيفية معالجة التحديثات في Microsoft Managed Desktop](service-description/updates.md)        |
|إدارة أصول الخدمة وتكوينها     | تتوفر المعلومات المتعلقة بنشر سطح المكتب المدار من Microsoft في مؤسستك على مدخل مسؤول تكنولوجيا المعلومات.  | [دعم المسؤول لسطح المكتب المدار من Microsoft](working-with-managed-desktop/admin-support.md) |
|إدارة المعارف     | يتم الاحتفاظ بالمعلومات حول خدمة سطح المكتب المدار من Microsoft على هذا الموقع.   | [محفوظات التغيير لوثائق Microsoft Managed Desktop](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>عملية الخدمة


|عملية ITIL |الوصف  |الوثائق  |
|---------|---------|---------|
|إدارة الأحداث     |  يتم توفير تفاصيل حول مراقبة الأجهزة.<br><br>إجراءات التشغيل القياسية لخدمة Microsoft Managed Desktop مفصلة. |  - [الأمان في Microsoft Managed Desktop](service-description/security.md)<br>- [عمليات ومراقبة سطح المكتب المدار من Microsoft](service-description/operations-and-monitoring.md)       |
|إدارة الحوادث  | سيتحقق Microsoft Managed Desktop من الأحداث ويتصرف بشأنها حسب تعريفات الخطورة المحددة.  |  [تعريفات خطورة طلبات الدعم](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|طلب إدارة الوفاء     |  يتم تعريف معالجة طلبات المعلومات وطلبات التغيير ذات الصلة لخدمة Microsoft Managed Desktop.         |[دعم المسؤول لسطح المكتب المدار من Microsoft](working-with-managed-desktop/admin-support.md)         |
|إدارة المشاكل     | يجب توجيه أي مشاكل تتعلق بالخدمة إلى فريق حسابك المحلي في الوقت نفسه. | الوثائق في وضع التطوير |
|إدارة Access     | مكونات إدارة Access ومسؤوليات العميل لضمان أن الوظائف مفصلة.  | [إدارة الهوية والوصول](service-description/security.md#identity-and-access-management)        |
