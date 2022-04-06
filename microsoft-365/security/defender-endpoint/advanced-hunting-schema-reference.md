---
title: مرجع مخطط الصيد المتقدم
description: تعرف على الجداول الموجودة في مخطط الصيد المتقدم لفهم البيانات التي يمكنك تشغيل استعلامات البحث عن المخاطر عليها.
keywords: الصيد المتقدم، وصيد التهديدات، وصيد التهديدات الإلكترونية، و mdatp، و microsoft defender atp، و microsoft defender لنقطة النهاية، وبحث wdatp، والاستعلام، وبيانات التعقب، ومرجع المخطط، و kusto، وجدول، وبيانات
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/14/2020
ms.technology: mde
ms.openlocfilehash: 2e45a4ae78d0beb9bc57b72a59b9cf1376ac7da7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468336"
---
# <a name="understand-the-advanced-hunting-schema-in-microsoft-defender-for-endpoint"></a>فهم مخطط الصيد المتقدم في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[ويقام مخطط الصيد](advanced-hunting-overview.md) المتقدم من جداول متعددة توفر معلومات الحدث أو معلومات حول الأجهزة والكيانات الأخرى. لإنشاء استعلامات تمتد عبر جداول متعددة بطريقة فعالة، ستحتاج إلى فهم الجداول والأعمدة في مخطط الصيد المتقدم.

## <a name="get-schema-information-in-the-defender-for-cloud"></a>الحصول على معلومات المخطط في Defender for Cloud

أثناء إنشاء الاستعلامات، استخدم مرجع المخطط المضمن للحصول بسرعة على المعلومات التالية حول كل جدول في المخطط:

- **وصف الجداول**: نوع البيانات المضمنة في الجدول ومصدر تلك البيانات.
- **الأعمدة**: كل الأعمدة في الجدول.
- **أنواع الإجراءات**: القيم المحتملة في العمود `ActionType` التي تمثل أنواع الأحداث التي يدعمها الجدول. يتم توفير هذه القيم فقط للجداول التي تحتوي على معلومات الحدث.
- **نموذج استعلام**: استعلامات نموذجية تتميز بكيفية استخدام الجدول.

### <a name="access-the-schema-reference"></a>الوصول إلى مرجع المخطط

للوصول بسرعة إلى مرجع المخطط، حدد الإجراء **عرض** المرجع بجانب اسم الجدول في تمثيل المخطط. يمكنك أيضا تحديد **مرجع المخطط** للبحث عن جدول.

:::image type="content" source="images/ah-reference.png" alt-text="صفحة الصيد المتقدمة" lightbox="images/ah-reference.png":::

## <a name="learn-the-schema-tables"></a>تعرف على جداول المخططات

يسرد المرجع التالي كل الجداول في مخطط الصيد المتقدم. ويربط كل اسم جدول بصفحة تصف أسماء الأعمدة لهذا الجدول.

يتم أيضا سرد أسماء الأعمدة والأعمدة ضمن Microsoft 365 Defender، في تمثيل المخطط على شاشة الصيد المتقدمة.

<br>

****

|اسم الجدول|الوصف|
|---|---|
|**[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)**|التنبيهات على Microsoft 365 Defender |
|**[DeviceInfo](advanced-hunting-deviceinfo-table.md)**|معلومات الجهاز، بما في ذلك معلومات نظام التشغيل|
|**[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)**|خصائص الشبكة للأجهزة، بما في ذلك المحولات وعناوين IP و MAC، بالإضافة إلى الشبكات والمجالات المتصلة|
|**[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)**|إنشاء العملية والأحداث ذات الصلة|
|**[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)**|اتصال الشبكة والأحداث ذات الصلة|
|**[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)**|إنشاء الملفات والتعديلات والأحداث الأخرى لنظام الملفات|
|**[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)**|إنشاء إدخالات السجل وتعديلها|
|**[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)**|تسجيل الدخول والأحداث الأخرى للمصادقة|
|**[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)**|أحداث تحميل DLL|
|**[DeviceEvents](advanced-hunting-deviceevents-table.md)**|أنواع أحداث متعددة، بما في ذلك الأحداث التي يتم تشغيلها بواسطة عناصر التحكم في الأمان مثل برنامج الحماية من الفيروسات من Microsoft Defender وحماية استغلال|
|**[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)**|معلومات الشهادة للملفات الموقعة التي تم الحصول عليها من أحداث التحقق من الشهادة على نقاط النهاية|
|**[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)**|مخزون البرامج المثبتة على الأجهزة، بما في ذلك معلومات الإصدار الخاصة بها ووضع نهاية الدعم|
|**[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)**|نقاط الضعف في البرامج الموجودة على الأجهزة وقائمة تحديثات الأمان المتوفرة التي تعالج كل ثغرة أمنية|
|**[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)**|قاعدة معارف الثغرات التي يتم الكشف عنها بشكل عام، بما في ذلك ما إذا كانت التعليمات البرمجية للاستغلال متوفرة بشكل عام|
|**[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)**|أحداث & إدارة الثغرات الأمنية، مما يشير إلى حالة تكوينات الأمان المختلفة على الأجهزة|
|**[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)**|قاعدة معارف تكوينات الأمان المختلفة المستخدمة بواسطة إدارة & الثغرات لتقييم الأجهزة؛ يتضمن تعيينات لمعايير ومقاييس مختلفة|
|

> [!TIP]
> استخدام [الصيد المتقدم في](/microsoft-365/security/defender/advanced-hunting-overview) Microsoft 365 Defender للبحث عن التهديدات باستخدام البيانات من Defender ل Endpoint، Microsoft Defender لـ Office 365، Microsoft Defender for Cloud Apps، و Microsoft Defender for Identity. [قم Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

تعرف على المزيد حول كيفية نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender في ترحيل [استعلامات](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde) الصيد المتقدمة من Microsoft Defender لنقطة النهاية.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على الكشف المخصص](overview-custom-detections.md)
- [تغييرات متقدمة في مخطط بيانات الصيد](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
