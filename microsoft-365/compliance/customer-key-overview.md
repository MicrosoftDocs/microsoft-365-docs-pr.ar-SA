---
title: تشفير الخدمة باستخدام مفتاح عميل Microsoft Purview
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: seo-marvel-apr2020
description: في هذه المقالة، ستتعرف على كيفية عمل تشفير الخدمة مع Microsoft Purview Customer Key.
ms.openlocfilehash: 98f298e88a53fee40e5f254e18695bca42aad52a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632454"
---
# <a name="service-encryption-with-microsoft-purview-customer-key"></a>تشفير الخدمة باستخدام مفتاح عميل Microsoft Purview

يوفر Microsoft 365 تشفيرا أساسيا على مستوى وحدة التخزين ممكنا من خلال BitLocker وSoursed Key Manager (DKM). يوفر Microsoft 365 طبقة إضافية من التشفير للمحتوى الخاص بك. يتضمن هذا المحتوى بيانات من Exchange Online Skype for Business وSharePoint Online OneDrive for Business وMicrosoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>كيفية عمل تشفير الخدمة وBitLocker ومفتاح العميل معا

يتم دائما تشفير بياناتك الثابتة في خدمة Microsoft 365 باستخدام BitLocker وDKM. لمزيد من المعلومات، راجع [كيفية تأمين Exchange Online أسرار البريد الإلكتروني](exchange-online-secures-email-secrets.md). يوفر Customer Key حماية إضافية ضد عرض البيانات من قبل أنظمة أو موظفين غير مصرح لهم، ويكمل تشفير قرص BitLocker في مراكز بيانات Microsoft. لا يقصد بتشفير الخدمة منع موظفي Microsoft من الوصول إلى بياناتك. بدلا من ذلك، يساعدك Customer Key على الوفاء بالالتزامات التنظيمية أو الامتثال للتحكم في مفاتيح الجذر. يمكنك تخويل خدمات Microsoft 365 صراحة لاستخدام مفاتيح التشفير الخاصة بك لتوفير خدمات سحابية ذات قيمة مضافة، مثل eDiscovery ومكافحة البرامج الضارة ومكافحة البريد العشوائي وفهرسة البحث وما إلى ذلك.

