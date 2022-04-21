---
title: إعداد التدقيق (Premium) في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: تصف هذه المقالة كيفية إعداد التدقيق (Premium) حتى تتمكن من إجراء التحقيقات الجنائية عند اختراق حسابات المستخدمين أو التحقيق في الحوادث الأخرى المتعلقة بالأمان.
ms.openlocfilehash: 6f4f9953c88b1d994d4f033629cc89a6529fb9de
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998827"
---
# <a name="set-up-microsoft-purview-audit-premium"></a>إعداد تدقيق Microsoft Purview (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

إذا كان لدى مؤسستك اشتراك وترخيص المستخدم النهائي الذي يدعم التدقيق (Premium)، فنفذ الخطوات التالية لإعداد القدرات الإضافية واستخدامها في Audit (Premium).

![سير العمل لإعداد التدقيق (Premium).](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-audit-premium-for-users"></a>الخطوة 1: إعداد التدقيق (Premium) للمستخدمين

تتطلب ميزات التدقيق (Premium) مثل القدرة على تسجيل الأحداث الهامة مثل MailItemsAccessed و Send ترخيص E5 مناسبا تم تعيينه للمستخدمين. بالإضافة إلى ذلك، يجب تمكين تطبيق/خدمة التدقيق المتقدم لهؤلاء المستخدمين. للتحقق من تعيين تطبيق التدقيق المتقدم للمستخدمين، نفذ الخطوات التالية لكل مستخدم:

1. في مركز مسؤولي Microsoft 365، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**مستخدمي UsersActive**</a> > ، وحدد مستخدما.

2. في صفحة القائمة المنبثقة لخصائص المستخدم، انقر فوق **"التراخيص والتطبيقات**".

3. في قسم **"التراخيص** "، تحقق من تعيين ترخيص E5 للمستخدم أو أنه تم تعيين ترخيص وظيفة إضافية مناسب له. للحصول على قائمة بالتراخيص التي تدعم التدقيق (Premium)، راجع [متطلبات ترخيص التدقيق (Premium](auditing-solutions-overview.md#audit-premium-1)).

4. قم بتوسيع قسم **"التطبيقات**"، وتحقق من تحديد خانة الاختيار **"تدقيق متقدم" Microsoft 365**.

5. إذا لم يتم تحديد خانة الاختيار، فحددها، ثم انقر فوق **"حفظ التغييرات".**

   سيبدأ تسجيل سجلات التدقيق ل MailItemsAccessed و Send في غضون 24 ساعة. يجب تنفيذ الخطوة 3 لبدء تسجيل حدثين آخرين للتدقيق (Premium): SearchQueryInitiatedExchange و SearchQueryInitiatedSharePoint.

أيضا، إذا قمت بتخصيص إجراءات علبة البريد التي تم تسجيلها على علب بريد المستخدمين أو علب البريد المشتركة، فلن يتم تدقيق أي أحداث تدقيق (Premium) جديدة تم إصدارها بواسطة Microsoft تلقائيا على علب البريد هذه. للحصول على معلومات حول تغيير إجراءات علبة البريد التي يتم تدقيقها لكل نوع من أنواع تسجيل الدخول، راجع القسم "تغيير إجراءات علبة البريد المسجلة بشكل افتراضي أو استعادتها" في [إدارة تدقيق علبة البريد](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-audit-premium-events"></a>الخطوة 2: تمكين أحداث التدقيق (Premium)

يجب تمكين حدثين للتدقيق (Premium) (SearchQueryInitiatedExchange و SearchQueryInitiatedSharePoint) ليتم تسجيلهما عندما يقوم المستخدمون بإجراء عمليات بحث في Exchange Online SharePoint Online. لتمكين تدقيق هذين الحدثين للمستخدمين، قم بتشغيل الأمر التالي (لكل مستخدم) في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

في بيئة متعددة المناطق الجغرافية، يجب تشغيل الأمر السابق **"مجموعة علبة البريد"** في الغابة حيث توجد علبة بريد المستخدم. لتحديد موقع علبة بريد المستخدم، قم بتشغيل الأمر التالي: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

إذا كان الأمر الخاص بتمكين تدقيق استعلامات البحث قد تم تشغيله مسبقا في غابة مختلفة عن تلك الموجودة في علبة بريد المستخدم، فيجب إزالة قيمة SearchQueryInitiated من علبة بريد المستخدم عن طريق تشغيلها `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` ثم إضافتها إلى علبة بريد المستخدم في الغابة حيث توجد علبة بريد المستخدم.

## <a name="step-3-set-up-audit-retention-policies"></a>الخطوة 3: إعداد نهج استبقاء التدقيق

بالإضافة إلى النهج الافتراضي الذي يحتفظ بسجلات تدقيق Exchange SharePoint وAzure AD لمدة عام واحد، يمكنك إنشاء نهج استبقاء سجل تدقيق إضافية لتلبية متطلبات عمليات الأمان وفرق تكنولوجيا المعلومات والتوافق في مؤسستك. لمزيد من المعلومات، راجع [إدارة نهج استبقاء سجل التدقيق](audit-log-retention-policies.md).

## <a name="step-4-search-for-audit-premium-events"></a>الخطوة 4: البحث عن أحداث التدقيق (Premium)

الآن بعد أن تم إعداد التدقيق (Premium) لمؤسستك، يمكنك البحث عن أحداث التدقيق (Premium) الهامة والأنشطة الأخرى عند إجراء التحقيقات الجنائية. بعد الانتهاء من الخطوة 1 والخطوة 2، يمكنك البحث في سجل التدقيق عن أحداث التدقيق (Premium) والأنشطة الأخرى أثناء التحقيقات الجنائية للحسابات المخترقة وأنواع أخرى من تحقيقات الأمان أو الامتثال. لمزيد من المعلومات حول إجراء تحقيق الطب الشرعي لحسابات المستخدمين المخترقة باستخدام حدث تدقيق MailItemsAccessed (Premium)، راجع [استخدام التدقيق (Premium) للتحقيق في الحسابات المخترقة](mailitemsaccessed-forensics-investigations.md).
