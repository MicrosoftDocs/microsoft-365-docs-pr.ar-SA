---
title: ميزات التشفير التي يديرها العميل
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
ms.custom:
- seo-marvel-mar2020
description: في هذه المقالة، ستتعرف على تقنيات التشفير التي يمكنك إدارتها وتكوينها في Microsoft 365.
ms.openlocfilehash: 55bc743f83b79ac83c764af24ef4100e5f72369d
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622537"
---
# <a name="customer-managed-encryption-features"></a>ميزات التشفير التي يديرها العميل

- [Azure Rights Management](/azure/information-protection/what-is-azure-rms)

- [تشفير الرسائل في Microsoft Purview](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [تأمين تدفق البريد مع مؤسسة شريكة](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

لمزيد من المعلومات حول هذه التقنيات، راجع [أوصاف خدمة Microsoft 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## <a name="azure-rights-management"></a>Azure Rights Management

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS) هي تقنية الحماية المستخدمة من قبل [Azure حماية البيانات](/information-protection/understand-explore/what-is-information-protection). ويستخدم سياسات التشفير والهوية والتخويل للمساعدة في تأمين الملفات والبريد الإلكتروني عبر أنظمة أساسية وأجهزة متعددة — الهواتف وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر الشخصية. يمكن حماية المعلومات داخل مؤسستك وخارجها لأن الحماية تبقى مع البيانات. يوفر Azure RMS حماية مستمرة لجميع أنواع الملفات، ويحمي الملفات في أي مكان، ويدعم التعاون بين الشركات، ومجموعة واسعة من الأجهزة Windows وغير Windows. يمكن لحماية Azure RMS أيضا زيادة [نهج منع فقدان البيانات (DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)). لمزيد من المعلومات حول التطبيقات والخدمات التي يمكنها استخدام خدمة Azure Rights Management من Azure حماية البيانات، راجع [كيفية دعم التطبيقات لخدمة azure Rights Management](/information-protection/understand-explore/applications-support).

تتكامل Azure RMS مع Microsoft 365 ومتاحة لجميع العملاء. لتكوين Microsoft 365 لاستخدام Azure RMS، راجع [تكوين IRM لاستخدام Rights Management Azure وإعداد Rights Management المعلومات (IRM) في مركز إدارة SharePoint](../enterprise/activate-rms-in-microsoft-365.md). إذا كنت تقوم بتشغيل خادم RMS Active Directory محلي (AD)، يمكنك أيضا [تكوين IRM لاستخدام خادم AD RMS محلي](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server)، ولكننا نوصي بشدة [بالرحل إلى Azure RMS](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) لاستخدام ميزات جديدة مثل التعاون الآمن مع المؤسسات الأخرى.

عند حماية بيانات العميل باستخدام Azure RMS، يستخدم Azure RMS مفتاح RSA 2048 بت غير متماثل مع خوارزمية تجزئة SHA-256 للتكامل لتشفير البيانات. المفتاح المتماثل Office المستندات والبريد الإلكتروني هو AES 128 بت. لكل مستند أو بريد إلكتروني محمي بواسطة Azure RMS، ينشئ Azure RMS مفتاح AES واحدا ("مفتاح المحتوى")، ويتم تضمين هذا المفتاح في المستند، ويستمر من خلال إصدارات المستند. يكون مفتاح المحتوى محميا بمفتاح RSA الخاص بالمؤسسة ("مفتاح المستأجر حماية البيانات Azure") كجزء من النهج في المستند، ويتم أيضا توقيع النهج من قبل كاتب المستند. يعد مفتاح المستأجر هذا شائعا لجميع المستندات ورسائل البريد الإلكتروني المحمية بواسطة Azure RMS للمؤسسة ولا يمكن تغيير هذا المفتاح إلا من قبل مسؤول حماية البيانات Azure إذا كانت المؤسسة تستخدم مفتاح مستأجر يديره العميل. لمزيد من المعلومات حول عناصر تحكم التشفير المستخدمة من قبل Azure RMS، راجع [كيف يعمل Azure RMS؟ تحت الغطاء](/information-protection/understand-explore/how-does-it-work).

في تطبيق Azure RMS الافتراضي، تنشئ Microsoft المفتاح الجذر الفريد لكل مستأجر وتديره. يمكن للعملاء إدارة دورة حياة مفتاح الجذر الخاص بهم في Azure RMS باستخدام Azure Key Vault Services باستخدام أسلوب إدارة مفتاح يسمى [Bring Your Own Key (BYOK)](/azure/information-protection/plan-implement-tenant-key) الذي يسمح لك بإنشاء مفتاحك في وحدات HSMs المحلية (وحدات أمان الأجهزة)، والبقاء في التحكم في هذا المفتاح بعد النقل إلى وحدات HSM المعتمدة من Microsoft من المستوى 140-2. لا يتم منح الوصول إلى المفتاح الجذر لأي موظفين حيث لا يمكن تصدير المفاتيح أو استخراجها من HSMs التي تحميهم. بالإضافة إلى ذلك، يمكنك الوصول إلى سجل قريب من الوقت الحقيقي يعرض جميع الوصول إلى المفتاح الجذر في أي وقت. لمزيد من المعلومات، راجع [التسجيل وتحليل استخدام Azure Rights Management](/azure/information-protection/log-analyze-usage).

يساعد Azure Rights Management على التخفيف من التهديدات مثل الاتصال بالأسلاك، والهجمات بين الشبكات، وسرقة البيانات، والانتهاكات غير المقصودة لنهج المشاركة المؤسسية. وفي الوقت نفسه، يتم منع أي وصول غير مبرر لبيانات العميل أثناء النقل أو الثابتة من قبل مستخدم غير مصرح له ليس لديه الأذونات المناسبة عبر النهج التي تتبع تلك البيانات، مما يقلل من خطر وقوع تلك البيانات في أيد غير صحيحة إما عن علم أو دون معرفة وتوفير وظائف منع فقدان البيانات. إذا تم استخدامها كجزء من Azure حماية البيانات، يوفر Azure RMS أيضا قدرات تصنيف البيانات والتسمية ووضع علامات على المحتوى وتعقب الوصول إلى المستندات وقدرات إبطال الوصول. لمعرفة المزيد حول هذه القدرات، راجع [ما هو azure حماية البيانات](/information-protection/understand-explore/what-is-information-protection)، [وخريطة طريق نشر Azure حماية البيانات](/information-protection/plan-design/deployment-roadmap)، [والبرنامج التعليمي للبدء السريع ل Azure حماية البيانات](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>تأمين ملحق بريد إنترنت متعدد الأغراض

تعد ملحقات بريد الإنترنت الآمنة/متعددة الأغراض (S/MIME) معيارا لتشفير المفتاح العام والتوقيع الرقمي لبيانات MIME. يتم تعريف S/MIME في RFCs 3369 و3370 و3850 و3851 وغيرها. يسمح للمستخدم بتشفير بريد إلكتروني وتوقيع بريد إلكتروني رقميا. لا يمكن فك تشفير البريد الإلكتروني المشفر باستخدام S/MIME إلا بواسطة مستلم البريد الإلكتروني باستخدام مفتاحه الخاص، والذي يتوفر فقط لهذا المستلم. على هذا النحو، لا يمكن فك تشفير رسائل البريد الإلكتروني بواسطة أي شخص آخر غير مستلم البريد الإلكتروني.

[تدعم Microsoft S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). يتم توزيع الشهادات العامة على Active Directory محلي العميل وتخزينها في سمات يمكن نسخها نسخا متماثلا إلى مستأجر Microsoft 365. تبقى المفاتيح الخاصة التي تتوافق مع المفاتيح العامة في أماكن العمل ولا يتم إرسالها أبدا إلى Office 365. يمكن للمستخدمين إنشاء رسائل البريد الإلكتروني وتشفيرها وفك تشفيرها وقراءتها وتوقيعها رقميا بين مستخدمين اثنين في مؤسسة باستخدام عملاء Outlook Outlook على ويب Exchange ActiveSync. لمزيد من المعلومات، راجع [تشفير S/MIME الآن في Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>تشفير الرسائل Office 365

[يمكنك Office 365 تشفير الرسائل](https://products.office.com/exchange/office-365-message-encryption) (OME) المضمنة أعلى [Azure حماية البيانات](/information-protection/understand-explore/what-is-information-protection) (AIP) من إرسال بريد مشفر ومحمي بحقوق إلى أي شخص. تخفف OME من التهديدات مثل الضغط على الأسلاك والهجمات التي تتم في الوسط، والتهديدات الأخرى، مثل الوصول غير المدعوم للبيانات من قبل مستخدم غير مصرح له ليس لديه الأذونات المناسبة. لقد قمنا بإجراء استثمارات توفر لك تجربة بريد إلكتروني أبسط وأكثر سهولة وأمانا مبنية على Azure حماية البيانات. يمكنك حماية الرسائل المرسلة من Microsoft 365 إلى أي شخص داخل مؤسستك أو خارجها. يمكن عرض هذه الرسائل عبر مجموعة متنوعة من عملاء البريد باستخدام أي هوية، بما في ذلك Azure Active Directory وحساب Microsoft ومعرف Google. لمزيد من المعلومات حول كيفية استخدام مؤسستك للرسائل المشفرة، راجع [Office 365 تشفير الرسائل](./ome.md).

## <a name="transport-layer-security"></a>أمان طبقة النقل

إذا كنت ترغب في ضمان الاتصال الآمن مع شريك، يمكنك استخدام الموصلات الواردة والصادرة لتوفير الأمان وتكامل الرسائل. يمكنك تكوين TLS الواردة والصادرة المفروضة على كل موصل، باستخدام شهادة. يمكن أن يؤدي استخدام قناة SMTP مشفرة إلى منع سرقة البيانات عبر هجوم دخيل. لمزيد من المعلومات، راجع [كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني](./exchange-online-uses-tls-to-secure-email-connections.md).

## <a name="domain-keys-identified-mail"></a>البريد المعرف لمفاتيح المجال

يدعم Exchange Online Protection (EOP) ورسائل Exchange Online التحقق الوارد من صحة رسائل البريد المعرف لمفاتيح المجال (DKIM). DKIM هو طريقة للتحقق من أن رسالة تم إرسالها من المجال الذي تقول إنها نشأت منه وأنه لم يتم تزييفها من قبل شخص آخر. وهي تربط رسالة بريد إلكتروني بالمؤسسة المسؤولة عن إرسالها، وهي جزء من نموذج أكبر لتشفير البريد الإلكتروني. لمزيد من المعلومات حول الأجزاء الثلاثة من هذا النموذج، راجع:

- [إعداد SPF للمساعدة في منع تزييف الهوية](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [استخدام DKIM للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك المخصص](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [استخدام DMARC للتحقق من صحة البريد الإلكتروني](/office365/SecurityCompliance/use-dmarc-to-validate-email)
