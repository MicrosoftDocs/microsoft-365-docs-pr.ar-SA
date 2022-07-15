---
title: إدارة مالكي الجدول الزمني لإدارة الورديات
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
description: تعرف على كيفية إدارة مالكي الورديات لإدارة الجدول الزمني. يمكنك تعيين نهج لرفع إذن عضو الفريق إلى مالك الجدول الزمني.
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- microsoftcloud-healthcare
- microsoftcloud-retail
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7e91519820adbefd780f27759c3da4ef31d7cb8f
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823662"
---
# <a name="schedule-owner-for-shift-management"></a>مالك الجدول الزمني لإدارة الورديات

## <a name="overview"></a>نظرة عامة

تتيح لك ميزة "مالك الجدول" رفع أذونات عضو الفريق بحيث يمكنه إدارة الجداول دون جعل الموظف مالكا للفريق. باستخدام أذونات "مالك الجدول"، يمكن للموظف إدارة جدول فريقه دون أن يتمكن من تعديل أي خصائص أخرى للفريق مثل تحديث قنوات الفريق أو تحريرها أو حذفها.

ما الذي يمكن للمستخدم الذي يملك أذونات مالك الجدولة فعله؟

- إنشاء جداول زمنية وتحريرها ونشرها لإدارة تعيينات الوردية الخاصة بفريقهم.
- عرض طلبات الورديات والموافقة عليها، بما في ذلك طلبات تبديل الورديات وأخذ الورديات المفتوحة.
- إدارة الإعدادات في الورديات لتمكين ميزات معينة للفريق.
- عرض الجدول الزمني لفريقهم وتعديله لمعالجة كشوف مرتبات الموظفين.

## <a name="why-schedule-owner"></a>لماذا مالك الجدول الزمني؟

بدون ميزة "مالك الجدول"، قد تتعطل وظائف الأعمال اليومية. بينما يساعد مالك الفريق على تشغيل الفريق، فقد لا يكون بالضرورة الشخص المسؤول عن الجدولة اليومية. في هذه الحالة، فإن نقل مسؤولية إدارة الجدول فقط إلى عضو آخر في الفريق يبسط العمليات اليومية داخل الفريق ويزيل ارتباك عضوين في الفريق يتمتعان بنفس امتيازات الوصول.

## <a name="scenario"></a>السيناريو

فيما يلي مثال على كيفية استخدام مؤسستك لميزة "مالك الجدول".

تعمل في مؤسسة كبيرة حيث يقوم مديرو الأقسام بالإبلاغ مباشرة إلى مدير المتجر. يتمتع مدير المتجر بمزيد من السلطة داخل شركتك وهو مالك الفريق في Shifts. من ناحية أخرى، تتم إضافة مديري الأقسام فقط إلى الورديات كأعضاء الفريق. في حين أن مديري المتاجر لديهم أقدمية من مديري الأقسام، فمن المنطقي أن يتعامل مديرو الأقسام مع الجدولة اليومية لموظفي فريقهم.

*بدون مالك الجدول الزمني*، يجب منح مديري الأقسام نفس الامتيازات التي يتمتع بها مالك الفريق. في الآونة الأخيرة، كان مديرو الأقسام ينقلون المعلومات ويغيرون اسم القنوات، وقد تسبب ذلك في حدوث تعقيدات مع عمل مدير المتجر. يريد مدير المتجر أن يتمكن مديرو الأقسام من تنظيم جداولهم، ولكنه لا يريدهم أن يتمكنوا من تغيير أي شيء آخر في الفريق، خارج الورديات.

*باستخدام "مالك الجدول"*، يمكن منح مديري الأقسام امتيازات الجدولة، دون أي امتيازات مالك فريق أخرى.

## <a name="manage-schedule-ownership"></a>إدارة ملكية الجدول

بصفتك مسؤولا، يمكنك استخدام النهج للتحكم في ملكية إدارة الجدولة في مؤسستك. يمكنك إدارة هذه النهج باستخدام أوامر PowerShell cmdlets التالية:

- [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy?view=teams-ps)
- [Get-CsTeamsShiftsPolicy](/powershell/module/teams/get-csteamsshiftspolicy?view=teams-ps)
- [Set-CsTeamsShiftsPolicy](/powershell/module/teams/set-csteamsshiftspolicy?view=teams-ps)
- [Grant-CsTeamsShiftsPolicy](/powershell/module/teams/grant-csteamsshiftspolicy?view=teams-ps)
- [Remove-CsTeamsShiftsPolicy](/powershell/module/teams/remove-csteamsshiftspolicy?view=teams-ps)

### <a name="example-1"></a>مثال 1

هنا، نقوم بإنشاء نهج جديد يسمى ScheduleOwnerPolicy مع تشغيل ميزة "مالك الجدول".

```powershell
New-CsTeamsShiftsPolicy –Identity ScheduleOwnerPolicy  -EnableScheduleOwnerPermissions $true -AccessType UnrestrictedAccess_TeamsApp
```

### <a name="example-2"></a>مثال 2

في هذا المثال، نقوم بتعيين نهج يسمى ScheduleOwnerPolicy لمستخدم يسمى remy@contoso.com.

```powershell
Grant-CsTeamsShiftsPolicy -Identity remy@contoso.com -PolicyName ScheduleOwnerPolicy
```

## <a name="related-articles"></a>المقالات ذات الصلة

- [إدارة تطبيق الورديات لمؤسستك في Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [إدارة الوصول المستند إلى الوردية للعاملين في الخطوط الأمامية في Teams](manage-shift-based-access-flw.md)
