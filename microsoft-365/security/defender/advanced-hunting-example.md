---
title: مثال عن الصيد المتقدم ل Microsoft Defender Office 365
description: بدء البحث عن تهديدات البريد الإلكتروني باستخدام الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، عمليات الكشف المخصصة، المخطط، kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 04e4fd2267cc3774e9a816539f0de044ae988dfb
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/30/2021
ms.locfileid: "63578268"
---
# <a name="advanced-hunting-example-for-microsoft-defender-for-office-365"></a>مثال عن الصيد المتقدم ل Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

هل تريد بدء البحث عن تهديدات البريد الإلكتروني باستخدام عمليات البحث المتقدمة؟ جرب ما يلي:

المقطع ["بدء استخدام](/microsoft-365/security/office-365-security/defender-for-office-365#getting-started)" من [مقالة Microsoft Defender Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) على أجزاء تكوين منطقية مبكرة تبدو على الشكل التالي:

1. قم بتكوين كل شيء باستخدام 'Anti' في الاسم.
   - مكافحة البرامج الضارة
   - مكافحة التصيد الاحتيالي
   - مكافحة البريد العشوائي
2. قم بإعداد كل شيء باستخدام "خزينة" في الاسم.
   - الارتباطات الآمنة
   - خزينة المرفقات
3. ادافع عن أحمال العمل (على بعض الحالات. SharePoint عبر الإنترنت OneDrive و Teams).
4. الحماية باستخدام إزالة تلقائية بدون ساعة.

جنبا إلى [جنب مع ارتباط](../office-365-security/protect-against-threats.md) للانكمات مباشرة والحصول على التكوين في اليوم 1.

الخطوة الأخيرة في **بدء العمل** هي حماية المستخدمين باستخدام إزالة تلقائية بدون **ساعة**، المعروفة أيضا ب ZAP. يمكن أن تكون معرفة ما إذا كانت جهودك في ZAP لبريد مريب أو ضار، بعد التسليم، ناجحة جدا.

إن التنقل بسرعة إلى لغة استعلام Kusto للبحث عن المشاكل هو ميزة من ميزات تقارب هذين المركزين الأمنيين. يمكن لفرق الأمان مراقبة ميزات ZAP عن طريق تنفيذ خطواتها التالية [هنا](https://security.microsoft.com/advanced-hunting)، ضمن **"** \> **البحث عن طريق البحث المتقدم**".

1. في صفحة البحث المتقدم، انقر فوق **استعلام**.
1. انسخ الاستعلام أدناه إلى نافذة الاستعلام.
1. حدد **تشغيل الاستعلام**.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfullyconverge-2-endpoints-new.png
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

:::image type="content" source="../../media/ah-query-example-new.png" alt-text="تم تحديد صفحة البحث المتقدم (ضمن الصيد) باستخدام الاستعلام في أعلى لوحة الاستعلام، وتشغيل استعلام Kusto لالتقاط إجراءات ZAP على مدار آخر 7 أيام." lightbox="../../media/ah-query-example-new.png":::

ستظهر البيانات من هذا الاستعلام في لوحة النتائج أسفل الاستعلام نفسه. تتضمن النتائج معلومات مثل 'DeviceName' و'AccountDisplayName' و'ZapTime' في مجموعة نتائج قابلة للتخصيص. يمكن أيضا تصدير النتائج لسجلاتك. إذا كان الاستعلام واحدا ستحتاج إليه مرة أخرى، فحدد **حفظ** >  **حفظ باسم** وأضف الاستعلام إلى قائمة الاستعلامات أو الاستعلامات المشتركة أو استعلامات المجتمع.

## <a name="related-information"></a>المعلومات ذات الصلة
- [أفضل الممارسات المتقدمة للصيد](advanced-hunting-best-practices.md)
- [نظرة عامة - البحث المتقدم](advanced-hunting-overview.md)
