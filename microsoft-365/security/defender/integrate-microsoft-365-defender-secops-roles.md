---
title: الخطوة 4. تعريف Microsoft 365 Defender الأدوار والمسؤوليات والإشراف
description: أساسيات تحديد الأدوار والمسؤوليات والإشراف عند Microsoft 365 Defender في عمليات الأمان.
keywords: الأحداث والتنبيهات والتحري والارتباط والهجمة والأجهزة والمستخدمين والهويات والهوية علبة البريد والبريد الإلكتروني و365 و microsoft و Microsoft 365 والاستجابة للحوادث والهجمة الإلكترونية والمناظير وعمليات الأمان وcc
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
ms.openlocfilehash: 7562eca50b905bf70f17844cf8fe3079fbf3fc14
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63574403"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>الخطوة 4. تعريف Microsoft 365 Defender الأدوار والمسؤوليات والإشراف

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يجب أن تنشئ مؤسستك ملكية Microsoft 365 Defender والتكوينات والإدارة كمهام أولية قبل تحديد أي أدوار تشغيلية. عادة، تقع ملكية التراخيص وتكاليف الاشتراك وإدارة خدمات Microsoft 365 و Enterprise Security + Mobility (EMS) (التي قد تتضمن Microsoft 365 Defender) خارج فرق مركز عمليات الأمان (SOC). يجب أن تعمل فرق SOC مع هؤلاء الأفراد لضمان الإشراف المناسب على Microsoft 365 Defender. 

تقوم العديد من SOCs الحديثة بتعيين أعضاء فريقها إلى فئات استنادا إلى مهاراتهم ووظائفهم. على سبيل المثال:

- فريق المعلومات المتعلقة بالتهريب المعين للمهام ذات الصلة بإدارة دورة حياة وظائف المخاطر والتحليلات.
- فريق مراقبة يتألف من محللي SOC المسؤولين عن الاحتفاظ بالسجلات والتنبيهات والأحداث ووظائف المراقبة.
- فريق & عمليات هندسية تم تعيينه لمهندس أجهزة الأمان وتحسينها.

ستتكامل أدوار فريق SOC ومسؤولياته Microsoft 365 Defender في هذه الفرق بشكل طبيعي.

يفصل الجدول التالي أدوار كل فريق SOC ومسؤولياته وكيفية تكامل أدواره مع Microsoft 365 Defender.

| فريق SOC | الأدوار والمسؤوليات | Microsoft 365 Defender المهام  |
|:-------|:-----|:-------|
| مراقبة SOC | <ul><li>تنفيذ حوكمة SOC</li><li>إنشاء عمليات يومية أو أسبوعية أو شهرية</li><li>توفير التدريب والوعي</li><li>توظيف الموظفين والمشاركة في المجموعات والاجتماعات النظيرة</li><li>إجراء تمارين الفريق باللون الأزرق والأحمر والأرجواني</ul>  | <ul><li>Microsoft 365 Defender الوصول إلى المدخل</li><li>الاحتفاظ بميزة/URL وتسجيل تحديث الترخيص</li><li>الحفاظ على التواصل مع المساهمين في تكنولوجيا المعلومات والامتثال والخصوصية</li><li>المشاركة في اجتماعات التحكم بالتغيير لمبادرات Microsoft 365 أو Microsoft Azure</ul> |
| تحليل المعلومات & المخاطر  | <ul><li>إدارة موجز intel threat</li><li>إسناد الفيروسات والبرامج الضارة</li><li>تصنيفات أحداث & المخاطر</li><li>تطوير السمة الخاصة بخطر Insider </li><li>تكامل Intel threat مع برنامج إدارة المخاطر</li><li>دمج رؤى البيانات مع علم البيانات و المعلومات المعلوماتية والتحليلات عبر فرق الموارد البشرية والموارد البشرية والموارد القانونية وفرق المعلومات والأمان<ul> | <ul><li>الاحتفاظ بنموذج المخاطر في Microsoft Defender for Identity</li><li>الاحتفاظ ب Microsoft Defender Office 365 المخاطر</li><li>الاحتفاظ ب Microsoft Defender لنمذجة تهديدات نقطة النهاية</ul> |
| المراقبة | <ul><li>محللون من المستوى 1 و2 و3</li><li>صيانة مصدر السجلات والهندسة</li><li>استخدام مصدر البيانات </li><li>تحليل SIEM والتنبيه والارتباط والتحسين</li><li>حدث وتنبيه الجيل</li><li>تحليل الحدث والتنبيه</li><li>الإبلاغ عن الأحداث والتنبيهات</li><li>صيانة نظام التذاكر</ul> | الاستخدامات: <ul><li>مركز & الأمان</li><li>Microsoft 365 Defender المدخل</ul> |
| الهندسة & SecOps | <ul><li>إدارة نقاط الضعف للتطبيقات و الأنظمة ونقاط النهاية</li><li>التنفيذ التلقائي ل XDR/SOAR</li><li>اختبار التوافق</li><li>التصيد الاحتيالي وهندسة DLP</li><li>الهندسة</li><li>عنصر تحكم تغيير الإحداثيات</li><li>إحداثيات تحديثات دفتر التشغيل</li><li>اختبار الاختراق<ul> | <ul><li>Microsoft Defender لتطبيقات السحابة</li><li>Defender لنقطة النهاية</li><li>Defender for Identity</ul> |
| فريق الاستجابة لحادث أمان الكمبيوتر (CSIRT) | <ul><li>التحقيق في أحداث الإنترنت والرد عليها</li><li>إجراء التحليلات الجنائية</li><li>**قد تكون معزولة في أغلب الأحيان عن SOC**</ul> | التعاون في العمل والحفاظ على Microsoft 365 Defender الاستجابة للحوادث |
||||


## <a name="next-step"></a>الخطوة التالية

[الخطوة 5. تطوير حالات الاستخدام واختبارها](integrate-microsoft-365-defender-secops-use-cases.md)
