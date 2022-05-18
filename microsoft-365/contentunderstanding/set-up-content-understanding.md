---
title: إعداد SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- admindeeplinkMAC
search.appverid: MET150
ms.localizationpriority: high
description: إعداد SharePoint Syntex
ms.openlocfilehash: 97d12527667de1583f787844da11a4ad875f34ba
ms.sourcegitcommit: 37111bc0c5a6cc4690f7144a019bbff11d44858f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/18/2022
ms.locfileid: "65463132"
---
# <a name="set-up-sharepoint-syntex"></a>إعداد SharePoint Syntex

يمكن للمسؤولين استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> لإعداد [Microsoft SharePoint Syntex](index.md). 

ضع في اعتبارك ما يلي قبل البدء:

- في أي مواقع SharePoint ستمكن معالجة النماذج؟ هل هي كلها أو بعضها أو مواقع محددة؟
- ما الذي ستقوم بتسمية مركز المحتوى الافتراضي الخاص بك؟

يمكنك تغيير الإعدادات بعد الإعداد الأولي في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>.

قبل الإعداد، تأكد من التخطيط للحصول على أفضل طريقة لإعداد فهم المحتوى وتكوينه في بيئتك. على سبيل المثال، تحتاج إلى اتخاذ القرارات التالية:

- مواقع SharePoint التي تريد تمكين معالجة النماذج فيها - كل منها أو بعضها أو مواقع محددة
- اسم مركز المحتوى والمسؤولين فيه

## <a name="requirements"></a>الاحتياجات 

> [!NOTE]
> يجب أن يكون لديك أذونات المسؤول العام أو المسؤول SharePoint لتتمكن من الوصول إلى مركز مسؤولي Microsoft 365 وإعداد SharePoint Syntex.

بصفتك مسؤولا، يمكنك أيضا إجراء تغييرات على الإعدادات المحددة في أي وقت بعد الإعداد، وفي جميع أنحاء إعدادات إدارة فهم المحتوى في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>.

### <a name="custom-power-platform-environments"></a>بيئات Power Platform المخصصة

إذا كنت تخطط لاستخدام بيئة Power Platform مخصصة، فيجب تثبيت *الذكاء الاصطناعي Builder لتطبيق Project Cortex* في هذه البيئة. راجع [إدارة تطبيقات Dynamics 365](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) للحصول على التفاصيل وابحث عن *الذكاء الاصطناعي Builder لتطبيق Project Cortex* في قائمة تطبيقات Dynamics 365.

تحتاج أيضا إلى [تخصيص أرصدة الذكاء الاصطناعي Builder](/power-platform/admin/capacity-add-on) إلى البيئة المخصصة قبل أن تتمكن من إنشاء نماذج معالجة النماذج. 

عند استخدام بيئة مخصصة، يجب تعيين دور أمان Environment Maker إلى منشئي النماذج، كما يجب تعيين دور أمان المستخدم الأساسي للمستخدم. راجع [تعيين دور أمان لمستخدم](/power-platform/admin/assign-security-roles) للحصول على مزيد من المعلومات.

يجب أن يكون المستخدمون الذين يقومون بإنشاء نماذج في [موقع مركز المحتوى](/microsoft-365/contentunderstanding/create-a-content-center) أعضاء في الموقع. يجب أن يكون المستخدمون الذين يقومون بإنشاء نماذج محليا خارج مركز المحتوى مالكي مواقع لتلك المواقع.

### <a name="licensing"></a>الترخيص

لاستخدام SharePoint Syntex، يجب أن يكون لدى مؤسستك اشتراك في SharePoint Syntex، ويجب أن يكون لكل مستخدم التراخيص التالية المعينة:

- بناء جملة SharePoint
- SharePoint Syntex - نوع SPO
- خدمة البيانات المشتركة SharePoint Syntex

لاستخدام معالجة النماذج، تحتاج أيضا إلى أرصدة الذكاء الاصطناعي Builder. إذا كان لديك 300 مستخدم مرخص أو أكثر، يتم تخصيص أرصدة الذكاء الاصطناعي Builder كل شهر.

