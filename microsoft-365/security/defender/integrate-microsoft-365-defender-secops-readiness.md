---
title: الخطوة 2. إجراء تقييم لجاهزية تكامل SOC باستخدام "إطار الثقة الصفري"
description: أساسيات إجراء تقييم لجاهزية تكامل SOC باستخدام إطار عمل الثقة الصفري عند Microsoft 365 Defender في عمليات الأمان.
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
ms.openlocfilehash: 1197edf14977c0232936531399d726f62ab70889
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570796"
---
# <a name="step-2-perform-a-soc-integration-readiness-assessment-using-the-zero-trust-framework"></a>الخطوة 2. إجراء تقييم لجاهزية تكامل SOC باستخدام "إطار الثقة الصفري"

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

بمجرد تحديد الوظائف الأساسية لفريق مركز عمليات الأمان (SOC)، فإن الخطوة التالية لمنظمتك هي التحضير لاعتماد Microsoft 365 Defender من خلال نهج [الثقة الصفرية](/security/zero-trust/). يمكن أن يساعدك الاعتماد على تحديد المتطلبات اللازمة Microsoft 365 Defender استخدام الممارسات الحديثة الرائدة في المجال، مع تقييم Microsoft 365 Defender في مقابل بيئتك.

يستند هذا النهج إلى أساس قوي من الحماية ويتضمن مجالات أساسية مثل الهوية ونقاط النهاية (الأجهزة) والبيانات والتطبيقات والبنية الأساسية والشبكات. سيحدد فريق تقييم الجهوزية المناطق التي لم يتم فيها بعد Microsoft 365 Defender المتطلبات الأساسية لتمكين الوصول إليها، وستحتاج إلى المعالجة.

فيما يلي بعض العناصر التي يجب إصلاحها لكي تتمكن SOC من تحسين العمليات بشكل كامل في SOC:

- **الهوية:** مجالات خدمات مجال Active Directory المحلية القديمة (AD DS) ولا خطة MFA ولا جرد للحسابات المتميزة وغيرها.
- **نقاط النهاية (الأجهزة):** عدد كبير من أنظمة التشغيل القديمة ومخزون الأجهزة المحدود وغيرها.
- **البيانات والتطبيقات:**  عدم وجود معايير لإدارة البيانات، وعدم وجود مخزون للتطبيقات المخصصة التي لن تتكامل.
- **البنية الأساسية:** عدد كبير من تراخيص SaaS غير الممنعة، بدون أمان حاويات، وغير ذلك.
- **الشبكات:** مشاكل الأداء بسبب انخفاض النطاق الترددي، الشبكة المسطحة، مشاكل الأمان اللاسلكي، وغيرها.

يجب على المؤسسات أيضا متابعة تشغيل [Microsoft 365 Defender](m365d-enable.md) لتسهيل مجموعة الأساسيات من متطلبات التكوين. ستحدد هذه الخطوات بدورها أنشطة المعالجة التي يجب على فرق SOC القيام بها لتطوير حالات الاستخدام بفعالية. 

يتم وصف إجراءات الاعتماد وإنشاء حالات الاستخدام في خطوتين 3 و4.

## <a name="next-step"></a>الخطوة التالية

[الخطوة 3. التخطيط لتكامل Microsoft 365 Defender مع كتالوج خدمات SOC](integrate-microsoft-365-defender-secops-services.md)
