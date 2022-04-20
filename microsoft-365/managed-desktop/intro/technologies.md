---
title: تقنيات Microsoft Managed Desktop
description: تسرد هذه المقالة التقنيات والتطبيقات المستخدمة في Microsoft Managed Desktop.
keywords: Microsoft Managed Desktop، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d7a7b6889451d83aaa6c2b53c1dce6ed035f9916
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945616"
---
# <a name="microsoft-managed-desktop-technologies"></a>تقنيات Microsoft Managed Desktop

تسرد هذه المقالة التقنيات والتطبيقات المستخدمة في Microsoft Managed Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

الترخيص Microsoft 365 Enterprise مطلوب لجميع المستخدمين Microsoft Managed Desktop. لمزيد من المعلومات حول متطلبات الترخيص للخدمة، راجع [المتطلبات الأساسية Microsoft Managed Desktop](../get-ready/prerequisites.md).

تلخص هذه المقالة المكونات المضمنة في تراخيص المؤسسة المطلوبة، وكيف تستخدم الخدمة كل مكون مع أجهزة Microsoft Managed Desktop. وتفصل الأدوار والمسؤوليات المحددة لكل مجال في وثائق Microsoft Managed Desktop.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 أو E5

| المنتج | المعلومات |
| ----- | ----- |
| Microsoft 365 Apps for enterprise (64 بت) | سيتم شحن تطبيقات Office التالية مع الجهاز:<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Publisher</li><li>وصول</li><li>Skype for Business</li><li>OneNote</li></ul><br>لا يتم تضمين الإصدارات الكاملة 64 بت من Microsoft Project وMicrosoft Visio. ومع ذلك، بما أن تثبيت هذه التطبيقات يعتمد على Microsoft 365 Apps لتثبيت Enterprise، Microsoft Managed Desktop إنشاء عمليات نشر Microsoft Intune الافتراضية ومجموعات الأمان التي يمكنك استخدامها لنشر هذه التطبيقات للمستخدمين المرخصين. لمزيد من المعلومات، راجع [تثبيت Microsoft Project أو Microsoft Visio على أجهزة Microsoft Managed Desktop](../get-started/project-visio.md). |
| OneDrive | يتم تمكين تسجيل الدخول الأحادي إلى Azure Active Directory للمستخدمين عند تسجيل الدخول لأول مرة إلى OneDrive.<br><br>يتم تضمين إعادة توجيه المجلدات المعروفة لمجلدات سطح المكتب والمستند والصور. يتم تمكين هذه المجلدات وتكوينها بواسطة Microsoft Managed Desktop. |
| تطبيقات المتجر | لا يتم شحن Microsoft Sway وPower BI مع الجهاز. تتوفر هذه التطبيقات للتنزيل من Microsoft Store. |
| تطبيقات Win32 | لا يتم شحن Teams مع الجهاز، ولكن يتم حزمه وتوفيره من قبل Microsoft للأجهزة Microsoft Managed Desktop. لا يتم شحن Azure حماية البيانات Client مع الجهاز، ولكن يمكنك حزمه للنشر. |
| تطبيقات ويب | لا يتم شحن تطبيقات الويب التالية مع الجهاز: <ul><li>Yammer</li><li>Office في مستعرض</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>تطبيقات الطاقة</li><li>Planner</li></ul> <br>يمكن للمستخدمين الوصول إلى إصدار الويب لهذه التطبيقات باستخدام مستعرض. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Enterprise E5 أو E3 مع Microsoft Defender لنقطة النهاية

نوصي مسؤولي تكنولوجيا المعلومات بتكوين الإعدادات التالية.

> [!NOTE]
> لا يتم تضمين هذه الإعدادات أو إدارتها كجزء من Microsoft Managed Desktop.

