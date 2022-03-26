---
title: شروط نهج DLP والاستثناءات والإجراءات
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
recommendations: false
description: التعرف على شروط نهج dlp والاستثناءات
ms.openlocfilehash: 771674b82e50987397fc1ae754f0b96719a04ae5
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63572971"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>شروط نهج DLP والاستثناءات والإجراءات

تحدد الشروط والاستثناءات في نهج DLP العناصر الحساسة التي يتم تطبيق النهج عليها. تعرف الإجراءات ما يحدث نتيجة لشرط الاستثناء الذي يتم وضعه.

- تحدد الشروط ما يجب تضمينه
- تحدد الاستثناءات ما يجب استبعاده.
- تعرف الإجراءات ما يحدث نتيجة لشرط أو استثناء يتم وضعه

تملك معظم الشروط والاستثناءات خاصية واحدة تدعم قيمة واحدة أو أكثر. على سبيل المثال، إذا تم تطبيق نهج DLP Exchange البريد الإلكتروني، فإن الشرط "المرسل" يتطلب  مرسل الرسالة. بعض الشروط لها نوعان من الخصائص. على سبيل المثال،  يتضمن رأس الرسالة أي شرط من هذه الكلمات يتطلب خاصية واحدة لتحديد حقل رأس الرسالة، و خاصية ثانية لتحديد النص الذي تريد البحث عنه في حقل الرأس. لا تملك بعض الشروط أو الاستثناءات أي خصائص. على سبيل المثال، **إن الشرط المرفق** محمي بكلمة مرور فقط للبحث عن المرفقات في الرسائل المحمية بكلمة مرور.

تتطلب الإجراءات عادة خصائص إضافية. على سبيل المثال، عندما تعيد قاعدة نهج DLP توجيه رسالة، ستحتاج إلى تحديد المكان الذي تمت إعادة توجيه الرسالة إليه.
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>الشروط والاستثناءات لنهج DLP

تصف الجداول في المقاطع التالية الشروط والاستثناءات المتوفرة في DLP.

