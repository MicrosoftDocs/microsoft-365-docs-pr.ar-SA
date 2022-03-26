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
description: مع Office 365، يتم تشفير المحتوى الخاص بك في وضع الراحة وعند النقل باستخدام أقوى التشفير والبروتوكولات والتقنيات المتوفرة. احصل على نظرة عامة حول التشفير في Office 365.
ms.openlocfilehash: a1ee73d7ded7a02cd7851081412d2403e0ca8f1d
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/26/2021
ms.locfileid: "63568561"
---
# <a name="encryption"></a>التشفير

التشفير هو جزء هام من استراتيجية حماية الملفات وحماية المعلومات. توفر هذه المقالة نظرة عامة على التشفير Office 365. احصل على تعليمات حول مهام التشفير مثل كيفية إعداد التشفير لمنظمتك وكيفية حماية Office المرور.
  
- للحصول على معلومات حول الشهادات والتقنيات مثل TLS، راجع [تفاصيل المراجع التقنية حول التشفير في](technical-reference-details-about-encryption.md) Office 365.

- للحصول على معلومات حول كيفية تكوين التشفير أو إعداده لمنظمتك، راجع إعداد التشفير [في](set-up-encryption.md) Office 365 Enterprise.

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>ما هو التشفير، وكيف يعمل في Office 365؟

ترميز البيانات (يشار إليها باسم النص العادي) إلى نص ciphertext. بخلاف النص العادي، لا يمكن استخدام ciphertext من قبل الأشخاص أو أجهزة الكمبيوتر إلا إذا تم فك تشفير ciphertext ونهاية. يتطلب فك التشفير مفتاح تشفير لا تملكه سوى المستخدمين المعتمدين. يساعد التشفير على ضمان أن المستلمين المخولاين فقط يمكنهم فك تشفير المحتوى الخاص بك. يتضمن المحتوى الملفات ورسائل البريد الإلكتروني إدخالات التقويم وما إلى ذلك.
  
لا يمنع التشفير بحد ذاته تقاطع المحتوى. التشفير هو جزء من استراتيجية حماية معلومات أكبر لمنظمتك. باستخدام التشفير، يمكنك المساعدة في ضمان أنه يمكن فقط للأطراف المخولاة استخدام البيانات المشفرة.
  
يمكنك وضع طبقات متعددة من التشفير في مكانها في الوقت نفسه. على سبيل المثال، يمكنك تشفير رسائل البريد الإلكتروني وقنوات الاتصال التي يتم من خلالها تدفق البريد الإلكتروني. باستخدام Office 365، يتم تشفير بياناتك في وضع الراحة والعبور، باستخدام العديد من بروتوكولات التشفير القوية والتقنيات التي تتضمن أمان طبقة النقل/طبقة مآخذ التوصيل الآمنة (TLS/SSL) وأمان بروتوكول الإنترنت (IPSec) معيار التشفير المتقدم (AES).
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>تشفير البيانات أثناء الراحة والبيانات أثناء النقل

  تتضمن أمثلة البيانات الباقية الملفات التي قمت بتحميلها إلى مكتبة SharePoint وبيانات Project Online والمستندات التي قمت بتحميلها في اجتماع Skype for Business ورسائل البريد الإلكتروني والمرفقات التي قمت بتخزينها في مجلدات في علبة البريد والملفات التي قمت بتحميلها إلى OneDrive for Business.
  
 **تتضمن أمثلة البيانات أثناء** النقل رسائل البريد التي يتم تسليمها أو المحادثات التي تجري في اجتماع عبر الإنترنت. في Office 365، يتم نقل البيانات كلما كان جهاز المستخدم يقوم بالتواصل مع خادم Microsoft، أو عندما يقوم خادم Microsoft بالتواصل مع خادم آخر.
  
باستخدام Office 365، تعمل الطبقات وأنواع التشفير المتعددة معا لتأمين البيانات. يتضمن الجدول التالي بعض الأمثلة، مع ارتباطات إلى معلومات إضافية.
  
