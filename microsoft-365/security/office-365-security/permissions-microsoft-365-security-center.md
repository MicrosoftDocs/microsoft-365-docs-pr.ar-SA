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
description: يمكن للمسؤولين معرفة كيفية إدارة الأذونات في مدخل Microsoft 365 Defender لجميع المهام المتعلقة بالأمان.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3381d3eb823b818aec01a181f176cb56f6af310c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939180"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>الأذونات في مدخل Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تحتاج إلى إدارة سيناريوهات الأمان التي تمتد عبر جميع خدمات Microsoft 365. وتحتاج إلى المرونة لمنح أذونات المسؤول المناسبة للأشخاص المناسبين في مؤسستك.

يدعم مدخل Microsoft 365 Defender في <https://security.microsoft.com> إدارة الأذونات مباشرة للمستخدمين الذين يقومون بمهام الأمان في Microsoft 365. باستخدام مدخل Microsoft 365 Defender لإدارة الأذونات، يمكنك إدارة الأذونات مركزيا لجميع المهام المتعلقة بالأمان.

لإدارة الأذونات في مدخل Microsoft 365 Defender، انتقل إلى **الأذونات & الأدوار** أو <https://security.microsoft.com/securitypermissions>. يجب أن تكون **مسؤولا عاما** أو عضوا في مجموعة دور **إدارة المؤسسة** في مدخل Microsoft 365 Defender. على وجه التحديد، يسمح دور **"إدارة الدور**" للمستخدمين بعرض مجموعات الأدوار وإنشاءها وتعديلها في مدخل Microsoft 365 Defender، وبشكل افتراضي، يتم تعيين هذا الدور إلى مجموعة أدوار **إدارة المؤسسة** فقط.

