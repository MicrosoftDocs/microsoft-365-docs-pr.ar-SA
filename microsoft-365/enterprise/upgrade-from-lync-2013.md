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
ms.openlocfilehash: 925b53d751cd559ce3ccdf28d823531021611551
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129130"
---
# <a name="upgrading-from-lync-server-2013"></a>الترقية من Lync Server 2013

سيصل Microsoft Lync Server 2013 إلى نهاية الدعم في **11 أبريل 2023**. توفر هذه المقالة موارد لمساعدتك على ترقية نشر Lync Server الحالي إلى Microsoft Teams أو Skype for Business محليا.

## <a name="what-is-end-of-support"></a>ما هي *نهاية الدعم*؟

تحتوي معظم منتجات Microsoft على دورة حياة دعم، تحصل خلالها على ميزات جديدة وتصحيحات الأخطاء وتصحيحات الأمان وما إلى ذلك. بعد تاريخ انتهاء الدعم، لا يتوقف المنتج عن العمل، ولكن لم تعد Microsoft توفر:

- الدعم التقني للمشاكل التي قد تحدث.

- إصلاحات الأخطاء للمشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.

- إصلاحات الأمان للثغرات الأمنية التي قد تجعل الخادم عرضة للخروقات الأمنية.

- تحديثات المنطقة الزمنية.

وهذا يعني أنه لن تكون هناك تحديثات أو تصحيحات أو إصلاحات أخرى للمنتج (بما في ذلك تصحيحات/إصلاحات الأمان). سيحول دعم Microsoft جهود الدعم بالكامل إلى الإصدارات الأحدث.

## <a name="plan-ahead"></a>التخطيط مسبقا

تحقق من التواريخ التي تدعم انتهاء في [موقع دورة حياة المنتج](/lifecycle/products/microsoft-lync-server-2013). خطط لترقياتك أو عمليات الترحيل مع وضع هذه التواريخ في الاعتبار. تذكر أن منتجك *لن يتوقف عن العمل* في التاريخ المدرج. ولكن نظرا إلى أنه لن يتم تصحيح التثبيت بعد ذلك التاريخ، فسترغب في التخطيط لانتقال سلس إلى الإصدار التالي من المنتج. يسرد الجدول أدناه الخيارات المتوفرة لك.

|منتج نهاية الدعم|دعم|اوصت|
|---|---|---|
|Lync Server 2013|الترقية إلى Skype for Business Server 2015 أو 2019|الترقية إلى Microsoft Teams

## <a name="whats-next"></a>ماذا بعد ذلك؟

نوصي بالترقية إلى Microsoft Teams. Microsoft Teams توسيع قدرات Lync Server، وجمع الدردشة والاجتماعات والمكالمات والتعاون وتكامل التطبيقات وتخزين الملفات في واجهة واحدة. يساعد Teams على تبسيط طريقة إنجاز المستخدمين للأشياء، وتحسين رضا المستخدم وتسريع نتائج الأعمال. نعمل باستمرار على توسيع قدرات Teams لتمكينك من التواصل والتعاون بطرق جديدة، وتقسيم الحواجز التنظيمية والجغرافية، ودفع الكفاءة في العملية واتخاذ القرار.

إذا تعذر عليك الترقية إلى Microsoft Teams، فيمكنك الترقية إلى Skype for Business Server 2015 أو 2019. أحد الاعتبارات الرئيسية للتخطيط الذي يجب معرفته هو أن كلا المنتجين سيصلان إلى نهاية الدعم في 14 أكتوبر 2025. لمزيد من المعلومات، راجع صفحات دورة حياة الدعم التالية:

- [معلومات دورة حياة دعم Skype for Business Server 2015](/lifecycle/products/skype-for-business-server-2015)
- [معلومات دورة حياة دعم Skype for Business Server 2019](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>الترقية إلى Microsoft Teams

لدينا إرشادات مفصلة حول الترقية إلى Microsoft Teams من النشر المحلي. أولا، دعونا نغطي بعض المتطلبات التقنية الرئيسية. ستحتاج إلى إنشاء اتصال مختلط، والذي سيمكنك من نقل المستخدمين إلى Teams. [توفر خطة الاتصال المختلط](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) نظرة عامة على إعداد بيئة مختلطة. على الرغم من أن المقالة تركز على Skype for Business، فإن كل المفاهيم تنطبق أيضا على Lync Server 2013. راجع قسم [متطلبات إصدار الخادم](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) للحصول على التفاصيل الخاصة ب Lync Server 2013.

تحتاج أيضا إلى التأكد من أن نشر Lync Server 2013 محدث بالكامل. ننشر [قائمة بجميع التحديثات الأخيرة ل Lync Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164)، ومع ذلك، يعد التحديث التالي شرطا مسبقا للترقية إلى Microsoft Teams:

- [التحديث التراكمي لشهر سبتمبر 2021 5.0.8308.1149 ل Lync Server 2013، Core Components](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043): يستبدل هذا التحديث مصادقة Live ID ببروتوكول مصادقة OAuth ل `Move-CSUser` cmdlet، والذي يستخدم لنقل المستخدمين المحليين إلى Microsoft Teams.

على الرغم من أن تجربة المستخدم في Microsoft Teams أكثر ثراء وتفوقا على Lync، إلا أنها تختلف أيضا بشكل كبير. لذلك، ستحتاج أيضا إلى إعداد مؤسستك والمستخدمين لضمان الاعتماد السريع Microsoft Teams. لدينا الكثير من المعلومات المتاحة حول كيفية إعداد مؤسستك، والتخطيط للترقية إلى Teams، وضمان الإطلاق الناجح.

**نوصي بالبدء في [مدخل الترقية Teams](/MicrosoftTeams/upgrade-skype-teams)** حيث يمكنك العثور على المعلومات التقنية وموارد التدريب والارتباطات إلى جلسات Ignite وموارد التعليمات المتوفرة ودراسات الحالة والمزيد.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="لقطة شاشة لمدخل ترقية Teams":::

### <a name="upgrade-to-skype-for-business-server"></a>الترقية إلى Skype for Business Server

سيكون مسار Skype for Business Server مختلفا استنادا إلى الإصدار الذي تختار الترقية إليه. يدعم Skype for Business Server 2015 الترقية الموضعية من Lync Server 2013. من ناحية أخرى، لكي تتمكن من الترقية إلى Skype for Business Server 2019، ستحتاج أولا إلى تقديم Skype for Business Server 2019 إلى تثبيت Lync Server 2013 عبر إضافة خادم جديد واحد أو أكثر، ثم نقل العمليات إلى خوادم 2019 الجديدة التي أضفتها.

إحدى النقاط المهمة التي يجب أخذها في الاعتبار هي أن مرحلة الدعم الحالية لكل منتج: Skype for Business 2019 في الدعم الرئيسي وأن Skype for Business 2015 حاليا في دعم موسع.  لذلك، نوصي بالترقية إلى Skype for Business Server 2019. لمعرفة المزيد حول الفرق بين الدعم الرئيسي والدعم الموسع، راجع [نهج دورة الحياة الثابتة](/lifecycle/policies/fixed).

راجع الموارد التالية للحصول على معلومات مفصلة حول كل سيناريو ترقية.

- [الترقية إلى Skype for Business Server 2019](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [الترقية إلى Skype for Business Server 2015](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
