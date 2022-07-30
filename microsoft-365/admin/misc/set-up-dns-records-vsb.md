---
title: توصيل مجالك بـ Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
search.appverid:
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: تعرف على كيفية التحقق من مجالك وإنشاء سجلات DNS باستخدام Microsoft 365.
ms.custom:
- VSBFY23
- AdminSurgePortfolio
ms.openlocfilehash: d4c2ee05b90ed890b9a1630d6e0911b6cab34cdd
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67085104"
---
# <a name="connect-your-domain-to-microsoft-365"></a>توصيل مجالك بـ Microsoft 365

> [!NOTE]
> إذا لم تقم بإضافة مجال، فسيستخدم الأشخاص في مؤسستك المجال onmicrosoft.com لعناوين بريدهم الإلكتروني حتى تقوم بذلك. من المهم إضافة مجالك قبل إضافة مستخدمين، حتى لا تضطر إلى إعدادهم مرتين.

[راجع الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml) إذا تعذر عليك العثور على ما تبحث عنه بالأسفل.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX حتى يصل البريد الإلكتروني لمجالك إلى Microsoft

ستحصل على معلومات لسجل MX من معالج إعداد مجال مركز المسؤولين.

على موقع ويب موفر الاستضافة الخاص بك، أضف سجل MX جديد.
تأكد من تعيين الحقول إلى القيم التالية:

- نوع السجل: `MX`
- الأولوية: تعيين إلى أعلى قيمة متوفرة، عادة تكون `0`.
- اسم المضيف: `@`
- يشير إلى العنوان: انسخ القيمة من مركز المسؤولين والصقها هنا.
- TTL: `3600` (أو الموفر الافتراضي الخاص بك)

احفظ السجل، ثم قم بإزالة أي سجلات MX أخرى.

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a>إضافة سجل CNAME لتوصيل المستخدمين بعلب البريد الخاصة بهم

ستحصل على معلومات لسجلات CNAME من معالج إعداد مجال مركز المسؤولين.

على موقع موفر الاستضافة على الويب، أضف سجل CNAME التالي. تأكد من تعيين الحقول إلى القيم التالية لكل منها:

- نوع السجل: `CNAME (Alias)`
- المضيف: قم بلصق القيم التي نسختها من مركز المسؤولين هنا.
- يشير إلى العنوان: انسخ القيمة من مركز المسؤولين والصقها هنا.
- TTL: `3600` (أو الموفر الافتراضي الخاص بك)

## <a name="add-a-txt-record-to-help-prevent-spam"></a>إضافة سجل TXT للمساعدة في منع البريد العشوائي

**قبل أن تبدأ:** إذا كان لديك بالفعل سجل SPF لمجالك، فلا تنشئ واحداً جديداً لـ Microsoft 365. بدلا من ذلك، أضف قيم Microsoft 365 المطلوبة إلى السجل الحالي على موقع ويب موفري الاستضافة بحيث يكون لديك سجل SPF *واحد* يتضمن كلاً من مجموعتي القيم.

على موقع ويب موفّر الاستضافة الخاص بك، قم بتحرير سجل SPF الموجود أو قم بإنشاء سجل SPF.
تأكد من تعيين الحقول إلى القيم التالية:

- نوع السجل: `TXT (Text)`
- المضيف: `@`
- قيمة TXT: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (أو الموفر الافتراضي الخاص بك)

حفظ السجل.

قم بالتحقق من صحة سجل SPF باستخدام أحد [أدوات التحقق من صحة SPF](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain).

تم تصميم SPF للمساعدة على منع تزييف الهوية، ولكن هناك أساليب لتزييف الهوية لا يستطيع SPF الحماية منها. لكي تتمكن من الحماية ضد تلك الأساليب، بمجرد إعداد SPF، ينبغي أيضاً إعداد بريد معرّف بمفاتيح المجال وDMARC لـ Office 365.

للبدء، راجع [استخدام بريد معرّف بمفاتيح المجال للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك في Microsoft 365](../../security/office-365-security/use-dkim-to-validate-outbound-email.md)و[استخدم DMARC للتحقق من صحة البريد الإلكتروني في Microsoft 365](../../security/office-365-security/use-dmarc-to-validate-email.md).

وأخيرا، عد إلى معالج إعداد مجال مركز الإدارة لإكمال الإعداد.
