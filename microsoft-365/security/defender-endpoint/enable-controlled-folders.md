---
title: تمكين الوصول إلى المجلدات الخاضعة للتحكم
keywords: الوصول المتحكم به إلى المجلدات، windows 10، windows 11، windows defender، برامج الفدية الضارة، الحماية، الملفات، المجلدات، تمكين، تشغيل، استخدام
description: تعرف على كيفية حماية ملفاتك المهمة من خلال تمكين الوصول إلى المجلدات الخاضعة للتحكم
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
ms.openlocfilehash: b62ff851cbee58cf3b29a2b4dde6fb1b6107dd85
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472804"
---
# <a name="enable-controlled-folder-access"></a>تمكين الوصول إلى المجلدات الخاضعة للتحكم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[يساعدك الوصول المتحكم به إلى](controlled-folders.md) المجلد على حماية البيانات القيمة من التطبيقات الضارة والتهديدات، مثل برامج الفدية الضارة. يتم تضمين الوصول المتحكم به إلى المجلدات مع Windows 10 Windows 11 Windows Server 2019. يتم أيضا تضمين الوصول المتحكم به للمجلدات كجزء من الحل الموحد الحديث Windows [Server 2012R2 و2016](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

يمكنك تمكين الوصول إلى المجلدات الخاضعة للتحكم باستخدام أي من هذه الأساليب:

