---
title: ميزات التشفير المدارة من قبل العملاء
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
ms.openlocfilehash: 80a0726e112324a673fc964a9fabdbc3ba0ac42e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566955"
---
# <a name="customer-managed-encryption-features"></a>ميزات التشفير المدارة من قبل العملاء

إلى جانب تقنيات التشفير في Microsoft 365 التي تديرها Microsoft، تعمل Microsoft 365 أيضا مع تقنيات التشفير الإضافية التي يمكنك إدارتها وتكوينها، مثل:

- [Azure Rights Management](/azure/information-protection/what-is-azure-rms)

- [Secure Multipurpose Internet Mail Extension](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx)

- [تشفير الرسائل من Office 365](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [تأمين تدفق البريد مع مؤسسة شريكة](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

لمزيد من المعلومات حول هذه التقنيات، راجع Microsoft 365 [أوصاف الخدمة.](/office365/servicedescriptions/office-365-service-descriptions-technet-library)

## <a name="azure-rights-management"></a>Azure Rights Management

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS) هي تقنية الحماية المستخدمة بواسطة [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection). فهو يستخدم سياسات التشفير والهوية والتخويل للمساعدة في تأمين الملفات والبريد الإلكتروني عبر الأنظمة الأساسية والأجهزة المتعددة— الهواتف وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر الشخصية. يمكن حماية المعلومات داخل مؤسستك وخارجها لأن الحماية تبقى مع البيانات. يوفر Azure RMS الحماية الدائمة لجميع أنواع الملفات، ويحمي الملفات من أي مكان، كما يدعم التعاون بين الأعمال، ومجموعة واسعة من الأجهزة Windows والأجهزة Windows الأخرى. يمكن أن تزيد حماية Azure RMS أيضا [من سياسات منع فقدان البيانات (DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)). لمزيد من المعلومات حول التطبيقات والخدمات التي يمكنها استخدام خدمة Azure Rights Management من Azure Information Protection، راجع كيفية دعم التطبيقات لخدمة [Azure Rights Management](/information-protection/understand-explore/applications-support).

إن Azure RMS متكامل مع Microsoft 365 ومتوفر لجميع العملاء. لتكوين Microsoft 365 استخدام Azure RMS، راجع تكوين إدارة حقوق المعلومات [(IRM) لاستخدام Azure Rights Management (إدارة حقوق Azure) ثم إعداد إدارة حقوق استخدام المعلومات (IRM) في SharePoint admin center](../enterprise/activate-rms-in-microsoft-365.md). إذا كنت تعمل على خادم RMS ل Active Directory (AD) المحلي، يمكنك أيضا تكوين إدارة حقوق المعلومات [(IRM) لاستخدام خادم AD RMS](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server) المحلي، ولكننا نوصي بشدة بالترحيل إلى [Azure RMS](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) لاستخدام ميزات جديدة مثل التعاون الآمن مع المؤسسات الأخرى.

عند حماية بيانات العملاء باستخدام Azure RMS، يستخدم Azure RMS مفتاح RSA غير متماثل 2048 بت مع خوارزمية التجزئة SHA-256 للتكامل لتشفير البيانات. المفتاح المتماثل لمستندات Office هو AES 128 بت. لكل مستند أو بريد إلكتروني محمي بواسطة Azure RMS، ينشئ Azure RMS مفتاح AES واحدا ("مفتاح المحتوى")، وهذا المفتاح مضمن في المستند، ويستمر عبر إصدارات المستند. يتم حماية مفتاح المحتوى باستخدام مفتاح RSA الخاص بالم المؤسسة ("مفتاح مستأجر Azure Information Protection") كجزء من النهج في المستند، كما يتم توقيع النهج من قبل كاتب المستند. إن مفتاح المستأجر هذا شائع في كل المستندات ورسائل البريد الإلكتروني المحمية بواسطة Azure RMS في المؤسسة ولا يمكن تغيير هذا المفتاح إلا بواسطة مسؤول Azure Information Protection إذا كانت المؤسسة تستخدم مفتاح مستأجر يديره العملاء. لمزيد من المعلومات حول عناصر تحكم التشفير المستخدمة بواسطة Azure RMS، راجع [كيف يعمل Azure RMS؟ تحت الغطاء](/information-protection/understand-explore/how-does-it-work).

في تنفيذ Azure RMS افتراضي، تقوم Microsoft بإنشاء المفتاح الجذر الفريد لكل مستأجر وإدارته. يمكن للعملاء إدارة دورة حياة المفتاح الجذر الخاص بهم في Azure RMS باستخدام Azure Key Vault Services باستخدام أسلوب إدارة رئيسي يسمى إحضار المفتاح الخاص بك [(BYOK)](/azure/information-protection/plan-implement-tenant-key) الذي يسمح لك بإنشاء المفتاح في HSMs المحلية (الوحدات النمطية لأمن الأجهزة)، والبقاء تتحكم في هذا المفتاح بعد النقل إلى نظام معلومات الأداء (FIPS 140-2) من Microsoft الذي تم التحقق من صحته من HSMs من المستوى 2. لا يتم منح حق الوصول إلى المفتاح الجذر لأي من الموظفين حيث لا يمكن تصدير المفاتيح أو استخراجها من أجهزة HSMs التي تحميهم. بالإضافة إلى ذلك، يمكنك الوصول إلى سجل في الوقت الحقيقي تقريبا يعرض كل الوصول إلى المفتاح الجذر في أي وقت. لمزيد من المعلومات، راجع [التسجيل وتحليل استخدام Azure Rights Management](/azure/information-protection/log-analyze-usage).

تساعد Azure Rights Management على التخفيف من المخاطر مثل التوسع السلكي وهجمة رجل في الوسط وسرقة البيانات والانتهاكات غير المقصودة لنهج المشاركة التنظيمية. وفي الوقت نفسه، يتم منع أي وصول غير مبرر لبيانات العميل أثناء النقل أو في وضع الراحة من قبل مستخدم غير مصرح له ليس لديه الأذونات المناسبة عبر سياسات تتبع تلك البيانات، وبالتالي تخفيف مخاطر وقوع تلك البيانات في أياد غير أمينة سواء عن علم أو عن غير علم وتوفير دالات منع فقدان البيانات. إذا تم استخدامها كجزء من Azure Information Protection، فإن Azure RMS يوفر أيضا قدرات تصنيف البيانات وتسميةها ووضع علامات على المحتوى وتعقب الوصول إلى المستندات وإمكانيات إلغاء الوصول. لمعرفة المزيد حول هذه الإمكانات، راجع [ما هو Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) وخريطة طريق نشر [Azure Information Protection](/information-protection/plan-design/deployment-roadmap) والبرامج التعليمية للبدء [السريع ل Azure Information Protection](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Secure Multipurpose Internet Mail Extension

إن Secure/Multipurpose Internet Mail Extensions (S/MIME) هي معيار لتشفير المفاتيح العامة والتوقيع الرقمي لبيانات MIME. يتم تعريف S/MIME في RFCs 3369 و3370 و3850 و3851 وغيرها. فهي تسمح للمستخدم بتشفير رسالة بريد إلكتروني وتوقيع رسالة بريد إلكتروني رقميا. لا يمكن فك تشفير البريد الإلكتروني المشفر باستخدام S/MIME إلا بواسطة مستلم البريد الإلكتروني باستخدام المفتاح الخاص الخاص به، وهو متوفر فقط لهذا المستلم. على هذا النحو، لا يمكن فك تشفير رسائل البريد الإلكتروني من قبل أي شخص آخر غير مستلم البريد الإلكتروني.

[تدعم Microsoft S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). يتم توزيع الشهادات العامة على Active Directory المحلية للعميل وتخزينها في سمات يمكن نسخها بشكل متماثل إلى مستأجر Microsoft 365 مستأجر. تبقى المفاتيح الخاصة التي تتوافق مع المفاتيح العمومية في الموقع ولا يتم إرسالها أبدا إلى Office 365. يمكن للمستخدمين إنشاء رسائل البريد الإلكتروني وتشفيرها وفك تشفيرها وقراءتها وتوقيعها رقميا بين مستخدمين اثنين في المؤسسة باستخدام Outlook Outlook على ويب و Exchange ActiveSync العملاء. لمزيد من المعلومات، راجع [تشفير S/MIME الآن في](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/) Office 365.

## <a name="office-365-message-encryption"></a>تشفير الرسائل من Office 365

[تشفير الرسائل من Office 365](https://products.office.com/exchange/office-365-message-encryption) (OME) المضمنة في أعلى [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) (AIP) من إرسال بريد مشفر ومحمي بحقوق لأي شخص. يعمل OME على الحد من المخاطر مثل اللمس السلكي وهجمة رجل في الوسط، وغير ذلك من التهديدات، مثل الوصول غير المبرر للبيانات من قبل مستخدم غير مصرح له ليس لديه الأذونات المناسبة. لقد قمنا باستثمارات توفر لك تجربة بريد إلكتروني أكثر بساطة وسهولة وأمانا مضمنة في حماية معلومات Azure. يمكنك حماية الرسائل المرسلة من Microsoft 365 إلى أي شخص داخل مؤسستك أو خارجها. يمكن عرض هذه الرسائل عبر مجموعة متنوعة من عملاء البريد باستخدام أي هوية، بما في ذلك Azure Active Directory و Microsoft Account و Google IDs. لمزيد من المعلومات حول كيفية استخدام مؤسستك للرسائل المشفرة[، راجع تشفير الرسائل من Office 365](./ome.md).

## <a name="transport-layer-security"></a>أمان طبقة النقل

إذا كنت تريد ضمان الاتصال الآمن مع شريك، يمكنك استخدام الموصلات الواردة والداخلة لتوفير الأمان وتكامل الرسائل. يمكنك تكوين TLS الصادرة والداخلة على كل موصل، باستخدام شهادة. يمكن أن يمنع استخدام قناة SMTP مشفرة من سرقة البيانات عبر هجوم رجل في الوسط. لمزيد من المعلومات، راجع [كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني](./exchange-online-uses-tls-to-secure-email-connections.md).

## <a name="domain-keys-identified-mail"></a>البريد المعرف لمفاتيح المجال

Exchange Online Protection (EOP) Exchange Online التحقق من الصحة الوارد لرسائل البريد المعرف لمفاتيح المجال (DKIM). DKIM هي طريقة للتحقق من أن رسالة تم إرسالها من المجال الذي تقول إنها منشئة منه ولم يتم اعادتها من قبل شخص آخر. وهو يربط رسالة بريد إلكتروني مع المؤسسة المسؤولة عن إرسالها، وهو جزء من نموذج أكبر لتشفير البريد الإلكتروني. لمزيد من المعلومات حول الأجزاء الثلاثة من هذا النموذج، راجع:

- [إعداد SPF للمساعدة في منع التهز](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [استخدام DKIM للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك المخصص](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [استخدام DMARC للتحقق من صحة البريد الإلكتروني](/office365/SecurityCompliance/use-dmarc-to-validate-email)