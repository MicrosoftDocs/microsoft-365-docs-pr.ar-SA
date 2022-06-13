---
title: استكشاف مشكلات الإلحاق المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية
description: استكشاف المشكلات التي قد تنشأ أثناء إلحاق الأجهزة باستخدام إدارة الأمان Microsoft Defender لنقطة النهاية وإصلاحها.
keywords: استكشاف أخطاء الإلحاق وإصلاحها، ومشكلات الإلحاق، وعارض الأحداث، وبنيات جمع البيانات والمعاينة، وبيانات المستشعر والتشخيصات
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: fbfb20b233f1f942faaddd2a235a55beeb48d2c6
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043111"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>استكشاف مشكلات الإلحاق المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

إدارة الأمان Microsoft Defender لنقطة النهاية هي إمكانية للأجهزة التي لا تتم إدارتها بواسطة إدارة نقاط النهاية من Microsoft، إما Microsoft Intune أو Microsoft Endpoint Configuration Manager، لتلقي تكوينات الأمان Microsoft Defender لنقطة النهاية مباشرة من إدارة نقاط النهاية.
لمزيد من المعلومات حول إدارة الأمان Microsoft Defender لنقطة النهاية، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تحتوي على إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration).

للحصول على إرشادات حول "إدارة الأمان" Microsoft Defender لنقطة النهاية الإلحاق، راجع [Microsoft Defender لنقطة النهاية إدارة تكوين الأمان](security-config-management.md)

تم تصميم هذا الإلحاق الشامل ليكون عديم الاحتكاك ولا يتطلب إدخال المستخدم. ومع ذلك، إذا واجهت مشاكل أثناء الإعداد، يمكنك عرض الأخطاء واستكشاف الأخطاء وإصلاحها داخل النظام الأساسي Microsoft Defender لنقطة النهاية.

