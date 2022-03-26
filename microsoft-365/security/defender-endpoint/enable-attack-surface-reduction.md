---
title: تمكين قواعد الحد من سطح الهجوم
description: تمكين قواعد تقليل مساحة الهجوم (ASR) لحماية أجهزتك من الهجمات التي تستخدم وحدات الماكرو، والنصية، وتقنيات بالحقن الشائعة.
keywords: الحد من سطح الهجوم، الوركين، نظام منع اقتحام المضيف، قواعد الحماية، مكافحة استغلال، مكافحة استغلال، استغلال، منع الإصابة، تمكين، تشغيل
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.date: 1/18/2022
ms.openlocfilehash: 9f5d721148bdbd70347868d8e237a8454b33c346
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63573317"
---
# <a name="enable-attack-surface-reduction-rules"></a>تمكين قواعد الحد من سطح الهجوم

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[تساعد قواعد الحد من](attack-surface-reduction.md) الهجمات (قواعد ASR) على منع الإجراءات التي غالبا ما تسيء البرامج الضارة إلى الأجهزة والشبكات.

## <a name="requirements"></a>المتطلبات

ميزات الحد من سطح الهجوم Windows الإصدارات

يمكنك تعيين قواعد تقليل مساحة الهجوم للأجهزة التي تقوم بتشغيل أي من الإصدارات والإصدارات التالية من Windows:

- Windows 10 Pro الإصدار [1709](/windows/whats-new/whats-new-windows-10-version-1709) أو الإصدارات الأحدث
- Windows 10 Enterprise الإصدار [1709 أو](/windows/whats-new/whats-new-windows-10-version-1709) الإصدارات الأحدث
- Windows Server، [الإصدار 1803 (قناة نصف سنوية)](/windows-server/get-started/whats-new-in-windows-server-1803) أو إصدار أحدث
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- Windows Server 2022

لاستخدام مجموعة الميزات الكاملة لقواعد الحد من سطح الهجوم، ستحتاج إلى:

- برنامج الحماية من الفيروسات لـ Windows Defender ك AV أساسي (الحماية في الوقت الحقيقي في)
- [حماية التسليم السحابي](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) في (تتطلب بعض القواعد ذلك)
- Windows 10 Enterprise E5 أو E3

على الرغم من أن قواعد تقليل مساحة الهجوم لا تتطلب ترخيص [Windows E5](/windows/deployment/deploy-enterprise-licenses)، مع ترخيص Windows E5، إلا أنك ستحصل على قدرات إدارة متقدمة بما في ذلك المراقبة والتحليلات ومسير العمل المتوفرة في Defender for Endpoint، بالإضافة إلى قدرات إعداد التقارير والتكوين <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">في مدخل Microsoft 365 Defender</a>. لا تتوفر هذه الإمكانات المتقدمة مع ترخيص E3، ولكن لا يزال بإمكانك استخدام "عارض الأحداث" لمراجعة أحداث قواعد الحد من سطح الهجوم.

تحتوي كل قاعدة ASR على أحد الإعدادات الأربعة:

- **غير مكون** |  **معطل**: تعطيل قاعدة ASR
- **الحظر**: تمكين قاعدة ASR
- **التدقيق**: تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها
- **تحذير**: تمكين قاعدة ASR مع السماح للمستخدم بتجاوز الحظر

