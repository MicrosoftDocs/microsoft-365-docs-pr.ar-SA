---
title: استخدم مرسلي ARC الموثوق بهم للأجهزة والخدمات المشروعة بين المرسل والمتلقي
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: سلسلة الاستلام المصادق عليها (ARC) هي مصادقة البريد الإلكتروني التي تحاول الحفاظ على نتائج المصادقة عبر الأجهزة وأي تدفقات بريد غير مباشرة تأتي بين المرسل والمستلم. فيما يلي كيفية إجراء استثناءات لمرسلي ARC الموثوق بهم.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7523a17eb8440d6b567d0414b63153bfc33338a2
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67107294"
---
# <a name="make-a-list-of-trusted-arc-senders-to-trust-legitimate-indirect-mailflows"></a>إنشاء قائمة بمرسلي ARC الموثوق بهم للوثوث بتدفقات البريد غير المباشرة *المشروعة*

**ينطبق على**

- Exchange Online Protection
- خطة 1 وخطة 2 من Microsoft Defender لـ Office 365
- Microsoft 365 Defender

يتم استخدام آليات مصادقة البريد الإلكتروني مثل [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md) [وDKIM](use-dkim-to-validate-outbound-email.md) [وDMARC](use-dmarc-to-validate-email.md) للتحقق من مرسلي رسائل البريد الإلكتروني *من أجل سلامة* مستلمي البريد الإلكتروني، ولكن قد تقوم بعض الخدمات المشروعة بإجراء تغييرات على البريد الإلكتروني بين المرسل والمستلم. **في Microsoft 365 Defender، ستساعد ARC على تقليل حالات فشل تسليم SPF وDKIM وDMARC التي تحدث بسبب تدفقات البريد غير المباشرة *المشروعة*.**

## <a name="authenticated-received-chain-arc-in-microsoft-365-defender-for-office"></a>سلسلة المستلمين المصادق عليها (ARC) في Microsoft 365 Defender ل Office

يمكن للخدمات التي تقوم بتعديل المحتوى أثناء نقل الرسالة قبل التسليم إلى مؤسستك إبطال توقيع البريد الإلكتروني DKIM والتأثير على مصادقة الرسالة. عندما تقوم هذه الخدمات الوسيطة بتنفيذ مثل هذه الإجراءات، يمكن استخدام ARC لتوفير تفاصيل المصادقة الأصلية قبل إجراء التعديلات، والتي يمكن لمؤسستك بعد ذلك الوثوق بها للمساعدة في مصادقة الرسالة.  

**تتيح أدوات تسرب ARC الموثوق بها للمسؤولين إضافة قائمة بالوسطاء *الموثوق بهم* إلى مدخل Microsoft 365 Defender.** تسمح فقمات ARC الموثوق بها لشركة Microsoft بتوقيع ARC من هذه الوسطاء الموثوق بهم، ما يمنع هذه الرسائل المشروعة من الفشل في سلسلة المصادقة.

> [!NOTE]
> ***فقمات ARC الموثوق بها هي قائمة أنشأها المسؤول من المجالات الوسيطة التي نفذت تسرب ARC.*** عند توجيه رسالة بريد إلكتروني إلى Office 365 من خلال وسيط ARC الموثوق به لمستأجر Office 365، تتحقق Microsoft من صحة توقيع ARC، واستنادا إلى نتائج ARC، يمكن أن تحترم تفاصيل المصادقة المقدمة.

## <a name="when-to-use-trusted-arc-sealers"></a>متى تستخدم فقمات ARC الموثوق بها؟

هناك حاجة إلى قائمة باختاقم ARC الموثوق بها فقط عندما يكون الوسطاء جزءا من تدفق البريد الإلكتروني للمؤسسة و:

1. قد يعدل عنوان البريد الإلكتروني أو محتويات البريد الإلكتروني.
2. قد تتسبب المصادقة في فشل لأسباب أخرى (على سبيل المثال، عن طريق إزالة المرفقات).
 
بإضافة مانع تسرب ARC موثوق به، سيقوم Office 365 بالتحقق من صحة نتائج المصادقة التي توفرها أداة الفقمة عند تسليم البريد إلى المستأجر في Office 365.

