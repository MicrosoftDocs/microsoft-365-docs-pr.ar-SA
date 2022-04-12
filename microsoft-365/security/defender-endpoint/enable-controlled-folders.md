---
title: تمكين الوصول إلى المجلدات الخاضعة للتحكم
keywords: الوصول المتحكم به إلى المجلد، windows 10، windows 11، windows defender، برامج الفدية الضارة، الحماية، الملفات، المجلدات، التمكين، تشغيل، استخدام
description: تعرف على كيفية حماية ملفاتك المهمة من خلال تمكين الوصول إلى المجلدات الخاضعة للرقابة
ms.prod: m365-security
ms.topic: article
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 4854ca235790cc8400f3f5a962e4bff203f86f98
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788117"
---
# <a name="enable-controlled-folder-access"></a>تمكين الوصول إلى المجلدات الخاضعة للتحكم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يساعدك [الوصول المتحكم به إلى المجلد](controlled-folders.md) على حماية البيانات القيمة من التطبيقات والتهديدات الضارة، مثل برامج الفدية الضارة. يتم تضمين الوصول إلى المجلدات التي يتم التحكم فيها مع Windows 10 Windows 11 وخادم Windows 2019. يتم أيضا تضمين الوصول إلى المجلدات الخاضعة للرقابة كجزء من [الحل الحديث والموحد Windows Server 2012R2 و2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

يمكنك تمكين الوصول المتحكم به إلى المجلدات باستخدام أي من هذه الأساليب:

