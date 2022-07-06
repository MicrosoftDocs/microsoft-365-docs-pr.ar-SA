---
title: التعرّف على إدارة الوصول المتميزة
description: توفر هذه المقالة نظرة عامة حول إدارة الوصول المتميز في Microsoft Purview، بما في ذلك الإجابات على الأسئلة المتداولة (الأسئلة المتداولة).
keywords: Microsoft 365، وMicrosoft Purview، والامتثال، وإدارة الوصول المتميز
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
f1.keywords:
- NOCSH
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.openlocfilehash: 6bf13adb96ae5d4d4030ebe44f10dab22602196e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622536"
---
# <a name="learn-about-privileged-access-management"></a>التعرّف على إدارة الوصول المتميزة

تسمح Microsoft Purview Privileged Access Management بالتحكم في الوصول الدقيق لمهام المسؤول المتميزة في Office 365. يمكن أن يساعد في حماية مؤسستك من الخروقات التي تستخدم حسابات المسؤول المتميزة الحالية مع الوصول الدائم إلى البيانات الحساسة أو الوصول إلى إعدادات التكوين الهامة. تتطلب إدارة الوصول المتميزة من المستخدمين طلب الوصول في الوقت المناسب لإكمال المهام المرتفعة والمميزة من خلال سير عمل الموافقة المحدد بدقة والوقت. يمنح هذا التكوين المستخدمين وصولا كافيا فقط لتنفيذ المهمة المطروحة، دون المخاطرة بالتعرض للبيانات الحساسة أو إعدادات التكوين الهامة. يتيح تمكين إدارة الوصول المتميز لمؤسستك العمل دون امتيازات دائمة وتوفير طبقة دفاع ضد الثغرات الأمنية في الوصول الإداري الدائم.

للحصول على نظرة عامة سريعة على مربع تأمين العميل المتكامل وسير عمل إدارة الوصول المتميز، راجع [مربع تأمين العميل هذا وفيديو إدارة الوصول المتميز](https://go.microsoft.com/fwlink/?linkid=2066800).

## <a name="layers-of-protection"></a>طبقات الحماية

تكمل إدارة الوصول المتميزة حماية ميزات الوصول والبيانات الأخرى ضمن بنية أمان Microsoft 365. يوفر تضمين إدارة الوصول المتميز كجزء من نهج متكامل متعدد الطبقات للأمان نموذجا أمنيا يزيد من حماية المعلومات الحساسة وإعدادات تكوين Microsoft 365. كما هو موضح في الرسم التخطيطي، تعتمد إدارة الوصول المتميز على الحماية المتوفرة مع التشفير الأصلي لبيانات Microsoft 365 ونموذج أمان التحكم في الوصول المستند إلى الدور لخدمات Microsoft 365. عند استخدامها مع [Azure AD إدارة الهويات المتميزة](/azure/active-directory/active-directory-privileged-identity-management-configure)، توفر هاتين الميزتين التحكم في الوصول مع الوصول في الوقت المناسب في نطاقات مختلفة.

![الحماية متعددة الطبقات في Microsoft 365.](../media/pam-layered-protection.png)

يتم تعريف إدارة الوصول المتميز وتحديد نطاقها على مستوى **المهمة**، بينما يطبق Azure AD إدارة الهويات المتميزة الحماية على مستوى **الدور** مع القدرة على تنفيذ مهام متعددة. يسمح Azure AD إدارة الهويات المتميزة بشكل أساسي بإدارة الوصول إلى أدوار AD ومجموعات الأدوار، بينما تطبق إدارة الوصول المتميز ل Microsoft Purview فقط على مستوى المهمة.

- **تمكين إدارة الوصول المتميزة أثناء استخدام Azure AD إدارة الهويات المتميزة:** توفر إضافة إدارة الوصول المتميز طبقة متعددة أخرى من قدرات الحماية والتدقيق للوصول المتميز إلى بيانات Microsoft 365.

- **تمكين Azure AD إدارة الهويات المتميزة أثناء استخدام Microsoft Purview Privileged Access Management:** إضافة Azure AD إدارة الهويات المتميزة  إلى Microsoft Purview Privileged Access Management يمكن توسيع الوصول المتميز إلى البيانات خارج Microsoft 365 التي يتم تعريفها بشكل أساسي بواسطة أدوار المستخدم أو الهوية.  

## <a name="privileged-access-management-architecture-and-process-flow"></a>بنية إدارة الوصول المتميز وتدفق العمليات

تحدد كل عملية من تدفقات العمليات التالية بنية الوصول المتميز وكيفية تفاعلها مع ركيزة Microsoft 365 والتدقيق ومساحة تشغيل Exchange Management.

### <a name="step-1-configure-a-privileged-access-policy"></a>الخطوة 1: تكوين نهج وصول متميز

عند تكوين نهج وصول متميز باستخدام [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) أو Exchange Management PowerShell، يمكنك تحديد النهج وعمليات ميزة الوصول المتميز وسمات النهج في ركيزة Microsoft 365. يتم تسجيل الأنشطة في مركز التوافق الأمني &amp; . تم الآن تمكين النهج وجاهز لمعالجة الطلبات الواردة للحصول على الموافقات.

![الخطوة 1: إنشاء النهج.](../media/pam-step1-policy-creation.jpg)

### <a name="step-2-access-request"></a>الخطوة 2: طلب الوصول

في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) أو باستخدام Exchange Management PowerShell، يمكن للمستخدمين طلب الوصول إلى المهام المرتفعة أو المتميزة. ترسل ميزة الوصول المتميز الطلب إلى ركيزة Microsoft 365 للمعالجة مقابل نهج الوصول إلى الامتياز الذي تم تكوينه وتسجل النشاط في سجلات مركز التوافق الأمني &amp; .

