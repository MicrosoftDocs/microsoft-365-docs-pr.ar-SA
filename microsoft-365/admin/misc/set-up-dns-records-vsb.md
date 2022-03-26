---
title: الاتصال مجالك Microsoft 365
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
- AdminSurgePortfolio
ms.openlocfilehash: 3aa43cd798c26dde8eb064754ae3fb74bd520c29
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569093"
---
# <a name="connect-your-domain-to-microsoft-365"></a>الاتصال مجالك Microsoft 365

> [!NOTE]
> إذا لم تضيف مجالا، سيستخدم الأشخاص في مؤسستك المجال onmicrosoft.com عناوين بريدهم الإلكتروني حتى تقوم بذلك. من المهم إضافة مجالك قبل إضافة المستخدمين، بحيث لا تحتاج إلى إعدادهم مرتين.

[تحقق من الأسئلة الشائعة حول](../setup/domains-faq.yml) المجالات إذا لم تعثر على ما تبحث عنه أدناه.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>إضافة سجل MX بحيث يتم إرسال البريد الإلكتروني لمجالك إلى Microsoft

ستحصل على معلومات سجل MX من معالج إعداد مجال مركز الإدارة.

على موقع موفر الاستضافة على الويب، أضف سجل MX جديدا.
تأكد من تعيين الحقول إلى القيم التالية:

- نوع السجل: `MX`
- الأولوية: تعيين إلى أعلى قيمة متوفرة، عادة `0`.
- اسم المضيف: `@`
- يشير إلى العنوان: نسخ القيمة من مركز الإدارة ولصقها هنا.
- TTL: `3600` (أو الموفر الافتراضي)

احفظ السجل، ثم قم بإزالة أي سجلات MX أخرى.

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a>إضافة سجل CNAME لتوصيل المستخدمين لعلب البريد الخاصة بهم

ستحصل على معلومات سجلات CNAME من معالج إعداد مجال مركز الإدارة.

على موقع موفر الاستضافة على الويب، أضف سجل CNAME التالي. تأكد من تعيين الحقول إلى القيم التالية لكل منها:

- نوع السجل: `CNAME (Alias)`
- المضيف: لصق القيم التي نسختها من مركز الإدارة هنا.
- يشير إلى العنوان: نسخ القيمة من مركز الإدارة ولصقها هنا.
- TTL: `3600` (أو الموفر الافتراضي)

## <a name="add-a-txt-record-to-help-prevent-spam"></a>إضافة سجل TXT للمساعدة في منع البريد العشوائي

**قبل البدء:** إذا كان لديك سجل SPF لمجالك، فلا تنشئ سجلا جديدا لمجالك Microsoft 365. بدلا من ذلك، أضف Microsoft 365 المطلوبة إلى السجل الحالي على موقع موفري الاستضافة على ويب بحيث يكون لديك *سجل SPF* واحد يتضمن مجموعتي القيم.

على موقع موفر الاستضافة على الويب، قم بتحرير سجل SPF الموجود أو قم بإنشاء سجل SPF.
تأكد من تعيين الحقول إلى القيم التالية:

- نوع السجل: `TXT (Text)`
- المضيف: `@`
- قيمة TXT: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (أو الموفر الافتراضي)

احفظ السجل.

التحقق من صحة سجل SPF باستخدام إحدى أدوات التحقق من [صحة SPF هذه](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

تم تصميم SPF للمساعدة في منع ال انتحال، ولكن هناك أساليب انتحال لا يمكن ل SPF حمايتها. للحماية من هذه، بمجرد إعداد SPF، يجب عليك أيضا إعداد DKIM و DMARC Microsoft 365.

للبدء، راجع استخدام [DKIM](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك في Microsoft 365 واستخدام [DMARC](../../security/office-365-security/use-dmarc-to-validate-email.md) للتحقق من صحة البريد الإلكتروني في Microsoft 365.

وأخيرا، ارجع إلى معالج إعداد مجال مركز الإدارة لإكمال عملية الإعداد.
