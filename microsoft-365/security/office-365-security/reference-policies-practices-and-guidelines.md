---
title: النهج المرجعية والممارسات والإرشادات
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ff3f140b-b005-445f-bfe0-7bc3f328aaf0
ms.collection:
- M365-security-compliance
description: طورت Microsoft سياسات وإجراءات مختلفة، كما اعتمدت العديد من أفضل الممارسات الصناعية للمساعدة في حماية مستخدمينا من البريد الإلكتروني المسيء أو غير المرغوب فيه أو الضار.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 815fea8981fdab8825a109dae69abaf8232997f9
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130352"
---
# <a name="reference-policies-practices-and-guidelines"></a>المرجع: النهج والممارسات والإرشادات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

إن Microsoft مخصصة للمساعدة في توفير تجربة المستخدم الأكثر موثوقية على الويب. لذلك، طورت Microsoft سياسات وإجراءات مختلفة، وتبنت العديد من أفضل الممارسات الصناعية للمساعدة في حماية مستخدمينا من البريد الإلكتروني المسيء أو غير المرغوب فيه أو الضار. يجب على المرسلين الذين يحاولون إرسال بريد إلكتروني إلى المستخدمين التأكد من فهمهم الكامل للإرشادات الواردة في هذه المقالة واتباعها للمساعدة في هذا الجهد وللمساعدة على تجنب مشاكل التسليم المحتملة.

إذا لم تكن متوافقا مع هذه النهج والإرشادات، فقد لا يكون من الممكن لفريق الدعم مساعدتك. إذا كنت تلتزم بالإرشادات والممارسات والنهج الواردة في هذه المقالة ولا تزال تواجه مشاكل في التسليم استنادا إلى عنوان IP المرسل، فالرجاء اتباع الخطوات لإرسال طلب إزالة القوائم. للحصول على الإرشادات، راجع [استخدام مدخل إلغاء القائمة لإزالة نفسك من قائمة المرسلين المحظورين](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="general-microsoft-policies"></a>نهج Microsoft العامة

يجب أن يتوافق البريد الإلكتروني المرسل إلى Microsoft 365 المستخدمين مع جميع نهج Microsoft التي تحكم إرسال البريد الإلكتروني واستخدام Microsoft 365.

- شروط الخدمات المطبقة على Microsoft 365؛ على وجه الخصوص، منع استخدام الخدمة للبريد العشوائي أو توزيع البرامج الضارة.

- [اتفاقية خدمات Microsoft](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>اللوائح الحكومية

يجب أن يلتزم البريد الإلكتروني المرسل إلى المستخدمين Microsoft 365 بجميع القوانين واللوائح المعمول بها التي تحكم اتصالات البريد الإلكتروني في الولاية القضائية المعمول بها.

- [قانون CAN-SPAM: دليل توافق للأعمال](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- [الاستجابات والمسؤوليات "إزالة لي": يجب على مسوقي البريد الإلكتروني احترام مطالبات "إلغاء الاشتراك"](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>الإرشادات التقنية

يجب أن يتوافق البريد الإلكتروني المرسل إلى Microsoft 365 مع التوصيات المعمول بها المدرجة في المستندات أدناه (تتوفر بعض الارتباطات باللغة الإنجليزية فقط).

- [RFC 2505: التوصيات مكافحة البريد العشوائي ل SMTP MTAs](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: ملحق خدمة SMTP ل Pipelining للأوامر](https://www.ietf.org/rfc/rfc2920.txt)

بالإضافة إلى ذلك، يجب أن تلتزم خوادم البريد الإلكتروني المتصلة Microsoft 365 بالمتطلبات التالية:

- من المتوقع أن يمتثل المرسل لجميع المعايير التقنية لإرسال البريد الإلكتروني عبر الإنترنت، كما تم نشره من قبل فريق مهام هندسة الإنترنت في مجتمع الإنترنت (IETF)، بما في ذلك RFC 5321 وRFC 5322 وغيرها.

- بعد إعطاء رمز استجابة خطأ SMTP رقمي بين 500 و599 (يعرف أيضا باستجابة دائمة بعدم التسليم أو NDR)، يجب ألا يحاول المرسل إعادة إرسال هذه الرسالة إلى هذا المستلم.

- بعد عدة استجابات بعدم التسليم، يجب على المرسل التوقف عن محاولات إرسال البريد الإلكتروني إلى هذا المستلم.

- يجب عدم إرسال الرسائل من خلال ترحيل البريد الإلكتروني غير الآمن أو الخوادم الوكيلة.

- يجب أن تكون آلية إلغاء الاشتراك، إما من القوائم الفردية أو جميع القوائم التي يستضيفها المرسل، موثقة بوضوح وسهلة للمستلمين للعثور عليها واستخدامها.

- قد لا يتم قبول الاتصالات من مساحة IP الديناميكية.

- يجب أن تحتوي خوادم البريد الإلكتروني على سجلات DNS عكسية صالحة.

## <a name="reputation-management"></a>إدارة السمعة

يجب على المرسلين وموفري خدمة الإنترنت وموفري الخدمات الآخرين إدارة سمعة عناوين IP الصادرة بشكل نشط.

## <a name="microsoft-365-limits"></a>حدود Microsoft 365

يجب على المرسلين الالتزام بحدود Microsoft 365 المدرجة في [حدود Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits).

## <a name="email-delivery-resources-and-organizations"></a>موارد تسليم البريد الإلكتروني والمؤسسات

تعمل Microsoft بنشاط مع الهيئات الصناعية وموفري الخدمات من أجل تحسين النظام البنائي للإنترنت والبريد الإلكتروني. نشرت هذه المؤسسات مستندات أفضل الممارسات التي ندعمها ونوصي بأن يلتزم بها المرسلون. يؤدي ذلك إلى تحسين قدرتك على تسليم البريد الإلكتروني بين العديد من موفري خدمة البريد الإلكتروني في جميع أنحاء العالم.

- [مجموعة عمل مكافحة إساءة استخدام البرامج الضارة للمراسلة على الأجهزة المحمولة](https://www.m3aawg.org/)

- [تحالف الثقة عبر الإنترنت](https://www.internetsociety.org/ota/)

- [تحالف موفر & مرسل البريد الإلكتروني](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>الإبلاغ عن إساءة الاستخدام والبريد العشوائي

للإبلاغ عن رسائل البريد الإلكتروني غير القانونية أو المسيئة أو غير المرغوب فيها أو الضارة، راجع [إرسال تقارير بالرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md). يعد إرسال هذه الأنواع من الاتصالات خرقا لنهج Microsoft، وسيتم اتخاذ الإجراء المناسب بشأن التقارير المؤكدة.

## <a name="law-enforcement"></a>انفاذ

إذا كنت عضوا في إنفاذ القانون وترغب في خدمة Microsoft Corporation مع وثائق قانونية تتعلق Office 365، أو إذا كانت لديك أسئلة تتعلق بالوثائق القانونية التي أرسلتها إلى Microsoft، فالرجاء الاتصال ب (1) (425) 722-1299.
