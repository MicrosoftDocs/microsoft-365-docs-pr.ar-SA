---
title: حول بصمة المستند
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
description: يتعامل العاملون في مجال المعلومات في مؤسستك مع أنواع عديدة من المعلومات الحساسة خلال يوم نموذجي. تسهل لك بصمة المستند حماية هذه المعلومات من خلال تحديد النماذج القياسية المستخدمة في جميع أنحاء مؤسستك. يصف هذا الموضوع المفاهيم وراء بصمة المستند وكيفية إنشاء واحد باستخدام PowerShell.
ms.openlocfilehash: 744b96f693676cf94357034a4404f63f0fbd2c45
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754467"
---
# <a name="document-fingerprinting"></a>تعريف المستند ببصمة الإصبع

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يتعامل العاملون في مجال المعلومات في مؤسستك مع أنواع عديدة من المعلومات الحساسة خلال يوم نموذجي. في مدخل التوافق في Microsoft Purview، تسهل لك بصمة المستند حماية هذه المعلومات من خلال تحديد النماذج القياسية المستخدمة في جميع أنحاء مؤسستك. يصف هذا الموضوع المفاهيم وراء بصمة المستند وكيفية إنشاء واحد باستخدام PowerShell.

## <a name="basic-scenario-for-document-fingerprinting"></a>سيناريو أساسي لبصمة المستند

بصمة المستند هي ميزة تفادي فقدان البيانات في Microsoft Purview (DLP) تحول نموذجا قياسيا إلى نوع معلومات حساسة، والتي يمكنك استخدامها في قواعد نهج DLP. على سبيل المثال، يمكنك إنشاء بصمة مستند استنادا إلى قالب براءة اختراع فارغ ثم إنشاء نهج DLP يكشف عن جميع قوالب براءة الاختراع الصادرة ويحظرها مع ملء محتوى حساس. بشكل اختياري، يمكنك إعداد [تلميحات النهج](use-notifications-and-policy-tips.md) لإعلام المرسلين بأنهم قد يرسلون معلومات حساسة، ويجب على المرسل التحقق من أن المستلمين مؤهلون لتلقي براءات الاختراع. تعمل هذه العملية مع أي نماذج مستندة إلى نص مستخدمة في مؤسستك. تتضمن الأمثلة الإضافية للنماذج التي يمكنك تحميلها ما يلي:

- النماذج الحكومية
- نماذج الامتثال لقانون نقل التأمين الصحي والمساءلة (HIPAA)
- نماذج معلومات الموظفين لأقسام الموارد البشرية
- النماذج المخصصة التي تم إنشاؤها خصيصا لمؤسستك

من الناحية المثالية، لدى مؤسستك بالفعل ممارسة تجارية راسخة لاستخدام نماذج معينة لنقل المعلومات الحساسة. بعد تحميل نموذج فارغ لتحويله إلى بصمة مستند وإعداد نهج مقابل، يكتشف DLP أي مستندات في البريد الصادر تتطابق مع بصمة الإصبع هذه.

## <a name="how-document-fingerprinting-works"></a>كيفية عمل بصمة المستند

ربما كنت قد خمنت بالفعل أن المستندات لا تحتوي على بصمات فعلية، ولكن الاسم يساعد على شرح الميزة. وبنفس الطريقة التي تحتوي بها بصمات الأشخاص على أنماط فريدة، فإن المستندات لها أنماط كلمات فريدة. عند تحميل ملف، يحدد DLP نمط الكلمة الفريد في المستند، وينشئ بصمة مستند استنادا إلى هذا النمط، ويستخدم بصمة المستند هذه للكشف عن المستندات الصادرة التي تحتوي على النمط نفسه. لهذا السبب يؤدي تحميل نموذج أو قالب إلى إنشاء النوع الأكثر فعالية من بصمة المستند. يستخدم كل شخص يقوم بتعبئة نموذج نفس المجموعة الأصلية من الكلمات ثم يضيف كلماته الخاصة إلى المستند. طالما أن المستند الصادر غير محمي بكلمة مرور ويحتوي على النص بالكامل من النموذج الأصلي، يمكن ل DLP تحديد ما إذا كان المستند يطابق بصمة المستند.

> [!IMPORTANT]
> في الوقت الحالي، يمكن ل DLP استخدام بصمة المستند كأسلوب اكتشاف في Exchange عبر الإنترنت فقط.

يوضح المثال التالي ما يحدث إذا قمت بإنشاء بصمة مستند استنادا إلى قالب براءة اختراع، ولكن يمكنك استخدام أي نموذج كأساس لإنشاء بصمة المستند.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>مثال على مستند براءة اختراع يطابق بصمة مستند لقالب براءة اختراع

![رسم تخطيطي لبصمة المستند.](../media/Document-Fingerprinting-diagram.png)

