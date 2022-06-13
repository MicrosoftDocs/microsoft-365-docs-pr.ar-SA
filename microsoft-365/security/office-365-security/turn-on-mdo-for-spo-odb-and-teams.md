---
title: تشغيل مرفقات آمنةSharePoint وOneDrive وMicrosoft Teams
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
description: يمكن للمسؤولين معرفة كيفية تشغيل مرفقات خزينة SharePoint OneDrive Microsoft Teams، بما في ذلك كيفية تعيين التنبيهات للملفات المكتشفة.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 55923b13cf47e0309a7246ba43dcb9adaf3c58ff
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015999"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>تشغيل مرفقات آمنةSharePoint وOneDrive وMicrosoft Teams

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender لـ Office 365 SharePoint OneDrive Microsoft Teams تحمي مؤسستك من مشاركة الملفات الضارة عن غير قصد. لمزيد من المعلومات، راجع [خزينة المرفقات SharePoint OneDrive Microsoft Teams](mdo-for-spo-odb-and-teams.md).

تحتوي هذه المقالة على خطوات تمكين خزينة المرفقات وتكوينها SharePoint OneDrive Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

- لتشغيل خزينة المرفقات SharePoint OneDrive Microsoft Teams، يجب أن تكون عضوا في مجموعات أدوار **مسؤول الأمان أو إدارة المؤسسة** في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- لاستخدام SharePoint Online PowerShell لمنع الأشخاص من تنزيل ملفات ضارة، يجب أن تكون عضوا في [المسؤول العام](/azure/active-directory/roles/permissions-reference#global-administrator) أو [SharePoint أدوار المسؤول](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) في Azure AD.

- تحقق من تمكين تسجيل التدقيق لمؤسستك. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](../../compliance/turn-audit-log-search-on-or-off.md).

- السماح بما يصل إلى 30 دقيقة حتى يتم تطبيق الإعدادات.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>الخطوة 1: استخدام مدخل Microsoft 365 Defender لتشغيل مرفقات خزينة SharePoint OneDrive Microsoft Teams

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **نهج قواعد & نهج** \> **التهديد** \> **خزينة المرفقات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، انقر فوق **الإعدادات العمومية**.

3. في **الإعدادات العمومية** التي تظهر، انتقل إلى قسم **حماية الملفات في SharePoint OneDrive Microsoft Teams**.

   انقل **Defender لـ Office 365 التشغيل للتبديل SharePoint OneDrive Microsoft Teams** إلى زر التبديل الأيمن![.](../../media/scc-toggle-on.png) لتشغيل مرفقات خزينة SharePoint OneDrive Microsoft Teams.

   عند الانتهاء، انقر فوق **حفظ**.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>استخدم Exchange Online PowerShell لتشغيل مرفقات خزينة SharePoint OneDrive Microsoft Teams

إذا كنت تفضل استخدام PowerShell لتشغيل مرفقات خزينة SharePoint OneDrive Microsoft Teams، [فقم بالاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) وتشغيل الأمر التالي:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>الخطوة 2: (مستحسن) استخدم SharePoint Online PowerShell لمنع المستخدمين من تنزيل ملفات ضارة

بشكل افتراضي، لا يمكن للمستخدمين فتح الملفات الضارة التي تم اكتشافها بواسطة خزينة المرفقات SharePoint OneDrive Microsoft Teams أو نقلها أو نسخها أو مشاركتها<sup>\*</sup>. ومع ذلك، يمكنهم حذف الملفات الضارة وتنزيلها.

<sup>\*</sup> إذا انتقل المستخدمون إلى **"إدارة الوصول**"، فسيظل الخيار **"مشاركة"** متوفرا.

لمنع المستخدمين من تنزيل ملفات ضارة، [اتصل SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) وقم بتشغيل الأمر التالي:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**الملاحظات**:

- يؤثر هذا الإعداد على كل من المستخدمين والمسؤولين.
- لا يزال بإمكان الأشخاص حذف الملفات الضارة.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>الخطوة 3 (مستحسن) استخدم مدخل Microsoft 365 Defender لإنشاء نهج تنبيه للملفات المكتشفة

يمكنك إنشاء نهج تنبيه يعلمك أنت والمسؤولين الآخرين عند خزينة المرفقات SharePoint OneDrive Microsoft Teams الكشف عن ملف ضار. لمعرفة المزيد حول التنبيهات، راجع [نهج التنبيه](../../compliance/alert-policies.md).

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **نهج التنبيه** **لقواعد &** \> النهج. للانتقال مباشرة إلى صفحة **نهج التنبيه** ، استخدم <https://security.microsoft.com/alertpolicies>.

2. في صفحة **نهج التنبيه** ، انقر فوق **نهج تنبيه جديد**.

