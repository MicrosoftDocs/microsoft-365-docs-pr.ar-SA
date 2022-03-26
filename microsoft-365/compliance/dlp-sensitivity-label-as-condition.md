---
title: استخدام تسميات الحساسية كالشروط في سياسات DLP
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
description: تعرف على الخدمات وأنواع العناصر التي يمكنك استخدام تسميات الحساسية كالشروط في سياسات DLP
ms.openlocfilehash: 1117471e38b430f1d7289c6aae76994ac5acd494
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63572941"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>استخدام تسميات الحساسية كالشروط في سياسات DLP

يمكنك استخدام [تسميات الحساسية](sensitivity-labels.md) كشرط في سياسات DLP لهذه المواقع:

- Exchange Online البريد الإلكتروني
- SharePoint Online
- OneDrive for Business ويب
- Windows 10 الأجهزة

تظهر تسميات الحساسية كخيار في القائمة **يحتوي المحتوى** على.

> [!div class="mx-imgBorder"]
> ![تسمية الحساسية كشرط.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> **لن تتوفر تسميات** الحساسية كشرط إذا قمت Teams رسائل الدردشة والقناة كموا موقع لتطبيق نهج DLP.


## <a name="supported-items-scenarios-and-policy-tips"></a>العناصر والسيناريوهات وتلميحات النهج المعتمدة

يمكنك استخدام تسميات الحساسية كالشروط على هذه العناصر وفي هذه السيناريوهات.

### <a name="supported-items"></a>العناصر المعتمدة

|الخدمة  |نوع العنصر  |متوفر لتلميح النهج  |قابل لفرض  |
|---------|---------|---------|---------|
|Exchange    |رسالة بريد إلكتروني         |نعم         |نعم         |
|Exchange    |مرفق البريد الإلكتروني         |لا         |نعم *         |
|SharePoint Online     |العناصر في SharePoint Online         |نعم         |نعم         |
|OneDrive for Business     |العناصر         |نعم         |نعم         |
|الفرق     |Teams الرسائل والقنوات         |غير قابل للتطبيق         |غير قابل للتطبيق         |
|الفرق     |المرفقات         |نعم **         |نعم **         |
|Windows 10 الأجهزة     |العناصر         |نعم         |نعم         |
|MCAS (معاينة) |العناصر         |نعم         |نعم         |

\*يتم دعم الكشف عن DLP لمرفقات البريد الإلكتروني التسمية بالحساسية Office الملفات فقط.

\** يتم تحميل المرفقات المرسلة Teams عبر الدردشة أو القنوات التي يزيد عددها عن 1:1 إلى OneDrive for Business SharePoint. وبالتالي إذا SharePoint عبر الإنترنت أو OneDrive for Business كمواد في نهج DLP، سيتم تضمين المرفقات الملصقات المرسلة في Teams تلقائيا في نطاق هذا الشرط. Teams يجب تحديد الموقع في نهج DLP.

> [!NOTE]
> إن قدرة DLP على الكشف عن تسميات الحساسية في SharePoint OneDrive محدودة. لمزيد من المعلومات، راجع تمكين تسميات الحساسية لملفات Office [في SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>السيناريوهات المعتمدة

- سيكون مسؤول DLP قادرا على رؤية قائمة بكل تسميات الحساسية في المستأجر عندما يختار تضمين تسمية حساسية واحدة أو أكثر كشرط.

- يتم دعم استخدام تسميات الحساسية كشرط عبر جميع أحمال العمل كما هو مشار إليه في مصفوفة الدعم أعلاه.

- سيستمر عرض تلميحات نهج DLP عبر أحمال العمل (باستثناء Outlook Win32) لنهج DLP التي تحتوي على تسمية الحساسية كشرط.

- ستظهر تسميات الحساسية أيضا كجزء من البريد الإلكتروني للتقرير عن الحادث إذا تطابق نهج DLP مع تسمية الحساسية كشرط.

- سيتم أيضا عرض تفاصيل تسمية الحساسية في قاعدة DLP تتطابق مع سجل التدقيق لمطابقة نهج DLP الذي يحتوي على تسمية الحساسية كشرط.


### <a name="support-policy-tips"></a>تلميحات نهج الدعم


|حمل العمل  |تلميحات النهج معتمدة/غير معتمدة  |
|---------|---------|
|OWA |    معتمد     |
|Outlook Win 32    |  غير معتمد       |
|SharePoint   |   معتمد      |
|OneDrive for Business    |    معتمد     |
|أجهزة نقاط النهاية   |  غير معتمد       |
