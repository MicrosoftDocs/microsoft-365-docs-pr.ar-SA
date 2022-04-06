---
title: الأذونات في مدخل Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: يمكن للمسؤولين معرفة كيفية إدارة الأذونات في Microsoft 365 Defender لكل المهام ذات الصلة والأمان.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd76eed421f4d926a956508961dc44a643dbb125
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467082"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>الأذونات في مدخل Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تحتاج إلى إدارة سيناريوهات الأمان التي تمتد عبر Microsoft 365 الخدمات. وستحتاج إلى المرونة اللازمة لإعطاء المسؤول المناسب أذونات للأشخاص المناسبين في مؤسستك.

يدعم Microsoft 365 Defender في <https://security.microsoft.com> إدارة الأذونات مباشرة للمستخدمين الذين ينفذون مهام الأمان في Microsoft 365. باستخدام مدخل Microsoft 365 Defender لإدارة الأذونات، يمكنك إدارة الأذونات مركزيا لكل المهام ذات الصلة والأمان.

لإدارة الأذونات في Microsoft 365 Defender، انتقل إلى أذونات & **الأدوار** أو <https://security.microsoft.com/securitypermissions>. يجب أن تكون مسؤولا **عاما** أو عضوا في مجموعة دور **"** إدارة المؤسسة" في Microsoft 365 Defender الإلكتروني. وبشكل خاص، يتيح  دور "إدارة الدور" للمستخدمين عرض مجموعات الدور وإنشاءها وتعديلها في مدخل Microsoft 365 Defender، وبشكل افتراضي، يتم تعيين هذا الدور لمجموعة دور "إدارة المؤسسة" فقط.