3. يفتح معالج **نهج التنبيه الجديد** منبثقا. في صفحة **"الاسم** " في التنبيه، قم بتكوين الإعدادات التالية:
   - **الاسم**: اكتب اسما فريدا ووصفيا. على سبيل المثال، الملفات الضارة في المكتبات.
   - **الوصف**: اكتب وصفا اختياريا. على سبيل المثال، إعلام المسؤولين عند اكتشاف ملفات ضارة في SharePoint Online أو OneDrive أو Microsoft Teams.
   - **الخطورة**: حدد **منخفضا** أو **متوسطا** أو **مرتفعا** من القائمة المنسدلة.
   - **الفئة**: حدد **إدارة المخاطر** من القائمة المنسدلة.

   عند الانتهاء، انقر فوق **"التالي**".

4. في صفحة **إنشاء إعدادات التنبيه** ، قم بتكوين الإعدادات التالية:
   - **ما الذي تريد التنبيه إليه؟** النشاط \> **هو** \> تحديد **البرامج الضارة المكتشفة في الملف** من القائمة المنسدلة.
   - **كيف تريد تشغيل التنبيه؟** القسم: اترك القيمة الافتراضية في **كل مرة يتطابق فيها النشاط مع القاعدة المحددة** .

   عند الانتهاء، انقر فوق **"التالي**".

5. في الصفحة **"تعيين المستلمين** "، قم بتكوين الإعدادات التالية:
   - تحقق من تحديد **إرسال إعلامات البريد الإلكتروني** . في المربع **"مستلمو البريد الإلكتروني** "، حدد مسؤولا عموميا واحدا أو أكثر أو مسؤولي أمان أو برامج قراءة الأمان التي يجب أن تتلقى إعلاما عند اكتشاف ملف ضار.
   - **حد الإعلام اليومي**: اترك القيمة الافتراضية **"بلا حد"** محددة.

   عند الانتهاء، انقر فوق **"التالي**".

6. في صفحة **مراجعة الإعدادات** ، راجع الإعدادات. يمكنك تحديد **"تحرير"** في كل مقطع لتعديل الإعدادات داخل المقطع. أو يمكنك النقر فوق **"الخلف"** أو تحديد الصفحة المحددة في المعالج.

   في القسم **"هل تريد تشغيل النهج على الفور"؟** اترك القيمة الافتراضية **"نعم"، وقم بتشغيلها مباشرة** .

   عند الانتهاء، انقر فوق **"إنهاء**".

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>استخدام Security & Compliance PowerShell لإنشاء نهج تنبيه للملفات المكتشفة

إذا كنت تفضل استخدام PowerShell لإنشاء نفس نهج التنبيه كما هو موضح في القسم السابق، [فتواصل مع Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) وقم بتشغيل الأمر التالي:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**ملاحظة**: قيمة _الخطورة_ الافتراضية منخفضة. لتحديد متوسط أو عال، قم بتضمين _معلمة الخطورة_ والقيمة في الأمر.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>كيف تعرف أن هذه الإجراءات تعمل؟

- للتحقق من تشغيل خزينة المرفقات بنجاح SharePoint OneDrive Microsoft Teams، استخدم أيا من الخطوات التالية:

  - في مدخل Microsoft 365 Defender، انتقل **إلى قسم** \> نهج نهج **المخاطر** \> **& النهج** \> **خزينة المرفقات**، وحدد **الإعدادات العمومية**، وتحقق من قيمة **Defender لـ Office 365 "تشغيل" SharePoint، إعداد OneDrive Microsoft Teams**.

  - في Exchange Online PowerShell، قم بتشغيل الأمر التالي للتحقق من إعداد الخاصية:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- للتحقق من حظر الأشخاص بنجاح من تنزيل ملفات ضارة، افتح SharePoint Online PowerShell، وقم بتشغيل الأمر التالي للتحقق من قيمة الخاصية:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- للتحقق من تكوين نهج تنبيه للملفات المكتشفة بنجاح، استخدم أيا من الخطوات التالية:
  - في مدخل Microsoft 365 Defender، انتقل إلى **نهج & نهج** \> **التنبيه** \> وحدد نهج التنبيه، وتحقق من الإعدادات.
  - في مدخل Microsoft 365 Defender PowerShell، استبدل \<AlertPolicyName\> باسم نهج التنبيه، وقم بتشغيل الأمر التالي، وتحقق من قيم الخصائص:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- استخدم [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report) لعرض معلومات حول الملفات المكتشفة في SharePoint OneDrive Microsoft Teams. على وجه التحديد، يمكنك استخدام **عرض البيانات بواسطة: طريقة عرض البرامج الضارة للمحتوى\>**.
