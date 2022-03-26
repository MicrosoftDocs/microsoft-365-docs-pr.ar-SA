---
title: قم خزينة المرفقات SharePoint OneDrive و Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: يمكن للمسؤولين معرفة كيفية تشغيل خزينة للملفات SharePoint و OneDrive و Microsoft Teams، بما في ذلك كيفية تعيين تنبيهات للملفات التي تم الكشف عنها.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6501097251f4001c58a651db7ddb34bc623e9b0a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63574230"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>قم خزينة المرفقات SharePoint OneDrive و Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يحمي Microsoft Defender Office 365 SharePoint OneDrive و Microsoft Teams مؤسستك من مشاركة الملفات الضارة عن غير قصد. لمزيد من المعلومات، راجع خزينة [المرفقات SharePoint OneDrive Microsoft Teams](mdo-for-spo-odb-and-teams.md).

تحتوي هذه المقالة على الخطوات اللازمة لتمكين خزينة المرفقات SharePoint OneDrive Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

- لكي خزينة مرفقات SharePoint و OneDrive و Microsoft Teams، يجب أن تكون عضوا في مجموعات دور مسؤول إدارة المؤسسة أو مسؤول الأمان في مدخل Microsoft 365 Defender.  لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).

- لاستخدام SharePoint Online PowerShell لمنع الأشخاص من تنزيل ملفات ضارة، يجب أن تكون عضوا في "المسؤول العام" أو SharePoint أدوار المسؤولين [](/azure/active-directory/roles/permissions-reference#global-administrator) في Azure [](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) AD.

- تحقق من تمكين تسجيل التدقيق لمنظمتك. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](../../compliance/turn-audit-log-search-on-or-off.md).

- السماح حتى 30 دقيقة لكي يتم تطبيق الإعدادات.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>الخطوة 1: استخدام مدخل Microsoft 365 Defender تشغيل خزينة لمرفقات SharePoint OneDrive Microsoft Teams

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>،  \>  \> انتقل إلى & قواعد المخاطر خزينة **المرفقات** في **المقطع سياسات**. الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، انقر فوق **إعدادات عام**.

3. في قائمة **الإعدادات** "عام" التي تظهر، انتقل إلى المقطع حماية الملفات في SharePoint OneDrive **Microsoft Teams.**

   قم **بتحريك تشغيل Defender Office 365 SharePoint** ![OneDrive و Microsoft Teams إلى اليمين تشغيل.](../../media/scc-toggle-on.png) ل تشغيل خزينة المرفقات SharePoint OneDrive Microsoft Teams.

   عند الانتهاء، انقر فوق **حفظ**.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>استخدم Exchange Online PowerShell ل تشغيل خزينة للمرفقات SharePoint OneDrive و Microsoft Teams

إذا كنت تفضل استخدام PowerShell لتشغيل مرفقات خزينة ل SharePoint و OneDrive و Microsoft Teams، فاتصل ب [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) و قم بتشغيل الأمر التالي:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>الخطوة 2: (مستحسن) استخدام SharePoint Online PowerShell لمنع المستخدمين من تنزيل ملفات ضارة

بشكل افتراضي<sup>\*</sup>، لا يمكن للمستخدمين فتح الملفات الضارة التي تم الكشف عنها بواسطة مرفقات خزينة أو OneDrive أو OneDrive SharePoint أو Microsoft Teams. ومع ذلك، يمكنهم حذف الملفات الضارة وتنزيلها.

<sup>\*</sup> إذا انتقل المستخدمون إلى **إدارة الوصول**، فإن **الخيار مشاركة** لا يزال متوفرا.

لمنع المستخدمين من تنزيل الملفات الضارة، اتصل [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) ثم قم بتشغيل الأمر التالي:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**ملاحظات**:

- يؤثر هذا الإعداد على كل من المستخدمين المسؤولين.
- لا يزال يمكن للأشخاص حذف الملفات الضارة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>الخطوة 3 (مستحسن) استخدام مدخل Microsoft 365 Defender لإنشاء نهج تنبيه للملفات التي تم الكشف عنها

يمكنك إنشاء نهج تنبيه يتم من خلاله اعريفك أنت والمسؤولين الآخرين عندما تكتشف خزينة المرفقات ل SharePoint و OneDrive و Microsoft Teams ملف ضار. لمعرفة المزيد حول التنبيهات، راجع [سياسات التنبيهات](../../compliance/alert-policies.md).

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **نهج** \> & **نهج التنبيه**. الانتقال مباشرة إلى صفحة **نهج التنبيه** ، استخدم <https://security.microsoft.com/alertpolicies>.

2. في صفحة **نهج التنبيه** ، انقر فوق **نهج تنبيه جديد**.

