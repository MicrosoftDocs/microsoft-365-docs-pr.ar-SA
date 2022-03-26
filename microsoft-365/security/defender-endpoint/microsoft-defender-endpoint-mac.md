---
title: Microsoft Defender ل Endpoint على Mac
ms.reviewer: ''
description: تعرف على كيفية تثبيت Microsoft Defender لنقطة النهاية وتكوينه وتحديثه واستخدامه على Mac.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamf، macos، monterey، big sur، catalina، mojave، mde for mac
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
ms.openlocfilehash: 504bed69cb8380d685abfc78abe9c579313c3963
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63573254"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Microsoft Defender ل Endpoint على Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يصف هذا الموضوع كيفية تثبيت Defender for Endpoint على Mac وتكوينه وتحديثه واستخدامه.

> [!CAUTION]
> من المرجح أن يؤدي تشغيل منتجات حماية نقاط نهاية أخرى من جهة خارجية إلى جانب Microsoft Defender for Endpoint على Mac إلى مشاكل في الأداء وتأثيرات جانبية غير متوقعة. إذا كانت الحماية من نقطة نهاية غير Microsoft من المتطلبات المطلقة في بيئتك، يمكنك مع ذلك الاستفادة من وظيفة Defender for Endpoint على Mac الكشف التلقائي والاستجابة على النقط النهائية بعد تكوين وظيفة الحماية من الفيروسات للتشغيل في الوضع "غير [النشط](mac-preferences.md#enforcement-level-for-antivirus-engine)".

## <a name="whats-new-in-the-latest-release"></a>ما الجديد في الإصدار الأخير

[ما الجديد في Microsoft Defender ل Endpoint](whats-new-in-microsoft-defender-endpoint.md)

[ما الجديد في Microsoft Defender for Endpoint على Mac](mac-whatsnew.md)

> [!TIP]
> إذا كانت لديك أي ملاحظات ترغب في مشاركتها، فأرسلها عن طريق فتح Microsoft Defender لنقطة النهاية على جهاز Mac على جهازك والتنقل إلى **المساعدة** \> **في إرسال الملاحظات**.

للحصول على أحدث الميزات، بما في ذلك إمكانيات المعاينة (مثل الكشف عن تهديدات نقاط النهاية والرد عليها أجهزة Mac)، قم بتكوين جهاز macOS الذي يعمل ب Microsoft Defender for Endpoint لكي يكون جهاز "Insider".

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>كيفية تثبيت Microsoft Defender لنقطة النهاية على Mac

### <a name="prerequisites"></a>المتطلبات الأساسية

- اشتراك Defender لنقطة النهاية والوصول إلى مدخل Microsoft 365 Defender
- تجربة المستوى المبتدئ في البرمجة النصية ل macOS وBASH
- الامتيازات الإدارية على الجهاز (في حالة النشر اليدوي)

### <a name="installation-instructions"></a>إرشادات التثبيت

هناك العديد من الأساليب وأدوات النشر التي يمكنك استخدامها لتثبيت وتكوين Defender ل Endpoint على Mac.

- أدوات الإدارة الخاصة ب جهة خارجية:
    - [Microsoft Intune يستند إلى](mac-install-with-intune.md)
    - [النشر المستند إلى JAMF](mac-install-with-jamf.md)
    - [منتجات MDM الأخرى](mac-install-with-other-mdm.md)

- أداة سطر الأوامر:
    - [النشر اليدوي](mac-install-manually.md)

### <a name="system-requirements"></a>متطلبات النظام

الإصدارات الرئيسية الثلاثة الأخيرة من macOS معتمدة.

> [!IMPORTANT]
> في macOS 11 (Big Sur) والأعلى، يتطلب Microsoft Defender ل Endpoint ملفات تعريف تكوين إضافية. إذا كنت عميلا موجودا تقوم بالترقية من إصدارات سابقة من macOS، فتأكد من نشر ملفات تعريف التكوين الإضافية المدرجة في ملفات تعريف التكوين الجديدة ل [macOS Catalina](mac-sysext-policies.md) والإصدارات الأحدث من macOS.

- 12 (مونتيري)، 11 (بيغ سور)، 10.15 (كاتالينا)
- مساحة القرص: 1 غيغابايت

إصدارات بيتا من macOS غير معتمدة.

دعم أجهزة macOS مع المعالجات المستندة إلى شريحة M1 مدعوم رسميا منذ الإصدار 101.40.84 من الوكيل.

بعد تمكين الخدمة، قد تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح للاتصالات الصادرة بينها وبين نقاط النهاية.

### <a name="licensing-requirements"></a>متطلبات الترخيص

يتطلب Microsoft Defender ل Endpoint على جهاز Mac أحد عروض الترخيص الكلي من Microsoft التالية:

- Microsoft 365 E5 (M365 E5)
- الأمان في Microsoft 365 E5
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Microsoft Defender لنقطة النهاية

