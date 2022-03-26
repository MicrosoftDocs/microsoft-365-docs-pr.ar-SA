---
title: إعداد موصل لأرشفة SQL البيانات في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: تعرف على كيفية إعداد موصل DataParser SQL 17a-4 واستخدامه لاستيراد SQL البيانات Microsoft 365.
ms.openlocfilehash: 2e1c12f164d34656f918f0083688268f043840ee
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570328"
---
# <a name="set-up-a-connector-to-archive-sql-data"></a>إعداد موصل لأرشفة SQL البيانات

استخدم SQL [DataParser](https://www.17a-4.com/sql-dataparser/) من 17a-4 LLC لاستيراد البيانات وأرشفتها من قاعدة بيانات SQL إلى علب بريد المستخدمين في Microsoft 365 الخاصة بك. يتضمن DataParser SQL تم تكوينه لالتقاط العناصر من مصدر بيانات جهة خارجية واستيراد هذه العناصر Microsoft 365. يقوم SQL DataParser بتحويل SQL البيانات إلى تنسيق رسالة بريد إلكتروني ثم استيراد هذه العناصر إلى علب بريد المستخدمين في Microsoft 365.

بعد SQL البيانات في علب بريد المستخدمين، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery ونهج الاستبقاء وتسميات الاستبقاء وتوافق الاتصالات. استخدام موصل SQL لاستيراد البيانات وأرشفتها في Microsoft 365 يساعد مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="overview-of-archiving-sql-data"></a>نظرة عامة حول أرشفة SQL البيانات

تشرح النظرة العامة التالية عملية استخدام موصل بيانات لأرشفة SQL في Microsoft 365.

![أرشفة سير العمل SQL البيانات من 17a-4.](../media/SQLDatabaseDataParserConnectorWorkflow.png)

1. تعمل مؤسستك مع 17a-4 لإعداد SQL DataParser.

2. بشكل منتظم، يتم SQL العناصر بواسطة DataParser. يحول DataParser أيضا محتوى الرسالة إلى تنسيق رسالة بريد إلكتروني.

3. يتصل SQL DataParser الذي تقوم بإنشاءه في مركز التوافق في Microsoft 365 ب DataParser وينقل الرسائل إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يتم إنشاء مجلد فرعي في مجلد علبة الوارد **SQL DataParser** في علب بريد المستخدمين، كما يتم استيراد SQL العناصر إلى ذلك المجلد. يحدد الموصل علبة البريد التي تريد استيراد العناصر لها باستخدام قيمة خاصية *البريد* الإلكتروني. يحتوي SQL عنصر على هذه الخاصية، التي يتم ملؤها عنوان البريد الإلكتروني لكل مشارك.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب DataParser لموصلات Microsoft. للقيام بذلك، اتصل [ب 17a-4 LLC](https://www.17a-4.com/contact/). يجب تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم SQL DataParser في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يتوفر موصل البيانات 17a-4 هذا في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. قد تشتمل التطبيقات والخدمات التي تقدمها جهة خارجية على تخزين بيانات عملاء مؤسستك ونقلها وحمايتها على أنظمة أخرى تقع خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات التوافق وحماية البيانات Microsoft 365. لا تقدم Microsoft أي تمثيل يشير فيه استخدام هذا المنتج للاتصال إلى تطبيقات  الأطراف الخارجية إلى أن تلك التطبيقات التي تقدمها جهة خارجية متوافقة مع FEDRAMP.

## <a name="step-1-set-up-a-sql-dataparser-connector"></a>الخطوة 1: إعداد موصل DataParser SQL DataParser

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مركز التوافق في Microsoft 365 وإنشاء موصل 17a-4 SQL البيانات.

1. انتقل إلى <https://compliance.microsoft.com> موصلات  >  البيانات **ثم انقر SQL DataParser**.

2. على الصفحة **SQL وصف منتج DataParser**، انقر فوق **إضافة موصل**.

3. في صفحة **شروط الخدمة** ، انقر فوق **قبول**.

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **التالي**.

5. سجل الدخول إلى حسابك في 17a-4 وأكمل الخطوات في معالج اتصال DataParser SQL DataParser.

## <a name="step-2-configure-the-sql-dataparser-connector"></a>الخطوة 2: تكوين SQL DataParser

العمل باستخدام دعم 17a-4 لتكوين SQL DataParser.

## <a name="step-3-map-users"></a>الخطوة 3: تعيين المستخدمين

يقوم SQL DataParser تلقائيا ب تعيين المستخدمين إلى عناوين بريدهم Microsoft 365 الإلكتروني قبل استيراد البيانات Microsoft 365.

## <a name="step-4-monitor-the-sql-dataparser-connector"></a>الخطوة 4: مراقبة SQL DataParser

بعد إنشاء SQL DataParser، يمكنك عرض حالة الموصل في مركز التوافق في Microsoft 365.

1. انتقل إلى <https://compliance.microsoft.com> **موصلات البيانات وانقر** فوقها في التنقل الأيسر.

2. انقر فوق **علامة** التبويب موصلات، ثم حدد SQL DataParser الذي أنشأته لعرض صفحة القائمة المطيرة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق الارتباط **تنزيل السجل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 مبايت. سيتوفر الدعم للعناصر الكبيرة في وقت لاحق.
