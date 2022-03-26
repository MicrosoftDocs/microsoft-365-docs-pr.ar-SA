---
title: Microsoft Defender لنقطة النهاية على نظام التشغيل Android - معلومات الخصوصية
description: عناصر التحكم بالخصوصية، وكيفية تكوين إعدادات النهج التي تؤثر على الخصوصية ومعلومات حول البيانات التشخيصية التي يتم تجميعها في Microsoft Defender for Endpoint على Android.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، android، الخصوصية، التشخيص
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6772539f4ca4ea819a0f8cd2a92a817fcea650f3
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/01/2022
ms.locfileid: "63573820"
---
# <a name="microsoft-defender-for-endpoint-on-android---privacy-information"></a>Microsoft Defender لنقطة النهاية على نظام التشغيل Android - معلومات الخصوصية

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يجمع Defender for Endpoint على Android المعلومات من أجهزة Android التي تم تكوينها ويخزنها في نفس المستأجر حيث لديك Defender for Endpoint. يتم تجميع المعلومات للمساعدة في الحفاظ على أمان Defender for Endpoint for Android، و تحديثه، وأداءه كما هو متوقع، ولدعم الخدمة.

لمزيد من المعلومات حول تخزين البيانات، راجع [Microsoft Defender لتخزين بيانات نقطة النهاية والخصوصية](data-storage-privacy.md).

يتم تجميع المعلومات للمساعدة في الحفاظ على أمان Defender for Endpoint for Android، و تحديثه، وأداءه كما هو متوقع ولدعم الخدمة.

لمزيد من المعلومات حول أسئلة الخصوصية الأكثر شيوعا حول Microsoft Defender ل Endpoint على الأجهزة المحمولة التي تعمل بنظامي التشغيل Android و iOS، راجع [Microsoft Defender ل Endpoint وخصوصيتك على الأجهزة المحمولة التي تعمل بنظامي التشغيل Android و iOS](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>البيانات المطلوبة

تتكون البيانات المطلوبة من البيانات الضرورية لجعل Defender for Endpoint for Android يعمل كما هو متوقع. هذه البيانات ضرورية لعملية الخدمة ويمكن أن تتضمن بيانات ذات صلة بالمستخدم والمنظمة والجهاز والتطبيقات. فيما يلي قائمة بأنواع البيانات التي يتم تجميعها:

### <a name="app-information"></a>معلومات التطبيق

معلومات حول **حزم** تطبيقات Android الضارة (APKs) على الجهاز بما في ذلك

- مصدر التثبيت
- موقع التخزين (مسار الملف) ل APK
- وقت التثبيت وحجم APK والأذونات

للأجهزة المدارة بشكل كامل ل Android Enterprise - معلومات حول حزم تطبيقات Android (APKs) المثبتة على الجهاز بما في ذلك

- اسم التطبيق واسم حزمة التطبيق
- رقم إصدار التطبيق
- اسم المورد

بالنسبة إلى Android Enterprise مع ملف تعريف العمل - معلومات حول حزم تطبيقات Android (APKs) المثبتة على ملف تعريف العمل للجهاز بما في ذلك

- اسم التطبيق واسم حزمة التطبيق
- رقم إصدار التطبيق
- اسم المورد

*يمكن لمنظمتك أيضا اختيار تكوين Defender for Endpoint لإرسال معلومات حول جميع التطبيقات المثبتة على الجهاز. بشكل افتراضي، لا يتم إرسال هذه المعلومات إلى مؤسستك.*


### <a name="web-page--network-information"></a>صفحة ويب / معلومات الشبكة

- عنوان URL الكامل لموقع ويب فقط عند الكشف عن اتصال ضار أو صفحة ويب وحظرها.
- معلومات الاتصال
- نوع البروتوكول (مثل HTTP وHTTPS وما إلى ذلك)

### <a name="device-and-account-information"></a>معلومات الجهاز الحساب

- معلومات الجهاز مثل & والوقت والإصدار Android ونموذج OEM ومعلومات CPU ومعرف الجهاز.
- معرف الجهاز هو أحد المعرفين أدناه:
  - Wi-Fi MAC لمحول الكمبيوتر
  - [Android ID](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (كما تم إنشاؤه بواسطة Android في وقت التشغيل الأول للجهاز).
  - معرف فريد عمومي تم إنشاؤه عشوائيا (GUID).

- معلومات المستأجر والجهاز والمستخدم
  - Azure Active Directory (AD) تعريف الجهاز ومحدد مستخدم Azure: يعرف الجهاز بشكل فريد، المستخدم على التوالي في Azure Active directory.
  - هوية مستأجر Azure: GUID الذي يعرف مؤسستك ضمن Azure Active Directory.
  - معرف مؤسسة Microsoft Defender ل Endpoint: معرف فريد مرتبط بالمؤسسة التي ينتمي إليها الجهاز. تسمح ل Microsoft بتحديد ما إذا كانت المشاكل تؤثر على مجموعة محددة من المؤسسات وعلى عدد المؤسسات التي تم التأثير عليها.
  - اسم المستخدم الأساسي: عنوان البريد الإلكتروني للمستخدم

### <a name="product-and-service-usage-data"></a>بيانات استخدام المنتجات والخدمات

يتم تجميع المعلومات التالية فقط لتطبيق Microsoft Defender for Endpoint المثبت على الجهاز. 

- معلومات حزمة التطبيق، بما في ذلك الاسم والإصدار حالة ترقية التطبيق.
- الإجراءات التي يتم تنفيذها في التطبيق.
- معلومات الكشف عن المخاطر، مثل اسم الخطر والفئة وما إلى ذلك.
- سجلات تقارير الأععطل التي تم إنشاؤها بواسطة Android.

## <a name="optional-data"></a>بيانات اختيارية

تتضمن البيانات الاختيارية بيانات تشخيصية وبيانات ملاحظات. البيانات التشخيصية الاختيارية هي البيانات الإضافية التي تساعدنا في إجراء تحسينات على المنتجات وتوفر معلومات محسّنة لمساعدتنا في اكتشاف المشاكل وتشخيصها ومعالجتها. تتضمن البيانات التشخيصية الاختيارية:

- استخدام التطبيق ووحدة المعالجة المركزية (CPU) والشبكات.
- حالة الجهاز من منظور التطبيق، بما في ذلك حالة الفحص وتوقيتات الفحص وأذونات التطبيق الممنوحة حالة الترقية.
- الميزات التي تم تكوينها بواسطة المسؤول.
- معلومات أساسية حول المستعرضات على الجهاز.

**يتم تجميع** "بيانات الملاحظات" من خلال الملاحظات داخل التطبيق التي يقدمها المستخدم

- عنوان البريد الإلكتروني للمستخدم، إذا اختار توفيره.
- نوع الملاحظات (ابتسامة، عابس، فكرة) وأي تعليقات ملاحظات تم تقديمها من قبل المستخدم.
