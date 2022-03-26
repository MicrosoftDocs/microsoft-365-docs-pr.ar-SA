---
title: Microsoft Defender لتخزين بيانات نقطة النهاية والخصوصية
description: تعرف على كيفية تعامل Microsoft Defender لنقطة النهاية مع الخصوصية والبيانات التي يقوم بتجميعها.
keywords: Microsoft Defender لنقطة النهاية، تخزين البيانات والخصوصية، التخزين، الخصوصية، الترخيص، الموقع الجغرافي، استبقاء البيانات، البيانات
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
ms.openlocfilehash: 7e6e530406b4211c62d315f26b8f956cf6bf1bde
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570496"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Microsoft Defender لتخزين بيانات نقطة النهاية والخصوصية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يتناول هذا القسم بعض الأسئلة الأكثر شيوعا المتعلقة بالخصوصية ومعالجة البيانات ل Defender for Endpoint.

> [!NOTE]
> يشرح هذا المستند تخزين البيانات وتفاصيل الخصوصية المتعلقة ب Defender for Endpoint. لمزيد من المعلومات المتعلقة ب Defender for Endpoint ومنتجات وخدمات أخرى مثل برنامج الحماية من الفيروسات من Microsoft Defender و Windows، راجع [بيان خصوصية Microsoft](https://go.microsoft.com/fwlink/?linkid=827576). راجع أيضا [Windows الأسئلة الشائعة حول](https://go.microsoft.com/fwlink/?linkid=827577) الخصوصية للحصول على مزيد من المعلومات.

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>ما هي البيانات التي يقوم Microsoft Defender for Endpoint بتجميعها؟

سيجمع Microsoft Defender for Endpoint المعلومات ويخزنها من أجهزتك التي تم تكوينها في مستأجر مخصص للعميل ومفزول خاص بالخدمة لأغراض الإدارة والتعقب وإعداد التقارير.

تتضمن المعلومات التي يتم تجميعها بيانات الملفات (مثل أسماء الملفات والأحجام والتفاصيل)، وبيانات العملية (العمليات قيد التشغيل، والتقعيد)، وبيانات السجل، وبيانات اتصال الشبكة (معرفات IPs والمنافذ المضيفة)، وتفاصيل الجهاز (مثل معرفات الأجهزة والأسماء، والإصدار الذي يستخدم نظام التشغيل).

تخزن Microsoft هذه البيانات بأمان في Microsoft Azure وتحتفظ بها وفقا لممارسات الخصوصية في Microsoft ونهج [مركز الثقة من Microsoft](https://go.microsoft.com/fwlink/?linkid=827578).

تمكن هذه البيانات Defender لنقطة النهاية من:

- تحديد مؤشرات الهجوم (IOAs) بشكل استباقي في مؤسستك
- إنشاء تنبيهات إذا تم اكتشاف هجوم محتمل
- زود عمليات الأمان الخاصة بك بنظرة عرض على الأجهزة والملفات وعنابر URL ذات الصلة بإشارة التهديدات من شبكتك، مما يمكنك من التحقق من وجود تهديدات الأمان واستكشافها على الشبكة.

لا تستخدم Microsoft بياناتك للإعلان.

## <a name="data-protection-and-encryption"></a>حماية البيانات والتشفير

تستخدم خدمة Defender for Endpoint أحدث تقنيات حماية البيانات المستندة إلى البنية الأساسية ل Microsoft Azure.

هناك جوانب مختلفة ذات صلة بحماية البيانات تهتم بها خدمتنا. التشفير هو أحد أكثر التشفيرات أهمية ويتضمن تشفير البيانات بشكل راحة والتشفير في رحلة الطيران وإدارة المفاتيح باستخدام "مخزن المفاتيح". لمزيد من المعلومات حول التقنيات الأخرى التي تستخدمها خدمة Defender for Endpoint، راجع [نظرة عامة حول تشفير Azure](/azure/security/security-azure-encryption-overview).

في كل السيناريوهات، يتم تشفير البيانات باستخدام تشفير [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) بال 256 بت كحد أدنى.

## <a name="data-storage-location"></a>موقع تخزين البيانات

يعمل Defender for Endpoint في مراكز بيانات Microsoft Azure في الاتحاد الأوروبي أو المملكة المتحدة أو الولايات المتحدة. قد يتم تخزين بيانات العملاء التي تقوم الخدمة بتجميعها في: (أ) الموقع الجغرافي للمستأجر كما هو محدد أثناء عملية توفير الخدمة، أو (ب) إذا كان Defender for Endpoint يستخدم خدمة Microsoft أخرى عبر الإنترنت لمعالجة هذه البيانات، فإن الموقع الجغرافي كما هو محدد بواسطة قواعد تخزين البيانات الخاصة بهذه الخدمة الأخرى عبر الإنترنت.

قد يتم أيضا تخزين بيانات العملاء في نموذج مستعار في أنظمة التخزين والتخزين المركزية في الولايات المتحدة.

بمجرد تكوينها، لا يمكنك تغيير الموقع الذي تم تخزين البيانات فيه. يوفر ذلك طريقة ملائمة لتقليل مخاطر التوافق عن طريق تحديد المواقع الجغرافية التي تقيم فيها بياناتك بشكل نشط.

## <a name="is-my-data-isolated-from-other-customer-data"></a>هل بياناتي معزولة عن بيانات العملاء الأخرى؟

نعم، يتم عزل بياناتك من خلال مصادقة الوصول والمصادقة المنطقية استنادا إلى معرف العميل. يمكن لكل عميل الوصول إلى البيانات التي يتم تجميعها من المؤسسة والبيانات العامة التي تقدمها Microsoft فقط.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>كيف تمنع Microsoft أنشطة insider الضارة وإساءة استخدام أدوار الامتيازات العالية؟

تم منح مطوري Microsoft ومديريه، حسب التصميم، امتيازات كافية لتنفيذ واجباتهم المعينة لتشغيل الخدمة تطويرها. تنشر Microsoft مجموعات من عناصر التحكم الوقائية والمهينة وتفاعلية بما في ذلك الآليات التالية للمساعدة في الحماية من أنشطة المطور و/أو النشاط الإداري غير المصرح به:

- تحكم وصول محكم للبيانات الحساسة
- مجموعات من عناصر التحكم التي تحسن إلى حد كبير الكشف المستقل عن النشاط الضار
- مستويات متعددة من المراقبة، والتسجل، وإعداد التقارير

بالإضافة إلى ذلك، تجري Microsoft عمليات التحقق في الخلفية لبعض العاملين في العمليات، كما تحصر إمكانية الوصول إلى التطبيقات والشبكات والبنية الأساسية للشبكة بما يتناسب مع مستوى التحقق في الخلفية. يتبع موظفو العمليات عملية رسمية عندما يطلبون منه الوصول إلى حساب العميل أو المعلومات ذات الصلة أثناء أداء واجباته.

يتم منح إمكانية الوصول إلى بيانات الخدمات التي تم نشرها في مراكز بيانات Microsoft Azure Government فقط للعاملين العاملين الذين تم فحصهم وموافقاتهم لمعالجة البيانات التي تخضع لبعض اللوائح والمتطلبات الحكومية، مثل FedRAMP وNIST 800.171 (DIB) و ITAR و IRS 1075 و DoD L4 و CJIS.

## <a name="is-data-shared-with-other-customers"></a>هل يتم مشاركة البيانات مع عملاء آخرين؟

لا. يتم عزل بيانات العملاء عن العملاء الآخرين ولا يتم مشاركتها. ومع ذلك، قد يتم مشاركة نتائج تحليلات البيانات الناتجة عن معالجة Microsoft، والتي لا تحتوي على أي بيانات خاصة بعملائنا، مع عملاء آخرين. يمكن لكل عميل الوصول إلى البيانات التي يتم تجميعها من المؤسسة والبيانات العامة التي تقدمها Microsoft فقط.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>ما المدة التي ستخزن فيها Microsoft بياناتي؟ ما هو نهج استبقاء البيانات في Microsoft؟

### <a name="at-service-onboarding"></a>في خدمة ال متنبها

بشكل افتراضي، يتم الاحتفاظ بالبيانات لمدة 180 يوما؛ ومع ذلك، يمكنك تحديد نهج استبقاء البيانات لبياناتك. يحدد ذلك المدة التي سيخزن بها Window Defender ل Endpoint بياناتك. هناك مرونة في الاختيار من شهر واحد إلى ستة أشهر لتلبية احتياجات التوافق التنظيمي للشركة.

### <a name="at-contract-termination-or-expiration"></a>عند إنهاء العقد أو انتهاء صلاحيته

سيتم الاحتفاظ بالبيانات وستتوفر لك عندما يكون الترخيص ضمن فترة سماح أو في وضع تعليق. في نهاية هذه الفترة، سيتم مسح تلك البيانات من أنظمة Microsoft لجعلها غير قابلة لردادها، في موعد لا يزيد عن 180 يوما من إنهاء العقد أو انتهاء صلاحيته.

### <a name="advanced-hunting-data"></a>البيانات المتقدمة للصيد

الصيد المتقدم هو أداة بحث عن تهديدات تستند إلى استعلام تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الخام.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>هل يمكن أن تساعدنا Microsoft في الحفاظ على التوافق التنظيمي؟

توفر Microsoft للعملاء معلومات مفصلة حول برامج الأمان والتوافق الخاصة ب Microsoft، بما في ذلك تقارير التدقيق وحزم التوافق، لمساعدة العملاء في تقييم Defender لخدمات نقطة النهاية وفقا لمتطلباتهم القانونية والتنظيمية الخاصة. لقد حقق Defender لنقطة النهاية عددا من الشهادات بما في ذلك ISO وSOC و FedRAMP High وPCI ويتابع متابعة الشهادات الوطنية والإقليمية وشهادات خاصة بال الصناعة.

من خلال تزويد العملاء بالخدمات المتوافقة والمتحقق منها بشكل مستقل، تسهل Microsoft على العملاء تحقيق التوافق للبنية الأساسية والتطبيقات التي يديرونها.

لمزيد من المعلومات حول تقارير مصادقة Defender for Endpoint، راجع [مركز Microsoft Trust Center](https://servicetrust.microsoft.com/). 

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
