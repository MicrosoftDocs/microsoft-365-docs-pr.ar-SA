---
title: نشر Microsoft Defender لنقطة النهاية على ميزات iOS
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على أجهزة iOS غير المسجلة.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، ios، التكوين، الميزات، ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1d05f515ef1f2badcb6ba0bde69daa3fa2677434
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873501"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>نشر Microsoft Defender لنقطة النهاية على أجهزة iOS غير المسجلة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> يستخدم Defender لنقطة النهاية على iOS VPN من أجل توفير ميزة حماية الويب. هذه ليست شبكة ظاهرية خاصة عادية وهي شبكة ظاهرية خاصة محلية/ذاتية الحلقة لا تأخذ نسبة استخدام الشبكة خارج الجهاز.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>تكوين إشارات مخاطر Microsoft Defender لنقطة النهاية في نهج حماية التطبيقات (MAM)

Microsoft Defender لنقطة النهاية على iOS، الذي يحمي بالفعل مستخدمي المؤسسة على سيناريوهات إدارة الجهاز الأجهزة المحمولة (MDM)، الآن توسيع الدعم إلى إدارة تطبيقات الأجهزة المحمولة (MAM)، للأجهزة غير المسجلة باستخدام إدارة الأجهزة المحمولة Intune (MDM). كما أنه يوسع هذا الدعم للعملاء الذين يستخدمون حلول إدارة تنقل المؤسسات الأخرى، مع الاستمرار في استخدام Intune لإدارة تطبيقات المحمول (MAM). تسمح لك هذه الإمكانية بإدارة بيانات مؤسستك وحمايتها داخل تطبيق ما.

يتم الاستفادة من Microsoft Defender لنقطة النهاية على معلومات التهديد لنظام التشغيل iOS من قبل Intune App Protection Policies لحماية هذه التطبيقات. نهج حماية التطبيقات (APP) هي قواعد تضمن بقاء بيانات المؤسسة آمنة أو مضمنة في تطبيق مدار. يحتوي التطبيق المدار على نهج حماية التطبيقات المطبقة عليه ويمكن إدارته من قبل Intune.  

يدعم Microsoft Defender لنقطة النهاية على iOS كلا تكويني MAM
- **Intune MDM + MAM**: يمكن لمسؤولي تكنولوجيا المعلومات إدارة التطبيقات فقط باستخدام نهج حماية التطبيقات على الأجهزة المسجلة في إدارة الأجهزة المحمولة Intune (MDM).
- **MAM بدون تسجيل الجهاز**: يسمح MAM بدون تسجيل الجهاز أو MAM-WE لمسؤولي تكنولوجيا المعلومات بإدارة التطبيقات باستخدام [نهج حماية التطبيقات](/mem/intune/apps/app-protection-policy) على الأجهزة غير المسجلة في Intune MDM. وهذا يعني أنه يمكن إدارة التطبيقات بواسطة Intune على الأجهزة المسجلة مع موفري EMM التابعين لجهات خارجية. لإدارة التطبيقات باستخدام كلا التكوينين أعلاه، يجب على العملاء استخدام Intune في [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)

لتمكين هذه الإمكانية، يحتاج المسؤول إلى تكوين الاتصال بين Microsoft Defender لنقطة النهاية وIntune، وإنشاء نهج حماية التطبيق، وتطبيق النهج على الأجهزة والتطبيقات المستهدفة. 
 
يحتاج المستخدمون أيضا إلى اتخاذ خطوات لتثبيت Microsoft Defender لنقطة النهاية على أجهزتهم وتنشيط تدفق الإلحاق.

### <a name="pre-requisites"></a>المتطلبات الأساسية

