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
ms.openlocfilehash: 244038e4c49801cad59bd9cf8939c47291c5270f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568105"
---
# <a name="set-up-sharepoint-syntex"></a>إعداد SharePoint Syntex

يمكن للمسؤولين <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">استخدام مركز مسؤولي Microsoft 365</a> لإعداد [Microsoft SharePoint Syntex](index.md). 

فكر في ما يلي قبل البدء:

- في أي SharePoint سيتم تمكين معالجة النموذج؟ هل هي كلها، أو بعضها، أو مواقع محددة؟
- ما الذي ستسميه مركز المحتوى الافتراضي؟

يمكنك تغيير الإعدادات بعد الإعداد <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">الأولي في مركز مسؤولي Microsoft 365</a>.

قبل الإعداد، تأكد من التخطيط لأفضل طريقة لإعداد فهم المحتوى وتكوينه في بيئتك. على سبيل المثال، تحتاج إلى اتخاذ القرارات التالية:

- المواقع SharePoint التي تريد تمكين معالجة النموذج فيها - كل هذه المواقع أو بعضها أو مواقع محددة
- اسم مركز المحتوى الخاص بك ومسؤولي

## <a name="requirements"></a>المتطلبات 

> [!NOTE]
> يجب أن يكون لديك أذونات المسؤول SharePoint العام لكي تتمكن من الوصول إلى مركز مسؤولي Microsoft 365 إعداد SharePoint Syntex.

ب أنت مسؤول، يمكنك أيضا إجراء تغييرات على الإعدادات المحددة في أي وقت بعد الإعداد، وفي إعدادات إدارة فهم المحتوى في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365.</a>

إذا كنت تخطط لاستخدام بيئة Power Platform مخصصة، فيجب تثبيت "منشئ [*AI" لتطبيق Project Cortex*](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) في هذه البيئة وتخصيص أرصدة "منشئ [AI](/power-platform/admin/capacity-add-on)" له قبل أن تتمكن من إنشاء نماذج معالجة النماذج.

### <a name="licensing"></a>الترخيص

لاستخدام SharePoint Syntex، يجب أن يكون لدى مؤسستك اشتراك في SharePoint Syntex، ويجب أن يكون لكل مستخدم التراخيص التالية المعينة:

- SharePoint Syntex
- SharePoint Syntex - نوع SPO
- خدمة البيانات الشائعة SharePoint Syntex

لاستخدام معالجة النموذج، تحتاج أيضا إلى أرصدة منشئ AI. إذا كان لديك 300 مستخدم مرخص أو أكثر، يتم توفير تخصيص لأرصدة منشئ AI كل شهر.

