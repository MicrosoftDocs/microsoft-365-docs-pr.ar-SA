---
title: الخطوة 6. تحديد مهام صيانة SOC
description: حدد مهام صيانة SOC عند Microsoft 365 Defender في عمليات الأمان.
keywords: الأحداث والتنبيهات والتحري والارتباط والهجمة والأجهزة والمستخدمين والهويات والهوية علبة البريد والبريد الإلكتروني و365 و microsoft و m365 والاستجابة للحوادث والهجمة الإلكترونية والمناظير وعمليات الأمان وcc
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
ms.openlocfilehash: 33dd846b54072551d2624bec0e025dad9f269b03
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583382"
---
# <a name="step-6-identify-soc-maintenance-tasks"></a>الخطوة 6. تحديد مهام صيانة SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

فيما يلي المهام الدورية أو المطلوبة للحفاظ على SOC Microsoft 365 Defender.

| Activity  | الوصف | التكاتف | الفريق المعين |
|:-------|:-----|:-------|:-------|
| التعاون في إدارة الخدمة مع SOC Teams   | إدارة الخدمات الطرفية مثل تعقب الأصول (CMDB) وترخيص التطبيقات (تراخيص SaaS الجديدة) ومشتريات الأجهزة (ترقيات أو تجديد عمليات نشر الأجهزة) والتغييرات الأخرى على نطاق المستأجر Microsoft 365 (Intune و Microsoft 365 وغيرها) التي قد تؤثر على نشر منتجات Microsoft 365 Defender. | أسبوعيا وكما هو مطلوب   | الهندسة & SecOps | 
| تحديث حملات مكافحة التصيد الاحتيالي ومنع فقدان البيانات | تضمين حالات استخدام SOC والدروس المستفادة مع المؤسسة الموسعة (الموارد البشرية والموارد القانونية والتدريب وغيرها).  | شهريا وكما هو مطلوب | مراقبة SOC |
| نشر البرامج النصية والخدمات التلقائية عند الاقتضاء | قم بتنزيل البرامج النصية التلقائية وملفات التكوين واختبارها من مواقع Microsoft المعتمدة لتحسين Microsoft 365 Defender العمليات. | أسبوعيا وكما هو مطلوب | الهندسة و SecOps | 
| إدارة المدخل أو الترخيص | تحقق من الإعلانات المراسلة من Microsoft مركز Microsoft 365 Defender الإلكتروني أو متطلبات الترخيص استنادا إلى تحديثات Microsoft والميزات الجديدة. | أسبوعيا | مراقبة SOC| 
| تحديث تذاكر تصاعد SOC | كل فرق SOC تحديث تذاكر التصاعد (مثل Sentinel، تذاكر ServiceNow) المعينة لهم. | يوميا | جميع فرق SOC | 
| تعقب Microsoft 365 Defender المخاطر & إصلاح الثغرات | إنشاء نشاط إصلاح النقاط الآمنة ل TvM وإنشاء تقرير لمالكي الأصول من خلال مدخل إنترانت. | يوميا | المراقبة | 
| إنشاء تقرير نقاط آمنة | مراقبة مسارات الفريق والتقارير حول تحسينات "نقاط آمنة". | SOC أسبوعيا | المراقبة | 
| تشغيل تمرين IR tabletop | اختبر دفاتر تشغيل فريق SOC في تمرين الكمبيوتر اللوحي. | حسب الحاجة | جميع فرق SOC | 
|||||

ادمج هذه المهام في عمليات SOC الحالية.

## <a name="next-steps"></a>الخطوات التالية

يجب مراجعة الدليل المشار إليه في هذا المحتوى وفي مكتبة Microsoft 365 Defender لتحديد كيفية تنظيم [](/microsoft-365/security/defender) تنفيذ Microsoft 365 Defender الخاص بك وتكامله.
