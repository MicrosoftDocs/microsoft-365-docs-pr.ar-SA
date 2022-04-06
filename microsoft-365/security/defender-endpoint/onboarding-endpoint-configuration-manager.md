---
title: الboarding باستخدام Microsoft Endpoint Configuration Manager
description: تعرف على كيفية الحافظة على Microsoft Defender لنقطة النهاية باستخدام Microsoft Endpoint Configuration Manager
keywords: التهيئة، التكوين، النشر، النشر، إدارة تكوين نقطة النهاية، Microsoft Defender لنقطة النهاية، إنشاء مجموعة، استجابة الكشف عن نقطة النهاية، حماية الجيل التالي، الحد من سطح الهجوم، إدارة تكوين نقطة نهاية Microsoft
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b8847fb9132ee037a3103bf86aabd14d21fb482f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469416"
---
# <a name="onboarding-using-microsoft-endpoint-configuration-manager"></a>الboarding باستخدام Microsoft Endpoint Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

هذه المقالة هي جزء من دليل النشر، وهي تعمل كطريقة تكاتف كمثال.

في موضوع [التخطيط](deployment-strategy.md) ، تم توفير عدة أساليب للأجهزة المجهزة للخدمة. يتناول هذا الموضوع بنية الإدارة المشاركة.

:::image type="content" source="images/co-management-architecture.png" alt-text="هندسة السحابة الأصلية" lightbox="images/co-management-architecture.png":::
*رسم تخطيطي لهنيات البيئة*

على الرغم من أن Defender for Endpoint يدعم التكهن بنقاط النهاية والأدوات المختلفة، لا تغطي هذه المقالة هذه النقاط والأدوات. للحصول على معلومات حول التكديب العام باستخدام أساليب وأدوات النشر المعتمدة الأخرى، راجع [نظرة عامة على التكديب](onboarding.md).

يرشد هذا الموضوع المستخدمين في:

- الخطوة 1: Windows الأجهزة للخدمة
- الخطوة 2: تكوين Defender لإمكانيات نقطة النهاية

ستعرض لك إرشادات التكسير هذه الخطوات الأساسية التالية التي تحتاج إلى اتخاذها عند استخدام Microsoft Endpoint Configuration Manager:

- **إنشاء مجموعة في Microsoft Endpoint Configuration Manager**
- **تكوين قدرات Microsoft Defender لنقطة النهاية باستخدام Microsoft Endpoint Configuration Manager**

> [!NOTE]
> يتم Windows فقط في نشر هذا المثال.

## <a name="step-1-onboard-windows-devices-using-microsoft-endpoint-configuration-manager"></a>الخطوة 1: Windows الأجهزة باستخدام Microsoft Endpoint Configuration Manager

### <a name="collection-creation"></a>إنشاء مجموعة

لتهيئة Windows الأجهزة Microsoft Endpoint Configuration Manager، يمكن أن يستهدف النشر مجموعة موجودة أو يمكن إنشاء مجموعة جديدة لاختبارها.

لا يقوم التركيب باستخدام أدوات مثل نهج المجموعة أو الأسلوب اليدوي بتثبيت أي عامل على النظام.

ضمن Microsoft Endpoint Configuration Manager وحدة التحكم، سيتم تكوين عملية التهيئة كجزء من إعدادات التوافق داخل وحدة التحكم.

سيحتفظ أي نظام يتلقى هذا التكوين المطلوب بهذا التكوين طالما Configuration Manager العميل يتلقى هذا النهج من نقطة الإدارة.

اتبع الخطوات أدناه لنقاط نهاية الحافظة باستخدام Microsoft Endpoint Configuration Manager.

1. في Microsoft Endpoint Configuration Manager التحكم، انتقل إلى **مجموعات الأجهزة نظرة \> \> عامة حول التوافق والأصول**.

    :::image type="content" source="images/configmgr-device-collections.png" alt-text="معالج Microsoft Endpoint Configuration Manager 1" lightbox="images/configmgr-device-collections.png":::

2. انقر **بيمين فوق مجموعة الأجهزة** وحدد **إنشاء مجموعة أجهزة**.

    :::image type="content" source="images/configmgr-create-device-collection.png" alt-text="معالج Microsoft Endpoint Configuration Manager 2" lightbox="images/configmgr-create-device-collection.png":::

