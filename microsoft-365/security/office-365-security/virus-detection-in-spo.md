---
title: الحماية من الفيروسات المضمنة في SharePoint عبر الإنترنت OneDrive و Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: reference
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: تعرف على SharePoint يكشف SharePoint Online عن وجود فيروسات في الملفات التي يقوم المستخدمون بتحميلها ويمنع المستخدمين من تنزيل الملفات أو مزامنتها.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ddb424458e991becefb98efbad5b2a86c5f9441c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566552"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>الحماية من الفيروسات المضمنة في SharePoint عبر الإنترنت OneDrive و Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)

Microsoft 365 مشغلا شائعا للكشف عن الفيروسات لمسح الملفات التي يقوم المستخدمون بتحميلها إلى SharePoint و OneDrive و Microsoft Teams. يتم تضمين هذه الحماية مع جميع الاشتراكات التي تتضمن SharePoint عبر الإنترنت OneDrive و Microsoft Teams.

> [!IMPORTANT]
> إمكانات مكافحة الفيروسات المضمنة هي طريقة للمساعدة في احتواء الفيروسات. فهي ليست نقطة حماية واحدة من البرامج الضارة  بيئتك. نحن نشجع جميع العملاء على التحقق من الحماية من البرامج الضارة وتطبيقها على طبقات مختلفة وتطبيق أفضل الممارسات لتأمين البنية الأساسية للمؤسسة. لمزيد من المعلومات حول الاستراتيجيات وأفضل الممارسات، راجع [خارطة طريق الأمان](security-roadmap.md).

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>ماذا يحدث إذا تم تحميل ملف موبوء إلى SharePoint عبر الإنترنت؟

يعمل Microsoft 365 الكشف عن الفيروسات بشكل غير متزامن (مستقل عن تحميل الملفات) ضمن SharePoint Online. **لا يتم فحص جميع الملفات تلقائيا**. تحدد نتائج الإحصاء الملفات التي تريد فحصها. عند العثور على ملف يحتوي على فيروس، يتم وضع علامة على الملف. في أبريل 2018، قمنا بإزالة حد 25 MB للملفات الممسوحة ضوئيا.

إليك ما يحدث:

1. يقوم المستخدم بتحميل ملف إلى SharePoint Online.
2. SharePoint Online، كجزء من عمليات فحص الفيروسات الخاصة به، في وقت لاحق تحديد ما إذا كان الملف يلبي معايير الفحص أم لا.
3. إذا كان الملف يلبي معايير الفحص، يقوم مشغل الكشف عن الفيروسات بفحص الملف.
4. إذا تم العثور على فيروس داخل الملف الممسوحة ضوئيا، فإن محرك الفيروسات يحدد خاصية على الملف تشير إلى أنه ملوث.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>ماذا يحدث عندما يحاول المستخدم تنزيل ملف موبوء باستخدام المستعرض؟

إذا تم إصابة ملف، لا يمكن للمستخدمين تنزيل الملف من SharePoint عبر الإنترنت باستخدام مستعرض.

إليك ما يحدث:

1. يفتح المستخدم مستعرض ويب ويحاول تنزيل ملف موبوء من SharePoint Online.
2. يتم إعطاء المستخدم تحذيرا بأنه تم الكشف عن فيروس. بشكل افتراضي، يتم منح المستخدم خيار تنزيل الملف ومحاولة تنظيفه باستخدام برنامج مكافحة الفيروسات على جهازه الخاص.

> [!NOTE]
>
> يمكن للمسؤولين استخدام المعلمة *DisallowInfectedFileDownload* على الأمر [cmdlet Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant) في SharePoint Online PowerShell لمنع المستخدمين من تنزيل الملفات المصابة، حتى في نافذة تحذير مكافحة الفيروسات. للحصول على الإرشادات، راجع [استخدام SharePoint Online PowerShell لمنع المستخدمين من تنزيل ملفات ضارة](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).
>
> بمجرد تمكين المعلمة *DisallowInfectedFileDownload* ، يتم حظر الوصول إلى الملفات المكتشفة/المحظورة بالكامل للمستخدمين المسؤولين.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>ماذا يحدث عندما يحاول العميل المزامنة من OneDrive مزامنة ملف موبوء؟

عند تحميل ملف ضار إلى OneDrive، سيتم مزامنته إلى الجهاز المحلي قبل وضع علامة عليه كبرامج ضارة. بعد وضع علامة على البرنامج الضار، لن يستطيع المستخدم فتح الملف الذي تتم مزامنته بعد الآن من جهازه المحلي.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>الإمكانات الموسعة مع Microsoft Defender Office 365

Microsoft 365 المؤسسات التي لديها [Microsoft Defender for Office 365](defender-for-office-365.md) مضمنة في اشتراكها أو التي تم شراؤها كعناة إضافية تمكين مرفقات خزينة ل SharePoint و OneDrive و Microsoft Teams لإعداد التقارير والحماية المحسنة. لمزيد من المعلومات، راجع خزينة [المرفقات SharePoint OneDrive Microsoft Teams](mdo-for-spo-odb-and-teams.md).

## <a name="related-articles"></a>المقالات ذات الصلة

[الحماية من البرامج الضارة والفدية الضارة في Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)

لمزيد من المعلومات حول مكافحة الفيروسات في SharePoint Online و OneDrive و Microsoft Teams، راجع الحماية من التهديدات و تشغيل مرفقات [خزينة ل SharePoint و OneDrive و Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).[](protect-against-threats.md)
