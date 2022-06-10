---
title: تمكين قواعد تقليل الأجزاء المعرضة للهجوم
description: تمكين قواعد تقليل الأجزاء المعرضة للهجوم (ASR) لحماية أجهزتك من الهجمات التي تستخدم وحدات الماكرو والبرامج النصية وتقنيات الإدخال الشائعة.
keywords: تقليل الأجزاء المعرضة للهجوم، والوركين، ونظام منع الاختراق للمضيف، وقواعد الحماية، ومكافحة الاستغلال، ومكافحة الاستغلال، والاستغلال، والوقاية من العدوى، وتمكين، وتشغيل
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
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.date: 1/18/2022
ms.openlocfilehash: 31af082f66836ecfbe6a7cd804fd3b7bba2ed4bd
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012373"
---
# <a name="enable-attack-surface-reduction-rules"></a>تمكين قواعد تقليل الأجزاء المعرضة للهجوم

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

تساعد [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md) (قواعد ASR) على منع الإجراءات التي غالبا ما تسيء البرامج الضارة إلى اختراق الأجهزة والشبكات.

## <a name="requirements"></a>الاحتياجات

ميزات تقليل الأجزاء المعرضة للهجوم عبر إصدارات Windows

يمكنك تعيين قواعد تقليل الأجزاء المعرضة للهجوم للأجهزة التي تقوم بتشغيل أي من الإصدارات والإصدارات التالية من Windows:

- [Windows 11 Pro](/windows/whats-new/windows-11-overview)
- [Windows 11 Enterprise](https://www.microsoft.com/microsoft-365/windows/windows-11-enterprise)
- Windows 10 Pro، [الإصدار 1709](/windows/whats-new/whats-new-windows-10-version-1709) أو الإصدارات الأحدث
- Windows 10 Enterprise، [الإصدار 1709](/windows/whats-new/whats-new-windows-10-version-1709) أو أحدث
- Windows Server أو [الإصدار 1803 (التحديث نصف السنوي)](/windows-server/get-started/whats-new-in-windows-server-1803) أو إصدار أحدث
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2022](/windows-server/get-started/whats-new-in-windows-server-2022)

لاستخدام مجموعة الميزات الكاملة لقواعد تقليل الأجزاء المعرضة للهجوم، تحتاج إلى:

- برنامج الحماية من الفيروسات لـ Windows Defender ك AV أساسي (تشغيل الحماية في الوقت الحقيقي)
- [Cloud-Delivery Protection](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) on (تتطلب بعض القواعد ذلك)
- ترخيص Windows 10 Enterprise E5 أو E3

على الرغم من أن قواعد تقليل الأجزاء المعرضة للهجوم لا تتطلب [ترخيص E5 Windows](/windows/deployment/deploy-enterprise-licenses)، مع ترخيص E5 Windows، إلا أنك تحصل على قدرات إدارة متقدمة بما في ذلك المراقبة والتحليلات وسير العمل المتوفرة في Defender لنقطة النهاية، بالإضافة إلى قدرات إعداد التقارير والتكوين في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>. لا تتوفر هذه القدرات المتقدمة مع ترخيص E3، ولكن لا يزال بإمكانك استخدام عارض الأحداث لمراجعة أحداث قاعدة تقليل الأجزاء المعرضة للهجوم.

تحتوي كل قاعدة ASR على أحد الإعدادات الأربعة:

- **لم يتم تكوينه** |  **معطل**: تعطيل قاعدة ASR
- **كتلة**: تمكين قاعدة ASR
- **التدقيق**: تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها
- **تحذير**: تمكين قاعدة ASR ولكن السماح للمستخدم النهائي بتجاوز الكتلة

نوصي باستخدام قواعد ASR مع ترخيص E5 Windows (أو SKU ترخيص مشابه) للاستفادة من قدرات المراقبة وإعداد التقارير المتقدمة المتوفرة في [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) (Defender لنقطة النهاية). ومع ذلك، إذا كان لديك ترخيص آخر، مثل Windows Professional أو Windows E3 لا يتضمن قدرات متقدمة للمراقبة وإعداد التقارير، يمكنك تطوير أدوات المراقبة وإعداد التقارير الخاصة بك أعلى الأحداث التي يتم إنشاؤها في كل نقطة نهاية عند تشغيل قواعد ASR (على سبيل المثال، إعادة توجيه الأحداث).