> [!NOTE]
> للحصول على معلومات حول الأذونات في مدخل توافق Microsoft Purview، راجع [الأذونات في مدخل توافق Microsoft Purview](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>علاقة الأعضاء والأدوار ومجموعات الأدوار

تستند الأذونات في مدخل Microsoft 365 Defender إلى نموذج أذونات التحكم في الوصول استنادا إلى الدور (RBAC). RBAC هو نفس نموذج الأذونات الذي تستخدمه معظم خدمات Microsoft 365، لذلك إذا كنت على دراية ببنية الأذونات في هذه الخدمات، فإن منح الأذونات في مدخل Microsoft 365 Defender سيكون مألوفا جدا.

يمنح **الدور** الأذونات للقيام بمجموعة من المهام.

**مجموعة الأدوار** هي مجموعة من الأدوار التي تتيح للأشخاص القيام بوظائفهم في مدخل Microsoft 365 Defender.

يتضمن مدخل Microsoft 365 Defender> مجموعات الأدوار الافتراضية للمهام والوظائف الأكثر شيوعا التي ستحتاج إلى تعيينها. بشكل عام، نوصي ببساطة بإضافة مستخدمين فرديين **كأعضاء** إلى مجموعات الأدوار الافتراضية.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="علاقة مجموعة الأدوار بأدوارها وأعضائها" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>الأدوار ومجموعات الأدوار في مدخل Microsoft 365 Defender

تتوفر الأنواع التالية من الأدوار ومجموعات الأدوار في صفحة **"الأذونات & الأدوار**" في مدخل <https://security.microsoft.com/securitypermissions> Microsoft 365 Defender:

- **أدوار Azure AD**: يمكنك عرض الأدوار والمستخدمين المعينين، ولكن لا يمكنك إدارتها مباشرة في مدخل Microsoft 365 Defender. أدوار Azure AD هي أدوار مركزية تعين أذونات **لجميع** خدمات Microsoft 365.

- **البريد الإلكتروني & أدوار التعاون**: هذه هي نفس مجموعات الأدوار المتوفرة في مركز توافق & الأمان، ولكن يمكنك إدارتها مباشرة في مدخل Microsoft 365 Defender. الأذونات التي تقوم بتعيينها هنا خاصة بمدخل Microsoft 365 Defender ومدخل توافق Microsoft Purview ومركز التوافق & الأمان، ولا تغطي جميع الأذونات المطلوبة في أحمال عمل Microsoft 365 الأخرى.

:::image type="content" source="../../media/m365-sc-permissions-and-roles-page.png" alt-text="صفحة أدوار & الأذونات في مدخل Microsoft 365 Defender" lightbox="../../media/m365-sc-permissions-and-roles-page.png":::

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>أدوار Azure AD في مدخل Microsoft 365 Defender

عند فتح مدخل <https://security.microsoft.com> Microsoft 365 Defender في **البريد الإلكتروني & أدوار** \> التعاون **& أدوار** \> **أدوار** \> Azure AD **(أو** مباشرة إلى<https://security.microsoft.com/aadpermissions>) سترى أدوار Azure AD الموضحة في هذا القسم.

عند تحديد دور، تظهر قائمة منبثقة للتفاصيل تحتوي على وصف الدور وتعيينات المستخدم. ولكن لإدارة هذه التعيينات، تحتاج إلى النقر فوق **"إدارة الأعضاء" في Azure AD** في القائمة المنبثقة للتفاصيل.

:::image type="content" source="../../media/permissions-manage-in-azure-ad-link.png" alt-text="الارتباط لإدارة الأذونات في Azure Active Directory" lightbox="../../media/permissions-manage-in-azure-ad-link.png":::

لمزيد من المعلومات، راجع [عرض أدوار المسؤول وتعيينها في Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|دور|الوصف|
|---|---|
|**المسؤول العام**|الوصول إلى جميع الميزات الإدارية في جميع خدمات Microsoft 365. يمكن للمسؤولين العموميين فقط تعيين أدوار المسؤولين الآخرين. لمزيد من المعلومات، راجع [المسؤول العام / مسؤول الشركة](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**مسؤول بيانات التوافق**|تعقب بيانات مؤسستك عبر Microsoft 365، وتأكد من أنها محمية، واحصل على رؤى حول أي مشكلات للمساعدة في التخفيف من المخاطر. لمزيد من المعلومات، راجع [مسؤول بيانات التوافق](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**مسؤول التوافق**|ساعد مؤسستك على البقاء متوافقة مع أي متطلبات تنظيمية، وإدارة حالات eDiscovery، والحفاظ على نهج حوكمة البيانات عبر مواقع Microsoft 365 والهويات والتطبيقات. لمزيد من المعلومات، راجع [مسؤول التوافق](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**عامل تشغيل الأمان**|عرض التهديدات النشطة للمستخدمين والأجهزة والمحتوى Microsoft 365 لديك والتحقيق فيها والاستجابة لها. لمزيد من المعلومات، راجع [عامل تشغيل الأمان](/azure/active-directory/roles/permissions-reference#security-operator).|
|**قارئ الأمان**|عرض التهديدات النشطة للمستخدمين والأجهزة والمحتوى Microsoft 365 والتحقيق فيها، ولكن (على عكس عامل تشغيل الأمان) ليس لديهم أذونات للاستجابة من خلال اتخاذ إجراء. لمزيد من المعلومات، راجع ["قارئ الأمان](/azure/active-directory/roles/permissions-reference#security-reader)".|
|**مسؤول الأمان**|يمكنك التحكم في الأمان العام لمؤسستك من خلال إدارة نهج الأمان، ومراجعة تحليلات الأمان والتقارير عبر منتجات Microsoft 365، والبقاء على اطلاع سريع على مشهد التهديد. لمزيد من المعلومات، راجع [مسؤول الأمان](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**القارئ العمومي**|الإصدار للقراءة فقط من دور **مسؤول عمومي**. عرض كافة الإعدادات والمعلومات الإدارية عبر Microsoft 365. لمزيد من المعلومات، راجع ["القارئ العمومي](/azure/active-directory/roles/permissions-reference#global-reader)".|
|**مسؤول محاكاة الهجوم**|إنشاء وإدارة جميع جوانب إنشاء [محاكاة الهجوم](attack-simulation-training.md) ، وبدء/جدولة المحاكاة، ومراجعة نتائج المحاكاة. لمزيد من المعلومات، راجع [مسؤول محاكاة الهجوم](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**كاتب حمولة الهجوم**|إنشاء حمولات الهجوم ولكن ليس في الواقع إطلاقها أو جدولتها. لمزيد من المعلومات، راجع [كاتب حمولة الهجوم](/azure/active-directory/roles/permissions-reference#attack-payload-author).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>البريد الإلكتروني & أدوار التعاون في مدخل Microsoft 365 Defender

عند فتح مدخل <https://security.microsoft.com> Microsoft 365 Defender في **البريد الإلكتروني & أدوار** \> التعاون **& أدوار** \> **البريد الإلكتروني & أدوار** \> التعاون (أو مباشرة إلى  <https://security.microsoft.com/emailandcollabpermissions>) سترى نفس مجموعات الأدوار المتوفرة في مركز التوافق & الأمان.

للحصول على معلومات كاملة حول مجموعات الأدوار هذه، راجع [الأذونات في مركز توافق & الأمان](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>تعديل عضوية دور التعاون & البريد الإلكتروني في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى أدوار \> **التعاون & البريد الإلكتروني** **& أدوار** \> **البريد الإلكتروني & أدوار** \> التعاون. للانتقال مباشرة إلى صفحة **الأذونات** ، استخدم <https://security.microsoft.com/emailandcollabpermissions>.

2. في صفحة **"الأذونات"** ، حدد مجموعة الأدوار التي تريد تعديلها من القائمة. يمكنك النقر فوق رأس عمود **"الاسم**" لفرز القائمة حسب الاسم، أو يمكنك النقر فوق أيقونة **البحث**![.](../../media/m365-cc-sc-search-icon.png) للعثور على مجموعة الأدوار.

3. في القائمة المنبثقة لتفاصيل مجموعة الأدوار التي تظهر، انقر فوق **"تحرير"** في المقطع **"الأعضاء** ".

4. في صفحة **"اختيار الأعضاء"** التي تظهر في "التحرير"، نفذ إحدى الخطوات التالية:
   - إذا لم يكن هناك أعضاء مجموعة أدوار، فانقر فوق **"اختيار الأعضاء**".
   - إذا كان هناك أعضاء مجموعة أدوار موجودين، فانقر فوق **"تحرير"**

5. في القائمة المنبثقة **"اختيار الأعضاء** " التي تظهر، نفذ إحدى الخطوات التالية:

   - انقر فوق **"إضافة**". في قائمة المستخدمين التي تظهر، حدد مستخدما واحدا أو أكثر. أو، يمكنك النقر فوق **أيقونة البحث**![.](../../media/m365-cc-sc-search-icon.png) للبحث عن المستخدمين وتحديدهم.

     عند تحديد المستخدمين الذين تريد إضافتهم، انقر فوق **"إضافة**".

   - انقر فوق **"إزالة**". حدد عضوا واحدا أو أكثر من الأعضاء الموجودين. أو، يمكنك النقر فوق **أيقونة البحث**![.](../../media/m365-cc-sc-search-icon.png) للبحث عن الأعضاء وتحديدهم.

     عند تحديد المستخدمين الذين تريد إزالتهم، انقر فوق **"إزالة**".

6. مرة أخرى في القائمة المنبثقة **"اختيار الأعضاء** "، انقر فوق **"تم**".

7. بالعودة إلى صفحة **"التحرير" لاختيار الأعضاء** ، انقر فوق **"حفظ**".

8. مرة أخرى على القائمة المنبثقة لتفاصيل مجموعة الأدوار، انقر فوق **"تم**".
