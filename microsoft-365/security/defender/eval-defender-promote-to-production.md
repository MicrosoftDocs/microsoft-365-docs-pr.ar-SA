---
title: الخطوة 7. ترقية بيئة Microsoft 365 Defender إلى الإنتاج
description: استخدم هذه المقالة للترويج ل evals من MDI و MDO و MDE و Defender لتطبيقات السحابة إلى بيئتك المباشرة في Microsoft 365 Defender أو M365D.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 47f36d965c9b2b6ef5f106c590e47fe0251163d8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63574012"
---
# <a name="step-7-promote-your-microsoft-365-defender-evaluation-environment-to-production"></a>الخطوة 7. ترقية بيئة Microsoft 365 Defender إلى إنتاج

**ينطبق على:**
- Microsoft 365 Defender

للترويج لبيئة Microsoft 365 Defender الخاصة بك للإنتاج، اشتر الترخيص اللازم أولا. اتبع الخطوات في [إنشاء بيئة eval](eval-create-eval-environment.md) وشراء ترخيص Office 365 E5 (بدلا من تحديد بدء الإصدار التجريبي المجاني).

بعد ذلك، أكمل أي تكوين إضافي ووسع مجموعاتك التجريبية حتى تصل إلى الإنتاج الكامل.

## <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

لا يتطلب Defender for Identity أي تكوين إضافي. ما عليك سوى التأكد من شراء التراخيص الضرورية وتثبيت المستشعر على كل وحدات التحكم في مجال Active Directory وخادمات خدمات Active Directory Federation Services (AD FS).

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender Office 365

بعد تقييم MDO أو تجريبه بنجاح، يمكن ترقيته إلى بيئة الإنتاج بأكملها.

1. قم بشراء التراخيص اللازمة وتوفيرها وتعيينها لمستخدمي الإنتاج.
2. إعادة تشغيل تكوينات نهج الأساس الموصى بها (إما قياسية أو صارمة) مقابل مجال بريدك الإلكتروني للإنتاج أو مجموعات معينة من المستخدمين.
3. يمكنك بشكل اختياري إنشاء أي من سياسات MDO المخصصة وتكوينها مقابل مجال البريد الإلكتروني للإنتاج أو مجموعات المستخدمين.  ومع ذلك، تذكر أن أي من سياسات الأساس المعينة ستتخذ دوما الأسبقية على السياسات المخصصة.
4. قم بتحديث سجل MX العام لمجال البريد الإلكتروني للإنتاج لحل EOP مباشرة.
5. قم بسحب أي بوابات SMTP من جهة خارجية وتعطيل أو حذف أي موصلات EXO مقترنة بهذا الترحيل.

## <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender لنقطة النهاية

للترويج لبيئة تقييم Microsoft Defender لنقطة النهاية من التجربة إلى الإنتاج، ما عليك سوى تهيئة المزيد من نقاط النهاية للخدمة باستخدام أي من الأدوات [والأساليب المعتمدة](../defender-endpoint/onboard-configure.md).

استخدم الإرشادات العامة التالية لتكوين المزيد من الأجهزة في Microsoft Defender لنقطة النهاية.

1. تحقق من أن الجهاز يفي [بالحد الأدنى من المتطلبات](../defender-endpoint/minimum-requirements.md).
2. استنادا إلى الجهاز، اتبع خطوات التكوين المتوفرة في قسم التهيئة في مدخل Defender for Endpoint.
3. استخدم أداة الإدارة المناسبة وطريقة النشر لأجهزتك.
4. يمكنك تشغيل اختبار الكشف للتحقق من أن الأجهزة مجهزه بشكل صحيح وتبلاغ الخدمة.

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender لتطبيقات السحابة

لا يتطلب Microsoft Defender لتطبيقات السحابة أي تكوين إضافي. ما عليك سوى التأكد من شراء التراخيص الضرورية. إذا قمت بنطاق النشر لمجموعات مستخدمين معينة، فزيد نطاق هذه المجموعات حتى تصل إلى مقياس الإنتاج.
