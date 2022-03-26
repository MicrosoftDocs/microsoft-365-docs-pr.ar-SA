---
title: تكوين إشارات المخاطر في Microsoft Defender لنقطة النهاية باستخدام "سياسات حماية التطبيقات" (MAM)
description: يصف كيفية تكوين إشارات مخاطر نقطة النهاية ل Microsoft Defender باستخدام سياسات حماية التطبيقات
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mde، android، التكوين، MAM، سياسات حماية التطبيقات، التطبيق المدار
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: shthota
author: shthota
manager: dansimp
ms.localizationpriority: medium
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5c18d5e9fbf628f5d4e4373b866fa300c193ac30
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63572025"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>تكوين إشارات المخاطر في Microsoft Defender لنقطة النهاية باستخدام "سياسات حماية التطبيقات" (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



يقوم Microsoft Defender ل Endpoint على نظام التشغيل Android، الذي يحمي بالفعل مستخدمي المؤسسات على سيناريوهات إدارة أجهزة المحمول (MDM)، بتوسيع الدعم الآن إلى إدارة تطبيقات الأجهزة المحمولة (MAM)، للأجهزة غير المسجلين باستخدام إدارة أجهزة Intune للأجهزة المحمولة (MDM). كما أنه يوسع هذا الدعم ليشمل العملاء الذين يستخدمون حلولا أخرى لإدارة تنقل المؤسسات، مع استخدام Intune لإدارة تطبيقات الأجهزة المحمولة (MAM). تسمح لك هذه الإمكانية بإدارة بيانات مؤسستك وحمايتها داخل تطبيق.

يتم الاستفادة من معلومات المخاطر الخاصة ب Microsoft Defender for Endpoint على Android بواسطة "سياسات حماية تطبيقات Intune" لحماية هذه التطبيقات. إن سياسات حماية التطبيق (APP) هي القواعد التي تضمن حماية بيانات المؤسسة أو احتواؤها في تطبيق مدار. يحتوي التطبيق المدار على سياسات حماية التطبيق المطبقة عليه ويمكن إدارتها بواسطة Intune.  

