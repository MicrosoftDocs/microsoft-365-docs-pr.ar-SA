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
ms.openlocfilehash: 02f970f7ad9981336ba54aaafcf936e952f1b726
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663105"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>عملية التكوين المبسطة في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business [للعملاء Microsoft 365 Business Premium](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم معاينة Defender for Business باعتباره اشتراكا مستقلا، وسيتم طرحه تدريجيا للعملاء وشركاء تكنولوجيا المعلومات الذين [يقومون بالتسجيل هنا](https://aka.ms/mdb-preview) لطلبه. تتضمن المعاينة [مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بانتظام.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالنواتج/الخدمات التي تم إصدارها مسبقا والتي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المقدمة هنا. 

يتميز Microsoft Defender for Business بعملية تكوين مبسطة، مصممة خصيصا للشركات الصغيرة والمتوسطة الحجم. تأخذ هذه التجربة التخمين من إعداد الأجهزة وإدارتها، مع تجربة تشبه المعالج والنهج الافتراضية التي تم تصميمها لحماية أجهزة شركتك من اليوم الأول. **نوصي باستخدام عملية التكوين المبسطة؛ ومع ذلك، لا تقتصر على هذا الخيار**.

عندما يتعلق الأمر بإلحاق الأجهزة وتكوين إعدادات الأمان لأجهزة شركتك، يمكنك الاختيار من بين العديد من التجارب: 

- عملية التكوين المبسطة في Microsoft Defender for Business (*مستحسن*) 
- إدارة نقاط النهاية من Microsoft، الذي يتضمن Microsoft Intune (مضمن في [Microsoft 365 Business Premium](../../business-premium/index.md))
- حلك غير التابع ل Microsoft لإدارة الأجهزة 

## <a name="what-to-do"></a>ما يجب فعله

1. [مراجعة خيارات الإعداد والتكوين](#review-your-setup-and-configuration-options)

2. [تعرف على المزيد حول عملية التكوين المبسطة في Defender for Business](#why-we-recommend-using-the-simplified-configuration-process)

3. [المتابعة إلى خطواتك التالية](#next-steps)

>
> **هل لديك دقيقة؟**
> يرجى الاطلاع <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">على استطلاعنا القصير حول Microsoft Defender for Business</a>. يسعدنا أن نستمع إليك!
>

## <a name="review-your-setup-and-configuration-options"></a>مراجعة خيارات الإعداد والتكوين

يصف الجدول التالي كل تجربة:
<br/><br/>

| تجربة المدخل  | الوصف  |
|---------|---------|
| تجربة التكوين المبسطة في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*هذا هو الخيار الموصى به لمعظم العملاء*)  | تتضمن تجربة التكوين المبسطة تجربة تشبه المعالج لمساعدتك على إعداد وتكوين Defender for Business. يتضمن التكوين المبسط أيضا إعدادات ونهج أمان افتراضية لمساعدتك على حماية أجهزة شركتك بمجرد إلحاقها ب Defender for Business. <br/><br/>باستخدام هذه التجربة، يستخدم فريق الأمان مدخل Microsoft 365 Defender من أجل: <br/>- إعداد وتكوين Defender for Business <br/>- عرض الحوادث وإدارتها<br/>- الاستجابة للتهديدات والتخفيف من حدتها<br/>- عرض التقارير<br/>- مراجعة الإجراءات المعلقة أو المكتملة <br/><br/> مدخل Microsoft 365 Defender هو متجرك الوحيد لإعدادات الأمان الخاصة بشركتك وقدرات الحماية من التهديدات. يمكنك الحصول على تجربة مبسطة لمساعدتك على البدء بسرعة وكفاءة. لمعرفة المزيد، راجع [استخدام المعالج لإعداد Microsoft Defender for Business](mdb-use-wizard.md).<br/><br/>ويمكنك تحرير إعداداتك أو تحديد نهج جديدة لتتناسب مع احتياجات شركتك.<br/><br/>لمعرفة المزيد، راجع [عرض نهج الجهاز أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md). |
| مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | يتضمن إدارة نقاط النهاية من Microsoft Microsoft Intune، وموفر إدارة أجهزة محمولة مستندة إلى السحابة (MDM) وموفر إدارة تطبيقات الأجهزة المحمولة (MAM) للتطبيقات والأجهزة. [Microsoft 365 Business Premium](../../business-premium/index.md) العملاء لديهم إدارة نقاط النهاية بالفعل. <br/><br/>تستخدم العديد من الشركات Intune لإدارة أجهزتها، مثل الهواتف المحمولة وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر المحمولة. لمعرفة المزيد، راجع [Microsoft Intune هو موفر MDM وMAM لأجهزتك](/mem/intune/fundamentals/what-is-intune). <br/><br/>إذا كنت تستخدم بالفعل Microsoft Intune أو إدارة نقاط النهاية من Microsoft، يمكنك الاستمرار في استخدام هذا الحل. |
| حل إدارة الأجهزة غير التابع ل Microsoft  | إذا كنت تستخدم حل إدارة الأجهزة والإنتاجية غير التابع ل Microsoft، يمكنك الاستمرار في استخدام هذا الحل مع Defender for Business. <br/><br/>عند إلحاق الأجهزة ب Defender for Business، سترى حالتها وتنبيهاتها في مدخل Microsoft 365 Defender. لمعرفة المزيد، راجع [خيارات أداة الإعداد والتكوين ل Defender لنقطة النهاية](../defender-endpoint/onboard-configure.md). |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>لماذا نوصي باستخدام عملية التكوين المبسطة

**نوصي باستخدام عملية التكوين المبسطة في Microsoft Defender for Business** لمعظم العملاء. يتم تبسيط عملية التكوين المبسطة خاصة للشركات الصغيرة والمتوسطة الحجم. تم تصميم Defender for Business لمساعدتك على حماية أجهزة شركتك في اليوم الأول، دون الحاجة إلى خبرة تقنية عميقة أو معرفة خاصة. باستخدام إعدادات الأمان والنهج الافتراضية، تتم حماية أجهزتك بمجرد إلحاقها.

تم تصميم Defender for Business لتوفير حماية قوية مع توفير الوقت والجهد في تكوين إعدادات الأمان الخاصة بك. تجعل التجربة المبسطة في مدخل Microsoft 365 Defender من السهل إلحاق الأجهزة وإدارتها. بالإضافة إلى ذلك، يتم تضمين النهج الافتراضية بحيث تتم حماية أجهزة شركتك بمجرد إلحاقها. يمكنك الاحتفاظ بالإعدادات الافتراضية كما هي، أو إجراء تغييرات لتلائم احتياجات عملك. يمكنك أيضا إضافة نهج جديدة لإدارة الأجهزة حسب الحاجة.

## <a name="next-steps"></a>الخطوات التالية

- [إعداد Microsoft Defender for Business وتكوينها](mdb-setup-configuration.md)

- [بدء استخدام Microsoft Defender for Business](mdb-get-started.md)
