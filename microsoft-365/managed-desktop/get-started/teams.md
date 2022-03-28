---
title: Microsoft Teams
description: كيفية Teams التثبيت على الأجهزة وتحديثها لاحقا
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق، التطبيقات، تطبيقات خط العمل، تطبيقات LOB
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: ITPro
ms.openlocfilehash: 3dfdd9f5187fba9a1e19e56a4df24cf1f7eff44b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575388"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) هو [تطبيق مراسلة](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0) يوفر أيضا مساحة عمل للتعاون والتواصل في الوقت الحقيقي والاجتماعات ومشاركة الملفات والتطبيقات.

## <a name="initial-deployment"></a>النشر الأولي

لا يتضمن معظم موردي الأجهزة بعد Teams كجزء من صورهم. ينشر Microsoft Managed Desktop Teams على أجهزتك باستخدام Microsoft Intune. تم تثبيت حزمة Teams .msi [جميع](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) الأجهزة المدارة. تضمن .msi الحزمة أن جميع المستخدمين، الذين سجلوا الدخول إلى جهاز، Microsoft Teams جاهزين للاستخدام. عند انتهاء تثبيت الحزمة أولا، Teams تلقائيا وإضافة اختصار إلى سطح المكتب.

### <a name="microsoft-intune-changes"></a>Microsoft Intune التغييرات

يضيف Microsoft Managed Desktop تطبيقين إلى مؤسسة Azure AD Microsoft Teams. يتم نشرها إلى عملاء 64 بت أو 32 بت حسب ملاءمة الجهاز:  

- Modern Workplace - Teams Machine Wide Installer x64  
- Modern Workplace - Teams Machine Wide Installer x32

## <a name="updates"></a>التحديثات

Teams مسار تحديث منفصل من Microsoft 365 Apps for enterprise. يقوم عميل سطح المكتب بتحديث نفسه تلقائيا. Teams التحقق من وجود تحديثات كل بضع ساعات، وتنزيلها، ثم انتظار أن يكون الكمبيوتر معطلا قبل تثبيت التحديث بصمت.  

لا Teams مجموعة منتجات microsoft للمسؤولين بالتحكم في التحديثات، لذلك يستخدم Microsoft Managed Desktop قناة التحديث [التلقائي القياسية](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>تحديث Teams

يمكن للمستخدمين الفرديين أيضا تنزيل التحديثات. في الجزء العلوي الأيمن من التطبيق، في قائمة ملف التعريف المنسدلة، حدد **التحقق من وجود تحديثات**. إذا كان هناك تحديث متوفر، سيتم تنزيله وتثبيته بصمت عندما يكون الكمبيوتر معطلا.

## <a name="delivery-optimization-of-updates"></a>تحسين تسليم التحديثات

يتم تشغيل تحسين Teams التحديثات بشكل افتراضي ولا يتطلب أي إجراء من المسؤولين أو المستخدمين.