- [المرسلون](#senders)
- [المستلمون](#recipients)
- [موضوع الرسالة أو نصها](#message-subject-or-body)
- [المرفقات](#attachments)
- [رؤوس الرسائل](#message-headers)
- [خصائص الرسالة](#message-properties)

### <a name="senders"></a>المرسلون

إذا كنت تستخدم عنوان المرسل كشرط أو استثناء، يختلف الحقل الفعلي حيث يتم البحث عن القيمة استنادا إلى موقع عنوان المرسل الذي تم تكوينه. بشكل افتراضي، تستخدم قواعد DLP عنوان الرأس كعنوان المرسل.

![صورة لرأس بريد إلكتروني تعرض الفرق بين عنوان المغلف (P1) وعنوان الرأس (P2)](../media/dlp-conditions-exceptions-meetinginvite-callouts.png)

على مستوى المستأجر، يمكنك تكوين موقع عنوان المرسل لكي يتم استخدامه عبر كل القواعد، ما لم يتم تجاوزه بواسطة قاعدة واحدة. لتعيين تكوين نهج DLP للمستأجر لتقييم عنوان المرسل من المغلف عبر كل القواعد، يمكنك تشغيل الأمر التالي:

```PowerShell
Set-PolicyConfig –SenderAddressLocation Envelope
```

لتكوين موقع عنوان المرسل على مستوى قاعدة DLP، تكون المعلمة _SenderAddressLocation_. القيم المتوفرة هي:

- **رأس الصفحة**: افحص المرسلين في رؤوس الرسائل فقط (على سبيل المثال، الحقول **من** أو مرسل أو رد **على**). هذه هي القيمة الافتراضية.

- **المغلف**: افحص المرسلين من مغلف الرسالة فقط (قيمة **MAIL FROM** التي تم استخدامها في إرسال SMTP، والتي يتم عادة تخزينها في حقل **Return-Path** ).

- **رأس أو مغلف** (`HeaderOrEnvelope`) افحص المرسلين في رأس الرسالة ومغلف الرسالة.
<br>

|شرط أو استثناء في DLP|معلمات الشرط/الاستثناء في Microsoft 365 PowerShell|نوع الخاصية|الوصف|
|---|---|---|---|
|المرسل هو|الشرط: *من* <br/> استثناء: *ExceptIfFrom*|العناوين|الرسائل التي يتم إرسالها بواسطة علب البريد المحددة أو مستخدمي البريد أو جهات اتصال البريد أو Microsoft 365 المجموعات في المؤسسة.|
|المرسل هو عضو في |_FromMemberOf_ <br/> _ExceptIfFromMemberOf_|العناوين|الرسائل التي يتم إرسالها بواسطة عضو في مجموعة التوزيع المحددة أو مجموعة الأمان التي تم تمكين البريد Microsoft 365 المجموعة.|
|عنوان IP المرسل هو|الشرط: *SenderIPRanges*<br/> استثناء: *ExceptIfSenderIPRanges*|IPAddressRanges|الرسائل التي يتطابق فيها عنوان IP الخاص المرسل مع عنوان IP المحدد، أو تقع ضمن نطاق عنوان IP المحدد.|
|يحتوي عنوان المرسل على كلمات|الشرط: *FromAddressContainsWords* <br/> استثناء: *ExceptIfFromAddressContainsWords*|الكلمات|الرسائل التي تحتوي على الكلمات المحددة في عنوان البريد الإلكتروني الخاص المرسل.|
|يتطابق عنوان المرسل مع الأنماط|الشرط: *FromAddressMatchesPatterns* <br/> استثناء: *ExceptFromAddressMatchesPatterns*|الأنماط|الرسائل التي يحتوي عنوان البريد الإلكتروني الخاص بها على أنماط نصية تتطابق مع التعبيرات العادية المحددة.|
|مجال المرسل هو|الشرط: *SenderDomainIs* <br/> استثناء: *ExceptIfSenderDomainIs*|DomainName|الرسائل التي يتطابق فيها مجال عنوان البريد الإلكتروني للمرسل مع القيمة المحددة. إذا كنت بحاجة إلى البحث عن مجالات المرسلين التي  تحتوي على المجال المحدد (على سبيل المثال، أي مجال فرعي لمجال)، فاستخدم الشرط تطابقات عنوان **المرسل (***FromAddressMatchesPatterns*) وحدد المجال باستخدام بناء الجملة: '\.domaincom\.$'.|
|نطاق المرسل|الشرط: *FromScope* <br/> استثناء: *ExceptIfFromScope*|UserScopeFrom|الرسائل المرسلة من قبل مرسلين داخليين أو خارجيين.|
|تتضمن الخصائص المحددة للمرسل أي من هذه الكلمات|الشرط: *SenderADAttributeContainsWords* <br/> استثناء: *ExceptIfSenderADAttributeContainsWords*|الخاصية الأولى: `ADAttribute` <p> الخاصية الثانية: `Words`|الرسائل التي تحتوي فيها سمة Active Directory المحددة للمرسل على أي من الكلمات المحددة.|
|تتطابق خصائص المرسل المحددة مع أنماط النص هذه|الشرط: *SenderADAttributeMatchesPatterns* <br/> استثناء: *ExceptIfSenderADAttributeMatchesPatterns*|الخاصية الأولى: `ADAttribute` <p> الخاصية الثانية: `Patterns`|الرسائل التي تحتوي فيها سمة Active Directory المحددة للمرسل على أنماط نصية تتطابق مع التعبيرات العادية المحددة.|
|

### <a name="recipients"></a>المستلمون

<br>

****

|شرط أو استثناء في DLP|معلمات الشرط/الاستثناء في Microsoft 365 PowerShell|نوع الخاصية|الوصف|
|---|---|---|---|
|المستلم هو|الشرط: *SentTo* <br/> استثناء: *ExceptIfSentTo*|العناوين|الرسائل التي يكون فيها أحد المستلمين هو علبة البريد المحددة أو مستخدم البريد أو جهة اتصال البريد في المؤسسة. يمكن أن يكون المستلمون في الحقول **إلى** أو **نسخة** أو **نسخة من** الرسالة.|
|مجال المستلم هو|الشرط: *RecipientDomainIs* <br/> استثناء: *ExceptIfRecipientDomainIs*|DomainName|الرسائل التي يتطابق فيها مجال عنوان البريد الإلكتروني للمستلم مع القيمة المحددة.|
|يحتوي عنوان المستلم على كلمات|الشرط: *AnyOfRecipientAddressContainsWords* <br/> استثناء: *ExceptIfAnyOfRecipientAddressContainsWords*|الكلمات|الرسائل التي تحتوي على الكلمات المحددة في عنوان البريد الإلكتروني للمستلم. <br/>**ملاحظة**: لا يعتبر هذا الشرط الرسائل المرسلة إلى عناوين وكيل المستلمين. وهو يتطابق فقط مع الرسائل التي يتم إرسالها إلى عنوان البريد الإلكتروني الأساسي للمستلم.|
|يتطابق عنوان المستلم مع الأنماط|الشرط: *AnyOfRecipientAddressMatchesPatterns* <br/> استثناء: *ExceptIfAnyOfRecipientAddressMatchesPatterns*|الأنماط|الرسائل التي يحتوي فيها عنوان البريد الإلكتروني للمستلم على أنماط نص تتطابق مع التعبيرات العادية المحددة. <br/> **ملاحظة**: لا يعتبر هذا الشرط الرسائل المرسلة إلى عناوين وكيل المستلمين. وهو يتطابق فقط مع الرسائل التي يتم إرسالها إلى عنوان البريد الإلكتروني الأساسي للمستلم.|
|تم إرسالها إلى عضو في|الشرط: *SentToMemberOf* <br/> استثناء: *ExceptIfSentToMemberOf*|العناوين|الرسائل التي تحتوي على مستلمين من أعضاء مجموعة التوزيع المحددة أو مجموعة الأمان التي تم تمكين البريد Microsoft 365 المجموعة. يمكن أن تكون المجموعة في الحقول **إلى** أو **نسخة** أو **نسخة من** الرسالة.|
|تتضمن الخصائص المحددة للمستلم أي من هذه الكلمات |_RecipientADAttributeContainsWords_ <br/> _ExceptIfRecipientADAttributeContainsWords_|الخاصية الأولى: `ADAttribute` <p> الخاصية الثانية: `Words`|الرسائل التي تحتوي فيها سمة Active Directory المحددة للمستلم على أي من الكلمات المحددة. <p> تجدر الإشارة إلى **أن السمة Country** تتطلب قيمة رمز البلد ذات الحرفين (على سبيل المثال، DE ل Germany).|
|تتطابق الخصائص المحددة للمستلم مع أنماط النص هذه |_RecipientADAttributeMatchesPatterns_ <br/> _ExceptIfRecipientADAttributeMatchesPatterns_|الخاصية الأولى: `ADAttribute` <p> الخاصية الثانية: `Patterns`|الرسائل التي تحتوي فيها سمة Active Directory المحددة للمستلم على أنماط نصية تتطابق مع التعبيرات العادية المحددة.|
|

### <a name="message-subject-or-body"></a>موضوع الرسالة أو نصها

<br>

****

|شرط أو استثناء في DLP|معلمات الشرط/الاستثناء في Microsoft 365 PowerShell|نوع الخاصية|الوصف|
|---|---|---|---|
|يحتوي الموضوع على كلمات أو عبارات|الشرط: *SubjectContainsWords* <br/> استثناء: *ExceptIf SubjectContainsWords*|الكلمات|الرسائل التي بها الكلمات المحددة في الحقل الموضوع.|
|يتطابق الموضوع مع الأنماط|الشرط: *SubjectMatchesPatterns* <br/> استثناء: *ExceptIf SubjectMatchesPatterns*|الأنماط|الرسائل التي يحتوي فيها حقل الموضوع على أنماط نص تتطابق مع التعبيرات العادية المحددة.|
|يحتوي المحتوى على|الشرط: *ContentContainsSensitiveInformation* <br/> استثناء *ExceptIfContentContainsSensitiveInformation*|SensitiveInformationTypes|الرسائل أو المستندات التي تحتوي على معلومات حساسة كما تم تعريفها بواسطة سياسات منع فقدان البيانات (DLP).|
|النمط "تطابق الموضوع" أو "الجسم"|الشرط: *SubjectOrBodyMatchesPatterns* <br/> استثناء: *ExceptIfSubjectOrBodyMatchesPatterns*|الأنماط|الرسائل التي يحتوي فيها حقل الموضوع أو نص الرسالة على أنماط نص تتطابق مع التعبيرات العادية المحددة.|
|يحتوي الموضوع أو النص النصي على كلمات|الشرط: *SubjectOrBodyContainsWords* <br/> استثناء: *ExceptIfSubjectOrBodyContainsWords*|الكلمات|الرسائل التي بها الكلمات المحددة في حقل الموضوع أو نص الرسالة|
|

### <a name="attachments"></a>المرفقات

<br>

****

|شرط أو استثناء في DLP|معلمات الشرط/الاستثناء في Microsoft 365 PowerShell|نوع الخاصية|الوصف|
|---|---|---|---|
|المرفق محمي بكلمة مرور|الشرط: *DocumentIsPasswordProtected* <br/> استثناء: *ExceptIfDocumentIsPasswordProtected*|بلا|الرسائل التي يكون فيها المرفق محميا بكلمة مرور (وبالتالي لا يمكن فحصه). يعمل الكشف عن كلمة المرور فقط Office المستندات .zip الملفات وملفات .7z.|
|ملحق ملف المرفق هو|الشرط: *ContentExtensionMatchesWords* <br/> استثناء: *ExceptIfContentExtensionMatchesWords*|الكلمات|الرسائل التي يتطابق فيها ملحق ملف المرفق مع أي من الكلمات المحددة.|
|لا يمكن فحص أي محتوى مرفق بريد إلكتروني|الشرط: *DocumentIsUnsupported* <br/>استثناء: *ExceptIf DocumentIsUnsupported*|n/a|الرسائل التي لا يتعرف عليها المرفق في Exchange Online.|
|لم يكمل أي محتوى مرفق بريد إلكتروني عملية المسح الضوئي|الشرط: *ProcessingLimitExceeded* <br/> استثناء: *ExceptIfProcessingLimitExceeded*|n/a|الرسائل التي لم يتمكن مشغل القواعد من إكمال فحص المرفقات فيها. يمكنك استخدام هذا الشرط لإنشاء القواعد التي تعمل معا لتعريف الرسائل التي لا يمكن فحص المحتوى فيها بشكل كامل.|
|يحتوي اسم المستند على كلمات|الشرط: *DocumentNameMatchesWords* <br/> استثناء: *ExceptIfDocumentNameMatchesWords*|الكلمات|الرسائل التي يتطابق فيها اسم ملف المرفق مع أي من الكلمات المحددة.|
|اسم المستند يتطابق مع الأنماط|الشرط: *DocumentNameMatchesPatterns* <br/> استثناء: *ExceptIfDocumentNameMatchesPatterns*|الأنماط|الرسائل التي يحتوي فيها اسم ملف المرفق على أنماط نصية تتطابق مع التعبيرات العادية المحددة.|
|الخاصية "مستند" هي|الشرط: *ContentPropertyContainsWords* <br/> استثناء: *ExceptIfContentPropertyContainsWords*|الكلمات|الرسائل أو المستندات التي يتطابق فيها ملحق ملف المرفق مع أي من الكلمات المحددة.|
|حجم المستند يساوي أو أكبر من|الشرط: *DocumentSizeOver* <br/> استثناء: *ExceptIfDocumentSizeOver*|الحجم|الرسائل التي يكون فيها أي مرفق أكبر من القيمة المحددة أو مساويا لها.|
|يتضمن أي محتوى مرفق أي من هذه الكلمات|الشرط: *DocumentContainsWords* <br/> استثناء: *ExceptIfDocumentContainsWords*|`Words`|الرسائل التي يحتوي فيها المرفق على الكلمات المحددة.|
|أي محتوى مرفقات يتطابق مع أنماط النص هذه|الشرط: *DocumentMatchesPatterns* <br/> استثناء: *ExceptIfDocumentMatchesPatterns*|`Patterns`|الرسائل التي يحتوي فيها المرفق على أنماط نصية تتطابق مع التعبيرات العادية المحددة.|
|

### <a name="message-headers"></a>رؤوس الرسائل

<br>

****

|شرط أو استثناء في DLP|معلمات الشرط/الاستثناء في Microsoft 365 PowerShell|نوع الخاصية|الوصف|
|---|---|---|---|
|يحتوي الرأس على كلمات أو عبارات|الشرط: *HeaderContainsWords* <br/> استثناء: *ExceptIfHeaderContainsWords*|جدول هاش|تحتوي الرسائل التي تحتوي على حقل الرأس المحدد، وقيمة حقل الرأس هذا على الكلمات المحددة.|
|يتطابق الرأس مع الأنماط|الشرط: *HeaderMatchesPatterns* <br/> استثناء: *ExceptIfHeaderMatchesPatterns*|جدول هاش|تحتوي الرسائل التي تحتوي على حقل الرأس المحدد، وقيمة حقل الرأس هذا على التعبيرات العادية المحددة.|

### <a name="message-properties"></a>خصائص الرسالة

<br>

****

|شرط أو استثناء في DLP|معلمات الشرط/الاستثناء في Microsoft 365 PowerShell|نوع الخاصية|الوصف|
|---|---|---|---|
|مع الأهمية|الشرط: *WithImportance* <br/> استثناء: *ExceptIfWithImportance*|الأهمية|الرسائل التي تم وضع علامة عليها بمستوى الأهمية المحدد.|
|تحتوي مجموعة أحرف المحتوى على كلمات|الشرط: *ContentCharacterSetContainsWords* <br/> *ExceptIfContentCharacterSetContainsWords*|مجموعات الأحرف|الرسائل التي لها أي من أسماء مجموعة الأحرف المحددة.|
|تم تجاوز المرسل|الشرط: *HasSenderOverride* <br/> استثناء: *ExceptIfHasSenderOverride*|n/a|الرسائل التي اختار فيها المرسل تجاوز نهج منع فقدان البيانات (DLP). لمزيد من المعلومات حول سياسات DLP، راجع [التعرف على منع فقدان البيانات](./dlp-learn-about-dlp.md)|
|تطابقات نوع الرسالة|الشرط: *MessageTypeMatches* <br/> استثناء: *ExceptIfMessageTypeMatches*|MessageType|رسائل من النوع المحدد.|
|حجم الرسالة أكبر من أو يساوي|الشرط: *MessageSizeOver* <br/> استثناء: *ExceptIfMessageSizeOver*|`Size`|الرسائل التي يكون فيها الحجم الإجمالي (الرسالة بالإضافة إلى المرفقات) أكبر من القيمة المحددة أو مساويا لها. **ملاحظة**: يتم تقييم حدود أحجام الرسائل في علب البريد قبل قواعد تدفق البريد. سيتم رفض رسالة كبيرة جدا لعلبة بريد قبل أن تتمكن قاعدة بهذا الشرط من العمل على الرسالة.|
|

## <a name="actions-for-dlp-policies"></a>إجراءات لنهج DLP

يصف هذا الجدول الإجراءات المتوفرة في DLP.

<br>

****

|إجراء في DLP|معلمات الإجراءات في Microsoft 365 PowerShell|نوع الخاصية|الوصف|
|---|---|---|---|
|تعيين رأس|SetHeader|الخاصية الأولى: *اسم الرأس* </br> الخاصية الثانية: *قيمة الرأس*|تحدد المعلمة SetHeader إجراء لقاعدة DLP التي تضيف أو تعدل حقل رأس وقيمة في رأس الرسالة. تستخدم هذه المعلمة بناء الجملة "HeaderName:HeaderValue". يمكنك تحديد عدة أزواج من أسماء الرأس والقيم مفصولة بفصول|
|إزالة الرأس|RemoveHeader|الخاصية الأولى: *MessageHeaderField*</br> الخاصية الثانية: *سلسلة*|تحدد المعلمة RemoveHeader إجراء لقاعدة DLP التي تزيل حقل رأس من رأس الرسالة. تستخدم هذه المعلمة بناء الجملة "HeaderName" أو "HeaderName:HeaderValue". يمكنك تحديد عدة أسماء رؤوس أو أسماء رؤوس وأزواج قيم مفصولة بفصول|
|إعادة توجيه الرسالة إلى مستخدمين محددين|*RedirectMessageTo*|العناوين|إعادة توجيه الرسالة إلى المستلمين المحددين. لا يتم تسليم الرسالة إلى المستلمين  الأصلية، ولا يتم إرسال أي إعلام إلى المرسل أو المستلمين  الأصلية.|
|إعادة توجيه الرسالة للموافقة عليها إلى مدير المرسل|متوسط|الخاصية الأولى: *ModerateMessageByManager*</br> الخاصية الثانية: *Boolean*|تحدد المعلمة متوسط إجراء لقاعدة DLP التي ترسل رسالة البريد الإلكتروني إلى المشرف. تستخدم هذه المعلمة بناء الجملة: @{ModerateMessageByManager = <$true \|$false>;|
|إعادة توجيه الرسالة للموافقة عليها إلى موافقين محددين|متوسط|الخاصية الأولى: *ModerateMessageByUser*</br>الخاصية الثانية: *العناوين*|تحدد المعلمة متوسط إجراء لقاعدة DLP التي ترسل رسالة البريد الإلكتروني إلى المشرف. تستخدم هذه المعلمة بناء الجملة: @{ ModerateMessageByUser = @("emailaddress1","emailaddress2",..."emailaddressN")}|
|إضافة مستلم|AddRecipients|الخاصية الأولى: *الحقل*</br>الخاصية الثانية: *العناوين*|إضافة مستلم واحد أو أكثر إلى الحقل إلى/نسخة/نسخة نسخة من الرسالة. تستخدم هذه المعلمة بناء الجملة: @{<AddToRecipients \|CopyTo \|BlindCopyTo> = "emailaddress"}|
|إضافة مدير المرسل كمستلم|AddRecipients|الخاصية الأولى: *AddedManagerAction*</br>الخاصية الثانية: *الحقل*|يضيف مدير المرسل إلى الرسالة كنوع المستلم المحدد (إلى، نسخة مرسلة)، أو يعيد توجيه الرسالة إلى مدير المرسل من دون إعلام المرسل أو المستلم. يعمل هذا الإجراء فقط إذا تم تعريف سمة إدارة المرسل في Active Directory. تستخدم هذه المعلمة بناء الجملة: @{AddManagerAsRecipientType = "<To \|Cc \|Bcc>"}|
الموضوع المبلل|PrependSubject|سلسلة|يضيف النص المحدد إلى بداية الحقل الموضوع للرسالة. فكر في استخدام مسافة أو نقطتين (:) الحرف الأخير من النص المحدد لتمييزه عن نص الموضوع الأصلي.</br>لمنع إضافة السلسلة نفسها إلى الرسائل التي تحتوي بالفعل على النص في الموضوع (على سبيل المثال، الردود)، أضف الاستثناء "يحتوي الموضوع على كلمات" (ExceptIfSubjectContainsWords) للقاعدة.|
|تطبيق إخلاء المسؤولية ل HTML|تطبيقHtmlDisclaimer|الخاصية الأولى: *نص*</br>الخاصية الثانية: *الموقع*</br>الخاصية الثالثة: *إجراء استرداد*|تطبيق إخلاء المسؤولية المحدد ل HTML على الموقع المطلوب للرسالة.</br>تستخدم هذه المعلمة بناء الجملة: @{ Text = " " ; Location = <Prepend prepend \|>; BackAction = <التفاف \|تجاهل \|رفض> }|
|إزالة تشفير الرسائل من Office 365 وحماية الحقوق|RemoveRMSTemplate|n/a|إزالة Office 365 التشفير المطبق على رسالة بريد إلكتروني|
|تسليم الرسالة إلى الفحص المستضاف |_الفحص_|n/a| هذا الإجراء موجود حاليا في **المعاينة العامة**. أثناء هذه المرحلة، ستظهر رسائل البريد الإلكتروني المعزولة بواسطة نهج DLP نوع النهج ك ExchangeTransportRule.</br> تسليم الرسالة إلى الفحص في EOP. لمزيد من المعلومات، راجع [رسائل البريد الإلكتروني المعزولة في EOP](/microsoft-365/security/office-365-security/quarantine-email-messages).|
|

<!--|Modify Subject|ModifySubject|PswsHashTable | Remove text from the subject line that matches a specific pattern and replace it with different text. See the example below. You can: </br>- **Replace** all matches in the subject with the replacement text </br>- **Append** to remove all matches in the subject and inserts the replacement text at the end of the subject. </br>- **Prepend** to remove all matches and inserts the replacement text at the beginning of the subject. See ModifySubject parameter in, /powershell/module/exchange/new-dlpcompliancerule|-->

