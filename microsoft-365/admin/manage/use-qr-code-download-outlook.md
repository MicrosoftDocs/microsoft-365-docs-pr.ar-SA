---
title: استخدام رمز الاستجابة السريعة (QR) تسجيل الدخول إلى Outlook الجوال
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
description: تعرف على كيفية استخدام رمز الاستجابة السريعة لمصادقة Outlook المحمول.
ms.openlocfilehash: 736628fb97cf2a6f4f6c6d175384a30c41bf642d
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/22/2021
ms.locfileid: "63570557"
---
# <a name="use-a-qr-code-to-sign-in-to-the-outlook-mobile-apps"></a>استخدام رمز الاستجابة السريعة (QR) تسجيل الدخول إلى Outlook الجوال

كمسؤول Microsoft 365، يمكنك تمكين المستخدمين من تسجيل الدخول Outlook لتطبيق Android أو iOS على أجهزتهم المحمولة دون الحاجة إلى إدخال اسم المستخدم وكلمة المرور. من خلال فحص رمز الاستجابة السريعة، يمكن للمستخدمين المصادقة بشكل آمن Outlook المحمول.

في Outlook على ويب تطبيقات سطح المكتب Outlook الأخرى، قد يرى المستخدمون إعلامات لإعلامهم بأنه يمكنهم استخدام Outlook على أجهزة المحمول الخاصة بهم. يمكن إدارة هذه الإعلامات بواسطة المسؤول باستخدام Exchange PowerShell. إذا اختار المستخدمون إرسال رسالة نصية قصيرة SMS لأنفسهم لتنزيل التطبيق على جهازهم المحمول، ستظهر رمز الاستجابة السريعة على أجهزة الكمبيوتر الخاصة بهم. وسيتمكن من فحص رمز الاستجابة السريعة لتسجيل الدخول إلى Outlook على الهاتف أو الكمبيوتر اللوحي. رمز الاستجابة السريعة هذا هو رمز مميز قصير يمكن استرداده مرة واحدة فقط.

يتم إنشاء الإعلام فقط إذا تم تحقيق الشروط التالية:

1. يتم تمكين تجربة رمز الاستجابة السريعة للمستأجر (يتم تمكين هذه التجربة بشكل افتراضي).

2. لا يستخدم المستخدم بالفعل Outlook لنظامي التشغيل iOS وAndroid.

3. لدى المستخدم حالة فارغة في جزء القراءة (لا يقوم بتحديد خيار فتح أول رسالة بريد إلكتروني تلقائية).

4. لم يتجاهل المستخدم الإعلام.

> [!NOTE]
> في بعض الحالات، يجب على المستخدمين إعادة المصادقة على أجهزة الكمبيوتر الخاصة بهم لإنشاء رمز الاستجابة السريعة.

## <a name="use-exchange-powershell"></a>استخدام Exchange PowerShell

تكون هذه الميزة في وضع الإعداد الافتراضي. لتعطيل هذه الميزة، اتبع الخطوات أدناه.

1. [الاتصال Exchange PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. باستخدام PowerShell، يمكنك تعطيل الإعلامات التي تعلم المستخدمين Outlook تطبيقات الأجهزة المحمولة. يمنع ذلك أيضا عرض تدفق تسجيل الدخول إلى رمز الاستجابة السريعة.

```powershell
Set-OrganizationConfig -MobileAppEducationEnabled <Boolean>
```

> [!NOTE]
> عند استخدام Exchange PowerShell، قد يستغرق نشر التغييرات ما يصل إلى 8 ساعات.

## <a name="related-content"></a>المحتوى ذي الصلة

[إعداد خيارات الإصدار القياسي أو](release-options-in-office-365.md) المستهدف (مقالة)\
[Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) (مقالة)
