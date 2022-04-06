---
title: منح حق الوصول إلى موفر خدمة الأمان المدار (MSSP)
description: اتخاذ الخطوات اللازمة لتكوين تكامل MSSP مع Microsoft Defender لنقطة النهاية
keywords: موفر خدمة الأمان المدار، mssp، تكوين، تكامل
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: cb92b67b3f19c578d12eb9673d2f80d5fadd131f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63583138"
---
# <a name="grant-managed-security-service-provider-mssp-access-preview"></a>منح موفر خدمة الأمان المدار (MSSP) حق الوصول (معاينة)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

لتنفيذ حل وصول مفوض متعدد المستأجرين، نفذ الخطوات التالية:

1. قم [بتمكين التحكم بالوصول المستند إلى الدور](rbac.md) في Defender for Endpoint والاتصال بالمجموعات Active Directory (AD).

2. تكوين حزم [الوصول إلى الإدارة](/azure/active-directory/governance/identity-governance-overview) لطلب الوصول وتوفيره.

3. إدارة طلبات الوصول والتدقيقات في [Microsoft Myaccess.](/azure/active-directory/governance/entitlement-management-request-approve)

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint"></a>تمكين عناصر التحكم بالوصول المستندة إلى الدور في Microsoft Defender لنقطة النهاية

1. **إنشاء مجموعات وصول إلى موارد MSSP في AAD (دليل Azure النشط): المجموعات**

    سيتم ربط هذه المجموعات بالأدوار التي تقوم بإنشاتها في Defender for Endpoint. للقيام بذلك، في مستأجر AD للعميل، قم بإنشاء ثلاث مجموعات. في نهج المثال، نقوم بإنشاء المجموعات التالية:

    - محلل من المستوى 1
    - محلل من المستوى 2
    - الموافقون على محللي MSSP

2. إنشاء أدوار Defender لنقطة النهاية لمستويات الوصول المناسبة في Customer Defender لنقطة النهاية.

    لتمكين RBAC في مدخل Microsoft 365 Defender العميل، يمكنك الوصول إلى الإعدادات > أذونات **>** الأدوار و"تشغيل الأدوار"، من حساب مستخدم مع حقوق المسؤول العام أو مسؤول الأمان.

    ![صورة الوصول إلى MSSP.](images/mssp-access.png)

    بعد ذلك، قم بإنشاء أدوار RBAC لتلبية احتياجات طبقة MSSP SOC. ربط هذه الأدوار ب مجموعات المستخدمين التي تم إنشاؤها عبر "مجموعات المستخدمين المعينين".

    دوران محتملان:

    - **محللو المستوى 1**

      قم بتنفيذ جميع الإجراءات باستثناء الاستجابة المباشرة وإدارة إعدادات الأمان.

    - **محللو المستوى 2**

      إمكانات المستوى 1 مع إضافة الاستجابة [المباشرة](live-response.md)

    لمزيد من المعلومات، راجع [استخدام التحكم بالوصول المستند إلى الدور](rbac.md).

## <a name="configure-governance-access-packages"></a>تكوين حزم الوصول إلى الإدارة

1. **إضافة MSSP كمنظمة متصلة في AAD (دليل Azure النشط): إدارة الهوية**

    ستسمح إضافة MSSP كمنظمة متصلة ل MSSP بطلب والوصول إليها.

    للقيام بذلك، في مستأجر AD للعميل، يمكنك الوصول إلى إدارة الهوية: المؤسسة المتصلة. أضف مؤسسة جديدة وابحث عن مستأجر محلل MSSP الخاص بك عبر "اسم المستأجر" أو "المجال". نقترح إنشاء مستأجر AD منفصل لمحللي MSSP.

2. **إنشاء كتالوج موارد في AAD (دليل Azure النشط): إدارة الهوية**

    كتالوجات الموارد عبارة عن مجموعة منطقية من حزم الوصول، تم إنشاؤها في مستأجر AD للعميل.

    للقيام بذلك، في مستأجر AD للعميل، يمكنك الوصول إلى إدارة الهوية: الكتالوجات وإضافة **كتالوج جديد**. في مثالنا، سنسميه **MSSP Accesses**.

    ![صورة لكتالوج جديد.](images/goverance-catalog.png)

    لمزيد من المعلومات، راجع [إنشاء كتالوج موارد](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **إنشاء حزم الوصول إلى موارد MSSP AAD (دليل Azure النشط): إدارة الهوية**

    حزم Access هي مجموعة من الحقوق والوصولات التي سيتم منحها من قبل طالب عند الموافقة.

    للقيام بذلك، في مستأجر AD للعميل، يمكنك الوصول إلى إدارة الهوية: حزم Access وإضافة **حزمة Access جديدة**. إنشاء حزمة وصول لموافقي MSSP وكل مستوى محلل. على سبيل المثال، ينشئ تكوين محلل المستوى 1 التالي حزمة وصول تقوم بما يلي:

    - يتطلب من عضو في مجموعة AD **الموافقون على محللي MSSP** تخويل طلبات جديدة
    - لديها مراجعات وصول سنوية، حيث يمكن لمحللين SOC طلب ملحق الوصول
    - يمكن فقط طلبها من قبل المستخدمين في مستأجر MSSP SOC
    - تنتهي صلاحية Access التلقائي بعد 365 يوما

    > [!div class="mx-imgBorder"]
    > ![صورة لحزمة وصول جديدة.](images/new-access-package.png)

    لمزيد من المعلومات، راجع [إنشاء حزمة وصول جديدة](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **توفير ارتباط طلب الوصول إلى موارد MSSP من AAD (دليل Azure النشط): إدارة الهوية**

    يستخدم محللو MSSP SOC ارتباط مدخل الوصول الخاص ب MsSP لطلب الوصول عبر حزم الوصول التي تم إنشاؤها. الارتباط دائم، مما يعني أنه قد يتم استخدام الارتباط نفسه مع مرور الوقت للمحللين الجدد. يدخل طلب المحلل في قائمة انتظار للموافقة عليه من قبل **الموافقين على محللي MSSP**.

    > [!div class="mx-imgBorder"]
    > ![صورة لخصائص Access.](images/access-properties.png)

    يقع الارتباط في صفحة نظرة عامة لكل حزمة وصول.

## <a name="manage-access"></a>إدارة الوصول

1. راجع طلبات الوصول و/أو تخويلها في Myaccess الخاصة بالعملاء و/أو MSSP.

    يتم إدارة طلبات الوصول في العميل My Access، من قبل أعضاء مجموعة الموافقين لمحللي MSSP.

    للقيام بذلك، يمكنك الوصول إلى myaccess الخاصة للعميل باستخدام: `https://myaccess.microsoft.com/@<Customer Domain>`.

    على سبيل المثال:`https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. الموافقة على الطلبات أو **رفضها** في الموافقات من واجهة المستخدم.

    في هذه المرحلة، تم توفير وصول المحللين، ويجب أن يتمكن كل محلل من الوصول إلى مدخل Microsoft 365 Defender العميل:`https://security.microsoft.com/?tid=<CustomerTenantId>`

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الوصول إلى مدخل عميل MSSP](access-mssp-portal.md)
- [تكوين إعلامات التنبيهات](configure-mssp-notifications.md)
- [إحضار التنبيهات من مستأجر العملاء](fetch-alerts-mssp.md)
