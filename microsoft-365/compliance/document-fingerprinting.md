---
title: بصمات أصابع المستند
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
search.appverid: MET150
ms.service: exchange-online
ms.collection: M365-security-compliance
ms.localizationpriority: medium
description: يتعامل عمال المعلومات في مؤسستك مع أنواع عديدة من المعلومات الحساسة خلال يوم نموذجي. تسهل عملية أخذ بصمات الأصابع للمستند من حماية هذه المعلومات من خلال تحديد النماذج القياسية المستخدمة في مؤسستك. يصف هذا الموضوع المفاهيم وراء بصمات أصابع المستند وكيفية إنشاء واحدة باستخدام PowerShell.
ms.openlocfilehash: cd75fe8ec8f4c727f86689cd3a46f331e71afdad
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63567120"
---
# <a name="document-fingerprinting"></a>بصمات أصابع المستند

يتعامل عمال المعلومات في مؤسستك مع أنواع عديدة من المعلومات الحساسة خلال يوم نموذجي. في مركز توافق &amp; الأمان، تسهل لك عملية أخذ بصمات الأصابع للمستندات حماية هذه المعلومات من خلال تحديد النماذج القياسية المستخدمة في مؤسستك. يصف هذا الموضوع المفاهيم وراء بصمات أصابع المستند وكيفية إنشاء واحدة باستخدام PowerShell.

## <a name="basic-scenario-for-document-fingerprinting"></a>السيناريو الأساسي لبصمات الأصابع في المستند

إن بصمات الأصابع في المستند هي ميزة منع فقدان البيانات (DLP) تقوم بتحويل نموذج قياسي إلى نوع معلومات حساسة، يمكنك استخدامها في قواعد سياسات DLP. على سبيل المثال، يمكنك إنشاء بصمة إصبع المستند استنادا إلى قالب براءة اختراع فارغ، ثم إنشاء نهج DLP يكشف عن كل قوالب براءات الاختراع الصادرة وتحظرها مع تعبئة المحتوى الحساس. بشكل اختياري، يمكنك إعداد تلميحات [](use-notifications-and-policy-tips.md) النهج لإعلام المرسلين بأنه قد يتم إرسال معلومات حساسة، ويجب أن يتحقق المرسل من أن المستلمين مؤهلون لتلقي براءات الاختراع. تعمل هذه العملية مع أي نماذج مستندة إلى نص مستخدمة في مؤسستك. تتضمن الأمثلة الإضافية للنماذج التي يمكنك تحميلها ما يلي:

- نماذج الحكومة
- نماذج توافق قانون قابلية النقل والمسؤولية في التأمين الصحي (HIPAA)
- نماذج معلومات الموظفين لأقسام الموارد البشرية
- النماذج المخصصة التي تم إنشاؤها خصيصا لمنظمتك

وبشكل مثالي، فإن مؤسستك لديها بالفعل ممارسة تجارية منشأ لها وهي استخدام نماذج معينة لإرسال معلومات حساسة. بعد تحميل نموذج فارغ لتحويله إلى بصمات أصابع المستند، ثم إعداد نهج مقابل، تكتشف DLP أي مستندات في البريد الصادر تتطابق مع بصمة الإصبع هذه.

## <a name="how-document-fingerprinting-works"></a>كيفية عمل بصمات الأصابع في المستند

ربما تكون قد خمنت مسبقا أن المستندات لا تحمل بصمات أصابع فعلية، ولكن الاسم يساعد على شرح هذه الميزة. بنفس الطريقة التي يكون بها لأصابع أصابع الشخص أنماط فريدة، فإن المستندات لديها أنماط كلمات فريدة. عند تحميل ملف، تحدد DLP نمط الكلمة الفريد في المستند، وتنشئ بصمة إصبع المستند استنادا إلى هذا النمط، وتستخدم بصمة إصبع المستند للكشف عن المستندات الصادرة التي تحتوي على النمط نفسه. ولهذا السبب، فإن تحميل نموذج أو قالب ينشئ النوع الأكثر فعالية من بصمات أصابع المستند. يستخدم كل شخص يملأ النموذج مجموعة الكلمات الأصلية نفسها ثم يضيف كلماته الخاصة إلى المستند. طالما أن المستند الصادر غير محمي بكلمة مرور ويحتوي على كل النص من النموذج الأصلي، يمكن ل DLP تحديد ما إذا كان المستند يتطابق مع بصمة إصبع المستند.

> [!IMPORTANT]
> في الوقت الحالي، يمكن ل DLP استخدام بصمات أصابع المستند كطريقة للكشف في Exchange الإنترنت فقط.

يوضح المثال التالي ما يحدث إذا قمت بإنشاء بصمة إصبع المستند استنادا إلى قالب براءة اختراع، ولكن يمكنك استخدام أي نموذج كأساس لإنشاء بصمة إصبع المستند.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>مثال لمستند براءة اختراع يطابق بصمات أصابع مستند قالب براءة اختراع

![رسم تخطيطي لبصمات أصابع المستند.](../media/Document-Fingerprinting-diagram.png)

