---
title: إزالة نفسك من قائمة المرسلين المحظورين وعنوان 5.7.511 أخطاء رفض Access
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
description: في هذه المقالة، ستتعرف على كيفية استخدام مدخل الحذف لإزالة نفسك من قائمة المرسلين المحظورين Microsoft 365 المحظورين. هذه هي أفضل استجابة لمعالجة الأخطاء التي تم رفضها في Access 5.7.511.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 58ddb2913ce7ecd047b1d5acb360c8f4c9ff5074
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775775"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>استخدام مدخل الحذف لإزالة نفسك من قائمة المرسلين المحظورين وعنوان 5.7.511 أخطاء رفض Access

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

هل تظهر رسالة خطأ عند محاولة إرسال رسالة بريد إلكتروني إلى مستلم يكون عنوان بريده الإلكتروني في Microsoft 365 (على سبيل المثال، تم رفض الوصول إلى العنوان 5.7.511)؟ إذا كنت تعتقد أنه لا يجب أن تتلقى رسالة الخطأ، يمكنك استخدام مدخل الحذف لإزالة نفسك من قائمة المرسلين المحظورين.

## <a name="what-is-the-blocked-senders-list"></a>ما هي قائمة المرسلين المحظورين؟

تستخدم Microsoft قائمة المرسلين المحظورين لحماية عملائها من هجمات البريد العشوائي والخادع والتصيد الاحتيالي. تم وضع علامة على عنوان IP الخاص بخادم البريد، أي العنوان الذي يستخدمه خادم البريد لتعريف نفسه على الإنترنت، كخطر محتمل على Microsoft 365 لعدة أسباب. عندما Microsoft 365 عنوان IP إلى القائمة، فإنه يمنع أي اتصال آخر بين عنوان IP وأي من عملائنا من خلال مراكز البيانات لدينا.

ستعرف أنك قد أضفت إلى القائمة عندما تتلقى ردا على رسالة بريد تتضمن رسالة خطأ تبدو على شكل ما يلي:

> 550 5.7.606-649 رفض Access، حظر إرسال IP [_عنوان IP_] (على المثال. 5.7.511 رفض الوصول): لطلب الإزالة من هذه القائمة، يرجى <https://sender.office.com/> زيارة هذه القائمة واتبع التوجيهات. لمزيد من المعلومات، راجع [إرسال تقارير بعدم التسليم بالبريد الإلكتروني في Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

حيث  _عنوان IP_ هو عنوان IP للكمبيوتر الذي يتم تشغيل خادم البريد عليه.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>التحقق من المرسلين قبل إزالتهم من قائمة المرسلين المحظورين

ثمة أسباب وجيهة تجعل المرسلين يغلقون قائمة المرسلين المحظورين، ولكن قد تحدث أخطاء. أطلع على هذا الفيديو للحصول على شرح متوازن للمرسلين المحظورين والشطب.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>لاستخدام مدخل الحذف لإزالة نفسك من قائمة المرسلين المحظورين (بعد أخطاء مثل 5.7.511 رفض Access)

1. في مستعرض ويب، انتقل إلى <https://sender.office.com>.

2. اتبع الإرشادات الموجودة على الصفحة. تأكد من استخدام عنوان البريد الإلكتروني الذي تم إرسال رسالة الخطأ له، وعنوان IP المحدد في رسالة الخطأ. يمكنك إدخال عنوان بريد إلكتروني واحد وعنوان IP واحد فقط لكل زيارة.

3. انقر **فوق إرسال**.

    يرسل المدخل بريدا إلكترونيا إلى عنوان البريد الإلكتروني الذي تقوم بتزويده به. سيبدو البريد الإلكتروني كما يلي:

    ![لقطة شاشة للبريد الإلكتروني الذي تم تلقيه عند إرسال طلب عبر مدخل الرفع.](../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)

4. انقر فوق ارتباط التأكيد في البريد الإلكتروني المرسل إليك بواسطة مدخل الشطب.

    سيعيدك ذلك إلى مدخل الشطب.

5. في مدخل الشطب، انقر فوق **Delist IP**.

    بعد إزالة عنوان IP من قائمة المرسلين المحظورين، سيتم تسليم رسائل البريد الإلكتروني من عنوان IP هذا إلى المستلمين الذين يستخدمون Microsoft 365. لذلك، تأكد من أنك واثق من أن البريد الإلكتروني المرسل من عنوان IP هذا لن يكون مسيئا أو ضارا؛ وإلا، فقد يتم حظر عنوان IP مرة أخرى.

    > [!NOTE]
    > قد يستغرق الأمر ما يصل إلى 24 ساعة أو قد تختلف النتائج على نطاق واسع قبل إزالة القيود.

راجع [إنشاء قوائم مرسلين آمنة في EOP](create-safe-sender-lists-in-office-365.md) والحماية من البريد العشوائي الصادر في [EOP](outbound-spam-controls.md) لمنع حظر IP.

### <a name="how-do-fix-error-code-57511"></a>كيفية إصلاح رمز الخطأ 5.7.511

عند وجود مشكلة في تسليم رسالة بريد إلكتروني أرسلتها، Microsoft 365 أو Office 365 رسالة بريد إلكتروني لتعلمك بها. البريد الإلكتروني الذي تتلقاه هو إعلام حالة التسليم، يعرف أيضا باسم DSN أو رسالة إعلام البريد المرتد. يسمى النوع الأكثر شيوعا تقرير بعدم التسليم (NDR) وأخبرك بأنه لم يتم تسليم رسالة. في بعض الحالات، يجب على Microsoft إجراء عمليات تحقيق إضافية ضد حركة المرور من IP، وإذا كنت تتلقى رمز NDR 5.7.511، لن تتمكن من استخدام مدخل الشطب.

> 550 5.7.511 رفض الوصول، المرسل المحظور[xxx.xxx.xxx.xxx]. لطلب الإزالة من هذه القائمة، يجب إعادة توجيه هذه الرسالة delist@messaging.microsoft.com. لمزيد من المعلومات، انتقل إلى <https://go.microsoft.com/fwlink/?LinkId=526653>.

في البريد الإلكتروني لطلب الإزالة من هذه القائمة، زودك NDR التعليمات البرمجية الكاملة وعنوان IP. ستتصل بك Microsoft في غضون 48 ساعة باستخدام الخطوات التالية.

## <a name="more-information"></a>معلومات إضافية

نموذج الشطب ل **Outlook.com،** يمكن العثور على خدمة المستهلك [هنا](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). تأكد من قراءة الأسئلة [الشائعة](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) أولا _لاتجاه_ الإرسال.
