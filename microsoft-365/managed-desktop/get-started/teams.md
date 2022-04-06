---
title: Microsoft Teams
description: كيفية Teams التثبيت على الأجهزة وتحديثها لاحقا
keywords: Microsoft Managed Desktop، Microsoft 365، الخدمة، الوثائق، التطبيقات، تطبيقات خط العمل، تطبيقات LOB
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: ITPro
ms.openlocfilehash: 469edf3e8ae856ea6e94bada8ffb9d6c97ba8b66
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634460"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) هو [تطبيق مراسلة](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0) يوفر أيضا مساحة عمل للتعاون والتواصل في الوقت الحقيقي والاجتماعات ومشاركة الملفات والتطبيقات.

## <a name="initial-deployment"></a>النشر الأولي

لا يتضمن معظم موردي الأجهزة بعد Teams كجزء من صورهم. Microsoft Managed Desktop نشر Teams على أجهزتك باستخدام Microsoft Intune. تم تثبيت حزمة Teams .msi [جميع](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) الأجهزة المدارة. تضمن .msi الحزمة أن جميع المستخدمين، الذين سجلوا الدخول إلى جهاز، Microsoft Teams جاهزين للاستخدام. عند انتهاء تثبيت الحزمة أولا، Teams تلقائيا وإضافة اختصار إلى سطح المكتب.

### <a name="microsoft-intune-changes"></a>Microsoft Intune التغييرات

Microsoft Managed Desktop إلى Microsoft Teams المستأجر: Modern Workplace - Teams Machine Wide Installer x64  

## <a name="updates"></a>التحديثات

Teams مسار تحديث منفصل من Microsoft 365 Apps for enterprise. يقوم عميل سطح المكتب بتحديث نفسه تلقائيا. Teams التحقق من وجود تحديثات كل بضع ساعات، وتنزيلها، ثم انتظار أن يكون الكمبيوتر معطلا قبل تثبيت التحديث بصمت.  

لا Teams مجموعة منتجات المستخدمين للمسؤولين بالتحكم في التحديثات، Microsoft Managed Desktop تستخدم هذه المجموعة قناة [التحديث التلقائي القياسية](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>تحديث Teams

يمكن للمستخدمين الفرديين أيضا تنزيل التحديثات. في الجزء العلوي الأيمن من التطبيق، في قائمة ملف التعريف المنسدلة، حدد **التحقق من وجود تحديثات**. إذا كان هناك تحديث متوفر، سيتم تنزيله وتثبيته بصمت عندما يكون الكمبيوتر معطلا.

## <a name="delivery-optimization-of-updates"></a>تحسين تسليم التحديثات

يتم تشغيل تحسين Teams التحديثات بشكل افتراضي ولا يتطلب أي إجراء من المسؤولين أو المستخدمين.
