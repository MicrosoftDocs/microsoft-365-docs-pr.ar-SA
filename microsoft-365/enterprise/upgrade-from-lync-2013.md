---
title: الترقية من Lync Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: ابحث عن المعلومات والموارد للترقية من Lync Server 2013. ينتهي الدعم في 11 أبريل 2023.
ms.openlocfilehash: 6d6d3baed383e85a1e97d37726ff7f1eb355e98c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63579984"
---
# <a name="upgrading-from-lync-server-2013"></a>الترقية من Lync Server 2013

سيصل Microsoft Lync Server 2013 إلى نهاية الدعم في **11 أبريل 2023**. توفر هذه المقالة موارد لمساعدتك على ترقية نشر Lync Server الحالي Microsoft Teams أو Skype for Business المحلية.

## <a name="what-is-end-of-support"></a>ما هو *انتهاء الدعم*؟

تحتوي معظم منتجات Microsoft على دورة حياة الدعم، حيث تحصل خلالها على ميزات جديدة وت تصحيحات الأخطاء وإصلاحات الأمان وما إلى ذلك. بعد انتهاء تاريخ الدعم، لا يتوقف المنتج عن العمل، ولكن لم تعد Microsoft توفر:

- الدعم التقني للمشاكل التي قد تحدث.

- إصلاحات الأخطاء ل المشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.

- إصلاحات الأمان لنقاط الضعف التي قد تجعل الخادم عرضة للثغرات الأمنية.

- تحديثات المنطقة الزمنية.

وهذا يعني أنه لن يتم إجراء أي تحديثات أو تصحيحات أو إصلاحات للمنتج (بما في ذلك تصحيحات/إصلاحات الأمان). سيبدل دعم Microsoft جهود الدعم بشكل كامل إلى الإصدارات الأحدث.

## <a name="plan-ahead"></a>التخطيط للمستقبل

تحقق من التواريخ التي ينتهي دعمها على موقع [دورة حياة المنتج](/lifecycle/products/lync-server-2013). خطط للترقية أو الترحيل مع وضع هذه التواريخ في الاعتبار. تذكر أن *منتجك لن يتوقف عن العمل* في التاريخ المدرج. ولكن بما أنه لن يتم تصحيح التثبيت بعد ذلك التاريخ، فسوف تحتاج إلى التخطيط لانتقال سلس إلى الإصدار التالي من المنتج. يسرد الجدول أدناه الخيارات المتوفرة لك.

|منتج انتهاء الدعم|معتمد|مستحسن|
|---|---|---|
|Lync Server 2013|الترقية إلى Skype for Business Server 2015 أو 2019|الترقية إلى Microsoft Teams

## <a name="whats-next"></a>ماذا بعد ذلك؟

نوصي بالترقية إلى Microsoft Teams. Microsoft Teams توسيع إمكانات Lync Server، مع جمع الدردشة والاجتماعات والمحادثات والتعاون وتكامل التطبيقات وتخزين الملفات في واجهة واحدة. Teams على تبسيط طريقة إنجاز المستخدمين للأمور، وتحسين مستوى رضا المستخدمين وتسريع نتائج الأعمال. نحن نعمل باستمرار على توسيع Teams لتمكينك من التواصل والتعاون بطرق جديدة، وكسر الحواجز التنظيمية والجغرافية، وزيادة الكفاءة في العملية واتخاذ القرار.

إذا لم تتمكن من الترقية إلى Microsoft Teams، يمكنك الترقية إلى Skype for Business Server 2015 أو 2019. من الاعتبارات الأساسية للتخطيط التي يجب معرفتها أن كلا هذين المنتجات سيبلغان نهاية الدعم في 14 أكتوبر 2025. لمزيد من المعلومات، راجع صفحات دورة حياة الدعم التالية:

- [Skype for Business Server دورة حياة الدعم في 2015](/lifecycle/products/skype-for-business-server-2015)
- [Skype for Business Server دورة حياة الدعم في 2019](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>الترقية إلى Microsoft Teams

لدينا إرشادات مفصلة حول الترقية Microsoft Teams من النشر في الموقع. أولا، دعنا نغطي بعض المتطلبات التقنية الأساسية. ستحتاج إلى إنشاء اتصال مختلط، مما يمكنك من نقل المستخدمين إلى Teams. [توفر خطة الاتصال المختلط](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) نظرة عامة حول إعداد بيئة مختلطة. على الرغم من تركيز المقالة على Skype for Business، فإن كل المفاهيم تنطبق على Lync Server 2013 أيضا. راجع القسم [متطلبات إصدار الخادم](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) للحصول على تفاصيل خاصة ب Lync Server 2013.

تحتاج أيضا إلى التأكد من أن نشر Lync Server 2013 مكتمل. ننشر قائمة بكل التحديثات الأخيرة ل [Lync Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164) ومع ذلك، فإن التحديث التالي هو أحد المتطلبات الأساسية للترقية إلى Microsoft Teams:

- التحديث التراكمي [ل سبتمبر 2021 5.0.8308.1149 ل Lync Server 2013،](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043) المكونات الأساسية: يستبدل هذا التحديث مصادقة الم ID Live ببروتوكول مصادقة OAuth `Move-CSUser` ل cmdlet، الذي يتم استخدامه لتحريك المستخدمين Microsoft Teams.

على الرغم من أن تجربة المستخدم في Microsoft Teams غنية ومتفوقة عن Lync، إلا أنها تختلف أيضا بشكل كبير. وبالتالي، ستحتاج أيضا إلى إعداد مؤسستك والمستخدمين لضمان الاعتماد السريع Microsoft Teams. تتوفر لدينا الكثير من المعلومات حول كيفية إعداد مؤسستك، وخطط الترقية إلى Teams، وضمان نجاح عملية طرحها.

**نوصيك بالبدء [](/MicrosoftTeams/upgrade-skype-teams)** في مدخل الترقية Teams حيث يمكنك العثور على المعلومات التقنية، وموارد التدريب، والربط إلى ابدء جلسات العمل، وموارد التعليمات المتوفرة، دراسات الحالة والمزيد.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="لقطة شاشة لمدخل Teams الترقية":::

### <a name="upgrade-to-skype-for-business-server"></a>الترقية إلى Skype for Business Server

سيختلف مسار Skype for Business Server وفقا للإصدار الذي تختار الترقية له. Skype for Business Server 2015 ترقية مكانية من Lync Server 2013. من ناحية أخرى، لكي تتمكن من الترقية إلى Skype for Business Server 2019، ستحتاج أولا إلى تقديم Skype for Business Server 2019 إلى تثبيت Lync Server 2013 عبر إضافة خادم جديد واحد أو أكثر، ثم نقل العمليات إلى خوادم 2019 الجديدة التي أضفتها.

هناك نقطة هامة يجب التفكير فيها وهي أن مرحلة الدعم الحالية لكل منتج: Skype for Business 2019 هو في الدعم العادي وأن Skype for Business 2015 حاليا في دعم موسع.  لذلك، نوصي بالترقية إلى Skype for Business Server 2019. لمعرفة المزيد حول الفرق بين الدعم الأساسي والموسع، راجع [نهج دورة الحياة الثابتة](/lifecycle/policies/fixed).

راجع الموارد التالية للحصول على معلومات مفصلة حول كل سيناريو ترقية.

- [الترقية إلى Skype for Business Server 2019](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [الترقية إلى Skype for Business Server 2015](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
