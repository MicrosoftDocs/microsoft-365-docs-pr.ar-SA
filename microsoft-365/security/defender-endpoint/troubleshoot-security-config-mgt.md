---
title: استكشاف المشاكل المتعلقة بإدارة الأمان ل Microsoft Defender لنقطة النهاية وإصلاحها
description: يمكنك استكشاف المشاكل التي قد تنشأ أثناء تشغيل الأجهزة وإصلاحها باستخدام إدارة الأمان ل Microsoft Defender لنقطة النهاية.
keywords: استكشاف الأخطاء المتعلقة باللوح وإصلاحها، ومشكلات الboard، وعارض الأحداث، وبناءات تجميع البيانات والمعاينة، وبيانات المستشعر، والت تشخيصات
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
ms.openlocfilehash: d6c3beb5a33a6d2323159917944e0f069b02035e
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63570868"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>استكشاف المشاكل المتعلقة بإدارة الأمان ل Microsoft Defender لنقطة النهاية وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تستخدم إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

إدارة الأمان ل Microsoft Defender ل Endpoint هي إمكانية للأجهزة التي لا يتم إدارتها بواسطة إدارة نقاط النهاية من Microsoft، إما Microsoft Intune أو Microsoft Endpoint Configuration Manager ، لتلقي تكوينات الأمان ل Microsoft Defender لنقطة النهاية مباشرة من إدارة نقاط النهاية.
لمزيد من المعلومات حول إدارة الأمان ل Microsoft Defender لنقطة النهاية، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة](/mem/intune/protect/mde-security-integration) التي تستخدم إدارة نقاط النهاية من Microsoft.

للحصول على إرشادات إدارة الأمان ل Microsoft Defender لتهيئة نقطة النهاية، راجع [إدارة تكوين أمان نقطة النهاية ل Microsoft Defender](security-config-management.md)

تم تصميم هذا التكاتف من النهاية إلى النهاية بحيث لا يحتاج إلى أي احتكاك ولا يتطلب إدخال المستخدم. ومع ذلك، إذا واجهت مشاكل أثناء التكوين، يمكنك عرض الأخطاء وإصلاحها ضمن النظام الأساسي ل Microsoft Defender for Endpoint.

