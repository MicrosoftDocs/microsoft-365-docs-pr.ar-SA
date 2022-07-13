---
title: تمكين بيئة التقييم Microsoft Defender لـ Office 365 في بيئة الإنتاج الخاصة بك
description: خطوات لتنشيط تقييم Microsoft Defender لـ Office 365، مع التراخيص التجريبية، ومعالجة سجلات MX، & تدقيق المجالات المقبولة والاتصالات الواردة.
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
- zerotrust-solution
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: f3298c67421dea921a014bc32e91be8033733183
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750089"
---
# <a name="enable-the-evaluation-environment"></a>تمكين بيئة التقييم

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 3](eval-defender-office-365-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender لـ Office 365. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-office-365-overview.md).

استخدم الخطوات التالية لتمكين التقييم Microsoft Defender لـ Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-eval-enable-steps.png" alt-text="خطوات تمكين Microsoft Defender لـ Office 365 في بيئة تقييم Microsoft Defender" lightbox="../../media/defender/m365-defender-office-eval-enable-steps.png":::


- [الخطوة 1: تنشيط التراخيص التجريبية](#step-1-activate-trial-licenses)
- [الخطوة 2: تدقيق سجل MX العام والتحقق منه](#step-2-audit-and-verify-the-public-mx-record)
- [الخطوة 3: تدقيق المجالات المقبولة](#step-3-audit-accepted-domains)
- [الخطوة 4: تدقيق الموصلات الواردة](#step-4-audit-inbound-connectors)
- [الخطوة 5: تنشيط التقييم](#step-5-activate-the-evaluation)

## <a name="step-1-activate-trial-licenses"></a>الخطوة 1: تنشيط التراخيص التجريبية

سجل الدخول إلى بيئة Microsoft Defender لـ Office 365 الموجودة أو مدخل إدارة المستأجر.

1. انتقل إلى مدخل الإدارة.
2. حدد خدمات الشراء من التشغيل السريع.

   :::image type="content" source="../../media/mdo-eval/1_m365-purchase-services.png" alt-text="الخيار &quot;خدمات الشراء&quot; الذي سيتم النقر فوقه في مركز مسؤولي Microsoft 365" lightbox="../../media/mdo-eval/1_m365-purchase-services.png":::

3. قم بالتمرير لأسفل إلى قسم Add-On (أو ابحث عن "Defender") لتحديد موقع خطط Microsoft Defender لـ Office 365.
4. انقر فوق "التفاصيل" إلى جانب الخطة التي تريد تقييمها.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="الزر &quot;تفاصيل&quot; الذي سيتم النقر فوقه" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

5. انقر فوق ارتباط *بدء الإصدار التجريبي المجاني* .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="الارتباط التشعبي لبدء الإصدار التجريبي المجاني" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

6. قم بتأكيد طلبك وانقر فوق الزر *"تجربة الآن* ".

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="الزر &quot;تجربة الآن&quot;" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="step-2-audit-and-verify-the-public-mx-record"></a>الخطوة 2: تدقيق سجل MX العام والتحقق منه

لتقييم Microsoft Defender لـ Office 365 بشكل فعال، من المهم ترحيل البريد الإلكتروني الخارجي الوارد عبر مثيل Exchange Online Protection (EOP) المقترن بالمستأجر الخاص بك.

1. سجل الدخول إلى مدخل مسؤول M365، وقم بتوسيع الإعدادات، وحدد المجالات.
2. حدد مجال البريد الإلكتروني الذي تم التحقق منه وانقر فوق "إدارة DNS".
3. دون سجل MX الذي تم إنشاؤه وتعيينه إلى مستأجر EOP.
4. الوصول إلى منطقة DNS الخارجية (العامة) والتحقق من سجل MX الأساسي المقترن بمجال بريدك الإلكتروني.
    - *إذا كان سجل MX العام الخاص بك يطابق حاليا عنوان EOP المعين (على سبيل المثال، tenant-com.mail.protection.outlook.com) فلا يجب أن تكون هناك حاجة إلى أي تغييرات أخرى في التوجيه*.
    - إذا تم حل سجل MX العام حاليا إلى بوابة SMTP تابعة لجهة خارجية أو محلية، فقد تكون هناك حاجة إلى تكوينات توجيه إضافية.
    - إذا تم حل سجل MX العام حاليا إلى Exchange المحلي، فقد تظل في نموذج مختلط حيث لم يتم ترحيل بعض علبة بريد المستلمين بعد إلى EXO.

## <a name="step-3-audit-accepted-domains"></a>الخطوة 3: تدقيق المجالات المقبولة

1. سجل الدخول إلى مدخل Exchange Online مسؤول، وحدد "تدفق البريد"، ثم انقر فوق "المجالات المقبولة".
2. من قائمة المجالات المقبولة التي تمت إضافتها والتحقق منها في المستأجر، دون **نوع المجال** لمجال البريد الإلكتروني الأساسي.
    - إذا تم تعيين نوع المجال إلى ***"موثوق***"، فمن المفترض أن تكون كافة علب بريد المستلمين لمؤسستك موجودة حاليا في Exchange Online.
    - إذا تم تعيين نوع المجال إلى ***"الترحيل الداخلي*** "، فقد تظل في نموذج مختلط حيث لا تزال بعض علب بريد المستلمين موجودة محليا.

## <a name="step-4-audit-inbound-connectors"></a>الخطوة 4: تدقيق الموصلات الواردة

1. سجل الدخول إلى مدخل Exchange Online مسؤول، وحدد "تدفق البريد"، ثم انقر فوق "الموصلات".
2. من قائمة الموصلات المكونة، دون أي إدخالات من **المؤسسة الشريكة** وقد ترتبط ببوابة SMTP تابعة لجهة خارجية.
3. من قائمة الموصلات المكونة، دون أي إدخالات مسماة **من خادم البريد الإلكتروني الخاص بالمؤسسة** والتي قد تشير إلى أنك لا تزال في السيناريو المختلط.

## <a name="step-5-activate-the-evaluation"></a>الخطوة 5: تنشيط التقييم

استخدم الإرشادات هنا لتنشيط تقييم Microsoft Defender لـ Office 365 من مدخل Microsoft 365 Defender.

1. سجل الدخول إلى المستأجر باستخدام حساب لديه حق الوصول إلى مدخل Microsoft 365 Defender.
2. اختر ما إذا كنت تريد جعل **مدخل Microsoft 365 Defender** واجهتك الافتراضية لإدارة Microsoft Defender لـ Office 365 (مستحسن).

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-activate-eval.png" alt-text="الزر &quot;تشغيل في الإعدادات&quot; ليؤدي إلى مدخل Microsoft 365 Defender مركزي ومحسن للإدارة" lightbox="../../media/mdo-eval/1_mdo-eval-activate-eval.png":::

3. من قائمة التنقل، حدد **"النهج & القواعد** " ضمن *"التعاون & البريد الإلكتروني*".

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-activate-eval.png" alt-text="عنصر قائمة قواعد & النهج المطلوب النقر فوقه" lightbox="../../media/mdo-eval/2_mdo-eval-activate-eval.png":::

4. في لوحة معلومات *"قواعد & النهج* "، انقر فوق **"نهج التهديد**".

   :::image type="content" source="../../media/mdo-eval/3_mdo-eval-activate-eval.png" alt-text="عنصر القائمة &quot;نهج التهديد&quot; الذي سيتم النقر فوقه" lightbox="../../media/mdo-eval/3_mdo-eval-activate-eval.png":::

5. قم بالتمرير لأسفل وصولا إلى *"نهج إضافية*" وحدد الإطار المتجانب **"تقييم Defender لـ Office 365**".

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-activate-eval.png" alt-text="تجانب Defender لـ Office 365 تقييم" lightbox="../../media/mdo-eval/4_mdo-eval-activate-eval.png":::

6. الآن اختر ما إذا كانت مسارات البريد الإلكتروني الخارجية إلى Exchange Online مباشرة، أو إلى بوابة أو خدمة تابعة لجهة خارجية، وانقر فوق "التالي".

   :::image type="content" source="../../media/mdo-eval/5_mdo-eval-activate-eval.png" alt-text="جزء إعدادات التوجيه في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/5_mdo-eval-activate-eval.png":::

7. إذا كنت تستخدم بوابة تابعة لجهة خارجية، فحدد اسم المورد من القائمة المنسدلة إلى جانب الموصل الوارد المقترن بهذا الحل. عند إدراج إجاباتك، انقر فوق "التالي".

   :::image type="content" source="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png" alt-text="جزء الإعدادات المحلي أو الخارجي في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/6-mdo-eval-activate-eval-settings.png":::

8. راجع الإعدادات وانقر فوق الزر **"إنشاء تقييم** ".

   |قبل|بعد|
   |:---:|:---:|
   |:::image type="content" source="../../media/mdo-eval/7-mdo-eval-activate-review.png" alt-text="جزء مراجعة الإعدادات في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/7-mdo-eval-activate-review.png":::|:::image type="content" source="../../media/mdo-eval/8-mdo-eval-activate-complete.png" alt-text="إعلام إكمال إعداد التقييم في مدخل Microsoft Defender لـ Office 365" lightbox="../../media/mdo-eval/8-mdo-eval-activate-complete.png":::|
   |

## <a name="next-steps"></a>الخطوات التالية

الخطوة 3 من 3: إعداد الإصدار التجريبي Microsoft Defender لـ Office 365

العودة إلى النظرة العامة لتقييم [Microsoft Defender لـ Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
