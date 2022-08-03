---
title: 'البرنامج التعليمي: جمع التحليل الذكي للمخاطر وتسلسل البنية الأساسية باستخدام تحليل ذكي للمخاطر في Microsoft Defender (Defender TI)'
description: في هذا البرنامج التعليمي، تعرف على كيفية جمع التحليل الذكي للمخاطر وسلسلة البنية الأساسية معا مؤشرات التسوية في تحليل ذكي للمخاطر في Microsoft Defender (Defender TI). ستغطي هذه المقالة تحقيق تاريخي في خرق MyPillow Magecart.
author: alexroland24
ms.author: aroland
ms.service: threat-intelligence
ms.topic: tutorial
ms.date: 08/02/2022
ms.custom: template-tutorial
ms.openlocfilehash: 7cdb70d72253164b24cb55d57b20cc3edb7c5a7c
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67171496"
---
# <a name="tutorial-gathering-threat-intelligence-and-infrastructure-chaining"></a>البرنامج التعليمي: جمع التحليل الذكي للمخاطر وتسلسل البنية الأساسية

في هذا البرنامج التعليمي، ستتعلم كيفية:
- إجراء أنواع متعددة من عمليات البحث عن المؤشرات وجمع التحليل الذكي للمخاطر والخصوم

  ![ti OverviewHome Page Chrome لقطة شاشة](media/tiOverviewHomePageChromeScreenshot.png)

## <a name="prerequisites"></a>المتطلبات الأساسية

