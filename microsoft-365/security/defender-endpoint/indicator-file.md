---
title: إنشاء مؤشرات للملفات
ms.reviewer: ''
description: إنشاء مؤشرات لتجزئة ملف تحدد الكشف عن الكيانات ومنعها واستبعادها.
keywords: ملف، تجزئة، إدارة، مسموح به، محظور، حظر، نظيف، ضار، تجزئة ملف، عنوان ip، عناوين url، المجال
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: da9e030d929f65c7ea5bd83010d2b7f49b1d90d9
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535581"
---
# <a name="create-indicators-for-files"></a>إنشاء مؤشرات للملفات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [الخطة 1 من Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

منع المزيد من نشر هجوم في مؤسستك عن طريق حظر الملفات التي يحتمل أن تكون ضارة أو البرامج الضارة المشتبه بها. إذا كنت تعرف ملفا قابلا للتنفيذ قابلا للنقل (PE) يحتمل أن يكون ضارا، يمكنك حظره. ستمنع هذه العملية قراءتها أو كتابتها أو تنفيذها على الأجهزة في مؤسستك.

هناك ثلاث طرق يمكنك من خلالها إنشاء مؤشرات للملفات:

- عن طريق إنشاء مؤشر من خلال صفحة الإعدادات
- عن طريق إنشاء مؤشر سياقي باستخدام زر إضافة مؤشر من صفحة تفاصيل الملف
- عن طريق إنشاء مؤشر من خلال [واجهة برمجة تطبيقات المؤشر](ti-indicator.md)

## <a name="before-you-begin"></a>قبل البدء

من المهم فهم المتطلبات الأساسية التالية قبل إنشاء مؤشرات للملفات:

