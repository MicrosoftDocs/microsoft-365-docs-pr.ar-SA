---
title: الفهرسة المتقدمة للبيانات غير الهامة
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: عندما تتم إضافة شخص منضم إلى حالة Advanced eDiscovery، تتم إعادة معالجة أي محتوى تم اعتباره مفهرسا جزئيا لجعله قابلا للبحث بشكل كامل.
ms.openlocfilehash: 1c43f55f399f69d58e05c073e688170d53480b42
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/01/2021
ms.locfileid: "63566087"
---
# <a name="advanced-indexing-of-custodian-data"></a>الفهرسة المتقدمة للبيانات غير الهامة

عند إضافة أحد المعيدين إلى حالة Advanced eDiscovery، يتم إعادة فهرسة أي محتوى تم اعتباره مفهرسا جزئيا أو لديه أخطاء في الفهرسة. تسمى عملية إعادة الفهرسة هذه *الفهرسة المتقدمة*. هناك أسباب كثيرة لفهرسة المحتوى جزئيا أو وجود أخطاء في الفهرسة. يشمل ذلك ملفات الصور أو وجود صور في ملف أو أنواع ملفات غير معتمدة أو حدود فهرسة حجم الملف. بالنسبة SharePoint الملفات، يتم وضع علامة على الفهرسة المتقدمة التي يتم تشغيلها فقط على العناصر كمفهرسة جزئيا أو التي بها أخطاء في الفهرسة. في Exchange، لا يتم وضع علامة على رسائل البريد الإلكتروني التي بها مرفقات صور على أنها مفهرسة جزئيا أو بها أخطاء في الفهرسة. وهذا يعني أنه لن يتم إعادة فهرسة هذه الملفات بواسطة عملية الفهرسة المتقدمة.

لمعرفة المزيد حول معالجة الدعم والعناصر المفهرسة جزئيا، راجع:

- [أنواع الملفات المعتمدة في Advanced eDiscovery](supported-filetypes-ediscovery20.md)

- [العناصر المفهرسة جزئيا في eDiscovery](partially-indexed-items-in-content-search.md)

- [تنسيقات الملفات المفهرسة حسب Exchange البحث](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [ملحقات أسماء الملفات وأنواع الملفات التي تم تحليلها افتراضيا في SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>عرض نتائج الفهرسة المتقدمة

بعد اكتمال عملية الفهرسة المتقدمة، يمكنك فهم مدى فعالية إعادة المعالجة.  في طريقة العرض نتائج الفهرسة المتقدمة على علامة  التبويب معالجة حالة، يسرد الرسم البياني عدد العناصر المضافة إلى *الفهرس المختلط*.  الفهرس المختلط هو المكان Advanced eDiscovery تخزين المحتوى الذي تتم إعادة معالجته فيه.

تتضمن طريقة العرض هذه أيضا عدد العناصر التي تتطلب المعالجة ورسما بيانيا آخر من الأخطاء حسب نوع الملف. لمزيد من المعلومات، اطلع على:

- [تصحيح الأخطاء عند معالجة البيانات](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [تصحيح خطأ عنصر واحد](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>تحديث الفهرس المتقدم للمدبرين

عندما تتم إضافة أحد المفهرسين إلى Advanced eDiscovery، تتم إعادة معالجة كل العناصر المفهرسة جزئيا. ومع ذلك، مع مرور الوقت، قد تضاف عناصر مفهرسة بشكل جزئي إلى علبة بريد المستخدم أو OneDrive المستخدم.  إذا لزم الأمر، يمكنك تحديث الفهرس لمؤشر معين. لمزيد من المعلومات، راجع [إدارة التغذية في Advanced eDiscovery أخرى](manage-new-custodians.md#reindex-custodian-data). يمكنك أيضا تحديث الفهرس لجميع التغذية في حالة بالنقر فوق الفهرس **تحديث** على **علامة التبويب** معالجة.

> [!NOTE]
> إن تحديث فهارس الكيانات هو عملية طويلة. من المستحسن عدم تحديث فهارس أكثر من مرة واحدة في اليوم في حالة ما.
