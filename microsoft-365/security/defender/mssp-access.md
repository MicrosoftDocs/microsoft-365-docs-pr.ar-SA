---
title: توفير الوصول إلى موفر خدمة الأمان المدار (MSSP)
description: تعرف على التغييرات من مركز حماية Microsoft Defender إلى مدخل Microsoft 365 Defender
keywords: بدء استخدام مدخل Microsoft 365 Defender، Microsoft Defender لـ Office 365، Microsoft Defender لنقطة النهاية، MDO، MDE، جزء واحد من الزجاج، مدخل متقارب، مدخل الأمان، مدخل أمان defender
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: f0148a8bfe18c7636e95ceae7b268cc70b2e58ed
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500398"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>توفير الوصول إلى موفر خدمة الأمان المدار (MSSP) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**ينطبق على:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

لتنفيذ حل وصول مفوض متعدد المستأجرين، نفذ الخطوات التالية:

1. قم [بتمكين التحكم بالوصول](/windows/security/threat-protection/microsoft-defender-atp/rbac) المستند إلى الدور ل Defender for Endpoint عبر Microsoft 365 Defender الوصول والاتصال مع مجموعات Azure Active Directory (Azure AD).

2. تكوين حزم [الوصول إلى الإدارة](/azure/active-directory/governance/identity-governance-overview) لطلب الوصول وتوفيره.

3. إدارة طلبات الوصول والتدقيقات في [Microsoft Myaccess.](/azure/active-directory/governance/entitlement-management-request-approve)

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>تمكين عناصر التحكم بالوصول المستندة إلى الدور في Microsoft Defender لنقطة النهاية في Microsoft 365 Defender المدخل

1. **إنشاء مجموعات وصول إلى موارد MSSP في AAD (دليل Azure النشط): المجموعات**

    سيتم ربط هذه المجموعات بالأدوار التي تقوم بإنشاتها في Defender for Endpoint في Microsoft 365 Defender المدخل. للقيام بذلك، في مستأجر AD للعميل، قم بإنشاء ثلاث مجموعات. في نهج المثال، نقوم بإنشاء المجموعات التالية:

    - محلل من المستوى 1
    - محلل من المستوى 2
    - الموافقون على محللي MSSP  

2. إنشاء أدوار Defender لنقطة النهاية لمستويات الوصول المناسبة في Customer Defender لنقطة النهاية في Microsoft 365 Defender المدخل والمجموعات.

    لتمكين RBAC في مدخل Microsoft 365 Defender العميل، يمكنك الوصول إلى **الأذونات > أدوار نقاط النهاية & مجموعات > الأدوار** باستخدام حساب مستخدم مع حقوق المسؤول العام أو مسؤول الأمان.

    :::image type="content" source="../../media/mssp-access.png" alt-text="تفاصيل الوصول إلى MSSP في مدخل Microsoft 365 Defender" lightbox="../../media/mssp-access.png":::

    بعد ذلك، قم بإنشاء أدوار RBAC لتلبية احتياجات طبقة MSSP SOC. ربط هذه الأدوار ب مجموعات المستخدمين التي تم إنشاؤها عبر "مجموعات المستخدمين المعينين".

    دوران محتملان:

    - **محللو المستوى 1** <br>
      قم بتنفيذ جميع الإجراءات باستثناء الاستجابة المباشرة وإدارة إعدادات الأمان.

    - **محللو المستوى 2** <br>
      إمكانات المستوى 1 مع إضافة الاستجابة [المباشرة](/windows/security/threat-protection/microsoft-defender-atp/live-response)

    لمزيد من المعلومات، راجع [استخدام التحكم بالوصول المستند إلى الدور](/windows/security/threat-protection/microsoft-defender-atp/rbac).

## <a name="configure-governance-access-packages"></a>تكوين حزم الوصول إلى الإدارة

1. **إضافة MSSP كمنظمة متصلة في AAD (دليل Azure النشط): إدارة الهوية**

    ستسمح إضافة MSSP كمنظمة متصلة ل MSSP بطلب والوصول إليها. 

    للقيام بذلك، في مستأجر AD للعميل، يمكنك الوصول إلى إدارة الهوية: المؤسسة المتصلة. أضف مؤسسة جديدة وابحث عن مستأجر محلل MSSP الخاص بك عبر "اسم المستأجر" أو "المجال". نقترح إنشاء مستأجر AD منفصل لمحللي MSSP.

