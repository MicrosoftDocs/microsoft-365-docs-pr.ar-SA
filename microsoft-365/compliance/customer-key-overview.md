---
title: تشفير الخدمة باستخدام "مفتاح العميل"
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
description: في هذه المقالة، ستتعرف على كيفية عمل تشفير الخدمة مع "مفتاح العميل" في Microsoft 365.
ms.openlocfilehash: 14760bfcb26fa1bf45c54661cbb6fc189bad7d93
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/14/2022
ms.locfileid: "63566368"
---
# <a name="service-encryption-with-customer-key"></a>تشفير الخدمة باستخدام "مفتاح العميل"

يوفر Microsoft 365 تشفيرا أساسيا على مستوى الصوت تم تمكينه من خلال BitLocker ومدير المفاتيح الموزع (DKM). Microsoft 365 طبقة إضافية من التشفير لمحتواك. يتضمن هذا المحتوى بيانات من Exchange Online Skype for Business و SharePoint عبر الإنترنت OneDrive for Business و Microsoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>كيفية عمل تشفير الخدمة و BitLocker و Customer Key معا

يتم تشفير بياناتك دائما في خدمة Microsoft 365 باستخدام BitLocker و DKM. لمزيد من المعلومات، راجع [Exchange Online تأمين أسرار بريدك الإلكتروني](exchange-online-secures-email-secrets.md). يوفر "مفتاح العميل" حماية إضافية من عرض البيانات بواسطة أنظمة أو موظفين غير مصرح لهم، كما يكمل تشفير القرص BitLocker في مراكز بيانات Microsoft. لا يقصد بتشفير الخدمة منع موظفي Microsoft من الوصول إلى بياناتك. بدلا من ذلك، يساعدك "مفتاح العميل" على الوفاء بالالتزامات التنظيمية أو الالتزامات المتعلقة بالتوافق للتحكم بالمفاتيح الجذر. أنت ترخص صراحة Microsoft 365 استخدام مفاتيح التشفير لتوفير خدمات سحابة ذات قيمة مضافة، مثل eDiscovery و مكافحة البرامج الضارة و مكافحة البريد العشوائي و فهرسة البحث وما إلى ذلك.

