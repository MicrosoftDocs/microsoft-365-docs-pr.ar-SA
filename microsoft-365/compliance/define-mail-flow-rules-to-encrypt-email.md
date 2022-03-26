---
title: تعريف قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني
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
description: يمكن للمسؤولين تعلم كيفية إنشاء قواعد تدفق البريد (قواعد النقل) لتشفير الرسائل وفك تشفيرها باستخدام تشفير الرسائل من Office 365.
ms.openlocfilehash: bb50ed5d2b22fd74d4a6f88eba29f82d10be1f50
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/16/2022
ms.locfileid: "63565887"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>تعريف قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني

كمسؤول يدير Exchange Online، يمكنك إنشاء قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) للمساعدة في حماية رسائل البريد الإلكتروني التي ترسلها وتستلمها. يمكنك إعداد القواعد لتشفير أي رسائل بريد إلكتروني الصادرة وإزالة التشفير من الرسائل المشفرة الواردة من داخل مؤسستك أو من الردود على الرسائل المشفرة المرسلة من مؤسستك. يمكنك استخدام Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">إدارة (EAC)</a> أو Exchange Online PowerShell لإنشاء هذه القواعد. بالإضافة إلى قواعد التشفير الشاملة، يمكنك أيضا اختيار تمكين خيارات تشفير الرسائل الفردية للمستخدمين النهائيين أو تعطيلها.

لا يمكنك تشفير البريد الوارد من المرسلين من خارج مؤسستك.

إذا قمت مؤخرا بالترحيل من Active Directory RMS إلى Azure Information Protection، ستحتاج إلى مراجعة قواعد تدفق البريد الموجودة للتأكد من أنها تستمر في العمل في بيئتك الجديدة. أيضا، إذا كنت تريد الاستفادة من إمكانيات تشفير الرسائل من Office 365 (OME) الجديدة المتوفرة لك من خلال Azure Information Protection، ستحتاج إلى تحديث قواعد تدفق البريد الموجودة. وإلا، سيستمر المستخدمون في تلقي البريد المشفر الذي يستخدم تنسيق مرفق HTML السابق بدلا من تجربة OME الجديدة السلسة. إذا لم تقم بإعداد OME بعد، فحدد إعداد إمكانيات تشفير الرسائل من Office 365 [جديدة](set-up-new-message-encryption-capabilities.md) للحصول على المعلومات.