3. يتم **فتح معالج نهج** التنبيه الجديد في عملية منفتحة. في صفحة **تسمية التنبيه** ، قم بتكوين الإعدادات التالية:
   - **الاسم**: اكتب اسما فريدا ووصفيا. على سبيل المثال، الملفات الضارة في المكتبات.
   - **الوصف**: اكتب وصفا اختياريا. على سبيل المثال، يتم اعريف المسؤولين عند اكتشاف ملفات ضارة في SharePoint أو OneDrive أو Microsoft Teams.
   - **الخطورة**: حدد **منخفض** أو **متوسط** أو **عال** من القائمة المنسدل.
   - **الفئة**: حدد **إدارة المخاطر** من القائمة المنسدل.

   عند الانتهاء، انقر فوق **التالي**.

4. في الصفحة **إنشاء إعدادات التنبيه** ، قم بتكوين الإعدادات التالية:
   - **ما الذي تريد التنبيه عليه؟** النشاط \> **هو** \> تحديد **البرامج الضارة التي تم الكشف عنها في ملف** من القائمة المنسدل.
   - **كيف تريد تشغيل التنبيه؟** القسم: اترك القيمة الافتراضية **في كل مرة يتطابق فيها نشاط مع القاعدة** المحددة.

   عند الانتهاء، انقر فوق **التالي**.

5. في الصفحة **تعيين المستلمين** ، قم بتكوين الإعدادات التالية:
   - تحقق **من تحديد إرسال إعلامات** البريد الإلكتروني. في المربع **مستلمو** البريد الإلكتروني، حدد واحدا أو أكثر من المسؤولين العامين أو مسؤولي الأمان أو برامج قراءة الأمان الذين يجب أن يتلقوا إعلاما عند الكشف عن ملف ضار.
   - **حد الإعلام اليومي**: اترك القيمة الافتراضية **بلا** حد محدد.

   عند الانتهاء، انقر فوق **التالي**.

6. في الصفحة **مراجعة الإعدادات** ، راجع الإعدادات. يمكنك تحديد **تحرير** في كل مقطع لتعديل الإعدادات ضمن المقطع. أو يمكنك النقر فوق **الخلف** أو تحديد الصفحة المحددة في المعالج.

   في المقطع **هل تريد تشغيل** النهج على الفور؟ اترك القيمة الافتراضية نعم، قم ب تشغيلها **على الفور** محددة.

   عند الانتهاء، انقر فوق **إنهاء**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>استخدام الأمان & التوافق PowerShell لإنشاء نهج تنبيه للملفات التي تم الكشف عنها

إذا كنت تفضل استخدام PowerShell لإنشاء نهج التنبيه نفسه كما هو موضح في القسم السابق، فاتصل بمركز التوافق & [PowerShell](/powershell/exchange/connect-to-scc-powershell) ثم قم بتشغيل الأمر التالي:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**ملاحظة**: قيمة _الخطورة الافتراضية_ منخفضة. لتحديد متوسط أو عال، قم _بتضمين معلمة الخطورة_ والقيمة في الأمر.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>كيف يمكنك معرفة كيفية عمل هذه الإجراءات؟

- للتحقق من أنك قمت بنجاح خزينة المرفقات ل SharePoint و OneDrive و Microsoft Teams، استخدم أي من الخطوات التالية:

  - في مدخل Microsoft 365 Defender، انتقل إلى القسم سياسات المخاطر **&** \>  \>  \> قواعد **خزينة** المرفقات، وحدد الإعدادات العامة، وتحقق من قيمة تشغيل Defender **for Office 365 SharePoint، OneDrive ، Microsoft Teams** الإعداد.

  - في Exchange Online PowerShell، يمكنك تشغيل الأمر التالي للتحقق من إعداد الخاصية:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- للتحقق من أنك منعت الأشخاص بنجاح من تنزيل الملفات الضارة، افتح SharePoint Online PowerShell، ثم قم بتشغيل الأمر التالي للتحقق من قيمة الخاصية:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- للتحقق من أنك قمت بتكوين نهج تنبيه للملفات التي تم الكشف عنها بنجاح، استخدم أي من الخطوات التالية:
  - في Microsoft 365 Defender،  \>  \> انتقل إلى نهج & نهج التنبيه حدد نهج التنبيه، وتحقق من الإعدادات.
  - في Microsoft 365 Defender PowerShell\<AlertPolicyName\>، استبدل باسم نهج التنبيه، ثم ادير الأمر التالي وتحقق من قيم الخاصية:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- استخدم تقرير [حالة الحماية من المخاطر](view-email-security-reports.md#threat-protection-status-report) لعرض معلومات حول الملفات التي تم اكتشافها في SharePoint OneDrive Microsoft Teams. بشكل خاص، يمكنك استخدام عرض **البيانات من خلال: طريقة عرض المحتوى \> البرامج الضارة** .
