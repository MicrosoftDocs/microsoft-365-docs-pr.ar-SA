---
title: معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية
description: تعرف على كيفية التعامل مع الإيجابيات الخاطئة أو السلبيات الخاطئة في Microsoft Defender لنقطة النهاية.
keywords: مكافحة الفيروسات، استثناء، استثناء، Microsoft Defender لنقطة النهاية، إيجابية خاطئة، سلبية خاطئة، ملف محظور، url محظور
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
- m365solution-scenario
- m365scenario-fpfn
ms.topic: how-to
ms.date: 12/02/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
ms.openlocfilehash: d7477c2006acd04008e6cb56cb22261a4db4a92b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789899"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

في حلول حماية نقطة النهاية، فإن الإيجابية الخاطئة هي كيان، مثل ملف أو عملية، تم اكتشافه وتحديده على أنه ضار، على الرغم من أن الكيان ليس في الواقع تهديدا. السالب الخاطئ هو كيان لم يتم الكشف عنه كتهديد، على الرغم من أنه في الواقع ضار. يمكن أن تحدث الإيجابيات/السلبيات الخاطئة مع أي حل للحماية من التهديدات، بما [في ذلك Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md).

:::image type="content" source="images/false-positives-overview.png" alt-text="تعريف الإيجابيات والسلبيات الخاطئة في مدخل Microsoft Defender لنقطة النهاية" lightbox="images/false-positives-overview.png":::

لحسن الحظ، يمكن اتخاذ خطوات لمعالجة هذه الأنواع من المشكلات وتقليلها. إذا كنت ترى إيجابيات/سلبيات خاطئة في [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)، يمكن لعمليات الأمان اتخاذ خطوات لمعالجتها باستخدام العملية التالية:

