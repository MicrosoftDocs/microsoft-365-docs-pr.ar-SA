---
title: إزالة نفسك من قائمة المرسلين المحظورين والعنوان 5.7.511 رفض Access الأخطاء
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/18/2016
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0bcecdd4-3343-4cc0-9e58-e19d4de515e8
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: في هذه المقالة، ستتعلم كيفية استخدام مدخل القائمة لإزالة نفسك من قائمة المرسلين المحظورين Microsoft 365. هذه هي أفضل استجابة لعنوان 5.7.511 تم رفض أخطاء Access.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 83822faaf1c667524dd88fc1bba400c10fa30ac3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647722"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>استخدم مدخل إلغاء القائمة لإزالة نفسك من قائمة المرسلين المحظورين وعنوان الأخطاء التي تم رفضها في Access 5.7.511

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

هل تتلقى رسالة خطأ عند محاولة إرسال بريد إلكتروني إلى مستلم يكون عنوان بريده الإلكتروني في Microsoft 365 (على سبيل المثال والعنوان 5.7.511 تم رفض الوصول)؟ إذا كنت تعتقد أنه لا يجب أن تتلقى رسالة الخطأ، يمكنك استخدام مدخل الإزالة لإزالة نفسك من قائمة المرسلين المحظورين.

## <a name="what-is-the-blocked-senders-list"></a>ما هي قائمة المرسلين المحظورين؟

تستخدم Microsoft قائمة المرسلين المحظورين لحماية عملائها من البريد العشوائي والانتحال وهجمات التصيد الاحتيالي. تم وضع علامة على عنوان IP الخاص بخادم البريد، أي العنوان الذي يستخدمه خادم البريد لتعريف نفسه على الإنترنت، على أنه تهديد محتمل Microsoft 365 لأحد الأسباب المتنوعة. عندما يضيف Microsoft 365 عنوان IP إلى القائمة، فإنه يمنع جميع الاتصالات الإضافية بين عنوان IP وأي من عملائنا من خلال مراكز البيانات الخاصة بنا.

ستعرف أنه تمت إضافتك إلى القائمة عندما تتلقى استجابة لرسالة بريد تتضمن خطأ يبدو مثل هذا:

> 550 5.7.606-649 تم رفض الوصول، وحظر إرسال IP [_عنوان IP_] (على سبيل المثال. 5.7.511 تم رفض الوصول: لطلب الإزالة من هذه القائمة، يرجى زيارة <https://sender.office.com/> الإرشادات واتباعها. لمزيد من المعلومات، راجع [تقارير البريد الإلكتروني بعدم التسليم في Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

حيث  _عنوان IP_ هو عنوان IP للكمبيوتر الذي يتم تشغيل خادم البريد عليه.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>التحقق من المرسلين قبل إزالتهم من قائمة المرسلين المحظورين

هناك أسباب وجيهة لانتهاء المرسلين في قائمة المرسلين المحظورين، ولكن يمكن أن تحدث أخطاء. ألق نظرة على هذا الفيديو للحصول على شرح متوازن للمرسلين المحظورين وإزالة القوائم.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>لاستخدام مدخل إلغاء القائمة لإزالة نفسك من قائمة المرسلين المحظورين (بعد رفض أخطاء مثل 5.7.511 Access)

1. في مستعرض ويب، انتقل إلى <https://sender.office.com>.

2. اتبع الإرشادات الموجودة على الصفحة. تأكد من استخدام عنوان البريد الإلكتروني الذي تم إرسال رسالة الخطأ إليه وعنوان IP المحدد في رسالة الخطأ. يمكنك إدخال عنوان بريد إلكتروني واحد وعنوان IP واحد فقط لكل زيارة.

3. انقر فوق **"إرسال**".

    يرسل المدخل رسالة بريد إلكتروني إلى عنوان البريد الإلكتروني الذي توفره. سيبدو البريد الإلكتروني كما يلي:

    :::image type="content" source="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png" alt-text="البريد الإلكتروني الذي تلقيته عند إرسال طلب من خلال مدخل القوائم" lightbox="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png":::

4. انقر فوق ارتباط التأكيد في البريد الإلكتروني المرسل إليك بواسطة مدخل الإزالة.

    هذا يعيدك إلى مدخل القوائم.

5. في مدخل الإزالة، انقر فوق **"Delist IP**".

    بعد إزالة عنوان IP من قائمة المرسلين المحظورين، سيتم تسليم رسائل البريد الإلكتروني من عنوان IP هذا إلى المستلمين الذين يستخدمون Microsoft 365. لذا، تأكد من أنك واثق من أن البريد الإلكتروني المرسل من عنوان IP هذا لن يكون مسيئا أو ضارا؛ وإلا، فقد يتم حظر عنوان IP مرة أخرى.

    > [!NOTE]
    > قد يستغرق الأمر ما يصل إلى 24 ساعة أو قد تختلف النتائج على نطاق واسع قبل إزالة القيود.

راجع [إنشاء قوائم مرسلين آمنة في EOP](create-safe-sender-lists-in-office-365.md) وحماية [البريد العشوائي الصادر في EOP](outbound-spam-controls.md) لمنع حظر IP.

### <a name="how-do-fix-error-code-57511"></a>كيف يمكن إصلاح رمز الخطأ 5.7.511

عندما تكون هناك مشكلة في تسليم رسالة بريد إلكتروني أرسلتها، يرسل Microsoft 365 أو Office 365 رسالة بريد إلكتروني لإعلامك بذلك. البريد الإلكتروني الذي تتلقاه هو إعلام بحالة التسليم، يعرف أيضا باسم DSN أو رسالة إعلام البريد المرتد. يسمى النوع الأكثر شيوعا تقرير بعدم التسليم (NDR) ويخبرك بأنه لم يتم تسليم رسالة. في بعض الحالات، يجب على Microsoft إجراء تحقيقات إضافية ضد نسبة استخدام الشبكة من IP الخاص بك، وإذا كنت تتلقى رمز NDR 5.7.511، **فلن** تتمكن من استخدام مدخل القائمة.

> 550 5.7.511 تم رفض الوصول، المرسل المحظور[xxx.xxx.xxx.xxx]. لطلب الإزالة من هذه القائمة، أعد توجيه هذه الرسالة إلى delist@messaging.microsoft.com. لمزيد من المعلومات، انتقل إلى <https://go.microsoft.com/fwlink/?LinkId=526653>.

في البريد الإلكتروني لطلب الإزالة من هذه القائمة، قم بتوفير رمز التقرير بعدم التسليم الكامل وعنوان IP. ستتصل بك Microsoft في غضون 48 ساعة باستخدام الخطوات التالية.

## <a name="more-information"></a>معلومات إضافية

نموذج إلغاء القوائم **ل Outlook.com، يمكن العثور على خدمة المستهلك** [هنا](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). تأكد من قراءة [الأسئلة المتداولة](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) أولا لاتجاه _الإرسال_ .
