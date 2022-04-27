---
title: تعيين أذونات eDiscovery في مدخل توافق Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5b9a067b-9d2e-4aa5-bb33-99d8c0d0b5d7
description: تعيين الأذونات المطلوبة لتنفيذ المهام ذات الصلة ب eDiscovery باستخدام مدخل توافق Microsoft Purview.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: e764aae4313a8e5d4dfc402e4c1f87eb8c1a5bbb
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090502"
---
# <a name="assign-ediscovery-permissions-in-the-compliance-portal"></a>تعيين أذونات eDiscovery في مدخل التوافق

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

إذا كنت تريد أن يستخدم الأشخاص أيا من [الأدوات ذات الصلة ب eDiscovery](ediscovery.md) في مدخل توافق Microsoft Purview، يجب عليك تعيين الأذونات المناسبة لهم. أسهل طريقة للقيام بذلك هي إضافة الشخص مجموعة الأدوار المناسبة في صفحة **الأذونات** في مركز التوافق. يصف هذا الموضوع الأذونات المطلوبة لتنفيذ مهام eDiscovery.
  
تسمى مجموعة الأدوار الأساسية المتعلقة ب eDiscovery في مدخل التوافق **eDiscovery Manager**. هناك مجموعتان فرعيتان ضمن مجموعة الأدوار هذه.
  
- **eDiscovery Manager** - يمكن لمدير eDiscovery استخدام أدوات البحث eDiscovery للبحث في مواقع المحتوى في المؤسسة، وتنفيذ إجراءات مختلفة متعلقة بالبحث مثل معاينة نتائج البحث وتصديرها. يمكن للأعضاء أيضا إنشاء الحالات وإدارتها في Microsoft Purview eDiscovery (قياسي) وMicrosoft Purview eDiscovery (Premium)، وإضافة أعضاء وإزالتها إلى حالة ما، وإنشاء عمليات احتجاز حالة، وتشغيل عمليات البحث المقترنة بالحالة، والوصول إلى بيانات الحالة. يمكن لمديري eDiscovery الوصول إلى الحالات التي يقومون بإنشائها وإدارتها فقط. لا يمكنهم الوصول إلى الحالات التي أنشأها مديرو eDiscovery الآخرون أو إدارتها.
  
