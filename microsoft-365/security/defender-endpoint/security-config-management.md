---
title: قم بإدارة Microsoft Defender لإعدادات تكوين نقطة النهاية على الأجهزة باستخدام دارة نقاط النهاية في Microsoft
description: تعرف على كيفية تمكين إعدادات الأمان في Microsoft إدارة نقاط النهاية من خلال Microsoft Defender لنقطة النهاية.
keywords: إدارة الأجهزة وتكوين أجهزة Microsoft Defender لنقطة النهاية وMicrosoft إدارة نقاط النهاية
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
ms.openlocfilehash: 2c19352d584bedc5acd94f9984242a2c50d2fcf3
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573902"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>قم بإدارة Microsoft Defender لإعدادات تكوين نقطة النهاية على الأجهزة باستخدام دارة نقاط النهاية في Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام Microsoft إدارة نقاط النهاية](/mem/intune/protect/mde-security-integration)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


إدارة الأمان Microsoft Defender لنقطة النهاية هي إمكانية للأجهزة التي لا تديرها إدارة نقاط النهاية Microsoft لتلقي تكوينات الأمان ل Microsoft Defender مباشرة من إدارة نقاط النهاية.


لمزيد من المعلومات حول إدارة تكوين الأمان، بما في ذلك المتطلبات الأساسية والأنظمة الأساسية المدعومة والمزيد، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام Microsoft إدارة نقاط النهاية](/mem/intune/protect/mde-security-integration).

شاهد هذا الفيديو لمعرفة كيفية استخدام Microsoft إدارة نقاط النهاية لإدارة تكوين الأمان Microsoft Defender لنقطة النهاية.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVq]

[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>يتم نشر هذه الإمكانية تدريجيا. 

لمزيد من المعلومات حول إدارة تكوين الأمان، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام Microsoft إدارة نقاط النهاية](/mem/intune/protect/mde-security-integration).

إذا واجهت مشاكل في التسجيل، فراجع [استكشاف مشكلات إعداد إدارة تكوين الأمان وإصلاحها](troubleshoot-security-config-mgt.md).

> [!NOTE]
> لا تنطبق هذه الإمكانية على الأجهزة المسجلة بالفعل في Microsoft إدارة نقاط النهاية (إما Intune أو Configuration Manager). ستستمر الأجهزة المسجلة في Intune في تلقي النهج من خلال قناة الإدارة المنشأة.

## <a name="identify-onboarded-devices"></a>تحديد الأجهزة الملحقة

استخدم الخطوات التالية للتحقق من أن نقاط النهاية قد أكملت إدارة الأمان لعملية إلحاق Microsoft Defender لنقطة النهاية بنجاح.

1.  تحقق من ظهور الجهاز في قسم "مخزون الجهاز" في [Microsoft 365 Defender](https://security.microsoft.com/).

2.  في مدخل [Azure Active Directory](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/)، تحقق من أن الجهاز قد تم تسجيله بنجاح.

3.  في [مركز إدارة نقاط النهاية مسؤول Microsoft](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview)، تحقق من أن الجهاز قد تم تسجيله بنجاح من خلال البحث عنه في قسم **الأجهزة > كافة الأجهزة**.


## <a name="offboard-devices"></a>إيقاف تشغيل الأجهزة
لإلغاء إلحاق الأجهزة التي تم إلحاقها عبر إدارة الأمان Microsoft Defender لنقطة النهاية، راجع [أجهزة Offboard من خدمة Microsoft Defender لنقطة النهاية](offboard-machines.md).

>[!NOTE]
>سيؤدي إلغاء الإلحاق إلى [تعطيل الحماية من العبث](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) إذا تم تمكينها.

## <a name="troubleshooting-security-management"></a>استكشاف أخطاء إدارة الأمان وإصلاحها 
لاستكشاف أخطاء إدارة الأمان وإصلاحها لمشكلات التسجيل Microsoft Defender لنقطة النهاية، راجع [استكشاف أخطاء الإلحاق المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>الموضوع ذو الصلة
- [استكشاف مشكلات الإلحاق المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية](troubleshoot-security-config-mgt.md)
- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام Microsoft إدارة نقاط النهاية](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
