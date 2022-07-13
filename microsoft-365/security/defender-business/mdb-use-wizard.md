---
title: استخدام معالج الإعداد في Microsoft Defender for Business
description: يسهل Defender for Business عملية الإعداد باستخدام معالج يقوم بتشغيل أول مرة تستخدم فيها Defender for Business. تعرف على كيفية عمل معالج الإعداد.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 0f37dd86cef388dfe183557ccf269810ef522445
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772422"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>استخدام معالج الإعداد في Microsoft Defender for Business

تم تصميم Defender for Business لتوفير الوقت والجهد للشركات الصغيرة والمتوسطة الحجم. على سبيل المثال، يمكنك إجراء الإعداد والتكوين الأوليين باستخدام معالج الإعداد. يرشدك معالج الإعداد من خلال منح حق الوصول إلى فريق الأمان وإعداد إعلامات البريد الإلكتروني لفريق الأمان الخاص بك وإعداد أجهزة Windows الخاصة بالشركة.


> [!TIP]
> استخدام معالج الإعداد اختياري. يمكنك اختيار العمل من خلال عملية الإعداد والتكوين يدويا. للتعرّف على المزيد، اطلع على:
> - [ماذا يحدث إذا لم أستخدم المعالج؟](#what-happens-if-i-dont-use-the-wizard)
> - [كيفية إعداد وتكوين Defender for Business](mdb-setup-configuration.md)

## <a name="how-to-start-the-setup-wizard"></a>كيفية بدء تشغيل معالج الإعداد

تم تصميم معالج الإعداد لتشغيل أول مرة يقوم فيها شخص ما في شركتك بتسجيل الدخول إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). 

إذا كانت شركتك تستخدم Microsoft 365 Business Premium، فسيعمل معالج إعداد Defender for Business في المرة الأولى التي ينتقل فيها شخص ما إلى **مخزون أجهزة** **نقاط** >  النهاية. 

تبدو شاشة بدء معالج الإعداد مثل الصورة التالية:

:::image type="content" source="media/mdb-wizard-start.png" alt-text="لقطة شاشة للشاشة الرئيسية للمعالج لإعداد Defender for Business.":::

## <a name="the-setup-wizard-flow"></a>تدفق معالج الإعداد

> [!IMPORTANT]
> يجب أن تكون مسؤولا عاما لتشغيل معالج الإعداد. الشخص الذي سجل شركتك في Microsoft 365 أو Defender for Business هو مسؤول عام بشكل افتراضي.

تم تصميم معالج الإعداد لمساعدتك على إعداد وتكوين Defender for Business بسرعة وكفاءة. يرشدك المعالج خلال الخطوات التالية:

1. **تعيين أذونات المستخدم**. في هذه الخطوة، يمكنك منح فريق الأمان حق الوصول إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). هذا المدخل هو المكان الذي ستدير فيه أنت وفريق الأمان قدرات الأمان الخاصة بك، وعرض التنبيهات، واتخاذ أي إجراءات مطلوبة بشأن التهديدات المكتشفة. يتم منح الوصول إلى المدخل من خلال الأدوار التي تتضمن أذونات معينة.

   في Defender for Business، يمكن تعيين أحد الأدوار الثلاثة التالية لأعضاء فريق الأمان:<br/>
   
   - **مسؤول العمومي**: يمكن للمسؤول العام عرض جميع الإعدادات وتحريرها عبر مستأجر Microsoft 365. يقوم المسؤول العام بإعداد وتكوين أولي لاشتراك Microsoft 365 الخاص بشركتك. 
   - **مسؤول الأمان**: يمكن لمسؤول الأمان عرض إعدادات الأمان وتحريرها، واتخاذ إجراء عند اكتشاف التهديدات.
   - **قارئ الأمان**: يمكن لقارئ الأمان عرض المعلومات في التقارير، ولكن لا يمكنه تغيير أي إعدادات أمان. 

   [تعرف على المزيد حول الأدوار والأذونات](mdb-roles-permissions.md). 

2. **إعداد إعلامات البريد الإلكتروني**. في هذه الخطوة، يمكنك إعداد إعلامات البريد الإلكتروني لفريق الأمان. بعد ذلك، عند إنشاء تنبيه أو اكتشاف ثغرة أمنية جديدة، لن يفوت فريق الأمان الخاص بك ذلك حتى لو كان بعيدا عن مكتبه. [تعرف على المزيد حول إعلامات البريد الإلكتروني](mdb-email-notifications.md). 

