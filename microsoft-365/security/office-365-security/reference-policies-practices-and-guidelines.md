---
title: المراجع والسياسات والممارسات والمبادئ التوجيهية
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
description: قامت Microsoft بتطوير سياسات وإجراءات متنوعة، كما تعتمد العديد من أفضل الممارسات الصناعية للمساعدة في حماية المستخدمين من البريد الإلكتروني المسيئ أو غير المرغوب فيه أو الضار.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 21b1918155755d7786f7b797ae7c705ca8c0ec39
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566505"
---
# <a name="reference-policies-practices-and-guidelines"></a>المرجع: السياسات، الممارسات، الإرشادات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تلتزم Microsoft بالمساعدة في توفير تجربة المستخدم الأكثر ثقة على الويب. لذلك، قامت Microsoft بتطوير سياسات وإجراءات متنوعة، كما تعتمد العديد من أفضل الممارسات الصناعية للمساعدة في حماية المستخدمين من البريد الإلكتروني المسيئ أو غير المرغوب فيه أو الضار. يجب أن يضمن المرسلون الذين يحاولون إرسال بريد إلكتروني إلى المستخدمين فهمهم الكامل ويتبعون الإرشادات الواردة في هذه المقالة للمساعدة في هذا الجهد وللمساعدة في تجنب مشاكل التسليم المحتملة.

إذا لم تكن ممتثلا لهذه السياسات والمبادئ التوجيهية، فقد لا يكون من الممكن لفريق الدعم لدينا مساعدتك. إذا كنت تلتزم بالمبادئ التوجيهية والممارسات والسياسات المقدمة في هذه المقالة ولا تزال تواجه مشاكل تتعلق بالتسليم استنادا إلى عنوان IP المرسل، فالرجاء اتباع الخطوات لإرسال طلب شطب. للحصول على الإرشادات، راجع [استخدام مدخل الحذف لإزالة نفسك من](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md) قائمة المرسلين المحظورين.

## <a name="general-microsoft-policies"></a>سياسات Microsoft العامة

يجب أن يمتثل Microsoft 365 الإلكتروني المرسل إلى المستخدمين لجميع سياسات Microsoft التي تحكم إرسال البريد الإلكتروني واستخدامه Microsoft 365.

- شروط الخدمات المطبقة على Microsoft 365، وعلى وجه الخصوص، حظر استخدام الخدمة للبريد العشوائي أو توزيع البرامج الضارة.

- [اتفاقية خدمات Microsoft](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>اللوائح الحكومية

يجب على Microsoft 365 الإلكتروني المرسل إلى المستخدمين الالتزام بجميع القوانين واللوائح المعمول بها التي تحكم اتصالات البريد الإلكتروني في الاختصاص القضائي المعمول به.

- [قانون CAN-SPAM: دليل توافق للأعمال](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- [الاستجابات والمسؤوليات "أزلني": يتعين على مسوقي البريد الإلكتروني احترام مطالبات "إلغاء الاشتراك"](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>الإرشادات التقنية

يجب أن Microsoft 365 البريد الإلكتروني المرسل إلى Microsoft 365 بالتوصيات السارية المدرجة في المستندات أدناه (تتوفر بعض الارتباطات باللغة الإنجليزية فقط).

- [RFC 2505: مكافحة البريد العشوائي التوصيات SMTP MTAs](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: ملحق خدمة SMTP لتنزيل الأوامر](https://www.ietf.org/rfc/rfc2920.txt)

بالإضافة إلى ذلك، يجب أن تلتزم خوادم البريد الإلكتروني التي تتصل Microsoft 365 بالمتطلبات التالية:

- من المتوقع أن يمتثل المرسل لجميع المعايير التقنية الخاصة بإرسال البريد الإلكتروني عبر الإنترنت، كما هو منشور بواسطة فريق المهام الهندسية عبر الإنترنت (IETF)، بما في ذلك RFC 5321 وRFC 5322 وغيرها.

- بعد إعطاء رمز استجابة لخطأ SMTP رقمي بين 500 و599 (يعرف أيضا بالاستجابة الدائمة لعدم التسليم أو التقرير بعدم التسليم)، يجب ألا يحاول المرسل إعادة إرسال هذه الرسالة إلى هذا المستلم.

- بعد عدة ردود بعدم التسليم، يجب على المرسل التوقف عن محاولات إرسال البريد الإلكتروني إلى هذا المستلم.

- يجب ألا يتم إرسال الرسائل عبر خوادم الوكيل أو ترحيل البريد الإلكتروني غير الآمن.

- يجب توثيق آلية إلغاء الاشتراك، إما من القوائم الفردية أو كل القوائم التي يستضيفها المرسل، توثيقا واضحا وسهلا على المستلمين العثور عليها واستخدامها.

- قد لا يتم قبول الاتصالات من مساحة IP ديناميكية.

- يجب أن يكون لدى خوادم البريد الإلكتروني سجلات DNS عكسية صالحة.

## <a name="reputation-management"></a>إدارة السمعة

يجب على المرسلين وموفري خدمات الإنترنت وموفري الخدمات الآخرين إدارة سمعة عناوين IP الصادرة الخاصة بك بشكل نشط.

## <a name="microsoft-365-limits"></a>Microsoft 365 الحدود

يجب أن يلتزم المرسلون Microsoft 365 الواردة في Exchange Online Protection [الحدود](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits).

## <a name="email-delivery-resources-and-organizations"></a>موارد تسليم البريد الإلكتروني وتنظيماته

تعمل Microsoft بنشاط مع الجهات الصناعية وموفري الخدمات لتحسين نظام الإنترنت والبريد الإلكتروني. نشرت هذه المؤسسات مستندات أفضل الممارسات التي ندعمها ونوصي المرسلين بالالتزام بها. يحسن ذلك من قدرتك على تسليم البريد الإلكتروني بين العديد من موفري خدمات البريد الإلكتروني حول العالم.

- [مجموعة عمل مكافحة إساءة استخدام البرامج الضارة على الأجهزة المحمولة للمراسلة](https://www.m3aawg.org/)

- [Online Trust Alliance](https://www.internetsociety.org/ota/)

- [مرسل البريد الإلكتروني & موفر الخدمة](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>الإبلاغ عن إساءة الاستخدام والبريد العشوائي

الإبلاغ عن بريد إلكتروني غير قانوني أو مسيئ أو غير مرغوب فيه أو ضار، راجع الإبلاغ عن [الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md). يشكل إرسال هذه الأنواع من الاتصالات مخالفة لنهية Microsoft، وستتخذ الإجراءات المناسبة في التقارير التي تم تأكيدها.

## <a name="law-enforcement"></a>تطبيق القانون

إذا كنت عضوا في تطبيق القانون وترغب في خدمة Microsoft Corporation بوثائق قانونية تتعلق ب Office 365، أو إذا كانت لديك أسئلة تتعلق بالوثائق القانونية التي قمت بتقديمها إلى Microsoft، فيرجى الاتصال (1) (425) 722-1299.