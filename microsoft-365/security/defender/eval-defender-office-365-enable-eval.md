---
title: تمكين بيئة التقييم ل Microsoft Defender Office 365 في بيئة الإنتاج
description: خطوات لتنشيط Microsoft Defender Office 365 التقييم، باستخدام التراخيص التجريبية ومعالجة سجل MX & تدقيق المجالات المقبولة والاتصالات الواردة.
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
ms.openlocfilehash: 4d2f77b41dccd5620b96d816869d7d7b6458a798
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63574014"
---
# <a name="enable-the-evaluation-environment"></a>تمكين بيئة التقييم

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 3](eval-defender-office-365-overview.md) في عملية إعداد بيئة التقييم ل Microsoft Defender Office 365. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-office-365-overview.md).

استخدم الخطوات التالية لتمكين تقييم Microsoft Defender Office 365.

![خطوات لتمكين Microsoft Defender Office 365 في بيئة تقييم Microsoft Defender.](../../media/defender/m365-defender-office-eval-enable-steps.png)

- [الخطوة 1: تنشيط التراخيص التجريبية](#step-1-activate-trial-licenses)
- [الخطوة 2: تدقيق سجل MX العام والتحقق منه](#step-2-audit-and-verify-the-public-mx-record)
- [الخطوة 3: تدقيق المجالات المقبولة](#step-3-audit-accepted-domains)
- [الخطوة 4: تدقيق الموصلات الواردة](#step-4-audit-inbound-connectors)
- [الخطوة 5: تنشيط التقييم](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>الخطوة 1: تنشيط التراخيص التجريبية

سجل دخولك إلى Microsoft Defender الحالي Office 365 بيئة المستأجر أو مدخل إدارة المستأجر.

1. انتقل إلى مدخل الإدارة.
2. حدد خدمات الشراء من عملية الإطلاق السريعة.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="انقر فوق شراء الخدمات في جزء التنقل في Office 365.":::

3. قم بالتمرير لأسفل Add-On المقطع (أو ابحث عن "Defender") لتحديد موقع Microsoft Defender Office 365 الجديدة.
4. انقر فوق تفاصيل بجانب الخطة التي تريد تقييمها.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="انقر فوق الزر تفاصيل، التالي.":::

5. انقر فوق *الارتباط بدء الإصدار التجريبي* المجاني.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="انقر فوق بدء الإصدار التجريبي المجاني *ارتباط تشعبي* على هذه اللوحة.":::

6. أكد طلبك وانقر فوق *الزر تجربة* الآن.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="انقر الآن فوق الزر جرب الآن **.":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>الخطوة 2: تدقيق سجل MX العام والتحقق منه

لتقييم Microsoft Defender بشكل Office 365، من المهم ترحيل البريد الإلكتروني الخارجي الوارد عبر مثيل Exchange Online Protection (EOP) المقترن بالمستأجر.

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

استخدم الإرشادات هنا لتنشيط تقييم Microsoft Defender Office 365 من Microsoft 365 Defender الإلكتروني.

1. سجل دخولك إلى المستأجر باستخدام حساب لديه حق الوصول إلى Microsoft 365 Defender الإلكتروني.
2. اختر ما إذا كنت تريد جعل Microsoft 365 Defender **المدخل** واجهة افتراضية ل Microsoft Defender Office 365 (مستحسن).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="انقر فوق الزر تشغيل الإعدادات لاستخدام المدخل المركزي والمحسن Microsoft 365 Defender للإدارة.":::

3. من قائمة التنقل، حدد & **القواعد** ضمن *البريد الإلكتروني & التعاون*.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="إليك صورة البريد الإلكتروني & التعاون تشير إلى &quot;& القواعد&quot;. انقر فوق ذلك!":::

4. على لوحة *المعلومات نهج &،* انقر فوق **نهج التهديدات**.

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="صورة لوحة معلومات & وقواعد النهج وسهم يشير إلى نهج التهديدات. انقر فوق ذلك التالي!":::

5. قم بالتمرير لأسفل *وصولا إلى سياسات إضافية* وحدد اللوحة **تقييم Defender Office 365**.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="لوحة Eval Defender Office 365 تقول إنه تجريبي لمدة 30 يوما عبر البريد الإلكتروني & متجهات التعاون. انقر من خلال.":::

6. اختر الآن ما إذا كانت مسارات البريد الإلكتروني الخارجية Exchange Online مباشرة، أو إلى بوابة أو خدمة جهة خارجية، وانقر فوق التالي.

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="سيقيم defender for Office 365 البريد المرسل إلى علب بريدك Exchange Online البريد. امنح تفاصيل حول كيفية توجيه البريد الآن، بما في ذلك اسم الموصل الصادر الذي يوصل بريدك. إذا كنت تستخدم Exchange Online Protection (EOP) فقط، فلن يكون لديك موصل. اختر أحد الموفرين الذين أستخدمهم من جهة خارجية أو في الموقع، أو أستخدم EOP فقط.":::

7. إذا كنت تستخدم بوابة جهة خارجية، فحدد اسم المورد من المنسدل إلى جانب الموصل الوارد المقترن بهذا الحل. عند إدراج إجاباتك، انقر فوق التالي.

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="في مربع الحوار هذا، يمكنك اختيار خدمة موردين من جهة خارجية تستخدمها مؤسستك، أو حدد *أخرى*. في مربع الحوار التالي، حدد الموصل الوارد. ثم انقر فوق التالي.":::

8. راجع الإعدادات وانقر فوق **الزر إنشاء** تقييم.

   |قبل|بعد|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="هذا الجزء به قائمة منسدل لمراجعة الإعدادات. كما أنه لديه ارتباط قابل للنقر فوقه إلى تحرير نوع التوجيه إذا كنت بحاجة إلى ذلك. عندما تكون جاهزا، انقر فوق الزر الأزرق الكبير إنشاء تقييم.":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="والآن اكتملت عملية إعداده. الزر الأزرق على هذه الصفحة يقول &quot;الانتقال إلى التقييم&quot;.":::|
   |

## <a name="next-steps"></a>الخطوات التالية

الخطوة 3 من 3: إعداد التجربة ل Microsoft Defender Office 365

العودة إلى نظرة عامة حول [تقييم Microsoft Defender Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
