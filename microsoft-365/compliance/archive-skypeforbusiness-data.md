---
title: إعداد موصل لأرشفة Skype for Business في Microsoft 365
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
description: تعرف على كيفية إعداد موصل واستخدامه في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من Skype for Business إلى Microsoft 365.
ms.openlocfilehash: a783ad4bea9b06fcef3f7da4f67a98c17310a38e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575555"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>إعداد موصل لأرشفة Skype for Business البيانات

استخدم موصل Veritas في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من النظام الأساسي Skype for Business إلى علب بريد المستخدمين في Microsoft 365 الخاصة بك. يوفر Veritas [Skype for Business](https://www.veritas.com/en/au/insights/merge1/skype-for-business) تم تكوينه لالتقاط العناصر من مصدر بيانات جهة خارجية (بشكل منتظم) واستيراد هذه العناصر إلى Microsoft 365. يحول الموصل المحتوى مثل الرسائل بين المستخدمين والمحادثات الثابتة ورسائل المؤتمر من Skype for Business إلى تنسيق رسالة بريد إلكتروني، ثم يقوم باستيراد هذه العناصر إلى علبة بريد المستخدم في Microsoft 365.

بعد Skype for Business البيانات في علب بريد المستخدمين، يمكنك تطبيق Microsoft 365 التوافق مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery ونهج الاستبقاء وتسميات الاستبقاء. استخدام موصل Skype for Business لاستيراد البيانات وأرشفتها في Microsoft 365 يساعد مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="overview-of-archiving-skype-for-business-data"></a>نظرة عامة حول أرشفة Skype for Business البيانات

تشرح النظرة العامة التالية عملية استخدام موصل لأرشفة Skype for Business في Microsoft 365.

![أرشفة سير العمل Skype for Business البيانات.](../media/SkypeforBusinessConnectorWorkflow.png)

1. تعمل مؤسستك مع Skype for Business لإعداد موقع Skype for Business ويب.

2. مرة واحدة كل 24 ساعة، Skype for Business نسخ العناصر إلى موقع Veritas Merge1. يحول الموصل أيضا Skype for Business إلى تنسيق رسالة بريد إلكتروني.

3. يتصل Skype for Business الذي تقوم بإنشاءه في مركز التوافق في Microsoft 365 بموقع Veritas Merge1 كل يوم، وينقل محتوى Skype for Business إلى موقع تخزين Azure آمن في سحابة Microsoft.

4. يقوم الموصل باستيراد العناصر التي تم تحويلها إلى علب بريد مستخدمين معينين باستخدام قيمة خاصية البريد  الإلكتروني لتعيين المستخدم التلقائي كما هو موضح في [الخطوة 3](#step-3-map-users-and-complete-the-connector-setup). يتم إنشاء مجلد فرعي في مجلد علبة الوارد **Skype for Business** في علب بريد المستخدمين، كما يتم استيراد العناصر إلى ذلك المجلد. يقوم الموصل بذلك باستخدام قيمة الخاصية *البريد* الإلكتروني. يحتوي Skype for Business عنصر على هذه الخاصية، التي يتم ملؤها عنوان البريد الإلكتروني لكل مشارك في العنصر.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

- إنشاء حساب Merge1 لموصلات Microsoft. للقيام بذلك، اتصل بدعم [عملاء Veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact.html). يجب تسجيل الدخول إلى هذا الحساب عند إنشاء الموصل في الخطوة 1.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم Skype for Business في الخطوة 1 (وإكماله في الخطوة 3). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- يوجد موصل بيانات Veritas هذا في المعاينة العامة في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. قد تشتمل التطبيقات والخدمات التي تقدمها جهة خارجية على تخزين بيانات عملاء مؤسستك ونقلها وحمايتها على أنظمة أخرى تقع خارج البنية الأساسية ل Microsoft 365 وبالتالي لا تغطيها التزامات التوافق وحماية البيانات Microsoft 365. لا تقدم Microsoft أي تمثيل يشير فيه استخدام هذا المنتج للاتصال إلى تطبيقات  الأطراف الخارجية إلى أن تلك التطبيقات التي تقدمها جهة خارجية متوافقة مع FEDRAMP.

## <a name="step-1-set-up-the-skype-for-business-connector"></a>الخطوة 1: إعداد Skype for Business الموصل

الخطوة الأولى هي الوصول إلى صفحة موصلات البيانات في مركز التوافق في Microsoft 365 وإنشاء موصل Skype for Business البيانات.

1. انتقل إلى <https://compliance.microsoft.com> موصلات  >  البيانات **وانقر Skype for Business**.

2. في الصفحة **Skype for Business** وصف المنتج، انقر فوق **إضافة موصل**.

3. في صفحة **شروط الخدمة** ، انقر فوق **قبول**.

4. أدخل اسما فريدا يعرف الموصل، ثم انقر فوق **التالي**.

5. سجل الدخول إلى حساب Merge1 لتكوين الموصل.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>الخطوة 2: تكوين Skype for Business على موقع Veritas Merge1

الخطوة الثانية هي تكوين موصل Skype for Business على موقع Veritas Merge1. للحصول على معلومات حول كيفية تكوين موصل Skype for Business، راجع [دمج1 دليل مستخدم الموصلات الخارجية](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).

بعد النقر **فوق & إنهاء**، يتم عرض صفحة تعيين المستخدم  في معالج الموصل في مركز التوافق في Microsoft 365.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>الخطوة 3: تعيين المستخدمين وإكمال إعداد الموصل

ل تعيين المستخدمين وإكمال إعداد الموصل في مركز التوافق في Microsoft 365، اتبع الخطوات التالية:

1. في الصفحة **تعيين Skype for Business للمستخدمين Microsoft 365** المستخدمين، يمكنك تعيين المستخدم تلقائيا. تتضمن Skype for Business العناصر خاصية تسمى *البريد الإلكتروني*، والتي تحتوي على عناوين البريد الإلكتروني للمستخدمين في مؤسستك. إذا كان يمكن للموصل إقران هذا العنوان بمستخدم Microsoft 365، يتم استيراد العناصر إلى علبة بريد هذا المستخدم.

2. انقر **فوق** التالي، وراجع الإعدادات، ثم انتقل إلى صفحة  موصلات البيانات للاطلاع على تقدم عملية الاستيراد للموصل الجديد.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>الخطوة 4: مراقبة Skype for Business الموصل

بعد إنشاء Skype for Business الموصل، يمكنك عرض حالة الموصل في مركز التوافق في Microsoft 365.

1. انتقل إلى <https://compliance.microsoft.com/> **موصلات البيانات وانقر** فوقها في التنقل الأيسر.

2. انقر فوق **علامة التبويب موصلات**، ثم حدد **Skype for Business الموصل لعرض** صفحة القائمة المطيرة، التي تحتوي على الخصائص والمعلومات حول الموصل.

3. ضمن **حالة الموصل مع المصدر**، انقر فوق الارتباط **تنزيل السجل** لفتح (أو حفظ) سجل الحالة للموصل. يحتوي هذا السجل على بيانات تم استيرادها إلى سحابة Microsoft.

## <a name="known-issues"></a>المشاكل المعروفة

- في هذا الوقت، لا ندعم استيراد المرفقات أو العناصر التي يزيد حجمها عن 10 مبايت. سيتوفر الدعم للعناصر الكبيرة في وقت لاحق.