يحتوي قالب براءة الاختراع على الحقول الفارغة "عنوان براءات الاختراع" و"المخزون" و"الوصف" وأوصاف كل حقل من هذه الحقول، وهذا هو نمط الكلمة. عند تحميل قالب براءة الاختراع الأصلي، يكون في أحد أنواع الملفات المعتمدة وبنص عادي. تحول DLP نمط الكلمة هذا إلى بصمات أصابع المستند، وهو ملف Unicode XML صغير يحتوي على قيمة هاش فريدة تمثل النص الأصلي، وتحفظ بصمة الإصبع ك تصنيف بيانات في Active Directory. (كمقياس أمان، لا يتم تخزين المستند الأصلي نفسه على الخدمة؛ بل يتم تخزين قيمة التجزئة فقط، ولا يمكن إعادة بناء المستند الأصلي من قيمة التجزئة.) تصبح بعد ذلك بصمات الأصابع من نوع المعلومات الحساسة التي يمكنك إقرانها مع نهج DLP. بعد إقران بصمة الإصبع مع نهج DLP، تكتشف DLP أي رسائل بريد إلكتروني واردة تحتوي على مستندات تتطابق مع بصمة الإصبع وتتعامل معها وفقا لسياسة مؤسستك.

على سبيل المثال، قد ترغب في إعداد نهج DLP يمنع الموظفين العاديين من إرسال رسائل البريد الصادر التي تحتوي على براءات اختراع. ستستخدم DLP بصمات أصابع براءة الاختراع للكشف عن براءات الاختراع وحظر رسائل البريد الإلكتروني هذه. بدلا من ذلك، قد ترغب في السماح للقسم القانوني لديك بأن يتمكن من إرسال براءات اختراع إلى مؤسسات أخرى لأنه يحتاج إلى عمل للقيام بذلك. يمكنك السماح لأقسام معينة بإرسال معلومات حساسة عن طريق إنشاء استثناءات لتلك الأقسام في نهج DLP، أو يمكنك السماح لها بتجاوز تلميح نهج باستخدام مبرر عمل.

### <a name="supported-file-types"></a>أنواع الملفات المعتمدة

تدعم عملية أخذ بصمات الأصابع للمستند أنواع الملفات نفسها المعتمدة في قواعد تدفق البريد (المعروفة أيضا بقواعد النقل). للحصول على قائمة بأنواع الملفات المعتمدة، راجع أنواع الملفات المعتمدة [لفحص محتوى قاعدة تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). ملاحظة سريعة حول أنواع الملفات: لا تدعم قواعد تدفق البريد ولا بصمات أصابع المستند نوع الملف dotx. الذي قد يكون مربكا لأنه ملف قالب في Word. عندما ترى الكلمة "قالب" في هذا الموضوع ومواضيع أخرى لبصمات أصابع المستند، فهي تشير إلى مستند أنشأته كنموذج قياسي، وليس نوع ملف القالب.

#### <a name="limitations-of-document-fingerprinting"></a>القيود المفروضة على أخذ بصمات الأصابع في المستند

لن تكشف بصمات أصابع المستند عن المعلومات الحساسة في الحالات التالية:

- الملفات المحمية بكلمة مرور
- الملفات التي تحتوي على الصور فقط
- المستندات التي لا تحتوي على كل النص من النموذج الأصلي المستخدم لإنشاء بصمة إصبع المستند
- الملفات التي يزيد عددها عن 10 مبايت

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>استخدام PowerShell لإنشاء حزمة قاعدة تصنيف استنادا إلى بصمات أصابع المستند

حاليا، يمكنك إنشاء بصمة إصبع المستند فقط في [مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

تستخدم DLP حزم قواعد التصنيف للكشف عن المحتوى الحساس. لإنشاء حزمة قاعدة تصنيف استنادا إلى بصمة إصبع المستند، استخدم **الأمرين cmdlets New-DlpFinger** و **New-DlpSensitiveInformationType** cmdlets. نظرا لعدم تخزين نتائج الطباعة **New-DlpFinger** خارج قاعدة تصنيف البيانات، يمكنك دائما تشغيل **New-DlpFingerprint** و **New-DlpSensitiveInformationType** أو **Set-DlpSensitiveInformationType** في جلسة PowerShell نفسها. ينشئ المثال التالي بصمات أصابع مستند جديد استنادا إلى الملف C:\My Documents\Contoso Employee Template.docx. يمكنك تخزين بصمة الإصبع الجديدة كمتغير بحيث يمكنك استخدامها مع **cmdlet New-DlpSensitiveInformationType** في جلسة PowerShell نفسها.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

والآن، دعنا ننشئ قاعدة جديدة لتصنيف البيانات تسمى "سري لموظف Contoso" تستخدم بصمات أصابع المستند للملف C:\My Documents\Contoso Customer Information Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

يمكنك الآن استخدام أمر cmdlet **Get-DlpSensitiveInformationType** للعثور على كافة حزم قواعد تصنيف بيانات DLP، وفي هذا المثال، "Contoso Customer Confidential" هو جزء من قائمة حزم قواعد تصنيف البيانات.

وأخيرا، أضف حزمة قواعد تصنيف البيانات "Contoso Customer Confidential" إلى نهج DLP في مركز توافق &amp; الأمان. يضيف هذا المثال قاعدة إلى نهج DLP موجود يسمى "ConfidentialPolicy".

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

يمكنك أيضا استخدام حزمة قواعد تصنيف البيانات في قواعد تدفق البريد في Exchange Online، كما هو موضح في المثال التالي. لتشغيل هذا الأمر، ستحتاج أولا إلى الاتصال [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). لاحظ أيضا أن &amp; مزامنة حزمة القواعد من مركز توافق الأمان إلى مركز إدارة Exchange يستغرق وقتا.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

تكتشف DLP الآن المستندات التي تتطابق مع "عميل Contoso" Form.docx بصمات أصابع المستند.

للحصول على بناء الجملة ومعلومات المعلمة، راجع:

- [الطباعة الجديدة ل DlpFinger](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
