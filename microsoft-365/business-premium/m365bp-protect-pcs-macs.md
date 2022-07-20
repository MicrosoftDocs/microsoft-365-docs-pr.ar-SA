---
title: حماية أجهزة كمبيوتر Windows وأجهزة Mac غير المدارة في Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: حماية الأجهزة غير المدارة أو إحضار أجهزتك الخاصة (BYOD) من الهجمات الإلكترونية باستخدام Microsoft 365 Business Premium. كيفية إعداد الأمان عبر الإنترنت لأجهزة الكمبيوتر الشخصية وأجهزة Mac التي تعمل بنظام التشغيل Windows.
ms.openlocfilehash: c6010661d11be2af064ddd3d5250f1cf9baacc09
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894350"
---
# <a name="protect-unmanaged-windows-pcs-and-macs-in-microsoft-365-business-premium"></a>حماية أجهزة كمبيوتر Windows وأجهزة Mac غير المدارة في Microsoft 365 Business Premium

يركز هذا الهدف على إنشاء حماية لأي أجهزة كمبيوتر وأجهزة Mac Windows 10 غير مدارة غير مسجلة في Microsoft Intune. من المحتمل جدا أن يكون لدى شركتك الصغيرة أو حملتك موظفون يجلبون أجهزتهم الخاصة (BYOD)، ولا تتم إدارة هذه الأجهزة. يتضمن BYOD الهواتف وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر الشخصية المملوكة شخصيا.

> [!NOTE]
> يجب على مستخدمي BYOD تثبيت وتشغيل تطبيق Company Portal لتسجيل هذه الأجهزة وتلقي الوصول إلى موارد الشركة.

من المهم التأكد من أن مستخدمي الواجهة الأمامية يتبعون هذه الإرشادات بحيث يتم تكوين الحد الأدنى من قدرات الأمان على جميع أجهزة BYOD.

## <a name="windows-10-or-11"></a>[Windows 10 أو 11](#tab/Windows10-11)

## <a name="windows-10-or-11"></a>Windows 10 أو 11

### <a name="turn-on-device-encryption"></a>تشغيل تشفير الجهاز

يتوفر تشفير الجهاز على مجموعة واسعة من أجهزة Windows ويساعد على حماية بياناتك عن طريق تشفيرها. إذا قمت بتشغيل تشفير الجهاز، فلن يتمكن سوى الأفراد المخولين من الوصول إلى جهازك وبياناتك. راجع [تشغيل تشفير الجهاز للحصول على](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) الإرشادات.

 إذا لم يكن تشفير الجهاز متوفرا على جهازك، يمكنك تشغيل [تشفير BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) القياسي بدلا من ذلك. (BitLocker غير متوفر في إصدار Windows 10 Home.) 

### <a name="protect-your-device-with-windows-security"></a>حماية جهازك باستخدام أمن Windows

إذا كان لديك Windows 10 أو 11، فستحصل على أحدث حماية من الفيروسات باستخدام أمن Windows. عندما تبدأ Windows 10 للمرة الأولى، يكون أمن Windows قيد التشغيل ويساعد بنشاط على حماية الكمبيوتر الشخصي من خلال البحث عن البرامج الضارة (البرامج الضارة) والفيروسات والتهديدات الأمنية. تستخدم أمن Windows الحماية في الوقت الحقيقي لفحص كل شيء تقوم بتنزيله أو تشغيله على الكمبيوتر الشخصي.

Windows Update تنزيل تحديثات أمن Windows تلقائيا للمساعدة في الحفاظ على أمان الكمبيوتر وحمايته من التهديدات.

إذا كان لديك إصدار سابق من Windows وتستخدم Microsoft Security Essentials، فمن المستحسن الانتقال إلى أمن Windows. لمزيد من المعلومات، راجع [المساعدة في حماية جهازي باستخدام أمن Windows](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

### <a name="turn-on-windows-defender-firewall"></a>تشغيل جدار حماية Windows Defender

يجب عليك دائما تشغيل جدار حماية Windows Defender حتى إذا كان لديك جدار حماية آخر قيد التشغيل. قد يؤدي إيقاف تشغيل جدار حماية Windows Defender إلى جعل جهازك (وشبكتك، إذا كان لديك واحد) أكثر عرضة للوصول غير المصرح به. راجع [تشغيل جدار حماية Windows أو إيقاف تشغيله](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) للحصول على الإرشادات.

## <a name="next-mission"></a>المهمة التالية

حسنا، اكتملت المهمة! الآن، دعونا نعمل على [تأمين نظام البريد الإلكتروني](m365bp-protect-email-overview.md) ضد التصيد الاحتيالي والهجمات الأخرى.

## <a name="mac"></a>[ماك](#tab/Mac)

## <a name="mac"></a>ماك

### <a name="use-filevault-to-encrypt-your-mac-disk"></a>استخدام FileVault لتشفير قرص Mac

يحمي تشفير القرص البيانات عند فقدان الأجهزة أو سرقتها. يساعد تشفير القرص الكامل FileVault على منع الوصول غير المصرح به إلى المعلومات الموجودة على قرص بدء التشغيل. راجع [استخدام FileVault لتشفير قرص بدء التشغيل على جهاز Mac](https://support.apple.com/HT204837) للحصول على الإرشادات.

### <a name="protect-your-mac-from-malware"></a>حماية جهاز Mac من البرامج الضارة

توصي Microsoft بتثبيت برنامج الحماية من الفيروسات الموثوق به واستخدامه على جهاز Mac. راجع المقالة التالية للحصول على قائمة بالخيارات: [أفضل برنامج الحماية من الفيروسات في Mac 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

يمكنك أيضا تقليل مخاطر البرامج الضارة باستخدام البرامج من مصادر موثوق بها فقط. تسمح لك الإعدادات الموجودة في تفضيلات الخصوصية & الأمان بتحديد مصادر البرامج المثبتة على جهاز Mac. لمزيد من المعلومات، راجع [حماية جهاز Mac من البرامج الضارة](https://support.apple.com/kb/PH25087).

### <a name="turn-on-firewall-protection"></a>تشغيل حماية جدار الحماية

استخدم إعدادات جدار الحماية لحماية جهاز Mac من جهة الاتصال غير المرغوب فيها التي تبدأها أجهزة الكمبيوتر الأخرى عند الاتصال بالإنترنت أو الشبكة. بدون هذه الحماية، قد يكون جهاز Mac الخاص بك أكثر عرضة للوصول غير المصرح به. راجع [جدار حماية التطبيق](https://support.apple.com/HT201642) للحصول على الإرشادات.

## <a name="next-mission"></a>المهمة التالية

حسنا، اكتملت المهمة! الآن، لنعمل على [تأمين استخدام البريد الإلكتروني](m365bp-protect-email-overview.md) ضد التصيد الاحتيالي والهجمات الأخرى.