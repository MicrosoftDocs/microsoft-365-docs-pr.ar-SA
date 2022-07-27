---
title: توفير وصول موفر خدمة الأمان المدار (MSSP)
description: تعرف على التغييرات من مركز حماية Microsoft Defender إلى مدخل Microsoft 365 Defender
keywords: الشروع في العمل مع مدخل Microsoft 365 Defender، Microsoft Defender لـ Office 365، Microsoft Defender لنقطة النهاية، MDO، MDE، جزء واحد من الزجاج، المدخل المتقارب، مدخل الأمان، مدخل أمان defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
manager: dansimp
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.openlocfilehash: 3df43fd4de6bd040db0acd13678434c7302aff5d
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67050692"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>توفير وصول موفر خدمة الأمان المدار (MSSP) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**ينطبق على:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

لتنفيذ حل وصول مفوض متعدد المستأجرين، اتبع الخطوات التالية:

1. تمكين [التحكم في الوصول المستند إلى الدور](/microsoft-365/security/defender-endpoint/rbac) ل Defender لنقطة النهاية عبر مدخل Microsoft 365 Defender والاتصال بمجموعات Azure Active Directory (Azure AD).

2. تكوين [إدارة الاستحقاق للمستخدمين الخارجيين](/azure/active-directory/governance/entitlement-management-external-users) داخل Azure AD Identity Governance لتمكين طلبات الوصول والتوفير.