2. **إنشاء كتالوج موارد في AAD (دليل Azure النشط): إدارة الهوية**

    كتالوجات الموارد عبارة عن مجموعة منطقية من حزم الوصول، تم إنشاؤها في مستأجر AD للعميل.

    للقيام بذلك، في مستأجر AD للعميل، يمكنك الوصول إلى إدارة الهوية: الكتالوجات وإضافة **كتالوج جديد**. في مثالنا، سنسميه **MSSP Accesses**.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="كتالوج جديد في مدخل Microsoft 365 Defender" lightbox="../../media/goverance-catalog.png":::


    لمزيد من المعلومات، راجع [إنشاء كتالوج موارد](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **إنشاء حزم الوصول إلى موارد MSSP AAD (دليل Azure النشط): إدارة الهوية**

    حزم Access هي مجموعة من الحقوق والوصولات التي سيتم منحها من قبل طالب عند الموافقة. 

    للقيام بذلك، في مستأجر AD للعميل، يمكنك الوصول إلى إدارة الهوية: حزم Access وإضافة **حزمة Access جديدة**. إنشاء حزمة وصول لموافقي MSSP وكل مستوى محلل. على سبيل المثال، ينشئ تكوين محلل المستوى 1 التالي حزمة وصول تقوم بما يلي:

    - يتطلب من عضو في مجموعة AD **الموافقون على محللي MSSP** تخويل طلبات جديدة
    - لديها مراجعات وصول سنوية، حيث يمكن لمحللين SOC طلب ملحق الوصول
    - يمكن فقط طلبها من قبل المستخدمين في مستأجر MSSP SOC
    - تنتهي صلاحية Access التلقائي بعد 365 يوما

    :::image type="content" source="../../media/new-access-package.png" alt-text="تفاصيل حزمة وصول جديدة في مدخل Microsoft 365 Defender" lightbox="../../media/new-access-package.png":::

    لمزيد من المعلومات، راجع [إنشاء حزمة وصول جديدة](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **توفير ارتباط طلب الوصول إلى موارد MSSP من AAD (دليل Azure النشط): إدارة الهوية**

    يستخدم محللو MSSP SOC ارتباط مدخل الوصول الخاص ب MsSP لطلب الوصول عبر حزم الوصول التي تم إنشاؤها. الارتباط دائم، مما يعني أنه قد يتم استخدام الارتباط نفسه مع مرور الوقت للمحللين الجدد. يدخل طلب المحلل في قائمة انتظار للموافقة عليه من قبل **الموافقين على محللي MSSP**.

    :::image type="content" source="../../media/access-properties.png" alt-text="خصائص الوصول في مدخل Microsoft 365 Defender" lightbox="../../media/access-properties.png":::

    يقع الارتباط في صفحة نظرة عامة لكل حزمة وصول.

## <a name="manage-access"></a>إدارة الوصول

1. راجع طلبات الوصول و/أو تخويلها في Myaccess الخاصة بالعملاء و/أو MSSP.

    يتم إدارة طلبات الوصول في العميل My Access، من قبل أعضاء مجموعة الموافقين لمحللي MSSP.

    للقيام بذلك، يمكنك الوصول إلى myaccess الخاصة للعميل باستخدام: `https://myaccess.microsoft.com/@<Customer Domain>`.

    على سبيل المثال:`https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. الموافقة على الطلبات أو **رفضها** في الموافقات من واجهة المستخدم.

     في هذه المرحلة، تم توفير وصول المحللين، ويجب أن يتمكن كل محلل من الوصول إلى مدخل Microsoft 365 Defender العميل:

    `https://security.microsoft.com/?tid=<CustomerTenantId>` مع الأذونات والأدوار التي تم تعيينها.

> [!IMPORTANT]
> يسمح الوصول المفوض Microsoft Defender لنقطة النهاية في Microsoft 365 Defender الوصول حاليا إلى مستأجر واحد لكل نافذة مستعرض.