3. قم بتوفير **مجموعة** أسماء **وحدود**، ثم حدد **التالي**.

    :::image type="content" source="images/configmgr-limiting-collection.png" alt-text="معالج Microsoft Endpoint Configuration Manager 3" lightbox="images/configmgr-limiting-collection.png":::

4. حدد **إضافة قاعدة واختر** **قاعدة الاستعلام**.

    :::image type="content" source="images/configmgr-query-rule.png" alt-text="معالج Microsoft Endpoint Configuration Manager 4" lightbox="images/configmgr-query-rule.png":::

5. انقر **فوق التالي** على **معالج العضوية المباشرة وانقر** فوق **تحرير بيان الاستعلام**.

    :::image type="content" source="images/configmgr-direct-membership.png" alt-text="المعالج Microsoft Endpoint Configuration Manager 5" lightbox="images/configmgr-direct-membership.png":::

6. حدد **معايير** ثم اختر أيقونة النجمة.

    :::image type="content" source="images/configmgr-criteria.png" alt-text="المعالج Microsoft Endpoint Configuration Manager 6" lightbox="images/configmgr-criteria.png":::

7. احتفظ بنوع المعيار **كقيمة** بسيطة، واختر المكان حيث يكون نظام التشغيل **-** رقم البناء،  عامل التشغيل كما هو أكبر من أو يساوي وقيمة **14393** وانقر فوق **موافق**.

    :::image type="content" source="images/configmgr-simple-value.png" alt-text="المعالج Microsoft Endpoint Configuration Manager 7" lightbox="images/configmgr-simple-value.png":::

8. حدد **التالي** ثم **إغلاق**.

    :::image type="content" source="images/configmgr-membership-rules.png" alt-text="المعالج Microsoft Endpoint Configuration Manager 8" lightbox="images/configmgr-membership-rules.png":::

9. حدد **التالي**.

    :::image type="content" source="images/configmgr-confirm.png" alt-text="المعالج Microsoft Endpoint Configuration Manager 9" lightbox="images/configmgr-confirm.png":::

بعد إكمال هذه المهمة، لديك الآن مجموعة أجهزة مع Windows نقاط النهاية في البيئة.

## <a name="step-2-configure-microsoft-defender-for-endpoint-capabilities"></a>الخطوة 2: تكوين Microsoft Defender لنقطة النهاية التقنية

يرشدك هذا القسم في تكوين الإمكانات التالية باستخدام Microsoft Endpoint Configuration Manager على Windows التالية:

