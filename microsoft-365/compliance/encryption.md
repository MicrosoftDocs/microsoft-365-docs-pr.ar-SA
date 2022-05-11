---
title: التشفير في Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 0a322724-08ca-43db-b69a-afbfa20484cd
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365solution-mip
- m365initiative-compliance
description: مع Office 365، يتم تشفير المحتوى الخاص بك في حالة السكون وفي أثناء النقل مع أقوى التشفير والبروتوكولات والتقنيات المتاحة. احصل على نظرة عامة على التشفير في Office 365.
ms.openlocfilehash: 5f866931eba3078074b47c9cc8c5ed310489b9bb
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319254"
---
# <a name="encryption"></a>التشفير

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يعد التشفير جزءا مهما من استراتيجية حماية الملفات وحماية المعلومات. توفر هذه المقالة نظرة عامة على التشفير Office 365. احصل على المساعدة في مهام التشفير مثل كيفية إعداد التشفير لمؤسستك وكيفية حماية مستندات Office بكلمة مرور.
  
- للحصول على معلومات حول الشهادات والتقنيات مثل TLS، راجع [تفاصيل المرجع التقني حول التشفير في Office 365](technical-reference-details-about-encryption.md).

- للحصول على معلومات حول كيفية تكوين التشفير لمؤسستك أو إعداده، راجع [إعداد التشفير في Office 365 Enterprise](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>ما هو التشفير، وكيف يعمل في Office 365؟

ترميز عملية التشفير بياناتك (يشار إليها بنص عادي) في شفرة. على عكس النص العادي، لا يمكن استخدام شفرة التشفير من قبل الأشخاص أو أجهزة الكمبيوتر ما لم يتم فك تشفير النص المشفر وحتى يتم فك تشفيره. يتطلب فك التشفير مفتاح تشفير يملكه المستخدمون المعتمدون فقط. يساعد التشفير على التأكد من أن المستلمين المخولين فقط يمكنهم فك تشفير المحتوى الخاص بك. يتضمن المحتوى الملفات ورسائل البريد الإلكتروني وإدخالات التقويم وما إلى ذلك.
  
لا يمنع التشفير بحد ذاته اعتراض المحتوى. يعد التشفير جزءا من استراتيجية أكبر لحماية المعلومات لمؤسستك. باستخدام التشفير، يمكنك المساعدة في التأكد من أن الأطراف المخولة فقط يمكنها استخدام البيانات المشفرة.
  
يمكن أن يكون لديك طبقات متعددة من التشفير في نفس الوقت. على سبيل المثال، يمكنك تشفير رسائل البريد الإلكتروني وقنوات الاتصال التي يتم من خلالها تدفق بريدك الإلكتروني. مع Office 365، يتم تشفير بياناتك الثابتة والمتنقلة، باستخدام العديد من بروتوكولات التشفير القوية، والتقنيات التي تتضمن بروتوكول أمان طبقة النقل/طبقة مآخذ التوصيل الآمنة (TLS/SSL) وأمان بروتوكول الإنترنت (IPSec) ومعيار التشفير المتقدم (AES).
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>تشفير البيانات الثابتة والبيانات المتنقلة

 تتضمن **أمثلة البيانات الثابتة** الملفات التي قمت بتحميلها إلى مكتبة SharePoint، Project Online البيانات، والمستندات التي قمت بتحميلها في اجتماع Skype for Business، ورسائل البريد الإلكتروني والمرفقات التي قمت بتخزينها في مجلدات في علبة البريد، والملفات التي قمت بتحميلها إلى OneDrive for Business.
  
 تتضمن **أمثلة البيانات المتنقلة** رسائل البريد التي يتم تسليمها أو المحادثات التي تتم في اجتماع عبر الإنترنت. في Office 365، تكون البيانات قيد النقل كلما كان جهاز المستخدم يتصل بخادم Microsoft، أو عندما يتصل خادم Microsoft بخادم آخر.
  
مع Office 365، تعمل طبقات وأنواع متعددة من التشفير معا لتأمين بياناتك. يتضمن الجدول التالي بعض الأمثلة، مع ارتباطات إلى معلومات إضافية.
  
|**أنواع المحتويات**|**تقنيات التشفير**|**الموارد لمعرفة المزيد**|
|:-----|:-----|:-----|
|ملفات على جهاز. يمكن أن تتضمن هذه الملفات رسائل البريد الإلكتروني المحفوظة في مجلد، Office المستندات المحفوظة على كمبيوتر أو كمبيوتر لوحي أو هاتف، أو البيانات المحفوظة في سحابة Microsoft.  <br/> |BitLocker في مراكز بيانات Microsoft. يمكن أيضا استخدام BitLocker على أجهزة العميل، مثل أجهزة الكمبيوتر Windows وأجهزة الكمبيوتر اللوحية  <br/> إدارة المفاتيح الموزعة (DKM) في مراكز بيانات Microsoft  <br/> مفتاح العميل Microsoft 365  <br/> |[Windows مركز تكنولوجيا المعلومات: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [مركز توثيق Microsoft: التشفير](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [سلسلة عناصر تحكم أمان السحابة: تشفير البيانات الثابتة](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [كيف تؤمّن Exchange Online أسرار بريدك الإلكتروني](exchange-online-secures-email-secrets.md) <br/> [تشفير الخدمة باستخدام مفتاح العميل](customer-key-overview.md) <br/> |
|الملفات المتنقلة بين المستخدمين. يمكن أن تتضمن هذه الملفات مستندات Office أو عناصر قائمة SharePoint تمت مشاركتها بين المستخدمين.  <br/> |TLS للملفات المتنقلة  <br/> |[تشفير البيانات في OneDrive for Business و SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype for Business Online: الأمان والأرشفة](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|البريد الإلكتروني المتنقل بين المستلمين. يتضمن هذا البريد الإلكتروني البريد الإلكتروني الذي تستضيفه Exchange Online.  <br/> |تشفير الرسائل في Microsoft Purview باستخدام Azure Rights Management وS/MIME وTLS للبريد الإلكتروني المتنقل  <br/> |[تشفير essage](ome.md) <br/> [تشفير البريد الإلكتروني في Office 365](email-encryption.md) <br/> [كيفية استخدام Exchange Online لـ TLS لتأمين اتصالات البريد الإلكتروني في Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|الدردشات والرسائل والملفات المتنقلة بين المستلمين باستخدام Microsoft Teams. <br/> |يستخدم Teams TLS وMTLS لتشفير الرسائل الفورية. يتم تشفير حركة مرور الوسائط باستخدام RTP الآمن (SRTP). تستخدم Teams خوارزميات متوافقة مع FIPS (معيار معالجة المعلومات الفيدرالية) لتبادل مفاتيح التشفير. <br/> |[تشفير Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>ماذا لو احتجت إلى مزيد من التحكم في التشفير لتلبية متطلبات الأمان والتوافق؟

يوفر Microsoft 365 حلولا تديرها Microsoft لتشفير وحدة التخزين وتشفير الملفات وتشفير علبة البريد في Office 365. بالإضافة إلى ذلك، توفر Microsoft حلول تشفير يمكنك إدارتها والتحكم فيها. تم إنشاء حلول التشفير هذه على Azure.
  
لمعرفة المزيد، راجع الموارد التالية:
  
- [ما هو Azure Rights Management؟](/information-protection/understand-explore/what-is-azure-rms)

- [تنشيط Rights Management في مركز الإدارة](../enterprise/activate-rms-in-microsoft-365.md)

- [إعداد Rights Management المعلومات (IRM) في مركز إدارة SharePoint](set-up-irm-in-sp-admin-center.md)

- [تشفير الخدمة باستخدام مفتاح عميل Microsoft Purview](customer-key-overview.md)

- [تشفير المفتاح المزدوج](double-key-encryption.md)

## <a name="how-do-i"></a>كيف يمكنني...

|**لتنفيذ هذه المهمة**|**الاطلاع على هذه الموارد**|
|:-----|:-----|
|إعداد التشفير لمؤسستي|[إعداد التشفير في Office 365 Enterprise](set-up-encryption.md)|
|عرض تفاصيل حول الشهادات والتقنيات ومجموعات تشفير TLS|[تفاصيل تقنية حول التشفير](technical-reference-details-about-encryption.md)|
|استخدام الرسائل المشفرة على جهاز محمول|[عرض الرسائل المشفرة على](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) [الرسائل المشفرة في Android deviceView على iPhone أو iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|تشفير مستند باستخدام الحماية بكلمة مرور. (الحماية بكلمة مرور غير معتمدة في المستعرض. استخدم إصدارات سطح المكتب من Word و Excel و PowerPoint للحماية بكلمة مرور.) |[إضافة حماية أو إزالتها في المستند أو المصنف أو العرض التقديمي](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). اختر مقطع **"إضافة حماية** "، ثم راجع **"تشفير باستخدام كلمة المرور**".|
|إزالة التشفير من مستند|[إضافة حماية أو إزالتها في المستند أو المصنف أو العرض التقديمي](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). اختر مقطع **إزالة الحماية** ، ثم راجع **إزالة تشفير كلمة المرور**.  |

## <a name="related-topics"></a>المواضيع ذات الصلة

[التخطيط لإمكانيات الأمان وحماية المعلومات Microsoft 365](plan-for-security-and-compliance.md)

[أفضل الممارسات لتأمين Microsoft 365 لخطط الأعمال](/office365/admin/security-and-compliance/secure-your-business-data)

[Microsoft Stream تشفير مستوى الفيديو وتدفق التشغيل](/stream/network-overview#video-level-encryption-and-playback-flow)
