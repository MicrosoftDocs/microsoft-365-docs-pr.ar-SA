---
title: إدارة إعدادات تكوين Microsoft Defender لنقطة النهاية على الأجهزة التي تستخدم إدارة نقاط النهاية من Microsoft
description: تعرف على كيفية تمكين إعدادات الأمان في إدارة نقاط النهاية من Microsoft من خلال Microsoft Defender لنقطة النهاية.
keywords: إدارة الأجهزة، وتكوين Microsoft Defender للأجهزة Endpoint، إدارة نقاط النهاية من Microsoft
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
ms.technology: mde
ms.openlocfilehash: e21346b48f65016465e669369aa14b3f4c85c23b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63583716"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>إدارة إعدادات تكوين Microsoft Defender لنقطة النهاية على الأجهزة التي تستخدم إدارة نقاط النهاية من Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تستخدم إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



[!include[Prerelease information](../../includes/prerelease.md)]


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


إدارة الأمان ل Microsoft Defender ل Endpoint هي إمكانية للأجهزة التي لا يتم إدارتها بواسطة إدارة نقاط النهاية من Microsoft، إما Microsoft Intune أو Microsoft Endpoint Configuration Manager ، لتلقي تكوينات الأمان ل Microsoft Defender مباشرة من إدارة نقاط النهاية.


لمزيد من المعلومات حول إدارة تكوين الأمان، بما في ذلك المتطلبات الأساسية و الأنظمة الأساسية المعتمدة والمزيد، راجع إدارة [Microsoft Defender لنقطة](/mem/intune/protect/mde-security-integration) النهاية على الأجهزة التي تتضمن إدارة نقاط النهاية من Microsoft.



[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>يتم طرح هذه الإمكانية تدريجيا. 

لمزيد من المعلومات حول إدارة تكوين الأمان، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تستخدم إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration).

إذا واجهت مشاكل في التسجيل، فشاهد استكشاف مشاكل [تشغيل إدارة تكوين الأمان وإصلاحها](troubleshoot-security-config-mgt.md).

> [!NOTE]
> لا تنطبق هذه الإمكانية على الأجهزة التي تم تسجيلها بالفعل في إدارة نقاط النهاية من Microsoft (إما Intune أو Configuration Manager). ستستمر الأجهزة التي تم تسجيلها في Intune في تلقي السياسات من خلال قناة الإدارة التي تم تأسيسها.

## <a name="identify-onboarded-devices"></a>تحديد الأجهزة المجهزة

استخدم الخطوات التالية للتحقق من أن نقاط النهاية قد أكملت بنجاح عملية إدارة الأمان ل Microsoft Defender ل تعيين نقاط النهاية.

1.  تحقق من ظهور الجهاز في قسم مخزون [الجهاز في Microsoft 365 Defender](https://security.microsoft.com/).

2.  في مدخل [Azure Active Directory](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/)، تحقق من تسجيل الجهاز بنجاح.

3.  في إدارة نقاط النهاية من Microsoft [إدارة](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview) الأجهزة، تحقق من أن الجهاز قد تم تسجيله بنجاح من خلال البحث عنه في المقطع الأجهزة **> كافة** الأجهزة.


## <a name="offboard-devices"></a>أجهزة إيقاف التشغيل
ل إيقاف تشغيل الأجهزة التي تم تشغيلها عبر إدارة الأمان ل Microsoft Defender ل Endpoint، راجع أجهزة إيقاف التشغيل من [خدمة Microsoft Defender لنقطة النهاية](offboard-machines.md).

>[!NOTE]
>سيؤدي إلغاء [االدبور إلى تعطيل الحماية](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) من العبث إذا تم تمكينها.

## <a name="troubleshooting-security-management"></a>استكشاف مشاكل إدارة الأمان وإصلاحها 
استكشاف مشاكل تسجيل إدارة الأمان ل Microsoft Defender لنقطة النهاية وإصلاحها، راجع استكشاف مشاكل الالتحاق وإصلاحها المتعلقة بإدارة الأمان ل [Microsoft Defender لنقطة النهاية](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>موضوع ذو صلة
- [استكشاف المشاكل المتعلقة بإدارة الأمان ل Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-security-config-mgt.md)
- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تستخدم إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