يحتوي قالب براءة الاختراع على الحقول الفارغة "عنوان براءة الاختراع" و"المجردون" و"الوصف" والأوصاف لكل حقل من هذه الحقول ، وهذا هو نمط الكلمة. عند تحميل قالب براءة الاختراع الأصلي، يكون في أحد أنواع الملفات المدعومة وفي نص عادي. يحول DLP نمط الكلمة هذا إلى بصمة مستند، وهو ملف Unicode XML صغير يحتوي على قيمة تجزئة فريدة تمثل النص الأصلي، ويتم حفظ بصمة الإصبع كتصنيف بيانات في Active Directory. (كإجراء أمان، لا يتم تخزين المستند الأصلي نفسه على الخدمة؛ يتم تخزين قيمة التجزئة فقط، ولا يمكن إعادة بناء المستند الأصلي من قيمة التجزئة.) ثم تصبح بصمة براءة الاختراع نوعا من المعلومات الحساسة التي يمكنك ربطها بنهج DLP. بعد إقران بصمة الإصبع بنهج DLP، تكتشف DLP أي رسائل بريد إلكتروني صادرة تحتوي على مستندات تطابق بصمة براءة الاختراع وتتعامل معها وفقا لنهج مؤسستك.

على سبيل المثال، قد ترغب في إعداد نهج DLP يمنع الموظفين العاديين من إرسال رسائل صادرة تحتوي على براءات اختراع. سيستخدم DLP بصمة براءة الاختراع للكشف عن براءات الاختراع ومنع رسائل البريد الإلكتروني هذه. بدلا من ذلك، قد ترغب في السماح للقسم القانوني الخاص بك بأن يكون قادرا على إرسال براءات الاختراع إلى مؤسسات أخرى لأن لديه حاجة تجارية للقيام بذلك. يمكنك السماح لأقسام معينة بإرسال معلومات حساسة عن طريق إنشاء استثناءات لتلك الأقسام في نهج DLP الخاص بك، أو يمكنك السماح لها بتجاوز تلميح نهج مع مبررات الأعمال.

### <a name="supported-file-types"></a>أنواع الملفات المعتمدة

تدعم بصمة المستند أنواع الملفات نفسها المعتمدة في قواعد تدفق البريد (المعروفة أيضا بقواعد النقل). للحصول على قائمة بأنواع الملفات المعتمدة، راجع [أنواع الملفات المعتمدة لفحص محتوى قاعدة تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). ملاحظة سريعة واحدة حول أنواع الملفات: لا تدعم قواعد تدفق البريد ولا بصمة المستند نوع ملف .dotx، والذي قد يكون مربكا لأن هذا ملف قالب في Word. عندما ترى الكلمة "قالب" في هذا الموضوع وموضوعات بصمات المستندات الأخرى، فإنها تشير إلى مستند أنشأته كنموذج قياسي، وليس نوع ملف القالب.

#### <a name="limitations-of-document-fingerprinting"></a>قيود بصمات المستندات

لن تكتشف بصمة المستند المعلومات الحساسة في الحالات التالية:

- الملفات المحمية بكلمة مرور
- الملفات التي تحتوي على صور فقط
- المستندات التي لا تحتوي على النص بالكامل من النموذج الأصلي المستخدم لإنشاء بصمة المستند
- ملفات أكبر من 10 ميغابايت

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>استخدام PowerShell لإنشاء حزمة قاعدة تصنيف استنادا إلى بصمة المستند

حاليا، يمكنك إنشاء بصمة مستند فقط في [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

يستخدم DLP حزم قواعد التصنيف للكشف عن المحتوى الحساس. لإنشاء حزمة قاعدة تصنيف استنادا إلى بصمة المستند، استخدم **New-DlpFingerprint** و **New-DlpSensitiveInformationType** cmdlets. نظرا لعدم تخزين نتائج **New-DlpFingerprint** خارج قاعدة تصنيف البيانات، يمكنك دائما تشغيل **New-DlpFingerprint** و **New-DlpSensitiveInformationType** أو **Set-DlpSensitiveInformationType** في نفس جلسة PowerShell. ينشئ المثال التالي بصمة مستند جديدة استنادا إلى الملف C:\My Documents\Contoso Employee Template.docx. يمكنك تخزين بصمة الإصبع الجديدة كمتغير حتى تتمكن من استخدامها مع **New-DlpSensitiveInformationType** cmdlet في نفس جلسة عمل PowerShell.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

الآن، دعنا ننشئ قاعدة تصنيف بيانات جديدة تسمى "Contoso Employee Confidential" تستخدم بصمة مستند الملف C:\My Documents\Contoso Customer Information Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

يمكنك الآن استخدام **Get-DlpSensitiveInformationType** cmdlet للعثور على جميع حزم قواعد تصنيف بيانات DLP، وفي هذا المثال، "Contoso Customer Confidential" هو جزء من قائمة حزم قواعد تصنيف البيانات.

وأخيرا، أضف حزمة قاعدة تصنيف البيانات "Contoso Customer Confidential" إلى نهج DLP في مدخل التوافق في Microsoft Purview. يضيف هذا المثال قاعدة إلى نهج DLP موجود يسمى "ConfidentialPolicy".

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

يمكنك أيضا استخدام حزمة قاعدة تصنيف البيانات في قواعد تدفق البريد في Exchange Online، كما هو موضح في المثال التالي. لتشغيل هذا الأمر، تحتاج أولا إلى [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). لاحظ أيضا أن مزامنة حزمة القواعد من مدخل التوافق في Microsoft Purview إلى مركز إدارة Exchange يستغرق وقتا.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

يكشف DLP الآن عن المستندات التي تطابق بصمة مستند Form.docx عميل Contoso.

للحصول على معلومات حول بناء الجملة والمعلمة، راجع:

- [New-DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