- [تطبيق أمن Windows *](#windows-security-app)
- [إدارة نقاط النهاية من Microsoft](#endpoint-manager)
- [إدارة الجهاز الجوال (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [نهج المجموعة](#group-policy)
- [PowerShell](#powershell)

يسمح لك [وضع التدقيق](evaluate-controlled-folder-access.md) لاختبار كيفية عمل الميزة (ومراجعة الأحداث) دون التأثير على الاستخدام العادي للجهاز.

ستتجاوز إعدادات نهج المجموعة التي تعطل دمج قائمة المسؤول المحلي إعدادات الوصول إلى المجلدات التي يتم التحكم فيها. كما أنها تتجاوز المجلدات المحمية والتطبيقات المسموح بها التي يعينها المسؤول المحلي من خلال الوصول إلى المجلدات التي يتم التحكم فيها. وتشمل هذه النهج ما يلي:

- برنامج الحماية من الفيروسات من Microsoft Defender **تكوين سلوك دمج المسؤولين المحليين للقوائم**
- System Center Endpoint Protection **السماح للمستخدمين بإضافة استثناءات وتجاوزات**

لمزيد من المعلومات حول تعطيل دمج القوائم المحلية، راجع [منع المستخدمين أو السماح لهم بتعديل إعدادات نهج Microsoft Defender AV محليا](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>تطبيق أمن Windows

1. افتح تطبيق أمن Windows عن طريق تحديد أيقونة الدرع في شريط المهام. يمكنك أيضا البحث في قائمة البدء عن **أمن Windows**.

2. حدد لوحة **الحماية من الفيروسات & التهديد** (أو أيقونة الدرع على شريط القوائم الأيسر) ثم حدد **الحماية من برامج الفدية الضارة**.

3. تعيين مفتاح **التبديل للوصول إلى المجلد الذي يتم التحكم فيه** إلى **"تشغيل**".

> [!NOTE]
> *هذا الأسلوب غير متوفر على Windows Server 2012R2 أو 2016.
> 
> إذا تم تكوين الوصول إلى المجلد المتحكم به باستخدام نهج المجموعة أو PowerShell أو MDM CSPs، فستتغير الحالة في تطبيق أمن Windows بعد إعادة تشغيل الجهاز.
> إذا تم تعيين الميزة إلى **وضع التدقيق** باستخدام أي من هذه الأدوات، فسيعرض تطبيق أمن Windows الحالة على أنها **متوقفة عن التشغيل**.
> إذا كنت تحمي بيانات ملف تعريف المستخدم، نوصي بأن يكون ملف تعريف المستخدم على محرك أقراص التثبيت الافتراضي Windows.

## <a name="endpoint-manager"></a>إدارة نقاط النهاية

1. سجل الدخول إلى [إدارة نقاط النهاية](https://endpoint.microsoft.com) وافتح **أمان نقطة النهاية**.

2. انتقل إلى نهج **تقليل الأجزاء** \> **المعرضة** للهجوم.

3. حدد **النظام الأساسي**، واختر **Windows 10 والإخيرة**، وحدد **قواعد** \> تقليل الأجزاء الهجومية لملف التعريف **التي تم إنشاؤها**.

4. قم بتسمية النهج وإضافة وصف. حدد **"التالي**".

5. قم بالتمرير لأسفل إلى الأسفل، وحدد القائمة المنسدلة **"تمكين حماية المجلد** "، واختر **"تمكين**".

6. حدد **قائمة بالمجلدات الإضافية التي يجب حمايتها** وأضف المجلدات التي يجب حمايتها.

7. حدد **قائمة التطبيقات التي لديها حق الوصول إلى المجلدات المحمية** وأضف التطبيقات التي لديها حق الوصول إلى المجلدات المحمية.

8. حدد **استبعاد الملفات والمسارات من قواعد تقليل الأجزاء المعرضة للهجوم** وأضف الملفات والمسارات التي تحتاج إلى استبعادها من قواعد تقليل الأجزاء المعرضة للهجوم.

9. حدد **تعيينات** ملف التعريف، وقم **بتعيينها إلى كافة المستخدمين & كافة الأجهزة**، وحدد **"حفظ**".

10. حدد **"التالي** " لحفظ كل جزء مفتوح ثم **قم بإنشاء**.

    > [!NOTE]
    > يتم اعتماد أحرف البدل للتطبيقات، ولكن ليس للمجلدات. المجلدات الفرعية غير محمية. ستستمر التطبيقات المسموح بها في تشغيل الأحداث حتى تتم إعادة تشغيلها.

## <a name="mobile-device-management-mdm"></a>إدارة الجهاز الجوال (MDM)

استخدم موفر خدمة تكوين [./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) (CSP) للسماح للتطبيقات بإجراء تغييرات على المجلدات المحمية.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. في Microsoft Endpoint Configuration Manager، انتقل إلى **"Assets and Compliance** \> **Endpoint Protection** \> **Windows Defender Exploit Guard**".

2. حدد **Home** \> **Create Exploit Guard Policy**.

3. أدخل اسما ووصفا، وحدد **الوصول إلى المجلد المتحكم به**، وحدد **"التالي**".

4. اختر ما إذا كنت تريد حظر التغييرات أو تدقيقها، أو السماح بتطبيقات أخرى، أو إضافة مجلدات أخرى، وحدد **"التالي**".

   > [!NOTE]
   > حرف البدل معتمد للتطبيقات، ولكن ليس للمجلدات. المجلدات الفرعية غير محمية. ستستمر التطبيقات المسموح بها في تشغيل الأحداث حتى تتم إعادة تشغيلها.

5. راجع الإعدادات وحدد **"التالي** " لإنشاء النهج.

6. بعد إنشاء النهج، **أغلق**.

## <a name="group-policy"></a>نهج المجموعة

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](https://technet.microsoft.com/library/cc731212.aspx)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > Windows Defender Exploit Guard > الوصول إلى المجلد الخاضع للرقابة**.

4. انقر نقرا مزدوجا فوق إعداد "**تكوين الوصول إلى المجلد الخاضع للتحكم**" وقم بتعيين الخيار إلى **"ممكن".** في قسم الخيارات، يجب تحديد أحد الخيارات التالية:
   - **تمكين** - لن يسمح للتطبيقات الضارة والمريبة بإجراء تغييرات على الملفات في المجلدات المحمية. سيتم توفير إعلام في سجل أحداث Windows.
   - **تعطيل (افتراضي)** - لن تعمل ميزة الوصول إلى المجلدات التي تم التحكم فيها. يمكن لجميع التطبيقات إجراء تغييرات على الملفات في المجلدات المحمية.
   - **وضع التدقيق** - سيتم السماح بالتغييرات إذا حاول تطبيق ضار أو مريب إجراء تغيير على ملف في مجلد محمي. ومع ذلك، سيتم تسجيله في سجل الأحداث Windows حيث يمكنك تقييم التأثير على مؤسستك.
   - **حظر تعديل القرص فقط** - سيتم تسجيل محاولات التطبيقات غير الموثوق بها للكتابة إلى قطاعات القرص في Windows سجل الأحداث. يمكن العثور على هذه السجلات في **سجلات التطبيقات والخدمات** \> Microsoft \> Windows \> Windows Defender \> Operational \> ID 1123.
   - **تعديل قرص التدقيق فقط** - سيتم تسجيل محاولات الكتابة إلى قطاعات الأقراص المحمية فقط في سجل أحداث Windows (ضمن **سجلات التطبيقات والخدمات** \> **Microsoft** \> **Windows** \> **Windows Defender** \> **Operational** \> **ID 1124**). لن يتم تسجيل محاولات تعديل الملفات أو حذفها في مجلدات محمية.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="الخيار &quot;تمكين نهج المجموعة&quot; وتحديد &quot;وضع التدقيق&quot;" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> لتمكين الوصول إلى المجلدات التي يتم التحكم فيها بشكل كامل، يجب تعيين الخيار نهج المجموعة إلى **"ممكن"** وتحديد **"حظر"** في القائمة المنسدلة "خيارات".

## <a name="powershell"></a>PowerShell

1. اكتب **powershell** في قائمة البدء، وانقر بزر الماوس الأيمن **فوق Windows PowerShell** وحدد **"تشغيل" كمسؤول**.

2. أدخل cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

يمكنك تمكين الميزة في وضع التدقيق عن طريق تحديد `AuditMode` بدلا من `Enabled`.

يستخدم `Disabled` لإيقاف تشغيل الميزة.

## <a name="see-also"></a>راجع أيضًا

- [حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات](controlled-folders.md)
- [تخصيص الوصول إلى المجلدات الخاضعة للتحكم](customize-controlled-folders.md)
- [تقييم Microsoft Defender لنقطة النهاية](evaluate-mde.md)
