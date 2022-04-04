---
title: خدمات لغير العملاء الذين يرسلون البريد إلى Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 19fd3e0f-8dbf-4049-a810-2c8ee6cefd48
ms.collection:
- M365-security-compliance
description: للمساعدة في الحفاظ على ثقة المستخدم في استخدام البريد الإلكتروني، وضعت Microsoft سياسات وتقنيات متنوعة للمساعدة في حماية المستخدمين.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7af1a901bf9b3b27f08a7a3d36de69d49c2c85e9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679555"
---
# <a name="services-for-non-customers-sending-mail-to-microsoft-365"></a>خدمات لغير العملاء الذين يرسلون البريد إلى Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


تستمر إساءة استخدام البريد الإلكتروني والبريد الإلكتروني غير الهام ورسائل البريد الإلكتروني الاحتيالية (التصيد الاحتيالي) في تحميل النظام البيئي للبريد الإلكتروني بأكمله العبئ. للمساعدة في الحفاظ على ثقة المستخدم في استخدام البريد الإلكتروني، وضعت Microsoft العديد من السياسات والتقنيات في مكانها للمساعدة في حماية المستخدمين. ومع ذلك، تدرك Microsoft أنه لا يجب أن يتأثر البريد الإلكتروني المشروع سلبا. لذلك، قمنا بإنشاء مجموعة من الخدمات لمساعدة المرسلين على تحسين قدرتهم على تسليم البريد الإلكتروني Microsoft 365 المستخدمين من خلال إدارة سمعتهم المرسلة بشكل استباقي.

توفر هذه النظرة العامة معلومات حول المزايا التي نوفرها لمنظمتك حتى لو لم تكن عميلا.

## <a name="sender-solutions"></a>حلول المرسلين

|الخدمة|المزايا|
|---|---|
|محتوى المساعدة هذا عبر الإنترنت|يوفر: <ul><li>نقطة بداية لأي أسئلة متعلقة بتسليم الاتصالات لمستخدمي EOP.</li><li>يتضمن دليل بسيط عبر الإنترنت مع سياساتنا ومتطلباتنا.</li><li>نظرة عامة حول عوامل تصفية البريد الإلكتروني غير الهام وتقنيات المصادقة المستخدمة بواسطة Microsoft.</li><ul>|
|[دعم Microsoft](#microsoft-support)|يوفر الدعم الذاتي للمساعدة والتصعيد لقضايا التسليم.|
|[مدخل Delist IP لمكافحة البريد العشوائي](#anti-spam-ip-delist-portal)|أداة لإرسال طلب شطب عناوين IP. قبل إرسال هذا الطلب، تقع على عاتق المرسل مسؤولية التأكد من أن أي بريد آخر مصدره عنوان IP المعني ليس مسيئا أو ضارا.|
|[الإبلاغ عن إساءة الاستخدام والبريد العشوائي للبريد الإلكتروني غير الهام الذي ينشأ من Exchange Online](#abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online)|تمنع إرسال البريد العشوائي والبريد غير المرغوب فيه من Exchange Online البريد الإلكتروني والتكدوج عبر الإنترنت ونظام البريد.|

## <a name="microsoft-support"></a>دعم Microsoft

توفر Microsoft العديد من خيارات الدعم للأشخاص الذين تواجههم مشكلة في إرسال البريد Microsoft 365 المستلمين. نوصي ب:

- اتبع الإرشادات الواردة في أي تقرير بعدم التسليم تتلقاه.

- اطلع على المشاكل الأكثر شيوعا التي يواجهها غير العملاء في استكشاف الأخطاء [وإصلاحها](troubleshooting-mail-sent-to-office-365.md) في البريد المرسل إلى Office 365.

- استخدم مدخل [Microsoft 365](https://sender.office.com) لإرسال طلب لإزالة IP الخاص بك من قائمة المرسلين المحظورين.

- اقرأ [منتديات مجتمع Microsoft](https://community.office365.com/f/).

- اتصل للعميل الذي تحاول إرسال بريد إلكتروني باستخدام طريقة أخرى واطلب منه الاتصال بدعم Microsoft وفتح تذكرة دعم بالنيابة عنك. في بعض الحالات، لأسباب قانونية، يجب على دعم Microsoft التواصل مباشرة مع المرسل الذي يملك مساحة IP التي يتم حظرها. ومع ذلك، لا يمكن لغير العملاء عادة فتح تذاكر الدعم.

  لمزيد من المعلومات حول دعم Microsoft التقني Office 365، راجع [الدعم](/office365/servicedescriptions/office-365-platform-service-description/support).

## <a name="anti-spam-ip-delist-portal"></a>مدخل Delist IP لمكافحة البريد العشوائي

هذا مدخل الخدمة الذاتية يمكنك استخدامه لإزالة نفسك من قائمة المرسلين المحظورين Microsoft 365 المحظورين. استخدم هذا المدخل إذا كنت تستلم رسالة خطأ عند محاولة إرسال رسالة بريد إلكتروني إلى مستلم يكون عنوان بريده الإلكتروني Microsoft 365 ولا تعتقد أنه يجب أن تكون كذلك. لمزيد من المعلومات، راجع [استخدام مدخل الحذف لإزالة نفسك من](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md) قائمة المرسلين المحظورين.

## <a name="abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online"></a>الإبلاغ عن إساءة الاستخدام والبريد العشوائي للبريد الإلكتروني غير الهام الذي ينشأ من Exchange Online

في بعض Microsoft 365 يتم استخدام البريد الإلكتروني من قبل جهات خارجية لإرسال بريد إلكتروني غير هام، في انتهاك لشروط الاستخدام والسياسات. إذا تلقيت أي بريد إلكتروني غير هام من Office 365، يمكنك الإبلاغ عن هذه الرسائل إلى Microsoft. للحصول على الإرشادات، راجع [الإبلاغ عن الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md).