|**أنواع المحتويات**|**تقنيات التشفير**|**الموارد لمعرفة المزيد**|
|:-----|:-----|:-----|
|الملفات على جهاز. يمكن أن تتضمن هذه الملفات رسائل بريد إلكتروني محفوظة في مجلد أو Office محفوظة على كمبيوتر أو كمبيوتر لوحي أو هاتف أو بيانات محفوظة في سحابة Microsoft.  <br/> |BitLocker في مراكز بيانات Microsoft. يمكن أيضا استخدام BitLocker على أجهزة العميل، مثل أجهزة الكمبيوتر وأجهزة الكمبيوتر اللوحية Windows الكمبيوتر  <br/> توزيع إدارة المفاتيح (DKM) في مراكز بيانات Microsoft  <br/> مفتاح العميل Microsoft 365  <br/> |[Windows مركز المعلومات: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [مركز Microsoft Trust Center: التشفير](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [سلسلة عناصر التحكم في أمان السحابة: تشفير البيانات في Rest](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [كيف Exchange Online تأمين أسرار بريدك الإلكتروني](exchange-online-secures-email-secrets.md) <br/> [تشفير الخدمة باستخدام "مفتاح العميل"](customer-key-overview.md) <br/> |
|الملفات التي يتم نقلها بين المستخدمين. يمكن أن تتضمن هذه الملفات Office مستندات أو SharePoint عناصر قائمة مشتركة بين المستخدمين.  <br/> |TLS للملفات أثناء النقل  <br/> |[تشفير البيانات في OneDrive for Business SharePoint عبر الإنترنت](data-encryption-in-odb-and-spo.md) <br/> [Skype for Business عبر الإنترنت: الأمان والأرشفة](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|البريد الإلكتروني أثناء النقل بين المستلمين. يتضمن هذا البريد الإلكتروني البريد الإلكتروني المستضاف بواسطة Exchange Online.  <br/> |تشفير الرسائل من Office 365 Azure Rights Management و S/MIME و TLS للبريد الإلكتروني أثناء النقل  <br/> |[تشفير الرسائل من Office 365 (OME)](ome.md) <br/> [تشفير البريد الإلكتروني في Office 365](email-encryption.md) <br/> [كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني في Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|الدردشات والرسائل والملفات أثناء نقلها بين المستلمين باستخدام Microsoft Teams. <br/> |Teams TLS و MTLS لتشفير الرسائل الفورية. يتم تشفير نقل الوسائط باستخدام Secure RTP (SRTP). Teams استخدام الخوارزميات المتوافقة مع FIPS (قياسي معالجة المعلومات الفيدرالية) لتبادل مفاتيح التشفير. <br/> |[تشفير Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>ماذا لو احتجت إلى المزيد من التحكم في التشفير لتلبية متطلبات الأمان والتوافق؟

Microsoft 365 حلولا مدارة من Microsoft لتشفير مستوى الصوت وتشفير الملفات وتشفير علبة البريد في Office 365. بالإضافة إلى ذلك، توفر Microsoft حلول تشفير يمكنك إدارتها والتحكم بها. لقد تم بناء حلول التشفير هذه على Azure.
  
لمعرفة المزيد، راجع الموارد التالية:
  
- [ما هي Azure Rights Management؟](/information-protection/understand-explore/what-is-azure-rms)

- [تنشيط إدارة الحقوق في مركز الإدارة](../enterprise/activate-rms-in-microsoft-365.md)

- [إعداد إدارة حقوق استخدام المعلومات (IRM) في SharePoint إدارة](set-up-irm-in-sp-admin-center.md)

- [تشفير الخدمة باستخدام "مفتاح العميل" في Office 365](customer-key-overview.md)

- [تشفير المفتاح المزدوج Microsoft 365](double-key-encryption.md)

## <a name="how-do-i"></a>كيف يمكنني...

|**للقيام بهذه المهمة**|**الاطلاع على هذه الموارد**|
|:-----|:-----|
|إعداد التشفير لمنظمتي|[إعداد التشفير في Office 365 Enterprise](set-up-encryption.md)|
|عرض تفاصيل حول الشهادات والتقنيات و مجموعات رموز TLS|[التفاصيل التقنية حول التشفير](technical-reference-details-about-encryption.md)|
|استخدام الرسائل المشفرة على جهاز محمول|[عرض الرسائل المشفرة على جهاز Androidعرض](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) الرسائل المشفرة على [iPhone أو iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|تشفير مستند باستخدام الحماية بكلمة مرور. (الحماية بكلمة مرور غير معتمدة في المستعرض. استخدم إصدارات سطح المكتب من Word Excel وs PowerPoint لحماية كلمة المرور.) |[يمكنك إضافة حماية أو إزالتها في المستند أو المصنف أو العرض التقديمي](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). اختر مقطع **إضافة حماية** ، ثم راجع **التشفير باستخدام كلمة المرور**.|
|إزالة التشفير من مستند|[يمكنك إضافة حماية أو إزالتها في المستند أو المصنف أو العرض التقديمي](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). اختر مقطع **إزالة الحماية** ، ثم راجع **إزالة تشفير كلمة المرور**.  |

## <a name="related-topics"></a>المواضيع ذات الصلة

[التخطيط Microsoft 365 الأمان وحماية المعلومات](plan-for-security-and-compliance.md)

[أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](/office365/admin/security-and-compliance/secure-your-business-data)

[تشفير مستوى فيديو Microsoft Stream وتدفق التشغيل](/stream/network-overview#video-level-encryption-and-playback-flow)