يدعم Microsoft Defender لنقطة النهاية على نظام التشغيل Android تكوينات MAM
- **Intune MDM + MAM**: يمكن لمسؤولي تكنولوجيا المعلومات إدارة التطبيقات فقط باستخدام "سياسات حماية التطبيقات" على الأجهزة التي تم تسجيلها في إدارة أجهزة Intune المحمولة (MDM).
- **MAM بدون تسجيل** الجهاز: تسمح MAM بدون تسجيل الجهاز أو MAM-WE لمسؤولي تكنولوجيا المعلومات بإدارة التطبيقات باستخدام "سياسات [](/mem/intune/app/app-protection-policy) حماية التطبيقات" على الأجهزة غير المسجلين في Intune MDM. وهذا يعني أنه يمكن إدارة التطبيقات بواسطة Intune على الأجهزة التي تم تسجيلها مع موفري EMM من جهة خارجية. لإدارة التطبيقات باستخدام كلا التكوينين أعلاه، يجب على العملاء استخدام Intune في [إدارة نقاط النهاية من Microsoft إدارة](https://go.microsoft.com/fwlink/?linkid=2109431)

لتمكين هذه الإمكانية، يحتاج المسؤول إلى تكوين الاتصال بين Microsoft Defender ل Endpoint و Intune، قم بإنشاء نهج حماية التطبيق، وطبق النهج على الأجهزة والتطبيقات المستهدفة. 
 
يحتاج المستخدمون أيضا إلى اتخاذ خطوات لتثبيت Microsoft Defender لنقطة النهاية على أصبعهم وتنشيط تدفق التركيب.


## <a name="admin-prerequisites"></a>المتطلبات الأساسية للمسؤول

- **التحقق من تمكين Microsoft Defender Endpoint-Intune موصل**

  أ. انتقل إلى security.microsoft.com. 

  ب. حدد **الإعدادات > نقاط النهاية> الميزات المتقدمة > Microsoft Intune اتصالك**.

  c. إذا لم يتم تشغيل الاتصال، فحدد تبديل ل تشغيل الاتصال ثم حدد **حفظ التفضيلات**.

  ![صورة ل Defender لنقطة النهاية -موصل Intune](images/enable-intune-connection.png)

  د. انتقل إلى **إدارة نقاط النهاية من Microsoft (Intune)** والتحقق من تمكين Microsoft Defender Endpoint-Intune موصل.

  ![صورة ل Defender Endpoint-Intune موصل في Intune](images/validate-intune-connector.png)

- **تمكين Microsoft Defender لنقطة النهاية على Android Connector for App Protection Policy (APP)**
  
  قم بتكوين الموصل على Intune إدارة نقاط النهاية من Microsoft لنهج حماية التطبيق:

  أ. انتقل إلى **إدارة المستأجر > الموصلات والرموز المميزة > Microsoft Defender لنقطة النهاية**.

  ب. قم تشغيل تبديل نهج حماية التطبيق لنظام التشغيل Android (كما هو متبع في لقطة الشاشة التالية).

  c. حدد **حفظ**.

  ![إعدادات التطبيق](images/app-settings.png)

- **إنشاء نهج حماية تطبيق** 
 
يمكنك حظر الوصول إلى بيانات تطبيق مدار أو مسحها استنادا إلى إشارات مخاطر نقطة النهاية من Microsoft Defender من خلال إنشاء نهج حماية التطبيق.
يمكن تكوين Microsoft Defender ل Endpoint لإرسال إشارات التهديد التي سيتم استخدامها في سياسات حماية التطبيق (APP، المعروفة أيضا ب MAM). باستخدام هذه الإمكانية، يمكنك استخدام Microsoft Defender ل Endpoint لحماية التطبيقات المدارة.

1. إنشاء نهج <br>
إن سياسات حماية التطبيق (APP) هي القواعد التي تضمن حماية بيانات المؤسسة أو احتواؤها في تطبيق مدار. يمكن أن يكون النهج قاعدة يتم فرضها عندما يحاول المستخدم الوصول إلى بيانات "الشركة" أو نقلها، أو مجموعة من الإجراءات المحظورة أو المراقبة عندما يكون المستخدم داخل التطبيق. 

![صورة لإنشاء نهج](images/create-policy.png)

2. إضافة تطبيقات <br>
    أ. اختر الطريقة التي تريد تطبيق هذا النهج بها على التطبيقات على أجهزة مختلفة. ثم أضف تطبيقا واحدا على الأقل. <br>
    استخدم هذا الخيار لتحديد ما إذا كان هذا النهج ينطبق على الأجهزة غير التي يتم استخدامها. في حالة Android، يمكنك تحديد النهج الذي ينطبق على Android Enterprise أو مسؤول الأجهزة أو الأجهزة غير الإدارية. يمكنك أيضا اختيار استهداف نهجك للتطبيقات على الأجهزة من أي حالة إدارة.
نظرا لأن إدارة تطبيقات الأجهزة المحمولة لا تتطلب إدارة الأجهزة، يمكنك حماية بيانات الشركة على كل من الأجهزة المدارة وغير المدارة. تركز الإدارة على هوية المستخدم، مما يزيل متطلبات إدارة الأجهزة. يمكن للشركات استخدام سياسات حماية التطبيق مع MDM أو بدونه في الوقت نفسه. على سبيل المثال، يجب التفكير في الموظف الذي يستخدم كلا من الهاتف الصادر عن الشركة والكمبيوتر اللوحي الشخصي الخاص به. يتم تسجيل هاتف الشركة في MDM ومحمي بواسطة سياسات حماية التطبيق بينما يكون الجهاز الشخصي محميا بواسطة سياسات حماية التطبيق فقط.

    ب. تحديد التطبيقات<br>
    التطبيق المدار هو تطبيق تم تطبيق سياسات حماية التطبيق عليه، ويمكن إدارته بواسطة Intune. يمكن إدارة أي تطبيق متكامل مع [Intune SDK](/mem/intune/developer/app-sdk) أو ملتف بواسطة أداة التفاف تطبيق [Intune](/mem/intune/developer/apps-prepare-mobile-application-management) باستخدام نهج حماية تطبيق Intune. راجع القائمة الرسمية Microsoft Intune [التطبيقات](/mem/intune/apps/apps-supported-intune-apps) المحمية التي تم إنشاؤها باستخدام هذه الأدوات والمتوفرة للاستخدام العام.

    *مثال: Outlook تطبيق مدار*

    ![صورة Outlook ك تطبيق مدار](images/managed-app.png)

 3. قم بتعيين متطلبات أمان تسجيل الدخول إلى نهج الحماية. <br>
حدد **إعداد > الحد الأقصى المسموح** به لمستوى تهديدات الجهاز في **"شروط** الجهاز" وأدخل قيمة. ثم حدد **إجراء: "حظر الوصول".** يشارك Microsoft Defender ل Endpoint على Android مستوى تهديدات الجهاز هذا.

    ![صورة تشغيل شرطي](images/conditional-launch.png)


- **تعيين مجموعات المستخدمين الذين يجب تطبيق النهج عليها.**<br>
  حدد **المجموعات المضمنة**. ثم أضف المجموعات ذات الصلة. 

    ![صورة للمسيجات](images/assignment.png)


## <a name="end-user-prerequisites"></a>المتطلبات الأساسية للمستخدم
- يجب تثبيت تطبيق الوسيط
    - Intune Company Portal
    
- لدى المستخدمين التراخيص المطلوبة للتطبيق المدار ومثبت عليه التطبيق

### <a name="end-user-onboarding"></a>ا متنبها للمستخدم 

1. سجل الدخول إلى تطبيق مدار، على سبيل المثال، Outlook. يتم تسجيل الجهاز ومزامنة نهج حماية التطبيق مع الجهاز. يتعرف نهج حماية التطبيق على حالة حماية الجهاز.  

2. حدد **متابعة**. يتم تقديم شاشة توصي بتنزيل Microsoft Defender ل Endpoint وإعداده على تطبيق Android.

3. حدد **تنزيل**. سيتم إعادة توجيهك إلى متجر التطبيقات (Google play). 

4.  قم بتثبيت تطبيق Microsoft Defender ل Endpoint (Mobile) ثم قم ب تشغيل شاشة تشغيل التطبيق المدار مرة أخرى.

  ![تثبيت MDE وشاشة تشغيل تشغيل التطبيق المدار مرة أخرى](images/download-mde.png)

5.  انقر **فوق متابعة > تشغيل**. يتم بدء تشغيل تدفق التنشيط/التنشيط في تطبيق Microsoft Defender ل Endpoint. اتبع الخطوات لإكمال عملية التكهين. سيعاد توجيهك تلقائيا إلى شاشة اعاده تشغيل التطبيق المدار، مما يشير الآن إلى أن الجهاز سليم.

6. حدد **متابعة** لتسجيل الدخول إلى التطبيق المدار. 



## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول Microsoft Defender لنقطة النهاية على نظام التشغيل Android](microsoft-defender-endpoint-android.md)
- [نشر Microsoft Defender ل Endpoint على Android باستخدام Microsoft Intune](android-intune.md)
