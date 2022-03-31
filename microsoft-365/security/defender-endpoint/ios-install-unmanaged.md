---
title: نشر Microsoft Defender لنقطة النهاية على ميزات iOS
description: يصف كيفية نشر Microsoft Defender ل Endpoint على أجهزة iOS غير المجهزة.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، ios، تكوين، ميزات، ios
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
ms.openlocfilehash: 082e03100c366294a193d5fc7eb3cf0dd868caa6
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63578421"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>نشر Microsoft Defender لنقطة النهاية على أجهزة iOS غير المزمة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> يستخدم Defender for Endpoint على نظام iOS VPN لتوفير ميزة حماية الويب. هذه ليست VPN عادية وهي VPN محلية/ذاتية التكرار لا تأخذ حركة المرور خارج الجهاز.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>تكوين إشارات مخاطر نقطة النهاية ل Microsoft Defender في نهج حماية التطبيق (MAM)

يعمل Microsoft Defender لنقطة النهاية على نظام التشغيل iOS، الذي يحمي بالفعل مستخدمي المؤسسات على سيناريوهات إدارة أجهزة المحمول (MDM)، على توسيع الدعم الآن ليشمل إدارة تطبيقات الأجهزة المحمولة (MAM)، للأجهزة غير المسجلين باستخدام إدارة أجهزة Intune للأجهزة المحمولة (MDM). كما أنه يوسع هذا الدعم ليشمل العملاء الذين يستخدمون حلولا أخرى لإدارة تنقل المؤسسات، مع استخدام Intune لإدارة تطبيقات الأجهزة المحمولة (MAM). تسمح لك هذه الإمكانية بإدارة بيانات مؤسستك وحمايتها داخل تطبيق.

يتم الاستفادة من Microsoft Defender ل Endpoint على معلومات التهديدات على نظام التشغيل iOS بواسطة "سياسات حماية تطبيقات Intune" لحماية هذه التطبيقات. إن سياسات حماية التطبيق (APP) هي القواعد التي تضمن حماية بيانات المؤسسة أو احتواؤها في تطبيق مدار. يحتوي التطبيق المدار على سياسات حماية التطبيق المطبقة عليه ويمكن إدارتها بواسطة Intune.  

