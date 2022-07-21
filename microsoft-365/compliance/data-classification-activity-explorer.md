---
title: بدء استخدام مستكشف النشاط
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: يتيح لك مستكشف النشاط رؤية الإجراءات التي يتخذها المستخدمون على المحتوى المسمى وتصفيتها.
ms.openlocfilehash: c33ff2653eef6813caf9b9281903b7248af12359
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917991"
---
# <a name="get-started-with-activity-explorer"></a>بدء استخدام مستكشف النشاط

تمنحك [نظرة عامة على تصنيف البيانات](data-classification-overview.md) وعلامات تبويب [مستكشف المحتوى](data-classification-content-explorer.md) إمكانية رؤية المحتوى الذي تم اكتشافه وتسمياته، ومكان وجود هذا المحتوى. يقوم مستكشف النشاط بتقريب هذه المجموعة من الوظائف من خلال السماح لك بمراقبة ما يتم القيام به مع المحتوى المسمى. يوفر مستكشف النشاط طريقة عرض تاريخية للأنشطة على المحتوى المسمى. يتم تجميع معلومات النشاط من سجلات التدقيق الموحدة ل Microsoft 365 وتحويلها وإتاحتها في واجهة مستخدم مستكشف النشاط. يبلغ مستكشف النشاط عن ما يصل إلى 30 يوما من البيانات.

![مستكشف نشاط نظرة عامة على لقطة شاشة العنصر النائب.](../media/data-classification-activity-explorer-1.png)

هناك أكثر من 30 من عوامل التصفية المختلفة المتاحة للاستخدام، وبعضها:

- نطاق التاريخ
- نوع النشاط
- موقع
- User
- وصف الحساسية
- تسمية الاستبقاء
- مسار الملف
- نهج DLP



## <a name="prerequisites"></a>المتطلبات الأساسية

يجب أن يكون لكل حساب يصل إلى تصنيف البيانات ويستخدمه ترخيص معين له من أحد هذه الاشتراكات:

- Microsoft 365 (E5)
- Office 365 (E5)
- الوظيفة الإضافية للتوافق المتقدم (E5)
- الوظيفة الإضافية Advanced Threat Intelligence (E5)
- إدارة & حماية المعلومات Microsoft 365 E5/a5
- توافق Microsoft 365 E5/A5

### <a name="permissions"></a>الأذونات

يجب تعيين عضوية للحساب بشكل صريح في أي من مجموعات الأدوار هذه أو منحه الدور بشكل صريح.

### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم في الوصول.

فيما يلي قائمة بالأدوار القابلة للتطبيق الموجودة في المعاينة. لمعرفة المزيد عنها، راجع ["الأدوار" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- حماية البيانات مسؤول
- محلل حماية البيانات
- حماية البيانات المحقق
- قارئ حماية البيانات

فيما يلي قائمة بمجموعات الأدوار القابلة للتطبيق الموجودة في المعاينة. لمعرفة المزيد حول ذلك، راجع [مجموعات الأدوار في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية البيانات
- مسؤولو حماية البيانات
- حماية البيانات المحللين
- المحققون حماية البيانات
- قارئات حماية البيانات

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**مجموعات أدوار Microsoft 365**

- المسؤول العام
- مسؤول التوافق
- مسؤول الأمان
- مسؤول بيانات التوافق

**أدوار Microsoft 365**

- مسؤول التوافق
- مسؤول الأمان
- قارئ الأمان

## <a name="activity-types"></a>أنواع الأنشطة

يجمع مستكشف النشاط معلومات النشاط من سجلات التدقيق على مصادر متعددة للأنشطة. لمزيد من المعلومات التفصيلية حول نشاط التسمية الذي يجعله في مستكشف النشاط، راجع [أحداث التسمية المتوفرة في مستكشف النشاط](data-classification-activity-explorer-available-events.md).

**أنشطة وصف الحساسية** **وأنشطة تسمية الاستبقاء** من تطبيقات Office الأصلية، وعميل الوصف الموحد ل Azure حماية البيانات (AIP) والماسح الضوئي، وSharePoint Online، Exchange Online (تسميات الحساسية فقط)، وOneDrive. بعض الأمثلة هي:

- تم تطبيق التسمية
- تم تغيير التسمية (تمت ترقيتها أو تخفيضها أو إزالتها)
- محاكاة التسمية التلقائية
- قراءة الملف

**الماسح الضوئي ل Azure حماية البيانات (AIP) وعملاء AIP**

- الحماية المطبقة
- تم تغيير الحماية
- تمت إزالة الحماية
- تم اكتشاف الملفات

يجمع مستكشف النشاط أيضا **نهج DLP مع** الأحداث من Exchange Online وSharePoint Online وOneDrive وTeams Chat و Channel (معاينة) ومجلدات ومكتبات SharePoint المحلية ومشاركات الملفات المحلية وأجهزة Windows 10 عبر **منع فقدان بيانات نقطة النهاية (DLP).** بعض الأمثلة على الأحداث من أجهزة Windows 10 هي ملف:

- الحذف
- الابداعات
- تم النسخ إلى الحافظة
- تعديل
- قراءه
- المطبوعه
- اعاده تسميه
- تم النسخ إلى مشاركة الشبكة
- تم الوصول إليه بواسطة تطبيق غير مسموح به 

يساعدك فهم الإجراءات التي يتم اتخاذها مع المحتوى الحساس المسمى على معرفة ما إذا كانت عناصر التحكم الموجودة لديك، مثل [نهج تفادي فقدان البيانات في Microsoft Purview](dlp-learn-about-dlp.md) فعالة أم لا. إذا لم يكن الأمر كذلك، أو إذا اكتشفت شيئا غير متوقع، مثل عدد كبير من العناصر المسماة `highly confidential` والمخفضة `general`، يمكنك إدارة نهجك المختلفة واتخاذ إجراءات جديدة لتقييد السلوك غير المرغوب فيه.

> [!NOTE]
> لا يراقب مستكشف النشاط حاليا أنشطة الاستبقاء Exchange Online.

## <a name="see-also"></a>راجع أيضًا

- [التعرّف على تسميات الحساسية](sensitivity-labels.md)
- [التعرف على نهج الاستبقاء وتسميات الاستبقاء](retention.md)
- [التعرّف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)
- [التعرّف على تصنيف البيانات](data-classification-overview.md)
