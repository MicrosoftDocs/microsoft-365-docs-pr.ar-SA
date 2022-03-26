---
title: إزالة ترخيص من علبة البريد المشتركة
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
ms.date: 05/11/2021
ms.openlocfilehash: 6de6f213cc0df7a216122d55ef07e270586aea12
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568176"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>إزالة ترخيص من علبة بريد مشتركة

لا تتطلب علب البريد المشتركة عادة ترخيصا. اتبع هذه الإرشادات لإزالة ترخيص من علبة بريد مشتركة بحيث يمكنك إما تعيينه إلى مستخدم أو إرجاع الترخيص بحيث لا تدفع مقابل ترخيص لا تحتاج إليه.

> [!NOTE]
>
> يلزم Exchange Online الخطة 2 في السيناريوهات التالية:
>
> - علبة البريد المشتركة لديها أكثر من 50 غيغابايت من مساحة التخزين في الاستخدام.
> - تستخدم علبة البريد المشتركة الأرشفة في مكانها.
> - يتم وضع علبة البريد المشتركة قيد الاحتجاز بسبب الدعاوى القضائية.
> - تم تعيين Microsoft 365 Defender بريد مشترك.
> 
> للحصول على إرشادات مفصلة خطوة بخطوة حول كيفية تعيين التراخيص، راجع [تعيين التراخيص للمستخدمين](/microsoft-365/admin/manage/assign-licenses-to-users). 


## <a name="remove-the-license"></a>إزالة الترخيص

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">النشطون</a> .

::: moniker-end

::: moniker range="o365-21vianet"

 1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">النشطون</a> .

::: moniker-end

   > [!NOTE]
   > تحتاج إلى إزالة الترخيص من صفحة المستخدمون النشطون. لا يمكنك إزالة الترخيص من صفحة علبة البريد المشتركة لأن التراخيص هي إعدادات المستخدم.
  
2. حدد علبة البريد المشتركة.

3. إحدى علامات **التبويب التراخيص والتطبيقات****، قم بتوسيع** التراخيص وأزل تحديد المربع الخاص بالترخيص الذي تريد إزالته.

4. حدد **حفظ التغييرات**.

5. عندما تعود إلى صفحة المستخدمون **النشطون** ، ستكون حالة علبة البريد المشتركة **غير مرخصة**.

6. ما زلت تدفع مقابل الترخيص. للتوقف عن الدفع، [قم بإزالة الترخيص من اشتراكك](../../commerce/licenses/buy-licenses.md).

## <a name="related-content"></a>المحتوى ذي الصلة

[حول علب البريد المشتركة](about-shared-mailboxes.md) (مقالة)\
[إنشاء علبة بريد مشتركة](create-a-shared-mailbox.md) (مقالة)\
[تكوين علبة بريد مشتركة](configure-a-shared-mailbox.md) (مقالة)\
[تحويل علبة بريد مستخدم إلى علبة بريد مشتركة](convert-user-mailbox-to-shared-mailbox.md) (مقالة)\
[حل المشاكل المتعلقة لعلب البريد المشتركة](resolve-issues-with-shared-mailboxes.md) (مقالة)
