---
title: الخطوة 6. تحديد مهام صيانة SOC
description: تحديد مهام صيانة SOC عند دمج Microsoft 365 Defender في عمليات الأمان الخاصة بك.
keywords: الحوادث، والتنبيهات، والتحقيق، والارتباط، والهجمات، والأجهزة، والمستخدمين، والهويات، والهوية، وعلبة البريد، والبريد الإلكتروني، و365، وmicrosoft، وm365، والاستجابة للحوادث، والهجمات الإلكترونية، وال secops، وعمليات الأمان، وsoc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 6b1ee22f8176d6f682eb9e9f2134cc27db91affd
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783590"
---
# <a name="step-6-identify-soc-maintenance-tasks"></a>الخطوة 6. تحديد مهام صيانة SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

فيما يلي المهام الدورية أو حسب الحاجة للحفاظ على SOC الخاص بك Microsoft 365 Defender.

|Activity|الوصف|الايقاع|تم تعيين الفريق|
|---|---|---|---|
|تعاون إدارة الخدمة مع SOC Teams|إدارة خدمات الأجهزة الطرفية مثل تعقب الأصول (CMDB) وترخيص التطبيق (تراخيص SaaS الجديدة) ومشتريات الأجهزة (ترقيات عمليات توزيع الأجهزة أو تجديدها) وغيرها من التغييرات Microsoft 365 على مستوى المستأجر (Intune Microsoft 365 وغيرها) التي قد تؤثر على نشر منتجات Microsoft 365 Defender.|أسبوعيا حسب الحاجة|هندسة & SecOps|
|تحديث حملات مكافحة التصيد الاحتيالي ومنع فقدان البيانات|دمج حالة استخدام SOC والدروس المستفادة مع المؤسسة الموسعة (الموارد البشرية والشؤون القانونية والتدريب وغيرها).|شهريا حسب الحاجة|الإشراف على SOC|
|توزيع البرامج النصية التلقائية والخدمات عند الاقتضاء|تنزيل واختبار البرامج النصية التلقائية وملفات التكوين من مواقع Microsoft المعتمدة لتحسين عمليات Microsoft 365 Defender.|أسبوعيا حسب الحاجة|الهندسة و SecOps|
|إدارة المدخل أو الترخيص|تحقق من الإعلانات ومركز المراسلة من Microsoft لبوابة Microsoft 365 Defender أو احتياجات الترخيص استنادا إلى تحديثات Microsoft والميزات الجديدة.|التنزيلات|الإشراف على SOC|
|تحديث تذاكر تصعيد SOC|تقوم جميع فرق SOC بتحديث تذاكر التصعيد (مثل Sentinel وتذاكر ServiceNow) المعينة لهم.|اليوميه|جميع فرق SOC|
|تعقب نشاط معالجة الثغرات الأمنية Microsoft 365 Defender & المخاطر|إنشاء نشاط معالجة النقاط الآمنة ل TvM وإعداد تقرير لمالكي الأصول من خلال مدخل إنترانت.|اليوميه|رصد|
|إنشاء تقرير نقاط آمنة|يتعقب فريق المراقبة تحسينات درجة الأمان ويبلغ بها.|SOC أسبوعيا|رصد|
|تشغيل تمرين IR tabletop|اختبار أدلة مبادئ فريق SOC في تمرين الكمبيوتر اللوحي.|حسب الحاجة|جميع فرق SOC|

دمج هذه المهام في عمليات SOC الحالية.

## <a name="next-steps"></a>الخطوات التالية

يجب مراجعة الدلائل المشار إليها في هذا المحتوى وفي [مكتبة Microsoft 365 Defender](/microsoft-365/security/defender) لتحديد كيفية تنظيم تنفيذك Microsoft 365 Defender وتكامله.
