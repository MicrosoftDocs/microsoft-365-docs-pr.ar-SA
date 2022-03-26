---
title: معلومات الخصوصية - Microsoft Defender لنقطة النهاية على نظام التشغيل iOS
ms.reviewer: ''
description: وصف معلومات الخصوصية ل Microsoft Defender ل Endpoint على نظام التشغيل iOS
keywords: microsoft، defender، Microsoft Defender for Endpoint، ios، نهج، نظرة عامة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4fc5d4fb51170a70edc8664d5ccba0943b93353d
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/29/2021
ms.locfileid: "63570676"
---
# <a name="privacy-information---microsoft-defender-for-endpoint-on-ios"></a>معلومات الخصوصية - Microsoft Defender لنقطة النهاية على نظام التشغيل iOS

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!NOTE]
> يستخدم Defender ل Endpoint على iOS VPN لتوفير ميزة حماية الويب. هذه ليست VPN عادية وهي VPN محلية أو ذاتية التكرار لا تأخذ حركة المرور خارج الجهاز. **لا ترى Microsoft أو مؤسستك نشاط الاستعراض.**

يجمع Defender for Endpoint على نظام iOS المعلومات من أجهزة iOS التي تم تكوينها ويخزنها في نفس المستأجر حيث لديك Defender for Endpoint. يتم تجميع المعلومات للمساعدة في الحفاظ على أمان Defender for Endpoint على iOS، ومواكبته لأوانيه، وأداءه كما هو متوقع، ولدعم الخدمة.

لمزيد من المعلومات حول تخزين البيانات، راجع [Microsoft Defender لتخزين بيانات نقطة النهاية والخصوصية](data-storage-privacy.md).

لمزيد من المعلومات حول أسئلة الخصوصية الأكثر شيوعا حول Microsoft Defender ل Endpoint على الأجهزة المحمولة التي تعمل بنظامي التشغيل Android و iOS، راجع [Microsoft Defender ل Endpoint وخصوصيتك على الأجهزة المحمولة التي تعمل بنظامي التشغيل Android و iOS](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>البيانات المطلوبة

تتكون البيانات المطلوبة من البيانات الضرورية لجعل Defender for Endpoint على iOS يعمل كما هو متوقع. هذه البيانات ضرورية لعملية الخدمة ويمكن أن تتضمن بيانات ذات صلة بالمستخدم والمنظمة والجهاز والتطبيقات.

فيما يلي قائمة بأنواع البيانات التي يتم تجميعها:

### <a name="web-page-or-network-information"></a>صفحة ويب أو معلومات الشبكة

- اسم المجال وعنوان IP لموقع ويب فقط عند الكشف عن اتصال ضار أو صفحة ويب ضارة.

### <a name="device-and-account-information"></a>معلومات الجهاز الحساب

- معلومات الجهاز مثل & والوقت والإصدار iOS ومعلومات CPU ومعرف الجهاز، حيث معرف الجهاز هو أحد ما يلي:
  - Wi-Fi MAC لمحول الكمبيوتر
  - معرف فريد عمومي تم إنشاؤه عشوائيا (GUID)
- معلومات المستأجر والجهاز والمستخدم
  - هوية جهاز Azure Active Directory (AD) ومحدد مستخدم Azure - يحدد الجهاز بشكل فريد، المستخدم على التوالي في Azure Active directory.
  - Azure tenant ID - GUID الذي يعرف مؤسستك ضمن Azure Active Directory.
  - معرف مؤسسة Microsoft Defender ل Endpoint - معرف فريد مقترن بالمؤسسة التي ينتمي إليها الجهاز. تسمح ل Microsoft بتحديد ما إذا كانت هناك مشاكل تؤثر على مجموعة محددة من المؤسسات وعدد المؤسسات التي تم التأثير عليها.
  - اسم المستخدم الأساسي - عنوان البريد الإلكتروني للمستخدم.

### <a name="product-and-service-usage-data"></a>بيانات استخدام المنتجات والخدمات

يتم تجميع المعلومات التالية فقط لتطبيق Microsoft Defender for Endpoint المثبت على الجهاز.

- معلومات حزمة التطبيق، بما في ذلك الاسم والإصدار حالة ترقية التطبيق.
- الإجراءات التي تم اتخاذها في التطبيق.
- سجلات تقارير التعطل التي تم إنشاؤها بواسطة iOS.
- بيانات استخدام الذاكرة.

## <a name="optional-data"></a>بيانات اختيارية

تتضمن البيانات الاختيارية بيانات تشخيصية وبيانات ملاحظات من العميل. البيانات التشخيصية الاختيارية هي البيانات الإضافية التي تساعدنا في إجراء تحسينات على المنتجات وتوفر معلومات محسّنة لمساعدتنا في اكتشاف المشاكل وتشخيصها ومعالجتها. هذه البيانات هي لأغراض تشخيصية فقط، وهي غير مطلوبة للخدمة نفسها.

تتضمن البيانات التشخيصية الاختيارية:

- استخدام التطبيق ووحدة المعالجة المركزية (CPU) والشبكات ل Defender ل Endpoint.
- الميزات التي تم تكوينها من قبل مسؤول Defender ل Endpoint.

يتم تجميع "بيانات الملاحظات" من خلال الملاحظات داخل التطبيق التي يقدمها المستخدم.

- عنوان البريد الإلكتروني للمستخدم، إذا اختار توفيره.
- نوع الملاحظات (ابتسامة، عابس، فكرة) وأي تعليقات ملاحظات تم تقديمها من قبل المستخدم.

لمزيد من المعلومات، راجع [المزيد حول الخصوصية](https://aka.ms/mdatpiosprivacystatement).