للحصول على معلومات حول المكونات التي مكونة قواعد تدفق البريد وكيفية عمل قواعد تدفق البريد، راجع قواعد تدفق البريد [(قواعد النقل) في](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) Exchange Online. للحصول على معلومات إضافية حول كيفية عمل قواعد تدفق البريد مع Azure Information Protection، راجع Exchange Online قواعد تدفق البريد لتسميات [Azure Information Protection](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> بالنسبة إلى Exchange المختلطة، يمكن للمستخدمين في الموقع إرسال البريد المشفر وتلقيه باستخدام OME فقط إذا تم توجيه البريد الإلكتروني عبر Exchange Online. لتكوين OME في بيئة Exchange مختلطة، ستحتاج أولا إلى تكوين مختلط باستخدام معالج التكوين المختلط ثم [](/Exchange/exchange-hybrid) تكوين البريد للتدفق من [Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) إلى خادم البريد الإلكتروني وتكوين البريد للتدفق من خادم البريد الإلكتروني إلى [Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365). بعد تكوين البريد للتدفق عبر Office 365، يمكنك تكوين قواعد تدفق البريد ل OME باستخدام هذه الإرشادات.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-the-new-ome-capabilities"></a>إنشاء قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني باستخدام قدرات OME الجديدة

يمكنك تعريف قواعد تدفق البريد الخاصة بتشغيل تشفير الرسائل باستخدام قدرات OME الجديدة باستخدام EAC.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-the-new-ome-capabilities"></a>استخدام EAC لإنشاء قاعدة لتشفير رسائل البريد الإلكتروني باستخدام قدرات OME الجديدة

1. في مستعرض ويب، باستخدام حساب عمل أو مدرسة تم منحه أذونات المسؤول العام، سجل الدخول [إلى](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) Office 365.

2. اختر لوحة **المسؤول** .

3. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365،</a> اختر **مراكز الإدارة Exchange** \> **.**

4. في EAC، انتقل إلى **قواعد تدفق** \> **البريد** وحدد **أيقونة جديد** ![جديد.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**إنشاء قاعدة جديدة**. لمزيد من المعلومات حول استخدام EAC، راجع Exchange [مركز الإدارة في Exchange Online](/exchange/exchange-admin-center).

5. في **الاسم**، اكتب اسما للقاعدة، مثل تشفير البريد DrToniRamos@hotmail.com.

6. في **تطبيق هذه القاعدة إذا**، حدد شرطا، وأدخل قيمة إذا لزم الأمر. على سبيل المثال، لتشفير الرسائل التي سيتم DrToniRamos@hotmail.com:

   1. في **تطبيق هذه القاعدة إذا**، حدد **المستلم هو**.

   2. حدد اسما موجودا من قائمة جهات الاتصال أو اكتب عنوان بريد إلكتروني جديدا في **خانة الاختيار أسماء** .

      - لتحديد اسم موجود، حدده من القائمة ثم انقر فوق **موافق**.

      - لإدخال اسم جديد، اكتب عنوان بريد إلكتروني في **خانة الاختيار أسماء** ثم حدد **التحقق من الأسماء** \> **موافق**.

7. لإضافة المزيد من الشروط، اختر **المزيد من الخيارات** ثم اختر **إضافة شرط** وحدد من القائمة.

   على سبيل المثال، لتطبيق القاعدة فقط إذا كان المستلم من خارج مؤسستك، حدد إضافة شرط  ثم حدد المستلم **خارجي/داخلي** \> خارج **المؤسسة** \> **موافق**.

8. لتمكين التشفير باستخدام قدرات OME الجديدة، من قم **بما** يلي، حدد تعديل أمان الرسالة  ثم اختر تطبيق تشفير الرسائل من Office 365 **وحماية الحقوق**. حدد قالب RMS من القائمة، واختر **حفظ**، ثم اختر **موافق**.
  
  تتضمن قائمة القوالب كل القوالب والخيارات الافتراضية بالإضافة إلى أي قوالب مخصصة قمت بإنشاءها لاستخدامها من قبل Office 365. إذا كانت القائمة فارغة، فتأكد من إعداد تشفير الرسائل من Office 365 باستخدام الإمكانات الجديدة كما هو موضح في إعداد [قدرات تشفير الرسائل من Office 365 جديدة](set-up-new-message-encryption-capabilities.md). للحصول على معلومات حول القوالب الافتراضية، راجع تكوين القوالب وإدارتها [ل Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). للحصول على معلومات حول الخيار **عدم إعادة توجيه** ، راجع [الخيار عدم إعادة توجيه رسائل البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). للحصول على معلومات حول **خيار التشفير فقط** ، راجع [خيار التشفير فقط لر البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  يمكنك اختيار **إضافة إجراء** إذا كنت تريد تحديد إجراء آخر.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-the-new-ome-capabilities"></a>استخدام EAC لتحديث قاعدة تدفق بريد موجودة لاستخدام قدرات OME الجديدة

1. في مستعرض ويب، باستخدام حساب عمل أو مدرسة تم منحه أذونات المسؤول العام، سجل الدخول [إلى](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) Office 365.

2. اختر لوحة **المسؤول** .

3. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365،</a> اختر **مراكز الإدارة Exchange** \> **.**

4. في EAC، انتقل إلى **قواعد تدفق** \> **البريد**.

5. في قائمة قواعد تدفق البريد، حدد القاعدة التي تريد تعديلها لاستخدام إمكانات OME الجديدة، ثم اختر **تحرير** ![أيقونة تحرير.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

6. لتمكين التشفير باستخدام قدرات OME الجديدة، من قم **بما** يلي، اختر تعديل أمان الرسالة  ثم اختر تطبيق تشفير الرسائل من Office 365 **وحماية الحقوق**. حدد قالب RMS من القائمة، واختر **حفظ** ثم اختر **موافق**.

   تتضمن قائمة القوالب كل القوالب والخيارات الافتراضية بالإضافة إلى أي قوالب مخصصة قمت بإنشاءها لاستخدامها من قبل Office 365. إذا كانت القائمة فارغة، فتأكد من إعداد تشفير الرسائل من Office 365 الجديدة كما هو موضح في إعداد قدرات تشفير الرسائل من Office 365 جديدة مضمنة في أعلى [Azure Information Protection](set-up-new-message-encryption-capabilities.md). للحصول على معلومات حول القوالب الافتراضية، راجع تكوين القوالب وإدارتها [ل Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). للحصول على معلومات حول الخيار عدم إعادة توجيه، راجع [الخيار عدم إعادة توجيه رسائل البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). للحصول على معلومات حول خيار التشفير فقط، راجع [الخيار تشفير رسائل البريد الإلكتروني فقط](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   يمكنك اختيار **إضافة إجراء** إذا كنت تريد تحديد إجراء آخر.

7. من القائمة **قم بالقائمة** التالية، قم بإزالة أي إجراءات تم تعيينها إلى **تعديل** \> أمان **الرسالة تطبيق الإصدار السابق من OME**.

8. اختر **حفظ**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-the-new-ome-capabilities"></a>إنشاء قواعد تدفق البريد لإزالة التشفير لرسائل البريد الإلكتروني باستخدام قدرات OME الجديدة

يمكنك تعريف قواعد تدفق البريد لتحريك تشفير الرسائل باستخدام قدرات OME الجديدة باستخدام EAC.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-the-new-ome-capabilities"></a>استخدام EAC لإنشاء قاعدة لإزالة التشفير من رسائل البريد الإلكتروني باستخدام قدرات OME الجديدة

يمكنك إزالة التشفير من الرسائل التي تم تطبيقها بواسطة مؤسستك. يمكنك أيضا إزالة التشفير من أي مرفقات مشفرة لضمان عدم حماية رسالة البريد الإلكتروني بكاملها.

1. في مستعرض ويب، باستخدام حساب عمل أو مدرسة تم منحه أذونات المسؤول العام، سجل الدخول [إلى](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) Office 365.

2. اختر لوحة **المسؤول** .

3. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365،</a> اختر **مراكز الإدارة Exchange** \> **.**

4. في EAC، انتقل إلى **قواعد تدفق** \> **البريد** وحدد **أيقونة جديد** ![جديد.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**إنشاء قاعدة جديدة**. لمزيد من المعلومات حول استخدام EAC، راجع Exchange [مركز الإدارة في Exchange Online](/exchange/exchange-admin-center).

5. في **الاسم**، اكتب اسما للقاعدة، مثل إزالة التشفير من البريد الصادر.

6. في **تطبيق هذه القاعدة إذا**، حدد الشروط التي يجب إزالة التشفير فيها من الرسائل. إضافة **يوجد المرسل** \>   \> داخل المؤسسة لإرسال البريد أو يوجد المستلم داخل **المؤسسة** لتلقي البريد.

7. في **قم بما يلي،** حدد **تعديل** \> أمان الرسالة **إزالة تشفير الرسائل من Office 365 حماية الحقوق التي تطبقها المؤسسة**.

8. (اختياري) في **قم بما يلي،** حدد **تعديل** \> أمان الرسالة **إزالة حماية حقوق المرفقات المطبقة من قبل المؤسسة**.

احفظ القاعدة.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-the-new-capabilities"></a>إنشاء قواعد تدفق البريد تشفير الرسائل من Office 365 دون القدرات الجديدة

إذا لم تكن قد نقلت مؤسستك بعد إلى قدرات OME الجديدة، فإن Microsoft توصي بأن تقوم بإجراء خطة للانتقال إلى قدرات OME الجديدة بمجرد أن تكون معقولة لمنظمتك. للحصول على الإرشادات، راجع إعداد [قدرات تشفير الرسائل من Office 365 الجديدة المضمنة في أعلى Azure Information Protection](set-up-new-message-encryption-capabilities.md). وبخلاف ذلك، راجع تحديد قواعد تدفق البريد [تشفير الرسائل من Office 365 التي لا تستخدم قدرات OME الجديدة](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities).

## <a name="related-content"></a>المحتوى ذي الصلة

[التشفير في Office 365](encryption.md)

[إعداد قدرات تشفير الرسائل من Office 365 الجديدة](set-up-new-message-encryption-capabilities.md)

[إضافة علامة تجارية إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md)

[قواعد تدفق البريد (قواعد النقل) في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
