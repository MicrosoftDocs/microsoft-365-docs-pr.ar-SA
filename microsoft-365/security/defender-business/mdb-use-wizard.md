---
title: استخدام معالج الإعداد في Microsoft Defender für Unternehmen
description: يتضمن Defender for Business عملية إعداد وتكوين تشبه المعالج. استخدم المعالج لتوفير الوقت والجهد.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/08/2022
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
ms.openlocfilehash: ad070273567d350973037f1ac5a0192036d22187
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746634"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>استخدام معالج الإعداد في Microsoft Defender für Unternehmen

> [!IMPORTANT]
> يتم طرح Microsoft Defender für Unternehmen [للعملاء Microsoft 365 Business Premium](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم معاينة Defender for Business باعتباره اشتراكا مستقلا، وسيتم طرحه تدريجيا للعملاء وشركاء تكنولوجيا المعلومات الذين [يقومون بالتسجيل هنا](https://aka.ms/mdb-preview) لطلبه. تتضمن المعاينة [مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بانتظام.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالنواتج/الخدمات التي تم إصدارها مسبقا والتي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المقدمة هنا. 

تم تصميم Microsoft Defender für Unternehmen لتوفير الوقت والجهد للشركات الصغيرة والمتوسطة الحجم باستخدام تجربة تشبه المعالج للإعداد والتكوين الأوليين. يرشدك معالج الإعداد من خلال منح حق الوصول إلى فريق الأمان وإعداد إعلامات البريد الإلكتروني لفريق الأمان الخاص بك وإعداد أجهزة Windows الخاصة بالشركة.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="لقطة شاشة للشاشة الرئيسية للمعالج لإعداد Defender for Business.":::

>
> **هل لديك دقيقة؟**
> يرجى الاطلاع <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">على استطلاعنا القصير حول Microsoft Defender für Unternehmen</a>. يسعدنا أن نستمع إليك!
>

## <a name="overview-of-the-setup-wizard"></a>نظرة عامة على معالج الإعداد

> [!IMPORTANT]
> قبل البدء، تأكد من إضافة مستخدمين بالفعل إلى اشتراكك في Microsoft 365. للحصول على تعليمات حول هذه المهمة، راجع [إضافة مستخدمين وتعيين التراخيص في الوقت نفسه](../../admin/add-users/add-users.md).

تم تصميم المعالج لمساعدتك على إعداد وتكوين Defender for Business بسرعة وكفاءة. يرشدك المعالج خلال الخطوات التالية:

1. **تعيين أذونات المستخدم**. في هذه الخطوة، يمكنك منح فريق الأمان حق الوصول إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). هذا المدخل هو المكان الذي ستدير فيه أنت وفريق الأمان قدرات الأمان الخاصة بك، وعرض التنبيهات، واتخاذ أي إجراءات مطلوبة بشأن التهديدات المكتشفة. يتم منح الوصول إلى المدخل من خلال الأدوار التي تتضمن أذونات معينة.

   في Defender for Business، يمكن تعيين أحد الأدوار الثلاثة لأعضاء فريق الأمان:<br/>
   
      - **المسؤول العام**: يمكن للمسؤول العام عرض جميع الإعدادات وتحريرها عبر مستأجر Microsoft 365. يقوم المسؤول العام بإعداد وتكوين أولي لاشتراك Microsoft 365 الخاص بشركتك. 
      - **مسؤول الأمان**: يمكن لمسؤول الأمان عرض إعدادات الأمان وتحريرها، واتخاذ إجراء عند اكتشاف التهديدات.
      - **قارئ الأمان**: يمكن لقارئ الأمان عرض المعلومات في التقارير، ولكن لا يمكنه تغيير أي إعدادات أمان. 
      
      [تعرف على المزيد حول الأدوار والأذونات](mdb-roles-permissions.md). 

2. **إعداد إعلامات البريد الإلكتروني**. في هذه الخطوة، يمكنك إعداد إعلامات البريد الإلكتروني لفريق الأمان. بعد ذلك، عند إنشاء تنبيه أو اكتشاف ثغرة أمنية جديدة، لن يتعلق الأمر بفريق الأمان الخاص بك حتى لو كان بعيدا عن مكتبه. 

   [تعرف على المزيد حول إعلامات البريد الإلكتروني](mdb-email-notifications.md). 

3. **إعداد أجهزة Windows وتكوينها**. في هذه الخطوة، يمكنك إلحاق أجهزة Windows الخاصة بشركتك إلى Defender for Business بسرعة. يساعد إلحاق الأجهزة على الفور على حماية هذه الأجهزة من اليوم الأول. 

   - **إذا كنت تستخدم Microsoft Endpoint Manager** (بما في ذلك Microsoft Intune)، وكان لدى شركتك أجهزة مسجلة في Endpoint Manager، فسيتم سؤالك عما إذا كنت تريد استخدام [الإلحاق التلقائي](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) لبعض أجهزة Windows المسجلة أو كلها. يقوم الإلحاق التلقائي بإعداد اتصال بين Endpoint Manager و Defender for Business، ثم إلحاق أجهزة Windows إلى Defender for Business بسلاسة. 
   - **إذا لم تكن تستخدم Endpoint Manager بالفعل**، يمكنك [إلحاق الأجهزة ب Defender for Business باستخدام برنامج نصي محلي](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
   اطلع [على معرفة المزيد حول إلحاق الأجهزة Microsoft Defender für Unternehmen](mdb-onboard-devices.md).
   
4. **تكوين نهج الأمان الخاصة بك**. يتضمن Defender for Business نهج أمان افتراضية لحماية الجيل التالي وحماية جدار الحماية التي يمكن تطبيقها على أجهزة شركتك. تستخدم هذه النهج الافتراضية الإعدادات الموصى بها وهي مصممة لتوفير حماية قوية لأجهزتك. يمكنك أيضا إنشاء نهج الأمان الخاصة بك. وإذا كنت تستخدم Endpoint Manager بالفعل، يمكنك الاستمرار في استخدام ذلك لإدارة نهج الأمان الخاصة بك.

   لمعرفة المزيد، راجع [عرض نهج الأمان وإعداداتك وتحريرها](mdb-configure-security-settings.md). |

## <a name="what-happens-if-i-dont-use-the-wizard"></a>ماذا يحدث إذا لم أستخدم المعالج؟

استخدام معالج الإعداد اختياري. إذا اخترت عدم استخدام المعالج، أو إذا كان المعالج مغلقا قبل اكتمال عملية الإعداد، يمكنك إكمال عملية الإعداد والتكوين بنفسك. راجع [إعداد Microsoft Defender für Unternehmen وتكوينها](mdb-setup-configuration.md) للتنقل عبر الخطوات التالية:

1. **[تعيين الأدوار والأذونات](mdb-roles-permissions.md)** حتى يتمكن فريق الأمان من الوصول إلى مدخل Microsoft 365 Defender واستخدامه ([https://security.microsoft.com](https://security.microsoft.com)).

2. **[قم بإعداد إعلامات البريد الإلكتروني لفريق الأمان](mdb-email-notifications.md)** بحيث تكون في حلقة حول التنبيهات أو الثغرات الأمنية الجديدة.

3. **[إلحاق الأجهزة](mdb-onboard-devices.md)** بحيث تكون محمية بواسطة Defender for Business.

4. **[إدارة نهج الأمان الخاصة بك](mdb-configure-security-settings.md)**، والتي تتضمن حماية الجيل التالي وحماية جدار الحماية وتصفية محتوى الويب.

## <a name="next-steps"></a>الخطوات التالية

- [إعداد إعلامات البريد الإلكتروني لفريق الأمان](mdb-email-notifications.md)

- [بدء استخدام مدخل Microsoft 365 Defender](mdb-get-started.md)

- [استخدام لوحة معلومات إدارة الثغرات الأمنية & المخاطر](mdb-view-tvm-dashboard.md)