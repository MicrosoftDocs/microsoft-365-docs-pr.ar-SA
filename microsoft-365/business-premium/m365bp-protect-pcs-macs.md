---
title: حماية أجهزة الكمبيوتر الشخصية Windows 10 التي لم Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: حماية الأجهزة غير التي لم يتم إدراجها أو إحضارها بنفسك (BYOD) باستخدام Microsoft 365 Business Premium.
ms.openlocfilehash: b3d783ba498337af7ff867fe749366abe1734da5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705003"
---
# <a name="protect-unmanaged-windows-10-pcs-and-macs-in-microsoft-365-business-premium"></a>حماية أجهزة الكمبيوتر الشخصية Windows 10 التي لم Microsoft 365 Business Premium

يمكنك إدارة Windows 10 الشخصية و Mac من خلال تسجيلها في Microsoft Intune، مما يسمح لك بالتأكد من أنها سليمة وآمنة قبل الوصول إلى البيانات في بيئتك. ومع ذلك، تتضمن العديد من الحملات والشركات الصغيرة الموظفين الذين يجلبون أجهزتهم الخاصة (BYOD)، والتي لن تديرها المؤسسة. بالنسبة إلى أجهزة الكمبيوتر الشخصية و Mac غير المضمنة هذه، استخدم هذه المقالة لضمان تكوين الحد الأدنى من قدرات الأمان.

<!--A Windows 10 PC is considered managed after you have completed the following two steps:

1. You (or the admin) set up device and data protection policies in the [setup  wizard](../business/set-up.md).

2. You have [connected your computer to Azure Active Directory](../business/set-up-windows-devices.md) and use your Microsoft 365 username and password to sign in.
3. --> 

## <a name="protect-a-computer-running-windows-10-or-a-mac"></a>حماية كمبيوتر يعمل Windows 10 أو جهاز Mac

<!--If you have a PC that is running Windows 10 that is not connected to Microsoft 365, or a Mac, the Microsoft 365 protections do not apply to it, but here are some things you can do to keep your data secure on these devices as well:
-->
إذا لم Windows 10 الكمبيوتر الشخصي أو جهاز Mac بواسطة مؤسستك، فتأكد من تكوين قدرات الأمان هذه.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**تشغيل تشفير الأجهزة**<p>

يتوفر تشفير الأجهزة على مجموعة واسعة من Windows الأجهزة ويساعد على حماية بياناتك عن طريق تشفيرها. إذا قمت ب تشغيل تشفير الأجهزة، لن يتمكن من الوصول إلى جهازك وبياناتك سوى الأشخاص المخولاين. راجع [تشغيل تشفير الأجهزة](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) للحصول على الإرشادات.

 إذا لم يكن تشفير الجهاز متوفرا على جهازك، يمكنك تشغيل تشفير [BitLocker القياسي](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) بدلا من ذلك. (BitLocker غير متوفر على إصدار Windows 10 Home.) 

**حماية جهازك باستخدام أمن Windows**<p>
إذا كان لديك Windows 10، ستحصل على أحدث حماية من الفيروسات باستخدام أمن Windows. عند بدء Windows 10 للمرة الأولى، أمن Windows تشغيل الكمبيوتر الشخصي ومساعدته بنشاط على حماية الكمبيوتر الشخصي من خلال إجراء مسح ضوئي بحثا عن البرامج الضارة والفيروسات وتهديدات الأمان. أمن Windows استخدام الحماية في الوقت الحقيقي لمسح كل شيء تقوم بتنزيلها أو تشغيلها على الكمبيوتر الشخصي.

Windows تنزيلات التحديثات أمن Windows تلقائيا للمساعدة في الحفاظ على أمان الكمبيوتر وحمايته من التهديدات.

إذا كان لديك إصدار سابق من Windows كنت تستخدم Microsoft Security Essentials، فمن الجيد الانتقال إلى أمن Windows. لمزيد من المعلومات، راجع [المساعدة في حماية جهازي باستخدام أمن Windows](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**تشغيل جدار Windows الحماية**<p>
يجب أن تقوم دائما Windows جدار الحماية حتى لو كان لديك جدار حماية آخر تم تشغيله. قد يجعل Windows جدار الحماية جهازك (شبكتك، إذا كان لديك واحدة) أكثر عرضة للوصول غير المصرح به. راجع [تشغيل Windows جدار الحماية أو إيقاف](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) تشغيله للحصول على الإرشادات.

## <a name="mac"></a>[Mac](#tab/Mac)

**استخدام FileVault لتشفير قرص Mac**<p>
يحمي تشفير القرص البيانات عند فقدان الأجهزة أو سرقتها. يساعد تشفير القرص الكامل FileVault على منع الوصول غير المصرح به إلى المعلومات على قرص بدء التشغيل. راجع [استخدام FileVault لتشفير قرص بدء التشغيل على جهاز Mac](https://support.apple.com/HT204837) للحصول على الإرشادات.

**حماية جهاز mac من البرامج الضارة**<p>
توصي Microsoft بتثبيت برنامج الحماية من الفيروسات الموثوق به واستخدامه على جهاز Mac. راجع المقالة التالية للحصول على قائمة الاختيارات: أفضل برنامج مكافحة الفيروسات [ل Mac 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

يمكنك أيضا تقليل مخاطر البرامج الضارة باستخدام البرامج من مصادر موثوق بها فقط. تسمح لك الإعدادات في & الخصوصية بتحديد مصادر البرامج المثبتة على جهاز Mac. لمزيد من المعلومات، راجع [حماية جهاز Mac من البرامج الضارة](https://support.apple.com/kb/PH25087).

**تشغيل حماية جدار الحماية**<p>
استخدم إعدادات جدار الحماية لحماية جهاز Mac من جهة الاتصال غير المرغوب فيها التي تبدأها أجهزة كمبيوتر أخرى عندما تكون متصلا بالإنترنت أو بشبكة. بدون هذه الحماية، قد يكون جهاز Mac الخاص بك أكثر عرضة للوصول غير المصرح به. راجع [حول جدار حماية التطبيق](https://support.apple.com/HT201642) للحصول على الإرشادات.