للحصول على تفاصيل حول ترخيص SharePoint Syntex، راجع [ترخيص SharePoint Syntex](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>لإعداد SharePoint Syntex

1. في مركز مسؤولي Microsoft 365، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**"إعداد**</a>"، ثم اعرض قسم "**الملفات والمحتوى**".

2. في قسم " **الملفات والمحتوى** "، حدد **"أتمتة فهم المحتوى**". لاحظ أن توفر رصيد الذكاء الاصطناعي Builder الحالي يظهر في قسم **نظرة سريعة** .<br/>

3. في صفحة **"أتمتة فهم المحتوى** "، انقر فوق **"بدء الاستخدام"** لتصفح عملية الإعداد. <br/>

    > [!div class="mx-imgBorder"]
    > ![بدء الإعداد.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. في صفحة **تكوين معالجة النماذج**، يمكنك اختيار ما إذا كنت تريد السماح للمستخدمين بإنشاء نماذج معالجة النماذج في مكتبات مستندات SharePoint معينة. سيتوفر خيار قائمة في شريط مكتبة المستندات **لإنشاء نموذج معالجة نموذج** في مكتبات المستندات SharePoint التي تم تمكينه فيها.
 
     بالنسبة إلى **مكتبات SharePoint التي يجب أن تظهر خيار إنشاء نموذج معالجة نموذج**، يمكنك تحديد:</br>
      - **المكتبات في كافة المواقع SharePoint** لتوفيرها لكافة مكتبات SharePoint في مؤسستك.</br>
      - **المكتبات في مواقع SharePoint المحددة**، ثم حدد المواقع التي تريد توفيرها فيها أو قم بتحميل قائمة تضم ما يصل إلى 50 موقعا.</br>
      - **لا SharePoint مكتبات** إذا كنت لا تريد إتاحتها لأي مواقع (يمكنك تغيير هذا بعد الإعداد).

   > [!div class="mx-imgBorder"]
   > ![تكوين خيارات موقع معالجة النماذج.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > لا تؤثر إزالة موقع بعد تضمينه على النماذج الموجودة المطبقة على المكتبات في هذا الموقع أو القدرة على تطبيق نماذج فهم المستندات على مكتبة. 
    
    إذا كانت لديك بيئات Power Platform متعددة تم تكوينها، يمكنك اختيار بيئات تريد استخدامها مع معالجة النماذج. (لن يظهر هذا الخيار إذا كانت لديك بيئة واحدة فقط.)

    ![تكوين خيارات Power Platform لمعالجة النماذج.](../media/content-understanding/setup-power-platform-env.png)

    بالنسبة **لبيئة Power Platform**، يمكنك تحديد:
    - **استخدم البيئة الافتراضية** لاستخدام بيئة Power Platform الافتراضية.
    - **استخدم بيئة مخصصة** لاستخدام بيئة مخصصة. اختر البيئة التي تريد استخدامها من القائمة. ([راجع متطلبات بيئة مخصصة](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    انقر فوق **التالي**.

5. في الصفحة **"إنشاء مركز المحتويات**"، يمكنك إنشاء موقع مركز محتوى SharePoint حيث يمكن للمستخدمين إنشاء نماذج فهم المستندات وإدارتها. إذا قمت مسبقا بإنشاء مركز محتوى من مركز إدارة SharePoint، فسيتم عرض هذه المعلومات هنا ويمكنك فقط تحديد **"التالي**".

    1. بالنسبة **لاسم الموقع**، اكتب الاسم الذي تريد منحه لموقع مركز المحتوى.
    
    1. سيظهر **عنوان الموقع** عنوان URL لموقعك، استنادا إلى ما حددته لاسم الموقع. إذا كنت تريد تغييره، فانقر فوق **"تحرير**".

       > [!div class="mx-imgBorder"]
       > ![إنشاء مركز محتوى.](../media/content-understanding/admin-cu-create-cc.png)</br>

       حدد **التالي**.

6. في صفحة **المراجعة والانتهاء** ، يمكنك إلقاء نظرة على الإعداد المحدد واختيار إجراء التغييرات. إذا كنت راضيا عن التحديدات، فحدد **"تنشيط**".

7. في صفحة التأكيد، انقر فوق **"تم**".

8. سيتم إرجاعك إلى صفحة **"أتمتة فهم المحتوى** ". من هذه الصفحة، يمكنك تحديد **"إدارة** " لإجراء أي تغييرات على إعدادات التكوين. 

## <a name="assign-licenses"></a>تعيين التراخيص

بمجرد تكوين SharePoint Syntex، يجب تعيين تراخيص للمستخدمين الذين سيستخدمون أي ميزات SharePoint Syntex.

لتعيين التراخيص:

1. في مركز مسؤولي Microsoft 365، ضمن **"المستخدمون**"، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**"المستخدمون النشطون**</a>".

2. حدد المستخدمين الذين تريد ترخيصهم، واختر **"إدارة تراخيص المنتجات**".

3. اختر **التطبيقات** من القائمة المنسدلة.

4. حدد **"إظهار التطبيقات SharePoint Syntex**". ضمن **"التطبيقات**"، تأكد من تحديد **"خدمة البيانات الشائعة" SharePoint Syntex** **SharePoint Syntex** SharePoint Syntex **- نوع SPO**.

    > [!div class="mx-imgBorder"]
    > ![SharePoint Syntex التراخيص في مركز مسؤولي Microsoft 365.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. انقر فوق **حفظ التغييرات**.

## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على نموذج معالجة النموذج](/ai-builder/form-processing-model-overview)

[خطوة بخطوة: كيفية إنشاء نموذج فهم المستندات (فيديو)](https://www.youtube.com/watch?v=DymSHObD-bg)

[إنشاء بيئات وإدارتها في مركز إدارة Power Platform](/power-platform/admin/create-environment)
