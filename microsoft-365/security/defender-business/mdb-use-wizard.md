---
title: استخدام المعالج لإعداد Microsoft Defender for Business
description: يتضمن Defender for Business عملية إعداد وتكوين مثل المعالج. استخدم المعالج لتوفير الوقت والجهد.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
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
ms.custom: intro-get-started
ms.openlocfilehash: 243630a43d75a4530024e246fbea57f26a51d06b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63570950"
---
# <a name="use-the-wizard-to-set-up-microsoft-defender-for-business"></a>استخدام المعالج لإعداد Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

تم تصميم Microsoft Defender for Business لتوفير الوقت والجهد للشركات الصغيرة والمتوسطة الحجم باستخدام تجربة تشبه تجربة المعالج للإعداد والتكوين الأوليين. تصف هذه المقالة خطوات المعالج وخيارات إعداد Defender for Business وتكوينه يدويا.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="لقطة شاشة للشاشة الرئيسية للمعالج لإعداد Defender for Business.":::

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="overview-of-the-wizard"></a>نظرة عامة حول المعالج

لقد تم تصميم المعالج لمساعدتك على إعداد Defender for Business وتكوينه بسرعة وفعالية. يستعرض المعالج الخطوات التالية:

1. **تعيين أذونات المستخدم**. في هذه الخطوة، ستمنح فريق الأمان حق الوصول إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). يتم منح الوصول إلى المدخل من خلال الأدوار التي تشير إلى أذونات معينة. [تعرف على المزيد حول الأدوار والأذونات](mdb-roles-permissions.md).

   - يمكن للمسؤول العام عرض كل الإعدادات وتحريرها عبر Microsoft 365 المستأجر. 
   - يمكن لمسؤول الأمان عرض إعدادات الأمان وتحريرها. 
   - يمكن لقارئ الأمان عرض المعلومات في التقارير فقط. 

2. **اجهزتك المجهزة Windows التهيئة**. في هذه الخطوة، يمكنك اجهزتك Windows على Defender for Business بسرعة. تساعد أجهزة التكهين على الفور على حماية هذه الأجهزة من اليوم الأول. راجع [الأجهزة المجهزة ل Microsoft Defender for Business](mdb-onboard-devices.md) للحصول على مزيد من التفاصيل.

   - إذا كنت تستخدم Microsoft Intune (جزء من إدارة نقاط النهاية من Microsoft)، وكان لدى شركتك أجهزة مسجله في إدارة نقاط النهاية، سيتم سؤالك عما إذا كنت تريد استخدام الالتحاق التلقائي لبعض أجهزة Windows أو كلها.[](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) يعمل التكامل التلقائي على إعداد اتصال بين إدارة نقاط النهاية و Defender for Business، ثم Windows الأجهزة إلى Defender for Business بسلاسة.

   - إذا لم تكن تستخدم إدارة نقاط النهاية بالفعل، أو إذا كان لديك أجهزة غير Windows مسجله في إدارة نقاط النهاية، يمكنك إلحاق الأجهزة ب [Defender for Business يدويا](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
3. **قم بتكوين سياسات الأمان**. يتضمن Defender for Business سياسات أمان افتراضية لحماية الجيل التالي وحماية جدار الحماية التي يمكن تطبيقها على أجهزة شركتك. تستخدم هذه السياسات الافتراضية الإعدادات المستحسنة وقد تم تصميمها لتوفير حماية قوية لأجهزتك. 

   يمكنك أيضا إنشاء سياسات الأمان الخاصة بك إذا أردت ذلك. وإذا كنت تستخدم إدارة نقاط النهاية، يمكنك الاستمرار في استخدام ذلك لإدارة سياسات الأمان. 

   لمعرفة المزيد، راجع عرض إعدادات ونهج الأمان [وتحريرها](mdb-configure-security-settings.md).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>ماذا يحدث إذا لم أستخدم المعالج؟

إذا اخترت عدم استخدام المعالج، أو إذا كان المعالج مغلقا قبل اكتمال عملية الإعداد، لا يزال بإمكانك إكمال عملية الإعداد والتكوين بنفسك. 

راجع [إعداد Microsoft Defender for Business](mdb-setup-configuration.md) وتكوينه للسير عبر الخطوات التالية:

1. [قم بتعيين الأدوار والأذونات](mdb-roles-permissions.md) حتى يمكن لفريق الأمان الوصول إلى المدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)).

2. [قم بإعداد إعلامات البريد الإلكتروني](mdb-email-notifications.md) لفريق الأمان بحيث تكون على علم بالتنبيهات أو الثغرات الجديدة.

3. [الأجهزة المجهزة](mdb-onboard-devices.md) بحيث تكون محمية بواسطة Defender for Business.

4. [يمكنك إدارة سياسات الأمان](mdb-configure-security-settings.md)، التي تتضمن حماية الجيل التالي وحماية جدار الحماية وتصفية محتوى الويب.

## <a name="next-steps"></a>الخطوات التالية

- [إعداد إعلامات البريد الإلكتروني لفريق الأمان](mdb-email-notifications.md)

- [بدء استخدام مدخل Microsoft 365 Defender](mdb-get-started.md)

- [استخدام لوحة معلومات إدارة & المخاطر](mdb-view-tvm-dashboard.md)