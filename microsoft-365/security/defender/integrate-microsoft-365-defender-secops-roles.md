---
title: الخطوة 4. تحديد الأدوار والمسؤوليات والرقابة Microsoft 365 Defender
description: أساسيات تحديد الأدوار والمسؤوليات والرقابة عند دمج Microsoft 365 Defender في عمليات الأمان الخاصة بك.
keywords: الحوادث، والتنبيهات، والتحقيق، والارتباط، والهجمات، والأجهزة، والمستخدمين، والهويات، والهوية، وعلبة البريد، والبريد الإلكتروني، و365، وmicrosoft، Microsoft 365، والاستجابة للحوادث، والهجمات الإلكترونية، وعمليات secops، وعمليات الأمان، وsoc
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
ms.openlocfilehash: 5410db413ece81a39453070985e6c744e8b684a6
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664051"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>الخطوة 4. تحديد الأدوار والمسؤوليات والرقابة Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يجب على مؤسستك تحديد الملكية والمساءلة لتراخيص Microsoft 365 Defender والتكوينات والإدارة كمهام أولية قبل تحديد أي أدوار تشغيلية. عادة ما تقع ملكية التراخيص وتكاليف الاشتراك وإدارة خدمات Microsoft 365 وأمان المؤسسة + التنقل (EMS) (التي قد تتضمن Microsoft 365 Defender) خارج فرق مركز عمليات الأمان (SOC). يجب أن تعمل فرق SOC مع هؤلاء الأفراد لضمان الإشراف المناسب على Microsoft 365 Defender. 

تقوم العديد من وحدات SOCs الحديثة بتعيين أعضاء فريقها إلى فئات استنادا إلى مجموعات المهارات والوظائف الخاصة بهم. على سبيل المثال:

- فريق تحليل ذكي للمخاطر تم تعيينه للمهام المتعلقة بإدارة دورة حياة وظائف التهديد والتحليلات.
- فريق مراقبة يتكون من محللي SOC المسؤولين عن الحفاظ على السجلات والتنبيهات والأحداث ووظائف المراقبة.
- فريق عمليات & هندسي تم تعيينه لهندسة أجهزة الأمان وتحسينها.

ومن الطبيعي أن تتكامل أدوار فريق SOC ومسؤولياته Microsoft 365 Defender في هذه الفرق.

يقسم الجدول التالي أدوار ومسؤوليات كل فريق من فرق SOC وكيفية تكامل أدوارهم مع Microsoft 365 Defender.

| فريق SOC | الأدوار والمسؤوليات | المهام Microsoft 365 Defender  |
|:-------|:-----|:-------|
| الإشراف على SOC | <ul><li>تنفيذ حوكمة SOC</li><li>إنشاء عمليات يومية أو أسبوعية أو شهرية</li><li>توفير التدريب والوعي</li><li>توظيف الموظفين والمشاركة في مجموعات النظير والاجتماعات</li><li>إجراء تمارين الفريق الأزرق والأحمر والأرجواني</ul>  | <ul><li>عناصر التحكم في الوصول إلى مدخل Microsoft 365 Defender</li><li>الاحتفاظ بميزة/عنوان URL وسجل تحديث الترخيص</li><li>الحفاظ على التواصل مع أصحاب المصلحة في مجال تكنولوجيا المعلومات والشؤون القانونية والتوافق والخصوصية</li><li>المشاركة في اجتماعات التحكم بالتغيير لمبادرات Microsoft 365 أو Microsoft Azure الجديدة</ul> |
| التحليلات & التحليلات الذكية للمخاطر  | <ul><li>إدارة موجز intel للمخاطر</li><li>إسناد الفيروسات والبرامج الضارة</li><li>نمذجة المخاطر & تصنيفات أحداث التهديد</li><li>تطوير سمة التهديد من Insider </li><li>تكامل Intel للمخاطر مع برنامج إدارة المخاطر</li><li>دمج رؤى البيانات مع علوم البيانات و BI والتحليلات عبر فرق الموارد البشرية والشؤون القانونية وتقنية المعلومات والأمان<ul> | <ul><li>يحافظ على نمذجة المخاطر Microsoft Defender for Identity</li><li>يحافظ على نمذجة المخاطر Microsoft Defender لـ Office 365</li><li>يحافظ على Microsoft Defender لنقطة النهاية نمذجة المخاطر</ul> |
| رصد | <ul><li>الطبقة 1، 2، 3 محللين</li><li>صيانة مصدر السجل وهندسةه</li><li>استيعاب مصدر البيانات </li><li>تحليل SIEM، والتنبيه، والارتباط، والتحسين</li><li>إنشاء الحدث والتنبيه</li><li>تحليل الحدث والتنبيه</li><li>تقارير الأحداث والتنبيهات</li><li>صيانة نظام التذاكر</ul> | يستخدم: <ul><li>مركز توافق & الأمان</li><li>مدخل Microsoft 365 Defender</ul> |
| هندسة & SecOps | <ul><li>إدارة الثغرات الأمنية للتطبيقات والأنظمة ونقاط النهاية</li><li>أتمتة XDR/SOAR</li><li>اختبار التوافق</li><li>التصيد الاحتيالي وهندسة DLP</li><li>الهندسه</li><li>عنصر تحكم تغيير الإحداثيات</li><li>إحداثيات تحديثات دفتر التشغيل</li><li>اختبار الاختراق<ul> | <ul><li>Microsoft Defender for Cloud Apps</li><li>Defender لنقطة النهاية</li><li>Defender for Identity</ul> |
| فريق الاستجابة لحوادث أمان الكمبيوتر (CSIRT) | <ul><li>التحقيق في الحوادث الإلكترونية والاستجابة لها</li><li>تنفيذ الطب الشرعي</li><li>**قد يكون غالبا معزولا عن SOC**</ul> | التعاون والحفاظ على أدلة مبادئ الاستجابة للحوادث Microsoft 365 Defender |
||||


## <a name="next-step"></a>الخطوة التالية

[الخطوة 5. تطوير حالات الاستخدام واختبارها](integrate-microsoft-365-defender-secops-use-cases.md)
