---
title: إنشاء Microsoft 365 Defender التقييم لمزيد من الأمان عبر الإنترنت وXDR
description: تعرف على ما هو مضمن في Microsoft 365 Defender XDR الذي سيتم تقييمه، واعمل على تحسين بيئة Microsoft 365 Defender الإصدار التجريبي أو الإصدار التجريبي من خلال تنشيط التراخيص التجريبية. ابدأ رحلة الأمن الإلكتروني ل XDR هنا وتعرف على كيفية إجراء هذا الاختبار للإنتاج.
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
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 5b684a1ead5638a787413d7470cb103cbe55e7df
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775511"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>الخطوة 1. إنشاء Microsoft 365 Defender التقييم لمزيد من الأمان عبر الإنترنت

يمكنك التعرف على حل Microsoft Defender XDR هذا في الخطوات التي يتم توزيعها عبر باقي هذه السلسلة:

- [كيفية إنشاء البيئة](eval-create-eval-environment.md)
- إعداد أو التعرف على كل تقنية من تقنيات Microsoft XDR هذه
    - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
    - [Microsoft Defender Office](eval-defender-office-365-overview.md)
    - [Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)
    - [Microsoft Defender لتطبيقات السحابة](eval-defender-mcas-overview.md)
- [كيفية التحقق والرد باستخدام XDR هذا](eval-defender-investigate-respond.md)
- [الترويج لبيئة الإصدار التجريبي للإنتاج](eval-defender-promote-to-production.md)
- [العودة إلى النظرة العامة](eval-overview.md)

يتم تشغيل الخطوات في هذه السلسلة بشكل شامل، من التعرف على المفاهيم Microsoft 365 Defender XDR إلى بنى هذه السلسلة، ونهاية بيئة التقييم إلى الإنتاج.

هناك طريقتان شائعتان للقيام بذلك الخطوة التالية في التقييم. تفترض هذه السلسلة أن لديك Microsoft 365 مستأجر وتنشيط تراخيص الإصدار التجريبي من E5 لتقييم Microsoft 365 Defender *في البيئة الحالية*. سيترك لك التقييم المواظبة على الاحتفاظ بأي أساليب أمان عند شراء التراخيص بعد فترة التقييم.

والثانية هي إعداد [بيئة Microsoft 365 Defender تجريبية](setup-m365deval.md) لغرض التقييم. تجدر الإشارة إلى أنه قد لا يكون لديها العديد من الإشارات الحقيقية من العمل أثناء الاختبار.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>ستحتاج إلى تنشيط تراخيص الإصدار التجريبي من E5 لتقييم Microsoft 365 Defender

1. سجل دخولك إلى مدخل إدارة المستأجر Microsoft 365 الحالي.
2. حدد **خدمات الشراء** من قائمة التنقل.
3. قم بالتمرير لأسفل Office 365 المقطع **وحدد زر** التفاصيل ضمن Office 365 E5 الترخيص.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="الزر &quot;تفاصيل&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

4. حدد **بدء ارتباط تجريبي** مجاني.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="زر البدء التجريبي المجاني في مدخل Microsoft 365 Defender" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

5. أكد طلبك وانقر فوق **الزر تجربة** الآن.

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="الزر &quot;تجربة الآن&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="go-to-the-next-step"></a>الانتقال إلى الخطوة التالية

[تعرف على كيفية تمكين Microsoft 365 الهوية](eval-defender-identity-overview.md)

أو ارجع إلى نظرة عامة حول [التقييم Microsoft 365 Defender](eval-overview.md)
