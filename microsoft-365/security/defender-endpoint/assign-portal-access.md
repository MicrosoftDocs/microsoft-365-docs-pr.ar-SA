---
title: تعيين وصول المستخدم إلى مركز حماية Microsoft Defender
description: تعيين حق الوصول للقراءة والكتابة أو القراءة فقط إلى مدخل Microsoft Defender لنقطة النهاية.
keywords: تعيين أدوار المستخدمين وتعيين حق الوصول للقراءة والكتابة وتعيين الوصول للقراءة فقط والمستخدم وأدوار المستخدمين والأدوار
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/28/2018
ms.technology: mde
ms.openlocfilehash: fa0157a37cf25efcdcf1b578473b4dc2f6deb10d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63575730"
---
# <a name="assign-user-access-to-microsoft-defender-security-center"></a>تعيين وصول المستخدم إلى مركز حماية Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- Azure Active Directory
- Office 365
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يدعم Defender for Endpoint طريقتين لإدارة الأذونات:

- **إدارة الأذونات الأساسية**: تعيين الأذونات للوصول الكامل أو للقراءة فقط.
- التحكم بالوصول المستند إلى الدور **(RBAC): تعيين الأذونات** الدقيقة من خلال تعريف الأدوار وتعيين مجموعات مستخدمي Azure AD إلى الأدوار ومنح مجموعات المستخدمين حق الوصول إلى مجموعات الأجهزة. لمزيد من المعلومات حول RBAC، راجع [إدارة الوصول إلى المدخل باستخدام التحكم بالوصول المستند إلى الدور](rbac.md).

> [!NOTE]
> إذا سبق لك تعيين أذونات أساسية، يمكنك التبديل إلى RBAC في أي وقت. فكر في ما يلي قبل إجراء التبديل:
>
> - يتم تلقائيا تعيين دور المسؤول الافتراضي Defender لمسؤول نقطة النهاية للمستخدمين الذين تم تعيين دور دليل مسؤول الأمان أو المسؤول العام لهم في Azure AD) تلقائيا. يمكن تعيين مجموعات مستخدم Azure AD إضافية إلى دور مسؤول Defender لنقطة النهاية بعد التبديل إلى RBAC. يمكن فقط للمستخدمين المعينين لدور مسؤول Defender for Endpoint إدارة الأذونات باستخدام RBAC. 
> - سيفقد المستخدمون الذين لديهم حق الوصول للقراءة فقط (قارئات الأمان) الوصول إلى المدخل حتى يتم تعيين دور لهم. تجدر الإشارة إلى أنه يمكن تعيين دور لمجموعات مستخدمي Azure AD فقط ضمن RBAC.
> - بعد التبديل إلى RBAC، لن تتمكن من العودة إلى استخدام إدارة الأذونات الأساسية.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [استخدام الأذونات الأساسية للوصول إلى المدخل](basic-permissions.md)
- [إدارة الوصول إلى المدخل باستخدام RBAC](rbac.md)
