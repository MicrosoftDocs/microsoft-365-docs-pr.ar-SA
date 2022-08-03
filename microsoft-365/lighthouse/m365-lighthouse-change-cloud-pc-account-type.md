---
title: تغيير نوع حساب كمبيوتر سحابي Windows 365 Business في Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: katmartin
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية تعيين نوع حساب كمبيوتر سحابي Windows 365 Business أو تغييره.
ms.openlocfilehash: c1cb1e8a8e6f850aa73fe05360289d280c4b9eb2
ms.sourcegitcommit: 23a53b5c5e372a2a7ad5e175850224d3d464f6dd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67171402"
---
# <a name="change-a-windows-365-business-cloud-pc-account-type-in-microsoft-365-lighthouse"></a>تغيير نوع حساب كمبيوتر سحابي Windows 365 Business في Microsoft 365 Lighthouse

قد يقوم فنيو موفر الخدمة المدارة (MSP) بتعيين نوع الحساب لجهاز كمبيوتر سحابي للأعمال أو إجراء تغييرات على نوع حساب موجود. تتوفر أنواع الحسابات التالية:

- **المستخدم القياسي (مستحسن)** - لدى حسابات المستخدمين القياسية الإذن بتثبيت البرامج فقط من Microsoft Store.

- **المسؤول المحلي** - تمتلك حسابات المسؤولين المحليين الإذن لتثبيت أي برنامج وإجراء تغييرات على أي جزء من نظام التشغيل. حدد نوع الحساب هذا فقط عند الحاجة، حيث قد تستخدم البرامج الضارة أذونات المسؤول لإصابة الملفات أو إتلافها.

> [!NOTE]
> يمكنك تعيين نوع الحساب أو تغييره لأجهزة الكمبيوتر السحابية فقط باستخدام ترخيص Business. لا يمكنك تغيير نوع الحساب لأجهزة الكمبيوتر السحابية بترخيص Enterprise.

## <a name="before-you-begin"></a>قبل البدء 

يجب أن تكون مسؤولا Windows 365 أو مسؤولا عاما في مستأجر الشريك.

## <a name="set-or-change-a-windows-365-business-cloud-pc-account-type"></a>تعيين نوع حساب كمبيوتر سحابي Windows 365 Business أو تغييره

1.  في جزء التنقل الأيمن في Lighthouse، حدد **"Devices** >  **Windows 365**".

2.  حدد علامة التبويب **"كافة أجهزة الكمبيوتر السحابية** ".

3.  استخدم شريط التعليقات التوضيحية الملونة للتنقل في أجهزة الكمبيوتر السحابية التي لها حالة **توفير** .

4.  من القائمة المنسدلة **"عوامل التصفية** "، حدد نوع ترخيص **الأعمال** للاطلاع على قائمة بجميع أجهزة الكمبيوتر السحابية مع ترخيص Business داخل مستأجري العملاء.

5.  من قائمة أجهزة الكمبيوتر السحابية، حدد كمبيوتر السحابة الذي تريد تغيير نوع الحساب له.

6.  في جزء تفاصيل Cloud PC، حدد **"تغيير نوع الحساب**".

7.  في جزء **نوع حساب Change Cloud PC** ، حدد نوع الحساب للكمبيوتر السحابي، ثم حدد **"حفظ**".

## <a name="next-steps"></a>الخطوات التالية

بمجرد تطبيق التحديث، سيحتاج المستخدم المعين للكمبيوتر السحابي إلى تسجيل الدخول مرة أخرى إلى الكمبيوتر السحابي أو إعادة تشغيل جهازه. قد يستغرق ظهور التغييرات الجديدة في Microsoft 365 Lighthouse عدة دقائق. يمكن لمسؤول الكمبيوتر السحابي أيضا إعادة تشغيل الكمبيوتر السحابي عن بعد، ولكن قد يفقد المستخدم أي بيانات غير محفوظة.

## <a name="related-content"></a>المحتويات ذات الصلة

[التحكم في الوصول المستند إلى دور الكمبيوتر السحابي](/windows-365/enterprise/role-based-access) (مقالة)\
[نظرة عامة على صفحة Windows 365 (أجهزة الكمبيوتر السحابية) في Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md) (مقال)\
[إعادة توفير الكمبيوتر السحابي لـ Windows 365 في Microsoft 365 Lighthouse](m365-lighthouse-reprovision-cloudpc.md) (مقال)