> [!TIP]
> لمعرفة المزيد حول الترخيص Windows، راجع [Windows 10 الترخيص](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) واحصل على [دليل الترخيص المجمع Windows 10](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf).

يمكنك تمكين قواعد تقليل الأجزاء المعرضة للهجوم باستخدام أي من هذه الأساليب:

- [Microsoft Intune](#intune)
- [إدارة الجهاز المحمول (MDM)](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [نهج المجموعة](#group-policy)
- [PowerShell](#powershell)

يوصى بإدارة على مستوى المؤسسة مثل Intune أو إدارة نقاط النهاية من Microsoft. ستؤدي الإدارة على مستوى المؤسسة إلى الكتابة فوق أي إعدادات نهج المجموعة أو PowerShell متضاربة عند بدء التشغيل.

## <a name="exclude-files-and-folders-from-asr-rules"></a>استبعاد الملفات والمجلدات من قواعد ASR

يمكنك استبعاد الملفات والمجلدات من تقييمها بواسطة معظم قواعد تقليل الأجزاء المعرضة للهجوم. وهذا يعني أنه حتى إذا حددت قاعدة ASR أن الملف أو المجلد يحتوي على سلوك ضار، فلن تمنع تشغيل الملف. قد يسمح هذا للملفات غير الآمنة بتشغيل أجهزتك وإصابتها.

يمكنك أيضا استبعاد قواعد ASR من التشغيل استنادا إلى تجزئة الشهادة والملفات عن طريق السماح بملف Defender المحدد لمؤشرات شهادة وملف نقطة النهاية. (راجع [إدارة المؤشرات](manage-indicators.md).)

> [!IMPORTANT]
> يمكن أن يؤدي استبعاد الملفات أو المجلدات إلى تقليل الحماية التي توفرها قواعد ASR بشكل كبير. سيتم السماح بتشغيل الملفات المستبعدة، ولن يتم تسجيل أي تقرير أو حدث.
> إذا كانت قواعد ASR تكشف عن الملفات التي تعتقد أنه لا ينبغي الكشف عنها، يجب [عليك استخدام وضع التدقيق أولا لاختبار القاعدة](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit).

يمكنك تحديد ملفات أو مجلدات فردية (باستخدام مسارات المجلدات أو أسماء الموارد المؤهلة بالكامل)، ولكن لا يمكنك تحديد القواعد التي تنطبق عليها الاستثناءات. يتم تطبيق الاستبعاد فقط عند بدء تشغيل التطبيق أو الخدمة المستبعدة. على سبيل المثال، إذا أضفت استثناء لخدمة تحديث قيد التشغيل بالفعل، فستستمر خدمة التحديث في تشغيل الأحداث حتى يتم إيقاف الخدمة وإعادة تشغيلها.

تدعم قواعد ASR متغيرات البيئة وأحرف البدل. للحصول على معلومات حول استخدام أحرف البدل، راجع [استخدام أحرف البدل في اسم الملف ومسار المجلد أو قوائم استثناء الملحق](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>تعارض النهج

1. إذا تم تطبيق نهج متضارب عبر MDM وGP، فإن الإعداد المطبق من MDM سيكون له الأسبقية.

2. تدعم قواعد تقليل الأجزاء المعرضة للهجوم للأجهزة المدارة بواسطة MEM الآن سلوك دمج الإعدادات من نهج مختلفة، لإنشاء مجموعة فائقة من النهج لكل جهاز. يتم دمج الإعدادات غير المتضاربة فقط، بينما لا تتم إضافة الإعدادات التي تتعارض إلى مجموعة القواعد الفائقة. في السابق، إذا تضمن نهجان تعارضات لإعداد واحد، تم وضع علامة على كلا النهجين على أنهما متضاربين، ولن يتم نشر أي إعدادات من ملف التعريف. سلوك دمج قاعدة تقليل الأجزاء المعرضة للهجوم كما يلي:
   - يتم تقييم قواعد تقليل الأجزاء المعرضة للهجوم من ملفات التعريف التالية لكل جهاز تنطبق عليه القواعد:
     - نهج تكوين الأجهزة > > ملف تعريف حماية نقطة النهاية > **تقليل سطح الحماية من مخاطر الهجمات من Microsoft Defender** >  [Attack](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules).
     - أمان نقطة النهاية > **قواعد** > [تقليل الأجزاء المعرضة للهجوم](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - أمان نقطة النهاية > أساسات الأمان >[قواعد تقليل الأجزاء المعرضة للهجوم](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules) **الأساس** >  ل Microsoft Defender ATP.
   - تتم إضافة الإعدادات التي لا تحتوي على تعارضات إلى مجموعة فائقة من النهج للجهاز.
   - عندما يكون لدى نهجين أو أكثر إعدادات متضاربة، لا تتم إضافة الإعدادات التعارضة إلى النهج المدمج، بينما تتم إضافة الإعدادات التي لا تتعارض إلى نهج المجموعة الفائقة التي تنطبق على جهاز.
   - يتم الاحتفاظ فقط بتكوينات الإعدادات المتضاربة مرة أخرى.

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

1. حدد **ملفات تعريف** **تكوين** \> الجهاز. اختر ملف تعريف حماية نقطة النهاية الموجود أو قم بإنشاء ملف تعريف جديد. لإنشاء ملف تعريف جديد، حدد **"إنشاء ملف تعريف** " وأدخل معلومات لملف التعريف هذا. بالنسبة **لنوع ملف التعريف**، حدد **حماية نقطة النهاية**. إذا اخترت ملف تعريف موجودا، فحدد **"خصائص**" ثم حدد **"الإعدادات**".

2. في جزء **حماية نقطة النهاية**، حدد **Windows Defender Exploit Guard**، ثم حدد **تقليل الأجزاء المعرضة للهجوم**. حدد الإعداد المطلوب لكل قاعدة ASR.

3. ضمن **استثناءات تقليل الأجزاء المعرضة للهجوم**، أدخل الملفات والمجلدات الفردية. يمكنك أيضا تحديد **"استيراد** " لاستيراد ملف CSV يحتوي على ملفات ومجلدات لاستبعادها من قواعد ASR. يجب تنسيق كل سطر في ملف CSV كما يلي:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. حدد **"موافق** " في أجزاء التكوين الثلاثة. ثم حدد **"إنشاء** " إذا كنت تقوم بإنشاء ملف حماية نقطة نهاية جديد أو **"حفظ** " إذا كنت تقوم بتحرير ملف موجود.

#### <a name="endpoint-security-policy"></a>نهج أمان نقطة النهاية

1. حدد **تقليل سطح هجوم** **أمان** \> نقطة النهاية. اختر قاعدة ASR موجودة أو قم بإنشاء قاعدة جديدة. لإنشاء نهج جديد، حدد **"إنشاء نهج** " وأدخل معلومات لملف التعريف هذا. بالنسبة **لنوع ملف التعريف**، حدد **قواعد تقليل الأجزاء المعرضة للهجوم**. إذا اخترت ملف تعريف موجودا، فحدد **"خصائص**" ثم حدد **"الإعدادات**".

2. في جزء **إعدادات التكوين** ، حدد **تقليل الأجزاء** المعرضة للهجوم ثم حدد الإعداد المطلوب لكل قاعدة ASR.

3. ضمن **قائمة المجلدات الإضافية التي يجب حمايتها**، **وقائمة التطبيقات التي لديها حق الوصول إلى المجلدات المحمية**، **واستبعاد الملفات والمسارات من قواعد تقليل الأجزاء المعرضة للهجوم**، أدخل الملفات والمجلدات الفردية. يمكنك أيضا تحديد **"استيراد** " لاستيراد ملف CSV يحتوي على ملفات ومجلدات لاستبعادها من قواعد ASR. يجب تنسيق كل سطر في ملف CSV كما يلي:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. حدد **"التالي** " في أجزاء التكوين الثلاثة، ثم حدد **"إنشاء** " إذا كنت تقوم بإنشاء نهج جديد أو **"حفظ** " إذا كنت تقوم بتحرير نهج موجود.

### <a name="mem"></a>MEM

يمكنك استخدام إدارة نقاط النهاية من Microsoft (MEM) OMA-URI لتكوين قواعد ASR المخصصة. يستخدم الإجراء التالي [إساءة استخدام القاعدة Block لبرامج التشغيل الموقعة المعرضة للخطر التي تم استغلالها](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) على سبيل المثال.

1. افتح مركز إدارة إدارة نقاط النهاية من Microsoft (MEM). في القائمة **"الشريط الرئيسي** "، انقر فوق  **"الأجهزة**"، وحدد **ملفات تعريف التكوين**، ثم انقر فوق **"إنشاء ملف تعريف**".

   > [!div class="mx-imgBorder"]
   >  :::image type="content" source="images/mem01-create-profile.png" alt-text="صفحة إنشاء ملف تعريف في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem01-create-profile.png":::

2. في **إنشاء ملف تعريف**، في القائمتين المنسدلتين التاليتين، حدد ما يلي:

   - في **النظام الأساسي**، حدد **Windows 10 والإي وقت لاحق**
   - في **نوع ملف التعريف**، حدد **"قوالب"**
   - إذا تم تعيين قواعد ASR بالفعل من خلال أمان نقطة النهاية، في **نوع ملف التعريف**، فحدد **الإعدادات Catalog**.

   حدد **"مخصص**"، ثم حدد **"إنشاء**".

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem02-profile-attributes.png" alt-text="سمات ملف تعريف القاعدة في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem02-profile-attributes.png":::

3. تفتح أداة القالب المخصص إلى أساسيات الخطوة **1**. في **1 Basics**، في **الاسم**، اكتب اسما للقالب، وفي **الوصف** يمكنك كتابة وصف (اختياري).

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem03-1-basics.png" alt-text="السمات الأساسية في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem03-1-basics.png":::

4. انقر فوق **التالي**. يتم فتح **إعدادات تكوين الخطوة 2** . للحصول على الإعدادات OMA-URI، انقر فوق **"إضافة**". يظهر الآن خياران: **إضافة** **وتصدير**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem04-2-configuration-settings.png" alt-text="إعدادات التكوين في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem04-2-configuration-settings.png":::

5. انقر فوق **"إضافة"** مرة أخرى. يتم فتح **الإعدادات Add Row OMA-URI**. في **"إضافة صف**"، قم بما يلي:

   - في **الاسم**، اكتب اسما للقاعدة.
   - في **الوصف**، اكتب وصفا موجزا.
   - في **OMA-URI**، اكتب ارتباط OMA-URI المحدد أو الصقه للقاعدة التي تقوم بإضافتها. راجع مقطع MDM في هذه المقالة لاستخدام OMA-URI لقاعدة المثال هذه. للحصول على GUID لقاعدة تقليل الأجزاء المعرضة للهجوم، راجع [أوصاف كل قاعدة](attack-surface-reduction-rules-reference.md#per-rule-descriptions) في الموضوع: قواعد تقليل الأجزاء المعرضة للهجوم.
   - في **نوع البيانات**، حدد **"سلسلة**".
   - في **القيمة**، اكتب قيمة \= GUID والعلامة وقيمة الحالة بدون مسافات (_GUID=StateValue) أو الصقها_. المكان:

     - 0 : تعطيل (تعطيل قاعدة ASR)
     - 1 : كتلة (تمكين قاعدة ASR)
     - 2 : التدقيق (تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها)
     - 6 : التحذير (تمكين قاعدة ASR ولكن السماح للمستخدم النهائي بتجاوز الكتلة)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem05-add-row-oma-uri.png" alt-text="تكوين URI OMA في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem05-add-row-oma-uri.png":::

6. حدد **حفظ**. **إضافة** إغلاق الصف. في **"مخصص**"، حدد **"التالي**". في **علامات نطاق الخطوة 3**، تكون علامات النطاق اختيارية. قم بأحد الإجراءات التالية:

   - حدد **"Select Scope tags"**، وحدد علامة النطاق (اختياري)، ثم حدد **"التالي**".
   - أو حدد **"التالي"**

7. في الخطوة **4 التعيينات**، في **المجموعات المضمنة**، للمجموعات التي تريد تطبيق هذه القاعدة عليها، حدد من الخيارات التالية:

   - **إضافة مجموعات**
   - **إضافة كافة المستخدمين**
   - **إضافة جميع الأجهزة**

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem06-4-assignments.png" alt-text="الواجبات في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem06-4-assignments.png":::

8. في **المجموعات المستبعدة**، حدد أي مجموعات تريد استبعادها من هذه القاعدة، ثم حدد **"التالي**".

9. في الخطوة **5 قواعد قابلية التطبيق** للإعدادات التالية، قم بما يلي:

   - في **"القاعدة"**، حدد إما **"تعيين ملف تعريف"** أو **"عدم تعيين ملف التعريف" إذا**
   - في **الخاصية**، حدد الخاصية التي تريد تطبيق هذه القاعدة عليها
   - في **Value**، أدخل القيمة القابلة للتطبيق أو نطاق القيمة

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem07-5-applicability-rules.png" alt-text="قواعد قابلية التطبيق في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem07-5-applicability-rules.png":::

10. حدد **التالي**. في الخطوة **6 Review + create**، راجع الإعدادات والمعلومات التي حددتها وأدخلتها، ثم حدد **Create**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mem08-6-review-create.png" alt-text="الخيار &quot;مراجعة وإنشاء&quot; في مدخل مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/mem08-6-review-create.png":::

    > [!NOTE]
    > القواعد نشطة وتعيش في غضون دقائق.

> [!NOTE]
> معالجة التعارض:
>
> إذا قمت بتعيين جهاز نهجين مختلفين ل ASR، فإن طريقة معالجة التعارض هي القواعد التي تم تعيين حالات مختلفة لها، ولا توجد إدارة تعارض في مكانها، والنتيجة هي خطأ.
>
> لن تؤدي القواعد غير المتضاربة إلى حدوث خطأ، وسيتم تطبيق القاعدة بشكل صحيح. والنتيجة هي تطبيق القاعدة الأولى، ودمج القواعد غير المتعارضة اللاحقة في النهج.

### <a name="mdm"></a>MDM

استخدم موفر خدمة تكوين [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) (CSP) لتمكين وضع كل قاعدة وتعيينه بشكل فردي.

فيما يلي عينة للرجوع إليها، باستخدام قيم GUID [لمرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

القيم التي يجب تمكينها (حظر) أو تعطيلها أو تحذيرها أو تمكينها في وضع التدقيق هي:

- 0 : تعطيل (تعطيل قاعدة ASR)
- 1 : كتلة (تمكين قاعدة ASR)
- 2 : التدقيق (تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها)
- 6 : التحذير (تمكين قاعدة ASR ولكن السماح للمستخدم النهائي بتجاوز الكتلة). يتوفر وضع التحذير لمعظم قواعد ASR.

استخدم موفر خدمة تكوين [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) لإضافة استثناءات.

على سبيل المثال:

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> تأكد من إدخال قيم OMA-URI بدون مسافات.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. في إدارة التكوين نقطة نهاية Microsoft، انتقل إلى **الأصول والتوافق**\>**حماية نقطة النهاية**\>**حماية من الهجمات لـ Windows Defender**.

2. حدد الصفحة **الرئيسية**\>**إنشاء نهج حماية ضد الهجمات**.

3. أدخل اسما ووصفا، وحدد **"Attack Surface Reduction**"، وحدد **"Next**".

4. اختر القواعد التي ستقوم بحظر الإجراءات أو تدقيقها وحدد **"التالي**".

5. راجع الإعدادات وحدد **"التالي** " لإنشاء النهج.

6. بعد إنشاء النهج، حدد **إغلاق**.

### <a name="group-policy"></a>نهج المجموعة

> [!WARNING]
> إذا قمت بإدارة أجهزة الكمبيوتر والأجهزة باستخدام Intune أو Configuration Manager أو أي نظام أساسي آخر للإدارة على مستوى المؤسسة، فسيؤدي برنامج الإدارة إلى الكتابة فوق أي إعدادات نهج المجموعة متضاربة عند بدء التشغيل.

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](https://technet.microsoft.com/library/cc731212.aspx)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **تقليل سطح الهجوم** **الحماية من مخاطر الهجمات من Microsoft Defender**\>.

4. حدد **تكوين قواعد تقليل الأجزاء المعرضة للهجوم** وحدد **Enabled**. يمكنك بعد ذلك تعيين الحالة الفردية لكل قاعدة في مقطع الخيارات. حدد **"إظهار"...** وأدخل معرف القاعدة في عمود **"اسم القيمة** " والحالة التي اخترتها في عمود **"القيمة** " كما يلي:

   - 0 : تعطيل (تعطيل قاعدة ASR)
   - 1 : كتلة (تمكين قاعدة ASR)
   - 2 : التدقيق (تقييم كيفية تأثير قاعدة ASR على مؤسستك إذا تم تمكينها)
   - 6 : التحذير (تمكين قاعدة ASR ولكن السماح للمستخدم النهائي بتجاوز الكتلة)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="قواعد ASR في نهج المجموعة" lightbox="images/asr-rules-gp.png":::

5. لاستبعاد الملفات والمجلدات من قواعد ASR، حدد **استبعاد الملفات والمسارات من إعداد قواعد تقليل الأجزاء المعرضة للهجوم** وقم بتعيين الخيار إلى **ممكن**. حدد **"إظهار** " وأدخل كل ملف أو مجلد في عمود **"اسم القيمة** ". أدخل **0** في عمود **"القيمة** " لكل عنصر.

   > [!WARNING]
   > لا تستخدم علامات الاقتباس لأنها غير معتمدة لعمود **اسم القيمة** أو عمود **"القيمة** ".

### <a name="powershell"></a>PowerShell

> [!WARNING]
> إذا كنت تدير أجهزة الكمبيوتر والأجهزة باستخدام Intune أو Configuration Manager أو نظام أساسي آخر للإدارة على مستوى المؤسسة، فسيؤدي برنامج الإدارة إلى الكتابة فوق أي إعدادات PowerShell متضاربة عند بدء التشغيل. للسماح للمستخدمين بتعريف القيمة باستخدام PowerShell، استخدم الخيار "معرف المستخدم" للقاعدة في النظام الأساسي للإدارة.
> يسمح "معرف المستخدم" لمستخدم مسؤول محلي بتكوين القاعدة.
> يظهر إعداد الخيار "معرف من قبل المستخدم" في الشكل التالي.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-user-defined.png" alt-text="الخيار &quot;تمكين&quot; لأمان بيانات الاعتماد" lightbox="images/asr-user-defined.png":::

1. اكتب **powershell** في قائمة البدء، وانقر بزر الماوس الأيمن **فوق Windows PowerShell** وحدد **"تشغيل" كمسؤول**.

2. اكتب أحد أوامر cmdlet التالية. (راجع [مرجع قواعد تقليل الأجزاء المعرضة](attack-surface-reduction-rules-reference.md) للهجوم للحصول على مزيد من التفاصيل، مثل معرف القاعدة.)

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    لتمكين قواعد ASR في وضع التدقيق، استخدم أمر cmdlet التالي:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    لتمكين قواعد ASR في وضع التحذير، استخدم أمر cmdlet التالي:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Warn
    ```

    لتمكين إساءة استخدام كتلة ASR لبرامج التشغيل الموقعة المعرضة للخطر، استخدم أمر cmdlet التالي:

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    لإيقاف تشغيل قواعد ASR، استخدم cmdlet التالية:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > يجب تحديد الحالة بشكل فردي لكل قاعدة، ولكن يمكنك دمج القواعد والحالة في قائمة مفصولة بفواصل.
    >
    > في المثال التالي، سيتم تمكين أول قاعدتين، وسيتم تعطيل القاعدة الثالثة، وسيتم تمكين القاعدة الرابعة في وضع التدقيق:
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    يمكنك أيضا استخدام `Add-MpPreference` فعل PowerShell لإضافة قواعد جديدة إلى القائمة الموجودة.

    > [!WARNING]
    > `Set-MpPreference` دائما ما يقوم بالكتابة فوق مجموعة القواعد الموجودة. إذا كنت تريد الإضافة إلى المجموعة الموجودة، فاستخدمها `Add-MpPreference` بدلا من ذلك.
    > يمكنك الحصول على قائمة بالقواعد وحالتها الحالية باستخدام `Get-MpPreference`.

3. لاستبعاد الملفات والمجلدات من قواعد ASR، استخدم أمر cmdlet التالي:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    تابع الاستخدام `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` لإضافة المزيد من الملفات والمجلدات إلى القائمة.

    > [!IMPORTANT]
    > يستخدم `Add-MpPreference` لإلحاق التطبيقات أو إضافتها إلى القائمة. `Set-MpPreference` سيؤدي استخدام cmdlet إلى الكتابة فوق القائمة الموجودة.

## <a name="related-articles"></a>المقالات ذات الصلة

- [مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md)
- [تقييم تقليل الأجزاء المعرضة للهجوم](evaluate-attack-surface-reduction.md)
- [الأسئلة المتداولة حول قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)
