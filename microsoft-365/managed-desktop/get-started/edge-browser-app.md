---
title: Microsoft Edge
description: يشرح كيفية نشر Microsoft Edge المستعرض وتحديثه
keywords: المستعرض، Microsoft Managed Desktop، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: aab02ec260f0131ab32d28834152f50b84abce21
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/08/2022
ms.locfileid: "63568303"
---
# <a name="microsoft-edge"></a>Microsoft Edge

[Microsoft Edge](https://www.microsoft.com/edge) أداء وقيمة من المستوى العالمي مع:

- المزيد من الخصوصية والحماية من التهديدات الخارجية.
- الوصول السريع إلى Office والملفات والمواقع المضمنة البحث من Microsoft.
- تجربة سلسة من خلال المزامنة عبر أجهزتك باستخدام الدعم عبر الأنظمة الأساسية وملفات التعريف.

> [!IMPORTANT]
> سيتم رفض تطبيق سطح المكتب Internet Explorer 11 وسيخرج من الدعم في 15 يونيو 2022 (للحصول على قائمة بما هو في نطاقه، راجع [الأسئلة الشائعة](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/internet-explorer-11-desktop-app-retirement-faq/ba-p/2366549). يمكن فتح تطبيقات IE11 والمواقع نفسها التي تستخدمها اليوم في Microsoft Edge وضع Internet Explorer. [تعرف على المزيد هنا](https://blogs.windows.com/windowsexperience/2021/05/19/the-future-of-internet-explorer-on-windows-10-is-in-microsoft-edge/).

## <a name="updates-to-microsoft-edge"></a>تحديثات Microsoft Edge

يقوم Microsoft Managed Desktop [بنشر القناة "](/deployedge/microsoft-edge-channels#extended-stable-channel)ثبات ممتد" Microsoft Edge، التي يتم تحديثها تلقائيا كل ثمانية أسابيع. يتم طرح التحديثات على القناة الثابتة الموسعة تدريجيا من Microsoft Edge [](/deployedge/microsoft-edge-update-progressive-rollout) المنتج لضمان أفضل تجربة للعملاء.

يتم [نشر قناة Beta](/deployedge/microsoft-edge-channels#beta-channel) على الأجهزة الموجودة في المجموعة اختبار للتحقق من صحة تمثيلية داخل المؤسسة. يتم دعم هذه القناة بالكامل وتحديثها تلقائيا بالميزات الجديدة كل أربعة أسابيع تقريبا.

> [!IMPORTANT]
> للتأكد من Microsoft Edge التحديثات بشكل صحيح، لا تعدل Microsoft Edge [التحديث.](/deployedge/microsoft-edge-update-policies)

## <a name="settings-managed-by-microsoft-managed-desktop"></a>الإعدادات مدار بواسطة Microsoft Managed Desktop

لقد أنشأ Microsoft Managed Desktop مجموعة افتراضية من Microsoft Edge لتأمين المستعرض. تكون إعدادات المستعرض الافتراضية كما يلي:

### <a name="microsoft-edge-extensions"></a>Microsoft Edge الملحقات

يقوم أساس الأمان Microsoft Edge على أجهزة سطح المكتب المدارة من Microsoft بتعيين نهجين لتعطيل جميع ملحقات Chrome والمستخدمين الآمنين. لتمكين الملحقات ونشرها في بيئتك، راجع الإعدادات [التي تديرها](#settings-you-manage).

| الإعداد | القيمة الافتراضية | الوصف |
| ------ | ------ | ------ |
| قائمة حظر تثبيت الملحق | الكل | يعمل Microsoft Managed Desktop على تعيين هذا النهج لمنع تثبيت ملحقات Chrome على نقاط النهاية المدارة. هناك مخاطر معروفة مقترنة Chromium الملحق بما في ذلك الحماية من فقدان البيانات والخصوصية والمخاطر الأخرى التي يمكن أن تعرض الأجهزة للخطر. |
| السماح لمضيفي المراسلة الأصلية على مستوى المستخدم (مثبت بدون أذونات المسؤول) | معطل | من خلال تعطيل هذا النهج، Microsoft Edge استخدام مضيفي المراسلة الأصليين المثبتة على مستوى النظام فقط. إن مضيفي المراسلة الأصليين هم جزء من ملحقات Chrome، التي تسمح للمستعرض بالتفاعل مع أجزاء أخرى من نقطة نهاية المستخدم، مما يؤدي إلى إنشاء مخاوف أمنية متنوعة. |

### <a name="secure-sockets-layer-tlsssl"></a>طبقة مآخذ توصيل آمنة (TLS/SSL)

| الإعداد | القيمة الافتراضية | الوصف
| ------ | ------ | ------ |
| الحد الأدنى من إصدار TLS | الحد الأدنى المعتمد ل TLS 1.2 | إذا كنت تريد استخدام TLS 1.1 الأقل أمانا، يمكنك تقديم طلب للقيام بذلك. |
| السماح للمستخدمين ب المتابعة من صفحة تحذير SSL | معطل | لا نوصي بتمكين هذا الإعداد لأنه يسمح للمستخدمين بزيارة المواقع التي بها أخطاء TSL. |

### <a name="microsoft-defender-smartscreen"></a>Microsoft Defender SmartScreen

| الإعداد | القيمة الافتراضية | الوصف
| ------ | ------ | ------ |
| تكوين شاشة smartScreen Windows Defender | تم التمكين | يتم تمكينه بشكل افتراضي للمساعدة في حماية المستخدمين. |
| Windows SmartScreen ل Defender للمواقع | تم التمكين | لا نوصي بتعطيل هذا الإعداد نظرا لأن ذلك سيسمح للمستخدمين بتجاهل التحذيرات والمتابعة إلى المواقع التي يحتمل أن تكون ضارة. |
| منع تجاوز تحذيرات SmartScreen Windows Defender حول التنزيلات | تم التمكين | لا نوصي بتعطيل هذا الإعداد نظرا لأن ذلك سيسمح للمستخدمين بتجاهل التحذيرات وإكمال التنزيلات التي لم يتم التحقيق فيها. |

### <a name="adobe-flash"></a>Adobe Flash

| الإعداد | القيمة الافتراضية | الوصف
| ------ | ------ | ------ |
| إعداد Adobe Flash الافتراضي | معطل | لا نوصي باستخدام Flash بسبب مخاطر الأمان المقترنة. <br><br> إذا كنت لا تزال لديك عمليات تعتمد على Flash، ف قم بتعيين نهج **[المكون الإضافيتمكين](/deployedge/microsoft-edge-policies#pluginsallowedforurls)** Flash للمواقع التي تحتاج إليه. إذا لم تتمكن من الاحتفاظ بالقائمة المسموح بها بالمواقع لاستخدام Flash، فطلب تغيير لتغيير القيمة إلى انقر للتشغيل، مما يسمح للمستخدمين باختيار الوقت المناسب لتشغيل Flash. |

### <a name="password-manager"></a>مدير كلمة المرور

| الإعداد | القيمة الافتراضية | الوصف
| ------ | ------ | ------ |
| تمكين حفظ كلمات المرور إلى مدير كلمة المرور | معطل | يتم تعطيل مدير كلمة المرور بشكل افتراضي. إذا كنت تريد تمكين هذه الميزة، فطلب طلب دعم ويمكن لمهندسي الخدمة تمكين الإعداد في بيئتك. |

### <a name="internet-explorer-mode-in-microsoft-edge"></a>وضع Internet Explorer في Microsoft Edge

يجعل وضع IE Microsoft Edge من السهل استخدام كل المواقع التي تحتاجها مؤسستك في مستعرض واحد. فهو يستخدم محرك Chromium للمواقع المتوافقة مع Chromium العرض. Microsoft Edge استخدام محرك Trident MSHTML من Internet Explorer 11 (IE11) للمواقع التي لا تملك أو لديها تبعيات على وظيفة IE. [معرفة المزيد](/DeployEdge/edge-ie-mode)

يمكن Microsoft Managed Desktop وضع Internet Explorer للأجهزة بشكل افتراضي.

| الإعداد | القيمة الافتراضية | الوصف
| ------ | ------ | ------ |
| تكامل وضع Internet Explorer | وضع Internet Explorer | بشكل افتراضي، يتم تعيين الأجهزة لاستخدام وضع Internet Explorer، ولكن يمكنك تعيينها لفتح المواقع في نافذة Internet Explorer 11 مستقلة بدلا من ذلك. لتغيير هذا السلوك، يجب تقديم طلب دعم. |
| إضافة مواقع إلى قائمة مواقع "وضع المؤسسة" | الاطلاع على الوصف | لكي تفتح المواقع في وضع Internet Explorer، يجب تضمينها في قائمة [موقع المؤسسة](/DeployEdge/edge-ie-mode-sitelist). تقع على عاتقك مسؤولية الاحتفاظ بالقائمة "موقع المؤسسة" ونشرها. للحصول على التفاصيل، راجع [تكوين باستخدام نهج "تكوين قائمة موقع وضع المؤسسة](/DeployEdge/edge-ie-mode-policies#configure-using-the-configure-the-enterprise-mode-site-list-policy)". |

### <a name="other-settings"></a>إعدادات أخرى

| الإعداد | القيمة الافتراضية | الوصف
| ------ | ------ | ------ |
| تمكين عزل الموقع لكل موقع | تم التمكين | عند تمكين هذا النهج، لا يمكن للمستخدمين إلغاء الاشتراك في السلوك الافتراضي الذي يتم فيه تشغيل كل موقع في العملية الخاصة به. |
| أنظمة المصادقة المعتمدة | NTLM، التفاوض | لا يدعم Microsoft Managed Desktop أنظمة المصادقة الأساسية أو مصادقة المهضم. |
| استيراد بيانات وإعدادات مستعرض آخر تلقائيا عند التشغيل الأول | استيراد كل أنواع البيانات والإعدادات المعتمدة تلقائيا من المستعرض الافتراضي. | مع تطبيق هذا النهج، ستتخطى تجربة التشغيل الأولى مقطع الاستيراد، مما يقلل من تفاعل المستخدم. سيتم ترحيل بيانات المستعرض من الإصدارات القديمة من Microsoft Edge البيانات دائما بصمت في التشغيل الأول، بغض النظر عن هذا الإعداد. |

## <a name="settings-you-manage"></a>الإعدادات التي تديرها

يمكنك نشر أي إعدادات Microsoft Edge لم يتم وصفها مسبقا باستخدام ملف تعريف القوالب الإدارية في Microsoft Intune. للحصول على التفاصيل، [راجع تكوين Microsoft Edge نهج مع Microsoft Intune](/deployedge/configure-edge-with-intune). إذا كنت تريد تقييم نهج غير مضمن حاليا في Microsoft Edge الإدارية في Intune، يمكنك استخدام إعدادات مخصصة للأجهزة Windows 10 Intune.

| الإعداد | الوصف
| ------ | ------ |
| تمكين ملحقات Chrome معينة | يوفر القالب الإداري إعدادا لنشر ملحقات Chrome معينة باستخدام Microsoft Intune. يمكنك العثور عليه في **تكوين الكمبيوتر > Microsoft Edge > الملحقات > السماح بتثبيت** ملحقات معينة. |
| تثبيت الملحقات بصمت | يمكنك أيضا استخدام القالب الإداري لتعيين Microsoft Edge لتثبيت الملحقات دون تنبيه المستخدم. يمكنك العثور عليه في تكوين الكمبيوتر > Microsoft Edge > **الملحقات > التحكم في الملحقات المثبتة بصمت**. |
| Microsoft Edge التحديث | للتأكد من Microsoft Edge التحديثات بشكل صحيح، لا تعدل Microsoft Edge [التحديث.](/deployedge/microsoft-edge-update-policies) |
| سياسات المؤسسة الشائعة الأخرى | Microsoft Edge العديد من السياسات الأخرى. فيما يلي بعض من أكثرها شيوعا: <ul> <li> [تكوين المواقع على قائمة مواقع المؤسسة ووضع IE](/deployedge/edge-ie-mode-sitelist)</li><li> [تكوين إعدادات صفحة البدء والصفحة الرئيسية وصفحة علامة التبويب الجديدة](/deployedge/microsoft-edge-policies#startup-home-page-and-new-tab-page)</li> <li> [تكوين إعداد لعبة Surf](/deployedge/microsoft-edge-policies#allowsurfgame)</li> <li> [تكوين إعدادات الخادم الوكيل](/deployedge/microsoft-edge-policies#proxy-server)</li></ul>
