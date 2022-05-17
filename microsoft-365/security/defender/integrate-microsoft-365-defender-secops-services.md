---
title: الخطوة 3. التخطيط للتكامل Microsoft 365 Defender مع كتالوج خدمات SOC
description: أساسيات دمج Microsoft 365 Defender في كتالوج عمليات الأمان الخاصة بك من الخدمات.
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
ms.openlocfilehash: f6cab6be7d41f1d71a6ccf69fbedfa616694ee78
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438477"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>الخطوة 3. التخطيط للتكامل Microsoft 365 Defender مع كتالوج خدمات SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يجب أن يحتوي مركز عمليات الأمان (SOC) المنشأة على كتالوج من الخدمات التي قد تتضمن:

- الاختراق & تحليل البرامج الضارة
- الإسناد & الهندسة العكسية
- التحليل الذكي للمخاطر
- تحليلات
- التحقيق في التتبع
- الطب الشرعي
- الاستجابة للحوادث 
- فريق الاستجابة لحوادث أمان الكمبيوتر (CSIRT) (الذي قد يتم فصله عن SOC) 
- اختبار التوافق
- مراقبة الاحتيال & المخاطر الداخلية
- مراقبة حدث & الأمان 
- فحص الثغرات الأمنية
- الكشف الموسع والاستجابة (XDR)/تزامن الأمان والأتمتة والاستجابة (SOAR)
- التصيّد الاحتيالي
- منع فقدان البيانات
- مراقبة العلامة التجارية

نظرا لأن تقنيات Microsoft 365 Defender تمتد عبر وظائف مختلفة، سيحتاج فريق SOC إلى تحديد الأدوار والمسؤوليات الأنسب لإدارة كل مكون من مكونات Microsoft 365 Defender والتوافق مع وظيفة الخدمة.

مكونات Microsoft 365 Defender هي:

- **Microsoft Defender for Identity** (المعروف سابقا باسم Azure Advanced Threat Protection، والمعروف أيضا باسم Azure ATP) هو حل أمان مستند إلى السحابة يستخدم إشارات خدمات مجال Active Directory (AD DS) لتحديد التهديدات المتقدمة والهويات المخترقة والإجراءات الداخلية الضارة الموجهة نحو المنظمات.

- **Microsoft Defender لنقطة النهاية** هو حل أمان شامل لنقطة النهاية التي توفرها السحابة للأجهزة التي تتضمن إدارة الثغرات الأمنية وتقييما قائمين على المخاطر، وتقليل الأجزاء المعرضة للهجوم، وحماية الجيل التالي المستندة إلى السلوك والمستندة إلى السحابة، الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية)، والتحقيق التلقائي والمعالجة، وخدمات التتبع المدارة، وواجهات برمجة التطبيقات الغنية، وإدارة الأمان الموحدة.

 - **Microsoft Defender لـ Office 365** هي خدمة تصفية بريد إلكتروني مستندة إلى السحابة تساعد على حماية المؤسسات من البرامج الضارة والفيروسات غير المعروفة من خلال توفير حماية قوية لمدة صفر يوم وتتضمن ميزات لحماية المؤسسات من الارتباطات الضارة في الوقت الحقيقي. كما يقدم مجموعة شاملة من التحقيق والتتبع، والاستجابة والمعالجة، والوعي والتدريب، وميزات الوضع الآمن.

- **Microsoft Defender for Cloud Apps** هو وسيط أمان الوصول إلى السحابة (CASB) الذي يدعم أوضاع النشر المختلفة بما في ذلك مجموعة السجلات وموصلات واجهة برمجة التطبيقات والوكيل العكسي. فهو يوفر رؤية غنية، والتحكم في نقل البيانات، وتحليلات متطورة لتحديد التهديدات الإلكترونية ومكافحتها عبر جميع خدمات Microsoft والخدمات السحابية لجهات خارجية.

نظرا لأن Microsoft 365 Defender المكونات والتقنيات تمتد عبر وظائف مختلفة، سيحتاج فريق SOC إلى تحديد الأدوار والمسؤوليات الأنسب لإدارة كل مكون من مكونات Microsoft 365 Defender والتوافق مع وظيفة الخدمة.

لدمج قدرات Microsoft 365 Defender، ستحتاج إلى تحسين خدمات SOC. لمزيد من المعلومات حول قدرات Microsoft 365 Defender، راجع المقالات التالية:

- [ما هو Microsoft Defender لنقطة النهاية؟](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [ما هو Microsoft Defender للهوية؟](/defender-for-identity/what-is)
- [ما هو Defender لـ Office 365؟](/microsoft-365/security/defender/microsoft-365-defender)
- [ما هو Microsoft Defender للتطبيقات السحابية؟](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>الخطوة التالية

[الخطوة 4. تحديد الأدوار والمسؤوليات والرقابة Microsoft 365 Defender](integrate-microsoft-365-defender-secops-roles.md)
