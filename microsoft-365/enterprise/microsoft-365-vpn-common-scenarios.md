---
title: سيناريوهات تقسيم VPN الشائعة للانقسام Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: سيناريوهات تقسيم VPN الشائعة للانقسام Microsoft 365
ms.openlocfilehash: 26f4cf10de3282c5257592a26ea61d073a0d3cd4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705173"
---
# <a name="common-vpn-split-tunneling-scenarios-for-microsoft-365"></a>سيناريوهات تقسيم VPN الشائعة للانقسام Microsoft 365

>[!NOTE]
>هذه المقالة هي جزء من مجموعة من المقالات التي تعالج Microsoft 365 للمستخدمين البعيدين.

>- للحصول على نظرة عامة حول استخدام تقسيم VPN لتحسين Microsoft 365 للمستخدمين البعيدين، راجع نظرة عامة[: تقسيم VPN](microsoft-365-vpn-split-tunnel.md) للتحكم Microsoft 365.
>- للحصول على إرشادات مفصلة حول تنفيذ تقسيم VPN، راجع تنفيذ تقسيم [VPN Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- للحصول على إرشادات حول تأمين Teams الوسائط في بيئات تقسيم VPN التي تم تقسيمها، راجع تأمين Teams الوسائط لتقسيم [VPN](microsoft-365-vpn-securing-teams.md).
>- للحصول على معلومات حول كيفية تكوين الدفق والأحداث المباشرة في بيئات VPN، راجع اعتبارات خاصة للبث والأحداث المباشرة [في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md).
>- للحصول على معلومات حول تحسين Microsoft 365 المستأجر على مستوى العالم للمستخدمين في الصين، راجع Microsoft 365 تحسين أداء [المستخدمين في الصين](microsoft-365-networking-china.md).

في القائمة أدناه، سترى سيناريوهات VPN الأكثر شيوعا في بيئات المؤسسة. يقوم معظم العملاء عادة بتشغيل النموذج 1 (VPN Forcedون). سيساعدك هذا القسم على الانتقال بسرعة وأمان إلى النموذج **2**، الذي يمكن تحقيقه من خلال جهد بسيط نسبيا، كما سيستفيد بشكل كبير من أداء الشبكة وتجربة المستخدم.

| نموذج | الوصف |
| --- | --- |
| [1. VPN Forcedهانا](#1-vpn-forced-tunnel) | 100٪ من حركة المرور يتم الوصول إلى VPN، بما في ذلك المحلي والإنترنت وكل O365/M365 |
| [2. VPN Forcedهاين مع استثناءات قليلة](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | يتم استخدام جزء VPN افتراضيا (يشير المسار الافتراضي إلى VPN)، مع عدد قليل من أهم سيناريوهات الإعفاء المسموح لها بالمباشرة |
| [3. VPN Forcedهاين مع استثناءات واسعة](#3-vpn-forced-tunnel-with-broad-exceptions) | تستخدم خدمة VPN بشكل افتراضي (نقاط المسار الافتراضية إلى VPN)، مع استثناءات واسعة النطاق المسموح لها بالمباشرة (مثل كل Microsoft 365 وكل Salesforce وكل التكبير/التصغير) |
| [4. VPN Selective](#4-vpn-selective-tunnel) | تستخدم شبكة VPN للخدمات المستندة إلى corpnet فقط. المسار الافتراضي (الإنترنت وجميع الخدمات المستندة إلى الإنترنت) يتم توجيهه مباشرة. |
| [5. لا توجد VPN](#5-no-vpn) | تباين من #2. بدلا من VPN القديم، يتم نشر جميع خدمات corpnet من خلال نهج الأمان الحديثة (مثل Zscaler ZPA و Azure Active Directory (Azure AD) Proxy/MCAS وغير ذلك) |

## <a name="1-vpn-forced-tunnel"></a>1. VPN Forcedهانا

سيناريو البدء الأكثر شيوعا لمعظم عملاء المؤسسة. يتم استخدام VPN إجباري، مما يعني أنه يتم توجيه 100٪ من حركة المرور إلى شبكة الشركة سواء كانت نقطة النهاية موجودة ضمن شبكة الشركة أم لا. يتم بعد ذلك تثبيت أي حركة مرور خارجية (إنترنت) مثل Microsoft 365 الإنترنت أو الاستعراض عبر الإنترنت خارج معدات الأمان المحلية مثل التكئات. في الحالة الحالية التي يعمل فيها ما يقرب من 100٪ من المستخدمين عن بعد، فإن هذا النموذج يضع تحميلا عاليا على البنية الأساسية للشبكة الافتراضية (VPN) ومن المرجح أن يعيق بشكل كبير أداء كل عمليات حركة مرور الشركات، وبالتالي تعمل المؤسسة بكفاءة في وقت ينتهى فيه الازدحام.

![VPN Forcedهاي نموذج 1.](../media/vpn-split-tunneling/vpn-model-1.png)

## <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. VPN Forcedهاين مع عدد صغير من الاستثناءات الموثوق بها

أكثر فعالية بكثير لكي تعمل المؤسسة ضمنها. يسمح هذا النموذج ببعض نقاط النهاية المعرفة والمتحكم بها والتي تكون حساسة للتحميل و زمن الانتقال لتجاوز مشكلة VPN و الانتقال مباشرة إلى Microsoft 365 الخدمة. يعمل هذا على تحسين أداء الخدمات التي تم تفريغها بشكل ملحوظ، كما يقلل الحمل على البنية الأساسية ل VPN، مما يسمح للعناصر التي لا تزال بحاجة إليها بالعمل مع أقل محتوى للموارد. هذا هو النموذج الذي تركز عليه هذه المقالة على المساعدة في الانتقال إلى كما يتيح اتخاذ إجراءات بسيطة ومحددة بسرعة مع العديد من النتائج الإيجابية.

![نموذج VPN المنقسم للانقسام VPN 2.](../media/vpn-split-tunneling/vpn-model-2.png)

## <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. VPN Forcedهاين مع استثناءات واسعة

توسيع نطاق النموذج 2. بدلا من إرسال مجموعة صغيرة من نقاط النهاية المعرفة مباشرة، فإنه يرسل بدلا من ذلك كل عمليات المرور مباشرة إلى الخدمات الموثوق بها مثل Microsoft 365 وS salesForce. هذا يقلل من التحميل على البنية الأساسية ل VPN الخاصة بالشركة ويحسن أداء الخدمات المعرفة. وبما أنه من المرجح أن يستغرق هذا النموذج مزيدا من الوقت لتقييم إمكانية تنفيذ هذا النموذج، فمن المرجح أن يتم تنفيذ هذه الخطوة بشكل متكاتف في وقت لاحق بمجرد نجاح النموذج الثاني.

![نموذج VPN المنقسم للانقسام للانقسام.](../media/vpn-split-tunneling/vpn-model-3.png)

## <a name="4-vpn-selective-tunnel"></a>4. VPN Selective

يعكس النموذج الثالث في أنه يتم إرسال حركة المرور المحددة فقط على أنها عنوان IP الشركة أسفل مسار VPN وبالتالي فإن مسار الإنترنت هو المسار الافتراضي لكل شيء آخر. يتطلب هذا النموذج أن تكون المؤسسة على المسار الصحيح نحو [الثقة الصفرية](https://www.microsoft.com/security/zero-trust?rtc=1) لكي تتمكن من تنفيذ هذا النموذج بأمان. من المفترض أن يصبح هذا النموذج أو بعض التباينات فيه هو الافتراضي الضروري مع مرور الوقت مع انتقال المزيد من الخدمات بعيدا عن شبكة الشركة وننتقل إلى السحابة.

تستخدم Microsoft هذا النموذج داخليا. يمكنك العثور على مزيد من المعلومات حول تنفيذ Microsoft لتقسيم VPN في [تشغيل على VPN: كيف تحافظ Microsoft على اتصال القوى العاملة البعيدة بها](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![نموذج VPN المنقسم للانقسام VPN 4.](../media/vpn-split-tunneling/vpn-model-4.png)

## <a name="5-no-vpn"></a>5. لا توجد VPN

إصدار أكثر تقدما من رقم النموذج 2، حيث يتم نشر أي خدمات داخلية من خلال نهج أمان حديث أو حل SDWAN مثل وكيل Azure AD و Defender for Cloud Apps و Zscaler ZPA وغير ذلك.

![نموذج VPN المنقسم للانقسام VPN 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="related-articles"></a>المقالات ذات الصلة

[نظرة عامة: تقسيم VPN إلى تقسيم Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[تنفيذ تقسيم VPN لتنفيذ Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[تأمين Teams الوسائط من أجل تقسيم VPN](microsoft-365-vpn-securing-teams.md)

[اعتبارات خاصة للبث والأحداث المباشرة في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 تحسين أداء المستخدمين في الصين](microsoft-365-networking-china.md)

[Microsoft 365 "مبادئ اتصال الشبكة"](microsoft-365-network-connectivity-principles.md)

[تقييم Microsoft 365 الشبكة](assessing-network-connectivity.md)

[Microsoft 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

[طرق بديلة لمحترفي الأمان تكنولوجيا المعلومات لتحقيق عناصر التحكم الحديثة في الأمان في سيناريوهات العمل عن بعد الفريدة اليوم (مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[تحسين أداء VPN في Microsoft: Windows 10 ملفات تعريف VPN للسماح باتصالات التشغيل التلقائي](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[تشغيل VPN: كيف تحافظ Microsoft على اتصال القوى العاملة البعيدة](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[شبكة Microsoft العامة](/azure/networking/microsoft-global-network)
