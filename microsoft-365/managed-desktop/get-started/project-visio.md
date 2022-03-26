---
title: تثبيت Microsoft Project أو Microsoft Visio على أجهزة سطح المكتب المدارة من Microsoft
description: معلومات حول تثبيت Microsoft Project أو Microsoft Visio على أجهزة سطح المكتب المدارة من Microsoft
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، Microsoft Project، Microsoft Visio
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: ab8a68ed17a8705c6e391371600d7b56660f6c57
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63568526"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>تثبيت Microsoft Project أو Microsoft Visio على أجهزة سطح المكتب المدارة من Microsoft

Microsoft Project Microsoft Visio خطوات معينة لكي يتم تثبيتها على أجهزة سطح المكتب المدارة من Microsoft. توثق هذه المقالة المتطلبات الأساسية وعملية التثبيت لهذه التطبيقات.

## <a name="prerequisites"></a>المتطلبات الأساسية

يجب على المسؤولين التحقق من أنهم يلبيون هذه المتطلبات الأساسية:

| المتطلبات الأساسية | الوصف |
| ------ | ------ |
| كميات التراخيص | يجب أن تتوفر التراخيص Microsoft Project و Microsoft Visio للمستخدمين. يدعم Microsoft Managed Desktop حاليا إصدارات 64 بت فقط من هذه التطبيقات. |
| أسماء التراخيص | أسماء التراخيص المناسبة لهذه التطبيقات هي: <ul><li>**Microsoft Project** - Project Online Professional أو Project Online Premium</li><li>**Microsoft Visio** - Visio Online الخطة 2</li><ul> |
| Company Portal | يجب Company Portal في المستأجر حتى يقوم المستخدمون بتثبيت هذه التطبيقات. إذا لم Company Portal في المستأجر، [فشاهد Company Portal](company-portal.md). |

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>نشر Project Visio لأجهزة سطح المكتب المدارة من Microsoft

سيضيف Microsoft Managed Desktop Microsoft Project و Microsoft Visio تطبيقين Win32 في Microsoft Intune. سنقوم أيضا بإنشاء المجموعتين في Azure Active Directory. سيتم تعيين المجموعات إلى التطبيق المناظر بهدف "متوفر".

**لنشر Project Visio:**

أضف المستخدم إلى المجموعة المناسبة وسيصبح التطبيق متوفرا في Company Portal. قد تستغرق المزامنة بضع دقائق، ولكن يمكن للمستخدمين تثبيت التطبيقات من Company Portal.

اسم مجموعة Azure AD | أي مستخدمين يجب تعيينهم؟
 --- | ---
Modern Workplace-Office-Project_Install | يحتاج المستخدمون Project
Modern Workplace-Office-Visio_Install | يحتاج المستخدمون Visio

## <a name="communicate-changes"></a>التواصل مع التغييرات

من المهم لمسؤولي تكنولوجيا المعلومات أن يعلموا المستخدمين بكيفية تثبيت Project Visio. يتضمن هذا الاتصال:

- إعلام المستخدمين عند توفر هذه التطبيقات لهم.
- إرشادات حول كيفية تثبيت هذه التطبيقات من Company Portal.