للحصول على تفاصيل حول SharePoint Syntex، راجع SharePoint Syntex [الترخيص](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>لإعداد SharePoint Syntex

1. في مركز مسؤولي Microsoft 365، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**إعداد**</a>، ثم اشاهد **مقطع الملفات والمحتوى**.

2. في المقطع **ملفات ومحتوى** ، حدد **أتمتة فهم المحتوى**. لاحظ أن توفر رصيد "منشئ AI" الحالي يظهر في القسم **نظرة** سريعة.<br/>

3. في الصفحة **أتمتة فهم المحتوى** ، **انقر فوق بدء** العمل للسير في عملية الإعداد. <br/>

    > [!div class="mx-imgBorder"]
    > ![ابدأ الإعداد.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. في **الصفحة تكوين** معالجة النماذج، يمكنك اختيار ما إذا كنت تريد السماح للمستخدمين بإنشاء نماذج لمعالجة النماذج في مكتبات مستندات SharePoint معينة. سيتوفر خيار قائمة في شريط مكتبة المستندات لإنشاء نموذج لمعالجة النماذج في  مكتبات المستندات SharePoint التي تم تمكينه فيها.
 
     بالنسبة **إلى SharePoint** التي يجب أن تظهرها مكتبات النماذج لإنشاء نموذج لمعالجة النماذج، يمكنك تحديد:</br>
      - **المكتبات في كل SharePoint لجعلها** متوفرة لجميع المكتبات SharePoint في مؤسستك.</br>
      - **المكتبات في مواقع SharePoint محددة**، ثم حدد المواقع التي تريد جعلها متوفرة فيها أو قم بتحميل قائمة تضم ما يصل إلى 50 موقعا.</br>
      - **لا SharePoint مكتبات** إذا كنت لا تريد جعلها متوفرة لأي مواقع (يمكنك تغيير ذلك بعد الإعداد).

   > [!div class="mx-imgBorder"]
   > ![تكوين خيارات موقع معالجة النموذج.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > لا تؤثر إزالة موقع بعد تضمينه على النماذج الموجودة المطبقة على المكتبات في ذلك الموقع أو القدرة على تطبيق نماذج فهم المستندات على مكتبة. 
    
    إذا تم تكوين بيئات Power Platform متعددة، يمكنك اختيار البيئات التي تريد استخدامها لمعالجة النموذج. (لن يظهر هذا الخيار إذا كان لديك بيئة واحدة فقط.)

    ![تكوين خيارات معالجة النموذج في Power Platform.](../media/content-understanding/setup-power-platform-env.png)

    بالنسبة **لبيئة Power Platform**، يمكنك تحديد:
    - **استخدم البيئة الافتراضية لاستخدام** بيئة Power Platform الافتراضية.
    - **استخدم بيئة مخصصة** لاستخدام بيئة مخصصة. اختر البيئة التي تريد استخدامها من القائمة. ([راجع متطلبات بيئة مخصصة](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    انقر فوق **التالي**.

5. في الصفحة **إنشاء مركز** المحتويات، يمكنك إنشاء موقع SharePoint المحتوى حيث يمكن للمستخدمين إنشاء نماذج فهم المستندات وإدارتها. إذا سبق لك إنشاء مركز محتوى من مركز إدارة SharePoint، سيتم عرض هذه المعلومات هنا، ما عليك سوى تحديد **التالي**.

    1. بالنسبة **إلى اسم الموقع**، اكتب الاسم الذي تريد منحه لموقع مركز المحتوى.
    
    1. **سيعرض عنوان** الموقع عنوان URL لموقعك، استنادا إلى ما حددته لاسم الموقع. إذا كنت تريد تغييره، انقر فوق **تحرير**.

       > [!div class="mx-imgBorder"]
       > ![إنشاء مركز المحتوى.](../media/content-understanding/admin-cu-create-cc.png)</br>

       حدد **التالي**.

6. في **صفحة المراجعة والانتهاء** ، يمكنك النظر إلى الإعداد المحدد واختيار إجراء تغييرات. إذا كنت راضيا عن التحديدات، فحدد **تنشيط**.

7. على صفحة التأكيد، انقر فوق **تم**.

8. سيتم إرجاعك إلى صفحة "أتمتة فهم **المحتوى** ". من هذه الصفحة، يمكنك تحديد **إدارة** من أجل إجراء أي تغييرات على إعدادات التكوين. 

## <a name="assign-licenses"></a>تعيين التراخيص

بعد تكوين SharePoint Syntex، يجب تعيين تراخيص للمستخدمين الذين سيستخدمون أي SharePoint Syntex أخرى.

لتعيين التراخيص:

1. في مركز مسؤولي Microsoft 365، ضمن **المستخدمون**، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**المستخدمون النشطون**</a>.

2. حدد المستخدمين الذين تريد ترخيصهم، واختر **إدارة تراخيص المنتجات**.

3. اختر **تطبيقات** من القائمة المنسدلة.

4. حدد **إظهار التطبيقات SharePoint Syntex**. ضمن **التطبيقات**، تأكد من تحديد خدمة البيانات الشائعة SharePoint Syntex و SharePoint Syntex و SharePoint Syntex **- نوع SPO**.

    > [!div class="mx-imgBorder"]
    > ![SharePoint Syntex التراخيص في مركز مسؤولي Microsoft 365.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. انقر فوق **حفظ التغييرات**.

## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على نموذج معالجة النماذج](/ai-builder/form-processing-model-overview)

[خطوة بخطوة: كيفية إنشاء نموذج فهم المستند (فيديو)](https://www.youtube.com/watch?v=DymSHObD-bg)

[إنشاء بيئات وإدارتها في مركز إدارة Power Platform](/power-platform/admin/create-environment)