> [!IMPORTANT]
> حاليا، وضع التحذير غير معتمد في ثلاث قواعد ASR عند تكوين قواعد ASR في إدارة نقاط النهاية من Microsoft (MEM). لمعرفة المزيد، راجع [الحالات التي يكون فيها وضع التحذير غير معتمد](attack-surface-reduction.md#cases-where-warn-mode-is-not-supported).

نوصي باستخدام قواعد ASR مع ترخيص Windows E5 (أو ترخيص SKU مماثل) للاستفادة من قدرات التقارير والمراقبة المتقدمة المتوفرة في [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) (Defender for Endpoint). ومع ذلك، إذا كان لديك ترخيص آخر، مثل Windows Professional أو Windows E3 لا يتضمن قدرات متقدمة على المراقبة وإعداد التقارير، يمكنك تطوير أدوات المراقبة وإعداد التقارير الخاصة بك أعلى الأحداث التي يتم إنشاؤها في كل نقطة نهاية عند تشغيل قواعد ASR (على سبيل المثال، إعادة توجيه الحدث).

> [!TIP]
> لمعرفة المزيد حول Windows، راجع Windows 10 الترخيص واحصل على دليل [](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) الترخيص [Windows 10.](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf)

يمكنك تمكين قواعد الحد من سطح الهجوم باستخدام أي من هذه الأساليب:

- [Microsoft Intune](#intune)
- [إدارة أجهزة المحمول (MDM)](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [نهج المجموعة](#group-policy)
- [PowerShell](#powershell)

يوصى بإدارة مستوى المؤسسة مثل Intune أو إدارة نقاط النهاية من Microsoft. ست الكتابة فوق أي نهج مجموعة متضاربة أو إعدادات PowerShell عند بدء التشغيل على مستوى المؤسسة.

## <a name="exclude-files-and-folders-from-asr-rules"></a>استبعاد الملفات والمجلدات من قواعد ASR

يمكنك استثناء الملفات والمجلدات التي لا يتم تقييمها بواسطة معظم قواعد تقليل مساحة الهجوم. وهذا يعني أنه حتى إذا كانت قاعدة ASR تحدد أن الملف أو المجلد يحتوي على سلوك ضار، فإنه لن يمنع تشغيل الملف. من المحتمل أن يسمح هذا بتشغيل الملفات غير الآمنة وإصابتها.

يمكنك أيضا استثناء قواعد ASR من المشغل استنادا إلى شهادات وتقشيزات الملفات من خلال السماح لمؤشرات محددة لملف وشهادة Defender لنقطة النهاية. (راجع [إدارة المؤشرات](manage-indicators.md).)

> [!IMPORTANT]
> قد يقلل استبعاد الملفات أو المجلدات بشدة من الحماية التي توفرها قواعد ASR. سيتم السماح بتشغيل الملفات المستبعدة، ولن يتم تسجيل أي تقرير أو حدث.
> إذا كانت قواعد ASR تكتشف الملفات التي تعتقد أنه لا يجب الكشف عنها، يجب استخدام وضع التدقيق أولا [لاختبار القاعدة](evaluate-attack-surface-reduction.md).

يمكنك تحديد الملفات أو المجلدات الفردية (باستخدام مسارات المجلدات أو أسماء الموارد المؤهلة بالكامل)، ولكن لا يمكنك تحديد القواعد التي تنطبق عليها الاستثناءات. يتم تطبيق الاستثناء فقط عند بدء تشغيل التطبيق أو الخدمة المستبعدة. على سبيل المثال، إذا أضفت استثناء لخدمة تحديث قيد التشغيل بالفعل، فستمر خدمة التحديث في تشغيل الأحداث حتى يتم إيقاف الخدمة وإعادة تشغيلها.

تدعم قواعد ASR متغيرات البيئة و أحرف البدل. للحصول على معلومات حول استخدام أحرف البدل، راجع استخدام أحرف البدل في اسم الملف ومسار [المجلد أو قوائم استثناءات الملحقات](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>تعارض النهج

1. إذا تم تطبيق نهج متضارب عبر MDM و GP، فإن الإعداد المطبق من MDM سيكون له الأسبقية.

2. تدعم قواعد تقليل مساحة الهجوم للأجهزة المدارة باستخدام MEM الآن سلوك دمج الإعدادات من نهج مختلفة، لإنشاء مجموعة كبيرة من النهج لكل جهاز. يتم دمج الإعدادات غير المتضاربة فقط، بينما لا تضاف الإعدادات المتضاربة إلى مجموعة القواعد فائقة التعارض. في السابق، إذا كان هناك سياساتان تتضمنان تعارضات لإعداد واحد، فقد تم وضع علامة على كل من المنهجين على أنهما في حالة تعارض، ولم يتم نشر أي إعدادات من أي ملف تعريف. سلوك دمج قاعدة الحد من سطح الهجوم كما يلي:
   - يتم تقييم قواعد تقليل مساحة الهجوم من ملفات التعريف التالية لكل جهاز تنطبق عليه القواعد:
     - يتم > نهج التكوين > ملف تعريف حماية نقطة النهاية > **الحماية من مخاطر الهجمات من Microsoft Defender** >  [تصغير Surface](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules).
     - نهج الحد من > **سطح** >  [الهجوميتثاق قواعد الحد من سطح النقاط](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - أمان نقطة النهاية > أساسيات الأمان > **أساسيات MICROSOFT Defender ATPتدريب** >  [قواعد الحد من Surface](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules).
   - الإعدادات إضافة أي تعارضات إلى مجموعة فائقة من النهج للجهاز.
   - عندما يكون هناك نهجان متضاربان أو أكثر، لا تضاف الإعدادات المتضاربة إلى النهج المدمج، بينما تضاف الإعدادات التي لا تتضارب إلى نهج مجموعة فائقة التي تنطبق على الجهاز.
   - يتم فقط منع تكوينات الإعدادات المتضاربة.

## <a name="configuration-methods"></a>أساليب التكوين

يوفر هذا القسم تفاصيل التكوين لأساليب التكوين التالية:

- [Intune](#intune)
- [MEM](#mem)
- [MDM](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [نهج المجموعة](#group-policy)
- [PowerShell](#powershell)

تتضمن الإجراءات التالية لتمكين قواعد ASR إرشادات حول كيفية استبعاد الملفات والمجلدات.

### <a name="intune"></a>Intune

#### <a name="device-configuration-profiles"></a>ملفات تعريف تكوين الجهاز

1. حدد **ملفات تعريف تكوين** \> **الجهاز**. اختر ملف تعريف حماية نقطة نهاية موجود أو قم بإنشاء ملف تعريف جديد. لإنشاء ملف تعريف جديد، حدد **إنشاء ملف تعريف** وأدخل معلومات لملف التعريف هذا. بالنسبة **لنوع ملف التعريف**، حدد **حماية نقطة النهاية**. إذا اخترت ملف تعريف موجود، فحدد **خصائص** **ثم حدد الإعدادات**.

2. في جزء **حماية نقطة** النهاية، حدد Windows **Defender Exploit Guard**، ثم حدد **تقليل مساحة الهجوم**. حدد الإعداد المطلوب لكل قاعدة ASR.

3. ضمن **استثناءات تقليل مساحة الهجوم**، أدخل الملفات والمجلدات الفردية. يمكنك أيضا تحديد **استيراد** لاستيراد ملف CSV يحتوي على ملفات ومجلدات لاستثنائها من قواعد ASR. يجب تنسيق كل سطر في ملف CSV كما يلي:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. حدد **موافق** على ثلاثة من اقالب التكوين. ثم حدد **إنشاء** إذا كنت تقوم بإنشاء ملف حماية نقطة نهاية جديد أو **حفظ** إذا كنت تقوم بتحرير ملف موجود.

#### <a name="endpoint-security-policy"></a>نهج أمان نقطة النهاية**

1. حدد **الحد من سطح الهجوم الأمني** \> **لنقطة النهاية**. اختر قاعدة ASR موجودة أو أنشئ قاعدة جديدة. لإنشاء نهج جديد، حدد **إنشاء نهج** وأدخل معلومات لملف التعريف هذا. بالنسبة **لنوع ملف التعريف**، حدد **قواعد تقليل مساحة الهجوم**. إذا اخترت ملف تعريف موجود، فحدد **خصائص** **ثم حدد الإعدادات**.

2. في جزء **إعدادات** التكوين، حدد **تقليل** مساحة الهجوم، ثم حدد الإعداد المطلوب لكل قاعدة ASR.

3. ضمن **قائمة المجلدات** الإضافية التي يجب حمايتها، أدخل قائمة التطبيقات التي لديها حق الوصول إلى المجلدات المحمية واستبعاد الملفات والمسارات من قواعد الحد من سطح الهجوم، وأدخل الملفات والمجلدات الفردية. يمكنك أيضا تحديد **استيراد** لاستيراد ملف CSV يحتوي على ملفات ومجلدات لاستثنائها من قواعد ASR. يجب تنسيق كل سطر في ملف CSV كما يلي:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. حدد **التالي** في اقالب التكوين الثلاثة، ثم حدد  إنشاء إذا كنت تقوم بإنشاء نهج جديد أو حفظ إذا  كنت تقوم بتحرير نهج موجود.

### <a name="mem"></a>MEM

يمكنك استخدام إدارة نقاط النهاية من Microsoft OMA-URI (MEM) لتكوين قواعد ASR مخصصة. يستخدم الإجراء التالي القاعدة حظر [إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) للمثال.

1. افتح إدارة نقاط النهاية من Microsoft إدارة (MEM). في القائمة **الصفحة** الرئيسية، انقر فوق  **الأجهزة**، وحدد **ملفات تعريف التكوين**، ثم انقر **فوق إنشاء ملف تعريف**.

   > [!div class="mx-imgBorder"]
   > ![MEM إنشاء ملف تعريف.](images/mem01-create-profile.png)

2. في **إنشاء ملف تعريف**، في القائمتين المنسدتين التاليتين، حدد ما يلي:

   - في **النظام الأساسي**، حدد Windows 10 **واللاحقة**
   - في **نوع ملف التعريف**، حدد **قوالب**
   - إذا تم تعيين قواعد ASR بالفعل من خلال أمان نقطة النهاية **، ففي نوع** ملف التعريف، حدد الإعدادات **الكتالوج**.

   حدد **مخصص**، ثم حدد **إنشاء**.

   > [!div class="mx-imgBorder"]
   > ![سمات ملف تعريف قاعدة MEM.](images/mem02-profile-attributes.png)

3. يتم فتح أداة القالب المخصص إلى الخطوة **1 أساسيات**. في **1 أساسيات**، في **الاسم**، اكتب اسما للقالب، وفي الوصف يمكنك  كتابة وصف (اختياري).

   > [!div class="mx-imgBorder"]
   > ![سمات MEM الأساسية.](images/mem03-1-basics.png)

4. انقر فوق **التالي**. يتم **فتح إعدادات تكوين الخطوة 2** . بالنسبة إلى OMA-URI الإعدادات، انقر فوق **إضافة**. يظهر خياران الآن: **إضافة** **وتصدير.**

   > [!div class="mx-imgBorder"]
   > ![إعدادات تكوين MEM.](images/mem04-2-configuration-settings.png)

5. انقر **فوق إضافة** مرة أخرى. يتم **فتح إضافة صف OMA-URI الإعدادات**. في **إضافة صف**، قم بما يلي:

   - في **الاسم**، اكتب اسما للقاعدة.
   - في **الوصف**، اكتب وصفا مختصرا.
   - في **OMA-URI**، اكتب ارتباط OMA-URI المحدد للقاعدة التي تقوم بإضافتها أو اللصق. راجع قسم MDM في هذه المقالة ل OMA-URI لاستخدامه لقاعدة المثال هذه. للحصول على قاعدة تقليل مساحة الهجوم GUIDS، راجع [أوصاف](attack-surface-reduction-rules-reference.md#per-rule-descriptions) كل قاعدة في الموضوع: قواعد الحد من سطح الهجوم.
   - في **نوع البيانات،** حدد **سلسلة**.
   - في **القيمة**، اكتب قيمة GUID \= والتوقيع وقيمة الولاية بدون مسافات (_GUID=StateValue) أو اللصق بها_. المكان:

     - 0 : تعطيل (تعطيل قاعدة ASR)
     - 1 : الحظر (تمكين قاعدة ASR)
     - 2 : التدقيق (تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها)
     - 6 : التحذير (تمكين قاعدة ASR مع السماح للمستخدم بتجاوز الحظر)

   > [!div class="mx-imgBorder"]
   > ![تكوين MEM OMA URI.](images/mem05-add-row-oma-uri.png)

6. حدد **حفظ**. **يتم إغلاق** إضافة صف. في **مخصص**، حدد **التالي**. في الخطوة **3 علامات النطاق**، تكون علامات النطاق اختيارية. القيام بوا واحد من الخطوات التالية:

   - حدد **تحديد علامات النطاق**، وحدد علامة النطاق (اختياري)، ثم حدد **التالي**.
   - أو حدد **التالي**

7. في الخطوة **4 التعيينات****، في المجموعات** المضمنة، للمجموعات التي تريد تطبيق هذه القاعدة عليها، حدد من الخيارات التالية:

   - **إضافة مجموعات**
   - **إضافة جميع المستخدمين**
   - **إضافة جميع الأجهزة**

   > [!div class="mx-imgBorder"]
   > ![تعيينات MEM.](images/mem06-4-assignments.png)

8. في **المجموعات المستبعدة**، حدد أي مجموعات تريد استبعادها من هذه القاعدة، ثم حدد **التالي**.

9. في الخطوة **5 قواعد إمكانية التطبيق** لإعدادات التالية، يمكنك القيام بما يلي:

   - في **القاعدة**، حدد إما **تعيين ملف تعريف إذا**، أو **عدم تعيين ملف تعريف إذا**
   - في **الخاصية**، حدد الخاصية التي تريد تطبيق هذه القاعدة عليها
   - في **القيمة**، أدخل نطاق القيمة أو القيمة المعمول بها

   > [!div class="mx-imgBorder"]
   > ![قواعد إمكانية تطبيق MEM.](images/mem07-5-applicability-rules.png)

10. حدد **التالي**. في الخطوة **6 مراجعة + إنشاء**، راجع الإعدادات والمعلومات التي حددتها وأدخلها، ثم حدد **إنشاء**.

    > [!div class="mx-imgBorder"]
    > ![مراجعة MEM وإنشاءه.](images/mem08-6-review-create.png)

    > [!NOTE]
    > القواعد نشطة وتحيا في غضون دقائق.

> [!NOTE]
> معالجة التعارضات:
>
> إذا قمت بتعيين اثنين من سياسات ASR مختلفة لجهاز، فإن الطريقة التي يتم بها التعامل مع التعارض هي القواعد التي تم تعيين حالات مختلفة لها، ولا توجد إدارة تعارضات في مكانها، والنتيجة هي خطأ.
>
> لن ينتج عن القواعد غير المتضاربة خطأ، وستطبق القاعدة بشكل صحيح. والنتيجة هي تطبيق القاعدة الأولى، ودمج القواعد اللاحقة غير المتضاربة في النهج.

### <a name="mdm"></a>MDM

استخدم [موفر خدمة تكوين ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) (CSP) لتمكين الوضع لكل قاعدة بشكل فردي.

فيما يلي نموذج للمرجع، باستخدام قيم GUID لمرجع قواعد [تقليل مساحة الهجوم](attack-surface-reduction-rules-reference.md).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

القيم التي يجب تمكينها (حظر) أو تعطيلها أو تحذيرها أو تمكينها في وضع التدقيق هي:

- 0 : تعطيل (تعطيل قاعدة ASR)
- 1 : الحظر (تمكين قاعدة ASR)
- 2 : التدقيق (تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها)
- 6 : التحذير (تمكين قاعدة ASR مع السماح للمستخدم بتجاوز الحظر). يتوفر وضع التحذير لمعظم قواعد ASR.

استخدم [موفر خدمة تكوين ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) (CSP) لإضافة استثناءات.

على سبيل المثال:

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> تأكد من إدخال قيم OMA-URI بدون مسافات.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. في Microsoft Endpoint Configuration Manager، انتقل إلى **الأصول والتوافق** \>  \> Endpoint Protection **Windows Defender Exploit Guard**.

2. حدد **الصفحة الرئيسية** \> **إنشاء نهج حماية استغلال**.

3. أدخل اسما ووصفا، وحدد **تقليل مساحة الهجوم**، وحدد **التالي**.

4. اختر القواعد التي ستحظر أو تدقق الإجراءات وحدد **التالي**.

5. راجع الإعدادات وحدد **التالي** لإنشاء النهج.

6. بعد إنشاء النهج، حدد **إغلاق**.

### <a name="group-policy"></a>نهج المجموعة

> [!WARNING]
> إذا كنت تدير أجهزة الكمبيوتر والأجهزة باستخدام Intune أو Configuration Manager أو أي نظام أساسي آخر للإدارة على مستوى المؤسسة، فإن برنامج الإدارة سي الكتابة فوق أي إعدادات تعارض في "نهج المجموعة" عند بدء التشغيل.

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](https://technet.microsoft.com/library/cc731212.aspx) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وحدد **تحرير**.

2. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة Windows **مكوناتها برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **الحماية من مخاطر الهجمات من Microsoft Defender** \> **الحد من سطح الهجوم**.

4. حدد **تكوين قواعد تقليل مساحة الهجوم** وحدد **تمكين**. يمكنك بعد ذلك تعيين الحالة الفردية لكل قاعدة في مقطع الخيارات. حدد **إظهار...** وأدخل "معرّف القاعدة" في عمود **"** اسم القيمة" و"الحالة التي اخترتها **" في عمود** "القيمة" كما يلي:

   - 0 : تعطيل (تعطيل قاعدة ASR)
   - 1 : الحظر (تمكين قاعدة ASR)
   - 2 : التدقيق (تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها)
   - 6 : التحذير (تمكين قاعدة ASR مع السماح للمستخدم بتجاوز الحظر)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="قواعد ASR في &quot;نهج المجموعة&quot;.":::

5. لاستبعاد الملفات والمجلدات من قواعد ASR، حدد الإعداد استبعاد  الملفات والمسارات من قواعد تقليل مساحة الهجوم، ثم قم بتعيين الخيار إلى **ممكن**. حدد **إظهار** وأدخل كل ملف أو مجلد في **العمود اسم** القيمة. أدخل **0** في عمود **القيمة** لكل عنصر.

   > [!WARNING]
   > لا تستخدم علامات الاقتباس لأنها غير معتمدة إما بالنسبة إلى عمود  اسم القيمة أو **عمود** القيمة.

### <a name="powershell"></a>PowerShell

> [!WARNING]
> إذا كنت تدير أجهزة الكمبيوتر والأجهزة باستخدام Intune أو Configuration Manager أو نظام أساسي آخر للإدارة على مستوى المؤسسة، فإن برنامج الإدارة سي الكتابة فوق أي إعدادات PowerShell متضاربة عند بدء التشغيل. للسماح للمستخدمين بتعريف القيمة باستخدام PowerShell، استخدم الخيار "معرف من قبل المستخدم" للقاعدة في النظام الأساسي للإدارة.
> يسمح "معرف من قبل المستخدم" لمستخدم مسؤول محلي بتكوين القاعدة.
> يظهر إعداد الخيار معرف من قبل المستخدم في الشكل التالي.

> [!div class="mx-imgBorder"]
> ![تمكين ASR "معرف من قبل المستخدم"](images/asr-user-defined.png)

1. اكتب **powershell** في قائمة البدء، وانقر بضغطة **Windows PowerShell وحدد** **تشغيل كمسؤول**.

2. اكتب أحد cmdlets التالية. (راجع مرجع [قواعد تقليل مساحة](attack-surface-reduction-rules-reference.md) الهجوم للحصول على مزيد من التفاصيل، مثل "المرجع").

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    لتمكين قواعد ASR في وضع التدقيق، استخدم cmdlet التالي:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    لتمكين قواعد ASR في وضع التحذير، استخدم cmdlet التالي:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Warn
    ```

    لتمكين ASR حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال، استخدم cmdlet التالي:

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    إيقاف تشغيل قواعد ASR، استخدم cmdlet التالي:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > يجب تحديد الحالة بشكل فردي لكل قاعدة، ولكن يمكنك دمج القواعد والولايات في قائمة مفصولة ب فاصلة.
    >
    > في المثال التالي، سيتم تمكين أول قاعدة، سيتم تعطيل القاعدة الثالثة، كما سيتم تمكين القاعدة الرابعة في وضع التدقيق:
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    يمكنك أيضا استخدام الفعل `Add-MpPreference` PowerShell لإضافة قواعد جديدة إلى القائمة الموجودة.

    > [!WARNING]
    > `Set-MpPreference` سيتم دائما الكتابة فوق مجموعة القواعد الموجودة. إذا كنت تريد الإضافة إلى المجموعة الموجودة، فاستخدم بدلا `Add-MpPreference` من ذلك.
    > يمكنك الحصول على قائمة بالقواعد و حالتها الحالية باستخدام `Get-MpPreference`.

3. لاستبعاد الملفات والمجلدات من قواعد ASR، استخدم cmdlet التالي:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    تابع الاستخدام `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` لإضافة المزيد من الملفات والمجلدات إلى القائمة.

    > [!IMPORTANT]
    > يتم `Add-MpPreference` استخدامها ل إلحاق التطبيقات بالقائمة أو إضافتها. سيكتم `Set-MpPreference` الكتابة فوق القائمة الموجودة باستخدام الأمر cmdlet.

## <a name="related-articles"></a>المقالات ذات الصلة

- [مرجع قواعد الحد من سطح الهجوم](attack-surface-reduction-rules-reference.md)
- [تقييم تقليل مساحة الهجوم](evaluate-attack-surface-reduction.md)
- [الأسئلة الشائعة حول الحد من سطح الهجوم](attack-surface-reduction.md)