![الخطوة 2: طلب الوصول.](../media/pam-step2-access-request.jpg)

### <a name="step-3-access-approval"></a>الخطوة 3: الموافقة على الوصول

يتم إنشاء طلب موافقة ويتم إرسال إعلام الطلب المعلق عبر البريد الإلكتروني إلى الموافقين. إذا تمت الموافقة عليه، تتم معالجة طلب الوصول المتميز كموافقة وتكون المهمة جاهزة للإكمال. إذا تم رفض المهمة، فسيتم حظرها ولا يتم منح حق الوصول إلى الطالب. يتم إعلام الطالب بالموافقة على الطلب أو رفضه عبر رسالة البريد الإلكتروني.

![الخطوة 3: الموافقة على الوصول.](../media/pam-step3-access-approval.jpg)

### <a name="step-4-access-processing"></a>الخطوة 4: معالجة الوصول

بالنسبة إلى طلب تمت الموافقة عليه، تتم معالجة المهمة بواسطة مساحة تشغيل Exchange Management. يتم التحقق من الموافقة مقابل نهج الوصول المتميز وتعالج بواسطة ركيزة Microsoft 365. يتم تسجيل كافة أنشطة المهمة في مركز توافق الأمان &amp; .

![الخطوة 4: معالجة الوصول.](../media/pam-step4-access-processing.jpg)

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

### <a name="what-skus-can-use-privileged-access-in-office-365"></a>ما هي وحدات SKU التي يمكنها استخدام الوصول المتميز في Office 365؟

تتوفر إدارة الوصول المتميز للعملاء لمجموعة واسعة من اشتراكات Microsoft 365 ووظائف Office 365 الإضافية. راجع [بدء استخدام إدارة الوصول المتميز](privileged-access-management-configuration.md) للحصول على التفاصيل.

### <a name="when-will-privileged-access-support-office-365-workloads-beyond-exchange"></a>متى سيدعم الوصول المتميز Office 365 أحمال العمل خارج Exchange؟

ستتوفر إدارة الوصول المتميز في أحمال عمل Office 365 أخرى قريبا. تفضل بزيارة [مخطط Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) للحصول على مزيد من التفاصيل.

### <a name="my-organization-needs-more-than-30-privileged-access-policies-will-this-limit-be-increased"></a>تحتاج مؤسستي إلى أكثر من 30 نهج وصول متميز، هل سيتم زيادة هذا الحد؟

نعم، إن رفع الحد الحالي البالغ 30 نهج وصول متميز لكل مؤسسة موجود في مخطط الميزات.

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a>هل أحتاج إلى أن أكون مسؤول عمومية لإدارة الوصول المتميز في Office 365؟

لا، تحتاج إلى تعيين دور Exchange Role Management إلى الحسابات التي تدير الوصول المتميز في Office 365. إذا كنت لا تريد تكوين دور "إدارة الدور" كإذن حساب مستقل، فسيتضمن دور "المسؤول العام" هذا الدور بشكل افتراضي ويمكنه إدارة الوصول المتميز. لا يحتاج المستخدمون المضمنون في مجموعة الموافقين إلى أن يكونوا مسؤول عمومية أو أن يكون لديهم دور "إدارة الأدوار" المعين لمراجعة الطلبات والموافقة عليها باستخدام PowerShell.

### <a name="how-is-privileged-access-management-related-to-customer-lockbox"></a>كيف ترتبط إدارة الوصول المتميزة ب Customer Lockbox؟

يسمح [مربع تأمين العميل](/office365/admin/manage/customer-lockbox-requests) بمستوى من التحكم بالوصول للمؤسسات عند وصول Microsoft إلى البيانات. تسمح إدارة الوصول المتميز بالتحكم في الوصول متعدد المستويات داخل مؤسسة لكل المهام المتميزة في Microsoft 365.

## <a name="ready-to-get-started"></a>هل أنت جاهز لبدء الاستخدام؟

ابدأ [بتكوين مؤسستك لإدارة الوصول المتميز](privileged-access-management-configuration.md).

## <a name="learn-more"></a>التعرف على المزيد

[الدليل التفاعلي: مراقبة مهام المسؤول والتحكم فيها باستخدام إدارة الوصول المتميزة](https://content.cloudguides.com/guides/Privileged%20Access%20Management)