1. **تحقق من تمكين الموصل**. <br> في [وحدة تحكم الأمان الموحدة](https://security.microsoft.com)، انتقل إلى **الإعدادات** >  **Endpoints****Advanced Features** >  وتأكد من تمكين **اتصال Microsoft Intune**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Defender لنقطة النهاية - موصل Intune" lightbox="images/enable-intune-connection.png":::

  
2. **تحقق من تمكين الموصل على مدخل Intune**. <br> في [مركز إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى **أمان** >  نقطة النهاية **Microsoft Defender لنقطة النهاية** وتأكد من تمكين حالة الاتصال.

  :::image type="content" source="images/app-settings.png" alt-text="إعدادات التطبيق" lightbox="images/app-settings.png":::

### <a name="create-an-app-protection-policy"></a>إنشاء نهج حماية التطبيق
 
حظر الوصول إلى بيانات تطبيق مدار أو مسحها استنادا إلى إشارات مخاطر Microsoft Defender لنقطة النهاية عن طريق إنشاء نهج حماية التطبيق.
يمكن تكوين Microsoft Defender لنقطة النهاية لإرسال إشارات التهديد لاستخدامها في نهج حماية التطبيقات (APP، المعروف أيضا باسم MAM). باستخدام هذه الإمكانية، يمكنك استخدام Microsoft Defender لنقطة النهاية لحماية التطبيقات المدارة.

1. إنشاء نهج <br>
نهج حماية التطبيقات (APP) هي قواعد تضمن بقاء بيانات المؤسسة آمنة أو مضمنة في تطبيق مدار. يمكن أن يكون النهج قاعدة يتم فرضها عندما يحاول المستخدم الوصول إلى بيانات "الشركة" أو نقلها، أو مجموعة من الإجراءات المحظورة أو المراقبة عندما يكون المستخدم داخل التطبيق. 

:::image type="content" source="images/create-policy.png" alt-text="علامة التبويب &quot;إنشاء نهج&quot; في عنصر القائمة &quot;نهج حماية التطبيقات&quot;" lightbox="images/create-policy.png":::

2. إضافة تطبيقات <br>
    أ. اختر الطريقة التي تريد بها تطبيق هذا النهج على التطبيقات على أجهزة مختلفة. ثم أضف تطبيقا واحدا على الأقل. <br>
    استخدم هذا الخيار لتحديد ما إذا كان هذا النهج ينطبق على الأجهزة غير المدارة. يمكنك أيضا اختيار استهداف نهجك للتطبيقات على الأجهزة من أي حالة إدارة.
نظرا لأن إدارة تطبيقات الأجهزة المحمولة لا تتطلب إدارة الأجهزة، يمكنك حماية بيانات الشركة على كل من الأجهزة المدارة وغير المدارة. توسيط الإدارة على هوية المستخدم، ما يزيل متطلبات إدارة الجهاز. يمكن للشركات استخدام نهج حماية التطبيقات مع إدارة أجهزة الهواتف المحمولة أو بدونها في الوقت نفسه. على سبيل المثال، ضع في اعتبارك الموظف الذي يستخدم كلا من الهاتف الذي أصدرته الشركة والكمبيوتر اللوحي الشخصي الخاص به. يتم تسجيل هاتف الشركة في MDM ومحميا بنهج حماية التطبيقات بينما يكون الجهاز الشخصي محميا بنهج حماية التطبيقات فقط.

    ب. تحديد التطبيقات<br>
    التطبيق المدار هو تطبيق يحتوي على نهج حماية التطبيقات المطبقة عليه، ويمكن إدارته من قبل Intune. يمكن إدارة أي تطبيق تم دمجه مع [Intune SDK](/mem/intune/developer/app-sdk) أو تضمينه بواسطة [أداة التفاف تطبيق Intune](/mem/intune/developer/apps-prepare-mobile-application-management) باستخدام نهج حماية تطبيق Intune. راجع القائمة الرسمية [للتطبيقات المحمية Microsoft Intune](/mem/intune/apps/apps-supported-intune-apps) التي تم إنشاؤها باستخدام هذه الأدوات والمتوفرة للاستخدام العام.

    *مثال: Outlook كتطبيق مدار*

     :::image type="content" source="images/managed-app.png" alt-text="عنصر قائمة Microsoft Outlook في جزء التنقل الأيمن" lightbox="images/managed-app.png":::
  

 3. تعيين متطلبات أمان تسجيل الدخول لنهج الحماية الخاص بك. <br>
حدد **"Setting > Max allowed device threat level** in **Device Conditions** " وأدخل قيمة. ثم حدد **الإجراء: "حظر الوصول".** Microsoft Defender لنقطة النهاية على iOS مشاركة مستوى مخاطر الجهاز هذا.

    
   :::image type="content" source="images/conditional-launch.png" alt-text="جزء شروط الجهاز" lightbox="images/conditional-launch.png":::

4. تعيين مجموعات المستخدمين الذين يجب تطبيق النهج عليهم.<br>
  حدد **المجموعات المضمنة**. ثم أضف المجموعات ذات الصلة. 


لمزيد من المعلومات حول MAM أو نهج حماية التطبيقات، راجع [إعدادات نهج حماية تطبيق iOS](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>نشر Microsoft Defender لنقطة النهاية ل MAM أو على الأجهزة غير المسجلة

يتيح Microsoft Defender لنقطة النهاية على iOS سيناريو نهج حماية التطبيق وهو متوفر في متجر تطبيقات Apple.

عند تكوين نهج حماية التطبيقات للتطبيقات لتضمين إشارات مخاطر الجهاز من Microsoft Defender لنقطة النهاية، ستتم إعادة توجيه المستخدمين لتثبيت Microsoft Defender لنقطة النهاية عند استخدام مثل هذه التطبيقات. بدلا من ذلك، يمكن للمستخدمين أيضا تثبيت أحدث إصدار من التطبيق مباشرة من متجر تطبيقات Apple.