> [!NOTE]
> للحصول على معلومات حول الأذونات في مركز التوافق في Microsoft 365، راجع [الأذونات في مركز التوافق في Microsoft 365](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>علاقة الأعضاء والأدوار ومجموعات الأدوار

تستند الأذونات في Microsoft 365 Defender المدخل إلى نموذج أذونات التحكم بالوصول المستند إلى الدور (RBAC). إن RBAC هو نموذج الأذونات نفسه الذي تستخدمه معظم خدمات Microsoft 365، وبالتالي إذا كنت ملما ببنية الأذونات في هذه الخدمات، فإن منح الأذونات في مدخل Microsoft 365 Defender سيكون مألوفا جدا.

يمنح **الدور** الأذونات للقيام مجموعة من المهام.

إن **مجموعة الأدوار** هي مجموعة من الأدوار التي تتيح للأشخاص القيام بواظيفهم في Microsoft 365 Defender المدخل.

تتضمن Microsoft 365 Defender المدخل> مجموعات الدور الافتراضية للمهام والوظائف الأكثر شيوعا التي ستحتاج إلى تعيينها. بشكل عام، نوصي ببساطة بإضافة مستخدمين فرديين **كأعضاء** إلى مجموعات الدور الافتراضية.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="علاقة مجموعة أدوار بأدوارها وأعضائها" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>الأدوار ومجموعات الأدوار في مدخل Microsoft 365 Defender

تتوفر الأنواع التالية من الأدوار ومجموعات  <https://security.microsoft.com/securitypermissions> الأدوار في صفحة الأذونات & في مدخل Microsoft 365 Defender:

- **أدوار Azure AD**: يمكنك عرض الأدوار والمستخدمين المعينين، ولكن لا يمكنك إدارتها مباشرة في مدخل Microsoft 365 Defender. أدوار Azure AD هي أدوار مركزية يتم تعيين أذونات لها **Microsoft 365** الخدمات.

- **البريد & أدوار** التعاون: هذه هي مجموعات الأدوار نفسها المتوفرة في مركز التوافق & الأمان، ولكن يمكنك إدارتها مباشرة في Microsoft 365 Defender المدخل. الأذونات التي تقوم بتعيينها هنا خاصة ببوابة Microsoft 365 Defender و مركز التوافق في Microsoft 365 ومركز توافق الأمان &، ولا تغطي كل الأذونات المطلوبة في أحمال العمل الأخرى Microsoft 365 العمل.

:::image type="content" source="../../media/m365-sc-permissions-and-roles-page.png" alt-text="صفحة الأذونات & في مدخل Microsoft 365 Defender" lightbox="../../media/m365-sc-permissions-and-roles-page.png":::

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>أدوار Azure AD في مدخل Microsoft 365 Defender

عندما تفتح مدخل Microsoft 365 Defender <https://security.microsoft.com> في وتذهب إلى أدوار التعاون في البريد الإلكتروني **&** \> أذونات **أدوار &** \> أدوار **Azure AD** \> **أدوار** (<https://security.microsoft.com/aadpermissions>أو مباشرة إلى ) سترى أدوار Azure AD الموضحة في هذا القسم.

عند تحديد دور، تظهر القائمة من القائمة من خلال القائمة من القائمة المنشرة بالتفاصيل التي تحتوي على وصف الدور وواجبات المستخدم. ولكن لإدارة هذه الواجبات، ستحتاج إلى النقر فوق إدارة الأعضاء في **Azure AD** في عناصر منتبة التفاصيل.

:::image type="content" source="../../media/permissions-manage-in-azure-ad-link.png" alt-text="الارتباط لإدارة الأذونات في Azure Active Directory" lightbox="../../media/permissions-manage-in-azure-ad-link.png":::

لمزيد من المعلومات، راجع [عرض أدوار المسؤولين وتعيينها في Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|الدور|الوصف|
|---|---|
|**المسؤول العام**|الوصول إلى جميع الميزات الإدارية في Microsoft 365 الخدمات. يمكن للمسؤولين العامين فقط تعيين أدوار المسؤولين الآخرين. لمزيد من المعلومات، راجع [المسؤول العام / مسؤول الشركة](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**مسؤول بيانات التوافق**|تعقب بيانات مؤسستك عبر Microsoft 365، وتأكد من أنها محمية، واحصل على تحليلات حول أي مشاكل للمساعدة في الحد من المخاطر. لمزيد من المعلومات، راجع [مسؤول بيانات التوافق](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**مسؤول التوافق**|ساعد مؤسستك على البقاء متوافقا مع أي متطلبات تنظيمية، وإدارة حالات eDiscovery، والحفاظ على سياسات إدارة البيانات عبر Microsoft 365 والهويات والتطبيقات. لمزيد من المعلومات، راجع [مسؤول التوافق](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**عامل تشغيل الأمان**|عرض التهديدات النشطة التي تواجه المستخدمين والأجهزة والمحتوى Microsoft 365 والرد عليها. لمزيد من المعلومات، راجع [عامل تشغيل الأمان](/azure/active-directory/roles/permissions-reference#security-operator).|
|**قارئ الأمان**|يمكنك عرض التهديدات النشطة Microsoft 365 المستخدمين والأجهزة والمحتوى الخاص بك، ولكن (على عكس عامل تشغيل الأمان) ليس لديهم الأذونات اللازمة للاستجابة من خلال اتخاذ إجراء ما. لمزيد من المعلومات، راجع [قارئ الأمان](/azure/active-directory/roles/permissions-reference#security-reader).|
|**مسؤول الأمان**|يمكنك التحكم في الأمان العام في مؤسستك من خلال إدارة سياسات الأمان ومراجعة تحليلات الأمان والتقارير عبر منتجات Microsoft 365، والبقاء على مستوى السرعة على مستوى المخاطر. لمزيد من المعلومات، راجع [مسؤول الأمان](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**القارئ العام**|إصدار القراءة فقط **من مسؤول عمومي.** عرض كل الإعدادات والمعلومات الإدارية عبر Microsoft 365. لمزيد من المعلومات، راجع [القارئ العام](/azure/active-directory/roles/permissions-reference#global-reader).|
|**مسؤول محاكاة الهجمات**|إنشاء جميع جوانب محاكاة الهجمات وإدارتها، و تشغيل/جدولة محاكاة، ومراجعة نتائج المحاكاة.[](attack-simulation-training.md) لمزيد من المعلومات، راجع [مسؤول محاكاة الهجمات](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**كاتب تحميل الهجوم**|قم بإنشاء تحميلات الهجوم ولكن ليس في الواقع تشغيلها أو جدولتها. لمزيد من المعلومات، راجع ["كاتب تحميل الهجوم](/azure/active-directory/roles/permissions-reference#attack-payload-author)".|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>استخدام & الإلكتروني في مدخل Microsoft 365 Defender الإلكتروني

عندما تفتح مدخل Microsoft 365 Defender <https://security.microsoft.com> في وتذهب إلى أدوار تعاون البريد الإلكتروني **&** \> أذونات **&** \> أدوار البريد الإلكتروني **& أدوار** \> التعاون **الأدوار (**<https://security.microsoft.com/emailandcollabpermissions>أو مباشرة إلى) سترى مجموعات الأدوار نفسها المتوفرة في مركز التوافق ل & الأمان.

للحصول على معلومات كاملة حول مجموعات الدور هذه، راجع الأذونات في [مركز التوافق & الأمان](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>تعديل دور & الإلكتروني في مدخل Microsoft 365 Defender الإلكتروني

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى البريد الإلكتروني & **أدوار** \> التعاون الأذونات & **أدوار** \> البريد الإلكتروني & **أدوار التعاون**\>. الانتقال مباشرة إلى صفحة **الأذونات** ، استخدم <https://security.microsoft.com/emailandcollabpermissions>.

2. في صفحة **الأذونات** ، حدد مجموعة الدور التي تريد تعديلها من القائمة. يمكنك النقر فوق رأس عمود  الاسم لفرز القائمة حسب الاسم، أو يمكنك النقر فوق **أيقونة بحث** ![في البحث.](../../media/m365-cc-sc-search-icon.png) للعثور على مجموعة الدور.

3. في الجزء المناير التفاصيل لمجموعة الدور الذي يظهر، انقر فوق **تحرير** في **المقطع** الأعضاء.

4. في **الصفحة تحرير اختيار** الأعضاء التي تظهر، قم بوا إحدى الخطوات التالية:
   - إذا لم يكن هناك أعضاء مجموعة دور، انقر **فوق اختيار أعضاء**.
   - إذا كان هناك أعضاء موجودون في مجموعة الدور، انقر فوق **تحرير**

5. في خيار **اختيار الأعضاء** الذي يظهر، قم بوا إحدى الخطوات التالية:

   - انقر **فوق إضافة**. في قائمة المستخدمين التي تظهر، حدد مستخدما واحدا أو أكثر. أو، يمكنك النقر فوق **أيقونة** ![البحث عن.](../../media/m365-cc-sc-search-icon.png) للعثور على المستخدمين وتحديدهم.

     عند تحديد المستخدمين الذين تريد إضافتهم، انقر فوق **إضافة**.

   - انقر **فوق إزالة**. حدد عضوا واحدا أو أكثر من الأعضاء  الموجودين. أو، يمكنك النقر فوق **أيقونة** ![البحث عن.](../../media/m365-cc-sc-search-icon.png) للعثور على الأعضاء وتحديدهم.

     عند تحديد المستخدمين الذين تريد إزالتهم، انقر فوق **إزالة**.

6. مرة أخرى على **خيار اختيار الأعضاء** ، انقر فوق **تم**.

7. بالعودة إلى **الصفحة تحرير اختيار** الأعضاء، انقر فوق **حفظ**.

8. بالعودة إلى الجزء المناير التفاصيل لمجموعة الدور، انقر فوق **تم**.