**يجب على المسؤولين إضافة *الخدمات المشروعة فقط* كققمات ARC موثوق بها.** ستساعد إضافة الخدمات التي تستخدمها المؤسسة صراحة وتعرفها فقط الرسائل التي يجب أن تمر أولا عبر خدمة لتمرير عمليات التحقق من مصادقة البريد الإلكتروني، ومنع إرسال الرسائل المشروعة إلى *"غير هام* " بسبب فشل المصادقة.

## <a name="steps-to-add-a-trusted-arc-sealer-to-microsoft-365-defender"></a>خطوات لإضافة مانع تسرب ARC موثوق به إلى Microsoft 365 Defender

تعرض فقمات ARC الموثوق بها في مدخل Microsoft 365 Defender جميع فقمات ARC التي أقر بها المستأجر الخاص بك وأضفتها إليه.

**لإضافة مانع تسرب ARC موثوق به جديد في مدخل المسؤول:**

1. انتقل إلى صفحة [إعدادات مصادقة البريد الإلكتروني](https://security.microsoft.com/authentication?viewid=ARC) .

2. إذا كانت هذه هي المرة الأولى التي تضيف فيها مانع تسرب ARC موثوقا به، فانقر فوق الزر "إضافة".
3. أضف فقمات ARC الموثوق بها في مربع النص المعروض.
    1. لاحظ أنك تضيف المجالات (مثال fabrikam.com).
    1. *يجب أن* يكون اسم المجال الذي تدخله هنا مطابقا للمجال المعروض في علامة المجال 'd' في رؤوس ARC-Seal و ARC-Message-Signature (على رؤوس البريد الإلكتروني للرسالة).
    1. يمكنك الاطلاع عليها في خصائص الرسالة في Outlook.

## <a name="steps-to-validate-your-trusted-arc-sealer"></a>خطوات للتحقق من صحة مانع تسرب ARC الموثوق به

إذا كان هناك فقم ARC من جهة خارجية قبل وصول الرسالة إلى Microsoft 365 Defender، **فتحقق من الرؤوس بمجرد تلقي البريد الإلكتروني وعرض أحدث رؤوس ARC**.

في رأس ***ARC-Authentication-Results** الأخير، تحقق مما إذا كان التحقق من صحة ARC مدرجا ك _*pass**.

يشير رأس ARC الذي يسرد "oda" من 1 إلى أنه تم *التحقق من ARC* السابق، وأن مانع تسرب ARC السابق *موثوق به*، ويمكن استخدام *نتيجة المرور* السابقة لتجاوز فشل DMARC الحالي.

**رأس تمرير ARC يظهر oda=1**

راجع أساليب مصادقة البريد الإلكتروني في نهاية كتلة الرأس هذه لنتيجة oda.

``
ARC-Authentication-Results: i=2; mx.microsoft.com 1; spf=pass (sender ip is
40.107.65.78) smtp.rcpttodomain=microsoft.com
smtp.mailfrom=sampledoamin.onmicrosoft.com; dmarc=bestguesspass action=none
header.from=sampledoamin.onmicrosoft.com; dkim=none (message not signed);
arc=pass (0 oda=1 ltdi=1
spf=[1,1,smtp.mailfrom=sampledoamin.onmicrosoft.com]
dkim=[1,1,header.d=sampledoamin.onmicrosoft.com]
dmarc=[1,1,header.from=sampledoamin.onmicrosoft.com])
``

للتحقق مما إذا تم استخدام نتيجة ARC لتجاوز فشل DMARC *، ابحث عن* نتيجة الحساب *وسبب التعليمات البرمجية (130)* في الرأس.

راجع الإدخال الأخير في كتلة الرأس هذه للعثور على *الحوسبة* *والسبب*.

``
Authentication-Results: spf=fail (sender IP is 51.163.158.241)
smtp.mailfrom=contoso.com; dkim=fail (body hash did not verify)
header.d=contoso.com;dmarc=fail action=none
header.from=contoso.com;compauth=pass reason=130
``

## <a name="powershell-steps-to-add-or-remove-a-trusted-arc-sealer"></a>خطوات PowerShell لإضافة مانع تسرب ARC موثوق به أو إزالته

**يمكن للمسؤولين أيضا إعداد تكوينات ARC باستخدام Exchange Online PowerShell.**

1. الاتصال Exchange Online PowerShell.
2. Connect-ExchangeOnline.
3. لإضافة مجال أو تحديثه إلى مانع تسرب ARC موثوق به:
</br>
``
Set-ArcConfig -Identity default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>أو</br>
``
Set-ArcConfig -Identity {tenant name/tenanid}\default -ArcTrustedSealers {a list of arc signing domains split by comma}
``
</br>تحتاج إلى توفير معلمة الهوية *-Identity* الافتراضية عند تشغيل *Set-ArcConfig*. يجب مطابقة الفقمات الموثوق بها بقيمة العلامة 'd' في *رأس ARC-Seal*.

4. عرض فقمات ARC الموثوق بها:
</br>
``
Get-ArcConfig
`` أو ``
Get-ArcConfig - Organization {tenant name}
``

## <a name="trusted-arc-sealer-mailflow-graphics"></a>رسومات تدفق بريد ARC الموثوق بها

تقوم هذه الرسومات التخطيطية بتباين عمليات تدفق البريد باستخدام مانع تسرب ARC موثوق به وبدونه، عند استخدام أي من مصادقة البريد الإلكتروني SPF وDKIM وDMARC. في كلا الرسمين، هناك خدمات شرعية تستخدمها الشركة يجب أن تتدخل في تدفق البريد، وأحيانا تنتهك معايير مصادقة البريد الإلكتروني عن طريق تغيير إرسال عناوين IP والكتابة إلى رأس البريد الإلكتروني. **في الحالة الأولى، توضح نسبة استخدام الشبكة غير المباشرة لتدفق البريد النتيجة *قبل* أن يضيف المسؤولون مانع تسرب ARC موثوقا به.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-without-trusted-arc-sealer.PNG" alt-text="في هذا الرسم، تنشر Contoso SPF وDKIM وDMARC كجزء من أمان البريد الإلكتروني القياسي. يرسل المرسل الذي يستخدم SPF البريد من داخل contoso.com إلى fabrikam.com، ويمرر هذا البريد عبر خدمة تابعة لجهة خارجية قامت Contoso بتعيينها، وتعدل هذه الخدمة عنوان IP المرسل في رأس البريد الإلكتروني. يفشل البريد في SPF بسبب IP المعدل، وDKIM لأنه تم تعديل المحتوى في جهة خارجية، أثناء التحقق من DNS في EOP. يفشل DMARC بسبب فشل SPF وDKIM. يتم إرسال الرسالة إلى &quot;غير هام&quot; أو &quot;عزل&quot; أو &quot;مرفوض&quot;.":::

هنا، ترى نفس المؤسسة **بعد الاستفادة من القدرة على إنشاء مانع تسرب ARC موثوق به.**

:::image type="content" source="../../media/m365d-indirect-traffic-flow-with-trusted-arc-sealer.PNG" alt-text="في شركة Contoso للرسم الثاني، أنشأت قائمة من فقمات ARC الموثوق بها. يرسل نفس المستخدم بريدا ثانيا من contoso.com إلى fabrikam.com. تعدل خدمة الجهة الخارجية التي عينتها شركة Contoso عنوان IP للمرسل في رأس البريد. ولكن هذه المرة قامت الخدمة بتنفيذ تسرب ARC، ولأن مسؤول المستأجر قد أضاف بالفعل مجال الطرف الثالث إلى أدوات تسرب ARC الموثوق بها، يتم قبول التعديل. فشل SPF لعنوان IP الجديد. يفشل DKIM بسبب تعديل المحتوى. يفشل DMARC بسبب حالات الفشل السابقة. ولكن ARC يتعرف على التعديلات، ويصدر تمريرا، ويقبل التغييرات. كما يتلقى الانتحال تمريرا. يتم إرسال الرسالة إلى علبة الوارد.":::

## <a name="next-steps-after-you-set-up-arc-for-microsoft-365-defender-for-office"></a>الخطوات التالية: بعد إعداد ARC ل Microsoft 365 Defender ل Office

بعد الإعداد، تحقق من رؤوس ARC باستخدام [محلل رأس الرسالة](https://mha.azurewebsites.net).

راجع [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md) [وDKIM](use-dkim-to-validate-outbound-email.md) [وDMARC](use-dmarc-to-validate-email.md) وخطوات التكوين.
