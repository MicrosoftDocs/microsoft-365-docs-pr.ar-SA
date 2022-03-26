---
title: المتطلبات الأساسية لسطح المكتب المدار من Microsoft
description: التراخيص وحسابات Azure وإعدادات المصادقة Microsoft 365 الإعدادات لإعدادها قبل التسجيل في Microsoft Managed Desktop
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 495aa7e505bdcec8b5848499ac688847afa129bc
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63565871"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>المتطلبات الأساسية لسطح المكتب المدار من Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure). DO NOT DELETE.-->
<!--from Prerequisites -->

توضح هذه المقالة متطلبات البنية الأساسية التي يجب تلبيتها لضمان النجاح في Microsoft Managed Desktop.

| المنطقة | تفاصيل المتطلبات الأساسية |
| ----- | ----- |
| الترخيص | يتطلب Microsoft Managed Desktop Microsoft 365 E3 الترخيص مع تعيين Microsoft Defender لنقطة النهاية (أو ما يعادله) للمستخدمين. <ul><li>للحصول على تفاصيل حول خطط الخدمة المحددة، راجع [المزيد حول التراخيص](#more-about-licenses).</li><li> لمزيد من المعلومات حول التراخيص المتوفرة، راجع Microsoft 365 [الترخيص](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans).</li></ul>
| الاتصال | تتطلب جميع أجهزة سطح المكتب المدارة من Microsoft الاتصال بنقاط نهاية خدمة Microsoft المتعددة من شبكة الشركة.<br><br> للحصول على القائمة الكاملة ل IPs وURLs المطلوبة، راجع [تكوين الشبكة](../get-ready/network.md).
| Azure Active Directory | يجب أن يكون Azure Active Directory (Azure AD) إما مصدر السلطة لكل حسابات المستخدمين، أو يجب مزامنة حسابات المستخدمين من Active Directory المحلي باستخدام أحدث إصدار مدعوم من Azure AD الاتصال. <ul><li>لمزيد من المعلومات، راجع [Azure AD الاتصال](/azure/active-directory/hybrid/whatis-azure-ad-connect).</li><li> لمزيد من المعلومات حول إصدارات Azure AD الاتصال، راجع [Azure AD الاتصال:محفوظات الإصدارات](/azure/active-directory/hybrid/reference-connect-version-history).</li></ul>
| المصادقة | إذا لم يكن Azure AD مصدر المصادقة الأساسية لحسابات المستخدمين، فيجب تكوين أحد أساليب المصادقة التالية في Azure AD الاتصال:<ul><li> مزامنة كلمة المرور.</li> <li> المصادقة المرورية.</li><li>موفر هوية خارجي (بما في ذلك Windows Server ADFS وغير Microsoft IDPs) تم تكوينه لتلبية متطلبات تكامل Azure AD. لمزيد من المعلومات، راجع [الإرشادات](https://www.microsoft.com/download/details.aspx?id=56843).</li></ul> <br> عند تعيين خيارات المصادقة باستخدام Azure AD الاتصال، يوصى أيضا بكتابة كلمة المرور. لمزيد من المعلومات، راجع [إعادة كتابة كلمة المرور](/azure/active-directory/authentication/howto-sspr-writeback). <br><br> إذا تم تنفيذ موفر هوية خارجي، فيجب التحقق من صحة الحل:<ul><li>يلبي متطلبات تكامل Azure AD.</li><li>يدعم Azure AD Conditional Access، الذي يسمح بتكوين نهج توافق أجهزة سطح المكتب المدارة من Microsoft.</li><li>تمكين تسجيل الجهاز أو استخدام Microsoft 365 أو الميزات المطلوبة كجزء من Microsoft Managed Desktop.</li></ul> <br>لمزيد من المعلومات حول خيارات المصادقة باستخدام Azure AD، راجع [Azure AD الاتصال تسجيل الدخول للمستخدم](/azure/active-directory/connect/active-directory-aadconnect-user-signin).
| Microsoft 365 | OneDrive for Business تمكين هذه الميزة لمستخدمي Microsoft Managed Desktop.<br><br>على الرغم من أنه ليس من المطلوب التسجيل في Microsoft Managed Desktop، إلا أننا نوصي بشدة بترحيل الخدمات التالية إلى السحابة:<ul><li>البريد الإلكتروني: الترحيل إلى علب البريد المستندة إلى السحابة، Exchange عبر الإنترنت، أو تكوينها باستخدام Exchange Online المختلط مع Exchange 2013 أو الإصدارات الأعلى، المحلية.</li><li>الملفات والمجلدات: الترحيل إلى OneDrive for Business أو SharePoint عبر الإنترنت.</li><li>أدوات التعاون عبر الإنترنت: الترحيل إلى Teams.</ul> |
| إدارة الأجهزة | تتطلب أجهزة سطح المكتب المدارة من Microsoft الإدارة باستخدام Microsoft Intune. يجب تعيين Intune كمرجع إدارة أجهزة المحمول.<br><br> لمزيد من المعلومات[، راجع Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).
| النسخ الاحتياطي للبيانات واستردادها | يتطلب Microsoft Managed Desktop مزامنة الملفات OneDrive for Business لحمايتها. لا يضمن Microsoft Managed Desktop OneDrive for Business الملفات التي لم تتم مزامنتها مع هذه الملفات. قد تفقد الملفات أثناء عمليات تبادل الأجهزة أو مكالمات الدعم التي تتطلب إعادة تعيين الجهاز.<br><br>على الرغم من أن هذا الأمر غير مطلوب، إلا أن Microsoft Managed Desktop يوصي بشدة با الترحيل من محركات أقراص الشبكة التي تم تعيينها إلى الحل السحابي المناسب. لمزيد من المعلومات، راجع [إعداد محركات أقراص تم تعيينها لسطح المكتب المدار من Microsoft](mapped-drives.md)

عندما تكون جاهزا للبدء باستخدام Microsoft Managed Desktop، اتصل ب Microsoft Account Manager.

## <a name="more-about-licenses"></a>المزيد حول التراخيص

يتطلب Microsoft Managed Desktop بعض خيارات الترخيص لكي يعمل. راجع [تقنيات سطح المكتب المدار من Microsoft](../intro/technologies.md) للحصول على معلومات حول كيفية استخدام هذه التراخيص.

> [!TIP]
> لتعيين خيارات الترخيص هذه لمستخدمين محددين، نوصيك ب الاستفادة من ميزة الترخيص المستندة إلى المجموعة ل Azure Active Directory.[](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)

- Azure Active Directory Premium P1
- Microsoft Intune
- Windows 10 Enterprise  
- Microsoft Defender لنقطة النهاية
- Microsoft 365 Apps for enterprise
- Microsoft Teams
- [SharePoint عبر الإنترنت 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans)

> [!TIP]
> سيساعدك Microsoft Account Manager على مراجعة التراخيص الحالية وخطط الخدمة والعثور على المسار الأكثر فعالية للحصول على أي تراخيص أو خطط خدمة إضافية قد تحتاج إليها، مع تجنب التكرار.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>خطوات الاستعداد لسطح المكتب المدار من Microsoft

1. مراجعة المتطلبات الأساسية (هذه المقالة).
1. تشغيل [أدوات تقييم الجهوزية](readiness-assessment-tool.md).
1. شراء [Company Portal](../get-started/company-portal.md).
1. مراجعة [المتطلبات الأساسية الخاصة وحسابات الضيوف](guest-accounts.md).
1. تحقق [من تكوين الشبكة](network.md).
1. [إعداد الشهادات وملفات تعريف الشبكة](certs-wifi-lan.md).
1. [إعداد وصول المستخدم إلى البيانات](authentication.md).
1. [تحضير التطبيقات](apps.md).
1. [إعداد محركات أقراص تم تعيينها](mapped-drives.md).
1. [تحضير موارد الطباعة](printing.md).
1. أسماء [أجهزة العنوان](address-device-names.md).
