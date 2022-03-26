---
title: خزينة المستندات في Microsoft Defender Office 365
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: تعرف على خزينة المستندات في Microsoft 365 E5/A5 أو Microsoft 365 E5/A5.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: beb34c04f93fe853678b30bcd9b5f7a621f4666b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63566160"
---
# <a name="safe-documents-in-microsoft-365-e5a5"></a>خزينة المستندات في Microsoft 365 E5/A5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

خزينة المستندات هي ميزة متميزة تستخدم الواجهة الخلفية السحابية ل [Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) لمسح مستندات Office في "طريقة عرض محمية" أو "[حماية](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46) التطبيقات" [](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) Office.

لا يحتاج المستخدمون إلى تثبيت Defender for Endpoint على أجهزتهم المحلية خزينة حماية المستندات. يحصل المستخدمون خزينة حماية المستندات إذا تم تلبية كل المتطلبات التالية:

- خزينة المستندات في المؤسسة كما هو موضح في هذه المقالة.
- يتم تعيين التراخيص من خطة ترخيص مطلوبة إلى المستخدمين. خزينة يتم التحكم في مستندات **Office 365 SafeDocs** (أو **SAFEDOCS** أو **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (المعروفة أيضا بالخدمة). تتوفر خطة الخدمة هذه في خطط الترخيص التالية (المعروفة أيضا بخطط الترخيص أو Microsoft 365 أو المنتجات):
  - Microsoft 365 A5 الكلية
  - Microsoft 365 A5 للطلاب
  - Microsoft 365 E5
  - الأمان في Microsoft 365 E5

  خزينة المستندات غير مضمنة في Microsoft Defender Office 365 الترخيص.

  لمزيد من المعلومات، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- يستخدمون الإصدار Microsoft 365 Apps for enterprise 2004 أو إصدار أحدث (المعروف سابقا باسم Office 365 ProPlus).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- تحتاج إلى أذونات في **Exchange Online** قبل أن تتمكن من تنفيذ الإجراءات في هذه المقالة:
  - لتكوين إعدادات خزينة المستندات، يجب أن تكون عضوا في مجموعات دور مسؤول إدارة **المؤسسة أو مسؤول** الأمان.
  - للوصول للقراءة فقط إلى خزينة المستندات، يجب أن تكون عضوا في مجموعات دور القارئ العام أو قارئ الأمان. 

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 للمستخدمين الأذونات والأذونات المطلوبة للميزات الأخرى  في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  >
  > - توفر **أيضا مجموعة دور "** إدارة [المؤسسات Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) طريقة العرض فقط" إمكانية الوصول للقراءة فقط إلى الميزة.

### <a name="how-does-microsoft-handle-your-data"></a>كيف تتعامل Microsoft مع بياناتك؟

للحفاظ على حمايتك، خزينة المستندات الملفات إلى [سحابة Microsoft Defender لنقطة](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) النهاية لتحليلها. يمكنك العثور على تفاصيل حول كيفية تعامل Microsoft Defender for Endpoint مع بياناتك هنا: [Microsoft Defender لتخزين بيانات نقطة النهاية والخصوصية](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

لا يتم الاحتفاظ بالملفات خزينة المستندات في Defender for Endpoint بعد الوقت المطلوب للتحليل (عادة ما يكون أقل من 24 ساعة).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>استخدام مدخل Microsoft 365 Defender لتكوين خزينة المستندات

1. في مدخل Microsoft 365 Defender،  \>  \>  \> <https://security.microsoft.com>انتقل إلى & البريد الإلكتروني ونهج التعاون & القواعد خزينة **المرفقات** في **القسم** "سياسات". الانتقال مباشرة إلى صفحة المرفقات خزينة **،** استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، انقر فوق **إعدادات عام**.

3. في قائمة **الإعدادات "** عام" التي تظهر، قم بتكوين الإعدادات التالية:
   - **قم خزينة المستندات** الخاصة Office العملاء: قم بنقل تبديل إلى اليمين ل تشغيل الميزة: ![تشغيل.](../../media/scc-toggle-on.png).
   - السماح للأشخاص بالنقر عبر "طريقة عرض **محمية**" حتى لو حددت خزينة المستندات الملف على أنه ضار: نوصي بترك هذا الخيار م إيقاف التشغيل (اترك زر تبديل إلى اليمين: ![إيقاف التشغيل.](../../media/scc-toggle-off.png)).

   عند الانتهاء، انقر فوق **حفظ**.

   ![خزينة إعدادات المستندات بعد تحديد الإعدادات "عام" على خزينة المرفقات.](../../media/safe-docs-global-settings.png)

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>استخدام Exchange Online PowerShell لتكوين خزينة المستندات

إذا كنت تفضل استخدام PowerShell لتكوين خزينة المستندات، فاستخدم بناء الجملة التالي في Exchange Online PowerShell:

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- تمكن _المعلمة EnableSafeDocs_ خزينة المستندات الخاصة ب المؤسسة بكاملها أو تعطلها.
- تسمح _المعلمة AllowSafeDocsOpen_ أو تمنع المستخدمين من مغادرة "طريقة عرض محمية" (أي فتح المستند) إذا تم تعريف المستند على أنه ضار.

يمكن هذا المثال خزينة المستندات الخاصة ب المؤسسة بكاملها، ويمنع المستخدمين من فتح المستندات التي تم تعريفها كضارة من "طريقة عرض محمية".

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>تكوين الوصول الفردي إلى خزينة المستندات

إذا كنت تريد السماح أو حظر الوصول إلى ميزة خزينة المستندات بشكل انتقائي، فاتبع الخطوات التالية:

1. قم خزينة المستندات في Microsoft 365 Defender أو Exchange Online PowerShell كما هو موضح سابقا في هذه المقالة.
2. استخدم Azure AD PowerShell لتعطيل خزينة لمستخدمين معينين كما هو موضح في تعطيل خدمات Microsoft 365 معينة لمستخدمين معينين [لخطة ترخيص معينة](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  اسم خطة الخدمة التي يجب تعطيلها في PowerShell هو **SAFEDOCS**.

لمزيد من المعلومات، راجع المواضيع التالية:

- [عرض Microsoft 365 والخدمات باستخدام PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [عرض Microsoft 365 تفاصيل الخدمة وترخيص الحساب باستخدام PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [أسماء المنتجات ومعرفات خطط الخدمة للترخيص](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>التمكن من الوصول إلى خدمة Microsoft Defender for Endpoint لتمكين إمكانات التدقيق

لتمكين إمكانات التدقيق، يجب أن يكون Microsoft Defender ل Endpoint مثبتا على الجهاز المحلي. لنشر Microsoft Defender لنقطة النهاية، تحتاج إلى الانتقال إلى مختلف مراحل النشر. بعد التهيئة، يمكنك تكوين قدرات التدقيق في Microsoft 365 Defender المدخل.

لمعرفة المزيد، راجع [Onboard إلى خدمة Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/onboarding). إذا كنت بحاجة إلى مساعدة إضافية، يمكنك الرجوع إلى استكشاف مشاكل [تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>كيف أتأكد من نجاح هذا الأمر؟

للتحقق من تمكين المستندات وتكوينها خزينة، قم بأي من الخطوات التالية:

- في مدخل Microsoft 365 Defender، انتقل إلى سياسات التعاون في البريد الإلكتروني  **&** \> **&** \>  \> قواعد المخاطر **خزينة** \> المرفقات في قسم "السياسات" الإعدادات العامة، وتحقق من تشغيل مستندات خزينة لعملاء **Office** و **السماح للأشخاص بالنقر عبر "طريقة عرض محمية" حتى خزينة المستندات تعرف الملف على أنه إعدادات ضارة**.

- تشغيل الأمر التالي في Exchange Online PowerShell والتحقق من قيم الخاصية:

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- تتوفر الملفات التالية لاختبار خزينة المستندات. تشبه هذه الملفات ملف EICAR.TXT لاختبار حلول مكافحة البرامج الضارة وفيروسات. الملفات ليست ضارة، ولكنها ستشغل خزينة حماية المستندات.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
