---
title: Microsoft Defender for Endpoint على Mac
ms.reviewer: ''
description: تعرف على كيفية تثبيت Microsoft Defender لنقطة النهاية على Mac وتكوينها وتحديثها واستخدامها.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، التوزيع، إلغاء التثبيت، intune، jamf، macos، مونتيري، بيج sur، catalina، mojave، mde for mac
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d6438c7af3d3dbb8f4b2c19fdfdd04640cc8b4d2
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174966"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Microsoft Defender for Endpoint على Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يوضح هذا الموضوع كيفية تثبيت Defender لنقطة النهاية على Mac وتكوينه وتحديثه واستخدامه.

> [!CAUTION]
> من المحتمل أن يؤدي تشغيل منتجات حماية نقطة النهاية الأخرى إلى جانب Microsoft Defender لنقطة النهاية على Mac إلى مشاكل في الأداء وتأثيرات جانبية غير متوقعة. إذا كانت حماية نقطة النهاية غير التابعة ل Microsoft متطلبا مطلقا في بيئتك، فلا يزال بإمكانك الاستفادة بأمان من وظيفة Defender لنقطة النهاية على Mac الكشف التلقائي والاستجابة على النقط النهائية بعد تكوين وظيفة مكافحة الفيروسات للتشغيل في [الوضع السلبي](mac-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="whats-new-in-the-latest-release"></a>أحدث الميزات في الإصدار الأخير

[ما الجديد في Microsoft Defender لنقطة النهاية](whats-new-in-microsoft-defender-endpoint.md)

[أحدث الميزات في Microsoft Defender لنقطة النهاية على Mac](mac-whatsnew.md)

> [!TIP]
> إذا كانت لديك أي ملاحظات تريد مشاركتها، فقم بإرسالها عن طريق فتح Microsoft Defender لنقطة النهاية على Mac على جهازك والتنقل للمساعدة **في** \> **إرسال الملاحظات**.

للحصول على أحدث الميزات، بما في ذلك إمكانيات المعاينة (مثل الكشف عن تهديدات نقاط النهاية والرد عليها لأجهزة Mac)، قم بتكوين جهاز macOS الذي يعمل Microsoft Defender لنقطة النهاية ليكون جهاز "Insider".

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>كيفية تثبيت Microsoft Defender لنقطة النهاية على Mac

### <a name="prerequisites"></a>المتطلبات الأساسية

- اشتراك Defender لنقطة النهاية والوصول إلى مدخل Microsoft 365 Defender
- خبرة على مستوى المبتدئين في البرمجة النصية macOS و BASH
- الامتيازات الإدارية على الجهاز (في حالة النشر اليدوي)

### <a name="installation-instructions"></a>إرشادات التثبيت

هناك العديد من الأساليب وأدوات النشر التي يمكنك استخدامها لتثبيت وتكوين Defender لنقطة النهاية على Mac.

- أدوات إدارة الجهات الخارجية:
    - [النشر المستند إلى Microsoft Intune](mac-install-with-intune.md)
    - [النشر المستند إلى JAMF](mac-install-with-jamf.md)
    - [منتجات MDM الأخرى](mac-install-with-other-mdm.md)

- أداة سطر الأوامر:
    - [النشر اليدوي](mac-install-manually.md)

### <a name="system-requirements"></a>متطلبات النظام

يتم دعم أحدث ثلاثة إصدارات رئيسية من macOS.

> [!IMPORTANT]
> في macOS 11 (Big Sur) وما فوقه، يتطلب Microsoft Defender لنقطة النهاية ملفات تعريف تكوين إضافية. إذا كنت عميلا موجودا يقوم بالترقية من إصدارات سابقة من macOS، فتأكد من نشر ملفات تعريف التكوين الإضافية المدرجة في [ملفات تعريف التكوين الجديدة ل macOS Catalina والإصدارات الأحدث من macOS](mac-sysext-policies.md).

- 12 (مونتيري)، 11 (بيغ سور)، 10.15 (كاتالينا)
- مساحة القرص: 1 غيغابايت

إصدارات بيتا من macOS غير معتمدة.

تم دعم أجهزة macOS مع المعالجات المستندة إلى شريحة M1 رسميا منذ الإصدار 101.40.84 من العامل.

بعد تمكين الخدمة، قد تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح بالاتصالات الصادرة بينها وبين نقاط النهاية.

### <a name="licensing-requirements"></a>متطلبات الترخيص

يتطلب Microsoft Defender لنقطة النهاية على Mac أحد عروض الترخيص المجمع التالية من Microsoft:

- Microsoft 365 E5 (M365 E5)
- الأمان في Microsoft 365 E5
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Microsoft Defender for Endpoint

> [!NOTE]
> يمكن للمستخدمين المرخص لهم المؤهلين استخدام Microsoft Defender لنقطة النهاية على ما يصل إلى خمسة أجهزة متزامنة.
> يتوفر Microsoft Defender لنقطة النهاية أيضا للشراء من Cloud Solution Provider (CSP). عند الشراء عبر موفر الخدمات المشتركة (CSP)، لا يتطلب إدراج عروض الترخيص المجمع من Microsoft.

### <a name="configuring-exclusions"></a>تكوين الاستثناءات

عند إضافة الاستثناءات، ضع في اعتبارك [أخطاء الاستبعاد الشائعة برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>اتصالات الشبكة

يسرد جدول البيانات التالي القابل للتنزيل الخدمات وعناوين URL المقترنة بها التي يجب أن تكون شبكتك قادرة على الاتصال بها. يجب التأكد من عدم وجود قواعد جدار حماية أو تصفية شبكة من شأنها رفض الوصول إلى عناوين URL هذه، أو قد تحتاج إلى إنشاء قاعدة *سماح* خاصة بها.


|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|Microsoft Defender لنقطة النهاية قائمة URL للعملاء التجاريين| جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender لنقطة النهاية قائمة URL ل Gov/سحابة القطاع الحكومي/DoD | جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

يمكن Microsoft Defender لنقطة النهاية اكتشاف خادم وكيل باستخدام أساليب الاكتشاف التالية:

- تكوين تلقائي للوكيل (PAC)
- بروتوكول الكشف التلقائي ل وكيل ويب (WPAD)
- تكوين وكيل ثابت يدوي

إذا كان وكيل أو جدار حماية يمنع حركة المرور المجهولة، فتأكد من السماح بنسبة استخدام الشبكة المجهولة في عناوين URL المدرجة مسبقا.

> [!WARNING]
> الوكلاء المصادق عليهم غير معتمدين. تأكد من استخدام PAC أو WPAD أو وكيل ثابت فقط.
>
> كما أن فحص SSL واعتراض الوكلاء غير مدعومين لأسباب أمنية. تكوين استثناء لفحص SSL والخادم الوكيل الخاص بك لتمرير البيانات مباشرة من Microsoft Defender لنقطة النهاية على macOS إلى عناوين URL ذات الصلة دون اعتراض. لن تسمح إضافة شهادة اعتراضك إلى المتجر العمومي با اعتراضها.

لاختبار أن الاتصال غير محظور، افتحه <https://x.cp.wd.microsoft.com/api/report> وفي <https://cdn.x.cp.wd.microsoft.com/ping> المستعرض.

إذا كنت تفضل سطر الأوامر، يمكنك أيضا التحقق من الاتصال عن طريق تشغيل الأمر التالي في Terminal:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

يجب أن يكون الإخراج من هذا الأمر مشابها للآتي:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> نوصي بالاحتفاظ بميزة [System Integrity Protection](https://support.apple.com/HT204899) (SIP) ممكنة على أجهزة العميل. SIP هي ميزة أمان macOS مضمنة تمنع العبث بمستوى منخفض من نظام التشغيل، ويتم تمكينها بشكل افتراضي.

بمجرد تثبيت Microsoft Defender لنقطة النهاية، يمكن التحقق من صحة الاتصال عن طريق تشغيل الأمر التالي في Terminal:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>كيفية تحديث Microsoft Defender لنقطة النهاية على Mac

تنشر Microsoft تحديثات البرامج بانتظام لتحسين الأداء والأمان وتقديم ميزات جديدة. لتحديث Microsoft Defender لنقطة النهاية على Mac، يتم استخدام برنامج يسمى التحديث التلقائي لبرامج Microsoft (MAU). لمعرفة المزيد، راجع [نشر تحديثات Microsoft Defender لنقطة النهاية على Mac](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>كيفية تكوين Microsoft Defender لنقطة النهاية على Mac

تتوفر إرشادات حول كيفية تكوين المنتج في بيئات المؤسسة في [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Mac](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>نواة macOS وملحقات النظام

بدءا من macOS 11 (Big Sur)، تم ترحيل Microsoft Defender لنقطة النهاية بالكامل من ملحق kernel إلى ملحقات النظام. لا يزال ملحق Kernel قيد الاستخدام على macOS 10.15 (Catalina).

## <a name="resources"></a>الموارد

- لمزيد من المعلومات حول التسجيل أو إلغاء التثبيت أو مواضيع أخرى، راجع ["الموارد" Microsoft Defender لنقطة النهاية على Mac](mac-resources.md).
- [خصوصية Microsoft Defender لنقطة النهاية على Mac](mac-privacy.md).
