---
title: دعم IPv6 في Microsoft 365 الخدمات
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'ملخص: يصف دعم IPv6 Microsoft 365 مكوناته وفي Microsoft 365 الحكومة.'
ms.openlocfilehash: a6a2e11ff2e312c02f10d152fe580bdead5fa7c9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63569581"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>دعم IPv6 في Microsoft 365 الخدمات

Microsoft 365 دعم كل من IPv6 و IPv4؛ ومع ذلك، لا يتم تمكين جميع Microsoft 365 بالكامل باستخدام IPv6. وهذا يعني أنه يجب استخدام كل من IPv4 و IPv6 للاتصال Microsoft 365. إذا كنت تقوم بتصفية حركة المرور الصادرة إلى Microsoft 365، يمكن العثور على القائمة الكاملة عناوين IPv6 المعتمدة بواسطة Microsoft 365 في المقالة Microsoft 365 نطاقات عناوين [IP وعناوين](urls-and-ip-address-ranges.md) URL. بعد تكوين الشبكة والسماح عناوين IPv6 المناسبة، يمكنك تنزيل خطة اختبار [iPv6 Microsoft 365 IPv6](https://go.microsoft.com/fwlink/?LinkId=293447) من مركز التنزيل ل Microsoft.

> [!NOTE]
> إن تمكين العملاء من تجربة Microsoft 365 SaaS من أي موقع وأي جهاز هو من أولويات Microsoft. يشمل ذلك السماح للعملاء بالاتصال بنظم المعلومات Microsoft 365 من IPv6 التي تم تمكينها و IPv6 فقط للعملاء وأنظمت المعلومات. كما يشمل أيضا تمكين عملاء الحكومة من تلبية التزامات IPv6 على شبكاتهم مع الاستمرار في استخدام Microsoft 365 الإنتاجية دون أي انقطاع.  
> توفر هذه المقالة قائمة بالخدمات Microsoft 365 SaaS التي تسمح باتصال IPv6 المباشر اليوم. من المتوقع أن يستمر توسيع نطاق الخدمات التي تسمح باتصال IPv6 المباشر. Microsoft 365 الخدمات التي لم يتم ذكرها بشكل صريح لدعم IPv6 المباشر، لتضمين خدمات مصادقة Azure Active Directory (AAD (دليل Azure النشط))، والتي تتطلب اتصال DNS64/NAT64 من عملاء وبيئات IPv6 فقط.  يتزامن هذا مع الهدف الموضح حاليا في وثائق NIST USGv6 الموجودة: تعد متطلبات إمكانية آلية الانتقال في المنشور الخاص [ل NIST 500-267A المراجعة 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 تقنيات مقبولة لاستخدامها.
> - دعم NAT64 للآلية الانتقالية NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Stateful NAT64: عنوان الشبكة وترجمة البروتوكول من عملاء IPv6 إلى خوادم IPv4
> - دعم DNS64 للآلية الانتقالية DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: ملحقات DNS لترجمة عنوان الشبكة من عملاء IPv6 إلى خادم IPv4

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>دعم IPv6 في Microsoft 365 الاشتراك

### <a name="exchange-online-and-ipv6"></a>Exchange Online و IPv6

إذا كان البرنامج الذي تستخدمه للاتصال Exchange Online يعتمد IPv6، سيستخدم IPv6 بشكل افتراضي على الشبكات السلكية واللاسلكية. إذا كنت تريد التحكم بالاتصالات Exchange Online، فاستخدم نطاقات عناوين IP [في Microsoft 365 URL ونطاقات عناوين IP](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online و IPv6

 **Microsoft 365 Government G1/G3/G4/K1** إذا كان البرنامج الذي تستخدمه للاتصال ب SharePoint Online يدعم IPv6، فإنه سيحاول استخدام IPv6 بشكل افتراضي.
  
 **سحابة عامة متعددة المستأجرين** تقوم Microsoft بتمكين SharePoint Online IPv6 بناء على طلبك. أنت بحاجة إلى توفير عناوين IP التي لم يتم توافها ل CIDR للبنية الأساسية ل DNS في مؤسستك. ضع في اعتبارك أنه لا يمكن مشاركة البنية الأساسية DNS هذه من قبل مؤسسات أخرى لتمكين IPv6 للمستأجر. بعد تمكين IPv6، إذا كان البرنامج الذي تستخدمه للاتصال ب SharePoint Online يدعم IPv6، فإنه يستخدم IPv6 بشكل افتراضي.
  
إذا كان البرنامج الذي تستخدمه للاتصال ب SharePoint Online يعتمد IPv6، سيستخدم IPv6 بشكل افتراضي على الشبكات السلكية واللاسلكية. إذا كنت تريد التحكم بالاتصالات SharePoint Online، فاستخدم نطاقات عناوين IP في نطاقات عناوين IP Microsoft 365 عناوين [URL وIP](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business و IPv6

يرجى العلم بأن IPv6 غير معتمد في Skype for Business ولا يمكن تمكينه بعد الآن.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams بوابة SIP و IPV6

Microsoft Teams التوجيه المباشر وبوابة SIP فقط IPv4. يدعم Microsoft Teams الخدمة والعميل كل من IPv4 و IPv6. إذا كنت تريد التحكم بالاتصالات Microsoft Teams، فاستخدم نطاقات عناوين IP في نطاقات عناوين IP Microsoft 365 عناوين [URL وIP](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection و IPv6

Exchange Online Protection (EOP) IPv6 إذا كان الإرسال يتم عبر بروتوكول أمان طبقة النقل. بالنسبة إلى نطاق EOP، استخدم Microsoft 365 [عناوين URL وIP](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>دعم IPv6 Microsoft 365 الحكومة

Microsoft 365 يتوافق دعم IPv6 ل العروض الحكومية مع مذكرة Office للإدارة والميزانية (OMB) الخاصة بكبير المسؤولين عن المعلومات في الأقسام التنفيذية والوكالات، بالإضافة إلى مذكرة اعتماد الحكومة الفيدرالية لبروتوكول الإنترنت الإصدار 6 (IPv6). [إن Microsoft 365 Microsoft ل Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) هي خدمة متعددة المستأجرين تخزن بيانات الحكومة الأمريكية في سحابة مجتمع منفصلة. مثل عروض Microsoft 365 الأخرى، يوفر خدمات الإنتاجية والتعاون، بما في ذلك Exchange Online و Skype for Business SharePoint عبر الإنترنت Microsoft 365 Apps for enterprise. 

تنطبق عروض Microsoft 365 Microsoft على 2013 واللاحقة فقط. لمزيد من المعلومات حول Microsoft 365 الحكومة، راجع الإعلان عن Microsoft 365 الحكومة[:](https://go.microsoft.com/fwlink/p/?LinkId=325414) سحابة القطاع الحكومي. قوانين التجارة الدولية في الأسلحة (ITAR) هي مجموعة من اللوائح الحكومية الأمريكية التي تتحكم في تصدير واستيراد المقالات والخدمات ذات الصلة بالدفاع في قائمة ذخائر الولايات المتحدة [(USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415) . 

توفر Microsoft 365 Microsoft للمؤسسات خدمات استضافة مخصصة لحلول إنتاجية Microsoft التي تدعم متطلبات الأمان والخصوصية والتوافق التنظيمي للوكالات الفيدرالية الأمريكية التي تتطلب مصادقة إدارة أمن المعلومات الفيدرالية (FISMA) والكيانات التجارية الخاضعة ل ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>الأمور التي يجب التفكير فيها عند استخدام IPv6 Microsoft 365

نوصي بعدم تعطيل IPv6. لمزيد من المعلومات، راجع [مقالة الإرشادات هذه](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). لتحديد إصدارات IP التي يتم استخدامها على شبكتك، فكر في ما يلي:
  
- إذا كان عرض الأمر **IPConfig** في موجه الأوامر يحتوي على صفوف تسمى "عنوان IPv6" أو "عنوان IPv6 مؤقت"، فإن IPv6 في بيئتك.

- إذا كانت كل عناوين IPv6 تبدأ ب "fe80" وتتوافق مع صفوف تسمى "عنوان IPv6 للارتباطات المحلية"، فليس لديك IPv6 في بيئتك.

قد تنطبق هذه الاعتبارات على شبكتك:
  
- لا تدعم خدمة الاشتراك العام الشراء بواسطة بطاقة الائتمان عبر IPv6. لا ينطبق هذا على سحابة القطاع الحكومي (سحابة القطاع الحكومي) لأن الحكومات تملك اتفاقية Enterprise (EA).

- لا يدعم IPv6 بعض سيناريوهات خدمات إدارة الحقوق (RMS).

- لا يدعم IPv6 BlackBerry® Enterprise Server (BES) لأن BlackBerry لا يدعم IPv6.

- إذا كنت تستخدم خدمات اتحاد Active Directory (AD FS) مع Microsoft 365، فإن الإعلان عن نقطة نهاية شبكة AD FS Microsoft 365 استخدام IPv6 غير معتمد. يجب ألا تقوم بتضمين سجلات AAAA في إدخال AD FS DNS عند استخدام Exchange Online. 

إليك ارتباط مختصر يمكنك استخدامه للعودة: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>راجع أيضًا

[خارطة طريق Learning IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[دليل بقاء IPv6](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
