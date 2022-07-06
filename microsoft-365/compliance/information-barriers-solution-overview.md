---
title: عوائق المعلومات
description: تعرف على كيفية تكوين حواجز المعلومات في Microsoft Purview.
keywords: Microsoft 365 وMicrosoft Purview والامتثال وحواجز المعلومات
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- m365solution-scenario
ms.openlocfilehash: 21ad4f0cc6614bed3c579a8025d83200446fec18
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627228"
---
# <a name="information-barriers"></a>عوائق المعلومات

يتيح Microsoft 365 الاتصال والتعاون عبر المجموعات والمؤسسات ويدعم طرقا لتقييد الاتصال والتعاون بين مجموعات معينة من المستخدمين عند الضرورة. قد يتضمن ذلك المواقف أو السيناريوهات التي تريد فيها تقييد الاتصال والتعاون بين مجموعتين لتجنب حدوث تعارض في الاهتمام في مؤسستك. قد يشمل ذلك أيضا المواقف التي تحتاج فيها إلى تقييد الاتصال والتعاون بين أشخاص معينين داخل مؤسستك لحماية المعلومات الداخلية.

Microsoft Purview Information Barriers (IB) مدعوم في Microsoft Teams وSharePoint Online OneDrive for Business. يمكن لمسؤول التوافق أو مسؤول IB تحديد النهج للسماح بالاتصالات بين مجموعات المستخدمين في Microsoft Teams أو منعها. يمكن استخدام نهج IB لحالات مثل هذه:

- يجب ألا يتصل المستخدم في مجموعة التاجر اليومي بالملفات أو يشاركها مع فريق التسويق
- يجب ألا يقوم موظفو الشؤون المالية الذين يعملون على معلومات سرية للشركة بتوصيل الملفات أو مشاركتها مع مجموعات معينة داخل مؤسستهم
- يجب ألا يتصل الفريق الداخلي الذي يحتوي على مواد سرية تجارية أو يدردش عبر الإنترنت مع أشخاص في مجموعات معينة داخل مؤسستهم
- يجب على فريق البحث الاتصال أو الدردشة عبر الإنترنت فقط مع فريق تطوير المنتجات

## <a name="configure-information-barriers"></a>تكوين حواجز المعلومات

استخدم الخطوات التالية لتكوين IB لمؤسستك:

![خطوات حواجز معلومات حل المخاطر الداخلية.](../media/ir-solution-ib-steps.png)

1. التعرف على [حواجز المعلومات](information-barriers.md)
2. تكوين [المتطلبات الأساسية والأذونات](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)
3. تقسيم [المستخدمين في مؤسستك](information-barriers-policies.md#step-2-segment-users-in-your-organization)
4. إنشاء نهج [IB](information-barriers-policies.md#step-3-create-ib-policies) وتكوينها
5. تطبيق [نهج IB](information-barriers-policies.md#step-4-apply-ib-policies)

## <a name="more-information-about-information-barriers"></a>مزيد من المعلومات حول حواجز المعلومات

- [سمات نهج IB](information-barriers-attributes.md)
- [تحرير نهج IB أو إزالتها](information-barriers-edit-segments-policies.md)
