---
title: حماية أجهزة كمبيوتر Windows وأجهزة Mac غير المدارة في Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
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
description: حماية الأجهزة غير المدارة أو إحضار أجهزتك الخاصة (BYOD) من الهجمات الإلكترونية باستخدام Microsoft 365 Business Premium. كيفية إعداد الأمان عبر الإنترنت لأجهزة الكمبيوتر الشخصية وأجهزة Mac التي تعمل بنظام التشغيل Windows.
ms.openlocfilehash: 10d8edd8a3e8106fc448fa3850590de9f6cda8df
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/04/2022
ms.locfileid: "65892571"
---
# <a name="protect-unmanaged-windows-pcs-and-macs-in-microsoft-365-business-premium"></a>حماية أجهزة كمبيوتر Windows وأجهزة Mac غير المدارة في Microsoft 365 Business Premium

يركز هذا الهدف على إنشاء حماية لأي أجهزة كمبيوتر وأجهزة Mac Windows 10 غير مدارة غير مسجلة في Microsoft Intune. من المحتمل جدا أن يكون لدى شركتك الصغيرة أو حملتك موظفون يجلبون أجهزتهم الخاصة (BYOD)، ولا تتم إدارة هذه الأجهزة. يتضمن BYOD الهواتف وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر الشخصية المملوكة شخصيا.

>[!NOTE]
>يجب على مستخدمي BYOD تثبيت كل تطبيق Company Portal وتشغيله لتسجيل هذه الأجهزة وتلقي الوصول إلى موارد الشركة.

من المهم التأكد من أن مستخدمي الواجهة الأمامية يتبعون هذه الإرشادات بحيث يتم تكوين الحد الأدنى من قدرات الأمان على جميع أجهزة BYOD.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**تشغيل تشفير الجهاز**<p>
يتوفر تشفير الجهاز على مجموعة واسعة من أجهزة Windows ويساعد على حماية بياناتك عن طريق تشفيرها. إذا قمت بتشغيل تشفير الجهاز، فلن يتمكن سوى الأفراد المخولين من الوصول إلى جهازك وبياناتك. راجع [تشغيل تشفير الجهاز للحصول على](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) الإرشادات.

 إذا لم يكن تشفير الجهاز متوفرا على جهازك، يمكنك تشغيل [تشفير BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) القياسي بدلا من ذلك. (BitLocker غير متوفر على إصدار Windows 10 Home.) 

**حماية جهازك باستخدام Windows Security**<p>
إذا كان لديك Windows 10، فستحصل على أحدث حماية من الفيروسات باستخدام أمان Windows. عند بدء تشغيل Windows 10 للمرة الأولى، يكون Windows Security قيد التشغيل ويساعد بنشاط على حماية الكمبيوتر الشخصي من خلال البحث عن البرامج الضارة (البرامج الضارة) والفيروسات وتهديدات الأمان. يستخدم Windows Security الحماية في الوقت الحقيقي لفحص كل ما تقوم بتنزيله أو تشغيله على الكمبيوتر الشخصي.

يقوم Windows Update بتنزيل التحديثات لأمان Windows تلقائيا للمساعدة في الحفاظ على أمان الكمبيوتر وحمايته من التهديدات.

إذا كان لديك إصدار سابق من Windows وتستخدم Microsoft Security Essentials، فمن المستحسن الانتقال إلى أمان Windows. لمزيد من المعلومات، راجع [المساعدة في حماية جهازي باستخدام Windows Security](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**تشغيل جدار حماية Windows**<p>
يجب عليك دائما تشغيل جدار حماية Windows حتى إذا كان لديك جدار حماية آخر قيد التشغيل. قد يؤدي إيقاف تشغيل جدار حماية Windows إلى جعل جهازك (وشبكتك، إذا كان لديك واحد) أكثر عرضة للوصول غير المصرح به. راجع [تشغيل جدار حماية Windows أو إيقاف تشغيله](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) للحصول على الإرشادات.

## <a name="next-mission"></a>المهمة التالية

حسنا، اكتملت المهمة! الآن، دعونا نعمل على [تأمين نظام البريد الإلكتروني](m365bp-protect-email-overview.md) ضد التصيد الاحتيالي والهجمات الأخرى.

## <a name="mac"></a>[ماك](#tab/Mac)

**استخدام FileVault لتشفير قرص Mac**<p>
يحمي تشفير القرص البيانات عند فقدان الأجهزة أو سرقتها. يساعد تشفير القرص الكامل FileVault على منع الوصول غير المصرح به إلى المعلومات الموجودة على قرص بدء التشغيل. راجع [استخدام FileVault لتشفير قرص بدء التشغيل على جهاز Mac](https://support.apple.com/HT204837) للحصول على الإرشادات.

**حماية جهاز Mac من البرامج الضارة**<p>
توصي Microsoft بتثبيت برنامج الحماية من الفيروسات الموثوق به واستخدامه على جهاز Mac. راجع المقالة التالية للحصول على قائمة بالخيارات: [أفضل برنامج الحماية من الفيروسات في Mac 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

يمكنك أيضا تقليل مخاطر البرامج الضارة باستخدام البرامج من مصادر موثوق بها فقط. تسمح لك الإعدادات الموجودة في تفضيلات الخصوصية & الأمان بتحديد مصادر البرامج المثبتة على جهاز Mac. لمزيد من المعلومات، راجع [حماية جهاز Mac من البرامج الضارة](https://support.apple.com/kb/PH25087).

**تشغيل حماية جدار الحماية**<p>
استخدم إعدادات جدار الحماية لحماية جهاز Mac من جهة الاتصال غير المرغوب فيها التي تبدأها أجهزة الكمبيوتر الأخرى عند الاتصال بالإنترنت أو الشبكة. بدون هذه الحماية، قد يكون جهاز Mac الخاص بك أكثر عرضة للوصول غير المصرح به. راجع [جدار حماية التطبيق](https://support.apple.com/HT201642) للحصول على الإرشادات.

## <a name="next-mission"></a>المهمة التالية

حسنا، اكتملت المهمة! الآن، دعونا نعمل على [تأمين نظام البريد الإلكتروني](m365bp-protect-email-overview.md) ضد التصيد الاحتيالي والهجمات الأخرى.