> [!NOTE]
> إذا كنت تواجه مشاكل في تدفق اللحق للأجهزة الجديدة، فراجع المتطلبات الأساسية ل [Microsoft Defender لنقطة](/mem/intune/protect/mde-security-integration#prerequisites) النهاية وتأكد من اتباع إرشادات اللحق.

لمزيد من المعلومات حول محلل العميل، راجع استكشاف الأخطاء وإصلاحها في صحة المستشعر [باستخدام Microsoft Defender ل Endpoint Client Analyzer](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>تسجيل أجهزة الكمبيوتر المنضمة إلى المجال باستخدام Azure Active Directory

لتسجيل الأجهزة بنجاح في Azure Active Directory، ستحتاج إلى التأكد من ما يلي:

- يمكن لأجهزة الكمبيوتر المصادقة باستخدام وحدة التحكم بالمجال
- يمكن لأجهزة الكمبيوتر الوصول إلى موارد Microsoft التالية من داخل شبكة مؤسستك:
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- تم تكوين Azure AD connect لمزامنة كائنات الكمبيوتر. بشكل افتراضي، توجد OUs للكمبيوتر في نطاق مزامنة اتصال Azure AD. إذا كانت كائنات الكمبيوتر تنتمي إلى وحدات تنظيمية معينة، ف قم بتكوين وحدات OUs للمزامنة في Azure AD الاتصال. لمعرفة المزيد حول كيفية مزامنة كائنات الكمبيوتر باستخدام Azure AD الاتصال، راجع التصفية [المستندة إلى وحدة المؤسسة](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> لا يقوم Azure AD connect بمزامنة Windows الكمبيوتر Server 2012 R2. إذا كنت بحاجة إلى تسجيلها باستخدام Azure AD لإدارة الأمان ل Microsoft Defender لنقطة النهاية، ستحتاج إلى تخصيص قاعدة مزامنة اتصال Azure AD لتضمين كائنات الكمبيوتر هذه في نطاق المزامنة. راجع [إرشادات لتطبيق قاعدة الانضمام إلى الكمبيوتر في Azure Active Directory]() الاتصال.

> [!NOTE]
> لإكمال تدفق الادراج بنجاح، وباستقلال عن نظام التشغيل الخاص بجهاز ما، يمكن تغيير حالة Azure Active Directory لجهاز، استنادا إلى الحالة الأولية للأجهزة:
>
> <br>
>
>|بدء حالة الجهاز|حالة الجهاز الجديد|
>|---|---|
>|AADJ أو HAADJ بالفعل|يبقى كما هو|
>|Not AADJ or Hybrid Azure Active Directory Join (HAADJ) + Domain join|الجهاز هو HAADJ'd|
>|Not AADJ أو HAADJ + Not domain joined|الجهاز هو AADJ'd|
>
> حيث تمثل AADJ Azure Active Directory Joined و HAADJ تمثل Azure Active Directory Hybrid Joined.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>استكشاف الأخطاء وإصلاحها من مدخل Microsoft Defender لنقطة النهاية

من خلال مدخل Microsoft Defender ل Endpoint، يمكن لمسؤولي الأمان الآن استكشاف الأخطاء في إدارة الأمان ل Microsoft Defender ل Onboardpoint Endpoint وإصلاحها.

في **مخزون الأجهزة في** \> نقاط النهاية **، تمت إضافة** العمود مدار حسب للتصفية حسب قناة الإدارة (على سبيل المثال، MEM).

:::image type="content" alt-text="صورة لصفحة مخزون الجهاز" source="./images/device-inventory-mde-error.png":::

لرؤية قائمة بكل الأجهزة التي فشلت عملية إدارة الأمان ل Microsoft Defender لضم نقطة النهاية، يمكنك تصفية الجدول حسب **MDE-Error**.

في القائمة، حدد جهازا معينا لرؤية تفاصيل استكشاف الأخطاء وإصلاحها في اللوحة الجانبية، مع الإشارة إلى السبب الجذر للخطأ والوثائق المقابلة.

:::image type="content" alt-text="صورة لصفحة مخزون الجهاز التي تمت تصفيتها" source="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>تشغيل Microsoft Defender for Endpoint Client Analyzer على Windows

فكر في تشغيل "محلل العملاء" على نقاط النهاية التي فشلت في إكمال تدفق إدارة الأمان ل Microsoft Defender لتكميل نقاط النهاية. لمزيد من المعلومات حول محلل العميل، راجع استكشاف الأخطاء وإصلاحها في صحة المستشعر [باستخدام Microsoft Defender ل Endpoint Client Analyzer](overview-client-analyzer.md).

يمكن أن يوفر ملف إخراج "محلل العميل" (MDE Client Analyzer Results.htm) معلومات أساسية حول استكشاف الأخطاء وإصلاحها:

- التحقق من أن نظام تشغيل الجهاز في نطاق تدفق "إدارة الأمان" ل Microsoft Defender ل Onboardpoint Endpoint في **القسم "تفاصيل الجهاز العامة** "
- التحقق من أن الجهاز قد سجل بنجاح في Azure Active Directory في **تفاصيل إدارة تكوين الجهاز**

    ![صورة لنتائج محلل العميل](images/client-analyzer-results.png)

في قسم **النتائج المفصلة** من التقرير، يوفر "محلل العملاء" أيضا إرشادات قابلة للتنفيذ.

> [!TIP]
> تأكد من أن قسم النتائج المفصلة في التقرير لا يتضمن أي "أخطاء"، وتأكد من مراجعة كل رسائل "التحذير".

على سبيل المثال، كجزء من تدفق إعداد إدارة الأمان، من المطلوب أن يكون "مستأجر Azure Active Directory" في مستأجر Microsoft Defender for Endpoint مطابقا لم ID مستأجر SCP الذي يظهر في القسم تفاصيل إدارة تكوين الجهاز **للتقارير.** إذا كان ذلك ذا صلة، سيوصي إخراج التقرير بتنفيذ عملية التحقق هذه.

![صورة للنتائج المفصلة](images/detailed-results.png)

## <a name="general-troubleshooting"></a>استكشاف الأخطاء وإصلاحها بشكل عام

إذا لم تتمكن من تحديد الجهاز المضاف في AAD (دليل Azure النشط) أو MEM`Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus`، ولم تتلق رسالة خطأ أثناء التسجيل، يمكن أن يوفر التحقق من مفتاح التسجيل معلومات إضافية حول استكشاف الأخطاء وإصلاحها.

:::image type="content" alt-text="صورة حالة التسجيل." source="images/enrollment-status.png":::

يسرد الجدول التالي الأخطاء والاتجاهات حول ما يجب محاولة/التحقق منه لمعالجة الخطأ. تجدر الإشارة إلى أن قائمة الأخطاء غير مكتملة والاستناد إلى الأخطاء النموذجية/الشائعة التي واجهها العملاء في الماضي:

<br>

****

|رمز الخطأ|حالة التسجيل|إجراءات المسؤول|
|---|---|---|
|`5-9`,`11-12`, `26-33`|خطأ عام|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان. قد يعود سبب ذلك إلى عدم تلبية الجهاز للمتطلبات [الأساسية ل Microsoft Defender ل قناة إدارة نقطة النهاية](security-config-management.md). يمكن [أن يساعد تشغيل "محلل العملاء](https://aka.ms/BetaMDEAnalyzer) " على الجهاز على تحديد السبب الجذر لهذه المشكلة. إذا لم يساعد ذلك، فالرجاء الاتصال بالدعم.|
|`13-14`,`20`,`24`,`25`|مشكلة في الاتصال|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان قد يكون بسبب مشكلة في الاتصال. تحقق من فتح [Azure Active Directory إدارة نقاط النهاية من Microsoft نقاط](security-config-management.md#connectivity-requirements) النهاية في جدار الحماية.|
|`10`,`42`|فشل الانضمام المختلط العام|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان وفشل نظام التشغيل في تنفيذ ضم مختلط. استخدم [الأجهزة المنضمة إلى Azure Active Directory](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) المختلطة وإصلاحها من أجل استكشاف مشاكل فشل الانضمام المختلط على مستوى نظام التشغيل وإصلاحها.|
|`15`|عدم تطابق المستأجر|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. على الرغم من ذلك، حدث خطأ في تدفق إدارة تكوين الأمان لأن Microsoft Defender لمحدد مستأجر نقطة النهاية لا يطابق "مستأجر Azure Active Directory" الخاص بك. تأكد من أن "مستأجر Azure Active Directory" من مستأجر Defender for Endpoint يتطابق مع "معر ى المستأجر" في إدخال SCP لمجالك. للحصول على مزيد من التفاصيل، استكشاف الأخطاء المتعلقة بإدارة الأمان ل [Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-security-config-mgt.md).|
|`16`,`17`|خطأ مختلط - نقطة اتصال الخدمة|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، لا يتم تكوين سجل نقطة اتصال الخدمة (SCP) بشكل صحيح ويعوز توصيل الجهاز ب Azure AD. قد يعود سبب ذلك إلى تكوين SCP للانضمام إلى Enterprise DRS. تأكد من أن سجل SCP يشير إلى AAD (دليل Azure النشط) تم تكوين SCP باتباع أفضل الممارسات. لمزيد من المعلومات، راجع [تكوين نقطة اتصال الخدمة](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|خطأ الشهادة|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان بسبب خطأ في شهادة الجهاز. تنتمي شهادة الجهاز إلى مستأجر مختلف. تحقق من اتباع أفضل الممارسات عند إنشاء [ملفات تعريف شهادات موثوق بها](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36`|خطأ في API (API) ل LDAP|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان. تحقق من طبولوجيا الشبكة وتأكد من توفر API ل LDAP لإكمال طلبات الانضمام المختلط.|
|`37`|مشكلة المزامنة في الموقع|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان. أعِد المحاولة لاحقًا. إذا لم يساعد ذلك، فشاهد استكشاف الأخطاء في مزامنة الكائنات وإصلاحها باستخدام [Azure AD الاتصال المزامنة](/azure/active-directory/hybrid/tshoot-connect-objectsync).|
|`38`,`41`|خطأ DNS|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان بسبب خطأ DNS. تحقق من إعدادات اتصال الإنترنت و/أو DNS على الجهاز. قد تكون إعدادات DNS غير الصالحة على جانب محطة العمل. يتطلب Active Directory منك استخدام المجال DNS للعمل بشكل صحيح (وليس عنوان الموجه). لمزيد من المعلومات، راجع استكشاف الأخطاء المتعلقة بإدارة الأمان ل [Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-security-config-mgt.md).|
|`40`|مشكلة مزامنة الساعة|تم تشغيل الجهاز بنجاح في Microsoft Defender لنقطة النهاية. ومع ذلك، حدث خطأ في تدفق إدارة تكوين الأمان. تحقق من تعيين الساعة بشكل صحيح ومزامنتها على الجهاز الذي يحدث فيه الخطأ.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>استكشاف الأخطاء وإصلاحها في وقت تشغيل Azure Active Directory

### <a name="azure-active-directory-runtime"></a>وقت تشغيل Azure Active Directory

إن الآلية الرئيسية لاستعلام وقت تشغيل Azure Active Directory (AADRT) وإصلاحها هي تجميع تتبعات تصحيح الأخطاء. يستخدم Azure Active Directory Runtime على Windows **موفر ETW مع ID bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. يجب التقاط تتبعات ETW مع إعادة إنتاج الفشل (على سبيل المثال، إذا حدث فشل في الانضمام، يجب تمكين عمليات التتبع طوال الفترة الزمنية التي تغطي المكالمات ب AADRT واجهات برمجة التطبيقات لتنفيذ الانضمام).

راجع أدناه للحصول على خطأ نموذجي في سجل AADRT وكيفية قراءته:

![صورة لخصائص الحدث](images/event-properties.png)

من المعلومات الواردة في الرسالة، من الممكن في معظم الحالات فهم الخطأ الذي تم مصادفةه، وما هي واجهات برمجة المستخدمين في Win32 التي أرجعت الخطأ (إذا كان ذلك ممكنا)، وURL (إذا كان ذلك ممكنا) الذي تم استخدامه، وخطأ AAD (دليل Azure النشط) API وقت التشغيل الذي تم مصادفة.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>إرشادات لتطبيق قاعدة الانضمام إلى الكمبيوتر في AAD (دليل Azure النشط) الاتصال

بالنسبة إلى إدارة الأمان ل Microsoft Defender لنقطة النهاية على أجهزة الكمبيوتر المنضمة إلى مجال Windows Server 2012 R2، يلزم تحديث قاعدة مزامنة Azure AD الاتصال "In from AD-Computer Join". يمكن تحقيق ذلك عن طريق الاستنساخ وتعديل القاعدة، مما سيؤدي إلى تعطيل القاعدة الأصلية "In from AD - الانضمام إلى الكمبيوتر". يوفر الاتصال Azure AD هذه التجربة بشكل افتراضي من أجل إجراء تغييرات على القواعد المضمنة.

> [!NOTE]
>يجب تطبيق هذه التغييرات على الخادم الذي AAD (دليل Azure النشط) الاتصال فيه. إذا كان لديك مثيلات متعددة AAD (دليل Azure النشط) الاتصال، فيجب تطبيق هذه التغييرات على كل المثيلات.

1. افتح تطبيق محرر قواعد المزامنة من قائمة البدء. في قائمة القواعد، حدد موقع القاعدة المسماة **In من AD – انضمام الكمبيوتر**. **دون القيمة في العمود "الأسبقية" لهذه القاعدة.**

    ![صورة محرر قواعد المزامنة](images/57ea94e2913562abaf93749d306dd6cf.png)

2. مع تمييز **القاعدة In from AD – الانضمام** إلى الكمبيوتر، حدد **تحرير**. في مربع **الحوار تحرير تأكيد** القاعدة المحجوزة، حدد **نعم**.

   ![صورة لتأكيد تحرير القاعدة المحجوزة](images/8854440d6180a5580efda24110551c68.png)

3. سيتم **عرض نافذة تحرير** قاعدة المزامنة الواردة. قم بتحديث وصف القاعدة لتلاحظ أنه Windows Server 2012R2 باستخدام هذه القاعدة. اترك كل الخيارات الأخرى بدون تغيير باستثناء قيمة الأسبقية. أدخل قيمة الأسبقية التي تكون أعلى من القيمة من القاعدة الأصلية (كما هو مشاهد في قائمة القواعد).

   ![صورة للتأكيد](images/ee0f29162bc3f2fbe666c22f14614c45.png)

4. حدد **التالي** ثلاث مرات. سينتقل ذلك إلى المقطع "تحويلات" للقاعدة. لا تقوم بإجراء أي تغييرات على المقطعين "تصفية تحديد الcoping" و"قواعد الانضمام" للقاعدة. يجب أن يظهر المقطع "تحويلات" الآن.

    ![صورة لقاعدة المزامنة الواردة](images/296f2c2a705e41233631c3784373bc23.png)

5. قم بالتمرير إلى أسفل قائمة التحويلات. ابحث عن تحويل **السمة cloudFiltered** . في مربع النص في **العمود المصدر** ، حدد النص كله (Control-A) واحذفه. يجب أن يكون مربع النص فارغا الآن.

6. لصق محتوى القاعدة الجديدة في مربع النص.

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

7. حدد **حفظ** لحفظ القاعدة الجديدة.

> [!NOTE]
> بعد إجراء تغيير القاعدة هذا، ستكون هناك حاجة إلى مزامنة كاملة ل Active Directory. بالنسبة للبيئات الكبيرة، من المستحسن جدولة تغيير هذه القاعدة والمزامنة الكاملة أثناء فترات الهدوء في Active Directory المحلية.

## <a name="related-topic"></a>موضوع ذو صلة

- [إدارة Microsoft Defender لنقطة النهاية على الأجهزة التي تستخدم إدارة نقاط النهاية من Microsoft](/mem/intune/protect/mde-security-integration)
