---
title: قم بإدارة Microsoft Defender لإعدادات تكوين نقطة النهاية على الأجهزة باستخدام دارة نقاط النهاية في Microsoft
description: تعرف على كيفية تمكين إعدادات الأمان في إدارة نقاط النهاية من Microsoft من خلال Microsoft Defender لنقطة النهاية.
keywords: إدارة الأجهزة، وتكوين أجهزة Microsoft Defender لنقطة النهاية، إدارة نقاط النهاية من Microsoft
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
ms.openlocfilehash: 272425ede6895c84c88aa1c4ea165bc0787238bb
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665877"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>قم بإدارة Microsoft Defender لإعدادات تكوين نقطة النهاية على الأجهزة باستخدام دارة نقاط النهاية في Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



[!include[Prerelease information](../../includes/prerelease.md)]


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


إدارة الأمان Microsoft Defender لنقطة النهاية هي إمكانية للأجهزة التي لا تتم إدارتها بواسطة إدارة نقاط النهاية من Microsoft، إما Microsoft Intune أو Microsoft Endpoint Configuration Manager، لتلقي تكوينات الأمان ل Microsoft Defender مباشرة من إدارة نقاط النهاية.


لمزيد من المعلومات حول إدارة تكوين الأمان، بما في ذلك المتطلبات الأساسية والأنظمة الأساسية المدعومة والمزيد، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تحتوي على إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration).



[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>يتم نشر هذه الإمكانية تدريجيا. 

لمزيد من المعلومات حول إدارة تكوين الأمان، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تحتوي على إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration).

إذا واجهت مشاكل في التسجيل، فراجع [استكشاف مشكلات إعداد إدارة تكوين الأمان وإصلاحها](troubleshoot-security-config-mgt.md).

> [!NOTE]
> لا تنطبق هذه الإمكانية على الأجهزة المسجلة بالفعل في إدارة نقاط النهاية من Microsoft (إما Intune أو Configuration Manager). ستستمر الأجهزة المسجلة في Intune في تلقي النهج من خلال قناة الإدارة المنشأة.

## <a name="identify-onboarded-devices"></a>تحديد الأجهزة الملحقة

استخدم الخطوات التالية للتحقق من أن نقاط النهاية قد أكملت إدارة الأمان لعملية إلحاق Microsoft Defender لنقطة النهاية بنجاح.

1.  تحقق من ظهور الجهاز في قسم "مخزون الجهاز" في [Microsoft 365 Defender](https://security.microsoft.com/).

2.  في مدخل [Azure Active Directory](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/)، تحقق من أن الجهاز قد تم تسجيله بنجاح.

3.  في [مركز إدارة إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview)، تحقق من أن الجهاز قد تم تسجيله بنجاح من خلال البحث عنه في قسم **الأجهزة > كافة الأجهزة**.


## <a name="offboard-devices"></a>إيقاف تشغيل الأجهزة
لإلغاء إلحاق الأجهزة التي تم إلحاقها عبر إدارة الأمان Microsoft Defender لنقطة النهاية، راجع [أجهزة Offboard من خدمة Microsoft Defender لنقطة النهاية](offboard-machines.md).

>[!NOTE]
>سيؤدي إلغاء الإلحاق إلى [تعطيل الحماية من العبث](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) إذا تم تمكينها.

## <a name="troubleshooting-security-management"></a>استكشاف أخطاء إدارة الأمان وإصلاحها 
لاستكشاف أخطاء إدارة الأمان وإصلاحها لمشكلات التسجيل Microsoft Defender لنقطة النهاية، راجع [استكشاف أخطاء الإلحاق المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>الموضوع ذو الصلة
- [استكشاف مشكلات الإلحاق المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية](troubleshoot-security-config-mgt.md)
- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
