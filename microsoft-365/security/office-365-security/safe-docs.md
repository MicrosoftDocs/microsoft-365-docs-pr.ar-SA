---
title: خزينة المستندات في Microsoft Defender لـ Office 365
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
description: تعرف على خزينة المستندات في Microsoft 365 A5 أو أمان E5.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e9e83ec902ec3beafff76e26fff3ce13d0a9b9a
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535515"
---
# <a name="safe-documents-in-microsoft-365-a5-or-e5-security"></a>خزينة المستندات في Microsoft 365 A5 أو أمان E5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

خزينة Documents هي ميزة متميزة تستخدم الخلفية السحابية [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) لفحص المستندات المفتوحة Office في ["طريقة عرض محمية"](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) أو ["حماية التطبيقات" للحصول على Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

لا يحتاج المستخدمون إلى تثبيت Defender لنقطة النهاية على أجهزتهم المحلية للحصول على حماية خزينة المستندات. يحصل المستخدمون على خزينة حماية المستندات إذا تم استيفاء جميع المتطلبات التالية:

- تم تمكين خزينة المستندات في المؤسسة كما هو موضح في هذه المقالة.
- يتم تعيين التراخيص من خطة ترخيص مطلوبة للمستخدمين. يتم التحكم في خزينة المستندات بواسطة **خطة خدمة SafeDocs Office 365** (أو **SAFEDOCS** أو **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (المعروفة أيضا باسم الخدمة). تتوفر خطة الخدمة هذه في خطط الترخيص التالية (المعروفة أيضا بخطط الترخيص أو خطط Microsoft 365 أو المنتجات):
  - Microsoft 365 A5 لهيئة التدريس
  - Microsoft 365 A5 للطلاب
  - الأمان في Microsoft 365 E5

  خزينة المستندات غير مضمنة في خطط الترخيص Microsoft Defender لـ Office 365.

  لمزيد من المعلومات، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- يستخدمون إصدار 2004 أو إصدار أحدث من Microsoft 365 Apps for enterprise (المعروف سابقا باسم Office 365 ProPlus).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- تحتاج إلى أذونات في **Exchange Online** قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لتكوين إعدادات خزينة المستندات، يجب أن تكون عضوا في مجموعات دور مسؤول **الأمان** أو **إدارة المؤسسة**.
  - للوصول للقراءة فقط إلى إعدادات خزينة المستندات، يجب أن تكون عضوا في مجموعات أدوار **"القارئ العمومي**" أو **"قارئ الأمان**".

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات _والأذونات_ المطلوبة للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  >
  > - كما توفر مجموعة دور **إدارة المؤسسة للعرض فقط** في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) إمكانية الوصول للقراءة فقط إلى الميزة.

### <a name="how-does-microsoft-handle-your-data"></a>كيف تتعامل Microsoft مع بياناتك؟

للمحافظة على حمايتك، خزينة ترسل المستندات الملفات إلى [سحابة Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) للتحليل. يمكن العثور هنا على تفاصيل حول كيفية معالجة Microsoft Defender لنقطة النهاية لبياناتك: [Microsoft Defender لنقطة النهاية تخزين البيانات والخصوصية](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

لا يتم الاحتفاظ بالملفات المرسلة بواسطة خزينة المستندات في Defender لنقطة النهاية بعد الوقت اللازم للتحليل (عادة أقل من 24 ساعة).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>استخدام مدخل Microsoft 365 Defender لتكوين مستندات خزينة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج تعاون** \> & البريد الإلكتروني **" & "قواعد** \> \> **التهديد**" **خزينة المرفقات** في قسم **"النهج**". للانتقال مباشرة إلى صفحة **المرفقات خزينة**، استخدم <https://security.microsoft.com/safeattachmentv2>.

2. في صفحة **خزينة المرفقات**، انقر فوق **الإعدادات العمومية**.

3. في **الإعدادات العمومية** المنبثقة التي تظهر، قم بتكوين الإعدادات التالية:
   - **تشغيل خزينة المستندات لعملاء Office**: انقل التبديل إلى اليمين لتشغيل الميزة: ![تشغيل.](../../media/scc-toggle-on.png)
   - **اسمح للأشخاص بالنقر عبر "طريقة عرض محمية" حتى إذا حددت المستندات خزينة الملف على أنه ضار**: نوصي بترك هذا الخيار متوقفا عن التشغيل (اترك زر التبديل إلى اليسار: ![إيقاف التشغيل.](../../media/scc-toggle-off.png)).

   عند الانتهاء، انقر فوق **حفظ**.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="إعدادات خزينة المستندات بعد تحديد الإعدادات العمومية في صفحة المرفقات خزينة" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>استخدام Exchange Online PowerShell لتكوين مستندات خزينة

إذا كنت تفضل استخدام PowerShell لتكوين مستندات خزينة، فاستخدم بناء الجملة التالي في Exchange Online PowerShell:

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- تمكن المعلمة _EnableSafeDocs_ خزينة Documents للمؤسسة بأكملها أو تعطلها.
- تسمح المعلمة _AllowSafeDocsOpen_ أو تمنع المستخدمين من مغادرة "طريقة العرض المحمية" (أي فتح المستند) إذا تم تعريف المستند على أنه ضار.

يمكن هذا المثال خزينة المستندات للمؤسسة بأكملها، ويمنع المستخدمين من فتح المستندات التي تم تعريفها على أنها ضارة من "طريقة عرض محمية".

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>تكوين الوصول الفردي إلى مستندات خزينة

إذا كنت تريد السماح بالوصول إلى ميزة مستندات خزينة أو حظرها بشكل انتقائي، فاتبع الخطوات التالية:

1. قم بتشغيل خزينة المستندات في مدخل Microsoft 365 Defender أو Exchange Online PowerShell كما هو موضح سابقا في هذه المقالة.
2. استخدم Azure AD PowerShell لتعطيل مستندات خزينة لمستخدمين محددين كما هو موضح في [تعطيل خدمات Microsoft 365 معينة لمستخدمين محددين لخطة ترخيص معينة](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  اسم خطة الخدمة التي يجب تعطيلها في PowerShell هو **SAFEDOCS**.

لمزيد من المعلومات، راجع المواضيع التالية:

- [عرض Microsoft 365 التراخيص والخدمات باستخدام PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [عرض ترخيص حساب Microsoft 365 وتفاصيل الخدمة باستخدام PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>إلحاق بخدمة Microsoft Defender لنقطة النهاية لتمكين قدرات التدقيق

لتمكين قدرات التدقيق، يحتاج الجهاز المحلي إلى تثبيت Microsoft Defender لنقطة النهاية. لنشر Microsoft Defender لنقطة النهاية، تحتاج إلى الانتقال إلى مراحل مختلفة من النشر. بعد الإلحاق، يمكنك تكوين قدرات التدقيق في مدخل Microsoft 365 Defender.

لمعرفة المزيد، راجع [إلحاق خدمة Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/onboarding). إذا كنت بحاجة إلى تعليمات إضافية، فراجع [استكشاف أخطاء Microsoft Defender لنقطة النهاية مشاكل الإلحاق وإصلاحها](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>كيف أتأكد من نجاح هذا الأمر؟

للتحقق من قيامك بتمكين خزينة المستندات وتكوينها، قم بأي من الخطوات التالية:

- في مدخل Microsoft 365 Defender،  انتقل إلى "نهج التعاون \> **& البريد الإلكتروني****" & "قواعد** \> \> **التهديد**" **خزينة المرفقات** في **الإعدادات العمومية** لمقطع \> "النهج"، وتحقق من **تشغيل "مستندات خزينة" لعملاء Office** **اسمح للأشخاص بالنقر عبر "طريقة عرض محمية" حتى لو كانت خزينة "المستندات" تعرف الملف كإعدادات ضارة**.

- تشغيل الأمر التالي في Exchange Online PowerShell والتحقق من قيم الخصائص:

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- تتوفر الملفات التالية لاختبار حماية المستندات خزينة. تشبه هذه الملفات ملف EICAR.TXT لاختبار حلول مكافحة البرامج الضارة ومكافحة الفيروسات. الملفات ليست ضارة، ولكن سيتم تشغيلها خزينة حماية المستندات.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
