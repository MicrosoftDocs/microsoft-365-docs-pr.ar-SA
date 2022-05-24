---
title: التعافي من هجوم برامج ضارة
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- m365solution-ransomware
description: يمكن للمسؤولين Microsoft 365 تعلم كيفية التعافي من هجوم برامج الفدية الضارة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 328457e37ea6ae351abb2c5d5f0089246145b32c
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648646"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>التعافي من هجوم برامج الفدية الضارة في Microsoft 365

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

حتى إذا اتخذت كل الاحتياطات لحماية مؤسستك، فلا يزال بإمكانك أن تقع ضحية لهجوم [برامج الفدية الضارة](/windows/security/threat-protection/intelligence/ransomware-malware) . برامج الفدية الضارة هي أعمال كبيرة، وفي مشهد التهديد اليوم Microsoft 365 هو هدف متزايد باستمرار [للهجمات المتطورة](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Cloudy-With-A-Chance-Of-APT-Novel-Microsoft-365-Attacks-In-The-Wild.pdf).

ستمنحك الخطوات الواردة في هذه المقالة أفضل فرصة لاسترداد البيانات وإيقاف الانتشار الداخلي للعدوى. قبل البدء، ضع في اعتبارك العناصر التالية:

- لا يوجد ضمان بأن دفع الفدية سيعيد الوصول إلى ملفاتك. في الواقع، دفع الفدية يمكن أن يجعل منك هدفا لمزيد من برامج الفدية الضارة.

  إذا كنت قد دفعت بالفعل، ولكنك قمت باسترداد المبلغ بدون استخدام حل المهاجم، فاتصل بالبنك لمعرفة ما إذا كان بإمكانه حظر المعاملة.

  نوصي أيضا بالإبلاغ عن هجوم برامج الفدية الضارة لتطبيق القانون ومواقع الإبلاغ عن رسائل احتيالية وMicrosoft كما هو موضح لاحقا في هذه المقالة.

- من المهم أن تستجيب بسرعة للهجوم وعواقبه. كلما انتظرت لفترة أطول، قل احتمالية إمكانية استرداد البيانات المتأثرة.

## <a name="step-1-verify-your-backups"></a>الخطوة 1: التحقق من النسخ الاحتياطية

إذا كان لديك نسخ احتياطية دون اتصال، يمكنك على الأرجح استعادة البيانات المشفرة **بعد** إزالة حمولة برامج الفدية الضارة (البرامج الضارة) من بيئتك **وبعد** التحقق من عدم وجود وصول غير مصرح به في بيئات Microsoft 365.

إذا لم يكن لديك نسخ احتياطية، أو إذا تأثرت النسخ الاحتياطية الخاصة بك أيضا برامج الفدية الضارة، يمكنك تخطي هذه الخطوة.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>الخطوة 2: تعطيل Exchange ActiveSync المزامنة من OneDrive

النقطة الرئيسية هنا هي إيقاف انتشار تشفير البيانات بواسطة برامج الفدية الضارة.

إذا كنت تشك في البريد الإلكتروني كهدف لتشفير برامج الفدية الضارة، فعطل وصول المستخدم مؤقتا إلى علب البريد. Exchange ActiveSync مزامنة البيانات بين الأجهزة وعلب بريد Exchange Online.

