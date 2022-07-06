---
title: تحديد قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 9b7daf19-d5f2-415b-bc43-a0f5f4a585e8
ms.collection:
- M365-security-compliance
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: يمكن للمسؤولين تعلم كيفية إنشاء قواعد تدفق البريد (قواعد النقل) لتشفير الرسائل وفك تشفيرها باستخدام تشفير الرسائل في Microsoft Purview.
ms.openlocfilehash: 75abd302bf661fda50b144f431572c8c6dfc8bcc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635688"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>تحديد قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني

بصفتك مسؤولا يدير Exchange Online، يمكنك إنشاء قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) للمساعدة في حماية رسائل البريد الإلكتروني التي ترسلها وتستلمها. يمكنك إعداد قواعد لتشفير أي رسائل بريد إلكتروني صادرة وإزالة التشفير من الرسائل المشفرة الواردة من داخل مؤسستك أو من الردود على الرسائل المشفرة المرسلة من مؤسستك. يمكنك استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange (EAC)</a> أو Exchange Online PowerShell لإنشاء هذه القواعد. بالإضافة إلى قواعد التشفير الشاملة، يمكنك أيضا اختيار تمكين خيارات تشفير الرسائل الفردية للمستخدمين النهائيين أو تعطيلها.

لا يمكنك تشفير البريد الوارد من المرسلين من خارج مؤسستك.

إذا قمت مؤخرا بالرحل من Active Directory RMS إلى Azure حماية البيانات، فستحتاج إلى مراجعة قواعد تدفق البريد الموجودة لضمان استمرارها في العمل في بيئتك الجديدة. أيضا، لاستخدام تشفير الرسائل في Microsoft Purview مع Azure حماية البيانات، تحتاج إلى تحديث قواعد تدفق البريد الموجودة. وإلا، سيستمر المستخدمون في تلقي البريد المشفر الذي يستخدم تنسيق مرفق HTML السابق بدلا من التجربة الجديدة السلسة. إذا لم تقم بإعداد تشفير الرسائل بعد، فراجع [إعداد تشفير الرسائل في Microsoft Purview](set-up-new-message-encryption-capabilities.md) للحصول على المعلومات.

