---
title: عملية التكوين المبسطة في Microsoft Defender for Business
description: تعرف على عملية التكوين المبسطة في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2445b7f35fb808c49c046027e2279c3b00057f54
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575166"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>عملية التكوين المبسطة في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

يتميز Microsoft Defender for Business بعملية تكوين مبسطة، تم تصميمها خصيصا للشركات الصغيرة والمتوسطة الحجم. تخمن هذه التجربة عملية إعداد الأجهزة وإدارتها، باستخدام تجربة مثل المعالج ونهج افتراضية تم تصميمها لحماية أجهزة شركتك من اليوم الأول. **نوصي باستخدام عملية التكوين المبسطة؛** ومع ذلك، أنت لست مقتصرا على هذا الخيار.

عندما يتعلق الأمر بأجهزة التهيئة وتكوين إعدادات الأمان للأجهزة الخاصة بالشركة، يمكنك الاختيار من بين عدة تجارب: 

- عملية التكوين المبسطة في Microsoft Defender for Business (*مستحسن*) 
- إدارة نقاط النهاية من Microsoft، التي تتضمن Microsoft Intune (مضمنة [في Microsoft 365 Business Premium](../../business-premium/index.md))
- الحل غير الخاص بك من Microsoft لإدارة الأجهزة 

## <a name="what-to-do"></a>ما يجب فعله

1. [مراجعة خيارات الإعداد والتكوين](#review-your-setup-and-configuration-options)

2. [تعرف على المزيد حول عملية التكوين المبسطة في Defender for Business](#why-we-recommend-using-the-simplified-configuration-process)

3. [المتابعة إلى الخطوات التالية](#next-steps)

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="review-your-setup-and-configuration-options"></a>مراجعة خيارات الإعداد والتكوين

يصف الجدول التالي كل تجربة:
<br/><br/>

| تجربة المدخل  | الوصف  |
|---------|---------|
| تجربة التكوين المبسطة في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*هذا هو الخيار الموصى به لمعظم العملاء*)  | تتضمن تجربة التكوين المبسطة تجربة تشبه تجربة المعالج لمساعدتك على إعداد Defender for Business وتكوينه. يتضمن التكوين المبسط أيضا إعدادات الأمان ونهجه الافتراضية لمساعدتك على حماية أجهزة شركتك بمجرد أن يتم إعدادها في Defender for Business. <br/><br/>باستخدام هذه التجربة، يستخدم فريق الأمان Microsoft 365 Defender إلى: <br/>- إعداد Defender for Business وتكوينه <br/>- عرض الأحداث وإدارتها<br/>- الاستجابة للتهديدات وتخفيفها<br/>- عرض التقارير<br/>- مراجعة الإجراءات المعلقة أو المكتملة <br/><br/> المدخل Microsoft 365 Defender هو متجرك الوحيد لإعدادات الأمان وإمكانيات الحماية من المخاطر الخاصة بالشركة. يمكنك الحصول على تجربة مبسطة لمساعدتك على بدء الاستخدام بسرعة وفعالية. لمعرفة المزيد، راجع [استخدام المعالج لإعداد Microsoft Defender for Business](mdb-use-wizard.md).<br/><br/>كما يمكنك تحرير الإعدادات أو تعريف سياسات جديدة لتتناسب مع احتياجات شركتك.<br/><br/>لمعرفة المزيد، راجع [عرض سياسات الأجهزة أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md). |
| مركز إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | إدارة نقاط النهاية من Microsoft على Microsoft Intune الأجهزة المحمولة (MDM) المستندة إلى السحابة وموفر إدارة تطبيقات الأجهزة المحمولة (MAM) للتطبيقات والأجهزة. [Microsoft 365 Business Premium](../../business-premium/index.md) العملاء بالفعل إدارة نقاط النهاية. <br/><br/>تستخدم العديد من الشركات Intune لإدارة أجهزتها، مثل الهواتف المحمولة وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر المحمولة. لمعرفة المزيد، راجع Microsoft Intune [هو موفر MDM وMAM لأجهزتك](/mem/intune/fundamentals/what-is-intune). <br/><br/>إذا كنت تستخدم Microsoft Intune أو إدارة نقاط النهاية من Microsoft، يمكنك الاستمرار في استخدام هذا الحل. |
| حل إدارة أجهزة غير Microsoft  | إذا كنت تستخدم حل إدارة الأجهزة والإنتاجية من Microsoft، يمكنك الاستمرار في استخدام هذا الحل مع Defender for Business. <br/><br/>عندما يتم وضع الأجهزة في موقع Defender for Business، سترى الحالة والتنبيهات في مدخل Microsoft 365 Defender. لمعرفة المزيد، راجع [خيارات أدوات التكوين والتهيئة ل Defender ل Endpoint](../defender-endpoint/onboard-configure.md). |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>لماذا نوصي باستخدام عملية التكوين المبسطة

**نوصي باستخدام عملية التكوين المبسطة في Microsoft Defender for Business** لمعظم العملاء. يتم تنظيم عملية التكوين المبسطة خاصة للشركات الصغيرة والمتوسطة الحجم. لقد تم تصميم Defender for Business لمساعدتك على حماية أجهزة شركتك في اليوم الأول، دون الحاجة إلى خبرة تقنية كبيرة أو معرفة خاصة. باستخدام إعدادات الأمان ونهجه الافتراضية، تكون أجهزتك محمية بمجرد أن يتم إعدادها.

تم تصميم Defender for Business لتوفير حماية قوية مع توفير الوقت والجهد في تكوين إعدادات الأمان. تجعل التجربة المبسطة في Microsoft 365 Defender الإلكتروني من السهل على الأجهزة المجهزة وإدارتها. بالإضافة إلى ذلك، يتم تضمين سياسات افتراضية بحيث تكون أجهزة شركتك محمية بمجرد الإضافة. يمكنك الاحتفاظ بإعداداتك الافتراضية كما هي، أو إجراء تغييرات لتتناسب مع احتياجات عملك. يمكنك أيضا إضافة سياسات جديدة لإدارة الأجهزة حسب الحاجة.

## <a name="next-steps"></a>الخطوات التالية

- [إعداد Microsoft Defender for Business وتكوينه](mdb-setup-configuration.md)

- [بدء استخدام Microsoft Defender for Business](mdb-get-started.md)
