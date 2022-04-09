---
title: استكشاف مشكلات خدمة Microsoft 365 Defender وإصلاحها
description: البحث عن حلول وحلول بديلة للمشاكل Microsoft 365 Defender المعروفة
keywords: استكشاف أخطاء Microsoft 365 Defender وإصلاحها Microsoft Defender for Identity والمشاكل والوظيفة الإضافية وصفحة الإعدادات
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 656599cf9ec66987119819b2f28f9a8eff1d4e77
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731659"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>استكشاف مشكلات خدمة Microsoft 365 Defender وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يعالج هذا القسم المشاكل التي قد تنشأ عند استخدام خدمة Microsoft 365 Defender.

## <a name="i-dont-see-microsoft-365-defender-content"></a>لا يمكنني رؤية محتوى Microsoft 365 Defender

إذا لم تتمكن من رؤية القدرات في جزء التنقل مثل Incidents أو Action center أو Hunting في المدخل الخاص بك، فستحتاج إلى التحقق من أن المستأجر الخاص بك لديه التراخيص المناسبة.

لمزيد من المعلومات، راجع [المتطلبات الأساسية](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>لا تظهر التنبيهات Microsoft Defender for Identity في حوادث Microsoft 365 Defender

إذا تم نشر Microsoft Defender for Identity في بيئتك ولكنك لا ترى تنبيهات Defender for Identity كجزء من أحداث Microsoft 365 Defender، فستحتاج إلى التأكد من أن Microsoft Defender for Cloud Apps  ويتم تمكين تكامل Defender for Identity.

لمزيد من المعلومات، راجع [Microsoft Defender for Identity التكامل](/cloud-app-security/mdi-integration).

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>أين توجد صفحة الإعدادات لتشغيل الخدمة؟

لتشغيل Microsoft 365 Defender، **الإعدادات** الوصول من جزء التنقل في مدخل Microsoft 365 Defender. يكون عنصر التنقل هذا مرئيا فقط إذا كان لديك [أذونات وتراخيص المتطلبات الأساسية](m365d-enable.md#check-license-eligibility-and-required-permissions).

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>كيف أعمل إنشاء استثناء للملف/URL الخاص بي؟

الإيجابية الخاطئة هي ملف أو URL يتم اكتشافه على أنه ضار ولكنه ليس تهديدا. يمكنك إنشاء مؤشرات وتحديد الاستثناءات لإلغاء حظر بعض الملفات/عناوين URL والسماح بها. راجع [النتائج الإيجابية/السلبيات الخاطئة للعنوان في Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives).
