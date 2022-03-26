---
title: حواجز المعلومات في Microsoft 365
description: تعرف على كيفية تكوين حواجز المعلومات في Microsoft 365.
keywords: Microsoft 365، مخاطر insider، التوافق
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
ms.openlocfilehash: e4116550336756fe9248a4a28dfa0f809c4012bb
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/13/2021
ms.locfileid: "63570133"
---
# <a name="information-barriers-in-microsoft-365"></a>حواجز المعلومات في Microsoft 365

Microsoft 365 التواصل والتعاون عبر المجموعات والمنظمات كما يدعم طرق تقييد الاتصال والتعاون بين مجموعات معينة من المستخدمين عند الضرورة. قد يتضمن ذلك حالات أو سيناريوهات حيث تريد تقييد التواصل والتعاون بين المجموعتين لتجنب حدوث تعارض في المصالح في مؤسستك. قد يشمل ذلك أيضا الحالات التي تحتاج فيها إلى تقييد التواصل والتعاون بين أشخاص معينين داخل مؤسستك لحماية المعلومات الداخلية.

يتم دعم حواجز المعلومات في Microsoft Teams SharePoint عبر الإنترنت OneDrive for Business. يمكن لمسؤول التوافق أو مسؤول حواجز المعلومات تعريف سياسات للسماح بالاتصالات بين مجموعات المستخدمين في Microsoft Teams. يمكن استخدام سياسات حاجز المعلومات في مثل هذه الحالات:

- يجب ألا يقوم المستخدم في مجموعة المتداولين اليوم بالتواصل مع فريق التسويق أو مشاركته
- لا يجب على الموظفين الماليين الذين يعملون على معلومات سرية للشركة التواصل مع مجموعات معينة داخل المؤسسة أو مشاركتها
- يجب ألا يتصل فريق داخلي بمواد سرية تجارية أو الدردشة عبر الإنترنت مع أشخاص في مجموعات معينة ضمن مؤسساتهم
- يجب على فريق البحث الاتصال أو الدردشة عبر الإنترنت فقط مع فريق تطوير المنتجات

## <a name="configure-information-barriers-for-microsoft-365"></a>تكوين حواجز المعلومات Microsoft 365

استخدم الخطوات التالية لتكوين حواجز المعلومات لمنظمتك:

![خطوات معلومات حل مخاطر Insider.](../media/ir-solution-ib-steps.png)

1. تعرف على [حواجز المعلومات](information-barriers.md) في Microsoft 365
2. تكوين المتطلبات [الأساسية والأذونات](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)
3. تقسيم [المستخدمين في مؤسستك](information-barriers-policies.md#step-2-segment-users-in-your-organization)
4. إنشاء سياسات حاجز [المعلومات وتكوينها](information-barriers-policies.md#step-3-define-information-barrier-policies)
5. تطبيق [سياسات حاجز المعلومات](information-barriers-policies.md#step-4-apply-information-barrier-policies)

## <a name="more-information-about-information-barriers"></a>مزيد من المعلومات حول حواجز المعلومات

- [سمات سياسات حاجز المعلومات](information-barriers-attributes.md)
- [تحرير سياسات حاجز المعلومات أو إزالتها](information-barriers-edit-segments-policies.md)