- **مسؤول eDiscovery** - مسؤول eDiscovery هو عضو في مجموعة أدوار eDiscovery Manager، ويمكنه تنفيذ نفس المهام المتعلقة بالبحث في المحتوى وإدارة الحالة التي يمكن أن يقوم بها مدير eDiscovery. بالإضافة إلى ذلك، يمكن لمسؤول eDiscovery:
  
  - الوصول إلى جميع الحالات المدرجة في صفحات **eDiscovery (قياسي)** **وeDiscovery (Premium)** في مدخل التوافق.

  - الوصول إلى بيانات حالة الأحرف في eDiscovery (Premium) لأي حالة في المؤسسة.
  
  - إدارة أي حالة eDiscovery بعد أن يضيفوا أنفسهم كعضو في الحالة.
  
  - إزالة الأعضاء من حالة eDiscovery. يمكن فقط لمسؤول eDiscovery إزالة الأعضاء من حالة. لا يمكن للمستخدمين الأعضاء في المجموعة الفرعية eDiscovery Manager إزالة الأعضاء من حالة ما، حتى لو أنشأ المستخدم الحالة.
  
  لأسباب تتعلق برغبتك في أن يكون مسؤولو eDiscovery في مؤسستك، راجع [المزيد من المعلومات](#more-information).

> [!NOTE]
> لتحليل بيانات المستخدم باستخدام eDiscovery (Premium)، يجب تعيين ترخيص Office 365 E5 أو ترخيص Microsoft 365 E5 للمستخدم (الوصي على البيانات). بدلا من ذلك، يمكن تعيين ترخيص Office 365 E1 التوافق في Microsoft 365 E5 أو Office 365 أو ترخيص Microsoft 365 E3 للمستخدمين الذين لديهم ترخيص التوافق في Microsoft 365 E5 أو Microsoft 365 eDiscovery ووظيفة التدقيق الإضافية. لا يحتاج المسؤولون أو مسؤولو الامتثال أو الموظفون القانونيون الذين تم تعيينهم إلى الحالات كأعضاء ويستخدمون eDiscovery (Premium) لجمع البيانات وعرضها وتحليلها إلى ترخيص E5. لمزيد من المعلومات حول ترخيص eDiscovery (Premium)، راجع [الاشتراكات والترخيص في eDiscovery (Premium)](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>قبل تعيين الأذونات

- يجب أن تكون عضوا في مجموعة دور إدارة المؤسسة أو أن يتم تعيين دور "إدارة الدور" لتعيين أذونات eDiscovery في مدخل التوافق.

- يمكنك استخدام [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) cmdlet في Security & Compliance Center PowerShell لإضافة مجموعة أمان ممكنة للبريد كعضو في المجموعة الفرعية eDiscovery Managers في مجموعة دور eDiscovery Manager. ومع ذلك، لا يمكنك إضافة مجموعة أمان ممكنة للبريد إلى المجموعة الفرعية لمسؤولي eDiscovery. للحصول على التفاصيل، راجع [المزيد من المعلومات](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>تعيين أذونات مسؤول eDiscovery

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق</a> وسجل الدخول باستخدام حساب يمكنه تعيين الأذونات.
  
2. في الجزء الأيمن، حدد **"أذونات**".

3. في صفحة **"الأذونات & Roles** "، ضمن **"مركز التوافق**"، انقر فوق **"Roles**".

4. في صفحة **أدوار مركز التوافق** ، حدد **eDiscovery Manager**.
  
5. في صفحة **القائمة المنبثقة eDiscovery Manager** ، قم بأحد الإجراءات التالية استنادا إلى أذونات eDiscovery التي تريد تعيينها.
  
    **لجعل المستخدم مدير eDiscovery:** إلى جانب **eDiscovery Manager**، حدد **Edit**. في صفحة معالج **اختيار eDiscovery Manager** ، انقر فوق !["إضافة أيقونة".](../media/ITPro-EAC-AddIcon.gif) **إضافة**. حدد المستخدم (أو المستخدمين) الذي تريد إضافته كمدير eDiscovery، ثم حدد **"إضافة**". عند الانتهاء من إضافة مستخدمين، حدد **"تم**". بعد ذلك، في صفحة معالج **Editing Choose eDiscovery Manager** ، حدد **"حفظ** " لحفظ التغييرات في عضوية eDiscovery Manager.
  
    **لجعل المستخدم مسؤول eDiscovery:** إلى جانب **مسؤول eDiscovery**، حدد **"تحرير**". في الصفحة **"اختيار مسؤول eDiscovery** "، انقر فوق !["إضافة أيقونة".](../media/ITPro-EAC-AddIcon.gif) **إضافة**. حدد المستخدم (أو المستخدمين) الذي تريد إضافته **كمسؤول eDiscovery**، ثم  **أضف**. عند الانتهاء من إضافة مستخدمين، حدد **"تم**". بعد ذلك، في صفحة معالج " **تحرير اختيار مسؤول eDiscovery** "، حدد **"حفظ** " لحفظ التغييرات في عضوية مسؤول eDiscovery.
  
> [!NOTE]
> يمكنك أيضا استخدام **Add-eDiscoveryCaseAdmin** cmdlet لجعل المستخدم مسؤول eDiscovery. ومع ذلك، يجب تعيين دور إدارة الحالة للمستخدم قبل أن تتمكن من استخدام أمر cmdlet هذا لجعله مسؤول eDiscovery. لمزيد من المعلومات، راجع [Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin).
  
في صفحة **"الأذونات** " في مدخل التوافق، يمكنك أيضا تعيين الأذونات المتعلقة ب eDiscovery للمستخدمين عن طريق إضافتها إلى مجموعات أدوار "مسؤول التوافق" و"إدارة المؤسسة" و"المراجع". للحصول على وصف لأدوار RBAC المتعلقة ب eDiscovery المعينة لكل مجموعة من مجموعات الأدوار هذه، راجع [أدوار RBAC المتعلقة ب eDiscovery](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>أدوار RBAC المتعلقة ب eDiscovery

يسرد الجدول التالي أدوار RBAC المتعلقة ب eDiscovery في مدخل التوافق، ويشير إلى مجموعات الأدوار المضمنة التي يتم تعيين كل دور إليها بشكل افتراضي.
  
| دور | مسؤول التوافق | مسؤول & eDiscovery Manager | إدارة المؤسسة | المراجع |
|:-----|:-----:|:-----:|:-----:|:-----:|
|إدارة الحالة <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> |
|اتصال <br/> | <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> | <br/> |
|البحث عن التوافق <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> |
|القيم <br/> | <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> | <br/> |
|التصدير <br/> | <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> | <br/> |
|عقد <br/>  |![علامة الاختيار.](../media/checkmark.png) <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> |
|معاينه <br/>  | <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> | <br/> |
|مراجعة <br/>  | <br/> |![علامة الاختيار.](../media/checkmark.png) <br/> | <br/> |![علامة اختيار](../media/checkmark.png) <br/> |
|فك تشفير RMS <br/>  ||![علامة اختيار](../media/checkmark.png) <br/> |||
|البحث والإزالة <br/> | <br/> | <br/> |![علامة اختيار](../media/checkmark.png)<br/> | <br/> |
||||||
  
تصف الأقسام التالية كل من أدوار RBAC المتعلقة ب eDiscovery المدرجة في الجدول السابق.

### <a name="case-management"></a>إدارة الحالة

يتيح هذا الدور للمستخدمين إنشاء حالات eDiscovery (قياسي) وeDiscovery (Premium) وتحريرها وحذفها والتحكم فيها في مدخل التوافق. كما هو موضح سابقا، يجب تعيين دور إدارة الحالة للمستخدم قبل أن تتمكن من استخدام **Add-eDiscoveryCaseAdmin** cmdlet لجعله مسؤول eDiscovery.

لمزيد من المعلومات، اطلع على:

- [بدء استخدام eDiscovery (قياسي)](get-started-core-ediscovery.md)

- [بدء استخدام eDiscovery (Premium)](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>اتصال

يتيح هذا الدور للمستخدمين إدارة جميع الاتصالات مع أمناء الحفظ المحددين في حالة eDiscovery (Premium). يتضمن ذلك إنشاء إعلامات الاحتجاز، والاحتفاظ بالتذكيرات، والتصعيدات إلى الإدارة. يمكن للمستخدم أيضا تعقب إقرار الوصي بإشعارات الاحتجاز وإدارة الوصول إلى مدخل الوصي الذي يستخدمه كل أمين لتعقب الاتصالات للحالات التي تم تحديدها على أنها وصي.

لمزيد من المعلومات، راجع ["العمل مع الاتصالات" في eDiscovery (Premium).](managing-custodian-communications.md)

### <a name="compliance-search"></a>البحث عن التوافق

يتيح هذا الدور للمستخدمين تشغيل أداة البحث عن المحتوى في مدخل التوافق للبحث في علب البريد والمجلدات العامة ومواقع SharePoint Online ومواقع OneDrive for Business ومحادثات Skype for Business ومجموعات Microsoft 365 ومجموعات مجموعات Microsoft Teams Yammer. يسمح هذا الدور للمستخدم بالحصول على تقدير لنتائج البحث وإنشاء تقارير التصدير، ولكن هناك حاجة إلى أدوار أخرى لبدء إجراءات البحث في المحتوى مثل معاينة نتائج البحث أو تصديرها أو حذفها.

في البحث في المحتوى وeDiscovery (قياسي)، يمكن للمستخدمين الذين تم تعيين دور "البحث في التوافق" ولكن ليس لديهم دور المعاينة معاينة نتائج البحث الذي تم فيه بدء إجراء المعاينة من قبل مستخدم تم تعيين دور المعاينة له. يمكن للمستخدم الذي ليس له دور المعاينة معاينة النتائج لمدة تصل إلى أسبوعين بعد إنشاء إجراء المعاينة الأولية.

وبالمثل، يمكن للمستخدمين في البحث في المحتوى وeDiscovery (قياسي) الذين تم تعيين دور البحث التوافقي ولكن ليس لديهم دور التصدير تنزيل نتائج البحث الذي بدأ فيه إجراء التصدير من قبل مستخدم تم تعيين دور التصدير له. يمكن للمستخدم الذي ليس له دور التصدير تنزيل نتائج البحث لمدة تصل إلى أسبوعين بعد إنشاء إجراء التصدير الأولي. بعد ذلك، لا يمكنهم تنزيل النتائج إلا إذا قام شخص ما بدور التصدير بإعادة تشغيل التصدير.

لا تنطبق فترة السماح لمدة أسبوعين لمعاينة نتائج البحث وتصديرها (بدون أدوار البحث والتصدير المقابلة) على eDiscovery (Premium). يجب تعيين أدوار المعاينة والتصدير للمستخدمين لمعاينة المحتوى وتصديره في eDiscovery (Premium).

### <a name="custodian"></a>القيم

يتيح هذا الدور للمستخدمين تحديد وإدارة أمناء حالات eDiscovery (Premium) واستخدام المعلومات من Azure Active Directory ومصادر أخرى للعثور على مصادر البيانات المرتبطة بالأمناء. يمكن للمستخدم إقران مصادر بيانات أخرى مثل علب البريد ومواقع SharePoint Teams مع أمناء الحفظ في حالة ما. يمكن للمستخدم أيضا وضع احتجاز قانوني على مصادر البيانات المرتبطة بأمناء الحفظ للحفاظ على المحتوى في سياق الحالة.

لمزيد من المعلومات، راجع [العمل مع أمناء الحفظ في eDiscovery (Premium).](managing-custodians.md)

### <a name="export"></a>التصدير

يتيح الدور للمستخدمين تصدير نتائج البحث في المحتوى إلى كمبيوتر محلي. كما يتيح لهم إعداد نتائج البحث للتحليل في eDiscovery (Premium).

لمزيد من المعلومات حول تصدير نتائج البحث، راجع [تصدير نتائج البحث من مدخل توافق Microsoft Purview](export-search-results.md).

### <a name="hold"></a>عقد

يتيح هذا الدور للمستخدمين وضع المحتوى قيد الاحتجاز في علب البريد والمجلدات العامة والمواقع والمحادثات Skype for Business ومجموعات Microsoft 365. عندما يكون المحتوى قيد الاحتجاز، لا يزال بإمكان مالكي المحتوى تعديل المحتوى الأصلي أو حذفه، ولكن سيتم الاحتفاظ بالمحتوى حتى تتم إزالة قائمة الاحتجاز أو حتى تنتهي مدة الاحتجاز.

لمزيد من المعلومات حول قوائم الاحتجاز، راجع:

- [إنشاء قائمة احتجاز في eDiscovery (قياسي)](create-ediscovery-holds.md) 

- [إنشاء قائمة احتجاز في eDiscovery (Premium)](add-custodians-to-case.md)

### <a name="preview"></a>معاينه

يتيح هذا الدور للمستخدمين عرض قائمة بالعناصر التي تم إرجاعها من البحث في المحتوى. كما يمكنهم فتح كل عنصر وعرضه من القائمة لعرض محتوياته.

### <a name="review"></a>مراجعة

يتيح هذا الدور للمستخدمين الوصول إلى مجموعات [المراجعة في eDiscovery (Premium).](overview-ediscovery-20.md) يمكن للمستخدمين الذين تم تعيين هذا الدور رؤية قائمة الحالات وفتحها على صفحة **eDiscovery > Advanced** في مدخل التوافق الذي هم أعضاء فيه. بعد وصول المستخدم إلى حالة eDiscovery (Premium)، يمكنه تحديد **مجموعات المراجعة** للوصول إلى بيانات الحالة. لا يسمح هذا الدور للمستخدم بمعاينة نتائج البحث في مجموعة مقترنة بالحالة أو القيام بمهام أخرى للبحث أو إدارة الحالة. يمكن للمستخدمين الذين لديهم هذا الدور الوصول إلى البيانات في مجموعة مراجعة فقط.

### <a name="rms-decrypt"></a>فك تشفير RMS

يتيح هذا الدور للمستخدمين عرض رسائل البريد الإلكتروني المحمية بحقوق عند معاينة نتائج البحث وتصدير رسائل البريد الإلكتروني المحمية بحقوق غير المشفرة. يتيح هذا الدور أيضا للمستخدمين عرض (وتصدير) ملف مشفر [باستخدام تقنية تشفير Microsoft](encryption.md) عند إرفاق الملف المشفر برسالة بريد إلكتروني مضمنة في نتائج بحث eDiscovery. بالإضافة إلى ذلك، يتيح هذا الدور للمستخدمين مراجعة مرفقات البريد الإلكتروني المشفرة التي تتم إضافتها إلى مجموعة مراجعة في eDiscovery (Premium) والاستعلام عنها. لمزيد من المعلومات حول فك التشفير في eDiscovery، راجع [فك التشفير في أدوات eDiscovery Microsoft 365](ediscovery-decryption.md).

### <a name="search-and-purge"></a>البحث والإزالة

يتيح هذا الدور للمستخدمين تنفيذ الإزالة المجمعة للبيانات المطابقة لمعايير البحث في المحتوى. لمزيد من المعلومات، راجع [البحث عن رسائل البريد الإلكتروني وحذفها في مؤسستك](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>إضافة مجموعات الأدوار كأعضاء في حالات eDiscovery

يمكنك إضافة مجموعات الأدوار كأعضاء في حالات eDiscovery (قياسي) وeDiscovery (Premium) بحيث يمكن لأعضاء مجموعات الأدوار الوصول إلى المهام وتنفيذها في الحالات المعينة. تحدد الأدوار المعينة إلى مجموعة الأدوار ما يمكن لأعضاء مجموعة الأدوار القيام به. ثم تتيح إضافة مجموعة أدوار كعضو في الحالة للأعضاء الوصول إلى هذه المهام وتنفيذها في حالة معينة. لمزيد من المعلومات حول إضافة مجموعات الأدوار كأعضاء في الحالات، راجع:

- [بدء استخدام eDiscovery (قياسي)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

- [إضافة أعضاء أو إزالتهم من حالة eDiscovery (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

مع وضع ذلك في الاعتبار، من المهم معرفة أنه إذا تمت إضافة دور أو إزالته من مجموعة أدوار، فستتم إزالة مجموعة الأدوار هذه تلقائيا كعضو في أي حالة تكون مجموعة الأدوار عضوا فيها. والسبب في ذلك هو حماية مؤسستك من توفير أذونات إضافية عن غير قصد لأعضاء حالة ما. وبالمثل، إذا تم حذف مجموعة أدوار، فستتم إزالتها من جميع الحالات التي كانت عضوا فيها.

قبل إضافة أدوار أو إزالتها إلى مجموعة أدوار قد تكون عضوا في حالة eDiscovery، يمكنك تشغيل الأوامر التالية في [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) للحصول على قائمة الحالات التي تكون مجموعة الأدوار عضوا فيها. بعد تحديث مجموعة الأدوار، يمكنك إضافة مجموعة الأدوار مرة أخرى كعضو في تلك الحالات.

### <a name="get-a-list-of-ediscovery-standard-cases-a-role-group-is-assigned-to"></a>الحصول على قائمة بحالات eDiscovery (القياسية) التي تم تعيين مجموعة أدوار لها

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-ediscovery-premium-cases-a-role-group-is-assigned-to"></a>الحصول على قائمة بحالات eDiscovery (Premium) التي تم تعيين مجموعة أدوار لها

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>معلومات إضافية

- **لماذا إنشاء مسؤول eDiscovery؟** كما هو موضح سابقا، مسؤول eDiscovery هو عضو في مجموعة أدوار eDiscovery Manager الذي يمكنه عرض جميع حالات eDiscovery والوصول إليها في مؤسستك. هذه القدرة على الوصول إلى جميع حالات eDiscovery لها غرضان مهمان:

  - إذا غادر شخص هو العضو الوحيد في حالة eDiscovery مؤسستك، فلن يتمكن أي شخص (بما في ذلك أعضاء مجموعة دور إدارة المؤسسة أو عضو آخر في مجموعة أدوار eDiscovery Manager) من الوصول إلى حالة eDiscovery هذه لأنهم ليسوا عضوا في حالة ما. في هذه الحالة، لن تكون هناك طريقة للوصول إلى البيانات في هذه الحالة. ولكن نظرا لأن مسؤول eDiscovery يمكنه الوصول إلى جميع حالات eDiscovery في المؤسسة، يمكنه عرض الحالة وإضافة نفسه أو مدير eDiscovery آخر كعضو في الحالة.

  - نظرا لأن مسؤول eDiscovery يمكنه عرض جميع حالات eDiscovery (القياسية) وeDiscovery (Premium) والوصول إليها، يمكنهم تدقيق جميع الحالات وعمليات البحث المرتبطة بالامتثال والإشراف عليها. يمكن أن يساعد هذا في منع أي إساءة استخدام لعمليات البحث عن التوافق أو حالات eDiscovery. ولأن مسؤولي eDiscovery يمكنهم الوصول إلى المعلومات الحساسة المحتملة في نتائج البحث عن التوافق، يجب عليك تحديد عدد الأشخاص الذين هم مسؤولو eDiscovery.

- **هل يمكنني إضافة مجموعة كعضو في مجموعة أدوار eDiscovery Manager؟** كما هو موضح سابقا، يمكنك إضافة مجموعة أمان ممكنة للبريد كعضو في المجموعة الفرعية eDiscovery Managers في مجموعة أدوار eDiscovery Manager باستخدام **cmdlet Add-RoleGroupMember** في Security & Compliance Center PowerShell. على سبيل المثال، يمكنك تشغيل الأمر التالي لإضافة مجموعة أمان ممكنة للبريد إلى مجموعة أدوار eDiscovery Manager. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange مجموعات التوزيع مجموعات Microsoft 365 غير مدعومة. يجب استخدام مجموعة أمان ممكنة للبريد، والتي يمكنك إنشاؤها في Exchange Online PowerShell عن طريق تشغيل `New-DistributionGroup -Type Security`. يمكنك أيضا إنشاء مجموعة أمان ممكنة للبريد (وإضافة أعضاء) في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> أو في [مركز مسؤولي Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). قد يستغرق الأمر ما يصل إلى 60 دقيقة بعد إنشائها لكي تتوفر مجموعة أمان جديدة ممكنة للبريد لإضافتها إلى مجموعة أدوار eDiscovery Managers.

    كما ذكر سابقا، لا يمكنك جعل مجموعة أمان ممكنة للبريد مسؤول eDiscovery باستخدام **Add-eDiscoveryCaseAdmin** cmdlet في Security & Compliance Center PowerShell. يمكنك فقط إضافة مستخدمين فرديين كمسؤولي eDiscovery.

    لا يمكنك أيضا إضافة مجموعة أمان ممكنة للبريد كعضو في حالة ما.