1. [مراجعة التنبيهات وتصنيفها](#part-1-review-and-classify-alerts)
2. [مراجعة إجراءات المعالجة التي تم اتخاذها](#part-2-review-remediation-actions)
3. [مراجعة الاستثناءات وتحديدها](#part-3-review-or-define-exclusions)
4. [إرسال كيان للتحليل](#part-4-submit-a-file-for-analysis)
5. [مراجعة إعدادات الحماية من التهديدات وضبطها](#part-5-review-and-adjust-your-threat-protection-settings)

يمكنك الحصول على المساعدة إذا كانت لا تزال لديك مشاكل تتعلق بإيجابيات/سلبيات خاطئة بعد تنفيذ المهام الموضحة في هذه المقالة. هل [لا تزال بحاجة إلى المساعدة؟](#still-need-help)

:::image type="content" source="images/false-positives-step-diagram.png" alt-text="خطوات معالجة الإيجابيات والسلبيات الخاطئة" lightbox="images/false-positives-step-diagram.png":::

> [!NOTE]
> تم إعداد هذه المقالة كإرشادات لمشغلي الأمان ومسؤولي الأمان الذين يستخدمون [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md).

## <a name="part-1-review-and-classify-alerts"></a>الجزء الأول: مراجعة التنبيهات وتصنيفها

إذا رأيت [تنبيها](alerts.md) تم تشغيله لأنه تم الكشف عن شيء ما على أنه ضار أو مريب لم يكن من المفترض أن يكون، يمكنك منع التنبيه لهذا الكيان. يمكنك أيضا منع التنبيهات التي ليست بالضرورة إيجابيات خاطئة، ولكنها غير موجبة. نوصي بتصنيف التنبيهات أيضا.

تساعد إدارة التنبيهات وتصنيف الإيجابيات الصحيحة/الخاطئة على تدريب حل الحماية من التهديدات ويمكن أن تقلل من عدد الإيجابيات الخاطئة أو السلبيات الخاطئة بمرور الوقت. يساعد اتخاذ هذه الخطوات أيضا على تقليل الضوضاء في لوحة معلومات عمليات الأمان بحيث يمكن لفريق الأمان التركيز على عناصر العمل ذات الأولوية الأعلى.

### <a name="determine-whether-an-alert-is-accurate"></a>تحديد ما إذا كان التنبيه دقيقا

قبل تصنيف تنبيه أو منعه، حدد ما إذا كان التنبيه دقيقا أو إيجابيا زائفا أو ضارا.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **قائمة انتظار التنبيهات**.

3. حدد تنبيها للحصول على مزيد من التفاصيل حول التنبيه. (راجع [تنبيهات المراجعة في Microsoft Defender لنقطة النهاية](review-alerts.md).)

4. استنادا إلى حالة التنبيه، اتبع الخطوات الموضحة في الجدول التالي:

   |حالة التنبيه|ما يجب فعله|
   |---|---|
   |التنبيه دقيق|قم بتعيين التنبيه، ثم [تحقق منه](investigate-alerts.md) بشكل أكبر.|
   |التنبيه إيجابي خطأ|1. [تصنيف التنبيه](#classify-an-alert) على أنه إيجابية خاطئة.<br/><br/>2. [منع التنبيه](#suppress-an-alert).<br/><br/>3. [إنشاء مؤشر](#indicators-for-microsoft-defender-for-endpoint) Microsoft Defender لنقطة النهاية.<br/><br/>4. [إرسال ملف إلى Microsoft للتحليل](#part-4-submit-a-file-for-analysis).|
   |التنبيه دقيق، ولكنه غير مهم (غير مهم)|[تصنيف التنبيه](#classify-an-alert) على أنه إيجابي حقيقي، ثم [منع التنبيه](#suppress-an-alert).|

### <a name="classify-an-alert"></a>تصنيف تنبيه

يمكن تصنيف التنبيهات على أنها إيجابيات خاطئة أو إيجابيات حقيقية في Microsoft 365 Defender. يساعد تصنيف التنبيهات على تدريب Microsoft Defender لنقطة النهاية بحيث، مع مرور الوقت، سترى المزيد من التنبيهات الصحيحة وتنبيهات خاطئة أقل.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. حدد **قائمة انتظار التنبيهات**، ثم حدد تنبيها.

3. بالنسبة للتنبيه المحدد، حدد **تنبيه "إدارة** **الإجراءات**\>". يتم فتح جزء قائمة منبثقة.

4. في قسم **"إدارة التنبيه** "، حدد إما **التنبيه "صواب"** أو **"تنبيه خطأ**". (استخدم **تنبيه False** لتصنيف إيجابية خاطئة.)

> [!TIP]
> لمزيد من المعلومات حول منع التنبيهات، راجع [إدارة التنبيهات Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/manage-alerts). وإذا كانت مؤسستك تستخدم خادم إدارة معلومات الأمان والأحداث (SIEM)، فتأكد من تعريف قاعدة منع هناك أيضا.

### <a name="suppress-an-alert"></a>منع تنبيه

إذا كانت لديك تنبيهات إما إيجابية خاطئة أو إيجابية صحيحة ولكن للأحداث غير المتوقعة، يمكنك منع هذه التنبيهات في Microsoft 365 Defender. يساعد منع التنبيهات على تقليل الضوضاء في لوحة معلومات عمليات الأمان.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، حدد **قائمة انتظار التنبيهات**.

3. حدد تنبيها تريد منعه لفتح جزء **التفاصيل** الخاص به.

4. في جزء **التفاصيل** ، اختر علامة الحذف (**...**)، ثم **أنشئ قاعدة منع**.

5. حدد كل الإعدادات لقاعدة المنع، ثم اختر **"حفظ**".

> [!TIP]
> هل تحتاج إلى المساعدة في قواعد المنع؟ راجع [منع تنبيه وإنشاء قاعدة منع جديدة](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>الجزء الثاني: مراجعة إجراءات المعالجة

يتم اتخاذ [إجراءات المعالجة](manage-auto-investigation.md#remediation-actions)، مثل إرسال ملف إلى العزل أو إيقاف عملية، على الكيانات (مثل الملفات) التي يتم الكشف عنها كتهديدات. تحدث عدة أنواع من إجراءات المعالجة تلقائيا من خلال التحقيق التلقائي برنامج الحماية من الفيروسات من Microsoft Defender:

- عزل ملف
- إزالة مفتاح تسجيل
- إنهاء عملية
- إيقاف خدمة
- تعطيل برنامج تشغيل
- إزالة مهمة مجدولة

تحدث إجراءات أخرى، مثل بدء فحص مكافحة الفيروسات أو جمع حزمة تحقيق، يدويا أو من خلال [Live Response](live-response.md). لا يمكن التراجع عن الإجراءات التي تم اتخاذها من خلال الاستجابة المباشرة.

بعد مراجعة التنبيهات، تكون خطوتك التالية هي [مراجعة إجراءات المعالجة](manage-auto-investigation.md). إذا تم اتخاذ أي إجراءات نتيجة للإيجابيات الخاطئة، يمكنك التراجع عن معظم أنواع إجراءات المعالجة. على وجه التحديد، يمكنك:

- [استعادة ملف تم عزله من مركز الصيانة](#restore-a-quarantined-file-from-the-action-center)
- [التراجع عن إجراءات متعددة في وقت واحد](#undo-multiple-actions-at-one-time)
- [إزالة ملف من العزل عبر أجهزة متعددة](#remove-a-file-from-quarantine-across-multiple-devices). و
- [استعادة ملف من الفحص](#restore-file-from-quarantine)

عند الانتهاء من مراجعة الإجراءات التي تم اتخاذها نتيجة لإيجابيات خاطئة والتراجع عنها، تابع [لمراجعة الاستثناءات أو تعريفها](#part-3-review-or-define-exclusions).

### <a name="review-completed-actions"></a>مراجعة الإجراءات المكتملة

1. في جزء التنقل الأيمن من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، انقر فوق **"مركز الصيانة**".

2. حدد علامة التبويب " **محفوظات** " لعرض قائمة بالإجراءات التي تم اتخاذها.

3. حدد عنصرا لعرض مزيد من التفاصيل حول إجراء المعالجة الذي تم اتخاذه.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>استعادة ملف تم عزله من مركز الصيانة

1. في جزء التنقل الأيمن من مدخل Microsoft 365 Defender، انقر فوق **"مركز الصيانة**".

2. في علامة التبويب " **محفوظات** "، حدد إجراء تريد التراجع عنه.

3. في جزء القائمة المنبثقة، حدد **"تراجع**". إذا تعذر التراجع عن الإجراء باستخدام هذا الأسلوب، فلن يظهر زر **"تراجع** ". (لمعرفة المزيد، راجع [التراجع عن الإجراءات المكتملة](manage-auto-investigation.md#undo-completed-actions).)

### <a name="undo-multiple-actions-at-one-time"></a>التراجع عن إجراءات متعددة في وقت واحد

1. في جزء التنقل الأيمن من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، انقر فوق **"مركز الصيانة**".

2. في علامة التبويب " **محفوظات** "، حدد الإجراءات التي تريد التراجع عنها.

3. في الجزء الموجود على الجانب الأيسر من الشاشة، حدد **"تراجع".**

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>إزالة ملف من العزل عبر أجهزة متعددة

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/autoir-quarantine-file-1.png" alt-text="ملف العزل" lightbox="images/autoir-quarantine-file-1.png":::

1. في جزء التنقل الأيمن من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، انقر فوق **"مركز الصيانة**".

2. في علامة التبويب " **محفوظات** "، حدد ملفا يحتوي على **ملف عزل** نوع الإجراء.

3. في الجزء الموجود على الجانب الأيسر من الشاشة، حدد **تطبيق على X المزيد من مثيلات هذا الملف**، ثم حدد **"تراجع".**

### <a name="restore-file-from-quarantine"></a>استعادة ملف من الفحص

يمكنك العودة إلى الحالة السابقة وإزالة ملف من العزل إذا كنت قد قررت أنه نظيف بعد التحقيق. قم بتشغيل الأمر التالي على كل جهاز حيث تم عزل الملف.

1. افتح موجه سطر أوامر غير مقيد على الجهاز:

   1. انتقل إلى **شاشة البدء** واكتب _cmd_.
   2. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

2. أدخل الأمر التالي، ثم اضغط على **مفتاح الإدخال Enter**:

    ```console
    "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > في بعض السيناريوهات، قد يظهر **ThreatName** ك `EUS:Win32/CustomEnterpriseBlock!cl`. سيقوم Defender لنقطة النهاية باستعادة كافة الملفات المحظورة المخصصة التي تم عزلها على هذا الجهاز في آخر 30 يوما.
    >
    > قد لا يكون الملف الذي تم عزله كتهديد محتمل للشبكة قابلا للاسترداد. إذا حاول مستخدم استعادة الملف بعد العزل، فقد لا يمكن الوصول إلى هذا الملف. قد يرجع ذلك إلى أن النظام لم يعد لديه بيانات اعتماد الشبكة للوصول إلى الملف. عادة ما يكون ذلك نتيجة لتسجيل الدخول المؤقت إلى نظام أو مجلد مشترك وانتهت صلاحية الرموز المميزة للوصول.

3. في الجزء الموجود على الجانب الأيسر من الشاشة، حدد **تطبيق على X المزيد من مثيلات هذا الملف**، ثم حدد **"تراجع".**

## <a name="part-3-review-or-define-exclusions"></a>الجزء 3: مراجعة الاستثناءات أو تعريفها

الاستثناء هو كيان، مثل ملف أو عنوان URL، تحدده استثناء لإجراءات المعالجة. لا يزال من الممكن الكشف عن الكيان المستبعد، ولكن لا يتم اتخاذ أي إجراءات معالجة على هذا الكيان. أي أنه لن يتم إيقاف الملف أو العملية المكتشفة أو إرسالها إلى العزل أو إزالتها أو تغييرها بواسطة Microsoft Defender لنقطة النهاية.

لتعريف الاستثناءات عبر Microsoft Defender لنقطة النهاية، قم بتنفيذ المهام التالية:

- [تحديد استثناءات برنامج الحماية من الفيروسات من Microsoft Defender](#exclusions-for-microsoft-defender-antivirus)
- [إنشاء مؤشرات "السماح" Microsoft Defender لنقطة النهاية](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> تنطبق استثناءات برنامج الحماية من الفيروسات من Microsoft Defender فقط على الحماية من الفيروسات، وليس عبر قدرات Microsoft Defender لنقطة النهاية الأخرى. لاستبعاد الملفات على نطاق واسع، استخدم الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender [والمؤشرات المخصصة](/microsoft-365/security/defender-endpoint/manage-indicators) Microsoft Defender لنقطة النهاية.

تصف الإجراءات الواردة في هذا القسم كيفية تحديد الاستثناءات والمؤشرات.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>استثناءات برنامج الحماية من الفيروسات من Microsoft Defender

بشكل عام، يجب ألا تحتاج إلى تحديد استثناءات برنامج الحماية من الفيروسات من Microsoft Defender. تأكد من تحديد الاستثناءات بشكل لا يضاهى، ومن تضمين الملفات والمجلدات والعمليات والملفات المفتوحة للعملية فقط التي تؤدي إلى نتائج إيجابية خاطئة. بالإضافة إلى ذلك، تأكد من مراجعة الاستثناءات المحددة بانتظام. نوصي باستخدام [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) لتعريف استثناءات الحماية من الفيروسات أو تحريرها؛ ومع ذلك، يمكنك استخدام أساليب أخرى، مثل [نهج المجموعة](/azure/active-directory-domain-services/manage-group-policy) (راجع [إدارة Microsoft Defender لنقطة النهاية](manage-mde-post-migration.md).

> [!TIP]
> هل تحتاج إلى مساعدة في استثناءات برنامج الحماية من الفيروسات؟ راجع [تكوين الاستثناءات والتحقق من صحتها لإجراء عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>استخدام إدارة نقاط النهاية من Microsoft لإدارة استثناءات مكافحة الفيروسات (للنهج الموجودة)

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com>) وسجل الدخول.

2. اختر برنامج **الحماية من الفيروسات** **لأمان** \> نقطة النهاية، ثم حدد نهجا موجودا. (إذا لم يكن لديك نهج موجود، أو إذا كنت تريد إنشاء نهج جديد، فانتقل إلى [الإجراء التالي](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions)).

3. اختر **"خصائص**"، وإلى جانب **إعدادات "التكوين"**، اختر **"تحرير**".

4. قم **بتوسيع برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات** ثم حدد الاستثناءات الخاصة بك.

5. اختر **"مراجعة + حفظ**"، ثم اختر **"حفظ**".

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>استخدام إدارة نقاط النهاية من Microsoft لإنشاء نهج الحماية من الفيروسات جديد مع استثناءات

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com>) وسجل الدخول.

2. اختر **Endpoint security** \> **Antivirus** \> **+ Create Policy**.

3. حدد نظاما أساسيا (مثل **Windows 10 والإي وقت لاحق** أو **macOS** أو **Windows 10 وخادم Windows**).

4. بالنسبة **لملف التعريف**، حدد **برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات**، ثم اختر **"إنشاء**".

5. حدد اسما ووصفا لملف التعريف، ثم اختر **"التالي**".

6. في علامة التبويب **"إعدادات التكوين"** ، حدد استثناءات برنامج الحماية من الفيروسات، ثم اختر **"التالي**".

7. في علامة التبويب **"Scope tags** "، إذا كنت تستخدم علامات النطاق في مؤسستك، فحدد علامات النطاق للنهج الذي تقوم بإنشائه. (راجع [علامات النطاق](/mem/intune/fundamentals/scope-tags).)

8. في علامة التبويب **"الواجبات** "، حدد المستخدمين والمجموعات التي يجب تطبيق نهجك عليها، ثم اختر **"التالي**". (إذا كنت بحاجة إلى مساعدة في التعيينات، فراجع [تعيين ملفات تعريف المستخدمين والجهاز في Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

9. في علامة التبويب **"مراجعة + إنشاء** "، راجع الإعدادات، ثم اختر **"إنشاء**".

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>مؤشرات Microsoft Defender لنقطة النهاية

تمكن [المؤشرات](/microsoft-365/security/defender-endpoint/manage-indicators) (وتحديدا مؤشرات التسوية أو IoCs) فريق عمليات الأمان من تحديد الكشف عن الكيانات ومنعها واستبعادها. على سبيل المثال، يمكنك تحديد ملفات معينة ليتم حذفها من عمليات الفحص وإجراءات المعالجة في Microsoft Defender لنقطة النهاية. أو، يمكن استخدام المؤشرات لإنشاء تنبيهات لبعض الملفات أو عناوين IP أو عناوين URL.

لتحديد الكيانات كاستثناءات Microsoft Defender لنقطة النهاية، قم بإنشاء مؤشرات "السماح" لتلك الكيانات. تنطبق مؤشرات "السماح" هذه في Microsoft Defender لنقطة النهاية على [الحماية من الجيل التالي](microsoft-defender-antivirus-in-windows-10.md)[، الكشف عن تهديدات نقاط النهاية والرد عليها](overview-endpoint-detection-response.md)، [والتحقيق التلقائي & المعالجة](/microsoft-365/security/defender-endpoint/automated-investigations).

يمكن إنشاء مؤشرات "السماح" من أجل:

- [الملفات](#indicators-for-files)
- [عناوين IP وعناوين URL والمجالات](#indicators-for-ip-addresses-urls-or-domains)
- [شهادات التطبيق](#indicators-for-application-certificates)

:::image type="content" source="images/false-positives-indicators.png" alt-text="أنواع المؤشرات" lightbox="images/false-positives-indicators.png":::

#### <a name="indicators-for-files"></a>مؤشرات الملفات

عند [إنشاء مؤشر "السماح" لملف، مثل ملف قابل للتنفيذ](/microsoft-365/security/defender-endpoint/indicator-file)، يساعد على منع حظر الملفات التي تستخدمها مؤسستك. يمكن أن تتضمن الملفات الملفات القابلة للتنفيذ المحمولة (PE)، مثل `.exe` والملفات `.dll` .

قبل إنشاء مؤشرات للملفات، تأكد من استيفاء المتطلبات التالية:

- تم تكوين برنامج الحماية من الفيروسات من Microsoft Defender مع تمكين الحماية المستندة إلى السحابة (راجع [إدارة الحماية المستندة إلى السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- إصدار عميل مكافحة البرامج الضارة هو 4.18.1901.x أو أحدث
- يتم تشغيل الأجهزة Windows 10 أو الإصدار 1703 أو الإصدارات الأحدث أو Windows 11؛ Windows Server 2016 أو Windows Server 2019 أو Windows Server 2022
- [تم تشغيل ميزة الحظر أو السماح](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>مؤشرات لعناوين IP أو عناوين URL أو المجالات

عند [إنشاء مؤشر "السماح" لعنوان IP أو URL أو المجال](/microsoft-365/security/defender-endpoint/indicator-ip-domain)، فإنه يساعد على منع حظر المواقع أو عناوين IP التي تستخدمها مؤسستك.

قبل إنشاء مؤشرات لعناوين IP أو عناوين URL أو المجالات، تأكد من استيفاء المتطلبات التالية:

- يتم تمكين حماية الشبكة في Defender لنقطة النهاية في وضع الحظر (راجع [تمكين حماية الشبكة](/microsoft-365/security/defender-endpoint/enable-network-protection))
- إصدار عميل مكافحة البرامج الضارة هو 4.18.1906.x أو أحدث
- يتم تشغيل الأجهزة Windows 10 أو الإصدار 1709 أو الإصدارات الأحدث أو Windows 11

يتم تشغيل مؤشرات الشبكة المخصصة في [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). لمعرفة المزيد، راجع [الميزات المتقدمة](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>مؤشرات شهادات التطبيق

عند [إنشاء مؤشر "السماح" لشهادة تطبيق](/microsoft-365/security/defender-endpoint/indicator-certificates)، فإنه يساعد على منع حظر التطبيقات، مثل التطبيقات المطورة داخليا، التي تستخدمها مؤسستك. `.CER` أو `.PEM` ملحقات الملفات معتمدة.

قبل إنشاء مؤشرات لشهادات التطبيق، تأكد من استيفاء المتطلبات التالية:

- تم تكوين برنامج الحماية من الفيروسات من Microsoft Defender مع تمكين الحماية المستندة إلى السحابة (راجع [إدارة الحماية المستندة إلى السحابة](deploy-manage-report-microsoft-defender-antivirus.md)
- إصدار عميل مكافحة البرامج الضارة هو 4.18.1901.x أو أحدث
- يتم تشغيل الأجهزة Windows 10 أو الإصدار 1703 أو الإصدارات الأحدث أو Windows 11؛ Windows Server 2016 أو Windows Server 2019 أو Windows Server 2022
- تعريفات الحماية من الفيروسات والتهديدات محدثة

> [!TIP]
> عند إنشاء مؤشرات، يمكنك تعريفها واحدا تلو الآخر، أو استيراد عناصر متعددة في وقت واحد. ضع في اعتبارك أن هناك حدا يبلغ 15000 مؤشر لمستأجر واحد. وقد تحتاج إلى جمع تفاصيل معينة أولا، مثل معلومات تجزئة الملف. تأكد من مراجعة المتطلبات الأساسية قبل [إنشاء المؤشرات](manage-indicators.md).

## <a name="part-4-submit-a-file-for-analysis"></a>الجزء 4: إرسال ملف للتحليل

يمكنك إرسال كيانات، مثل الملفات وعمليات الكشف بدون ملفات، إلى Microsoft للتحليل. يحلل باحثو الأمان في Microsoft جميع عمليات الإرسال، وتساعد نتائجهم في إعلام Microsoft Defender لنقطة النهاية قدرات الحماية من التهديدات. عند تسجيل الدخول إلى موقع الإرسال، يمكنك تعقب عمليات الإرسال.

### <a name="submit-a-file-for-analysis"></a>إرسال ملف للتحليل

إذا كان لديك ملف تم اكتشافه بشكل خاطئ على أنه ضار أو فائت، فاتبع هذه الخطوات لإرسال الملف للتحليل.

1. راجع الإرشادات هنا: [إرسال الملفات للتحليل](/windows/security/threat-protection/intelligence/submission-guide).

2. تفضل بزيارة [موقع إرسال التحليل الذكي لمخاطر الأمان من Microsoft](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)وأرسل ملفك).

### <a name="submit-a-fileless-detection-for-analysis"></a>إرسال الكشف بدون ملف للتحليل

إذا تم الكشف عن شيء ما على أنه برامج ضارة استنادا إلى السلوك، ولم يكن لديك ملف، يمكنك إرسال `Mpsupport.cab` الملف للتحليل. يمكنك الحصول على ملف *.cab* باستخدام أداة الأداة المساعدة Command-Line للحماية من البرامج الضارة من Microsoft (MPCmdRun.exe) على Windows 10 أو Windows 11.

1. انتقل إلى ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`، ثم قم بتشغيله `MpCmdRun.exe` كمسؤول.

2. اكتب `mpcmdrun.exe -GetFiles`، ثم اضغط على **مفتاح الإدخال Enter**.

   يتم إنشاء ملف .cab يحتوي على سجلات تشخيص مختلفة. يتم تحديد موقع الملف في إخراج موجه الأوامر. بشكل افتراضي، يكون الموقع `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

3. راجع الإرشادات هنا: [إرسال الملفات للتحليل](/windows/security/threat-protection/intelligence/submission-guide).

4. تفضل بزيارة [موقع إرسال التحليل الذكي لمخاطر الأمان من Microsoft](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)وأرسل ملفات .cab.

### <a name="what-happens-after-a-file-is-submitted"></a>ماذا يحدث بعد إرسال ملف؟

يتم فحص عمليات الإرسال الخاصة بك على الفور بواسطة أنظمتنا لمنحك أحدث قرار حتى قبل أن يبدأ المحلل في معالجة حالتك. من المحتمل أن يكون قد تم بالفعل إرسال ملف ومعالجتها من قبل محلل. وفي هذه الحالات، يتم اتخاذ قرار بسرعة.

بالنسبة إلى عمليات الإرسال التي لم تتم معالجتها بالفعل، يتم ترتيب أولوياتها للتحليل كما يلي:

- يتم إعطاء أولوية أعلى للملفات الشائعة التي يحتمل أن تؤثر على أعداد كبيرة من أجهزة الكمبيوتر.
- يتم إعطاء العملاء المصادق عليهم، وخاصة عملاء المؤسسات الذين يستخدمون [معرفات ضمان البرامج (SAIDs)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) الصالحة، أولوية أعلى.
- يتم إعطاء عمليات الإرسال التي تم وضع علامة عليها على أنها ذات أولوية عالية من قبل أصحاب SAID اهتماما فوريا.

للتحقق من وجود تحديثات تتعلق بإرسالك، سجل الدخول إلى [موقع إرسال التحليل الذكي لمخاطر الأمان من Microsoft](https://www.microsoft.com/wdsi/filesubmission).

> [!TIP]
> لمعرفة المزيد، راجع ["إرسال الملفات" للتحليل](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>الجزء 5: مراجعة إعدادات الحماية من التهديدات وضبطها

يوفر Microsoft Defender لنقطة النهاية مجموعة واسعة من الخيارات، بما في ذلك القدرة على ضبط الإعدادات لمختلف الميزات والقدرات. إذا كنت تحصل على العديد من الإيجابيات الخاطئة، فتأكد من مراجعة إعدادات الحماية من التهديدات في مؤسستك. قد تحتاج إلى إجراء بعض التعديلات على:

- [الحماية المقدمة من السحابة](#cloud-delivered-protection)
- [المعالجة للتطبيقات التي يحتمل أن تكون غير مرغوب فيها](#remediation-for-potentially-unwanted-applications)
- [التحقيق التلقائي والمعالجة](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>الحماية المقدمة من السحابة

تحقق من مستوى الحماية المقدمة من السحابة للحصول على برنامج الحماية من الفيروسات من Microsoft Defender. بشكل افتراضي، يتم تعيين الحماية المقدمة من السحابة إلى **غير مكونة**، والتي تتوافق مع مستوى عادي من الحماية لمعظم المؤسسات. إذا تم تعيين الحماية التي توفرها السحابة إلى تسامح **عال** أو **مرتفع أو** **صفري**، فقد تواجه عددا أعلى من الإيجابيات الخاطئة.

> [!TIP]
> لمعرفة المزيد حول تكوين الحماية التي توفرها السحابة، راجع [تحديد مستوى الحماية المقدمة من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

نوصي باستخدام [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) لتحرير إعدادات الحماية التي توفرها السحابة أو تعيينها؛ ومع ذلك، يمكنك استخدام أساليب أخرى، مثل [نهج المجموعة](/azure/active-directory-domain-services/manage-group-policy) (راجع [إدارة Microsoft Defender لنقطة النهاية](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>استخدام إدارة نقاط النهاية من Microsoft لمراجعة إعدادات الحماية المقدمة من السحابة وتحريرها (للنهج الحالية)

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com>) وسجل الدخول.

2. اختر برنامج **الحماية من الفيروسات** **لأمان** \> نقطة النهاية ثم حدد نهجا موجودا. (إذا لم يكن لديك نهج موجود، أو إذا كنت تريد إنشاء نهج جديد، فانتقل إلى [الإجراء التالي](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy)).

3. ضمن **"إدارة**"، حدد **"خصائص**". بعد ذلك، إلى جانب **إعدادات التكوين**، اختر **"تحرير**".

4. قم بتوسيع **حماية السحابة**، ومراجعة الإعداد الحالي في صف **مستوى الحماية المقدمة من السحابة** . نوصي بتعيين الحماية المقدمة من السحابة إلى **غير مكونة**، ما يوفر حماية قوية مع تقليل فرص الحصول على إيجابيات خاطئة.

5. اختر **"مراجعة + حفظ**"، ثم **"حفظ**".

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>استخدام إدارة نقاط النهاية من Microsoft لتعيين إعدادات الحماية المقدمة من السحابة (لنهج جديد)

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com>) وسجل الدخول.

2. اختر **Endpoint security** \> **Antivirus** \> **+ Create policy**.

3. بالنسبة للنظام **الأساسي**، حدد خيارا، ثم **لملف التعريف**، حدد **برنامج الحماية من الفيروسات** أو **برنامج الحماية من الفيروسات من Microsoft Defender** (يعتمد الخيار المحدد على ما حددته للنظام **الأساسي**.) ثم اختر **"إنشاء**".

4. في علامة التبويب **"Basics** "، حدد اسما ووصفا للنهج. ثم اختر **"التالي**".

5. في علامة التبويب **"إعدادات التكوين"** ، قم بتوسيع **حماية السحابة**، وحدد الإعدادات التالية:

   - قم **بتعيين تشغيل الحماية المقدمة من السحابة** إلى **"نعم**".
   - تعيين **مستوى الحماية المقدمة من السحابة** إلى **غير مكون**. (يوفر هذا المستوى مستوى قويا من الحماية بشكل افتراضي مع تقليل فرص الحصول على إيجابيات خاطئة.)

6. في علامة التبويب **"Scope tags** "، إذا كنت تستخدم علامات النطاق في مؤسستك، فحدد علامات النطاق للنهج. (راجع [علامات النطاق](/mem/intune/fundamentals/scope-tags).)

7. في علامة التبويب **"الواجبات** "، حدد المستخدمين والمجموعات التي يجب تطبيق نهجك عليها، ثم اختر **"التالي**". (إذا كنت بحاجة إلى مساعدة في التعيينات، فراجع [تعيين ملفات تعريف المستخدمين والجهاز في Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. في علامة التبويب **"مراجعة + إنشاء** "، راجع الإعدادات، ثم اختر **"إنشاء**".

### <a name="remediation-for-potentially-unwanted-applications"></a>المعالجة للتطبيقات التي يحتمل أن تكون غير مرغوب فيها

التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA) هي فئة من البرامج التي يمكن أن تتسبب في تشغيل الأجهزة ببطء أو عرض إعلانات غير متوقعة أو تثبيت برامج أخرى قد تكون غير متوقعة أو غير مرغوب فيها. تتضمن أمثلة PUA البرامج الإعلانية وبرامج التجميع وبرامج التهرب التي تتصرف بشكل مختلف مع منتجات الأمان. على الرغم من أن PUA لا يعتبر برامج ضارة، فإن بعض أنواع البرامج تعتمد على سلوكها وسمعتها.

> [!TIP]
> لمعرفة المزيد حول PUA، راجع [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

استنادا إلى التطبيقات التي تستخدمها مؤسستك، قد تحصل على إيجابيات خاطئة نتيجة لإعدادات حماية PUA. إذا لزم الأمر، ففكر في تشغيل حماية PUA في وضع التدقيق لفترة من الوقت، أو طبق حماية PUA على مجموعة فرعية من الأجهزة في مؤسستك. يمكن تكوين حماية PUA للمستعرض Microsoft Edge ول برنامج الحماية من الفيروسات من Microsoft Defender.

نوصي باستخدام [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) لتحرير إعدادات حماية PUA أو تعيينها؛ ومع ذلك، يمكنك استخدام أساليب أخرى، مثل [نهج المجموعة](/azure/active-directory-domain-services/manage-group-policy) (راجع [إدارة Microsoft Defender لنقطة النهاية](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>استخدام إدارة نقاط النهاية من Microsoft لتحرير حماية PUA (لملفات تعريف التكوين الموجودة)

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com>) وسجل الدخول.

2. اختر **ملفات تعريف تكوين** **الأجهزة**\>، ثم حدد نهجا موجودا. (إذا لم يكن لديك نهج موجود، أو إذا كنت تريد إنشاء نهج جديد، فانتقل إلى [الإجراء التالي](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile).)

3. ضمن **"إدارة**"، اختر **"خصائص**"، ثم إلى جانب **إعدادات التكوين**، اختر **"تحرير**".

4. في علامة التبويب **"إعدادات التكوين"**، قم بالتمرير لأسفل ثم قم بتوسيع **برنامج الحماية من الفيروسات من Microsoft Defender**.

5. تعيين **الكشف عن التطبيقات غير المرغوب فيها** إلى **التدقيق**. (يمكنك إيقاف تشغيله، ولكن باستخدام وضع التدقيق، ستتمكن من رؤية عمليات الكشف.)

6. اختر **"مراجعة + حفظ**"، ثم اختر **"حفظ**".

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>استخدام إدارة نقاط النهاية من Microsoft لتعيين حماية PUA (لملف تعريف تكوين جديد)

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com>) وسجل الدخول.

2. اختر **ملفات تعريف** \> تكوين **الأجهزة** \> **+ إنشاء ملف تعريف**.

3. بالنسبة إلى **النظام الأساسي**، اختر **Windows 10 والإصدارات الأحدث**، وبالنسبة إلى **ملف التعريف**، حدد **قيود الجهاز**.

4. في علامة التبويب **"Basics** "، حدد اسما ووصفا للنهج الخاص بك. ثم اختر **"التالي**".

5. في علامة التبويب **"إعدادات التكوين"**، قم بالتمرير لأسفل ثم قم بتوسيع **برنامج الحماية من الفيروسات من Microsoft Defender**.

6. قم بتعيين **"الكشف عن التطبيقات غير المرغوب فيها** " إلى **"التدقيق**"، ثم اختر **"التالي**". (يمكنك إيقاف تشغيل حماية PUA، ولكن باستخدام وضع التدقيق، ستتمكن من رؤية عمليات الكشف.)

7. في علامة التبويب **"الواجبات** "، حدد المستخدمين والمجموعات التي يجب تطبيق نهجك عليها، ثم اختر **"التالي**". (إذا كنت بحاجة إلى مساعدة في التعيينات، فراجع [تعيين ملفات تعريف المستخدمين والجهاز في Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. في علامة التبويب " **قواعد التطبيق"** ، حدد إصدارات نظام التشغيل أو الإصدارات لتضمينها أو استبعادها من النهج. على سبيل المثال، يمكنك تعيين النهج الذي سيتم تطبيقه على جميع الأجهزة إصدارات معينة من Windows 10. ثم اختر **"التالي**".

9. في علامة التبويب **"مراجعة + إنشاء** "، راجع الإعدادات، ثم اختر **"إنشاء**".

### <a name="automated-investigation-and-remediation"></a>التحقيق التلقائي والمعالجة

تم تصميم قدرات [التحقيق والمعالجة التلقائية](automated-investigations.md) (AIR) لفحص التنبيهات واتخاذ إجراءات فورية لحل الخروقات. مع تشغيل التنبيهات، وإجراء تحقيق تلقائي، يتم إصدار حكم لكل قطعة من الأدلة التي يتم التحقيق فيها. يمكن أن تكون الأحكام *ضارة* أو *مريبة* أو *لم يتم العثور على أي تهديدات*.

اعتمادا على [مستوى التشغيل التلقائي](/microsoft-365/security/defender-endpoint/automation-levels) المعين لمؤسستك وإعدادات الأمان الأخرى، يتم اتخاذ إجراءات المعالجة على البيانات الاصطناعية التي تعتبر *ضارة* أو *مريبة*. في بعض الحالات، تحدث إجراءات المعالجة تلقائيا؛ في حالات أخرى، يتم اتخاذ إجراءات المعالجة يدويا أو فقط عند موافقة فريق عمليات الأمان.

- [تعرف على المزيد حول مستويات التشغيل التلقائي](/microsoft-365/security/defender-endpoint/automation-levels)؛ وبعد ذلك
- [تكوين قدرات AIR في Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation).

> [!IMPORTANT]
> نوصي باستخدام *التشغيل التلقائي الكامل* للتحقيق التلقائي والمعالجة. لا توقف تشغيل هذه القدرات بسبب إيجابية خاطئة. بدلا من ذلك، استخدم [مؤشرات "السماح" لتعريف الاستثناءات](#indicators-for-microsoft-defender-for-endpoint)، واحتفظ بتعيين التحقيق والمعالجة التلقائيين لاتخاذ الإجراءات المناسبة تلقائيا. يساعد اتباع [هذه الإرشادات](automation-levels.md#levels-of-automation) على تقليل عدد التنبيهات التي يجب على فريق عمليات الأمان التعامل معها.

## <a name="still-need-help"></a>هل ما زلت بحاجة إلى المساعدة؟

إذا كنت قد عملت على جميع الخطوات الواردة في هذه المقالة وكنت لا تزال بحاجة إلى المساعدة، فاتصل بالدعم التقني.

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> وسجل الدخول.

2. في الزاوية العلوية اليسرى، حدد علامة الاستفهام (**؟**)، ثم حدد **دعم Microsoft**.

3. في نافذة **مساعد الدعم** ، صف مشكلتك، ثم أرسل رسالتك. من هناك، يمكنك فتح طلب خدمة.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md) 

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft Defender لنقطة النهاية](manage-mde-post-migration.md)

[نظرة عامة على مدخل Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