للحصول على معلومات حول المكونات التي تشكل قواعد تدفق البريد وكيفية عمل قواعد تدفق البريد، راجع [قواعد تدفق البريد (قواعد النقل) في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules). للحصول على معلومات إضافية حول كيفية عمل قواعد تدفق البريد مع Azure حماية البيانات، راجع [تكوين قواعد تدفق البريد Exchange Online لتسميات Azure حماية البيانات](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> بالنسبة إلى بيئات Exchange المختلطة، يمكن للمستخدمين المحليين إرسال البريد المشفر وتلقيه باستخدام تشفير الرسائل فقط إذا تم توجيه البريد الإلكتروني عبر Exchange Online. لتكوين تشفير الرسائل في بيئة Exchange المختلطة، تحتاج أولا إلى [تكوين مختلط باستخدام معالج التكوين المختلط](/Exchange/exchange-hybrid) ثم [تكوين البريد للتدفق من Office 365 إلى خادم البريد الإلكتروني](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) [وتكوين البريد للتدفق من خادم البريد الإلكتروني إلى Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365). بمجرد تكوين البريد للتدفق عبر Office 365، يمكنك تكوين قواعد تدفق البريد لتشفير الرسائل باستخدام هذه الإرشادات.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-microsoft-purview-message-encryption"></a>إنشاء قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني باستخدام تشفير الرسائل في Microsoft Purview

يمكنك تعريف قواعد تدفق البريد لتشغيل تشفير الرسائل باستخدام EAC.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-microsoft-purview-message-encryption"></a>استخدم EAC لإنشاء قاعدة لتشفير رسائل البريد الإلكتروني باستخدام تشفير الرسائل في Microsoft Purview

1. في مستعرض ويب، باستخدام حساب العمل أو المؤسسة التعليمية الذي تم منحه أذونات المسؤول العام، [سجل الدخول إلى Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. اختر **لوحة مسؤول**.

3. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>، اختر **مسؤول مراكز** \> **Exchange**.

4. في EAC، انتقل إلى **"قواعد** **تدفق** \> البريد" وحدد أيقونة **"جديد**![".](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**إنشاء قاعدة جديدة**. لمزيد من المعلومات حول استخدام EAC، راجع [مركز إدارة Exchange في Exchange Online](/exchange/exchange-admin-center).

5. في **الاسم**، اكتب اسما للقاعدة، مثل تشفير البريد DrToniRamos@hotmail.com.

6. في **تطبيق هذه القاعدة إذا**، حدد شرطا، وأدخل قيمة إذا لزم الأمر. على سبيل المثال، لتشفير الرسائل التي ستنتقل إلى DrToniRamos@hotmail.com:

   1. في **تطبيق هذه القاعدة إذا**، حدد **المستلم.**

   2. حدد اسما موجودا من قائمة جهات الاتصال أو اكتب عنوان بريد إلكتروني جديدا في خانة **الاختيار "أسماء** ".

      - لتحديد اسم موجود، حدده من القائمة ثم انقر فوق **"موافق**".

      - لإدخال اسم جديد، اكتب عنوان بريد إلكتروني في خانة **الاختيار "أسماء** " ثم حدد **"التحقق من الأسماء** \> **" "موافق**".

7. لإضافة المزيد من الشروط، اختر **المزيد من الخيارات** ثم اختر **إضافة شرط** وحدد من القائمة.

   على سبيل المثال، لتطبيق القاعدة فقط إذا كان المستلم خارج مؤسستك، حدد **إضافة شرط** ثم حدد **المستلم خارجي/داخلي** \> **خارج المؤسسة** \> **موافق**.

8. لتمكين تشفير الرسالة، من **القيام بما يلي**، حدد **"تعديل أمان الرسالة**" ثم اختر **"تطبيق Office 365 تشفير الرسائل وحماية الحقوق**". حدد قالب RMS من القائمة، واختر **"حفظ"**، ثم اختر **"موافق**".
  
  تتضمن قائمة القوالب جميع القوالب والخيارات الافتراضية بالإضافة إلى أي قوالب مخصصة قمت بإنشائها للاستخدام من قبل Office 365. إذا كانت القائمة فارغة، فتأكد من إعداد تشفير الرسائل في Microsoft Purview كما هو موضح في [إعداد تشفير الرسائل في Microsoft Purview](set-up-new-message-encryption-capabilities.md). للحصول على معلومات حول القوالب الافتراضية، راجع [تكوين القوالب وإدارتها ل Azure حماية البيانات](/information-protection/deploy-use/configure-policy-templates). للحصول على معلومات حول الخيار **"عدم إعادة التوجيه** "، راجع [الخيار "عدم إعادة التوجيه" لرسائل البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). للحصول على معلومات حول خيار **التشفير فقط** ، راجع [خيار التشفير فقط لرسائل البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  يمكنك اختيار **إضافة إجراء** إذا كنت تريد تحديد إجراء آخر.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-microsoft-purview-message-encryption"></a>استخدم EAC لتحديث قاعدة تدفق بريد موجودة لاستخدام تشفير الرسائل في Microsoft Purview

1. في مستعرض ويب، باستخدام حساب العمل أو المؤسسة التعليمية الذي تم منحه أذونات المسؤول العام، [سجل الدخول إلى Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. اختر **لوحة مسؤول**.

3. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>، اختر **مسؤول مراكز** \> **Exchange**.

4. في EAC، انتقل إلى **قواعد** **تدفق** \> البريد.

5. في قائمة قواعد تدفق البريد، حدد القاعدة التي تريد تعديلها لاستخدامها مع تشفير الرسائل في Microsoft Purview ثم اختر **أيقونة "تحرير**![".](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)

6. لتمكين التشفير باستخدام تشفير الرسائل في Microsoft Purview، من **القيام بما يلي**، اختر **"تعديل أمان الرسالة**" ثم اختر **"تطبيق Office 365 تشفير الرسائل وحماية الحقوق**". حدد قالب RMS من القائمة، واختر **"حفظ"** ، ثم اختر **"موافق**".

   تتضمن قائمة القوالب جميع القوالب والخيارات الافتراضية بالإضافة إلى أي قوالب مخصصة قمت بإنشائها للاستخدام من قبل Office 365. إذا كانت القائمة فارغة، فتأكد من إعداد تشفير الرسائل في Microsoft Purview كما هو موضح في [إعداد تشفير الرسائل في Microsoft Purview](set-up-new-message-encryption-capabilities.md). للحصول على معلومات حول القوالب الافتراضية، راجع [تكوين القوالب وإدارتها ل Azure حماية البيانات](/information-protection/deploy-use/configure-policy-templates). للحصول على معلومات حول الخيار "عدم إعادة التوجيه"، راجع [الخيار "عدم إعادة التوجيه" لرسائل البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). للحصول على معلومات حول خيار التشفير فقط، راجع [الخيار "تشفير فقط" لرسائل البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   يمكنك اختيار **إضافة إجراء** إذا كنت تريد تحديد إجراء آخر.

7. من القائمة **"قم بما يلي** "، قم بإزالة أي إجراءات تم تعيينها **لتعديل أمان** \> الرسالة **تطبيق الإصدار السابق من OME**.

8. اختر **"حفظ**".

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-microsoft-purview-message-encryption"></a>إنشاء قواعد تدفق البريد لإزالة التشفير لرسائل البريد الإلكتروني باستخدام تشفير الرسائل في Microsoft Purview

يمكنك تعريف قواعد تدفق البريد لإزالة تشفير الرسائل باستخدام تشفير الرسائل في Microsoft Purview باستخدام EAC.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-microsoft-purview-message-encryption"></a>استخدم EAC لإنشاء قاعدة لإزالة التشفير من رسائل البريد الإلكتروني باستخدام تشفير الرسائل في Microsoft Purview

يمكنك إزالة التشفير من الرسائل التي تم تطبيقها من قبل مؤسستك. يمكنك أيضا إزالة التشفير من أي مرفقات مشفرة للتأكد من أن رسالة البريد الإلكتروني بأكملها بدون أي حماية.

1. في مستعرض ويب، باستخدام حساب العمل أو المؤسسة التعليمية الذي تم منحه أذونات المسؤول العام، [سجل الدخول إلى Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. اختر **لوحة مسؤول**.

3. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>، اختر **مسؤول مراكز** \> **Exchange**.

4. في EAC، انتقل إلى **"قواعد** **تدفق** \> البريد" وحدد أيقونة **"جديد**![".](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**إنشاء قاعدة جديدة**. لمزيد من المعلومات حول استخدام EAC، راجع [مركز إدارة Exchange في Exchange Online](/exchange/exchange-admin-center).

5. في **الاسم**، اكتب اسما للقاعدة، مثل `Remove encryption from outgoing mail`.

6. في **تطبيق هذه القاعدة إذا**، حدد الشروط التي يجب إزالة التشفير فيها من الرسائل. إضافة **المرسل موجود** \> **داخل المؤسسة** لإرسال البريد _أو_ **أن المستلم موجود** \> **داخل المؤسسة** لتلقي البريد.

7. في **"القيام بما يلي"**، حدد **"تعديل" أمان** \> الرسالة **"إزالة Office 365 تشفير الرسائل وحماية الحقوق المطبقة من قبل المؤسسة**".

8. (اختياري) في **"القيام بما يلي"**، حدد **"تعديل حماية** **حقوق المرفق" التي تطبقها المؤسسة على** أمان \> الرسالة.

حفظ القاعدة.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-microsoft-purview-message-encryption"></a>إنشاء قواعد تدفق البريد لتشفير الرسائل Office 365 دون تشفير الرسائل في Microsoft Purview

إذا لم تقم بعد بنقل مؤسستك إلى تشفير الرسائل في Microsoft Purview، توصي Microsoft بوضع خطة للتنقل بمجرد أن يكون ذلك معقولا لمؤسستك. للحصول على الإرشادات، راجع [إعداد تشفير الرسائل في Microsoft Purview](set-up-new-message-encryption-capabilities.md). بخلاف ذلك، راجع [تعريف قواعد تدفق البريد لتشفير الرسائل Office 365 التي لا تستخدم تشفير الرسائل في Microsoft Purview](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption).

## <a name="related-content"></a>المحتوى ذو الصلة

[التشفير في Office 365](encryption.md)

[إعداد تشفير الرسائل من Microsoft Purview](set-up-new-message-encryption-capabilities.md)

[إضافة علامة تجارية إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md)

[قواعد تدفق البريد (قواعد النقل) في Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
