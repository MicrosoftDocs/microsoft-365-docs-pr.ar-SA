---
title: الخطوة 7. تنفيذ منع فقدان البيانات (DLP) باستخدام قدرات حماية المعلومات
ms.author: bcarter
author: brendacarter
f1.keywords:
- Endpoint dlp
- data loss prevention
- dlp policies
manager: dougeby
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- endpoint dlp
- data loss prevention
- dlp policies
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
description: يمكنك تنفيذ DLP لنقطة النهاية من خلال العمل مع فريق حماية المعلومات والحوكمة لإنشاء سياسات DLP لمنظمتك.
ms.openlocfilehash: c38171d790ffd376c7886da0547345cf7e74e36c
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/25/2022
ms.locfileid: "63572083"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>الخطوة 7. تنفيذ منع فقدان البيانات (DLP) باستخدام قدرات حماية المعلومات


إذا كانت مؤسستك قد وضعت الوقت بالفعل في فهم البيانات وتطوير مخطط حساسية البيانات وتطبيق المخطط، فقد تكون جاهزا لتوسيع عناصر هذا المخطط إلى نقاط النهاية باستخدام سياسات منع فقدان البيانات (DLP). 

ينطبق منع فقدان بيانات نقطة نهاية Microsoft (DLP) حاليا على:
- Windows 10، Windows 11
- macOS

يتم إنشاء سياسات DLP بواسطة فريق حماية المعلومات والحوكمة. يعرف كل نهج DLP العناصر داخل مجموعة البيانات التي يجب البحث عنها، مثل أنواع المعلومات الحساسة أو التسميات، وكيفية حماية هذه البيانات. 

على سبيل المثال، يمكن أن تبحث سياسة DLP عن بيانات شخصية مثل رقم جواز السفر. سيتضمن نهج DLP شرطا يؤدي إلى تشغيل النهج لاتخاذ إجراء، مثل مشاركة رقم جواز سفر مع أشخاص من خارج مؤسستك. يمكن تكوين الإجراء الذي يتخذه النهج أيضا. تتراوح الخيارات من مجرد الإبلاغ عن الإجراء إلى المسؤولين أو تحذير المستخدمين أو حتى منع مشاركة البيانات.

يحدد نهج DLP أيضا الموقع الذي يجب تطبيق النهج عليه، Exchange البريد الإلكتروني SharePoint المواقع. أحد المواقع المتوفرة للمسؤولين هو الأجهزة. إذا تم تحديد الأجهزة، يمكنك تحديد المستخدمين ومجموعات المستخدمين التي يجب تطبيق النهج عليها. يمكنك أيضا تحديد المستخدمين ومجموعات المستخدمين للاستبعاد من النهج.

إذا كان فريق حماية المعلومات والحوكمة جاهزا لتوسيع سياسات DLP لتمتد إلى نقاط النهاية، ستحتاج إلى التنسيق معها لتمكين الأجهزة ل DLP لنقطة النهاية واختبار سياسات DLP وضبطها وتدريب المستخدمين ومراقبة النتائج. 

![خطوات DLP لنقطة النهاية لمسؤول الجهاز](../media/devices/endpoint-dlp-steps.png#lightbox)

إذا أكملت [الخطوة 2. تسجيل الأجهزة في الإدارة](manage-devices-with-intune-enroll.md) [والخطوة 6. تسجيل الأجهزة في Defender for Endpoint](manage-devices-with-intune-monitor-risk.md) لمراقبة مخاطر الأجهزة وتوافقها مع خطوط الأمان الأساسية، تم تمكين أجهزتك بالفعل ل Endpoint DLP. 


استخدم الخطوات التالية للعمل مع فريق حماية المعلومات.


|الخطوة  |الوصف  |
|---------|---------|
|1     |  [تعرف على Microsoft 365 فقدان بيانات نقطة النهاية](../compliance/endpoint-dlp-learn-about.md).        |
|2     | تمكين الأجهزة ل DLP نقطة النهاية. إذا قمت ب علي الأجهزة المجهزه ب Microsoft Defender ل Endpoint، يتم تمكين أجهزتك بالفعل ل DLP نقطة النهاية. إذا كانت أجهزتك غير مجهزه في Defender for Endpoint، راجع بدء استخدام منع فقدان بيانات [نقطة](../compliance/endpoint-dlp-getting-started.md) النهاية للحصول على الإرشادات.|
|3     |   اعمل مع فريق حماية المعلومات والحوكمة لتحديد النهج واختبارها وضبطها. يشمل ذلك مراقبة النتائج. راجع هذه الموارد:<br>- [استخدام منع فقدان البيانات في نقطة النهاية](../compliance/endpoint-dlp-using.md)<br>- [عرض التقارير لمنع فقدان البيانات](../compliance/view-the-dlp-reports.md)      |
|     |         |