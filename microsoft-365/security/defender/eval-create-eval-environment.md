---
title: إنشاء بيئة تقييم Microsoft 365 Defender لمزيد من الأمان السيبراني و XDR
description: تعرف على ما هو مضمن في Microsoft 365 Defender XDR الذي ستقوم بتقييمه، وقم بتسلسل Microsoft 365 Defender التجربة أو بيئة الإصدار التجريبي من خلال تنشيط التراخيص التجريبية. ابدأ رحلة الأمان السيبراني ل XDR هنا وتعلم كيفية إجراء هذا الاختبار للإنتاج.
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
ms.date: 05/19/2021
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
ms.openlocfilehash: fb097532fe809fa1b1ec4c29a9a489bcb4ea2871
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747956"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>الخطوة 1. إنشاء بيئة تقييم Microsoft 365 Defender لمزيد من الأمان السيبراني

يمكنك التعرف على هذا الحل Microsoft Defender XDR وإنشاءه في الخطوات التي يتم توزيعها من خلال بقية هذه السلسلة:

- [كيفية إنشاء البيئة](eval-create-eval-environment.md)
- إعداد كل تقنية من تقنيات Microsoft XDR هذه أو التعرف عليها
    - [Microsoft Defender للهوية](eval-defender-identity-overview.md)
    - [Microsoft Defender ل Office](eval-defender-office-365-overview.md)
    - [مشكلات الأداء في Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)
    - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [كيفية التحقيق والاستجابة باستخدام XDR هذا](eval-defender-investigate-respond.md)
- [ترقية بيئة الإصدار التجريبي إلى الإنتاج](eval-defender-promote-to-production.md)
- [العودة إلى النظرة العامة](eval-overview.md)

تعمل الخطوات في هذه السلسلة من البداية إلى النهاية، بدءا من تعلم المفاهيم وراء Microsoft 365 Defender XDR إلى إنشائها، وإلى نقل بيئة التقييم مباشرة إلى الإنتاج.

هناك طريقتان شائعتان للقيام بهذه الخطوة التالية في التقييم. تفترض هذه السلسلة أن لديك بالفعل مستأجر Microsoft 365 للإنتاج وستنشط تراخيص E5 التجريبية لتقييم Microsoft 365 Defender في *البيئة الحالية*. سيسمح لك التقييم الموضعي بالاحتفاظ بأي أساليب أمان مع شراء التراخيص بعد فترة التقييم.

والثاني هو [إعداد بيئة المختبر التجريبية Microsoft 365 Defender](setup-m365deval.md) لغرض التقييم. لاحظ أنه قد لا يحتوي على العديد من الإشارات الحقيقية من الأعمال أثناء الاختبار.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>ستحتاج إلى تنشيط تراخيص E5 التجريبية لتقييم Microsoft 365 Defender

1. سجل الدخول إلى مدخل إدارة مستأجر Microsoft 365 الحالي.
2. حدد **خدمات الشراء** من قائمة التنقل.
3. قم بالتمرير لأسفل وصولا إلى قسم Office 365 وحدد زر **التفاصيل** ضمن ترخيص Office 365 E5.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="الزر &quot;تفاصيل&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

4. حدد "بدء تشغيل ارتباط **الإصدار التجريبي المجاني** ".

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="زر بدء الإصدار التجريبي المجاني في مدخل Microsoft 365 Defender" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

5. قم بتأكيد طلبك وانقر فوق الزر **"تجربة الآن** ".

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="الزر &quot;تجربة الآن&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="go-to-the-next-step"></a>الانتقال إلى الخطوة التالية

[تعرف على كيفية تمكين Microsoft 365 for Identity](eval-defender-identity-overview.md)

أو ارجع إلى نظرة عامة على [التقييم Microsoft 365 Defender](eval-overview.md)
