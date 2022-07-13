---
title: الخطوة 7. ترقية بيئة تقييم Microsoft 365 Defender إلى الإنتاج
description: استخدم هذه المقالة لترقية قيم MDI وMDO و MDE و Defender for Cloud Apps إلى بيئتك المباشرة في Microsoft 365 Defender أو M365D.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 769a70177ada62b4dbb505a8363fe3bdbfc4a59a
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748726"
---
# <a name="step-7-promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>الخطوة 7. ترقية بيئة تقييم Microsoft 365 Defender إلى الإنتاج

**ينطبق على:**
- Microsoft 365 Defender

لترقية بيئة تقييم Microsoft 365 Defender إلى الإنتاج، قم أولا بشراء الترخيص الضروري. اتبع الخطوات [الواردة في إنشاء بيئة التقييم](eval-create-eval-environment.md) وشراء ترخيص Office 365 E5 (بدلا من تحديد بدء الإصدار التجريبي المجاني).

بعد ذلك، أكمل أي تكوين إضافي وقم بتوسيع مجموعات الإصدار التجريبي الخاصة بك حتى تصل إلى الإنتاج الكامل.

## <a name="microsoft-defender-for-identity"></a>Microsoft Defender للهوية

لا يتطلب Defender for Identity أي تكوين إضافي. ما عليك سوى التأكد من أنك اشتريت التراخيص الضرورية وثبتت جهاز الاستشعار على جميع وحدات تحكم مجال Active Directory وخوادم خدمات الأمان المشترك لـ Active Directory (AD FS).

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender لـ Office 365

بعد تقييم MDO أو إصداره التجريبي بنجاح، يمكن ترقيته إلى بيئة الإنتاج بأكملها.

1. قم بشراء التراخيص الضرورية وتوفيرها وتعيينها لمستخدمي الإنتاج.
2. أعد تشغيل تكوينات نهج الأساس الموصى بها (إما قياسية أو صارمة) مقابل مجال البريد الإلكتروني للإنتاج أو مجموعات معينة من المستخدمين.
3. يمكنك إنشاء أي نهج MDO مخصصة وتكوينها بشكل اختياري مقابل مجال البريد الإلكتروني للإنتاج أو مجموعات المستخدمين.  ومع ذلك، تذكر أن أي نهج أساسية معينة ستكون لها الأسبقية دائما على النهج المخصصة.
4. قم بتحديث سجل MX العام لمجال البريد الإلكتروني للإنتاج الخاص بك لحله مباشرة إلى EOP.
5. قم بإيقاف تشغيل أي بوابات SMTP تابعة لجهة خارجية وتعطيل أو حذف أي موصلات EXO مقترنة بهذا المرحل.

## <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

لترقية بيئة التقييم Microsoft Defender لنقطة النهاية من الإصدار التجريبي إلى الإنتاج، ما عليك سوى إلحاق المزيد من نقاط النهاية بالخدمة باستخدام أي من [الأدوات والأساليب المدعومة](../defender-endpoint/onboard-configure.md).

استخدم الإرشادات العامة التالية لإلحاق المزيد من الأجهزة Microsoft Defender لنقطة النهاية.

1. تحقق من أن الجهاز يفي [بالحد الأدنى من المتطلبات](../defender-endpoint/minimum-requirements.md).
2. اعتمادا على الجهاز، اتبع خطوات التكوين المتوفرة في قسم الإلحاق في مدخل Defender لنقطة النهاية.
3. استخدم أداة الإدارة المناسبة وطريقة النشر لأجهزتك.
4. قم بتشغيل اختبار الكشف للتحقق من أن الأجهزة تم إلحاقها بشكل صحيح وإعداد التقارير إلى الخدمة.

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

لا يتطلب Microsoft Defender for Cloud Apps أي تكوين إضافي. ما عليك سوى التأكد من أنك اشتريت التراخيص الضرورية. إذا حددت نطاق النشر لمجموعات مستخدمين معينة، فقم بزيادة نطاق هذه المجموعات حتى تصل إلى مقياس الإنتاج.
