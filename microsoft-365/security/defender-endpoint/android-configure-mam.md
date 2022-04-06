---
title: تكوين Microsoft Defender لنقطة النهاية المخاطر باستخدام "سياسات حماية التطبيقات" (MAM)
description: يصف كيفية تكوين Microsoft Defender لنقطة النهاية المخاطر باستخدام سياسات حماية التطبيقات
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mde، android، التكوين، MAM، سياسات حماية التطبيق، التطبيق المدار
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
ms.openlocfilehash: 5d74fd2af61ee4047dd2728c28e6093efbc58ce9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471286"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>تكوين Microsoft Defender لنقطة النهاية المخاطر باستخدام "سياسات حماية التطبيقات" (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Microsoft Defender لنقطة النهاية على نظام التشغيل Android، الذي يحمي بالفعل مستخدمي المؤسسات على سيناريوهات الأجهزة المحمولة إدارة الجهاز (MDM)، الآن إلى توسيع الدعم ليشمل إدارة تطبيقات الأجهزة المحمولة (MAM)، للأجهزة غير المسجلين باستخدام إدارة أجهزة Intune المحمولة (MDM). كما أنه يوسع هذا الدعم ليشمل العملاء الذين يستخدمون حلولا أخرى لإدارة تنقل المؤسسات، مع استخدام Intune لإدارة تطبيقات الأجهزة المحمولة (MAM). تسمح لك هذه الإمكانية بإدارة بيانات مؤسستك وحمايتها داخل تطبيق.

Microsoft Defender لنقطة النهاية المعلومات المتعلقة بخطر Android بواسطة "سياسات حماية تطبيقات Intune" لحماية هذه التطبيقات. حماية التطبيقات هي القواعد التي تضمن سلامة بيانات المؤسسة أو احتواؤها في تطبيق مدار. يحتوي التطبيق المدار على سياسات حماية التطبيق المطبقة عليه ويمكن إدارتها بواسطة Intune.  

