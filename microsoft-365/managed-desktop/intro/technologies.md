---
title: تقنيات سطح المكتب المدار من Microsoft
description: تسرد هذه المقالة التقنيات والتطبيقات المستخدمة في Microsoft Managed Desktop.
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 302666c6b29d2cffd4db641509f14ba616cfd459
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566481"
---
# <a name="microsoft-managed-desktop-technologies"></a>تقنيات سطح المكتب المدار من Microsoft

تسرد هذه المقالة التقنيات والتطبيقات المستخدمة في Microsoft Managed Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Enterprise الترخيص مطلوبا لجميع مستخدمي سطح المكتب المدار من Microsoft. لمزيد من المعلومات حول متطلبات الترخيص للخدمة، راجع [المتطلبات الأساسية لسطح المكتب المدار من Microsoft](../get-ready/prerequisites.md).

تلخص هذه المقالة المكونات المضمنة في تراخيص Enterprise المطلوبة، وكيفية استخدام الخدمة لكل مكون مع أجهزة Microsoft Managed Desktop. يتم تفصيل الأدوار والمسؤوليات المعينة لكل منطقة في وثائق سطح المكتب المدار من Microsoft.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 أو E5

| المنتج | معلومات |
| ----- | ----- |
| Microsoft 365 Apps for enterprise (64 بت) | سيتم شحن Office التالية مع الجهاز:<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Publisher</li><li>وصول</li><li>Skype for Business</li><li>OneNote</li></ul><br>لا يتم تضمين الإصدارات الكاملة Microsoft Project 64 بت Visio Microsoft. ومع ذلك، بما أن تثبيت هذه التطبيقات يعتمد على Microsoft 365 Apps تثبيت Enterprise، فقد أنشأ Microsoft Managed Desktop عمليات نشر Microsoft Intune الافتراضية ومجموعات الأمان التي يمكنك استخدامها لنشر هذه التطبيقات للمستخدمين المرخصين. لمزيد من المعلومات، راجع [تثبيت Microsoft Project أو Microsoft Visio على أجهزة سطح المكتب المدارة من Microsoft](../get-started/project-visio.md). |
| OneDrive | يتم تمكين Azure Active Directory Single Sign On للمستخدمين عند تسجيل الدخول لأول مرة OneDrive.<br><br>يتم تضمين مجلدات "إعادة توجيه المجلدات" المعروفة لسطح المكتب والمستند والصور. يتم تمكين هذه المجلدات وتكوينها بواسطة Microsoft Managed Desktop. |
| تطبيقات المتجر | لا يتم شحن Microsoft Sway و Power BI مع الجهاز. تتوفر هذه التطبيقات للتنزيل من Microsoft Store. |
| تطبيقات Win32 | Teams يتم شحنها مع الجهاز، ولكن يتم حزمها وموفرة بواسطة Microsoft لأجهزة سطح المكتب المدارة من Microsoft. لا يتم شحن Azure Information Protection Client مع الجهاز، ولكن يمكنك أن تقوم بحزمه للنشر. |
| تطبيقات الويب | لا يتم شحن تطبيقات الويب التالية مع الجهاز: <ul><li>Yammer</li><li>Office في مستعرض</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>تطبيقات الطاقة</li><li>Planner</li></ul> <br>يمكن للمستخدمين الوصول إلى إصدار الويب لهذه التطبيقات باستخدام مستعرض. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Enterprise E5 أو E3 باستخدام Microsoft Defender لنقطة النهاية

نوصي بأن يكون مسؤولو المعلومات لديك الإعدادات التالية.

> [!NOTE]
> لا يتم تضمين هذه الإعدادات أو إدارتها كجزء من Microsoft Managed Desktop.