تم إنشاء "مفتاح العميل" على تشفير الخدمة ويسمح لك بتوفير مفاتيح التشفير والتحكم بها. Microsoft 365 استخدام هذه المفاتيح لتشفير بياناتك بشكل مطمئن كما هو موضح في شروط الخدمات عبر [الإنترنت (OST).](https://www.microsoft.com/licensing/product-licensing/products.aspx) يساعدك "مفتاح العميل" على الوفاء بالالتزامات المتعلقة بالتوافق لأنك تتحكم في مفاتيح التشفير التي تستخدمها Microsoft 365 تشفير البيانات وفك تشفيرها.
  
يحسن "مفتاح العميل" قدرة مؤسستك على تلبية متطلبات التوافق التي تحدد الترتيبات الأساسية مع موفر خدمة السحابة. باستخدام "مفتاح العميل"، يمكنك توفير مفاتيح التشفير الجذر Microsoft 365 البيانات الموجودة على مستوى التطبيق والتحكم بها. ونتيجة لذلك، يمكنك التحكم في مفاتيح مؤسستك.

## <a name="customer-key-with-hybrid-deployments"></a>مفتاح العميل مع عمليات نشر مختلطة

يقوم "مفتاح العميل" بتشفير البيانات فقط في السحابة. لا يعمل "مفتاح العميل" على حماية علب البريد والملفات المحلية. يمكنك تشفير بياناتك في الموقع باستخدام طريقة أخرى، مثل BitLocker.

## <a name="about-data-encryption-policies"></a>حول سياسات تشفير البيانات

يعرف نهج تشفير البيانات (DEP) التسلسل الهيكلي للتشفير. تستخدم الخدمة هذا التسلسل الهيكلي لتشفير البيانات باستخدام كل مفتاح من المفاتيح التي تديرها ومفتاح التوفر المحمي بواسطة Microsoft. يمكنك إنشاء DEPs باستخدام PowerShell cmdlets، ثم تعيين هذه DEPs لتشفير بيانات التطبيق. هناك ثلاثة أنواع من أنواع DEPs Microsoft 365 Customer Key، يستخدم كل نوع نهج cmdlets مختلفة ويوفر تغطية لنوع مختلف من البيانات. تتضمن DEPs التي يمكنك تعريفها ما يلي:

**DEP لأحمال Microsoft 365 عمل** متعددة يقوم DEPs بتشفير البيانات عبر أحمال عمل M365 متعددة لجميع المستخدمين ضمن نطاق المستأجر. تتضمن أحمال العمل هذه:

- Teams رسائل الدردشة (الدردشات 1:1، الدردشات الجماعية، دردشات الاجتماعات ومحادثات القناة)
- Teams الوسائط (الصور، قصاصات التعليمات البرمجية، رسائل الفيديو، الرسائل الصوتية، صور wiki)
- Teams تسجيلات الاجتماعات والمكاتب المخزنة في Teams التخزين
- Teams إعلامات الدردشة
- Teams اقتراحات الدردشة حسب Cortana
- Teams رسائل الحالة
- معلومات المستخدم والإشارة Exchange Online
- Exchange Online علب البريد التي لم يتم تشفيرها مسبقا بواسطة مكتبات DEPs لعلب البريد
- حماية البيانات في Microsoft:

  - تتطابق البيانات بدقة (EDM)، بما في ذلك مخططات ملفات البيانات وحزم القواعد والأملاح المستخدمة لتحسيم البيانات الحساسة. بالنسبة إلى EDM Microsoft Teams، يقوم DEP متعدد حمل العمل بتشفير البيانات الجديدة من وقت تعيين DEP للمستأجر. بالنسبة Exchange Online، يقوم "مفتاح العميل" بتشفير كل البيانات الموجودة أو الجديدة.

  - تكوين التسميات لتسميات الحساسية

لا يقوم برنامج DEPs متعدد حمل العمل بتشفير أنواع البيانات التالية. بدلا من Microsoft 365 يستخدم المستخدمون أنواعا أخرى من التشفير لحماية هذه البيانات.

- SharePoint البيانات OneDrive for Business البيانات.
- Microsoft Teams الملفات وبعض Teams المكالمات وتسجيلات الاجتماعات المحفوظة في OneDrive for Business و SharePoint Online باستخدام SharePoint Online DEP.
- أحمال Microsoft 365 أخرى مثل Yammer و Planner غير المعتمدة حاليا بواسطة "مفتاح العميل".
- Teams بيانات الحدث المباشر.

يمكنك إنشاء العديد من DEPs لكل مستأجر ولكن تعيين DEP واحد فقط في كل مرة. عند تعيين DEP، يبدأ التشفير تلقائيا ولكنه يستغرق بعض الوقت لإكماله استنادا إلى حجم المستأجر.

**توفر DEPs لعلب Exchange Online** علب البريد DEPs تحكما أكثر دقة لعلب البريد الفردية ضمن Exchange Online. استخدم DEPs لعلب البريد لتشفير البيانات المخزنة في علب بريد EXO من أنواع مختلفة مثل UserMailbox وMailUser و Group و PublicFolder و علب البريد المشتركة. يمكن أن يكون لديك ما يصل إلى 50 DEPs نشطا لكل مستأجر وتعيين هذه DEPs لعلب بريد فردية. يمكنك تعيين DEP واحد إلى علب بريد متعددة.

بشكل افتراضي، يتم تشفير علب البريد باستخدام المفاتيح المدارة من Microsoft. عند تعيين DEP لمفتاح العميل إلى علبة بريد:

- إذا كانت علبة البريد مشفرة باستخدام DEP متعدد حمل العمل، فإن الخدمة تعيد استخدام علبة البريد باستخدام DEP لعلبة البريد الجديدة طالما أن المستخدم أو عملية النظام يمكن الوصول إلى بيانات علبة البريد.

- إذا كانت علبة البريد مشفرة بالفعل باستخدام مفاتيح مدارة من Microsoft، فإن الخدمة تعيد الكتابة إلى علبة البريد باستخدام DEP لعلبة البريد الجديدة طالما أن المستخدم أو عملية النظام قد تمكنت من الوصول إلى بيانات علبة البريد.

- إذا لم تكن علبة البريد مشفرة بعد باستخدام التشفير الافتراضي، فستعمل الخدمة على وضع علامة على علبة البريد لنقلها. يتم التشفير بمجرد اكتمال عملية الانتقال. يتم التحكم في نقل علب البريد استنادا إلى الأولويات التي تم تعيينها لجميع Microsoft 365. لمزيد من المعلومات، راجع نقل [الطلبات في Microsoft 365 الخدمة](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). إذا لم يتم تشفير علب البريد خلال الوقت المحدد، فاتصل ب Microsoft.

في وقت لاحق، يمكنك تحديث DEP أو تعيين DEP مختلف إلى علبة البريد كما هو موضح في إدارة مفتاح العميل [Office 365](customer-key-manage.md). يجب أن يكون لكل علبة بريد التراخيص المناسبة لتعيين DEP. لمزيد من المعلومات حول الترخيص، راجع [قبل إعداد مفتاح العميل](customer-key-set-up.md#before-you-set-up-customer-key).

يمكن تعيين DEPs لعلبة بريد مشتركة، علبة بريد مجلد عمومي، Microsoft 365 بريد المجموعة للمستأجرين الذين يلبيون متطلبات الترخيص لعلب بريد المستخدمين. لست بحاجة إلى تراخيص منفصلة لعلب البريد غير الخاصة بالمستخدم لتعيين DEP لمفتاح العميل.

بالنسبة إلى برامج DEPS لمفتاح العميل التي تقوم بتعيينها إلى علب بريد فردية، يمكنك أن تطلب من Microsoft إزالة برامج DEPs معينة عند مغادرة الخدمة. للحصول على معلومات حول عملية إزالة البيانات وإبطال المفتاح، راجع إبطال المفاتيح وبدء عملية مسار [إزالة البيانات](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

عند إبطال الوصول إلى المفاتيح كجزء من مغادرة الخدمة، يتم حذف مفتاح التوفر، مما يؤدي إلى حذف التشفير لبياناتك. يعمل حذف التشفير على تقليل مخاطر إعادة استخدام البيانات، وهو أمر مهم للوفاء بكل من التزامات الأمان والتوافق.

**DEP SharePoint عبر الإنترنت OneDrive for Business** يتم استخدام DEP لتشفير المحتوى المخزن في SPO OneDrive for Business، بما في ذلك Microsoft Teams المخزنة في SPO. إذا كنت تستخدم ميزة تعدد الجغرافيا، يمكنك إنشاء DEP واحد لكل جغرافي لمنظمتك. إذا كنت لا تستخدم ميزة متعددة الجغرافيا، يمكنك إنشاء DEP واحد فقط لكل مستأجر. راجع التفاصيل في [إعداد مفتاح العميل](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>تشفير ciphers المستخدم بواسطة "مفتاح العميل"

يستخدم "مفتاح العميل" أشكال تشفير متنوعة لتشفير المفاتيح كما هو موضح في الأرقام التالية.

التسلسل الهيكلي الرئيسي المستخدم ل DEPs الذي يقوم بتشفير البيانات لأحمال عمل Microsoft 365 متعددة مماثل للتسلسل الهيكلي المستخدم ل DEPs لعلب بريد Exchange Online الفردية. والفرق الوحيد هو استبدال مفتاح علبة البريد بالمفتاح المطابق Microsoft 365 العمل.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>تشفير ciphers المستخدمة لتشفير المفاتيح Exchange Online Skype for Business

![تشفير ciphers Exchange Online Customer Key.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>تشفير ciphers المستخدمة لتشفير المفاتيح SharePoint على OneDrive for Business والملفات Teams الإنترنت

![تشفير ciphers SharePoint Online Customer Key.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>المقالات ذات الصلة

- [إعداد مفتاح العميل](customer-key-set-up.md)

- [إدارة مفتاح العميل](customer-key-manage.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)

- [Customer Lockbox](customer-lockbox-requests.md)

- [تشفير الخدمة](office-365-service-encryption.md)
