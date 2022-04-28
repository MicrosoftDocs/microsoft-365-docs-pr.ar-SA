---
title: إزالة الترخيص من علبة البريد المشتركة
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
ms.reviewer: sinakassaw, nicholak
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
- commerce_licensing
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: 'قم بإزالة ترخيص من علبة بريد مشتركة لتعيينه إلى مستخدم آخر أو إرجاع الترخيص حتى لا تدفع ثمنه. '
ms.date: 04/22/2022
ms.openlocfilehash: 4445163281e403505612066285192b31adc44979
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091908"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>إزالة ترخيص من علبة بريد مشتركة

لا تتطلب علب البريد المشتركة عادة ترخيصا. اتبع هذه الإرشادات لإزالة ترخيص من علبة بريد مشتركة بحيث يمكنك إما تعيينه إلى مستخدم أو إرجاع الترخيص بحيث لا تدفع مقابل ترخيص لا تحتاج إليه.

> [!NOTE]
>
> مطلوب ترخيص Exchange Online الخطة 2 في السيناريوهات التالية:
>
> - تحتوي علبة البريد المشتركة على أكثر من 50 غيغابايت من مساحة التخزين المستخدمة.
> - تستخدم علبة البريد المشتركة الأرشفة الموضعية.
> - يتم وضع علبة البريد المشتركة في احتجاز التقاضي.
> - تحتوي علبة البريد المشتركة على ترخيص Microsoft 365 Defender معين.
> 
> للحصول على إرشادات مفصلة خطوة بخطوة حول كيفية تعيين التراخيص، راجع [تعيين التراخيص للمستخدمين](/microsoft-365/admin/manage/assign-licenses-to-users). 


## <a name="remove-the-license"></a>إزالة الترخيص

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

 1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank"></a>

::: moniker-end

   > [!NOTE]
   > تحتاج إلى إزالة الترخيص من صفحة "المستخدمون النشطون". لا يمكنك إزالة الترخيص من صفحة علبة البريد المشتركة لأن التراخيص هي إعدادات المستخدم.
  
2. حدد علبة البريد المشتركة.

3. ضمن علامة التبويب **"التراخيص والتطبيقات** "، قم بتوسيع **"التراخيص** " وقم بإلغاء تحديد المربع الخاص بالترخيص الذي تريد إزالته.

4. حدد **"حفظ التغييرات**".

5. عند العودة إلى صفحة **"المستخدمون النشطون** "، ستكون حالة علبة البريد المشتركة **غير مرخصة**.

6. لا تزال تدفع مقابل الترخيص. لإيقاف الدفع، [قم بإزالة الترخيص من اشتراكك](../../commerce/licenses/buy-licenses.md).

## <a name="related-content"></a>المحتويات ذات الصلة

[حول علب البريد المشتركة](about-shared-mailboxes.md) (مقالة)\
[إنشاء علبة بريد مشتركة](create-a-shared-mailbox.md) (مقالة)\
[تكوين علبة بريد مشتركة](configure-a-shared-mailbox.md) (مقالة)\
[تحويل علبة بريد مستخدم إلى علبة بريد مشتركة](convert-user-mailbox-to-shared-mailbox.md) (مقالة)\
[حل المشاكل المتعلقة بعلب البريد المشتركة](resolve-issues-with-shared-mailboxes.md) (مقالة)
