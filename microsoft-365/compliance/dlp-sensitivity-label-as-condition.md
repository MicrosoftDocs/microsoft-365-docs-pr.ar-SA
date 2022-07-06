---
title: استخدام تسميات الحساسية كشروط في نهج DLP
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
description: تعرف على الخدمات وأنواع العناصر التي يمكنك استخدامها أوصاف الحساسية كشروط في نهج DLP
ms.openlocfilehash: 55803a2c354890264f99753af2aa6337cf49182a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632388"
---
# <a name="use-sensitivity-labels-as-conditions-in-dlp-policies"></a>استخدام تسميات الحساسية كشروط في نهج DLP

يمكنك استخدام [تسميات الحساسية](sensitivity-labels.md) كشرط في نهج DLP لهذه المواقع:

- Exchange Online رسائل البريد الإلكتروني
- SharePoint Online
- مواقع OneDrive for Business
- أجهزة Windows 10

تظهر تسميات الحساسية كخيار في قائمة **تحتوي على المحتوى** .

> [!div class="mx-imgBorder"]
> ![وصف الحساسية كشرط.](../media/dlp-sensitivity-label-as-a-condition.png)

> [!IMPORTANT]
> لن تتوفر **تسميات الحساسية** كشرط إذا قمت بتحديد **دردشة Teams ورسائل القناة** كموقع لتطبيق نهج DLP.


## <a name="supported-items-scenarios-and-policy-tips"></a>العناصر والسيناريوهات وتلميحات النهج المعتمدة

يمكنك استخدام تسميات الحساسية كشروط على هذه العناصر وفي هذه السيناريوهات.

### <a name="supported-items"></a>العناصر المدعومة

|الخدمة  |نوع العنصر  |متوفر لتلميح النهج  |قابله  |
|---------|---------|---------|---------|
|Exchange    |رسالة بريد إلكتروني         |نعم         |نعم         |
|Exchange    |مرفق البريد الإلكتروني         |no         |نعم *         |
|SharePoint Online     |العناصر في SharePoint Online         |نعم         |نعم         |
|OneDrive for Business     |العناصر         |نعم         |نعم         |
|الفرق     |Teams ورسائل القناة         |غير قابل للتطبيق         |غير قابل للتطبيق         |
|الفرق     |المرفقات         |نعم **         |نعم **         |
|أجهزة Windows 10     |العناصر         |نعم         |نعم         |
|MCAS (معاينة) |العناصر         |نعم         |نعم         |

\* يتم دعم الكشف عن DLP لمرفقات البريد الإلكتروني المسماة بالحساسية لأنواع ملفات Office المستندة إلى Open XML فقط.

\** يتم تحميل المرفقات المرسلة في Teams عبر الدردشة أو القنوات 1:1 تلقائيا إلى OneDrive for Business وSharePoint. وبالتالي، إذا تم تضمين SharePoint Online أو OneDrive for Business كمواقع في نهج DLP، فسيتم تضمين المرفقات المسماة المرسلة في Teams تلقائيا في نطاق هذا الشرط. لا يلزم تحديد Teams كموقع في نهج DLP.

> [!NOTE]
> قدرة DLP على الكشف عن تسميات الحساسية في SharePoint وOneDrive for business محدودة. لمزيد من المعلومات، راجع [تمكين تسميات الحساسية لملفات Office في SharePoint وOneDrive](sensitivity-labels-sharepoint-onedrive-files.md#limitations).

### <a name="supported-scenarios"></a>السيناريوهات المدعومة

- سيتمكن مسؤول DLP من رؤية قائمة بجميع تسميات الحساسية في المستأجر عندما يختارون تضمين تسمية حساسية واحدة أو أكثر كشرط.

- يتم دعم استخدام تسميات الحساسية كشرط عبر جميع أحمال العمل كما هو موضح في مصفوفة الدعم أعلاه.

- سيستمر عرض تلميحات نهج DLP عبر أحمال العمل (باستثناء Outlook Win32) لنهج DLP التي تحتوي على وصف الحساسية كشرط.

- ستظهر أوصاف الحساسية أيضا كجزء من البريد الإلكتروني لتقرير الحادث إذا تطابق نهج DLP مع وصف الحساسية كشرط.

- سيتم أيضا عرض تفاصيل وصف الحساسية في سجل تدقيق مطابقة قاعدة DLP لمطابقة نهج DLP الذي يحتوي على وصف الحساسية كشرط.


### <a name="support-policy-tips"></a>تلميحات نهج الدعم


|عبء العمل  |تلميحات النهج المعتمدة/غير المعتمدة  |
|---------|---------|
|OWA |    دعم     |
|Outlook Win 32    |  غير معتمد       |
|SharePoint   |   دعم      |
|OneDrive for Business    |    دعم     |
|أجهزة نقطة النهاية   |  غير معتمد       |