> [!NOTE]
> إذا كنت تواجه مشاكل في تدفق الإلحاق للأجهزة الجديدة، فراجع [المتطلبات الأساسية Microsoft Defender لنقطة النهاية](/mem/intune/protect/mde-security-integration#prerequisites) وتأكد من اتباع إرشادات الإلحاق.

لمزيد من المعلومات حول محلل العميل، راجع [استكشاف أخطاء حماية جهاز الاستشعار وإصلاحها باستخدام Microsoft Defender لنقطة النهاية Client Analyzer](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>تسجيل أجهزة الكمبيوتر المتصلة بالمجال باستخدام Azure Active Directory

لتسجيل الأجهزة بنجاح في Azure Active Directory، ستحتاج إلى التأكد من ما يلي:

- يمكن لأجهزة الكمبيوتر المصادقة باستخدام وحدة التحكم بالمجال
- يمكن لأجهزة الكمبيوتر الوصول إلى موارد Microsoft التالية من داخل شبكة مؤسستك:
  - /windows/iot/iot-enterprise/commercialization/licensing
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- تم تكوين Azure AD الاتصال لمزامنة كائنات الكمبيوتر. بشكل افتراضي، تكون الوحدات التنظيمية للكمبيوتر في نطاق مزامنة الاتصال Azure AD. إذا كانت كائنات الكمبيوتر تنتمي إلى وحدات تنظيمية معينة (OUs)، فكون الوحدات التنظيمية للمزامنة في Azure AD الاتصال. لمعرفة المزيد حول كيفية مزامنة كائنات الكمبيوتر باستخدام Azure AD الاتصال، راجع [التصفية المستندة إلى وحدة تنظيمية](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> لا تتم مزامنة Azure AD الاتصال Windows كائنات الكمبيوتر Server 2012 R2. إذا كنت بحاجة إلى تسجيلها في Azure AD لإدارة الأمان Microsoft Defender لنقطة النهاية، فستحتاج إلى تخصيص قاعدة مزامنة الاتصال Azure AD لتضمين عناصر الكمبيوتر هذه في نطاق المزامنة. راجع [إرشادات تطبيق قاعدة انضمام الكمبيوتر في الاتصال Azure Active Directory]().

> [!NOTE]
> لإكمال تدفق الإلحاق بنجاح، وبمعزل عن نظام التشغيل الخاص بالجهاز، يمكن أن تتغير حالة Azure Active Directory للجهاز، استنادا إلى الحالة الأولية للأجهزة:
>
> <br>
>
>|بدء حالة الجهاز|حالة جهاز جديد|
>|---|---|
>|AADJ أو HAADJ بالفعل|يبقى كما هو|
>|لم يتم ضم AADJ أو Hybrid Azure Active Directory Join (HAADJ) + Domain|الجهاز هو HAADJ'd|
>|ليس AADJ أو HAADJ + Not domain joined|الجهاز هو AADJ'd|
>
> حيث يمثل AADJ Azure Active Directory Joined ويمثل HAADJ Hybrid Azure Active Directory المنضم.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>استكشاف الأخطاء وإصلاحها من مدخل Microsoft Defender لنقطة النهاية

من خلال مدخل Microsoft Defender لنقطة النهاية، يمكن لمسؤولي الأمان الآن استكشاف أخطاء إدارة الأمان وإصلاحها للإلحاق Microsoft Defender لنقطة النهاية.

في **إدارة التكوين**، تمت إضافة عنصر واجهة مستخدم **إدارة أمان MDE الذي تم إلحاقه** لتقديم تصنيف حالة التسجيل للأجهزة المدارة Microsoft Defender لنقطة النهاية.

لمشاهدة قائمة بجميع الأجهزة التي تديرها Microsoft Defender لنقطة النهاية، حدد **عرض جميع الأجهزة المدارة بواسطة MDE**.

في القائمة، إذا لم تكن حالة تسجيل الجهاز "نجاح"، فحدد الجهاز للاطلاع على تفاصيل استكشاف الأخطاء وإصلاحها في اللوحة الجانبية، مع الإشارة إلى السبب الجذري للخطأ، والوثائق المقابلة.


:::image type="content" source="./images/secconfig-mde-error.png" alt-text="معايير التصفية المطبقة على صفحة مخزون الجهاز" lightbox="./images/secconfig-mde-error.png":::

> [!NOTE] 
> نحن على علم بمشكلة تؤثر على الكشف الدقيق عن أجهزة MDMs التابعة لجهات خارجية عند محاولة استخدام ميزة إدارة الأمان ونعمل على إصلاحها. 

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>تشغيل محلل عميل Microsoft Defender لنقطة النهاية على Windows

ضع في اعتبارك تشغيل "محلل العميل" على نقاط النهاية التي فشلت في إكمال إدارة الأمان لتدفق Microsoft Defender لنقطة النهاية الإلحاق. لمزيد من المعلومات حول محلل العميل، راجع [استكشاف أخطاء حماية جهاز الاستشعار وإصلاحها باستخدام Microsoft Defender لنقطة النهاية Client Analyzer](overview-client-analyzer.md).

يمكن أن يوفر ملف إخراج محلل العميل (MDE Client Analyzer Results.htm) معلومات استكشاف الأخطاء وإصلاحها الرئيسية:

- تحقق من أن نظام تشغيل الجهاز في نطاق إدارة الأمان لتدفق إلحاق Microsoft Defender لنقطة النهاية في قسم **"تفاصيل الجهاز العام**"
- تحقق من أن الجهاز قد سجل بنجاح في Azure Active Directory في **تفاصيل إدارة تكوين الجهاز**

  :::image type="content" source="images/client-analyzer-results.png" alt-text="نتائج محلل العميل" lightbox="images/client-analyzer-results.png":::

في قسم **"النتائج التفصيلية** " في التقرير، يوفر "محلل العميل" أيضا إرشادات قابلة للتنفيذ.

> [!TIP]
> تأكد من أن قسم "النتائج التفصيلية" في التقرير لا يتضمن أي "أخطاء"، وتأكد من مراجعة كافة رسائل "التحذير".

على سبيل المثال، كجزء من تدفق إلحاق إدارة الأمان، يجب أن يتطابق معرف مستأجر Azure Active Directory في مستأجر Microsoft Defender لنقطة النهاية مع معرف مستأجر SCP الذي يظهر في قسم **تفاصيل إدارة تكوين الجهاز** الخاص بالتقارير. إذا كان ذلك مناسبا، فسيوصي إخراج التقرير بإجراء هذا التحقق.

:::image type="content" source="images/detailed-results.png" alt-text="الصفحة التي تعرض النتائج التفصيلية" lightbox="images/detailed-results.png"

## <a name="general-troubleshooting"></a>استكشاف الأخطاء وإصلاحها بشكل عام

إذا لم تتمكن من تحديد الجهاز الذي تم إلحاقه في AAD أو MEM، ولم تتلق خطأ أثناء التسجيل، يمكن أن يوفر التحقق من مفتاح `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` التسجيل معلومات إضافية حول استكشاف الأخطاء وإصلاحها.

:::image type="content" source="images/enrollment-status.png" alt-text="الصفحة التي تعرض حالة التسجيل" lightbox="images/enrollment-status.png":::

يسرد الجدول التالي الأخطاء والاتجاهات حول ما يجب تجربته/إيداعه لمعالجة الخطأ. لاحظ أن قائمة الأخطاء غير مكتملة وتستند إلى الأخطاء النموذجية/الشائعة التي واجهها العملاء في الماضي:

<br>

****

|رمز الخطأ|حالة التسجيل|إجراءات المسؤول|
|---|---|---|
|`5-7`, `9`, `11-12`, `26-33`|خطأ عام|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان. قد يرجع ذلك إلى عدم استيفاء الجهاز [للمتطلبات الأساسية لقناة إدارة Microsoft Defender لنقطة النهاية](security-config-management.md). يمكن أن يساعد تشغيل ["محلل العميل"](https://aka.ms/BetaMDEAnalyzer) على الجهاز في تحديد السبب الجذري للمشكلة. إذا لم ينجح هذا الإجراء، فالرجاء الاتصال بالدعم.|
| `8`, `44` | مشكلة تكوين إدارة نقاط النهاية من Microsoft | تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، لم يتم تكوين إدارة نقاط النهاية من Microsoft من خلال مركز الإدارة للسماح بتكوين الأمان Microsoft Defender لنقطة النهاية. تأكد من [تكوين المستأجر إدارة نقاط النهاية من Microsoft وتشغيل الميزة](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management).|
|`13-14`,`20`,`24`,`25`|مشكلة في الاتصال|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان الذي قد يكون بسبب مشكلة في الاتصال. تحقق من فتح [Azure Active Directory ونقاط نهاية إدارة نقاط النهاية من Microsoft](security-config-management.md#connectivity-requirements) في جدار الحماية الخاص بك.|
|`10`,`42`|فشل الانضمام المختلط العام|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان وفشل نظام التشغيل في تنفيذ الصلة المختلطة. استخدم [استكشاف أخطاء الأجهزة المختلطة المتصلة ب Azure Active Directory](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) وإصلاحها لاستكشاف أخطاء الانضمام المختلط على مستوى نظام التشغيل وإصلاحها.|
|`15`|عدم تطابق المستأجر|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان لأن معرف المستأجر Microsoft Defender لنقطة النهاية لا يتطابق مع معرف مستأجر Azure Active Directory. تأكد من أن معرف مستأجر Azure Active Directory من مستأجر Defender لنقطة النهاية يطابق معرف المستأجر في إدخال SCP لمجالك. لمزيد من التفاصيل، [قم باستكشاف المشكلات المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-security-config-mgt.md).|
|`16`,`17`|خطأ مختلط - نقطة اتصال الخدمة|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، لم يتم تكوين سجل نقطة اتصال الخدمة (SCP) بشكل صحيح وتعذر ربط الجهاز Azure AD. قد يرجع ذلك إلى تكوين SCP للانضمام إلى DRS على مستوى المؤسسة. تأكد من تكوين نقاط سجل SCP إلى AAD وSCP باتباع أفضل الممارسات. لمزيد من المعلومات، راجع [تكوين نقطة اتصال خدمة](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|خطأ في الشهادة|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان بسبب خطأ في شهادة الجهاز. تنتمي شهادة الجهاز إلى مستأجر مختلف. تحقق من اتباع أفضل الممارسات عند إنشاء [ملفات تعريف شهادات موثوق بها](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36` , `37`| تكوين الاتصال AAD بشكل خاطئ |تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان بسبب تكوين خاطئ في الاتصال AAD. لتحديد ما يمنع الجهاز من التسجيل في AAD، ضع في اعتبارك تشغيل [أداة مستكشف أخطاء تسجيل الجهاز ومصلحها](/samples/azure-samples/dsregtool/dsregtool). بالنسبة Windows Server 2012 R2، قم بتشغيل [إرشادات استكشاف الأخطاء وإصلاحها المخصصة](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy).  |
|`38`,`41`|خطأ DNS|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان بسبب خطأ DNS. تحقق من اتصال الإنترنت و/أو إعدادات DNS على الجهاز. قد تكون إعدادات DNS غير صالحة على جانب محطة العمل. يتطلب منك Active Directory استخدام DNS للمجال للعمل بشكل صحيح (وليس عنوان الموجه). لمزيد من المعلومات، راجع [استكشاف المشكلات المتعلقة بإدارة الأمان Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-security-config-mgt.md).|
|`40`|مشكلة مزامنة الساعة|تم إلحاق الجهاز بنجاح Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان. تحقق من تعيين الساعة بشكل صحيح ومزامنتها على الجهاز الذي يحدث فيه الخطأ.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>استكشاف أخطاء وقت تشغيل Azure Active Directory وإصلاحها

### <a name="azure-active-directory-runtime"></a>وقت تشغيل Azure Active Directory

تتمثل الآلية الرئيسية لاستكشاف أخطاء وقت تشغيل Azure Active Directory (AADRT) وإصلاحها في جمع تتبعات تتبع الأخطاء. يستخدم وقت تشغيل Azure Active Directory على Windows **موفر ETW مع المعرف bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. يجب التقاط تتبعات ETW مع إعادة إنتاج الفشل (على سبيل المثال، إذا حدث فشل في الانضمام، يجب تمكين التتبعات طوال مدة تغطية المكالمات إلى واجهات برمجة تطبيقات AADRT لتنفيذ الانضمام).

راجع أدناه للحصول على خطأ نموذجي في سجل AADRT وكيفية قراءته:

:::image type="content" source="images/event-properties.png" alt-text="صفحة خصائص الحدث" lightbox="images/event-properties.png":::

من المعلومات الموجودة في الرسالة، من الممكن في معظم الحالات فهم الخطأ الذي تمت مواجهته، وما أرجعه Win32 API الخطأ (إن أمكن)، وعنوان URL (إذا كان قابلا للتطبيق) الذي تم استخدامه وما حدث من خطأ واجهة برمجة تطبيقات وقت تشغيل AAD.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>إرشادات تطبيق قاعدة "انضمام الكمبيوتر" في الاتصال AAD

بالنسبة لإدارة الأمان Microsoft Defender لنقطة النهاية على أجهزة الكمبيوتر المتصلة بمجال Windows Server 2012 R2، يلزم تحديث قاعدة مزامنة Azure AD الاتصال "من AD-Computer Join". يمكن تحقيق ذلك عن طريق استنساخ القاعدة وتعديلها، والتي ستعطل قاعدة "In from AD - Computer Join" الأصلية. يوفر Azure AD الاتصال بشكل افتراضي هذه التجربة لإجراء تغييرات على القواعد المضمنة.

> [!NOTE]
>يجب تطبيق هذه التغييرات على الخادم حيث يتم تشغيل الاتصال AAD. إذا كان لديك مثيلات متعددة الاتصال نشر AAD، فيجب تطبيق هذه التغييرات على كافة المثيلات.

1. افتح تطبيق محرر قواعد المزامنة من قائمة البدء. في قائمة القواعد، حدد موقع القاعدة المسماة **In من AD – Computer Join**. **لاحظ القيمة الموجودة في عمود "الأسبقية" لهذه القاعدة.**

   :::image type="content" source="images/57ea94e2913562abaf93749d306dd6cf.png" alt-text="محرر قواعد المزامنة" lightbox="images/57ea94e2913562abaf93749d306dd6cf.png":::

2. مع تمييز قاعدة **"In from AD – Computer Join** "، حدد **"Edit**". في مربع الحوار **"تحرير تأكيد القاعدة المحجوزة** "، حدد **"نعم**".

   :::image type="content" source="images/8854440d6180a5580efda24110551c68.png" alt-text="صفحة تأكيد القاعدة المحجوزة للتحرير" lightbox="images/8854440d6180a5580efda24110551c68.png":::

3. سيتم عرض نافذة **قاعدة تحرير المزامنة الواردة** . حدث وصف القاعدة لتلاحظ أنه ستتم مزامنة Windows Server 2012R2 باستخدام هذه القاعدة. اترك كافة الخيارات الأخرى دون تغيير باستثناء قيمة الأسبقية. أدخل قيمة للأسبقية أعلى من القيمة من القاعدة الأصلية (كما هو موضح في قائمة القواعد).

   :::image type="content" source="images/ee0f29162bc3f2fbe666c22f14614c45.png" alt-text="صفحة قاعدة تحرير المزامنة الواردة التي تقوم بإدخال القيم فيها" lightbox="images/ee0f29162bc3f2fbe666c22f14614c45.png":::

4. حدد **التالي** ثلاث مرات. سيؤدي ذلك إلى الانتقال إلى قسم "التحويلات" في القاعدة. لا تقم بإجراء أي تغييرات على مقاطع "عامل تصفية النطاق" و"قواعد الصلة" في القاعدة. يجب الآن عرض قسم "التحويلات".

   :::image type="content" source="images/296f2c2a705e41233631c3784373bc23.png" alt-text="قاعدة المزامنة الواردة" lightbox="images/296f2c2a705e41233631c3784373bc23.png":::

5. قم بالتمرير إلى أسفل قائمة التحويلات. ابحث عن التحويل للسمة **cloudFiltered** . في مربع النص في العمود **"المصدر** "، حدد النص بالكامل (Control-A) واحذفه. يجب أن يكون مربع النص فارغا الآن.

6. الصق محتوى القاعدة الجديدة في مربع النص.

    ```command
    IIF(
      IsNullOrEmpty([userCertificate])
      ||
      (
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        (Left([operatingSystemVersion],2) = "6.")
        &&
        (Left([operatingSystemVersion],3) <> "6.3")
      )
      ||
      (
        (Left([operatingSystemVersion],3) = "6.3")
        &&
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        With(
          $validCerts,
          Where(
            $c,
            [userCertificate],
            IsCert($c) && CertNotAfter($c) > Now() && RegexIsMatch(CertSubject($c), "CN=[{]*" & StringFromGuid([objectGUID]) & "[}]*", "IgnoreCase")),
          Count($validCerts) = 0)
      ),
      True,
      NULL
    )
    ```

7. حدد **"حفظ** " لحفظ القاعدة الجديدة.

> [!NOTE]
> بعد إجراء تغيير القاعدة هذا، ستكون هناك حاجة إلى مزامنة كاملة ل Active Directory. بالنسبة إلى البيئات الكبيرة، يوصى بجدولة تغيير القاعدة هذا والمزامنة الكاملة أثناء فترات الهدوء المحلية ل Active Directory.

## <a name="related-topic"></a>الموضوع ذو الصلة

- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة باستخدام إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration)