> [!NOTE]
> يمكن للمستخدمين المرخصين المؤهلين استخدام Microsoft Defender ل Endpoint على ما يصل إلى خمسة أجهزة متزامنة.
> يتوفر Microsoft Defender ل Endpoint أيضا للشراء من Cloud Solution Provider (CSP). عند الشراء عبر CSP، لا يتطلب إدراج عروض الترخيص الكلي من Microsoft.

### <a name="configuring-exclusions"></a>تكوين الاستثناءات

عند إضافة الاستثناءات، يجب الانتباه إلى [أخطاء الاستثناء الشائعة برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>اتصالات الشبكة

يسرد جدول البيانات القابل للتنزيل التالي الخدمات وقوائم URL المقترنة بها التي يجب أن تتمكن شبكتك من الاتصال بها. يجب أن تضمن عدم وجود جدار حماية أو قواعد لتصفية الشبكة من شأنها رفض الوصول إلى عناوين URL هذه، أو قد تحتاج إلى إنشاء قاعدة السماح لها بشكل  خاص.


|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|قائمة URL ل Microsoft Defender لنقطة النهاية للعملاء التجاريين | جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| قائمة URL ل Microsoft Defender لنقطة النهاية لعملاء Gov/سحابة القطاع الحكومي/DoD| جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|




يمكن ل Microsoft Defender ل Endpoint اكتشاف خادم وكيل باستخدام أساليب الاكتشاف التالية:

- Autoconfig الوكيل (PAC)
- بروتوكول Autodiscovery لوكيل ويب (WPAD)
- تكوين وكيل ثابت يدوي

إذا كان الوكيل أو جدار الحماية يمنع حركة مرور مجهولة، فتأكد من أن حركة المرور المجهولة مسموح بها في عناوين URL المدرجة سابقا.

> [!WARNING]
> إن المحترفين المصادق عليه غير معتمدين. تأكد من استخدام PAC أو WPAD أو وكيل ثابت فقط.
>
> كما أن فحص SSL وتكويلات التقاطع غير معتمدة أيضا لأسباب تتعلق بالأمن. قم بتكوين استثناء لفحص SSL وخادم الوكيل الخاص بك لتمرير البيانات مباشرة من Microsoft Defender ل Endpoint على macOS إلى عناوين URL ذات الصلة دون أي اعتراض. لن تسمح إضافة شهادة التقاطع إلى المتجر العام بالتقاطع.

لاختبار عدم حظر الاتصال <https://x.cp.wd.microsoft.com/api/report> ، افتحه وفي <https://cdn.x.cp.wd.microsoft.com/ping> مستعرض.

إذا كنت تفضل سطر الأوامر، يمكنك أيضا التحقق من الاتصال عن طريق تشغيل الأمر التالي في المحطة الطرفية:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

يجب أن يكون الإخراج من هذا الأمر مماثلا للمخرجات التالية:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> نوصيك باإبقاء [حماية تكامل](https://support.apple.com/HT204899) النظام (SIP) ممكنة على أجهزة العميل. إن SIP هي ميزة أمان macOS مضمنة تمنع التلاعب على مستوى منخفض في نظام التشغيل، وهي يتم تمكينها بشكل افتراضي.

بمجرد تثبيت Microsoft Defender ل Endpoint، يمكن التحقق من الاتصال عن طريق تشغيل الأمر التالي في المحطة الطرفية:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>كيفية تحديث Microsoft Defender لنقطة النهاية على Mac

تنشر Microsoft تحديثات البرامج بشكل منتظم لتحسين الأداء والأمان وتقديم ميزات جديدة. لتحديث Microsoft Defender ل Endpoint على Mac، يتم استخدام برنامج يسمى التحديث التلقائي ل Microsoft (MAU). لمعرفة المزيد، راجع [نشر تحديثات ل Microsoft Defender لنقطة النهاية على Mac](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>كيفية تكوين Microsoft Defender لنقطة النهاية على Mac

تتوفر إرشادات حول كيفية تكوين المنتج في بيئات المؤسسة في تعيين التفضيلات ل [Microsoft Defender ل Endpoint على Mac](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>macOS kernel وملحقات النظام

بالمحاذاة مع تطور macOS، نقوم بإعداد تحديث Microsoft Defender ل Endpoint على Mac الذي تستفيد منه ملحقات النظام بدلا من ملحقات kernel. للحصول على التفاصيل ذات الصلة، راجع [ما الجديد في Microsoft Defender for Endpoint على Mac](mac-whatsnew.md).

## <a name="resources"></a>الموارد

- لمزيد من المعلومات حول التسجيل أو إلغاء تثبيته أو مواضيع أخرى، راجع [موارد ل Microsoft Defender ل Endpoint على Mac](mac-resources.md).
- [الخصوصية ل Microsoft Defender ل Endpoint على Mac](mac-privacy.md).
