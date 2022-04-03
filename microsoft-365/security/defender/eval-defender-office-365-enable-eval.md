---
title: تمكين بيئة التقييم Microsoft Defender لـ Office 365 بيئة الإنتاج
description: خطوات لتنشيط Microsoft Defender لـ Office 365، باستخدام التراخيص التجريبية ومعالجة سجل MX & تدقيق المجالات المقبولة والاتصالات الواردة.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: a5a14d507f7cd10ff4f7ab62b552ab256f0e4a5e
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498990"
---
# <a name="enable-the-evaluation-environment"></a>تمكين بيئة التقييم

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 3](eval-defender-office-365-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender لـ Office 365. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-office-365-overview.md).

استخدم الخطوات التالية لتمكين تقييم Microsoft Defender لـ Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="الخطوات اللازمة لتمكين Microsoft Defender لـ Office 365 في بيئة تقييم Microsoft Defender" lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::


- [الخطوة 1: تنشيط التراخيص التجريبية](#step-1-activate-trial-licenses)
- [الخطوة 2: تدقيق سجل MX العام والتحقق منه](#step-2-audit-and-verify-the-public-mx-record)
- [الخطوة 3: تدقيق المجالات المقبولة](#step-3-audit-accepted-domains)
- [الخطوة 4: تدقيق الموصلات الواردة](#step-4-audit-inbound-connectors)
- [الخطوة 5: تنشيط التقييم](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>الخطوة 1: تنشيط التراخيص التجريبية

سجل دخولك إلى مدخل إدارة Microsoft Defender لـ Office 365 المستأجر أو بيئتك الحالية.

1. انتقل إلى مدخل الإدارة.
2. حدد خدمات الشراء من عملية الإطلاق السريعة.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="الخيار &quot;خدمات الشراء&quot; الذي يجب النقر فوقه في مركز مسؤولي Microsoft 365" lightbox="../../media/mdo-eval/1_m365-purchase-services.png":::

3. قم بالتمرير لأسفل Add-On المقطع (أو ابحث عن "Defender") لتحديد موقع Microsoft Defender لـ Office 365 الجديدة.
4. انقر فوق تفاصيل بجانب الخطة التي تريد تقييمها.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="الزر &quot;تفاصيل&quot; الذي يجب النقر فوقه" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

5. انقر فوق *الارتباط بدء الإصدار التجريبي* المجاني.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="الارتباط التشعبي &quot;بدء الإصدار التجريبي المجاني&quot;" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

6. أكد طلبك وانقر فوق *الزر تجربة* الآن.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="الزر &quot;تجربة الآن&quot;" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>الخطوة 2: تدقيق سجل MX العام والتحقق منه

لتقييم Microsoft Defender لـ Office 365، من المهم ترحيل البريد الإلكتروني الخارجي الوارد عبر مثيل Exchange Online Protection (EOP) المقترن بالمستأجر.

1. سجل دخولك إلى مدخل مسؤول M365، الإعدادات، وحدد المجالات.
2. حدد مجال البريد الإلكتروني الذي تم التحقق منه وانقر فوق إدارة DNS.
3. دون سجل MX الذي تم إنشاؤه وتعيينه إلى مستأجر EOP.
4. يمكنك الوصول إلى منطقة DNS الخارجية (العامة) والتحقق من سجل MX الأساسي المقترن بمجال بريدك الإلكتروني.
    - *إذا كان سجل MX* العام يتطابق حاليا مع عنوان EOP المعين (على سبيل المثال، tenant-com.mail.protection.outlook.com) فلا يلزم إجراء أي تغييرات توجيه إضافية.
    - إذا تم حل سجل MX العام حاليا لبوابة SMTP جهة خارجية أو في الموقع، فقد تكون هناك حاجة إلى تكوينات توجيه إضافية.
    - إذا تم حل سجل MX العام حاليا Exchange، فقد تكون في نموذج مختلط حيث لم يتم ترحيل بعض علب بريد المستلمين إلى EXO بعد.

## <a name="step-3-audit-accepted-domains"></a>الخطوة 3: تدقيق المجالات المقبولة

1. سجل دخولك إلى Exchange Online المسؤول، وحدد البريد Flow، ثم انقر فوق المجالات المقبولة.
2. من قائمة المجالات المقبولة التي تم إضافتها والتحقق منها في نطاق المستأجر، دون نوع المجال لمجال البريد الإلكتروني  الأساسي.
    - إذا تم تعيين نوع المجال إلى ***موثوق***، فيفترض أن كل علب بريد المستلمين في مؤسستك موجودة حاليا في Exchange Online.
    - إذا تم تعيين نوع المجال إلى الترحيل  الداخلي، فقد تكون لا تزال في نموذج مختلط حيث لا تزال بعض علب بريد المستلمين موجودة في الموقع.

## <a name="step-4-audit-inbound-connectors"></a>الخطوة 4: تدقيق الموصلات الواردة

1. سجل دخولك إلى Exchange Online المسؤول، وحدد البريد Flow، ثم انقر فوق موصلات.
2. من قائمة الموصلات المكونة، دون أي إدخالات من مؤسسة الشريك وقد ترتبط ببوابة SMTP من جهة خارجية.
3. من قائمة الموصلات التي تم تكوينها، دون أي إدخالات تم تسميتها من  خادم البريد الإلكتروني في مؤسستك والتي قد تشير إلى أنك لا تزال في السيناريو المختلط.

## <a name="step-5-activate-the-evaluation"></a>الخطوة 5: تنشيط التقييم

استخدم الإرشادات هنا لتنشيط تقييم Microsoft Defender لـ Office 365 من Microsoft 365 Defender المدخل.

1. سجل دخولك إلى المستأجر باستخدام حساب لديه حق الوصول إلى Microsoft 365 Defender الإلكتروني.
2. اختر ما إذا كنت تريد جعل Microsoft 365 Defender **المدخل** واجهة افتراضية Microsoft Defender لـ Office 365 (مستحسن).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="الزر &quot;تشغيل الإعدادات&quot; ليؤدي إلى مدخل مركزي ومحسن Microsoft 365 Defender الإدارة" lightbox="../../media/mdo-eval/1_mdo-eval-activate-eval.png":::

3. من قائمة التنقل، حدد & **القواعد** ضمن *البريد الإلكتروني & التعاون*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="عنصر القائمة & &quot;&&quot; الذي يجب النقر فوقه" lightbox="../../media/mdo-eval/2_mdo-eval-activate-eval.png":::

4. على لوحة *المعلومات نهج &،* انقر فوق **نهج التهديدات**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="عنصر القائمة &quot;سياسات التهديدات&quot; الذي يجب النقر فوقه" lightbox="../../media/mdo-eval/3_mdo-eval-activate-eval.png":::

5. قم بالتمرير لأسفل *وصولا إلى سياسات إضافية* وحدد اللوحة **تقييم Defender لـ Office 365** الإضافية.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="لوحة Defender لـ Office 365 Eval" lightbox="../../media/mdo-eval/4_mdo-eval-activate-eval.png":::

6. اختر الآن ما إذا كانت مسارات البريد الإلكتروني الخارجية Exchange Online مباشرة، أو إلى بوابة أو خدمة جهة خارجية، وانقر فوق التالي.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="جزء إعدادات التوجيه في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/5_mdo-eval-activate-eval.png":::

7. إذا كنت تستخدم بوابة جهة خارجية، فحدد اسم المورد من المنسدل إلى جانب الموصل الوارد المقترن بهذا الحل. عند إدراج إجاباتك، انقر فوق التالي.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="الجزء &quot;إعدادات الطرف الثالث&quot; أو &quot;الإعدادات&quot; في Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png":::

8. راجع الإعدادات وانقر فوق **الزر إنشاء** تقييم.

   |قبل|بعد|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="الجزء &quot;مراجعة الإعدادات&quot; في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/7-mdo-eval-activate-review.png":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="إعلام اكتمال إعداد التقييم في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/8-mdo-eval-activate-complete.png":::|
   |

## <a name="next-steps"></a>الخطوات التالية

الخطوة 3 من 3: إعداد التجربة Microsoft Defender لـ Office 365

العودة إلى نظرة عامة [حول تقييم](eval-defender-office-365-overview.md) Microsoft Defender لـ Office 365

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
