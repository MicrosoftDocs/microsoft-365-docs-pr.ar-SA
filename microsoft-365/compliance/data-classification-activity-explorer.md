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
description: يتيح لك "مستكشف النشاط" الاطلاع على الإجراءات التي يقوم المستخدمون باتخاذها على المحتوى المسمى وتصفيتها.
ms.openlocfilehash: 93cd3910a79b136d95ba46fa79940d379340cf75
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63567192"
---
# <a name="get-started-with-activity-explorer"></a>بدء استخدام مستكشف النشاط

[تمنحك علامة](data-classification-overview.md) التبويب نظرة [](data-classification-content-explorer.md) عامة حول تصنيف البيانات ومستكشف المحتوى إمكانية رؤية المحتوى الذي تم اكتشافه ونسميته، وأين يوجد هذا المحتوى. يستكشف مستكشف النشاط مجموعة الوظائف هذه من خلال السماح لك بمراقبة ما يتم القيام به باستخدام المحتوى المسمى. يوفر "مستكشف النشاط" طريقة عرض تاريخية لأنشطة على المحتوى المسمى. يتم تجميع معلومات النشاط من Microsoft 365 التدقيق الموحدة وتحويلها وجعلها متوفرة في واجهة مستخدم مستكشف النشاط. تقارير مستكشف النشاط حول بيانات تصل قيمتها إلى 30 يوما.

![نظرة عامة حول نشاط لقطة شاشة العنصر النائب.](../media/data-classification-activity-explorer-1.png)

هناك أكثر من 30 عامل تصفية مختلف متوفر للاستخدام، وبعضها:

- نطاق التاريخ
- نوع النشاط
- الموقع
- User
- تسمية الحساسية
- تسمية الاستبقاء
- مسار الملف
- نهج DLP



## <a name="prerequisites"></a>المتطلبات الأساسية

يجب تعيين ترخيص لكل حساب يمكن الوصول إليه واستخدامه لتصنيف البيانات من أحد هذه الاشتراكات:

- Microsoft 365 (E5)
- Office 365 (E5)
- الوظائف الإضافية للتوافق المتقدم (E5)
- الوظائف الإضافية المتقدمة لذكاء المخاطر (E5)
- Microsoft 365 E5/A5 إدارة & المعلومات
- Microsoft 365 E5/توافق A5

### <a name="permissions"></a>الأذونات

يجب تعيين عضوية إلى حساب بشكل صريح في أي مجموعة من مجموعات الدور هذه أو منحه الدور بشكل صريح.

### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم بالوصول.

فيما يلي قائمة بأدوار حماية البيانات في Microsoft (MIP) في المعاينة. لمعرفة المزيد حولها، راجع [الأدوار في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- مسؤول حماية المعلومات
- محلل حماية المعلومات
- حماية المعلوماتمحقق
- قارئ حماية المعلومات

فيما يلي قائمة مجموعات دور MIP التي تكون في المعاينة. لمعرفة المزيد حول، راجع [مجموعات الدور في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية المعلومات
- مسؤولو حماية المعلومات
- محللو حماية المعلومات
- الباحثون عن حماية المعلومات
- قراء حماية المعلومات

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Microsoft 365 الدور**

- المسؤول العام
- مسؤول التوافق
- مسؤول الأمان
- مسؤول بيانات التوافق

**Microsoft 365 الأدوار**

- مسؤول التوافق
- مسؤول الأمان
- قارئ الأمان

## <a name="activity-types"></a>أنواع الأنشطة

يجمع مستكشف النشاط معلومات النشاط من سجلات التدقيق على مصادر أنشطة متعددة. للحصول على مزيد من المعلومات المفصلة حول نشاط التسمية الذي يتم الوصول به إلى "مستكشف النشاط"، راجع أحداث التسمية [المتوفرة في "مستكشف النشاط](data-classification-activity-explorer-available-events.md)".

أنشطة **تسمية** الحساسية وأنشطة تسمية  الاستبقاء من تطبيقات Office الأصلية، و"Azure Information Protection"، و"SharePoint Online"، و"Exchange Online" (تسميات الحساسية فقط)، OneDrive. بعض الأمثلة هي:

- تم تطبيق التسمية
- تم تغيير التسمية (تمت ترقيتها أو تخفيضها أو إزالتها)
- محاكاة التصفية التلقائية
- قراءة الملف

**الماسح الضوئي ل Azure Information Protection (AIP) والعملاء AIP**

- تم تطبيق الحماية
- تم تغيير الحماية
- تمت إزالة الحماية
- الملفات التي تم اكتشافها

يجمع مستكشف النشاط أيضا نهج **DLP** مع الأحداث من Exchange Online و SharePoint عبر الإنترنت و OneDrive و Teams الدردشة و القناة (معاينة) ومجلدات ومكتبات SharePoint المحلي، وملفات مشاركة المحلي، وأجهزة Windows 10 عبر **منع فقدان بيانات نقطة النهاية (DLP)**. بعض الأمثلة على الأحداث من Windows 10 هي ملفات:

- عمليات الحذف
- الإنشاءات
- تم النسخ إلى الحافظة
- تاريخ التعديل
- قراءة
- مطبوع
- تمت إعادة تسميته
- تم النسخ إلى مشاركة الشبكة
- تم الوصول إليه بواسطة تطبيق غير مسموح به 

يساعدك فهم الإجراءات التي يتم اتخاذها باستخدام المحتوى المسمى بالحساسية على معرفة ما إذا كانت عناصر التحكم الموجودة لديك، مثل سياسات [](dlp-learn-about-dlp.md) منع فقدان البيانات فعالة أم لا. إذا لم `highly confidential` `general`يكن الأمر كذلك، أو إذا اكتشفت شيئا غير متوقع، مثل عدد كبير من العناصر التي تم وصفها بالتسمية التي تم تخفيض تصنيفها ، يمكنك إدارة مختلف سياساتك واتخاذ إجراءات جديدة لتقييد السلوك غير المتوقع.

> [!NOTE]
> لا يقوم مستكشف النشاط حاليا بمراقبة أنشطة الاستبقاء Exchange Online.

## <a name="see-also"></a>راجع أيضًا

- [التعرّف على تسميات الحساسية](sensitivity-labels.md)
- [التعرف على سياسات الاستبقاء وتسميات الاستبقاء](retention.md)
- [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)
- [التعرف على تصنيف البيانات](data-classification-overview.md)
