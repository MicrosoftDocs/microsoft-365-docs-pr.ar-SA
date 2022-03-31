---
title: استخدام Power Automate
description: تعرف على المزيد حول التشغيل التلقائي Microsoft 365 Defender وكيفية استخدامها.
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، و microsoft 365، و m365، والبحث، والاستعلام، والتعقب، والكشف المخصص، والم المخططات، والمناظير
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
ms.openlocfilehash: a707de259897080f8e726aed70618ea6505bdea6
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/03/2021
ms.locfileid: "63578462"
---
# <a name="use-power-automate-in-microsoft-365-defender"></a>استخدم Power Automate في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

> هل تريد تجربة Microsoft 365 Defender؟ يمكنك [تقييمه في بيئة معملية](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) أو [تشغيل مشروعك التجريبي في الإنتاج](m365d-pilot.md?ocid=cx-evalpilot).
>

تحتاج فرق عمليات الأمان الحديثة (SecOps) إلى التنفيذ التلقائي للعمل بفعالية. للتركيز على الصيد والتحري عن التهديدات الحقيقية، تستخدم فرق SecOps Power Automate للفرز عبر قائمة التنبيهات وإزالة تلك التي ليست تهديدات.  

## <a name="criteria-for-resolving-alerts"></a>معايير حل التنبيهات

- تم تشغيل رسالة "خارج المكتب" للمستخدم

- لا يتم وضع علامة على المستخدم كخطر عال

إذا كان كل منهما صحيحا، فإن SecOps يصادف التنبيه على أنه سفر شرعي ويحله. يتم نشر إعلام في Microsoft Teams بعد حل التنبيه. 

## <a name="connect-power-automate-to-microsoft-cloud-app-security"></a>الاتصال Power Automate Microsoft Cloud App Security

لإنشاء التنفيذ التلقائي، ستحتاج إلى رمز API مميز قبل أن تتمكن من Power Automate Microsoft Cloud App Security (MCAS). 

1. انقر **الإعدادات**، وحدد **ملحقات الأمان**، ثم انقر فوق **إضافة** رمز مميز في علامة التبويب **رموز API المميزة**. 

2. قم بتوفير اسم لرمزك المميز، ثم انقر فوق **إنشاء**. احفظ الرمز المميز كما ستحتاج إليه لاحقا.

## <a name="create-an-automated-flow"></a>إنشاء تدفق تلقائي

للحصول على العملية المفصلة خطوة بخطوة، راجع الفيديو [هنا](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn). 

يصف هذا الفيديو أيضا كيفية توصيل الطاقة التلقائية ب MCAS. 

## <a name="related-information"></a>المعلومات ذات الصلة

- [دمج Power Automate مع Microsoft Cloud App Security](/cloud-app-security/flow-integration)

- [وثائق Microsoft Power Automate Microsoft](/power-automate)