تم إنشاء مفتاح العميل على تشفير الخدمة ويسمح لك بتوفير مفاتيح التشفير والتحكم فيها. ثم يستخدم Microsoft 365 هذه المفاتيح لتشفير بياناتك الثابتة كما هو موضح في [شروط الخدمات عبر الإنترنت (OST).](https://www.microsoft.com/licensing/product-licensing/products.aspx) يساعدك Customer Key على الوفاء بالتزامات التوافق لأنك تتحكم في مفاتيح التشفير التي يستخدمها Microsoft 365 لتشفير البيانات وفك تشفيرها.
  
يعزز مفتاح العميل قدرة مؤسستك على تلبية متطلبات التوافق التي تحدد الترتيبات الرئيسية مع موفر خدمة السحابة. باستخدام Customer Key، يمكنك توفير مفاتيح التشفير الجذرية لبيانات Microsoft 365 الثابتة والتحكم فيها على مستوى التطبيق. ونتيجة لذلك، يمكنك ممارسة التحكم في مفاتيح مؤسستك.

## <a name="customer-key-with-hybrid-deployments"></a>مفتاح العميل مع عمليات النشر المختلطة

يقوم مفتاح العميل فقط بتشفير البيانات الثابتة في السحابة. لا يعمل مفتاح العميل على حماية علب البريد والملفات المحلية. يمكنك تشفير البيانات المحلية باستخدام أسلوب آخر، مثل BitLocker.

## <a name="about-data-encryption-policies"></a>حول نهج تشفير البيانات

يعرف نهج تشفير البيانات (DEP) التسلسل الهرمي للتشفير. تستخدم الخدمة هذا التسلسل الهرمي لتشفير البيانات باستخدام كل مفتاح من المفاتيح التي تديرها ومفتاح التوفر المحمي بواسطة Microsoft. يمكنك إنشاء DEPs باستخدام PowerShell cmdlets، ثم تعيين DEPs لتشفير بيانات التطبيق. هناك ثلاثة أنواع من DEPs المدعومة من قبل مفتاح العميل، يستخدم كل نوع نهج أوامر cmdlets مختلفة ويوفر تغطية لنوع مختلف من البيانات. تتضمن برامج DEPs التي يمكنك تعريفها ما يلي:

**DEP لأحمال عمل Microsoft 365 المتعددة** تقوم عمليات DEPs هذه بتشفير البيانات عبر أحمال عمل M365 متعددة لجميع المستخدمين داخل المستأجر. وتشمل أحمال العمل هذه ما يلي:

- رسائل دردشة Teams (دردشات 1:1 ودردشات جماعية ودردشات اجتماعات ومحادثات قناة)
- رسائل وسائط Teams (الصور، القصاصات البرمجية، رسائل الفيديو، الرسائل الصوتية، صور wiki)
- تسجيلات مكالمات Teams والاجتماعات المخزنة في تخزين Teams
- إعلامات دردشة Teams
- اقتراحات دردشة Teams من Cortana
- رسائل حالة Teams
- معلومات المستخدم والإشارة Exchange Online
- Exchange Online علب البريد غير المشفرة بالفعل بواسطة علب البريد DEPs
- حماية البيانات في Microsoft Purview:

  - بيانات مطابقة البيانات الدقيقة (EDM)، بما في ذلك مخططات ملفات البيانات وحزم القواعد والملوحة المستخدمة لتجزئة البيانات الحساسة. بالنسبة إلى EDM وMicrosoft Teams، يقوم DEP متعدد أحمال العمل بتشفير البيانات الجديدة من وقت تعيين DEP للمستأجر. بالنسبة Exchange Online، يقوم Customer Key بتشفير كافة البيانات الموجودة والجديدة.

  - تكوين التسمية لأوصاف الحساسية

لا تقوم برامج DEPs متعددة حمل العمل بتشفير الأنواع التالية من البيانات. بدلا من ذلك، يستخدم Microsoft 365 أنواعا أخرى من التشفير لحماية هذه البيانات.

- SharePoint وبيانات OneDrive for Business.
- يتم تشفير ملفات Microsoft Teams وبعض تسجيلات المكالمات والاجتماعات في Teams المحفوظة في OneDrive for Business وSharePoint Online باستخدام SHAREPoint Online DEP.
- أحمال عمل Microsoft 365 الأخرى مثل Yammer و Planner التي لا يدعمها مفتاح العميل حاليا.
- بيانات الحدث المباشر ل Teams.

يمكنك إنشاء العديد من DEPs لكل مستأجر ولكن تعيين DEP واحد فقط في كل مرة. عند تعيين DEP، يبدأ التشفير تلقائيا ولكن يستغرق بعض الوقت لإكماله اعتمادا على حجم المستأجر الخاص بك.

توفر **DEPs لعلب بريد Exchange Online** DEPs تحكما أكثر دقة في علب البريد الفردية داخل Exchange Online. استخدم DEPs علبة البريد لتشفير البيانات المخزنة في علب بريد EXO من أنواع مختلفة مثل UserMailbox وMailUser وGroup و PublicFolder وعلب البريد المشتركة. يمكن أن يكون لديك ما يصل إلى 50 موفري DEPs نشطين لكل مستأجر وتعيين عمليات DEPs هذه إلى علب بريد فردية. يمكنك تعيين DEP واحد إلى علب بريد متعددة.

بشكل افتراضي، يتم تشفير علب البريد باستخدام المفاتيح التي تديرها Microsoft. عند تعيين مفتاح العميل DEP إلى علبة بريد:

- إذا تم تشفير علبة البريد باستخدام DEP متعدد أحمال العمل، تعيد الخدمة تشغيل علبة البريد باستخدام DEP علبة البريد الجديدة طالما أن المستخدم أو عملية النظام تصل إلى بيانات علبة البريد.

- إذا كانت علبة البريد مشفرة بالفعل باستخدام المفاتيح التي تديرها Microsoft، فستعيد الخدمة تشغيل علبة البريد باستخدام DEP علبة البريد الجديدة طالما أن المستخدم أو عملية النظام تصل إلى بيانات علبة البريد.

- إذا لم يتم تشفير علبة البريد بعد باستخدام التشفير الافتراضي، فإن الخدمة تحدد علبة البريد للتنقل. يتم التشفير بمجرد اكتمال النقل. يتم التحكم في عمليات نقل علبة البريد استنادا إلى الأولويات المحددة لكل Microsoft 365. لمزيد من المعلومات، راجع [نقل الطلبات في خدمة Microsoft 365](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). إذا لم يتم تشفير علب البريد خلال الوقت المحدد، فاتصل ب Microsoft.

في وقت لاحق، يمكنك إما تحديث DEP أو تعيين DEP مختلف إلى علبة البريد كما هو موضح في ["إدارة مفتاح العميل" Office 365](customer-key-manage.md). يجب أن يكون لكل علبة بريد تراخيص مناسبة لتعيين DEP. لمزيد من المعلومات حول الترخيص، راجع [قبل إعداد مفتاح العميل](customer-key-set-up.md#before-you-set-up-customer-key).

يمكن تعيين DEPs إلى علبة بريد مشتركة وعلبة بريد مجلد عام وعلبة بريد مجموعة Microsoft 365 للمستأجرين الذين يستوفون متطلبات الترخيص لعلب بريد المستخدمين. لا تحتاج إلى تراخيص منفصلة لعلب البريد غير الخاصة بالمستخدم لتعيين Customer Key DEP.

بالنسبة لملفات DEPs لمفتاح العميل التي تقوم بتعيينها إلى علب بريد فردية، يمكنك طلب قيام Microsoft بإزالة DEPs معينة عند مغادرة الخدمة. للحصول على معلومات حول عملية إزالة البيانات وإبطال المفتاح، راجع [إبطال المفاتيح وبدء عملية مسار إزالة البيانات](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

عند إبطال الوصول إلى مفاتيحك كجزء من مغادرة الخدمة، يتم حذف مفتاح التوفر، ما يؤدي إلى حذف تشفير بياناتك. يقلل الحذف التشفيري من مخاطر إعادة تشغيل البيانات، وهو أمر مهم للوفاء بالتزامات الأمان والتوافق.

يستخدم **DEP ل SharePoint Online OneDrive for Business** يتم استخدام DEP هذا لتشفير المحتوى المخزن في SPO OneDrive for Business، بما في ذلك ملفات Microsoft Teams المخزنة في SPO. إذا كنت تستخدم الميزة متعددة المناطق الجغرافية، يمكنك إنشاء DEP واحد لكل جغرافيا لمؤسستك. إذا كنت لا تستخدم الميزة متعددة المناطق الجغرافية، يمكنك إنشاء DEP واحد فقط لكل مستأجر. راجع التفاصيل في [إعداد مفتاح العميل](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>شفرات التشفير المستخدمة من قبل مفتاح العميل

يستخدم "مفتاح العميل" العديد من رموز التشفير لتشفير المفاتيح كما هو موضح في الأرقام التالية.

يشبه التسلسل الهرمي الرئيسي المستخدم ل DEPs الذي يقوم بتشفير البيانات لأحمال عمل Microsoft 365 المتعددة التسلسل الهرمي المستخدم ل DEPs لعلب بريد Exchange Online الفردية. الفرق الوحيد هو استبدال مفتاح علبة البريد بمفتاح حمل عمل Microsoft 365 المطابق.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>تشفير الرموز المستخدمة لتشفير مفاتيح Exchange Online Skype for Business

![شفرات التشفير لمفتاح العميل Exchange Online.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>تشفير الرموز المستخدمة لتشفير المفاتيح لملفات SharePoint Online OneDrive for Business وTeams

![شفرات تشفير لمفتاح عميل SharePoint Online.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>المقالات ذات الصلة

- [إعداد مفتاح العميل](customer-key-set-up.md)

- [إدارة مفتاح العميل](customer-key-manage.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)

- [صندوق تأمين بيانات العملاء](customer-lockbox-requests.md)

- [تشفير الخدمة](office-365-service-encryption.md)
