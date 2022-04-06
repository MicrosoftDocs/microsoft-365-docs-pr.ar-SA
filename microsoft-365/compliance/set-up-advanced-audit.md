---
title: إعداد التدقيق المتقدم في Microsoft 365
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
description: تصف هذه المقالة كيفية إعداد التدقيق المتقدم لكي تتمكن من إجراء عمليات التحقيق في الطب الشرعي عند اختراق حسابات المستخدمين أو التحقيق في أحداث أخرى ذات صلة بالامن.
ms.openlocfilehash: 34ae98eaafcc3eeb3d6a25a457f017999b8c6078
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63583284"
---
# <a name="set-up-advanced-audit-in-microsoft-365"></a>إعداد التدقيق المتقدم في Microsoft 365

إذا كانت مؤسستك لديها اشتراك وترخيص مستخدم يدعم التدقيق المتقدم، فاتبع الخطوات التالية لإعداد الإمكانيات الإضافية واستخدامها في التدقيق المتقدم.

![سير العمل لإعداد التدقيق المتقدم.](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-advanced-audit-for-users"></a>الخطوة 1: إعداد التدقيق المتقدم للمستخدمين

تتطلب ميزات التدقيق المتقدمة مثل القدرة على تسجيل الأحداث المهمة مثل MailItemsAccessed وSed send ترخيص E5 مناسب تم تعيينه للمستخدمين. بالإضافة إلى ذلك، يجب تمكين خطة الخدمة/تطبيق التدقيق المتقدم لهؤلاء المستخدمين. للتحقق من تعيين تطبيق التدقيق المتقدم للمستخدمين، قم بتنفيذ الخطوات التالية لكل مستخدم:

1. في مركز مسؤولي Microsoft 365، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive**</a> >  users (المستخدمون النشطة) وحدد مستخدما.

2. في صفحة منتحل معلومات خصائص المستخدم، انقر فوق **التراخيص والتطبيقات**.

3. في القسم **التراخيص** ، تحقق من تعيين ترخيص E5 للمستخدم أو تعيين ترخيص الوظائف الإضافية المناسب له. للحصول على قائمة بالتراخيص التي تدعم التدقيق المتقدم، راجع [متطلبات ترخيص التدقيق المتقدم](auditing-solutions-overview.md#advanced-audit-1).

4. قم بتوسيع **قسم** التطبيقات، وتحقق من تحديد خانة Microsoft 365 تدقيق متقدم.

5. إذا لم تكن خانة الاختيار محددة، فحددها، ثم انقر فوق **حفظ التغييرات.**

   سيبدأ تسجيل سجلات التدقيق ل MailItemsAccessed و Send في غضون 24 ساعة. يجب تنفيذ الخطوة 3 لبدء تسجيل حدثين آخرين للتدقيق المتقدم: SearchQueryInitiatedExchange و SearchQueryInitiatedSharePoint.

بالنسبة إلى المؤسسات التي تقوم بتعيين تراخيص لمجموعات من المستخدمين باستخدام الترخيص المستند إلى المجموعة، يجب إيقاف تشغيل تعيين الترخيص ل Microsoft 365 تدقيق متقدم للمجموعة. بعد حفظ التغييرات، تحقق من Microsoft 365 إيقاف تشغيل التدقيق المتقدم للمجموعة. ثم قم ب تشغيل تعيين الترخيص للمجموعة مرة أخرى. للحصول على إرشادات حول الترخيص المستند إلى المجموعة، راجع [تعيين تراخيص للمستخدمين حسب عضوية المجموعة في Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign).

أيضا، إذا قمت بتخصيص إجراءات علب البريد التي تم تسجيلها في علب بريد المستخدمين أو علب البريد المشتركة، لن يتم تلقائيا تدقيق أي أحداث تدقيق متقدم جديدة تم إصدارها بواسطة Microsoft على علب البريد هذه. للحصول على معلومات حول تغيير إجراءات علبة البريد التي يتم تدقيقها لكل نوع تسجيل دخول، راجع المقطع "تغيير إجراءات علبة البريد أو استعادتها التي تم تسجيلها بشكل افتراضي" في [إدارة تدقيق علبة البريد](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-advanced-audit-events"></a>الخطوة 2: تمكين أحداث التدقيق المتقدم

يجب تمكين حدثين من أحداث التدقيق المتقدم (SearchQueryInitiatedExchange و SearchQueryInitiatedSharePoint) لتسجيلهم عندما يقوم المستخدمون بإجراء عمليات بحث في Exchange Online SharePoint Online. لتمكين تدقيق هذين الحدثين للمستخدمين، يمكنك تشغيل الأمر التالي (لكل مستخدم) [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

في بيئة متعددة الجغرافيا، يجب تشغيل الأمر **السابق Set-Mailbox** في الغابات حيث توجد علبة بريد المستخدم. لتحديد موقع علبة بريد المستخدم، قم بتشغيل الأمر التالي: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

إذا كان الأمر لتمكين تدقيق استعلامات البحث قد تم تشغيله مسبقا في غابة تختلف عن تلك الموجودة في علبة بريد المستخدم، فيجب إزالة القيمة SearchQueryInitiated `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` من علبة بريد المستخدم عن طريق التشغيل ثم إضافتها إلى علبة بريد المستخدم في الغابات حيث توجد علبة بريد المستخدم.

## <a name="step-3-set-up-audit-retention-policies"></a>الخطوة 3: إعداد سياسات استبقاء التدقيق

بالإضافة إلى النهج الافتراضي الذي يحتفظ بسجلات تدقيق Exchange و SharePoint و Azure AD لمدة سنة واحدة، يمكنك إنشاء نهج استبقاء إضافية لسجل التدقيق لتلبية متطلبات عمليات الأمان في مؤسستك وفرق المعلومات والتوافق. لمزيد من المعلومات، راجع [إدارة سياسات استبقاء سجل التدقيق](audit-log-retention-policies.md).

## <a name="step-4-search-for-advanced-audit-events"></a>الخطوة 4: البحث عن أحداث التدقيق المتقدم

الآن وقد تم إعداد التدقيق المتقدم لمنظمتك، يمكنك البحث عن أحداث تدقيق متقدم هامة وأنشطة أخرى عند إجراء عمليات التحقيق في الطب الشرعي. بعد إكمال الخطوة 1 والخطوة 2، يمكنك البحث في سجل التدقيق عن أحداث التدقيق المتقدم وأنشطة أخرى أثناء عمليات التحقيق في التحليلات الجنائية للحسابات المساسة والأنواع الأخرى من عمليات التحقق من الأمان أو التوافق. للحصول على مزيد من المعلومات حول إجراء تحقيق في التحليلات الجنائية حول حسابات المستخدمين التي تم اختراقها باستخدام حدث التدقيق المتقدم MailItemsAccessed، راجع استخدام التدقيق المتقدم للتحقق من الحسابات المساس [بها](mailitemsaccessed-forensics-investigations.md).