يدعم Microsoft Defender لنقطة النهاية على نظام التشغيل iOS تكوينات MAM
- **Intune MDM + MAM**: يمكن لمسؤولي تكنولوجيا المعلومات إدارة التطبيقات فقط باستخدام "سياسات حماية التطبيقات" على الأجهزة التي تم تسجيلها في إدارة أجهزة Intune المحمولة (MDM).
- **MAM بدون تسجيل** الجهاز: تسمح MAM بدون تسجيل الجهاز أو MAM-WE لمسؤولي تكنولوجيا المعلومات بإدارة التطبيقات باستخدام "سياسات [](/mem/intune/app/app-protection-policy) حماية التطبيقات" على الأجهزة غير المسجلين في Intune MDM. وهذا يعني أنه يمكن إدارة التطبيقات بواسطة Intune على الأجهزة التي تم تسجيلها مع موفري EMM من جهة خارجية. لإدارة التطبيقات باستخدام كلا التكوينين أعلاه، يجب على العملاء استخدام Intune في [إدارة نقاط النهاية من Microsoft إدارة](https://go.microsoft.com/fwlink/?linkid=2109431)

لتمكين هذه الإمكانية، يحتاج المسؤول إلى تكوين الاتصال بين Microsoft Defender ل Endpoint و Intune، قم بإنشاء نهج حماية التطبيق، وطبق النهج على الأجهزة والتطبيقات المستهدفة. 
 
يحتاج المستخدمون أيضا إلى اتخاذ خطوات لتثبيت Microsoft Defender لنقطة النهاية على أصبعهم وتنشيط تدفق التركيب.

### <a name="pre-requisites"></a>المتطلبات الأساسية

1. **تحقق من تمكين الموصل**. <br> في وحدة [تحكم الأمان الموحدة](https://security.microsoft.com)، **انتقل إلى الإعدادات** >  **EndpointsAdvanced** >  **Features** وتأكد من تمكين Microsoft Intune الاتصال.

  ![صورة ل Defender لنقطة النهاية -موصل Intune](images/enable-intune-connection.png)
  
2. **تحقق من تمكين الموصل على مدخل Intune**. <br> في [مركز إدارة Microsoft Endpoint،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **Endpoint SecurityMicrosoft** >  **Defender ل Endpoint** وتأكد من تمكين حالة الاتصال.

  ![إعدادات التطبيق](images/app-settings.png)

### <a name="create-an-app-protection-policy"></a>إنشاء نهج حماية تطبيق
 
يمكنك حظر الوصول إلى بيانات تطبيق مدار أو مسحها استنادا إلى إشارات مخاطر نقطة النهاية من Microsoft Defender من خلال إنشاء نهج حماية التطبيق.
يمكن تكوين Microsoft Defender ل Endpoint لإرسال إشارات التهديد التي سيتم استخدامها في سياسات حماية التطبيق (APP، المعروفة أيضا ب MAM). باستخدام هذه الإمكانية، يمكنك استخدام Microsoft Defender ل Endpoint لحماية التطبيقات المدارة.

1. إنشاء نهج <br>
إن سياسات حماية التطبيق (APP) هي القواعد التي تضمن حماية بيانات المؤسسة أو احتواؤها في تطبيق مدار. يمكن أن يكون النهج قاعدة يتم فرضها عندما يحاول المستخدم الوصول إلى بيانات "الشركة" أو نقلها، أو مجموعة من الإجراءات المحظورة أو المراقبة عندما يكون المستخدم داخل التطبيق. 

![صورة لإنشاء نهج](images/create-policy.png)

2. إضافة تطبيقات <br>
    أ. اختر الطريقة التي تريد تطبيق هذا النهج بها على التطبيقات على أجهزة مختلفة. ثم أضف تطبيقا واحدا على الأقل. <br>
    استخدم هذا الخيار لتحديد ما إذا كان هذا النهج ينطبق على الأجهزة غير التي يتم استخدامها. يمكنك أيضا اختيار استهداف نهجك للتطبيقات على الأجهزة من أي حالة إدارة.
نظرا لأن إدارة تطبيقات الأجهزة المحمولة لا تتطلب إدارة الأجهزة، يمكنك حماية بيانات الشركة على كل من الأجهزة المدارة وغير المدارة. تركز الإدارة على هوية المستخدم، مما يزيل متطلبات إدارة الأجهزة. يمكن للشركات استخدام سياسات حماية التطبيق مع MDM أو بدونه في الوقت نفسه. على سبيل المثال، يجب التفكير في الموظف الذي يستخدم كلا من الهاتف الصادر عن الشركة والكمبيوتر اللوحي الشخصي الخاص به. يتم تسجيل هاتف الشركة في MDM ومحمي بواسطة سياسات حماية التطبيق بينما يكون الجهاز الشخصي محميا بواسطة سياسات حماية التطبيق فقط.

    ب. تحديد التطبيقات<br>
    التطبيق المدار هو تطبيق تم تطبيق سياسات حماية التطبيق عليه، ويمكن إدارته بواسطة Intune. يمكن إدارة أي تطبيق متكامل مع [Intune SDK](/mem/intune/developer/app-sdk) أو ملتف بواسطة أداة التفاف تطبيق [Intune](/mem/intune/developer/apps-prepare-mobile-application-management) باستخدام نهج حماية تطبيق Intune. راجع القائمة الرسمية Microsoft Intune [التطبيقات](/mem/intune/apps/apps-supported-intune-apps) المحمية التي تم إنشاؤها باستخدام هذه الأدوات والمتوفرة للاستخدام العام.

    *مثال: Outlook تطبيق مدار*

    ![صورة Outlook ك تطبيق مدار](images/managed-app.png)

 3. قم بتعيين متطلبات أمان تسجيل الدخول إلى نهج الحماية. <br>
حدد **إعداد > الحد الأقصى المسموح** به لمستوى تهديدات الجهاز في **"شروط** الجهاز" وأدخل قيمة. ثم حدد **إجراء: "حظر الوصول".** يشارك Microsoft Defender لنقطة النهاية على نظام التشغيل iOS مستوى تهديدات الجهاز هذا.

    ![صورة تشغيل شرطي](images/conditional-launch.png)

4. تعيين مجموعات المستخدمين الذين يجب تطبيق النهج عليها.<br>
  حدد **المجموعات المضمنة**. ثم أضف المجموعات ذات الصلة. 


لمزيد من المعلومات حول MAM أو نهج حماية التطبيق، راجع إعدادات نهج [حماية تطبيق iOS](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>نشر Microsoft Defender لنقطة النهاية ل MAM أو على الأجهزة غير التي تم نشرها

يمكن Microsoft Defender ل Endpoint على نظام التشغيل iOS سيناريو نهج حماية التطبيق وهو متوفر في متجر تطبيقات Apple.

عند تكوين سياسات حماية التطبيقات للتطبيقات لتضمين إشارات مخاطر الجهاز من Microsoft Defender لنقطة النهاية، سيتم إعادة توجيه المستخدمين لتثبيت Microsoft Defender ل Endpoint عند استخدام مثل هذه التطبيقات. بدلا من ذلك، يمكن للمستخدمين أيضا تثبيت أحدث إصدار من التطبيق مباشرة من متجر تطبيقات Apple.