3. **إعداد أجهزة Windows وتكوينها**. في هذه الخطوة، يمكنك إلحاق أجهزة Windows الخاصة بشركتك ب Defender for Business بسرعة. يساعد إلحاق الأجهزة على الفور على حماية هذه الأجهزة من اليوم الأول. 

   - **إذا كنت تستخدم Microsoft Intune بالفعل**، وكان لدى شركتك أجهزة مسجلة في Intune، فستسأل عما إذا كنت تريد استخدام [الإلحاق التلقائي](#what-is-automatic-onboarding) لبعض أجهزة Windows المسجلة أو كلها. يقوم الإلحاق التلقائي بإعداد اتصال بين Intune و Defender for Business، ثم إلحاق أجهزة Windows ب Defender for Business بسلاسة. 
   - **إذا لم تكن تستخدم Intune بالفعل**، يمكنك [إلحاق الأجهزة ب Defender for Business](mdb-onboard-devices.md). 
   
   [تعرف على المزيد حول إلحاق الأجهزة ب Defender for Business](mdb-onboard-devices.md).
   
4. **تكوين نهج الأمان الخاصة بك**. يتضمن Defender for Business نهج أمان افتراضية لحماية الجيل التالي وحماية جدار الحماية التي يمكن تطبيقها على أجهزة شركتك. تستخدم هذه النهج الافتراضية الإعدادات الموصى بها وهي مصممة لتوفير حماية قوية لأجهزتك. يمكنك أيضا إنشاء نهج الأمان الخاصة بك. وإذا كنت تستخدم Intune بالفعل، يمكنك الاستمرار في استخدام مركز إدارة Microsoft إدارة نقاط النهاية لإدارة نهج الأمان الخاصة بك.

   [عرض نهج الأمان وإعداداتك وتحريرها](mdb-configure-security-settings.md).

## <a name="what-is-automatic-onboarding"></a>ما هو الإلحاق التلقائي؟

الإلحاق التلقائي هو طريقة مبسطة لإلحاق أجهزة Windows ب Defender for Business. يتوفر الإلحاق التلقائي فقط لأجهزة Windows المسجلة بالفعل في Microsoft Intune. 

أثناء استخدام معالج الإعداد، سيكتشف النظام ما إذا كانت أجهزة Windows مسجلة بالفعل في Intune. سيتم سؤالك عما إذا كنت تريد استخدام الإلحاق التلقائي لجميع هذه الأجهزة أو بعضها. يمكنك إلحاق جميع أجهزة Windows في وقت واحد، أو تحديد أجهزة معينة للبدء بها، ثم إضافة المزيد من الأجهزة لاحقا. 

لإلحاق الأجهزة الأخرى، راجع [إلحاق الأجهزة ب Defender for Business](mdb-onboard-devices.md).

> [!TIP]
> - نوصي بتحديد خيار "جميع الأجهزة المسجلة". وبهذه الطريقة، عندما يتم تسجيل أجهزة Windows في Intune لاحقا، سيتم إلحاقها ب Defender for Business تلقائيا. 
> - إذا كنت تدير نهج الأمان وإعداداته في مركز إدارة إدارة نقاط النهاية، نوصي بالتبديل إلى مدخل Microsoft 365 Defender لإدارة أجهزتك ونهجك وإعداداتك. لمعرفة المزيد، راجع [اختيار مكان إدارة نهج الأمان والأجهزة](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>ماذا يحدث إذا لم أستخدم المعالج؟

استخدام معالج الإعداد اختياري. إذا اخترت عدم استخدام المعالج، أو إذا كان المعالج مغلقا قبل اكتمال عملية الإعداد، يمكنك إكمال عملية الإعداد والتكوين بنفسك. 

راجع [إعداد وتكوين Defender for Business](mdb-setup-configuration.md) للاطلاع على الخطوات التالية:

1. **[تعيين الأدوار والأذونات](mdb-roles-permissions.md)** حتى يتمكن فريق الأمان من الوصول إلى مدخل Microsoft 365 Defender واستخدامه ([https://security.microsoft.com](https://security.microsoft.com)).

2. **[قم بإعداد إعلامات البريد الإلكتروني لفريق الأمان](mdb-email-notifications.md)** بحيث تكون في حلقة حول التنبيهات أو الثغرات الأمنية الجديدة.

3. **[إلحاق الأجهزة](mdb-onboard-devices.md)** بحيث تكون محمية بواسطة Defender for Business.

4. **[إدارة نهج الأمان الخاصة بك](mdb-configure-security-settings.md)**، والتي تتضمن حماية الجيل التالي وحماية جدار الحماية وتصفية محتوى الويب.

## <a name="next-steps"></a>الخطوات التالية

- [إلحاق المزيد من الأجهزة ب Defender for Business](mdb-onboard-devices.md)
- [عرض نهج الأمان وإعداداتك وتحريرها في Defender for Business](mdb-configure-security-settings.md)