| المنتج | معلومات |
| ----- | ----- |
| Windows Hello for Business | يجب تنفيذ Windows Hello for Business لاستبدال كلمات المرور بمصادقة قوية ثنائية لأجهزة سطح المكتب المدارة من Microsoft. لمزيد من المعلومات، [راجع Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| ظاهرية التطبيق | يمكنك نشر حزم Application Virtualization (App-V) باستخدام عميل إدارة تطبيق Intune Win32. لمزيد من المعلومات، راجع [ظاهرية التطبيق](/windows/application-management/app-v/appv-technical-reference). |
| Microsoft 365 فقدان البيانات | يجب تنفيذ Microsoft 365 فقدان البيانات لمراقبة الإجراءات التي تم اتخاذها على العناصر التي حددت أنها حساسة، وللمساعدة على منع المشاركة غير المقصودة لتلك العناصر. لمزيد من المعلومات، [راجع Microsoft 365 فقدان البيانات](../../compliance/endpoint-dlp-learn-about.md). |

الميزات المضمنة والمدارة كجزء من Microsoft Managed Desktop:

| المنتج | معلومات |
| ----- | ----- |
| تشفير محرك أقراص BitLocker | يتم استخدام تشفير محرك أقراص BitLocker لتشفير كل محركات أقراص النظام. لمزيد من المعلومات، راجع [تشفير محرك أقراص BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| Windows Defender System Guard | يحمي تكامل النظام عند بدء التشغيل، ويتحقق من أن تكامل النظام قد تم الاحتفاظ به بالفعل. لمزيد من المعلومات، راجع Windows [Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Windows بيانات اعتماد Defender | Windows "حماية بيانات الاعتماد ل Defender" الأمان المستند إلى الظاهرية لعزل الأسرار بحيث لا يمكن الوصول إليها إلا من قبل برامج النظام المتميزة. لمزيد من المعلومات، راجع Windows [Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Microsoft Defender لنقطة النهاية - الكشف عن نقطة النهاية والاستجابة | تستجيب عمليات أمان سطح المكتب المدارة من Microsoft للتنبيهات وتأخذ إجراءات للرد على التهديدات باستخدام الكشف عن نقاط النهاية والاستجابة لها. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - الكشف عن نقطة النهاية والاستجابة لها](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response). |
| Microsoft Defender لنقطة النهاية - خبراء التهديدات | يتكامل Microsoft Managed Desktop مع تحليلات خبراء المخاطر وبياناتهم من خلال إعلامات الهجمات المستهدفة. يجب عليك تقديم موافقة إضافية قبل تمكين هذه الخدمة. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - خبراء التهديدات](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Microsoft Defender لنقطة النهاية - إدارة المخاطر والثغرات | مطلوب للاستخدام في المستقبل في خطة خدمة Microsoft Managed Desktop. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - إدارة المخاطر والثغرات الأمنية](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Microsoft Defender لنقطة النهاية - تقليل مساحة الهجوم | تستهدف سلوكيات البرامج الخطر التي غالبا ما يتم إساءة استخدامها من قبل المهاجمين. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - تقليل مساحة الهجوم](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Microsoft Defender لنقطة النهاية - الحماية من استغلال | يحمي من البرامج الضارة التي تستخدم عمليات استغلال لإصابة الأجهزة، وتوزع البيانات من خلال تطبيق أساليب تقليل المخاطر تلقائيا على عمليات وتطبيقات نظام التشغيل. لمزيد من المعلومات، راجع [Microsoft Defender ل Endpoint - الحماية من استغلال.](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) |
| Microsoft Defender لنقطة النهاية - حماية الشبكة | توسيع نطاق Microsoft Defender SmartScreen لحظر كل عمليات مرور HTTP وHTTPS الصادرة التي تحاول الاتصال بمصادر ذات سمعة منخفضة. لمزيد من المعلومات، راجع [Microsoft Defender ل Endpoint - حماية الشبكة](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| الحماية من التلاعب في Microsoft Defender | Windows استخدام الحماية من العبث لمنع تغيير إعدادات الأمان مثل الحماية من الفيروسات. لمزيد من المعلومات، راجع [الحماية من التلاعب في Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| برنامج الحماية من الفيروسات من Microsoft Defender الحماية من الفيروسات المستندة إلى السلوك والحماية من الفيروسات في الوقت الحقيقي | قم دائما بالفحص للكشف عن تهديدات الملفات و المعالجة التي قد لا يتم الكشف عنها كبرامج ضارة. لمزيد من المعلومات، راجع برنامج الحماية من الفيروسات من Microsoft Defender الحماية من الفيروسات المستندة إلى السلوك، [والحماية](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) من الفيروسات في الوقت الحقيقي. |
| برنامج الحماية من الفيروسات من Microsoft Defender السحابة | يوفر حماية تلقائية وديناميكية قريبة من المخاطر الجديدة والناشئة. لمزيد من المعلومات، [راجع برنامج الحماية من الفيروسات من Microsoft Defender السحابة.](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus) |
| Microsoft Defender لنقطة النهاية - "الحظر من النظرة الأولى" | يوفر الكشف عن البرامج الضارة الجديدة وحظرها Windows الكشف عن ملف مريب أو غير معروف. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - الحظر من النظرة الأولى](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| برنامج الحماية من الفيروسات من Microsoft Defender المحتمل أن تكون غير مرغوب فيها | يستخدم لحظر التطبيقات التي يمكن أن تتسبب في تشغيل جهازك ببطء، أو عرض إعلانات غير متوقعة، أو، في أسوأ الأحوال، تثبيت برامج أخرى قد تكون غير متوقعة أو غير مرغوب فيها. لمزيد من المعلومات، راجع برنامج الحماية من الفيروسات من Microsoft Defender [التي قد تكون غير مرغوب فيها](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| Windows Defender مع الأمان المتقدم | تقوم تصفية حركة مرور الشبكة المستندة إلى المضيف والمزددفة لجهاز ما Windows جدار الحماية ل Defender بحظر حركة مرور الشبكة غير المصرح بها التي تتدفق إلى الجهاز المحلي أو خارجه. لمزيد من المعلومات، [راجع Windows Defender Firewall مع الأمان المتقدم](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). |
| التحكم في حساب المستخدم | يقوم "التحكم في حساب المستخدم" بالتبديل إلى "سطح المكتب الآمن" عندما تتطلب مهمة أو إجراء وصول من نوع حساب المسؤول. يتم تعيين وصول مستخدم قياسي لمستخدمي سطح المكتب المدار من Microsoft عند التسجيل. لمزيد من المعلومات، راجع [التحكم في حساب المستخدم](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| المنتج | معلومات |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory Premium P2 | يمكنك استخدام جميع ميزات Enterprise Mobility + Security E3 لإدارة أجهزة MDM.<br><br>يمكنك استخدام Azure Active Directory Premium P2 كمميزة اختيارية مع Microsoft Managed Desktop. |
| Microsoft Defender لتطبيقات السحابة | يمكنك استخدام هذه الميزة الاختيارية مع Microsoft Managed Desktop.
| Azure Information Protection P2  | يمكنك استخدام هذه الميزة الاختيارية مع Microsoft Managed Desktop.