Microsoft Defender لنقطة النهاية على Android كل من تكوينات MAM
- **Intune MDM + MAM**: يمكن لمسؤولي تكنولوجيا المعلومات إدارة التطبيقات فقط باستخدام "سياسات حماية التطبيقات" على الأجهزة التي تم تسجيلها في إدارة أجهزة Intune المحمولة (MDM).
- **MAM بدون تسجيل** الجهاز: تسمح MAM بدون تسجيل الجهاز أو MAM-WE لمسؤولي تكنولوجيا المعلومات بإدارة التطبيقات باستخدام "سياسات [](/mem/intune/app/app-protection-policy) حماية التطبيقات" على الأجهزة غير المسجلين في Intune MDM. يعني هذا الاعتماد أنه يمكن إدارة التطبيقات بواسطة Intune على الأجهزة التي تم تسجيلها مع موفري EMM من جهة خارجية. لإدارة التطبيقات باستخدام كلا التكوينين أعلاه، يجب على العملاء استخدام Intune في [إدارة نقاط النهاية من Microsoft إدارة](https://go.microsoft.com/fwlink/?linkid=2109431)

لتمكين هذه الإمكانية، يحتاج المسؤول إلى تكوين الاتصال بين Microsoft Defender لنقطة النهاية و Intune، قم بإنشاء نهج حماية التطبيق، وطبق النهج على الأجهزة والتطبيقات المستهدفة. 
 
يحتاج المستخدمون أيضا إلى اتخاذ خطوات لتثبيت Microsoft Defender لنقطة النهاية على أصبعهم وتنشيط تدفق التركيب.


## <a name="admin-prerequisites"></a>المتطلبات الأساسية للمسؤول

- **التحقق من تمكين Microsoft Defender Endpoint-Intune موصل**

  أ. انتقل إلى security.microsoft.com. 

  ب. حدد **الإعدادات > نقاط النهاية> الميزات المتقدمة > Microsoft Intune اتصالك**.

  c. إذا لم يتم تشغيل الاتصال، فحدد تبديل ل تشغيل الاتصال ثم حدد **حفظ التفضيلات**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="قسم الميزات المتقدمة في مدخل Microsoft 365 Defender" lightbox="images/enable-intune-connection.png":::

  د. انتقل إلى **إدارة نقاط النهاية من Microsoft (Intune)** والتحقق من تمكين Microsoft Defender Endpoint-Intune موصل.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="جزء حالة intune-connector في مدخل Microsoft 365 Defender" lightbox="images/validate-intune-connector.png":::

- **تمكين Microsoft Defender لنقطة النهاية على Android Connector for App Protection Policy (APP)**
  
  تكوين الموصل على Intune إدارة نقاط النهاية من Microsoft حماية التطبيقات:

  أ. انتقل إلى **إدارة المستأجر > الموصلات والرموز المميزة > Microsoft Defender لنقطة النهاية**.

  ب. قم تشغيل تبديل نهج حماية التطبيق لنظام التشغيل Android (كما هو متبع في لقطة الشاشة التالية).

  c. حدد **حفظ**.

  :::image type="content" source="images/app-settings.png" alt-text="جزء إعدادات التطبيق في مدخل Microsoft 365 Defender" lightbox="images/app-settings.png":::

- **إنشاء نهج حماية تطبيق** 
 
يمكنك حظر الوصول إلى بيانات تطبيق مدار أو مسحها استنادا إلى Microsoft Defender لنقطة النهاية المخاطر من خلال إنشاء نهج حماية التطبيق.
Microsoft Defender لنقطة النهاية تكوين رسائل لإرسال إشارات التهديد التي سيتم استخدامها في سياسات حماية التطبيقات (APP، المعروفة أيضا باسم MAM). باستخدام هذه الإمكانية، يمكنك استخدام Microsoft Defender لنقطة النهاية لحماية التطبيقات المدارة.

1. إنشاء نهج <br>
حماية التطبيقات هي القواعد التي تضمن سلامة بيانات المؤسسة أو احتواؤها في تطبيق مدار. يمكن أن يكون النهج قاعدة يتم فرضها عندما يحاول المستخدم الوصول إلى بيانات "الشركة" أو نقلها، أو مجموعة من الإجراءات المحظورة أو المراقبة عندما يكون المستخدم داخل التطبيق. 

:::image type="content" source="images/create-policy.png" alt-text="علامة التبويب &quot;إنشاء نهج&quot; في صفحة نهج حماية التطبيقات في مدخل Microsoft 365 Defender" lightbox="images/create-policy.png":::

2. إضافة تطبيقات <br>
    أ. اختر الطريقة التي تريد تطبيق هذا النهج بها على التطبيقات على أجهزة مختلفة. ثم أضف تطبيقا واحدا على الأقل. <br>
    استخدم هذا الخيار لتحديد ما إذا كان هذا النهج ينطبق على الأجهزة غير التي يتم استخدامها. في Android، يمكنك تحديد النهج الذي ينطبق على Android Enterprise أو مسؤول الجهاز أو الأجهزة غير الإدارية. يمكنك أيضا اختيار استهداف نهجك للتطبيقات على الأجهزة من أي حالة إدارة.
نظرا لأن إدارة تطبيقات الأجهزة المحمولة لا تتطلب إدارة الأجهزة، يمكنك حماية بيانات الشركة على كل من الأجهزة المدارة وغير المدارة. تركز الإدارة على هوية المستخدم، مما يزيل متطلبات إدارة الأجهزة. يمكن للشركات استخدام سياسات حماية التطبيق مع MDM أو بدونه في الوقت نفسه. على سبيل المثال، يجب التفكير في الموظف الذي يستخدم كلا من الهاتف الصادر عن الشركة والكمبيوتر اللوحي الشخصي الخاص به. يتم تسجيل هاتف الشركة في MDM ومحمي بواسطة سياسات حماية التطبيق بينما يكون الجهاز الشخصي محميا بواسطة سياسات حماية التطبيق فقط.

    ب. تحديد التطبيقات<br>
    التطبيق المدار هو تطبيق تم تطبيق سياسات حماية التطبيق عليه، ويمكن إدارته بواسطة Intune. يمكن إدارة أي تطبيق متكامل مع [Intune SDK](/mem/intune/developer/app-sdk) أو ملتف بواسطة أداة التفاف تطبيق [Intune](/mem/intune/developer/apps-prepare-mobile-application-management) باستخدام نهج حماية تطبيق Intune. راجع القائمة الرسمية Microsoft Intune [التطبيقات](/mem/intune/apps/apps-supported-intune-apps) المحمية التي تم إنشاؤها باستخدام هذه الأدوات والمتوفرة للاستخدام العام.

    *مثال: Outlook تطبيق مدار*

  :::image type="content" source="images/managed-app.png" alt-text="جزء التطبيقات العامة في مدخل Microsoft 365 Defender" lightbox="images/managed-app.png":::


 3. قم بتعيين متطلبات أمان تسجيل الدخول إلى نهج الحماية. <br>
حدد **إعداد > الحد الأقصى المسموح** به لمستوى تهديدات الجهاز في **"شروط** الجهاز" وأدخل قيمة. ثم حدد **إجراء: "حظر الوصول".** Microsoft Defender لنقطة النهاية على Android مستوى خطر الجهاز هذا.

  :::image type="content" source="images/conditional-launch.png" alt-text="جزء شروط الجهاز في مدخل Microsoft 365 Defender" lightbox="images/conditional-launch.png":::
  
- **تعيين مجموعات المستخدمين الذين يجب تطبيق النهج عليها.**<br>
  حدد **المجموعات المضمنة**. ثم أضف المجموعات ذات الصلة. 

    :::image type="content" source="images/assignment.png" alt-text="جزء المجموعات المضمنة في مدخل Microsoft 365 Defender" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>المتطلبات الأساسية للمستخدم النهائي
- يجب تثبيت تطبيق الوسيط
    - Intune Company Portal
    
- لدى المستخدمين التراخيص المطلوبة للتطبيق المدار وتثبيت التطبيق

### <a name="end-user-onboarding"></a>ا متنبها للمستخدم النهائي 

1. سجل الدخول إلى تطبيق مدار، على سبيل المثال، Outlook. يتم تسجيل الجهاز ومزامنة نهج حماية التطبيق مع الجهاز. يتعرف نهج حماية التطبيق على حالة حماية الجهاز.  

2. حدد **متابعة**. يتم تقديم شاشة توصي بتنزيل Microsoft Defender لنقطة النهاية على تطبيق Android.

3. حدد **تنزيل**. سيتم إعادة توجيهك إلى متجر التطبيقات (Google play). 

4.  قم بتثبيت Microsoft Defender لنقطة النهاية (الأجهزة المحمولة) ثم قم ب تشغيل شاشة التركيب للتطبيق المدار مرة أخرى.

  :::image type="content" source="images/download-mde.png" alt-text="الصفحات التوضيحية التي تحتوي على إجراء تنزيل MDE وشاشة إعادة تشغيل التطبيق" lightbox="images/download-mde.png":::
  

5.  انقر **فوق متابعة > تشغيل**. يتم Microsoft Defender لنقطة النهاية تشغيل التطبيق/تنشيطه. اتبع الخطوات لإكمال عملية التكهين. سيعاد توجيهك تلقائيا إلى شاشة اعاده تشغيل التطبيق المدار، مما يشير الآن إلى أن الجهاز سليم.

6. حدد **متابعة** لتسجيل الدخول إلى التطبيق المدار. 



## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على Microsoft Defender لنقطة النهاية على Android](microsoft-defender-endpoint-android.md)
- [نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune](android-intune.md)