3. إدارة طلبات الوصول والتدقيقات في [Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>تمكين عناصر التحكم في الوصول المستندة إلى الدور في Microsoft Defender لنقطة النهاية في مدخل Microsoft 365 Defender

1. **إنشاء مجموعات الوصول لموارد MSSP في Customer AAD: Groups**

    سيتم ربط هذه المجموعات بالأدوار التي تقوم بإنشائها في Defender لنقطة النهاية في مدخل Microsoft 365 Defender. للقيام بذلك، في مستأجر AD العميل، قم بإنشاء ثلاث مجموعات. في نهجنا المثال، ننشئ المجموعات التالية:

    - محلل من المستوى 1
    - محلل من المستوى 2
    - الموافقون على محلل MSSP  

2. إنشاء أدوار Defender لنقطة النهاية لمستويات الوصول المناسبة في Customer Defender لنقطة النهاية في Microsoft 365 Defender أدوار المدخل ومجموعاته.

    لتمكين RBAC في مدخل Microsoft 365 Defender العميل، يمكنك الوصول إلى **أدوار نقاط النهاية > & المجموعات > Roles** باستخدام حساب مستخدم له حقوق المسؤول العام أو مسؤول الأمان.

    :::image type="content" source="../../media/mssp-access.png" alt-text="تفاصيل الوصول إلى MSSP في مدخل Microsoft 365 Defender" lightbox="../../media/mssp-access.png":::

    ثم قم بإنشاء أدوار RBAC لتلبية احتياجات طبقة MSSP SOC. ربط هذه الأدوار بمجموعات المستخدمين التي تم إنشاؤها عبر "مجموعات المستخدمين المعينين".

    دوران محتملان:

    - **محللو المستوى 1** <br>
      تنفيذ كافة الإجراءات باستثناء الاستجابة المباشرة وإدارة إعدادات الأمان.

    - **محللو المستوى 2** <br>
      قدرات المستوى 1 مع إضافة إلى [الاستجابة المباشرة](/microsoft-365/security/defender-endpoint/live-response).

    لمزيد من المعلومات، راجع [إدارة الوصول إلى المدخل باستخدام التحكم في الوصول المستند إلى الدور](/microsoft-365/security/defender-endpoint/rbac).

## <a name="configure-governance-access-packages"></a>تكوين حزم الوصول إلى الحوكمة

1. **إضافة MSSP كمؤسسة متصلة في Customer AAD: Identity Governance**

    ستسمح إضافة MSSP كمؤسسة متصلة ل MSSP بالطلب وتوفير الوصول. 

    للقيام بذلك، في مستأجر عميل AD، الوصول إلى Identity Governance: Connected organization. أضف مؤسسة جديدة وابحث عن مستأجر محلل MSSP عبر معرف المستأجر أو المجال. نقترح إنشاء مستأجر AD منفصل لمحللي MSSP.

2. **إنشاء كتالوج موارد في Customer AAD: Identity Governance**

    كتالوجات الموارد هي مجموعة منطقية من حزم الوصول، التي تم إنشاؤها في مستأجر عميل AD.

    للقيام بذلك، في مستأجر AD العميل، الوصول إلى Identity Governance: Catalogs وإضافة **كتالوج جديد**. في مثالنا، سنسميه **MSSP Accesses**.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="كتالوج جديد في مدخل Microsoft 365 Defender" lightbox="../../media/goverance-catalog.png":::


    لمزيد من المعلومات، راجع [إنشاء كتالوج الموارد](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **إنشاء حزم الوصول لموارد MSSP Customer AAD: Identity Governance**

    حزم الوصول هي مجموعة الحقوق والوصول التي سيتم منح الطالب لها عند الموافقة. 

    للقيام بذلك، في مستأجر عميل AD، قم بالوصول إلى Identity Governance: Access Packages، وإضافة **حزمة وصول جديدة**. إنشاء حزمة وصول لموافقي MSSP وكل مستوى محلل. على سبيل المثال، ينشئ تكوين محلل المستوى 1 التالي حزمة وصول:

    - يتطلب من عضو في مجموعة AD **MSSP Analyst Approvers** تخويل طلبات جديدة
    - لديه مراجعات صلاحية الوصول السنوية، حيث يمكن لمحللين SOC طلب ملحق وصول
    - يمكن طلبها فقط من قبل المستخدمين في مستأجر MSSP SOC
    - تنتهي صلاحية الوصول التلقائي بعد 365 يوما

    :::image type="content" source="../../media/new-access-package.png" alt-text="تفاصيل حزمة وصول جديدة في مدخل Microsoft 365 Defender" lightbox="../../media/new-access-package.png":::

    لمزيد من المعلومات، راجع [إنشاء حزمة وصول جديدة](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **توفير ارتباط طلب الوصول إلى موارد MSSP من Customer AAD: Identity Governance**

    يتم استخدام ارتباط مدخل الوصول الخاص بي من قبل محللي MSSP SOC لطلب الوصول عبر حزم الوصول التي تم إنشاؤها. الارتباط دائم، ما يعني أنه يمكن استخدام نفس الارتباط بمرور الوقت للمحللين الجدد. ينتقل طلب المحلل إلى قائمة انتظار للموافقة عليها من قبل **الموافقين على محلل MSSP**.

    :::image type="content" source="../../media/access-properties.png" alt-text="خصائص الوصول في مدخل Microsoft 365 Defender" lightbox="../../media/access-properties.png":::

    يقع الارتباط على صفحة النظرة العامة لكل حزمة وصول.

## <a name="manage-access"></a>إدارة الوصول

1. مراجعة طلبات الوصول وتخويلها في العميل و/أو MSSP myaccess.

    تتم إدارة طلبات الوصول في العميل "الوصول الخاص بي"، من قبل أعضاء مجموعة موافقي محلل MSSP.

    للقيام بذلك، قم بالوصول إلى myaccess الخاصة بالعميل باستخدام: `https://myaccess.microsoft.com/@<Customer Domain>`.

    على سبيل المثال:`https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. الموافقة على الطلبات أو رفضها في قسم **"الموافقات** " في واجهة المستخدم.

     في هذه المرحلة، تم توفير وصول المحللين، ويجب أن يكون كل محلل قادرا على الوصول إلى مدخل Microsoft 365 Defender العميل:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` بالأذونات والأدوار التي تم تعيينها لهم.