- تتوفر هذه الميزة إذا كانت مؤسستك تستخدم **برنامج الحماية من الفيروسات من Microsoft Defender (في الوضع النشط)** **وتم تمكين الحماية المستندة إلى السحابة**. لمزيد من المعلومات، راجع [إدارة الحماية المستندة إلى السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- يجب أن يكون إصدار عميل مكافحة البرامج الضارة 4.18.1901.x أو أحدث. الاطلاع [على إصدارات النظام الأساسي والمحرك الشهرية](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- معتمدة على الأجهزة التي تحتوي على Windows 10 والإصدار 1703 أو الإصدارات الأحدث Windows Server 2019 Windows Server 2016 Windows Server 2012 R2 Windows Server 2022.
    
   > [!NOTE]
   > يجب إلحاق Windows Server 2016 وserver Windows 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) المحلية لكي تعمل هذه الميزة. مؤشرات الملفات المخصصة مع إجراءات السماح والحظر والمعالجة متوفرة الآن أيضا في [المعاينة العامة لقدرات محرك مكافحة البرامج الضارة المحسنة macOS وLinux](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-engine-capabilities-for-linux-and-macos/ba-p/3292003).

- لبدء حظر الملفات، تحتاج أولا إلى [تشغيل ميزة "الحظر أو السماح"](advanced-features.md) في الإعدادات.

تم تصميم هذه الميزة لمنع تنزيل البرامج الضارة المشتبه بها (أو الملفات التي يحتمل أن تكون ضارة) من الويب. وهو يدعم حاليا الملفات القابلة للتنفيذ المحمولة (PE)، بما في ذلك ملفات .exe .dll. سيتم تمديد التغطية بمرور الوقت.

> [!IMPORTANT]
> في Defender for Endpoint Plan 1 و Defender for Business، يمكنك إنشاء مؤشر لحظر ملف أو السماح به. في Defender for Business، يتم تطبيق المؤشر عبر بيئتك ولا يمكن تحديد نطاقه على أجهزة معينة.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>إنشاء مؤشر للملفات من صفحة الإعدادات

1. في جزء التنقل، حدد **الإعدادات** \> **مؤشرات** **نقاط** \> النهاية (ضمن **القواعد**).

2. حدد علامة التبويب **"تجزئة الملف** ".

3. حدد **إضافة عنصر**.

4. حدد التفاصيل التالية:
    - مؤشر - حدد تفاصيل الكيان وحدد انتهاء صلاحية المؤشر.
    - الإجراء - حدد الإجراء الذي يجب اتخاذه وقم بتوفير وصف.
    - النطاق - حدد نطاق مجموعة الأجهزة (النطاق غير متوفر في [Defender for Business](../defender-business/mdb-overview.md)).

5. راجع التفاصيل في علامة التبويب "ملخص"، ثم حدد **"حفظ**".

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>إنشاء مؤشر سياقي من صفحة تفاصيل الملف

أحد الخيارات عند اتخاذ [إجراءات الاستجابة على ملف](respond-file-alerts.md) هو إضافة مؤشر للملف. عند إضافة تجزئة مؤشر لملف، يمكنك اختيار رفع تنبيه وحظر الملف كلما حاول جهاز في مؤسستك تشغيله.

لن تظهر الملفات التي تم حظرها تلقائيا بواسطة مؤشر في مركز الصيانة للملف، ولكن ستظل التنبيهات مرئية في قائمة انتظار التنبيهات.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>المعاينة العامة: التنبيه بشأن إجراءات حظر الملفات

> [!IMPORTANT]
> تتعلق المعلومات الواردة في هذا القسم (**المعاينة العامة لمحرك التحقيق والمعالجة التلقائي**) بالناتج التجريبي الذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

الإجراءات الحالية المدعومة لملف IOC هي السماح والتدقيق والحظر والمعالجة. بعد اختيار حظر ملف، يمكنك اختيار ما إذا كان هناك حاجة إلى تشغيل تنبيه. وبهذه الطريقة ستتمكن من التحكم في عدد التنبيهات التي يتم الوصول إليها في فرق عمليات الأمان الخاصة بك والتأكد من رفع التنبيهات المطلوبة فقط.

في Microsoft 365 Defender، انتقل إلى **الإعدادات** >  EndpointsIndicatorsAdd >  >  **New File Hash**.

اختر حظر الملف ومعالجتها.

اختر ما إذا كنت تريد إنشاء تنبيه على حدث كتلة الملف وتحديد إعدادات التنبيهات:

- عنوان التنبيه
- خطورة التنبيه
- الفئة
- الوصف
- الإجراءات الموصى بها

:::image type="content" source="images/indicators-generate-alert.png" alt-text="إعدادات التنبيه لمؤشرات الملفات" lightbox="images/indicators-generate-alert.png":::

> [!IMPORTANT]
>
> - عادة ما يتم فرض كتل الملفات وإزالتها في غضون دقيقتين، ولكن يمكن أن تستغرق ما يزيد عن 30 دقيقة.
> - إذا كانت هناك نهج IoC ملف متضاربة بنفس نوع الإنفاذ والهدف، فسيتم تطبيق نهج التجزئة الأكثر أمانا. سيفوز نهج IoC لتجزئة ملف SHA-256 على نهج IoC لتجزئة ملف SHA-1، والذي سيفوز على نهج IoC لتجزئة ملف MD5 إذا كانت أنواع التجزئة تحدد الملف نفسه. هذا صحيح دائما بغض النظر عن مجموعة الأجهزة.
> - في جميع الحالات الأخرى، إذا تم تطبيق نهج IoC للملفات المتضاربة ذات هدف الإنفاذ نفسه على جميع الأجهزة وعلى مجموعة الجهاز، فعندئذ بالنسبة إلى الجهاز، ستربح السياسة في مجموعة الأجهزة.
> - إذا تم تعطيل نهج مجموعة EnableFileHashComputation، يتم تقليل دقة حظر IoC للملف. ومع ذلك، قد يؤثر التمكين `EnableFileHashComputation` على أداء الجهاز. على سبيل المثال، قد يكون لنسخ ملفات كبيرة من مشاركة شبكة اتصال على جهازك المحلي، خاصة عبر اتصال VPN، تأثير على أداء الجهاز.
>
> لمزيد من المعلومات حول نهج مجموعة EnableFileHashComputation، راجع [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="public-preview-advanced-hunting-capabilities"></a>المعاينة العامة: قدرات التتبع المتقدمة

> [!IMPORTANT]
> تتعلق المعلومات الواردة في هذا القسم (**معاينة عامة لمحرك التحقيق والمعالجة التلقائي**) بالناتج التجريبي الذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

يمكنك الاستعلام عن نشاط إجراء الاستجابة في التتبع المسبق. فيما يلي نموذج استعلام تتبع متقدم:

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

لمزيد من المعلومات حول التتبع المتقدم، راجع [البحث بشكل استباقي عن التهديدات باستخدام التتبع المتقدم](advanced-hunting-overview.md).

فيما يلي أسماء مؤشرات الترابط الإضافية التي يمكن استخدامها في استعلام العينة من أعلى:

الملفات:

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

شهادات:

- EUS:Win32/CustomCertEnterpriseBlock!cl

يمكن أيضا عرض نشاط إجراء الاستجابة في المخطط الزمني للجهاز.

## <a name="policy-conflict-handling"></a>معالجة تعارض النهج

سيتبع تعارض معالجة نهج Cert وFily IoC الترتيب أدناه:

- إذا لم يسمح Windows Defender Application Control وAppLocker بفرض نهج/نهج الوضع، **فحظر**
- وإلا إذا كان الملف مسموحا به من قبل استبعاد برنامج الحماية من الفيروسات من Microsoft Defender، **فاسمح**
- وإلا إذا تم حظر الملف أو تحذيره بواسطة حظر أو تحذير IoC، **فحظر/احذر**
- وإلا إذا كان الملف مسموحا به من قبل نهج IoC لملف السماح، **فاسمح**
- وإلا إذا تم حظر الملف بواسطة قواعد ASR، CFA، AV، SmartScreen، ثم **الحظر**
- Else **Allow** (يمرر Windows Defender Application Control & نهج AppLocker، لا تنطبق قواعد IoC عليه)

>[!NOTE]
> في الحالات التي يتم فيها تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى **"حظر**"، ولكن تم تعيين Defender لنقطة النهاية إلى **"السماح**"، سيتم تعيين النهج الافتراضي إلى **"السماح**".

إذا كانت هناك نهج IoC ملف متضاربة بنفس نوع الإنفاذ والهدف، فسيتم تطبيق نهج تجزئة أكثر أمانا (بمعنى أطول). على سبيل المثال، سيفوز نهج IoC لتجزئة ملف SHA-256 على نهج IoC لتجزئة ملف MD5 إذا كان كلا النوعين من التجزئة يعرفان الملف نفسه.

> [!WARNING]
> تختلف معالجة تعارض النهج للملفات والشهادات عن معالجة تعارض النهج للمجالات/عناوين URL/عناوين IP.

تستخدم ميزات التطبيق المعرض للخطر للمخاطر وحظر إدارة الثغرات الأمنية IoCs الملف للتنفيذ وستتبع ترتيب معالجة التعارض أعلاه.

### <a name="examples"></a>أمثلة

<br>

****

|مكون|فرض المكونات|إجراء مؤشر الملف|نتيجه|
|---|---|---|---|
|استبعاد مسار ملف تقليل الأجزاء المعرضة للهجوم|سماح|حظر|حظر|
|قاعدة تقليل الأجزاء المعرضة للهجوم|حظر|سماح|سماح|
|التحكم في تطبيق Windows Defender|سماح|حظر|سماح|
|التحكم في تطبيق Windows Defender|حظر|سماح|حظر|
|استبعاد برنامج الحماية من الفيروسات من Microsoft Defender|سماح|حظر|سماح|
|

## <a name="see-also"></a>راجع أيضًا

- [إنشاء مؤشرات](manage-indicators.md)
- [إنشاء مؤشرات لـ IPs أو عناوين URL/المجالات](indicator-ip-domain.md)
- [إنشاء مؤشرات استنادا إلى الشهادات](indicator-certificates.md)
- [إدارة المؤشرات](indicator-manage.md)
