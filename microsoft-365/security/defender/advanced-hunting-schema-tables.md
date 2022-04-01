---
title: جداول البيانات في Microsoft 365 Defender الصيد المتقدم
description: تعرف على الجداول في مخطط الصيد المتقدم لفهم البيانات التي يمكنك تشغيل استعلامات البحث عن التهديدات عليها
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، مرجع المخطط، kusto، الجدول، البيانات
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a496e0e293e72821016d6efa5fbd9622f669ab0b
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755531"
---
# <a name="understand-the-advanced-hunting-schema"></a>فهم مخطط الصيد المتقدم

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[ويقام مخطط الصيد](advanced-hunting-overview.md) المتقدم من جداول متعددة توفر معلومات الحدث أو معلومات حول الأجهزة والتنبيهات والهويات وأنواع الكيانات الأخرى. لإنشاء استعلامات تمتد عبر جداول متعددة بطريقة فعالة، ستحتاج إلى فهم الجداول والأعمدة في مخطط الصيد المتقدم.

<a name="get-schema-information-in-the-security-center"></a>

## <a name="get-schema-information"></a>الحصول على معلومات المخطط

أثناء إنشاء الاستعلامات، استخدم مرجع المخطط المضمن للحصول بسرعة على المعلومات التالية حول كل جدول في المخطط:

- **وصف الجداول**— نوع البيانات المضمنة في الجدول ومصدر تلك البيانات.
- **الأعمدة**— كل الأعمدة في الجدول.
- **أنواع الإجراءات**— القيم المحتملة في العمود `ActionType` التي تمثل أنواع الأحداث التي يدعمها الجدول. يتم توفير هذه المعلومات فقط للجداول التي تحتوي على معلومات الحدث.
- **نموذج استعلام**— مثال للاستعلامات التي تتميز بكيفية استخدام الجدول.

### <a name="access-the-schema-reference"></a>الوصول إلى مرجع المخطط
للوصول بسرعة إلى مرجع المخطط، حدد الإجراء **عرض** المرجع بجانب اسم الجدول في تمثيل المخطط. يمكنك أيضا تحديد **مرجع المخطط** للبحث عن جدول.

:::image type="content" source="../../media/understand-schema-1.png" alt-text="الصفحة &quot;مرجع المخطط&quot; على صفحة &quot;الصيد المتقدم&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/understand-schema-1.png":::

## <a name="learn-the-schema-tables"></a>تعرف على جداول المخططات
يسرد المرجع التالي كل الجداول في المخطط. ويربط كل اسم جدول بصفحة تصف أسماء الأعمدة لهذا الجدول. يتم أيضا إدراج أسماء الأعمدة والأعمدة في Defender for Cloud كجزء من تمثيل المخطط على شاشة الصيد المتقدمة.

| اسم الجدول | الوصف |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | الملفات أو عناوين IP أو عناوين URL أو المستخدمين أو الأجهزة المقترنة بالتنبيهات |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | تنبيهات من Microsoft Defender لنقطة النهاية و Microsoft Defender ل Office 365 و Microsoft Defender لتطبيقات السحابة و Microsoft Defender for Identity، بما في ذلك معلومات الخطورة وتصنيف التهديدات  |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | الأحداث التي تتضمن الحسابات والكائنات في Office 365 وتطبيقات وخدمات السحابة الأخرى |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | أنواع أحداث متعددة، بما في ذلك الأحداث التي يتم تشغيلها بواسطة عناصر التحكم في الأمان مثل برنامج الحماية من الفيروسات لـ Windows Defender وحماية استغلال |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | معلومات الشهادة للملفات الموقعة التي تم الحصول عليها من أحداث التحقق من الشهادة على نقاط النهاية |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | إنشاء الملفات والتعديلات والأحداث الأخرى لنظام الملفات |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | أحداث تحميل DLL |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | معلومات الجهاز، بما في ذلك معلومات نظام التشغيل |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | تسجيل الدخول والأحداث الأخرى للمصادقة على الأجهزة |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | اتصال الشبكة والأحداث ذات الصلة |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | خصائص الشبكة للأجهزة، بما في ذلك المحولات الفعلية وعناوين IP و MAC، بالإضافة إلى الشبكات والمجالات المتصلة |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | إنشاء العملية والأحداث ذات الصلة |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | إنشاء إدخالات السجل وتعديلها |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | أحداث & إدارة الثغرات الأمنية، مما يشير إلى حالة تكوينات الأمان المختلفة على الأجهزة |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | قاعدة معارف تكوينات الأمان المختلفة المستخدمة بواسطة إدارة & الثغرات لتقييم الأجهزة؛ يتضمن تعيينات لمعايير ومقاييس مختلفة  |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | مخزون البرامج المثبتة على الأجهزة، بما في ذلك معلومات الإصدار الخاصة بها ووضع نهاية الدعم |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | نقاط الضعف في البرامج الموجودة على الأجهزة وقائمة تحديثات الأمان المتوفرة التي تعالج كل ثغرة أمنية |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | قاعدة معارف الثغرات التي يتم الكشف عنها بشكل عام، بما في ذلك ما إذا كانت التعليمات البرمجية للاستغلال متوفرة بشكل عام |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | معلومات حول الملفات المرفقة ببريدات البريد الإلكتروني |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Microsoft 365 البريد الإلكتروني، بما في ذلك تسليم البريد الإلكتروني والأحداث المحظورة |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | أحداث الأمان التي تحدث بعد التسليم، بعد Microsoft 365 تسليم رسائل البريد الإلكتروني إلى علبة بريد المستلم |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | معلومات حول عناوين URL على رسائل البريد الإلكتروني |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | الأحداث التي تتضمن وحدة تحكم المجال المحلي التي تقوم بتشغيل Active Directory (AD). يتناول هذا الجدول مجموعة من الأحداث المتعلقة بالهوية والأحداث المتعلقة بالهوية على وحدة التحكم بالمجال. |
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | معلومات الحساب من مصادر مختلفة، بما في ذلك Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | أحداث المصادقة على خدمات Active Directory و Microsoft عبر الإنترنت |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | الاستعلامات الخاصة بكائنات Active Directory، مثل المستخدمين والمجموعات والأجهزة والمجالات |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