- [أمن Windows التطبيق *](#windows-security-app)
- [إدارة نقاط النهاية من Microsoft](#endpoint-manager)
- [الأجهزة إدارة الجهاز (MDM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [نهج المجموعة](#group-policy)
- [PowerShell](#powershell)

[يسمح لك](evaluate-controlled-folder-access.md) وضع التدقيق باختبار كيفية عمل الميزة (ومراجعة الأحداث) دون التأثير على الاستخدام العادي للجهاز.

نهج المجموعة الإعدادات التي تعطل دمج قائمة المسؤولين المحليين إلى تجاوز إعدادات الوصول إلى المجلدات التي يتم التحكم بها. كما أنها تتجاوز المجلدات المحمية والتطبيقات المسموح بها التي يحددها المسؤول المحلي من خلال الوصول المتحكم به إلى المجلدات. تتضمن هذه السياسات ما يلي:

- برنامج الحماية من الفيروسات من Microsoft Defender **تكوين سلوك دمج المسؤول المحلي في القوائم**
- System Center Endpoint Protection **السماح للمستخدمين بإضافة استثناءات وتجاوزات**

لمزيد من المعلومات حول تعطيل دمج القائمة المحلية، راجع منع المستخدمين من تعديل إعدادات نهج [Microsoft Defender AV محليا أو السماح لهم بذلك](/windows/security/threat-protection/microsoft-defender-antivirus/configure-local-policy-overrides-microsoft-defender-antivirus).

## <a name="windows-security-app"></a>أمن Windows التطبيق

1. افتح أمن Windows عن طريق تحديد أيقونة الدرع في شريط المهام. يمكنك أيضا البحث في قائمة **البدء عن أمن Windows**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر) ثم حدد **الحماية من برامج الفدية الضارة**.

3. قم بتعيين مفتاح التبديل للوصول **إلى المجلدات التي تم التحكم بها** إلى **تشغيل**.

> [!NOTE]
> *لا يتوفر هذا الأسلوب على Windows Server 2012R2 أو 2016.
> 
> إذا تم تكوين الوصول المتحكم به للمجلدات باستخدام نهج المجموعة CSPs أو PowerShell أو MDM، ستتغير الحالة في تطبيق أمن Windows بعد إعادة تشغيل الجهاز.
> إذا تم تعيين الميزة إلى **وضع التدقيق** باستخدام أي من هذه الأدوات، أمن Windows التطبيق الحالة ك **إيقاف تشغيل**.
> إذا كنت تحمي بيانات ملف تعريف المستخدم، نوصي بأن يكون ملف تعريف المستخدم على محرك Windows الافتراضي.

## <a name="endpoint-manager"></a>إدارة نقاط النهاية

1. سجل [الدخول إلى إدارة نقاط النهاية](https://endpoint.microsoft.com) وأفتح **أمان نقطة النهاية**.

2. انتقل إلى **نهج تقليل مساحة الهجوم**\>.

3. حدد **النظام** الأساسي **، واختر Windows 10 واللاحقة**، وحدد ملف التعريف قواعد تقليل الهجوم **على Surface** \> **إنشاء**.

4. قم  تسمية النهج وأضف وصفا. حدد **التالي**.

5. قم بالتمرير لأسفل، وحدد القائمة المنسدل **تمكين حماية** المجلد، واختر **تمكين**.

6. حدد **قائمة بالمجلدات الإضافية التي تحتاج** إلى حماية وأضف المجلدات التي تحتاج إلى حماية.

7. حدد **قائمة التطبيقات التي لديها حق الوصول** إلى المجلدات المحمية وأضف التطبيقات التي لديها حق الوصول إلى المجلدات المحمية.

8. حدد **استبعاد الملفات والمسارات** من قواعد الحد من سطح الهجوم وإضافة الملفات والمسارات التي يجب استبعادها من قواعد الحد من سطح الهجوم.

9. حدد **تعيينات ملف التعريف**، وحدد كل المستخدمين & **كافة الأجهزة**، ثم حدد **حفظ**.

10. حدد **التالي** لحفظ كل ريشة مفتوحة ثم **إنشاء**.

    > [!NOTE]
    > أحرف البدل معتمدة للتطبيقات، ولكن ليس للمجلدات. لا يتم حماية المكاتب الفرعية. ستستمر التطبيقات المسموح بها في تشغيل الأحداث حتى تتم إعادة تشغيلها.

## <a name="mobile-device-management-mdm"></a>الأجهزة إدارة الجهاز (MDM)

استخدم [موفر خدمة تكوين ./Vendor/MSFT/Policy/Config/ControlledFolderAccessProtectedFolders](/windows/client-management/mdm/policy-csp-defender) (CSP) للسماح للتطبيقات بإجراء تغييرات على المجلدات المحمية.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. في Microsoft Endpoint Configuration Manager، انتقل إلى **الأصول والتوافق** \>  \> Endpoint Protection **Windows Defender Exploit Guard**.

2. حدد **الصفحة الرئيسية** \> **إنشاء نهج حماية استغلال**.

3. أدخل اسما ووصفا، وحدد **الوصول إلى** المجلدات الخاضعة للتحكم، وحدد **التالي**.

4. اختر ما إذا كنت تقوم بحظر التغييرات أو تدقيقها، أو السماح للتطبيقات الأخرى، أو إضافة مجلدات أخرى، وحدد **التالي**.

   > [!NOTE]
   > يتم دعم أحرف البدل للتطبيقات، ولكن ليس للمجلدات. لا يتم حماية المكاتب الفرعية. ستستمر التطبيقات المسموح بها في تشغيل الأحداث حتى تتم إعادة تشغيلها.

5. راجع الإعدادات وحدد **التالي** لإنشاء النهج.

6. بعد إنشاء النهج **، أغلق.**

## <a name="group-policy"></a>نهج المجموعة

1. على جهاز نهج المجموعة، افتح وحدة التحكم نهج المجموعة [الإدارة](https://technet.microsoft.com/library/cc731212.aspx)، وانقر ب الماوس الأيمن فوق نهج المجموعة الذي تريد تكوينه وحدد **تحرير**.

2. في نهج المجموعة **إدارة،** انتقل إلى **تكوين الكمبيوتر** وحدد **قوالب إدارية**.

3. قم بتوسيع الشجرة Windows **مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > Windows Defender Exploit Guard > الوصول إلى المجلدات الخاضعة للتحكم**.

4. انقر نقرا مزدوجا **فوق إعداد "تكوين الوصول إلى** المجلدات التي تم التحكم فيها" ثم قم بتعيين الخيار إلى **"تمكين**". في قسم الخيارات، يجب تحديد أحد الخيارات التالية:
   - **تمكين** - لن يسمح للتطبيقات الضارة والمريبة بإجراء تغييرات على الملفات في المجلدات المحمية. سيتم توفير إعلام في Windows الأحداث.
   - **تعطيل (افتراضي)** - لن تعمل ميزة الوصول إلى المجلدات التي تم التحكم بها. يمكن لجميع التطبيقات إجراء تغييرات على الملفات في المجلدات المحمية.
   - **وضع التدقيق** - سيتم السماح بالتغييرات إذا حاول تطبيق ضار أو مريب إجراء تغيير على ملف في مجلد محمي. ومع ذلك، سيتم تسجيله في Windows الأحداث حيث يمكنك تقييم التأثير على مؤسستك.
   - **حظر تعديل القرص فقط** - سيتم تسجيل المحاولات التي تقوم بها تطبيقات غير صحيحة للكتابة في قطاعات الأقراص في Windows الحدث. يمكن العثور على هذه السجلات في **سجلات** \> التطبيقات والخدمات ل Microsoft \> \> Windows Windows Defender \> \> التشغيلية 1123.
   - **تعديل القرص** للتدقيق فقط - سيتم تسجيل محاولات الكتابة إلى قطاعات القرص المحمية فقط في سجل أحداث Windows  (ضمن **سجلات** \> التطبيقات والخدمات **Microsoft** \> **Windows** \> **Windows Defender** \> \> التشغيلية 1124). لن يتم تسجيل محاولات تعديل الملفات أو حذفها في المجلدات المحمية.

    :::image type="content" source="../../media/cfa-gp-enable.png" alt-text="الخيار &quot;تمكين نهج المجموعة&quot; و&quot;وضع التدقيق&quot; المحدد" lightbox="../../media/cfa-gp-enable.png":::

> [!IMPORTANT]
> لتمكين الوصول إلى المجلدات التي يتم التحكم فيها بشكل كامل، يجب تعيين نهج المجموعة إلى تمكين وتحديد  **حظر** في القائمة المنسدلة خيارات.

## <a name="powershell"></a>PowerShell

1. اكتب **powershell** في قائمة البدء، وانقر بضغطة **Windows PowerShell وحدد** **تشغيل كمسؤول**.

2. أدخل cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableControlledFolderAccess Enabled
    ```

يمكنك تمكين الميزة في وضع التدقيق عن طريق تحديد `AuditMode` بدلا من `Enabled`.

يتم `Disabled` استخدامها إيقاف تشغيل الميزة.

## <a name="see-also"></a>راجع أيضًا

- [حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات](controlled-folders.md)
- [تخصيص الوصول إلى المجلدات الخاضعة للتحكم](customize-controlled-folders.md)
- [تقييم Microsoft Defender لنقطة النهاية](evaluate-mde.md)