- Azure Active Directory أو حساب Microsoft شخصي. [تسجيل الدخول أو إنشاء حساب](https://signup.microsoft.com/)
- ترخيص تحليل ذكي للمخاطر في Microsoft Defender (Defender TI) Premium.

    > [!NOTE]
    > سيظل المستخدمون الذين ليس لديهم ترخيص Defender TI Premium قادرين على تسجيل الدخول إلى بوابة Defender Threat Intelligence والوصول إلى عرض Defender TI المجاني.

## <a name="disclaimer"></a>اخلاء المسؤوليه

قد تتضمن تحليل ذكي للمخاطر في Microsoft Defender (Defender TI) ملاحظات مباشرة ومؤشرات تهديد في الوقت الحقيقي، بما في ذلك البنية الأساسية الضارة والأدوات ضد التهديدات. أي عمليات بحث في IP والمجال داخل نظام Defender TI الأساسي آمنة للبحث.

ستقوم Microsoft بمشاركة الموارد عبر الإنترنت (على سبيل المثال، عناوين IP وأسماء المجالات) التي يجب اعتبارها تهديدات حقيقية تشكل خطرا واضحا وحاضر.

نطلب من المستخدمين استخدام أفضل حكم عليهم وتقليل المخاطر غير الضرورية أثناء التفاعل مع الأنظمة الضارة عند تنفيذ البرنامج التعليمي أدناه. يرجى ملاحظة أن Microsoft عملت على تقليل المخاطر عن طريق تعريف عناوين IP الضارة والمضيفين والمجالات.

## <a name="before-you-begin"></a>قبل البدء
كما هو الحال في إخلاء المسؤولية أعلاه، تم تعريف المؤشرات المشبوهة والضارة من أجل سلامتك. الرجاء إزالة أي أقواس من عناوين IP والمجالات والمضيفين عند البحث في Defender TI. لا تبحث في هذه المؤشرات مباشرة في المستعرض.

## <a name="perform-several-types-of-indicator-searches-and-gather-threat-and-adversary-intelligence"></a>إجراء أنواع متعددة من عمليات البحث عن المؤشرات وجمع التحليل الذكي للمخاطر والخصوم

في هذا البرنامج التعليمي، ستقوم بتنفيذ سلسلة من الخطوات [لسلسلة البنية التحتية](infrastructure-chaining.md) معا مؤشرات التسوية (IOCs) المتعلقة بخرق Magecart وجمع التهديد والذكاء الخصم على طول الطريق. يستفيد تسلسل البنية الأساسية من الطبيعة المتصلة للغاية للإنترنت لتوسيع IOC واحد إلى العديد بناء على التفاصيل المتداخلة أو الخصائص المشتركة. يتيح بناء سلاسل البنية الأساسية لمتتبعي التهديدات أو المستجيبين للحوادث تحديد حالة الحضور الرقمي للخصم، ما يتيح لهم التركيز بسرعة عبر مجموعات البيانات هذه لإنشاء سياق حول حادث أو تحقيق، ما يسمح بفرز أكثر فعالية للتنبيه إلى الحوادث داخل المؤسسة وتنفيذها.

![تسلسل البنية الأساسية](media/infrastructureChaining.png)

**الأشخاص المعنيون:** محلل التحليل الذكي للمخاطر، ومتتبع التهديدات، ومستجيب الحوادث، ومحلل عمليات الأمان

### <a name="magecart-breach"></a>خرق Magecart

تعمل Microsoft على جمع المعلومات وتتابع أنشطة Magecart، وهي مجموعة من المجموعات الإلكترونية الجنائية خلف مئات الخروقات لمنصات البيع بالتجزئة عبر الإنترنت من خلال وضع المتزلجين الرقميين على مواقع التجارة الإلكترونية المخترقة.

يقومون بذلك عن طريق إدخال برنامج نصي مصمم لسرقة البيانات الحساسة التي يدخلها المستهلكون في نماذج الدفع عبر الإنترنت على مواقع التجارة الإلكترونية مباشرة أو من خلال موردين خارجيين معرضين للخطر قد تعتمد عليهم مواقع الويب لجعل مواقعهم تعمل.

مرة أخرى في أكتوبر 2018، تسللوا إلى موقع MyPillow على الإنترنت، mypillow.com، لسرقة معلومات الدفع عن طريق إدخال برنامج نصي في متجر الويب الخاص بهم الذي تمت استضافته على مجال قرطاسية مطبعي يحتوي على المتزلج، mypiltow.com.

كان خرق MyPillow عبارة عن هجوم على مرحلتين، حيث كان أول متزلج نشطا لفترة قصيرة فقط قبل أن يتم التعرف عليه على أنه غير مشروع وإزالته، ولكن المهاجمين لا يزال لديهم حق الوصول إلى شبكة MyPillow وفي 26 أكتوبر 2018، لاحظت Microsoft أنهم سجلوا مجالا جديدا، livechatinc[.] مؤسسة

عادة ما تقوم جهات Magecart بتسجيل انتهاك المجال لجعله يبدو مشابها قدر الإمكان للمجال المشروع، بحيث إذا كنت تبحث في التعليمات البرمجية ل JavaScript، إلا إذا نظرت بعناية حقا، فقد لا تلاحظ أنهم أدخلوا برنامجهم النصي الخاص الذي يلتقط معلومات دفع بطاقة الائتمان ويدفعها إلى بنيتها الأساسية الخاصة،  كطريقة لإخفاء بشكل أساسي.
ولكن نظرا لأن مستخدمينا الظاهريين يلتقطون DOM ويعثرون على جميع الارتباطات الديناميكية والتغييرات التي أجراها JavaScript من عمليات التسجيل في الفهرس على الخلفية، تمكنا من اكتشاف هذا النشاط وتحديد هذا المجال المزيف الذي كان يستضيف البرنامج النصي الذي تم إدخاله في مخزن ويب MyPillow.

1. الوصول إلى [مدخل Defender Threat Intelligence](https://ti.defender.microsoft.com/).
2. أكمل مصادقة Microsoft للوصول إلى المدخل.
3. ابحث عن "mypillow.com" في الصفحة الرئيسية لتحليل ذكي للمخاطر ل Defender TI.
    أ. ما هي المقالات المقترنة بهذا المجال؟
    - قد يفقد المستهلكون النوم بسبب خرقي Magecart هذين

      ![مقالة Infra Chain My Deviationcom الخاصة بالبرنامج التعليمي](media/tutorialInfraChainMyPillowcomArticle.png)

4. حدد مقالة "قد يفقد المستهلكون النوم بسبب خرقي Magecart" هذين.
    أ. ما هي المعلومات المتوفرة حول هذه الحملة ذات الصلة؟
      - تم نشر هذه المقالة في 20 مارس 2019، وتوفر رؤى حول كيفية اختراق MyPillow من قبل مجموعة ممثل التهديد Magecart في أكتوبر 2018. توضح المقالة كيفية تنفيذ الهجوم.
5. حدد علامة التبويب "المؤشرات العامة". أ. ما هي IOCs المدرجة المتعلقة بهذه الحملة؟
      - ameridrive.github[.] io
      - cmytuok[.] أعلى
      - livechatinc[.] مؤسسة
      - mypiltow[.] com
6. حدد الكل في القائمة المنسدلة لشريط البحث والاستعلام 'mypillow.com'. ثم انتقل إلى علامة التبويب "بيانات". أ. ما هي مجموعة البيانات التي قد تكون مفيدة في العثور على دليل على إدخال البرنامج النصي؟
     - تكشف أزواج المضيفين عن الاتصالات بين مواقع الويب التي لن تظهر مصادر البيانات التقليدية (pDNS و Whois) وتمكنك من معرفة مكان استخدام مواردك والعكس بالعكس.
7. حدد جزء "Host Pairs Data"، وفرز حسب "First Seen"، وعامل التصفية حسب script.src كسبب. مرر الصفحة حتى تعثر على علاقات زوج المضيف التي وقعت في أكتوبر 2018.
    أ. هل تلاحظ أي مجالات mypillow ل typosquat؟
      - لاحظ أن mypillow[.] يقوم com بسحب المحتوى عبر برنامج نصي من mypiltow.com (3-5 أكتوبر) كدليل على خرق حقن البرنامج النصي

          ![البرنامج التعليمي Infra Chain My Botcom Host Pairs Live Chat Script Src](media/tutorialInfraChainMyPillowcomHostPairsLiveChatScriptSrc.gif)
8. Pivot on 'mypiltow[.] com'.
    أ. للوهلة الأولى، ما الذي يظهر مختلفا حول هذا المجال مقارنة بمجال mypillow.com؟
      - السمعة: ضارة، في حين أن سمعة mypillow.com غير معروفة

        ![البرنامج التعليمي InfraChain My Piltowcom Reputation](media/tutorialInfraChainMyPiltowcomReputation.png)

        ![البرنامج التعليمي Infra Chain My Reputation](media/tutorialInfraChainMyPillowcomReputation.png)
9. انتقل إلى علامة التبويب "بيانات" ومن نتائج "التحليلات"، قم بتمحور حول عنوان IP الذي mypiltow[.] تم حل com خلال أكتوبر 2018. كرر هذه الخطوة mypillow.com أيضا.
    أ. ما الذي تلاحظه حول الاختلافات في عناوين IP بين mypillow.com وmypiltow[.] خلال أكتوبر 2018؟
      - عنوان IP، 195.161.41[.] 65, mypiltow[.] com قد تم حله، تتم استضافته في روسيا.
      - ASN مختلفة مستخدمة.

          ![البرنامج التعليمي Infra Chain My Piltow Ip Summary](media/tutorialInfraChainMyPiltowIpSummary.png)

          ![ملخص Ip الخاص بي في السلسلة الأساسية لبرنامج تعليمي](media/tutorialInfraChainMyPillowIpSummary.png)
10. قم بالتمرير إلى قسم "المقالات".
    أ. ما هي المقالات الأخرى التي تم نشرها والتي تتعلق mypiltow.com؟
    - RiskIQ: Magecart Injected URLs and C2 Domains, June 3-14, 2022
    - RiskIQ: قام Magecart بإدخال عناوين URL ومجالات C2، من 20 إلى 27 مايو 2022
    - تزلج على السلع & اتجاهات Magecart في الربع الأول من عام 2022
    - RiskIQ: نشاط مجموعة Magecart 8 في بداية عام 2022
    - مجموعة Magecart 8 العقارات: أنماط الاستضافة المقترنة بمجموعة التزلج
    - حزمة التزحلق المتداخل المستخدمة في هجمات المتجانس
    - مجموعة Magecart 8 تمزج في NutriBullet.com إضافة إلى قائمة ضحاهم المتزايدة

     ![مقالات Piltowcom الخاصة بي في البرنامج التعليمي Infra Chain](media/tutorialInfraChainMyPiltowcomArticles.gif)
11. راجع كل مقالة من المقالات الإضافية من الخطوة 9.
    أ. ما هي المعلومات الإضافية التي يمكنك العثور عليها حول مجموعة ممثل التهديد Magecart؟ (الأهداف، وTTPs، وIOCs إضافية، وما إلى ذلك)
12. انتقل إلى علامة التبويب "بيانات" وحدد شفرة "بيانات Whois" وقارن معلومات Whois بين "mypillow.com" و"mypiltow[.] com' a. ما هي قيم Whois التي تختلف؟
      - mypillow.com
        1. إذا حددت سجل Whois من أكتوبر 2011، فستجد أن المجال مملوك بوضوح لشركة My Framework Inc.

            ![البرنامج التعليمي Infra Chain My Piltowcom 2 Whois](media/tutorialInfraChainMyPiltowcom2Whois.png)
        2. mypiltow[.] com
        3. إذا قمت بتحديد سجل Whois من أكتوبر 2018، فستجد mypiltow[.] تم تسجيل com في هونغ كونغ، الصين وهو محمي بالخصوصية بواسطة Domain ID Shield Service CO.
        4. mypiltow[.] جهة تسجيل com هي OnlineNIC, Inc.

            ![البرنامج التعليمي Infra Chain My Piltowcom 2 Whois](media/tutorialInfraChainMyPiltowcom2Whois.png)

    ب. ما يبدو مريبا حتى الآن حول mypiltow[.] com بالنظر إلى سجلات A وتفاصيل Whois التي قمنا بتحليلها؟
      - عند تقييم ما إذا كانت mypiltow[.] قد يكون com البنية الأساسية لشركة شرعية، يجب أن يجد المحلل أنه من الفردي أن يتم حماية IP الروسية في المقام الأول من قبل خدمة الخصوصية الصينية لشركة مقرها الولايات المتحدة.
13. البحث في 'livechatinc[.] المؤسسة ' في الصفحة الرئيسية لذكاء التهديد ل Defender TI.
    أ. ما هي المقالات الجديدة المقترنة بهذا المجال التي لم نرها عند البحث في mypillow.com في الجزء 1؟
      - مجموعة Magecart 8 تمزج في NutriBullet.com إضافة إلى قائمة ضحاهم المتزايدة
14. حدد مجموعة Magecart 8 Blends في NutriBullet.com إضافة إلى القائمة المتزايدة الخاصة بهم من مقالة ضحى.
    أ. ما هي المعلومات المتوفرة حول هذه الحملة ذات الصلة؟
      - تم نشر مقالة "Magecart Group 8 Blends into NutriBullet.com Adding to their Growing List of Victims" في 18 مارس 2020. في هذه المقالة، نكتشف أن Nutribullet وAmeridrive و ABS-CBN كانوا أيضا من ضحية مجموعة ممثل التهديد Magecart.
15. حدد علامة التبويب "المؤشرات العامة". أ. ما هي IOCs المدرجة المتعلقة بهذه الحملة؟
      - عناوين URL
        1. hxxps://coffemokko[.] com/tr/, hxxps://freshdepor[.] com/tr/, hxxps://prodealscenter[.] com/tr/, hxxps://scriptoscript[.] com/tr/, hxxps://swappastore[.] com/tr/
        2. المجالات
            - 3 رفع[.] org, abtasty[.] net, adaptivecss[.] org, adorebeauty[.] org, all-about-sneakers[.] org, ameridrive.github[.] io, ar500arnor[.] com, authorizecdn[.] com, bannerbuzz[.] معلومات، قوة البطارية[.] org, batterynart[.] com، blackriverimaging[.] org, braincdn[.] org, btosports[.] net, cdnassels[.] com, cdnmage[.] com, vasaddlery[.] net, childsplayclothing[.] org, christohperward[.] org, citywlnery[.] org, arraylondon[.] org, cmytuok[.] أعلى، coffemokko[.] com, coffetea[.] org, configsysrc[.] info, tahlie[.] org, davidsfootoma[.] org, dobell[.] su, elegrina[.] com, energycoffe[.] org, energytea[.] org, eitesupply[.] org, exrpesso[.] org, foodandcot[.] com, freshchat[.] معلومات، freshdepor[.] com, greatfurnituretradingco[.] org, info-js[.] link, tahondirect[.] com, js-cloud[.] com, kandypens[.] net, kikvape[.] org, labbe[.] biz, lamoodbighats[.] net, link js[.] link, livechatinc[.] org, londontea[.] net, mage-checkout[.] org, magejavascripts[.] com, magescripts[.] pw, magesecuritys[.] com, ماوسوربلوس[.] com, map-js[.] link, mcloudjs[.] com, mechat[.] info, melbounestorm[.] com, misshaus[.] org, mylrendyphone[.] com, mypiltow[.] com, nililotan[.] org, potandfort[.] org, ottocap[.] مؤسسة، حديقة[.] su, paypaypay[.] org, pmtonline[.] su, prodealscenter[.] com, replacemyremote[.] org, sagecdn[.] org, scriptoscript[.] com, security-payment[.] su, shop-rnib[.] org, slickjs[.] org, slickmin[.] com, smart-js[.] link, swappastore[.] com, teacoffe[.] net, top5value[.] com, track-js[.] link, ukcoffe[.] com, verywellfitnesse[.] com, walletgear[.] org, webanalyzer[.] net, zapaljs[.] com, zoplm[.] com

16. ابحث عن mypillow.com في الصفحة الرئيسية ل "التحليل الذكي للمخاطر" ل Defender TI وحدد علامة التبويب "بيانات". حدد جزء "Host Pairs Data". قم بالفرز حسب أول ظهور وتحديد موقع علاقات "زوج المضيف" التي حدثت في أكتوبر 2018.

    أ. هل تلاحظ علاقة برنامج نصي مشابهة بين mypillow.com و secure.livechatinc[.] مؤسسة تعكس نفس العلاقة التي كانت mypillow.com مع mypiltow[.] com؟
      - لاحظ كيف تمت ملاحظة www.mypillow.com لأول مرة وهي تتواصل مع secure.livechatinc[.] مؤسسة في 10/26/2018، لأنه تمت ملاحظة طلب GET للبرنامج النصي من www.mypillow.com إلى secure.livechatinc[.] المؤسسة. استغرقت هذه العلاقة حتى 19/11/2018.

           ![البرنامج التعليمي Infra Chain My Wavecom Host Pairs Live Chat ScriptSrc](media/tutorialInfraChainMyPillowcomHostPairsLiveChatScriptSrc.gif) ii. بالإضافة إلى ذلك، secure.livechatinc[.] تواصلت المؤسسة مع www.mypillow.com للوصول إلى خادم www.mypillow.com (xmlhttprequest).
17. راجع علاقات mypillow.com"Host Pair" بشكل أكبر.
    أ. هل mypillow.com أي علاقات زوج مضيف باسم مجال مشابه ل secure.livechatinc[.] مؤسسة؟
      - نعم. هناك أنواع متعددة من العلاقات التي تمت ملاحظتها mypillow.com لدى المضيفين بالمجالات التالية:
        1. cdn.livechatinc[.] com, secure.livechatinc[.] com, api.livechatinc[.] com
     - تتضمن أسباب العلاقة ما يلي:
        1. script.src
        2. iframe.src
        3. مجهول
        4. topLevelRedirect
        5. img.src
        6. xmlhttprequest
      - Livechat هي خدمة دردشة دعم مباشر يمكن لمتاجر التجزئة عبر الإنترنت إضافتها إلى مواقع الويب الخاصة بهم، لذلك فهي مورد تابع لجهة خارجية وتستخدمها العديد من الأنظمة الأساسية للتجارة الإلكترونية، بما في ذلك MyPillow. هذا المجال المزيف أكثر إثارة للاهتمام قليلا لأن موقعهم الرسمي livechatinc.com بالفعل. لذلك، في هذه الحالة، استخدموا طباعة مجال من المستوى الأعلى لإخفاء حقيقة أنهم وضعوا أداة تزلج ثانية على موقع MyPillow على الويب.
18. ارجع وابحث عن علاقة زوج مضيف مع 'secure.livechatinc[.] المؤسسة وpivot خارج اسم المضيف هذا.
    أ. ما هو عنوان IP الذي قام هذا المضيف بحله خلال أكتوبر من عام 2018؟
      - 212.109.222[.] 230

        ![البرامج التعليمية Infra Chain Secure Live Chat Inc Org Resolutions](media/tutorialInfraChainSecureLiveChatIncOrgResolutions.png)
      - لاحظ كيف تتم استضافة عنوان IP هذا أيضا في روسيا ومنظمة ASN هي JSC IOT.

        ![ملخص Ip لبرنامج Infra Chain Secure Live Chat Inc Org](media/tutorialInfraChainSecureLiveChatIncOrgIpSummary.png)
19. البحث 'secure.livechatinc[.] المؤسسة' في الصفحة الرئيسية ل "التحليل الذكي للمخاطر" ل Defender TI، حدد علامة التبويب "بيانات"، وانقر فوق جزء Whois. حدد السجل من 12/25/2018.
    أ. ما هي جهة التسجيل التي تم استخدامها لهذا السجل؟
      - OnlineNIC Inc.
            1. هذه هي جهة التسجيل نفسها التي تم استخدامها لتسجيل mypiltow[.] com في أثناء الحملة نفسها.
                2. إذا قمت بتحديد السجل من 12/25/2018، فستلاحظ أن المجال كان يستخدم أيضا نفس خدمة حماية الخصوصية الصينية، خدمة حماية معرف المجال، التي mypiltow[.] كما استخدم com.
    ب. ما خوادم الأسماء التي تم استخدامها لهذا السجل؟
      - ns1.jino.ru
      - ns2.jino.ru
      - ns3.jino.ru
      - ns4.jino.ru
        1. كانت هذه هي نفس خوادم الأسماء المستخدمة في سجل 10/01/2018 ل mypiltow[.] com. غالبا ما يستخدم الخصوم نفس خوادم الأسماء لتقسيم بنيتهم الأساسية.

            ![البرنامج التعليمي Infra Chain Secure Live Chat Inc Org Whois](media/tutorialInfraChainSecureLiveChatIncOrgWhois.png)

            ![البرنامج التعليمي Infra Chain My Piltowcom 2 Whois](media/tutorialInfraChainMyPiltowcom2Whois.png)
20. حدد جزء "Host Pairs Data".
    أ. ما هي علاقات زوج المضيف التي تراها في أكتوبر وتشرين الثاني من عام 2018؟
      - secure.livechatinc[.] قامت المؤسسة بإعادة توجيه المستخدمين إلى secure.livechatinc.com في 11/19/2022. هذا أكثر من المحتمل أن يكون تقنية تعتيم للكشف عن التقصي.
      - www.mypillow.com سحب برنامج نصي مستضاف على secure.livechatinc[.] مؤسسة (موقع LiveChat المزيف) من 10/26/2018 حتى 11/19/2022. خلال هذا الإطار الزمني، من المحتمل أن تكون مشتريات المستخدم من www.mypillow.com معرضة للخطر.
      - secure.livechatinc[.] كانت المؤسسة تطلب بيانات من الخادم، www.mypillow.com، واستضافة موقع MyPillow الحقيقي (xmlhttprequest) بين 10/27/2018 حتى 29/10/2018.

          ![البرنامج التعليمي Infra Chain Secure Live Chat Inc Org Host Pairs](media/tutorialInfraChainSecureLiveChatIncOrgHostPairs.png) b. ماذا تعتقد أن هذه العلاقات تعني؟

## <a name="clean-up-resources"></a>تنظيف الموارد
لا توجد موارد للتنظيف في هذا المقطع.

## <a name="next-steps"></a>الخطوات التالية
في هذا البرنامج التعليمي، تعلمت كيفية جمع التحليل الذكي للمخاطر وسلسلة البنية الأساسية معا مؤشرات التسوية.