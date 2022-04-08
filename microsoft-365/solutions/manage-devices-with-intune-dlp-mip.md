---
title: الخطوة 7. تنفيذ تفادي فقدان البيانات (DLP) مع قدرات حماية المعلومات
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
description: تنفيذ DLP نقطة النهاية من خلال العمل مع فريق حماية المعلومات والحوكمة لإنشاء نهج DLP لمؤسستك.
ms.openlocfilehash: ab0be14f0a20f35044489e7f3ad0ba3f60180bcd
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705176"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>الخطوة 7. تنفيذ تفادي فقدان البيانات (DLP) مع قدرات حماية المعلومات


إذا كانت مؤسستك تستخدم Microsoft 365 حماية البيانات وقد وضعت الوقت لفهم بياناتك وتطوير مخطط حساسية البيانات وتطبيق المخطط، فقد تكون مستعدا لتوسيع عناصر هذا المخطط إلى نقاط النهاية باستخدام نهج منع فقدان البيانات (DLP). 

ينطبق حاليا منع فقدان بيانات نقطة النهاية من Microsoft (DLP لنقطة النهاية) على:
- Windows 10، Windows 11
- ماك

يتم إنشاء نهج DLP بواسطة فريق حماية المعلومات والحوكمة. يحدد كل نهج DLP العناصر داخل مجموعة البيانات للبحث عنها، مثل أنواع المعلومات الحساسة أو التسميات، وكيفية حماية هذه البيانات. 

على سبيل المثال، يمكن لنهج DLP البحث عن البيانات الشخصية مثل رقم جواز السفر. سيتضمن نهج منع فقدان البيانات شرطا يشغل النهج لاتخاذ إجراء، مثل عندما تتم مشاركة رقم جواز سفر مع أشخاص من خارج مؤسستك. يمكن تكوين الإجراء الذي يتخذه النهج أيضا. تتراوح الخيارات من مجرد الإبلاغ عن الإجراء إلى المسؤولين، أو تحذير المستخدمين، أو حتى منع مشاركة البيانات.

يحدد نهج DLP أيضا الموقع الذي يجب تطبيق النهج عليه، مثل Exchange البريد الإلكتروني ومواقع SharePoint. أحد المواقع المتوفرة للمسؤولين هو الأجهزة. إذا تم تحديد الأجهزة، يمكنك تحديد المستخدمين ومجموعات المستخدمين التي يجب تطبيق النهج عليها. يمكنك أيضا تحديد المستخدمين ومجموعات المستخدمين لاستثنائهم من النهج.

إذا كان فريق حماية المعلومات والحوكمة جاهزا لتوسيع نهج DLP إلى نقاط النهاية، فستحتاج إلى التنسيق معها لتمكين الأجهزة الخاصة ب DLP لنقطة النهاية، واختبار نهج DLP وضبطها، وتدريب المستخدمين، ومراقبة النتائج. 

![خطوات DLP لنقطة النهاية لمسؤول الجهاز](../media/devices/endpoint-dlp-steps.png#lightbox)


استخدم الخطوات التالية للعمل مع فريق حماية المعلومات.


|خطوه  |الوصف  |
|---------|---------|
|1     |  [تعرف على Microsoft 365 منع فقدان بيانات نقطة النهاية](../compliance/endpoint-dlp-learn-about.md).        |
|2     | إلحاق الأجهزة ل DLP لنقطة النهاية. إذا قمت بإلحاق الأجهزة Microsoft Defender لنقطة النهاية، يتم بالفعل إلحاق أجهزتك بتوافق Microsoft 365، بما في ذلك DLP لنقطة النهاية. إذا لم يتم إلحاق أجهزتك ب Defender لنقطة النهاية، فراجع [بدء استخدام منع فقدان بيانات نقطة النهاية](../compliance/endpoint-dlp-getting-started.md) للحصول على الإرشادات. لمزيد من المعلومات حول كيفية عمل الإلحاق، راجع [تسجيل الأجهزة مقابل أجهزة الإلحاق](manage-devices-with-intune-overview.md#enrolling-devices-vs-onboarding-devices)|
|3     |   اعمل مع فريق حماية المعلومات والحوكمة لتحديد النهج واختبارها وضبطها. وهذا يشمل مراقبة النتائج. راجع هذه الموارد:<br>- [استخدام منع فقدان بيانات نقطة النهاية](../compliance/endpoint-dlp-using.md)<br>- [عرض التقارير لمنع فقدان البيانات](../compliance/view-the-dlp-reports.md)      |
