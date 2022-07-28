---
title: الحماية المضمنة من الفيروسات في SharePoint Online وOneDrive وMicrosoft Teams
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
description: تعرف على كيفية اكتشاف SharePoint Online للفيروسات في الملفات التي يقوم المستخدمون بتحميلها ومنع المستخدمين من تنزيل الملفات أو مزامنتها.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b04e9a1ca2e722a2f581441f44716c22be7a1635
ms.sourcegitcommit: 1e53bf8208c30d7b60685896207cc1142bebf34a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67059678"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>الحماية المضمنة من الفيروسات في SharePoint Online وOneDrive وMicrosoft Teams

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)

يستخدم Microsoft 365 محركا شائعا للكشف عن الفيروسات لفحص الملفات التي يقوم المستخدمون بتحميلها إلى SharePoint Online وOneDrive وMicrosoft Teams. يتم تضمين هذه الحماية مع جميع الاشتراكات التي تتضمن SharePoint Online وOneDrive وMicrosoft Teams.

> [!IMPORTANT]
> قدرات مكافحة الفيروسات المضمنة هي طريقة للمساعدة في احتواء الفيروسات. لا يقصد بها أن تكون نقطة دفاع واحدة ضد البرامج الضارة وبيئتك. نحن نشجع جميع العملاء على التحقق من الحماية من البرامج الضارة وتنفيذها في طبقات مختلفة وتطبيق أفضل الممارسات لتأمين البنية الأساسية للمؤسسة الخاصة بهم. لمزيد من المعلومات حول الاستراتيجيات وأفضل الممارسات، راجع [مخطط الأمان](security-roadmap.md).

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>ماذا يحدث إذا تم تحميل ملف مصاب إلى SharePoint Online؟

يعمل محرك الكشف عن الفيروسات في Microsoft 365 بشكل غير متزامن (مستقل عن تحميلات الملفات) داخل SharePoint Online. **لا يتم مسح كافة الملفات ضوئيا تلقائيا**. تحدد الأساليب الاستدائية الملفات التي يجب فحصها. عند العثور على ملف يحتوي على فيروس، يتم وضع علامة على الملف. في أبريل 2018، قمنا بإزالة حد 25 ميغابايت للملفات الممسوحة ضوئيا.

إليك ما يحدث:

1. يقوم مستخدم بتحميل ملف إلى SharePoint Online.
2. يحدد SharePoint Online لاحقا، كجزء من عمليات فحص الفيروسات، ما إذا كان الملف يفي بمعايير الفحص.
3. إذا كان الملف يفي بمعايير الفحص، يقوم محرك الكشف عن الفيروسات بمسح الملف.
4. إذا تم العثور على فيروس داخل الملف الممسوح ضوئيا، يقوم محرك الفيروسات بتعيين خاصية على الملف تشير إلى أن الملف مصاب.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>ماذا يحدث عندما يحاول المستخدم تنزيل ملف مصاب باستخدام المستعرض؟

بشكل افتراضي، يمكن للمستخدمين تنزيل الملفات المصابة من SharePoint Online. إليك ما يحدث:

1. في مستعرض ويب، يحاول مستخدم تنزيل ملف من SharePoint Online يحدث أن يكون مصابا.
2. يظهر للمستخدم تحذير بأنه تم الكشف عن فيروس في الملف. يتم منح المستخدم خيار متابعة التنزيل ومحاولة تنظيفه باستخدام برنامج مكافحة الفيروسات على جهازه.

لتغيير هذا السلوك حتى لا يتمكن المستخدمون من تنزيل الملفات المصابة، حتى من نافذة التحذير ضد الفيروسات، يمكن للمسؤولين استخدام المعلمة *DisallowInfectedFileDownload* على **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** cmdlet في SharePoint Online PowerShell. تمنع القيمة $true لمعلمة *DisallowInfectedFileDownload* الوصول الكامل إلى الملفات المكتشفة/المهتزة للمستخدمين.

للحصول على الإرشادات، راجع [استخدام SharePoint Online PowerShell لمنع المستخدمين من تنزيل ملفات ضارة](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

## <a name="can-admins-bypass-disallowinfectedfiledownload-and-extract-infected-files"></a>هل يمكن للمسؤولين تجاوز *DisallowInlowInfectedFileDownload* واستخراج الملفات المصابة؟

يسمح لمسؤولي SharePoint والمسؤولين العموميين بإجراء عمليات استخراج الملفات الجنائية للملفات المصابة بالبرامج الضارة في SharePoint Online PowerShell باستخدام [Get-SPOMalwareFileContent](/powershell/module/sharepoint-online/get-spomalwarefilecontent) cmdlet. لا يحتاج المسؤولون إلى الوصول إلى الموقع الذي يستضيف المحتوى المصاب. طالما تم وضع علامة على الملف على أنه برنامج ضار، يمكن للمسؤولين استخدام **Get-SPOMalwareFileContent** لاستخراج الملف. 

لمزيد من المعلومات حول الملف المصاب، يمكن للمسؤولين استخدام **[Get-SPOMalwareFile](/powershell/module/sharepoint-online/get-spomalwarefile)** cmdlet للاطلاع على نوع البرامج الضارة التي تم الكشف عنها وحالة العدوى. 

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>ماذا يحدث عندما يحاول عميل المزامنة من OneDrive مزامنة ملف مصاب؟

عند تحميل ملف ضار إلى OneDrive، ستتم مزامنته مع الجهاز المحلي قبل أن يتم وضع علامة عليه على أنه برنامج ضار. بعد وضع علامة على الملف على أنه برنامج ضار، لن يتمكن المستخدم من فتح الملف الذي تمت مزامنته بعد الآن من جهازه المحلي.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>القدرات الموسعة مع Microsoft Defender لـ Office 365

يمكن لمؤسسات Microsoft 365 التي [Microsoft Defender لـ Office 365](defender-for-office-365.md) مضمنة في اشتراكها أو تم شراؤها كوظيفة إضافية تمكين "المرفقات الآمنة" ل SharePoint وOneDrive وMicrosoft Teams لإعداد التقارير والحماية المحسنة. لمزيد من المعلومات، راجع ["المرفقات الآمنة" ل SharePoint وOneDrive وMicrosoft Teams](mdo-for-spo-odb-and-teams.md).

## <a name="related-articles"></a>المقالات ذات الصلة

[البرامج الضارة والحماية من برامج الفدية الضارة في Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)

لمزيد من المعلومات حول مكافحة الفيروسات في SharePoint Online وOneDrive وMicrosoft Teams، راجع [الحماية من التهديدات](protect-against-threats.md) [وتشغيل المرفقات الآمنة ل SharePoint وOneDrive وMicrosoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).
