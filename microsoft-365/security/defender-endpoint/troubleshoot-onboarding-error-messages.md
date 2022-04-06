---
title: استكشاف أخطاء الboard ورسائل الخطأ وإصلاحها
description: استكشاف مشاكل التكدث ورسالة الخطأ وإصلاحها أثناء إكمال إعداد Microsoft Defender لنقطة النهاية.
keywords: استكشاف الأخطاء وإصلاحها، Azure Active Directory، الادراج، رسالة الخطأ، رسائل الخطأ، microsoft defender لنقطة النهاية
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: cfbd91743ed2e61809d9e2b6f0243b5c327bdae4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467544"
---
# <a name="troubleshoot-subscription-and-portal-access-issues"></a>استكشاف مشاكل الوصول إلى المدخل والاشتراك وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troublshootonboarding-abovefoldlink)

توفر هذه الصفحة خطوات مفصلة لاستعلام الأخطاء التي قد تحدث عند إعداد Microsoft Defender لنقطة النهاية الخدمة.

إذا تلقيت رسالة خطأ، Microsoft 365 Defender هذه الرسالة شرحا مفصلا حول المشكلة وستوفر الارتباطات ذات الصلة.

## <a name="no-subscriptions-found"></a>لم يتم العثور على أي اشتراكات

إذا لم Microsoft 365 Defender رسالة تم العثور عليها من دون اشتراكات، فهذا يعني أن Azure Active Directory (Azure AD) المستخدم لتسجيل دخول المستخدم إلى المدخل، لا Microsoft Defender لنقطة النهاية ترخيص.

الأسباب المحتملة:

- تُعد تراخيص Windows E5 وOffice E5 تراخيص منفصلة.
- تم شراء الترخيص ولكن لم يتم توفيره لمثيل Azure AD هذا.
  - قد تكون مشكلة في توفير التراخيص.
  - قد تكون قمت عن غير قصد بتوفير الترخيص إلى Microsoft Azure AD مختلفة عن تلك المستخدمة للمصادقة في الخدمة.

في كلتا الحالتين، يجب الاتصال بدعم Microsoft في [دعم عام Microsoft Defender لنقطة النهاية دعم](https://support.microsoft.com/getsupport?wf=0&tenant=ClassicCommercial&oaspworkflow=start_1.0.0.0&locale=en-us&supportregion=en-us&pesid=16055&ccsid=636419533611396913) أو [دعم الترخيص بالحجم](https://www.microsoft.com/licensing/servicecenter/Help/Contact.aspx).

:::image type="content" source="images/atp-no-subscriptions-found.png" alt-text="الصفحة &quot;لا توجد اشتراكات&quot;" lightbox="images/atp-no-subscriptions-found.png":::

## <a name="your-subscription-has-expired"></a>انتهت صلاحية اشتراكك

إذا انتهت صلاحية Microsoft 365 Defender عند الوصول إلى رسالة انتهت صلاحية اشتراكك، فقد انتهت صلاحية اشتراك الخدمة عبر الإنترنت. Microsoft Defender لنقطة النهاية الاشتراك، مثل أي اشتراك خدمة عبر الإنترنت آخر، تاريخ انتهاء الصلاحية.

يمكنك اختيار تجديد الترخيص أو تمديده في أي وقت. عند الوصول إلى المدخل بعد تاريخ انتهاء الصلاحية،  سيتم تقديم رسالة انتهت صلاحية اشتراكك مع خيار لتنزيل حزمة إلغاء ازاله الجهاز، إذا اخترت عدم تجديد الترخيص.

> [!NOTE]
> لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

:::image type="content" source="images/atp-subscription-expired.png" alt-text="رسالة الإعلام منتهية صلاحية الاشتراك" lightbox="images/atp-subscription-expired.png":::

## <a name="you-are-not-authorized-to-access-the-portal"></a>أنت غير مصرح لك بالوصول إلى المدخل

إذا **تلقيت A أنت** غير مصرح لك بالوصول إلى المدخل، فتنبه إلى أن Microsoft Defender لنقطة النهاية هو منتج مراقبة أمان وتحري عن الحوادث والاستجابة لها، وعلى هذا النحو، فإن الوصول إليه مقيد ويتحكم به المستخدم.
لمزيد من المعلومات، راجع [**تعيين وصول المستخدم إلى المدخل**](/windows/threat-protection/windows-defender-atp/assign-portal-access-windows-defender-advanced-threat-protection).

:::image type="content" source="images/atp-not-authorized-to-access-portal.png" alt-text="رسالة الإعلام غير مسموح بها في Access" lightbox="images/atp-not-authorized-to-access-portal.png":::

## <a name="data-currently-isnt-available-on-some-sections-of-the-portal"></a>البيانات غير متوفرة حاليا في بعض أقسام المدخل

إذا كانت لوحة معلومات المدخل والمقسمات الأخرى تظهر رسالة خطأ مثل "البيانات غير متوفرة حاليا":

:::image type="content" source="images/atp-data-not-available.png" alt-text="رسالة إعلام عدم توفر البيانات" lightbox="images/atp-data-not-available.png":::

ستحتاج إلى السماح بكل `security.windows.com` المجالين الفرعيين ضمنه على مستعرض الويب. على سبيل المثال، `*.security.windows.com`.

## <a name="portal-communication-issues"></a>مشاكل اتصال المدخل

إذا واجهت مشاكل تتعلق بالوصول إلى المدخل أو البيانات المفقودة أو الوصول المقيد إلى أجزاء من المدخل، فسوف تحتاج إلى التحقق من السماح باستخدام عناوين URL التالية وفتحها للاتصال.

- `*.blob.core.windows.net`
- `crl.microsoft.com`
- `https://*.microsoftonline-p.com`
- `https://*.security.microsoft.com`
- `https://automatediracs-eus-prd.security.microsoft.com`
- `https://login.microsoftonline.com`
- `https://login.windows.net`
- `https://onboardingpackagescusprd.blob.core.windows.net`
- `https://secure.aadcdn.microsoftonline-p.com`
- `https://security.microsoft.com`
- `https://static2.sharepointonline.com`
