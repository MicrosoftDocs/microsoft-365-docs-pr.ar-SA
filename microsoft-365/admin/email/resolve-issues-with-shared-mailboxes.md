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
ms.openlocfilehash: 2be12810e6651da5b062afbd0a3437913b9a4d60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568366"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>حل المشاكل المتعلقة لعلب البريد المشتركة

إذا رأيت رسائل خطأ عند إنشاء علبة بريد مشتركة أو استخدامها، فجرب هذه الحلول الممكنة. 

## <a name="error-when-creating-shared-mailboxes"></a>خطأ عند إنشاء علب بريد مشتركة
<a name="bkmk_Fix"> </a>

إذا رأيت رسالة الخطأ، يتم استخدام عنوان الوكيل **"smtp:<اسم\> علبة البريد المشتركة" بالفعل بواسطة عناوين الوكيل أو LegacyExchangeDN ل "\<name>". الرجاء اختيار عنوان وكيل آخر**، وهذا يعني أنك تحاول تسمية علبة البريد المشتركة باسم يستخدم بالفعل. على سبيل المثال، لنقول أنك تريد تسمية علب البريد المشتركة info@domain1 info@domain2. هناك طريقتان للقيام بذلك:

  - استخدم Windows PowerShell. راجع منشور المدونة هذا للحصول على إرشادات: [إنشاء علب بريد مشتركة بنفس الاسم المستعار في مجالات مختلفة](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)
    
  - يمكنك تسمية علبة البريد المشتركة الثانية بطريقة مختلفة عن البداية للعبث بالخطأ. ثم في مركز الإدارة، أعد تسمية علبة البريد المشتركة إلى ما تريد أن تكون عليه.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>خطأ حول عدم وجود أذونات إرسال عند استخدام علبة بريد مشتركة

إذا قمت بإنشاء علبة بريد مشتركة ثم حاولت إرسال رسالة منها، فقد تحصل على ما يلي:

**لا يمكن إرسال هذه الرسالة. ليس لديك الإذن لإرسال الرسالة نيابة عن المستخدم المحدد.**

تظهر هذه الرسالة عندما Microsoft 365 تواجه مشكلة في زمن التكرار. يجب أن تزول بعد ساعة أو نحو ذلك، عندما يتم نسخ المعلومات حول علبة البريد المشتركة الجديدة (أو المستخدم المضاف) عبر كل مراكز البيانات لدينا. انتظر لمدة ساعة ثم حاول مرة أخرى إرسال رسالة.

## <a name="related-content"></a>المحتوى ذي الصلة

[حول علب البريد المشتركة](about-shared-mailboxes.md) (مقالة)\
[إنشاء علبة بريد مشتركة](create-a-shared-mailbox.md) (مقالة)\
[تكوين علبة بريد مشتركة](configure-a-shared-mailbox.md) (مقالة)\
[تحويل علبة بريد مستخدم إلى علبة بريد مشتركة](convert-user-mailbox-to-shared-mailbox.md) (مقالة)\
[إزالة ترخيص من علبة بريد مشتركة](remove-license-from-shared-mailbox.md) (مقالة)


    

