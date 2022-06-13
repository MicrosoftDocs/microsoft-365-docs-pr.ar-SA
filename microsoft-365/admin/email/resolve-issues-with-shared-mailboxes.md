---
title: حل المشاكل المتعلقة لعلب البريد المشتركة
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: قد تحصل على أخطاء عند إعداد علب البريد المشتركة. جرب هذه الحلول إذا واجهت مشاكل في علب البريد المشتركة.
ms.openlocfilehash: 08b5bbaa1ea952ee2b9bb6c626328fdb6b91d71c
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008568"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>حل المشاكل المتعلقة لعلب البريد المشتركة

إذا رأيت رسائل خطأ عند إنشاء علبة بريد مشتركة أو استخدامها، فجرب هذه الحلول الممكنة. 

## <a name="error-when-creating-shared-mailboxes"></a>خطأ عند إنشاء علب بريد مشتركة

إذا رأيت رسالة الخطأ، **فإن عنوان الوكيل "smtp:<اسم\> علبة البريد المشتركة" قيد الاستخدام بالفعل من قبل عناوين الوكيل أو LegacyExchangeDN ل "\<name>". الرجاء اختيار عنوان وكيل آخر**، فهذا يعني أنك تحاول إعطاء علبة البريد المشتركة اسما قيد الاستخدام بالفعل. على سبيل المثال، لنفترض أنك تريد علب البريد المشتركة المسماة info@domain1 info@domain2. هناك طريقتان للقيام بذلك:

- استخدم Exchange Online PowerShell. راجع منشور المدونة هذا للحصول على إرشادات: [إنشاء علب بريد مشتركة بنفس الاسم المستعار في مجالات مختلفة](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)

- قم بتسمية علبة البريد المشتركة الثانية بشيء مختلف عن البداية للتغلب على الخطأ. ثم في مركز الإدارة، أعد تسمية علبة البريد المشتركة إلى ما تريد أن تكون عليه.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>خطأ في عدم وجود أذونات إرسال عند استخدام علبة بريد مشتركة

إذا قمت بإنشاء علبة بريد مشتركة ثم حاولت إرسال رسالة منها، فقد تحصل على ما يلي:

**تعذر إرسال هذه الرسالة. ليس لديك الإذن لإرسال الرسالة نيابة عن المستخدم المحدد.**

تظهر هذه الرسالة عندما يواجه Microsoft 365 مشكلة في زمن انتقال النسخ المتماثل. يجب أن تزول في غضون ساعة أو نحو ذلك، عندما يتم نسخ المعلومات حول علبة البريد المشتركة الجديدة (أو المستخدم المضاف) عبر جميع مراكز البيانات الخاصة بنا. انتظر ساعة ثم حاول مرة أخرى لإرسال رسالة.

## <a name="related-content"></a>المحتويات ذات الصلة

[حول علب البريد المشتركة](about-shared-mailboxes.md) (مقالة)\
[إنشاء علبة بريد مشتركة](create-a-shared-mailbox.md) (مقالة)\
[تكوين علبة بريد مشتركة](configure-a-shared-mailbox.md) (مقالة)\
[تحويل علبة بريد مستخدم إلى علبة بريد مشتركة](convert-user-mailbox-to-shared-mailbox.md) (مقالة)\
[إزالة ترخيص من علبة بريد مشتركة](remove-license-from-shared-mailbox.md) (مقالة)