لتعطيل Exchange ActiveSync علبة بريد، راجع [كيفية تعطيل Exchange ActiveSync للمستخدمين في Exchange Online](https://support.microsoft.com/help/2795303).

لتعطيل أنواع أخرى من الوصول إلى علبة البريد، راجع:

- [تمكين MAPI لعلبة بريد أو تعطيلها](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).

- [تمكين الوصول إلى POP3 أو IMAP4 أو تعطيله لمستخدم](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

سيساعد إيقاف المزامنة من OneDrive مؤقتا على حماية بياناتك السحابية من التحديث بواسطة الأجهزة التي يحتمل أن تكون مصابة. لمزيد من المعلومات، راجع [كيفية إيقاف المزامنة مؤقتا واستئنافها في OneDrive](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e).

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>الخطوة 3: إزالة البرامج الضارة من الأجهزة المتأثرة

قم بتشغيل فحص كامل مكافحة الفيروسات الحالي على جميع أجهزة الكمبيوتر والأجهزة المشتبه بها للكشف عن الحمولة المقترنة ببرامج الفدية الضارة وإزالتها.

لا تنس فحص الأجهزة التي تقوم بمزامنة البيانات، أو أهداف محركات أقراص الشبكة المعينة.

يمكنك استخدام [Windows Defender](https://www.microsoft.com/windows/comprehensive-security) أو (للعملاء الأقدم) [Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201).

البديل الذي سيساعدك أيضا على إزالة برامج الفدية الضارة أو البرامج الضارة هو [أداة إزالة البرامج الضارة (MSRT).](https://www.microsoft.com/download/details.aspx?id=9905)

إذا لم تعمل هذه الخيارات، يمكنك تجربة [Windows Defender دون اتصال](https://support.microsoft.com/help/17466) أو [استكشاف المشاكل المتعلقة بالكشف عن البرامج الضارة وإزالتها](https://support.microsoft.com/help/4466982) وإصلاحها.

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>الخطوة 4: استرداد الملفات على كمبيوتر أو جهاز تم تنظيفه

بعد الانتهاء من الخطوة السابقة لإزالة حمولة برامج الفدية الضارة من بيئتك (والتي ستمنع برامج الفدية الضارة من تشفير ملفاتك أو إزالتها)، يمكنك استخدام [محفوظات](https://support.microsoft.com/help/17128) الملفات في Windows 11، Windows 10، Windows 8.1، وباستخدام System Protection في Windows 7 لمحاولة استرداد الملفات والمجلدات المحلية.

**الملاحظات**:

- ستقوم بعض برامج الفدية الضارة أيضا بتشفير إصدارات النسخ الاحتياطي أو حذفها، بحيث لا يمكنك استخدام "محفوظات الملفات" أو "حماية النظام" لاستعادة الملفات. إذا حدث ذلك، تحتاج إلى استخدام النسخ الاحتياطية على محركات الأقراص الخارجية أو الأجهزة التي لم تتأثر برامج الفدية الضارة أو OneDrive كما هو موضح في القسم التالي.

- إذا تمت مزامنة مجلد مع OneDrive ولا تستخدم أحدث إصدار من Windows، فقد تكون هناك بعض القيود باستخدام "محفوظات الملفات".

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>الخطوة 5: استرداد ملفاتك في OneDrive for Business

تسمح لك استعادة الملفات في OneDrive for Business باستعادة OneDrive بالكامل إلى نقطة زمنية سابقة خلال آخر 30 يوما. لمزيد من المعلومات، راجع [استعادة OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15).

## <a name="step-6-recover-deleted-email"></a>الخطوة 6: استرداد البريد الإلكتروني المحذوفة

في الحالة النادرة التي حذفت برامج الفدية الضارة جميع رسائل البريد الإلكتروني الخاصة بك، يمكنك على الأرجح استرداد العناصر المحذوفة. لمزيد من المعلومات، اطلع على:

- [استرداد الرسائل المحذوفة في علبة بريد المستخدم](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [استرداد العناصر المحذوفة في Outlook Windows](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>الخطوة 7: إعادة تمكين Exchange ActiveSync المزامنة من OneDrive

بعد تنظيف أجهزة الكمبيوتر والأجهزة واسترداد بياناتك، يمكنك إعادة تمكين Exchange ActiveSync المزامنة من OneDrive التي قمت بتعطيلها مسبقا في [الخطوة 2](#step-2-disable-exchange-activesync-and-onedrive-sync).

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>الخطوة 8 (اختياري): حظر المزامنة من OneDrive لملحقات ملفات معينة

بعد التعافي، يمكنك منع العملاء OneDrive for Business من مزامنة أنواع الملفات التي تأثرت باستخدام برامج الفدية الضارة هذه. لمزيد من المعلومات، راجع [Set-SPOTenantSyncClientRestriction](/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction)

## <a name="report-the-attack"></a>الإبلاغ عن الهجوم

### <a name="contact-law-enforcement"></a>الاتصال بتطبيق القانون

يجب عليك الاتصال بوكالات إنفاذ القانون المحلية أو الفيدرالية. على سبيل المثال، إذا كنت في الولايات المتحدة، يمكنك الاتصال [بمكتب الحقول المحلي في مكتب إدارة الحقول أو](https://www.fbi.gov/contact-us/field) [IC3](http://www.ic3.gov/complaint/default.aspx) أو [الخدمة السرية](http://www.secretservice.gov/).

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>إرسال تقرير إلى موقع ويب الخاص بتقارير الرسائل الخادعة في بلدك

توفر مواقع التقارير الخادعة معلومات حول كيفية منع رسائل الخادعة وتجنبها. كما أنها توفر آليات للإبلاغ إذا كنت ضحية لعملية احتيال.

- أستراليا: [SCAMwatch](http://www.scamwatch.gov.au/)

- كندا: [المركز الكندي لمكافحة الاحتيال](http://www.antifraudcentre-centreantifraude.ca/)

- فرنسا: [معلومات الوكالة الوطنية ل la sécurité des systèmes d'information](http://www.ssi.gouv.fr/)

- ألمانيا: [بونdesamt für Sicherheit في der Informationstechtechtechit](https://www.bsi.bund.de/DE/Home/home_node.html)

- أيرلندا: [جاردا سيوشانا](http://www.garda.ie/)

- نيوزيلندا: [رسائل تصيد احتيالي حول الشؤون الاستهلاكية](http://www.consumeraffairs.govt.nz/scams)

- سويسرا [Nationales Zentrum für Cybersicherheit NCSC](https://www.ncsc.admin.ch/ncsc/de/home.html)

- المملكة المتحدة: [الاحتيال الإجرائي](http://www.actionfraud.police.uk/)

- الولايات المتحدة: [عند الحماية عبر الإنترنت](http://www.onguardonline.gov/)

إذا لم يكن بلدك مدرجا، فاسأل وكالات إنفاذ القانون المحلية أو الفيدرالية.

### <a name="submit-email-messages-to-microsoft"></a>إرسال رسائل البريد الإلكتروني إلى Microsoft

يمكنك الإبلاغ عن رسائل التصيد الاحتيالي التي تحتوي على برامج الفدية الضارة باستخدام إحدى الطرق المتعددة. لمزيد من المعلومات، راجع [تقارير الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="additional-ransomware-resources"></a>موارد برامج الفدية الإضافية

المعلومات الرئيسية من Microsoft:

- [التهديد المتزايد من برامج الفدية الضارة](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/)، منشور مدونة Microsoft On the Issues في 20 يوليو 2021
- [برامج الفدية الضارة التي يديرها الإنسان](/security/compass/human-operated-ransomware)
- [الحماية السريعة من برامج الفدية الضارة والمساهمة](/security/compass/protect-against-ransomware)
- [تقرير الدفاع الرقمي ل Microsoft 2021](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (راجع الصفحات 10-19)
- [برامج الفدية الضارة: تقرير تحليلات مخاطر التهديدات المنتشرة والمستمرة](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) في مدخل Microsoft 365 Defender

Microsoft 365:

- [نشر الحماية من برامج الفدية الضارة لمستأجر Microsoft 365 الخاص بك](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [زيادة مرونة برامج الفدية الضارة مع Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [البرامج الضارة والحماية من برامج الفدية الضارة](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [حماية الكمبيوتر الشخصي Windows من برامج الفدية الضارة](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [التعامل مع برامج الفدية الضارة في SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [تقارير تحليلات التهديد حول برامج الفدية الضارة](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) في مدخل Microsoft 365 Defender

Microsoft 365 Defender:

- [البحث عن برامج الفدية الضارة باستخدام التتبع المتقدم](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses لهجمات برامج الفدية الضارة](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [زيادة مرونة برامج الفدية الضارة مع Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [خطة النسخ الاحتياطي والاستعادة للحماية من برامج الفدية الضارة](/security/compass/backup-plan-to-protect-against-ransomware)
- [المساعدة في الحماية من برامج الفدية الضارة باستخدام Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (فيديو لمدة 26 دقيقة)
- [التعافي من اختراق الهوية النظامية](/azure/security/fundamentals/recover-from-identity-compromise)
- [الكشف المتقدم عن الهجوم متعدد المستويات في Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [اكتشاف الاندماج لبرنامج الفدية الضارة في Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [إنشاء نهج الكشف عن الحالات الشاذة في Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

منشورات مدونة فريق أمان Microsoft:

- [3 خطوات لمنع برامج الفدية الضارة والتعافي منها (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [دليل لمكافحة برامج الفدية الضارة التي يديرها الإنسان: الجزء الأول (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  الخطوات الرئيسية حول كيفية قيام فريق الكشف والاستجابة من Microsoft (DART) بإجراء التحقيقات في حوادث برامج الفدية الضارة.

- [دليل لمكافحة برامج الفدية الضارة التي يديرها الإنسان: الجزء 2 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  التوصيات وأفضل الممارسات.

- [القدرة على الصمود من خلال فهم مخاطر الأمان عبر الإنترنت: الجزء 4 - التنقل بين التهديدات الحالية (مايو 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  راجع قسم **برامج الفدية الضارة** .

- [هجمات برامج الفدية الضارة التي يديرها الإنسان: كارثة يمكن الوقاية منها (مارس 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  يتضمن تحليلات سلسلة الهجوم للهجمات الفعلية.

- [استجابة برامج الفدية الضارة - للدفع أو عدم الدفع؟ (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [يستجيب Norsk Hydro لهجوم برامج الفدية الضارة بالشفافية (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
