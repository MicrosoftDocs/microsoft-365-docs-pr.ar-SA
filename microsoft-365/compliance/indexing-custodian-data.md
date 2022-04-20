---
title: الفهرسة المتقدمة لبيانات الوصي
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
description: عند إضافة أمين إلى حالة eDiscovery (Premium)، تتم إعادة معالجة أي محتوى يعتبر مفهرسا جزئيا لجعله قابلا للبحث بالكامل.
ms.openlocfilehash: 3c6f0079f87dbc4711fed7d776204c287d5b5865
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64931968"
---
# <a name="advanced-indexing-of-custodian-data"></a>الفهرسة المتقدمة لبيانات الوصي

عند إضافة أمين إلى حالة eDiscovery (Premium)، يعاد فهرسة أي محتوى يعتبر مفهرسا جزئيا أو به أخطاء فهرسة. تسمى عملية إعادة الفهرسة هذه *الفهرسة المتقدمة*. هناك العديد من الأسباب التي تجعل المحتوى مفهرسا جزئيا أو يحتوي على أخطاء فهرسة. يتضمن ذلك ملفات الصور أو وجود صور في ملف أو أنواع ملفات غير معتمدة أو حدود فهرسة بحجم الملف. بالنسبة لملفات SharePoint، يتم وضع علامة على الفهرسة المتقدمة فقط على العناصر على أنها مفهرسة جزئيا أو تحتوي على أخطاء فهرسة. في Exchange، لا يتم وضع علامة على رسائل البريد الإلكتروني التي تحتوي على مرفقات صور على أنها مفهرسة جزئيا أو بها أخطاء فهرسة. وهذا يعني أنه لن تتم إعادة فهرسة هذه الملفات بواسطة عملية الفهرسة المتقدمة.

لمعرفة المزيد حول معالجة الدعم والعناصر المفهرسة جزئيا، راجع:

- [أنواع الملفات المعتمدة في eDiscovery (Premium)](supported-filetypes-ediscovery20.md)

- [العناصر المفهرسة جزئيا في eDiscovery](partially-indexed-items-in-content-search.md)

- [تنسيقات الملفات المفهرسة بواسطة Exchange Search](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- [ملحقات أسماء الملفات المتتبعة الافتراضية وأنواع الملفات الموزعة في SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)

## <a name="viewing-advanced-indexing-results"></a>عرض نتائج الفهرسة المتقدمة

بعد اكتمال عملية الفهرسة المتقدمة، يمكنك الحصول على فهم لفعالية إعادة المعالجة.  في طريقة عرض نتائج الفهرسة المتقدمة على علامة التبويب **"معالجة** " لحالة ما، يسرد الرسم البياني عدد العناصر المضافة إلى *الفهرس المختلط*.  الفهرس المختلط هو المكان الذي يخزن فيه eDiscovery (Premium) المحتوى الذي تمت إعادة معالجتها.

تتضمن طريقة العرض هذه أيضا عدد العناصر التي تتطلب المعالجة ورسما بيانيا آخر للأخطاء حسب نوع الملف. لمزيد من المعلومات، اطلع على:

- [معالجة الخطأ عند معالجة البيانات](error-remediation-when-processing-data-in-advanced-ediscovery.md)

- [تصحيح خطأ عنصر واحد](single-item-error-remediation.md)

## <a name="updating-the-advanced-index-for-custodians"></a>تحديث الفهرس المتقدم للأمناء

عند إضافة أمين إلى حالة eDiscovery (Premium)، تتم إعادة معالجة جميع العناصر المفهرسة جزئيا. ومع ذلك، مع مرور الوقت، قد تتم إضافة المزيد من العناصر المفهرسة جزئيا إلى علبة بريد المستخدم أو حساب OneDrive.  إذا لزم الأمر، يمكنك تحديث الفهرس لوصي معين. لمزيد من المعلومات، راجع [إدارة أمناء الحفظ في حالة eDiscovery (Premium](manage-new-custodians.md#reindex-custodian-data)). يمكنك أيضا تحديث الفهرس لكافة أمناء الحفظ في حالة ما بالنقر فوق **فهرس التحديث** على علامة التبويب **"معالجة** ".

> [!NOTE]
> تحديث فهارس الوصي عملية طويلة الأمد. يوصى بعدم تحديث الفهارس أكثر من مرة واحدة في اليوم في كل حالة.
