---
title: دعم IPv6 في خدمات Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/03/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'ملخص: يصف دعم IPv6 في مكونات Microsoft 365 وفي عروض الحكومة Microsoft 365.'
ms.openlocfilehash: 6cd53b71c6e15346d4940c539eea4aff0e5a613e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096469"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>دعم IPv6 في خدمات Microsoft 365

يدعم Microsoft 365 كل من IPv6 وIPv4؛ ومع ذلك، لا يتم تمكين جميع ميزات Microsoft 365 بالكامل باستخدام IPv6. وهذا يعني أنه يجب عليك استخدام كل من IPv4 وIPv6 للاتصال Microsoft 365. إذا كنت تقوم بتصفية نسبة استخدام الشبكة الصادرة إلى Microsoft 365، يمكن العثور على القائمة الكاملة لعناوين IPv6 المعتمدة من قبل Microsoft 365 في [المقالة Microsoft 365 عناوين URL ونطاقات عناوين IP](urls-and-ip-address-ranges.md). بعد تكوين الشبكة الخاصة بك ويسمح بعناوين IPv6 المناسبة، يمكنك تنزيل [خطة اختبار IPv6 Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=293447) من مركز تنزيل Microsoft.

> [!NOTE]
> يعد تمكين العملاء من تجربة Microsoft 365 خدمات SaaS من أي موقع وأي جهاز أولوية ل Microsoft. يشمل ذلك السماح للعملاء بالاتصال واستهلاك Microsoft 365 من عملاء IPv6 الممكنين وIPv6 فقط وأنظمة المعلومات. كما يتضمن تمكين عملاء الحكومة من الوفاء بالتزامات IPv6 على شبكاتهم مع الاستمرار في استهلاك Microsoft 365 سيناريوهات الإنتاجية دون أي انقطاع.  
> توفر هذه المقالة قائمة بخدمات Microsoft 365 SaaS التي تسمح بالاتصال المباشر ب IPv6 اليوم. من المتوقع أن يستمر توسيع نطاق الخدمات التي تسمح بالاتصال المباشر ب IPv6. Microsoft 365 الخدمات غير المذكورة صراحة لدعم IPv6 المباشر، لتضمين خدمات مصادقة Azure Active Directory (AAD (دليل Azure النشط))، يجب اعتبار أنها تتطلب اتصال DNS64/NAT64 من عملاء وبيئات IPv6 فقط.  وهذا يتماشى مع الهدف الموضح حاليا في وثائق NIST USGv6 الحالية: متطلبات قدرة آلية الانتقال في [منشور NIST الخاص 500-267A Revision 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 هي تقنيات مقبولة لتوظيفها.
> - دعم NAT64 لآلية الانتقال NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Stateful NAT64: عنوان الشبكة وترجمة البروتوكول من عملاء IPv6 إلى خوادم IPv4
> - دعم DNS64 لآلية الانتقال DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: ملحقات DNS لترجمة عنوان الشبكة من عملاء IPv6 إلى IPv4 Server

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>دعم IPv6 في خدمة اشتراك Microsoft 365

### <a name="exchange-online-and-ipv6"></a>Exchange Online وIPv6

إذا كان البرنامج الذي تستخدمه للاتصال Exchange Online يدعم IPv6، فسيستخدم IPv6 بشكل افتراضي على كل من الشبكات السلكية واللاسلكية. إذا كنت تريد التحكم في الاتصالات Exchange Online، فاستخدم نطاقات عناوين IP في [Microsoft 365 نطاقات عناوين URL وعناوين IP](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online وIPv6

 **Microsoft 365 Government G1/G3/G4/K1** إذا كان البرنامج الذي تستخدمه للاتصال SharePoint Online يدعم IPv6، فسيحاول استخدام IPv6 بشكل افتراضي.
  
 **السحابة العامة متعددة المستأجرين** تمكن Microsoft SharePoint Online IPv6 بناء على طلبك. تحتاج إلى توفير عناوين IP الموضحة CIDR للبنية الأساسية DNS لمؤسستك. ضع في اعتبارك أنه لا يمكن مشاركة البنية الأساسية DNS هذه من قبل مؤسسات أخرى لتمكين IPv6 للمستأجر الخاص بك. بعد تمكين IPv6، إذا كان البرنامج الذي تستخدمه للاتصال SharePoint Online يدعم IPv6، فإنه يستخدم IPv6 بشكل افتراضي.
  
إذا كان البرنامج الذي تستخدمه للاتصال SharePoint Online يدعم IPv6، فسيستخدم IPv6 بشكل افتراضي على كل من الشبكات السلكية واللاسلكية. إذا كنت تريد التحكم في الاتصالات إلى SharePoint Online، فاستخدم نطاقات عناوين IP في [Microsoft 365 نطاقات عناوين URL وعناوين IP](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business وIPv6

الرجاء العلم أن IPv6 غير معتمد في Skype for Business ولا يمكن تمكينه بعد الآن.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams وبوابة SIP وIPV6

يدعم Microsoft Teams التوجيه المباشر وبوابة SIP IPv4 فقط. تدعم خدمة Microsoft Teams والعميل كل من IPv4 وIPv6. إذا كنت تريد التحكم في الاتصالات Microsoft Teams، فاستخدم نطاقات عناوين IP في [Microsoft 365 نطاقات عناوين URL وعناوين IP](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection وIPv6

يدعم Exchange Online Protection (EOP) IPv6 إذا حدث الإرسال عبر بروتوكول أمان طبقة النقل. بالنسبة إلى نطاق EOP، استخدم [عناوين URL Microsoft 365 ونطاقات عناوين IP](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>دعم IPv6 لعروض Microsoft 365 الحكومية

يتوافق دعم IPv6 Microsoft 365 لعروض الحكومة مع Office الإدارة والميزانية (OMB) للمسؤولين عن المعلومات في الأقسام التنفيذية والوكالة، بالإضافة إلى مصادقة الحكومة الفيدرالية لإصدار بروتوكول الإنترنت 6 (IPv6). [Microsoft Microsoft 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) هي خدمة متعددة المستأجرين تخزن بيانات حكومة الولايات المتحدة في سحابة مجتمع منفصلة. مثل عروض Microsoft 365 الأخرى، يوفر خدمات الإنتاجية والتعاون، بما في ذلك Exchange Online، Skype for Business، SharePoint Online، Microsoft 365 Apps for enterprise. 

تنطبق عروض Microsoft Microsoft 365 الحكومية فقط على عام 2013 والإصدارات الأحدث. لمزيد من المعلومات حول عروض الحكومة Microsoft 365، راجع [الإعلان عن Microsoft 365 للحكومة: سحابة القطاع الحكومي أمريكي](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). 

توفر Microsoft Microsoft 365 للمؤسسات خدمات استضافة مخصصة لحلول إنتاجية Microsoft التي تدعم متطلبات الأمان والخصوصية والتوافق التنظيمي للوكالات الفيدرالية الأمريكية التي تتطلب شهادة إدارة أمان المعلومات الفيدرالية (FISMA) والكيانات التجارية الخاضعة ل ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>الأمور التي يجب مراعاتها عند استخدام IPv6 و Microsoft 365

نوصي بعدم تعطيل IPv6. لمزيد من المعلومات، راجع [مقالة الإرشادات](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users) هذه. لتحديد إصدارات IP المستخدمة على شبكتك، ضع في اعتبارك ما يلي:
  
- إذا احتوى عرض الأمر **IPConfig** في موجه الأوامر على صفوف تسمى "عنوان IPv6" أو "عنوان IPv6 مؤقت"، فلديك IPv6 في بيئتك.

- إذا كانت جميع عناوين IPv6 تبدأ ب "fe80" وتتوافق مع الصفوف المسماة "Link-Local IPv6 Address"، فليس لديك IPv6 في بيئتك.

قد تنطبق هذه الاعتبارات على شبكتك:
  
- لا تدعم خدمة الاشتراك العام الشراء بواسطة بطاقة الائتمان عبر IPv6. لا ينطبق هذا على سحابة القطاع الحكومي (سحابة القطاع الحكومي) لأن الحكومات لديها ترخيص اتفاقية Enterprise (EA).

- لا يدعم IPv6 بعض سيناريوهات خدمات إدارة الحقوق (RMS).

- لا يدعم IPv6 خادم BlackBerry® Enterprise Server (BES) لأن BlackBerry لا يدعم IPv6.

- إذا كنت تستخدم خدمات الأمان المشترك لـ Active Directory (AD FS) مع Microsoft 365، فلن يتم دعم الإعلان عن نقطة نهاية شبكة AD FS Microsoft 365 باستخدام IPv6. يجب عدم تضمين سجلات AAAA في إدخال AD FS DNS عند استخدام Exchange Online. 

فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>راجع أيضًا

[خارطة طريق Learning IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[دليل بقاء IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
