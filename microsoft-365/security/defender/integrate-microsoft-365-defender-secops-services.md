---
title: الخطوة 3. التخطيط لتكامل Microsoft 365 Defender مع كتالوج خدمات SOC
description: أساسيات دمج Microsoft 365 Defender في كتالوج خدمات عمليات الأمان.
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
ms.openlocfilehash: 45497f74db9c68959d4b23e013c6ea483e86378a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578432"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>الخطوة 3. التخطيط لتكامل Microsoft 365 Defender مع كتالوج خدمات SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يجب أن يتضمن مركز عمليات الأمان (SOC) المنشأ كتالوج خدمات قد يتضمن:

- تحليل & البرامج الضارة
- الهندسة العكسية & الإسناد
- المعلومات الاستخبارية للتهديدات
- التحليلات
- التحقيق في الصيد
- الطب الشرعي
- استجابة للحوادث 
- فريق الاستجابة لحادث أمان الكمبيوتر (CSIRT) (الذي قد يتم فصله عن SOC) 
- اختبار التوافق
- تهديدات Insider & الاحتيال
- مراقبة أحداث & الأمان 
- فحص الثغرة
- الكشف والاستجابة الموسعة (XDR)/تنظيم الأمان والأتمتة والاستجابة (SOAR)
- التصيد الاحتيالي
- منع فقدان البيانات
- مراقبة العلامة التجارية

نظرا Microsoft 365 Defender التقنيات عبر دالات مختلفة، سيحتاج فريق SOC إلى تحديد الأدوار والمسؤوليات الأكثر ملاءمة لإدارة كل مكون من مكونات Microsoft 365 Defender والمحاذاة إلى وظيفة الخدمة.

مكونات Microsoft 365 Defender هي:

- **Microsoft Defender for Identity** (المعروف سابقا باسم Azure Advanced Threat Protection، المعروف أيضا ب Azure ATP) هو حل أمان مستند إلى السحابة يستخدم إشارات خدمات مجال Active Directory (AD DS) لتحديد التهديدات المتقدمة والهويات المضرة والإجراءات الضارة ل insider الموجهة إلى المؤسسات والكشف عنها والتحقق من وجودها.

- **Microsoft Defender ل Endpoint** هو حل أمان شامل يتم تسليمه عبر السحابة للأجهزة التي تتضمن التقييمات المستندة إلى المخاطر إدارة الثغرات الأمنية والحد من سطح الهجوم والحماية السلوكية المستندة إلى السحابة والجيل التالي، الكشف عن تهديدات نقاط النهاية والرد عليها ( الكشف التلقائي والاستجابة على النقط النهائية)، والتحري والوساطة التلقائية، وخدمات الصيد المدارة، و واجهات برمجة التطبيقات الغنية، وإدارة الأمان الموحدة.

 - **Microsoft Defender ل Office 365** هو خدمة لتصفية البريد الإلكتروني مستندة إلى السحابة وتساعد على حماية المؤسسات من البرامج الضارة والفيروسات غير المعروفة من خلال توفير حماية قوية لمدة صفرية وتتضمن ميزات لحماية المؤسسات من الارتباطات الضارة في الوقت الحقيقي. كما يوفر أيضا مجموعة شاملة من التحقيق والصيد والاستجابة والرد والرد والوعي والتدريب وميزات الوضع الآمن.

- **Microsoft Defender for Cloud Apps** هو وسيط أمان الوصول السحابي (CASB) الذي يدعم أوضاع النشر المختلفة بما في ذلك مجموعة السجلات وموصلات API والوكيل العكسي. فهو يوفر رؤية غنية، والتحكم في تنقل البيانات، وتحليلات متطورة لتحديد مكافحة التهديدات الإلكترونية عبر جميع خدمات Microsoft وسحابة  الجهة الخارجية.

نظرا Microsoft 365 Defender المكونات والتقنيات عبر وظائف مختلفة، سيحتاج فريق SOC إلى تحديد الأدوار والمسؤوليات الأكثر ملاءمة لإدارة كل مكون من مكونات Microsoft 365 Defender والمحاذاة إلى وظيفة الخدمة.

لدمج قدرات Microsoft 365 Defender، ستحتاج إلى تحسين خدمات SOC. لمزيد من المعلومات حول إمكانيات Microsoft 365 Defender، راجع المقالات التالية:

- [ما هو Microsoft Defender لنقطة النهاية؟](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [ما هو Microsoft Defender for Identity؟](/defender-for-identity/what-is)
- [ما هو Defender for Office 365؟](/office-365-security/defender-for-office-365)
- [ما هو Microsoft Defender لتطبيقات السحابة؟](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>الخطوة التالية

[الخطوة 4. تعريف Microsoft 365 Defender الأدوار والمسؤوليات والإشراف](integrate-microsoft-365-defender-secops-roles.md)
