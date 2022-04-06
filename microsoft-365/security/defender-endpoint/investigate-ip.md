---
title: التحقق من عنوان IP المقترن بتنبيه
description: استخدم خيارات التحقيق لفحص الاتصالات المحتملة بين الأجهزة وعناوين IP الخارجية.
keywords: التحقيق، عنوان IP، التنبيه، Microsoft Defender ل Endpoint، IP الخارجي
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: b20a8d5f1f33ebe62fa1ec9a5e8c8e05dbddbc2b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583061"
---
# <a name="investigate-an-ip-address-associated-with-a-microsoft-defender-for-endpoint-alert"></a>التحقق من عنوان IP مقترن بتنبيه Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

افحص الاتصال المحتمل بين أجهزتك وعناوين بروتوكول الإنترنت الخارجي (IP).

يساعد تحديد جميع الأجهزة في المؤسسة التي تتواصل مع عنوان IP ضار مشتبه به أو معروف، مثل خوادم الأمر والتحكم (C2) على تحديد النطاق المحتمل للخرق والملفات المقترنة والأجهزة المصابة.

يمكنك العثور على معلومات من المقاطع التالية في طريقة عرض عنوان IP:

- IP حول العالم
- عكس أسماء DNS
- التنبيهات ذات الصلة ب IP هذا
- IP في المؤسسة
- نواة

## <a name="ip-worldwide-and-reverse-dns-names"></a>أسماء IP Worldwide وSNS العكسية

يعرض قسم تفاصيل عنوان IP سمات عنوان IP مثل ASN وأسماء DNS العكسية الخاصة به.

## <a name="alerts-related-to-this-ip"></a>التنبيهات ذات الصلة ب IP هذا

يوفر **قسم التنبيهات المرتبطة ب IP** هذا قائمة بالتنبيهات المقترنة ب IP.

## <a name="ip-in-organization"></a>IP في المؤسسة

يوفر **قسم IP** في المؤسسة تفاصيل حول عنوان IP في المؤسسة.

## <a name="prevalence"></a>نواة

يعرض **القسم "** تناول المشاكل" عدد الأجهزة التي تم توصيلها عنوان IP هذا، ومتى تم عرض IP للمرة الأولى والأخيرة. يمكنك تصفية نتائج هذا المقطع حسب الفترة الزمنية؛ الفترة الافتراضية هي 30 يوما.

## <a name="most-recent-observed-devices-with-ip"></a>أحدث الأجهزة التي تم ملاحظتها باستخدام IP

يوفر **أحدث الأجهزة التي** تم ملاحظتها مع قسم IP طريقة عرض ذات ترتيب زمني للأحداث والتنبيهات المقترنة التي تم ملاحظتها على عنوان IP.

**التحقق من عنوان IP خارجي:**

1. حدد **IP** من القائمة المنسدلة **شريط** البحث.
2. أدخل عنوان IP في **حقل** البحث.
3. انقر فوق أيقونة البحث أو اضغط على **Enter**.

يتم عرض تفاصيل حول عنوان IP، بما في ذلك: تفاصيل التسجيل (إذا كانت متوفرة)، وIP العكسية (على سبيل المثال، المجالات)، ومعالجات الأجهزة في المؤسسة التي تواصلت مع عنوان IP هذا (خلال فترة زمنية محددة)، والأجهزة في المؤسسة التي تم ملاحظتها وهي تتواصل مع عنوان IP هذا.

> [!NOTE]
> سيتم إرجاع نتائج البحث فقط عن عناوين IP التي يتم ملاحظتها عند الاتصال بالأجهزة في المؤسسة.

استخدم عوامل تصفية البحث لتعريف معايير البحث. يمكنك أيضا استخدام مربع البحث في المخطط الزمني لتصفية النتائج المعروضة لجميع الأجهزة في المؤسسة التي تمت ملاحظتها وهي تتواصل مع عنوان IP والملف المقترن بالتصال والتاريخ الأخير الذي تمت ملاحظته.

يؤدي النقر فوق أي من أسماء الأجهزة إلى الوصول إلى طريقة عرض هذا الجهاز، حيث يمكنك متابعة التحقق من التنبيهات والسلوكيات والأحداث التي تم التقارير عنها.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [عرض قائمة انتظار تنبيهات نقطة النهاية في Microsoft Defender وتنظيمها](alerts-queue.md)
- [إدارة تنبيهات Microsoft Defender لنقطة النهاية](manage-alerts.md)
- [التحقق من تنبيهات نقطة النهاية ل Microsoft Defender](investigate-alerts.md)
- [التحقق من ملف مقترن بتنبيه Microsoft Defender لنقطة النهاية](investigate-files.md)
- [التحقق من الأجهزة في قائمة أجهزة نقطة النهاية ل Microsoft Defender](investigate-machines.md)
- [التحقق من مجال مقترن بتنبيه Microsoft Defender لنقطة النهاية](investigate-domain.md)
- [التحقق من حساب مستخدم في Microsoft Defender لنقطة النهاية](investigate-user.md)