- [**الكشف عن نقطة النهاية والاستجابة لها**](#endpoint-detection-and-response)
- [**حماية الجيل التالي**](#next-generation-protection)
- [**الحد من سطح الهجوم**](#attack-surface-reduction)

### <a name="endpoint-detection-and-response"></a>الكشف عن نقطة النهاية والاستجابة لها

#### <a name="windows-10-and-windows-11"></a>Windows 10 Windows 11

من داخل Microsoft 365 Defender `.onboarding` من الممكن تنزيل النهج الذي يمكن استخدامه لإنشاء النهج في System Center Configuration Manager ونشر هذا النهج Windows 10 Windows 11 الأخرى.

1. من مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender،</a> حدد الإعدادات [ثم اداخل](https://security.microsoft.com/preferences2/onboarding).

2. ضمن أسلوب النشر، حدد الإصدار **المعتمد من Microsoft Endpoint Configuration Manager**.

    :::image type="content" source="images/mdatp-onboarding-wizard.png" alt-text="معالج Microsoft Endpoint Configuration Manager 10" lightbox="images/mdatp-onboarding-wizard.png":::

3. حدد **تنزيل الحزمة**.

   :::image type="content" source="images/mdatp-download-package.png" alt-text="معالج Microsoft Endpoint Configuration Manager 11" lightbox="images/mdatp-download-package.png":::

4. احفظ الحزمة في موقع يمكن الوصول إليه.
5. في Microsoft Endpoint Configuration Manager، انتقل إلى: **الأصول والتوافق > نظرة عامة > Endpoint Protection > Microsoft Defender ATP**.

6. انقر بز الماوس **الأيمن فوق نهج ATP ل Microsoft Defender** وحدد **إنشاء نهج ATP ل Microsoft Defender**.

    :::image type="content" source="images/configmgr-create-policy.png" alt-text="معالج Microsoft Endpoint Configuration Manager 12" lightbox="images/configmgr-create-policy.png":::

7. أدخل الاسم والوصف، وتحقق من تحديد **التكئب** ، ثم حدد **التالي**.

    :::image type="content" source="images/configmgr-policy-name.png" alt-text="معالج Microsoft Endpoint Configuration Manager 13" lightbox="images/configmgr-policy-name.png":::

8. انقر **فوق استعراض**.

9. انتقل إلى موقع الملف الذي تم تنزيله من الخطوة 4 أعلاه.

10. انقر فوق **التالي**.
11. تكوين الوكيل باستخدام النماذج المناسبة (**أنواع الملفات بلا** أو **كافة الملفات**).

    :::image type="content" source="images/configmgr-config-settings.png" alt-text="إعدادات التكوين1" lightbox="images/configmgr-config-settings.png":::

12. حدد بيانات التكليف المناسبة (**عادي** أو **معجل**) ثم انقر فوق **التالي**.

    :::image type="content" source="images/configmgr-telemetry.png" alt-text="إعدادات التكوين2" lightbox="images/configmgr-telemetry.png":::

13. تحقق من التكوين، ثم انقر فوق **التالي**.

    :::image type="content" source="images/configmgr-verify-configuration.png" alt-text="إعدادات التكوين3" lightbox="images/configmgr-verify-configuration.png":::

14. انقر **فوق** إغلاق عند اكتمال المعالج.

15. في وحدة Microsoft Endpoint Configuration Manager، انقر بيمين فوق نهج Defender for Endpoint الذي أنشأته للتو وحدد **نشر**.

    :::image type="content" source="images/configmgr-deploy.png" alt-text="إعدادات التكوين4" lightbox="images/configmgr-deploy.png":::

16. في اللوحة اليمنى، حدد المجموعة التي تم إنشاؤها مسبقا وانقر فوق **موافق**.

    :::image type="content" source="images/configmgr-select-collection.png" alt-text="إعدادات التكوين5" lightbox="images/configmgr-select-collection.png":::

#### <a name="previous-versions-of-windows-client-windows-7-and-windows-81"></a>الإصدارات السابقة من Windows العميل (Windows 7 Windows 8.1)

اتبع الخطوات أدناه لتحديد "مفتاح مساحة عمل ومفتاح مساحة العمل ل Defender لنقطة النهاية"، المطلوب لتكوين الإصدارات السابقة من Windows.

1. من مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender،</a> **حدد الإعدادات** \> **نقاط** \> **النهاية (****ضمن إدارة الجهاز**).

2. ضمن نظام التشغيل **، اختر Windows 7 SP1 و8.1**.

3. انسخ **"مفتاح مساحة** العمل ومفتاح **مساحة العمل** " واحفظهما. سيتم استخدامها لاحقا في العملية.

   :::image type="content" source="images/91b738e4b97c4272fd6d438d8c2d5269.png" alt-text="عملية الboarding" lightbox="images/91b738e4b97c4272fd6d438d8c2d5269.png":::

4. تثبيت وكيل مراقبة Microsoft (MMA).

   يتم دعم MMA حاليا (حتى يناير 2019) على Windows أنظمة التشغيل التالية:

   - خوادم SKUs: Windows Server 2008 SP1 أو أحدث
   - عملة SKUs: Windows 7 SP1 واللاحقة

   يجب تثبيت عامل MMA على Windows الأجهزة. لتثبيت العامل، ستحتاج بعض الأنظمة إلى تنزيل التحديث لتجربة العملاء وبيانات بيانات [](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry) بيانات التشخيص من أجل تجميع البيانات باستخدام MMA. تتضمن إصدارات النظام هذه، ولكن قد لا تقتصر على:

   - Windows 8.1
   - Windows 7
   - Windows Server 2016‏
   - Windows Server 2012 R2
   - Windows Server 2008 R2

   بشكل خاص، Windows 7 SP1، يجب تثبيت التصحيحات التالية:

   - تثبيت [KB4074598](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
   - قم بتثبيت [.NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (أو أي وقت لاحق) **أو** [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework). لا تقوم بتثبيت كليهما على النظام نفسه.

5. إذا كنت تستخدم وكيلا للاتصال بالإنترنت، فشاهد المقطع تكوين إعدادات الوكيل.

بمجرد الانتهاء، من المفترض أن ترى نقاط النهاية المضمنة في المدخل في غضون ساعة.

### <a name="next-generation-protection"></a>حماية الجيل التالي

برنامج الحماية من الفيروسات من Microsoft Defender هو حل مضمن للحماية من البرامج الضارة يوفر حماية الجيل التالي لأجهزة سطح المكتب وأجهزة الكمبيوتر المحمولة الخوادم.

1. في وحدة Microsoft Endpoint Configuration Manager، انتقل إلى **نظرة \> \> عامة حول الأصول والتوافق \> Endpoint Protection نهج** مكافحة البرامج الضارة **واختر إنشاء نهج مكافحة البرامج الضارة**.

   :::image type="content" source="images/9736e0358e86bc778ce1bd4c516adb8b.png" alt-text="نهج مكافحة البرامج الضارة" lightbox="images/9736e0358e86bc778ce1bd4c516adb8b.png":::

2. حدد **عمليات الفحص** المجدولة وإعدادات الفحص والإجراءات الافتراضية والحماية في الوقت الحقيقي وإعدادات الاستثناء والمتقدمة وتجاوز التهديدات وخدمة الحماية السحابية **وتحديثات** معلومات الأمان واختر **موافق**. 

   :::image type="content" source="images/1566ad81bae3d714cc9e0d47575a8cbd.png" alt-text="جزء حماية الجيل التالي1" lightbox="images/1566ad81bae3d714cc9e0d47575a8cbd.png":::

    في بعض الصناعات أو بعض عملاء المؤسسات المحددة قد يكون لديهم احتياجات خاصة حول كيفية تكوين برنامج الحماية من الفيروسات.

    [المسح السريع مقابل الفحص الكامل والفحص المخصص](/windows/security/threat-protection/microsoft-defender-antivirus/scheduled-catch-up-scans-microsoft-defender-antivirus#quick-scan-versus-full-scan-and-custom-scan)

    لمزيد من التفاصيل، راجع أمن Windows [إطار عمل التكوين](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-configuration-framework).
  
    :::image type="content" source="images/cd7daeb392ad5a36f2d3a15d650f1e96.png" alt-text="جزء حماية الجيل التالي2" lightbox="images/cd7daeb392ad5a36f2d3a15d650f1e96.png":::

    :::image type="content" source="images/36c7c2ed737f2f4b54918a4f20791d4b.png" alt-text="جزء حماية الجيل التالي3" lightbox="images/36c7c2ed737f2f4b54918a4f20791d4b.png":::

    :::image type="content" source="images/a28afc02c1940d5220b233640364970c.png" alt-text="جزء حماية الجيل التالي4" lightbox="images/a28afc02c1940d5220b233640364970c.png":::

    :::image type="content" source="images/5420a8790c550f39f189830775a6d4c9.png" alt-text="جزء حماية الجيل التالي5" lightbox="images/5420a8790c550f39f189830775a6d4c9.png":::

    :::image type="content" source="images/33f08a38f2f4dd12a364f8eac95e8c6b.png" alt-text="جزء حماية الجيل التالي6" lightbox="images/33f08a38f2f4dd12a364f8eac95e8c6b.png":::

    :::image type="content" source="images/41b9a023bc96364062c2041a8f5c344e.png" alt-text="جزء حماية الجيل التالي7" lightbox="images/41b9a023bc96364062c2041a8f5c344e.png":::

    :::image type="content" source="images/945c9c5d66797037c3caeaa5c19f135c.png" alt-text="جزء حماية الجيل التالي8" lightbox="images/945c9c5d66797037c3caeaa5c19f135c.png":::

    :::image type="content" source="images/3876ca687391bfc0ce215d221c683970.png" alt-text="جزء حماية الجيل التالي9" lightbox="images/3876ca687391bfc0ce215d221c683970.png":::

3. انقر بضغطة زر الماوس الأيمن فوق نهج مكافحة البرامج الضارة الذي تم إنشاؤه حديثا وحدد **نشر**.

    :::image type="content" source="images/f5508317cd8c7870627cb4726acd5f3d.png" alt-text="جزء حماية الجيل التالي10" lightbox="images/f5508317cd8c7870627cb4726acd5f3d.png":::

4. يمكنك استهداف نهج مكافحة البرامج الضارة الجديد Windows البرامج الضارة وانقر فوق **موافق**.

    :::image type="content" source="images/configmgr-select-collection.png" alt-text="جزء حماية الجيل التالي11" lightbox="images/configmgr-select-collection.png":::

بعد إكمال هذه المهمة، قمت الآن بتكوين برنامج الحماية من الفيروسات لـ Windows Defender.

### <a name="attack-surface-reduction"></a>الحد من سطح الهجوم

تتضمن ركيزة الحد من سطح الهجوم ل Defender for Endpoint مجموعة الميزات المتوفرة ضمن "حماية المخاطر". قواعد تقليل مساحة الهجوم (ASR) والوصول إلى المجلدات الخاضعة للتحكم وحماية الشبكة والحماية من الهجمات.

توفر كل هذه الميزات وضع تدقيق ووضع حظر. في وضع التدقيق، لا يوجد أي تأثير للمستخدم النهائي. كل ما يقوم به هو جمع بيانات بيانات إضافية وجعلها متوفرة في Microsoft 365 Defender الإلكتروني. الهدف من النشر هو نقل عناصر التحكم في الأمان خطوة بخطوة إلى وضع الحظر.

لتعيين قواعد ASR في وضع التدقيق:

1. في وحدة Microsoft Endpoint Configuration Manager، انتقل إلى **نظرة \> \> عامة حول الأصول والتوافق \> Endpoint Protection Windows Defender Exploit Guard** **واختر إنشاء نهج حماية استغلال**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="وحدة Microsoft Endpoint Configuration Manager 0" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. حدد **تقليل مساحة الهجوم**.

3. قم بتعيين القواعد إلى **تدقيق وانقر** فوق **التالي**.

   :::image type="content" source="images/d18e40c9e60aecf1f9a93065cb7567bd.png" alt-text="وحدة Microsoft Endpoint Configuration Manager 1" lightbox="images/d18e40c9e60aecf1f9a93065cb7567bd.png":::

4. تأكد من نهج "حماية استغلال" الجديد بالنقر فوق **التالي**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="وحدة Microsoft Endpoint Configuration Manager 2" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. بعد إنشاء النهج، انقر فوق **إغلاق**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="وحدة Microsoft Endpoint Configuration Manager 3" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. انقر بضغطة زر الماوس الأيمن فوق النهج الذي تم إنشاؤه حديثا واختر **نشر**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="وحدة Microsoft Endpoint Configuration Manager 4" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::

7. قم باستهداف النهج إلى مجموعة Windows التي تم إنشاؤها حديثا وانقر فوق **موافق**.

   :::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="وحدة Microsoft Endpoint Configuration Manager 5" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

بعد إكمال هذه المهمة، قمت الآن بتكوين قواعد ASR بنجاح في وضع التدقيق.

فيما يلي خطوات إضافية للتحقق مما إذا تم تطبيق قواعد ASR بشكل صحيح على نقاط النهاية. (قد يستغرق ذلك بضع دقائق)

1. من مستعرض ويب، <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">انتقل إلى Microsoft 365 Defender</a>.

2. حدد **إدارة التكوين** من القائمة الموجودة على الجانب الأيمن.

3. انقر **فوق الانتقال إلى إدارة سطح الهجوم** في لوحة إدارة سطح الهجوم.

   :::image type="content" source="images/security-center-attack-surface-mgnt-tile.png" alt-text="إدارة سطح الهجوم" lightbox="images/security-center-attack-surface-mgnt-tile.png":::

4. انقر **فوق علامة التبويب** تكوين في تقارير قواعد تقليل مساحة الهجوم. وهو يعرض نظرة عامة حول تكوين قواعد ASR ووضع قواعد ASR على كل جهاز.

   :::image type="content" source="images/f91f406e6e0aae197a947d3b0e8b2d0d.png" alt-text="تقارير قواعد الحد من سطح الهجوم1" lightbox="images/f91f406e6e0aae197a947d3b0e8b2d0d.png":::

5. انقر فوق كل جهاز يعرض تفاصيل تكوين قواعد ASR.

   :::image type="content" source="images/24bfb16ed561cbb468bd8ce51130ca9d.png" alt-text="تقارير قواعد الحد من سطح الهجوم2" lightbox="images/24bfb16ed561cbb468bd8ce51130ca9d.png":::

راجع [تحسين نشر قاعدة ASR واكتشافاتها](/microsoft-365/security/defender-endpoint/configure-machines-asr) للحصول على مزيد من التفاصيل.

#### <a name="set-network-protection-rules-in-audit-mode"></a>تعيين قواعد حماية الشبكة في وضع التدقيق

1. في وحدة Microsoft Endpoint Configuration Manager، انتقل إلى **نظرة \> \> عامة حول الأصول والتوافق \> Endpoint Protection Windows Defender Exploit Guard** **واختر إنشاء نهج حماية استغلال**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="The System Center Configuration Manager1" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. حدد **حماية الشبكة**.

3. قم بتعيين الإعداد إلى **تدقيق وانقر** فوق **التالي**.

   :::image type="content" source="images/c039b2e05dba1ade6fb4512456380c9f.png" alt-text="The System Center Configuration Manager2" lightbox="images/c039b2e05dba1ade6fb4512456380c9f.png":::

4. تأكد من نهج "حماية استغلال" الجديد بالنقر فوق **التالي**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="نهج &quot;حماية استغلال&quot; 1" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. بمجرد إنشاء النهج، انقر فوق **إغلاق**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="نهج &quot;حماية استغلال&quot;2" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. انقر بضغطة زر الماوس الأيمن فوق النهج الذي تم إنشاؤه حديثا واختر **نشر**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Microsoft Endpoint Configuration Manager-1" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::

7. حدد النهج إلى مجموعة Windows التي تم إنشاؤها حديثا واختر **موافق**.

   :::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Microsoft Endpoint Configuration Manager-2" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

بعد إكمال هذه المهمة، قمت الآن بتكوين حماية الشبكة بنجاح في وضع التدقيق.

#### <a name="to-set-controlled-folder-access-rules-in-audit-mode"></a>لتعيين قواعد الوصول إلى المجلدات الخاضعة للتحكم في وضع التدقيق

1. في وحدة Microsoft Endpoint Configuration Manager، انتقل إلى الأصول و **ComplianceOverview** >  >  >  Endpoint Protection **Windows Defender Exploit Guard** ثم اختر **إنشاء نهج حماية استغلال**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="Microsoft Endpoint Configuration Manager-3" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. حدد **الوصول المتحكم به إلى المجلد**.

3. قم بتعيين التكوين إلى **تدقيق وانقر** فوق **التالي**.

   :::image type="content" source="images/a8b934dab2dbba289cf64fe30e0e8aa4.png" alt-text="ال Microsoft Endpoint Configuration Manager-4" lightbox="images/a8b934dab2dbba289cf64fe30e0e8aa4.png":::

4. تأكد من نهج "حماية استغلال" الجديد بالنقر فوق **التالي**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="Microsoft Endpoint Configuration Manager-5" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. بمجرد إنشاء النهج، انقر فوق **إغلاق**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="Microsoft Endpoint Configuration Manager-6" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. انقر بضغطة زر الماوس الأيمن فوق النهج الذي تم إنشاؤه حديثا واختر **نشر**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Microsoft Endpoint Configuration Manager-7" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::


7. قم باستهداف النهج إلى مجموعة Windows التي تم إنشاؤها حديثا وانقر فوق **موافق**.


:::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Microsoft Endpoint Configuration Manager-8" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

لقد قمت الآن بتكوين الوصول إلى المجلدات الخاضعة للتحكم بنجاح في وضع التدقيق.

## <a name="related-topic"></a>موضوع ذو صلة

- [الboarding باستخدام إدارة نقاط النهاية من Microsoft](onboarding-endpoint-manager.md)