| المنتج | المعلومات |
| ----- | ----- |
| Windows Hello للأعمال | يجب تنفيذ Windows Hello للأعمال لاستبدال كلمات المرور بمصادقة قوية ثنائية العوامل للأجهزة Microsoft Managed Desktop. لمزيد من المعلومات، راجع [Windows Hello للأعمال](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| المحاكاة الظاهرية للتطبيق | يمكنك نشر حزم Application Virtualization (App-V) باستخدام عميل إدارة تطبيقات Intune Win32. لمزيد من المعلومات، راجع [المحاكاة الظاهرية للتطبيق](/windows/application-management/app-v/appv-technical-reference). |
| منع فقدان بيانات Microsoft Purview | يجب تنفيذ منع فقدان البيانات لمراقبة الإجراءات التي تم اتخاذها على العناصر التي حددت أنها حساسة، وللمساعدة في منع المشاركة غير المقصودة لتلك العناصر. لمزيد من المعلومات، راجع [منع فقدان البيانات](../../compliance/endpoint-dlp-learn-about.md). |

الميزات المضمنة والمدارة كجزء من Microsoft Managed Desktop:

| المنتج | المعلومات |
| ----- | ----- |
| تشفير محرك الأقراص BitLocker | يتم استخدام تشفير محرك الأقراص BitLocker لتشفير جميع محركات أقراص النظام. لمزيد من المعلومات، راجع [تشفير محرك أقراص BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| حماية نظام Windows Defender | يحمي تكامل النظام عند بدء التشغيل، ويتحقق من أن تكامل النظام قد تم الحفاظ عليه حقا. لمزيد من المعلومات، راجع [حماية نظام Windows Defender](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| حماية بيانات اعتماد Windows Defender | يستخدم Windows Defender Credential Guard الأمان المستند إلى الظاهرية لعزل الأسرار بحيث يمكن لبرنامج النظام المتميز فقط الوصول إليها. لمزيد من المعلومات، راجع [حماية نظام Windows Defender](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Microsoft Defender لنقطة النهاية - الكشف عن نقطة النهاية والاستجابة لها | Microsoft Managed Desktop تستجيب عمليات الأمان للتنبيهات وتتخذ إجراءات لمعالجة التهديدات باستخدام الكشف عن نقطة النهاية والاستجابة لها. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - الكشف عن نقطة النهاية والاستجابة](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) لها. |
| Microsoft Defender لنقطة النهاية - خبراء التهديد | يتكامل Microsoft Managed Desktop مع رؤى وبيانات خبراء التهديد من خلال إعلامات الهجوم المستهدف. يجب تقديم موافقة إضافية قبل تمكين هذه الخدمة. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - خبراء التهديد](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Microsoft Defender لنقطة النهاية - إدارة المخاطر والثغرات الأمنية | مطلوب للاستخدام المستقبلي في خطة خدمة Microsoft Managed Desktop. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - إدارة المخاطر والثغرات الأمنية](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Microsoft Defender لنقطة النهاية - تقليل الأجزاء المعرضة للهجوم | يستهدف سلوكيات البرامج المحفوفة بالمخاطر التي غالبا ما يتم إساءة استخدامها من قبل المهاجمين. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - تقليل الأجزاء المعرضة للهجوم](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Microsoft Defender لنقطة النهاية - الحماية من الاستغلال | يحمي من البرامج الضارة التي تستخدم مهاجمات لإصابة الأجهزة، وينتشر من خلال تطبيق تقنيات التخفيف من الاستغلال تلقائيا على عمليات وتطبيقات نظام التشغيل. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - الحماية من الاستغلال](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection). |
| Microsoft Defender لنقطة النهاية - حماية الشبكة | توسيع نطاق Microsoft Defender SmartScreen لحظر كافة نسبة استخدام شبكة HTTP وHTTPS الصادرة التي تحاول الاتصال بمصادر ذات سمعة منخفضة. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - Network Protection](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| حماية العبث ب Microsoft Defender | يتم استخدام Windows الحماية من العبث لمنع تغيير إعدادات الأمان مثل الحماية من الفيروسات. لمزيد من المعلومات، راجع [حماية العبث ب Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| برنامج الحماية من الفيروسات من Microsoft Defender الحماية من الفيروسات المستندة إلى السلوك والمستندة إلى السلوك والحماية من الفيروسات في الوقت الحقيقي | افحص دائما بحثا عن تهديدات الملفات ومعالجتها التي قد لا يتم اكتشافها على أنها برامج ضارة. لمزيد من المعلومات، راجع [برنامج الحماية من الفيروسات من Microsoft Defender الحماية من الفيروسات المستندة إلى السلوك والمعرفية والحماية من الفيروسات في الوقت الحقيقي](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md). |
| برنامج الحماية من الفيروسات من Microsoft Defender الحماية المقدمة من السحابة | يوفر حماية ديناميكية شبه فورية وآلية ضد التهديدات الجديدة والناشئة. لمزيد من المعلومات، راجع [برنامج الحماية من الفيروسات من Microsoft Defender الحماية المقدمة من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus). |
| Microsoft Defender لنقطة النهاية - "حظر من النظرة الأولى" | يوفر الكشف عن البرامج الضارة الجديدة وحظرها عندما يكشف Windows عن ملف مريب أو غير معروف. لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية - حظر للوهلة الأولى](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| برنامج الحماية من الفيروسات من Microsoft Defender التطبيقات التي يحتمل أن تكون غير مرغوب فيها | يستخدم لحظر التطبيقات التي قد تتسبب في تشغيل جهازك ببطء، أو عرض إعلانات غير متوقعة، أو في أسوأ الأحوال، تثبيت برامج أخرى قد تكون غير متوقعة أو غير مرغوب فيها. لمزيد من المعلومات، راجع [برنامج الحماية من الفيروسات من Microsoft Defender التطبيقات التي يحتمل أن تكون غير مرغوب فيها](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| جدار حماية Windows Defender مع الأمان المتقدم | تقوم تصفية نسبة استخدام الشبكة ثنائية الاتجاه المستندة إلى المضيف لجهاز ما، Windows Defender Firewall بحظر نسبة استخدام الشبكة غير المصرح بها التي تتدفق إلى الجهاز المحلي أو خارجه. لمزيد من المعلومات، راجع [Windows Defender Firewall مع الأمان المتقدم](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). |
| التحكم في حساب المستخدم | يقوم عنصر تحكم حساب المستخدم بالتبديل إلى "سطح المكتب الآمن" عندما تتطلب مهمة أو إجراء الوصول من نوع حساب المسؤول. يتم تعيين وصول المستخدم القياسي للمستخدمين Microsoft Managed Desktop عند التسجيل. لمزيد من المعلومات، راجع [التحكم في حساب المستخدم](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| المنتج | المعلومات |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory Premium P2 | يمكنك استخدام جميع ميزات Enterprise Mobility + Security E3 لإدارة أجهزة MDM.<br><br>يمكنك استخدام Azure Active Directory Premium P2 كميزة اختيارية مع Microsoft Managed Desktop. |
| Microsoft Defender for Cloud Apps | يمكنك استخدام هذه الميزة الاختيارية مع Microsoft Managed Desktop.
| Azure حماية البيانات P2  | يمكنك استخدام هذه الميزة الاختيارية مع Microsoft Managed Desktop.
