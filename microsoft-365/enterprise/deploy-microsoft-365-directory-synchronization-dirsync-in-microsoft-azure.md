---
title: نشر Microsoft 365 الدليل في Microsoft Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: تعرف على كيفية نشر Azure AD الاتصال على جهاز ظاهري في Azure لمزامنة الحسابات بين الدليل الخاص بك في الموقع ومستأجر Azure AD.
ms.openlocfilehash: 6535b46fb360cf326d8daf07662cb7fa366ae6c2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63576929"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>نشر Microsoft 365 الدليل في Microsoft Azure

Azure Active Directory (Azure AD) الاتصال (المعروف سابقا باسم أداة مزامنة الدليل أو أداة مزامنة الدليل أو أداة DirSync.exe) هو تطبيق تقوم بتثبيته على خادم انضم إلى مجال لمزامنة مستخدمي خدمات مجال Active Directory (AD DS) المحلي إلى مستأجر Azure AD لاشتراكك في Microsoft 365. Microsoft 365 Azure AD لخدمة الدليل الخاصة به. يتضمن Microsoft 365 الخاص بك مستأجر Azure AD. يمكن استخدام هذا المستأجر أيضا لإدارة هويات مؤسستك مع أحمال العمل السحابية الأخرى، بما في ذلك تطبيقات SaaS وتطبيقات أخرى في Azure.

يمكنك تثبيت Azure AD الاتصال على خادم في الموقع، ولكن يمكنك أيضا تثبيته على جهاز ظاهري في Azure للأسباب التالية:
  
- يمكنك توفير الخوادم المستندة إلى السحابة وتكوينها بشكل أسرع، مما يجعل الخدمات متوفرة للمستخدمين في وقت أقرب.
- يوفر Azure توفر موقع أفضل مع جهد أقل.
- يمكنك تقليل عدد الخوادم في مؤسستك.

يتطلب هذا الحل الاتصال بين شبكتك المحلية وشبكة Azure الظاهرية. لمزيد من المعلومات، راجع الاتصال شبكة المحلية [إلى شبكة Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> تصف هذه المقالة مزامنة مجال واحد في غابة واحدة. يتزامن Azure AD الاتصال مجالات AD DS في غابة Active Directory مع Microsoft 365. إذا كان لديك عدة غابات Active Directory لمزامنتها مع Microsoft 365، ف راجع مزامنة الدليل متعدد الغابات مع [سيناريو Sign-On واحد](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>نظرة عامة حول نشر Microsoft 365 الدليل في Azure

يعرض الرسم التخطيطي التالي Azure AD الاتصال يعمل على جهاز ظاهري في Azure (خادم مزامنة الدليل) الذي يتزامن مع غابة AD DS المحلية Microsoft 365 اشتراك.
  
![أداة Azure AD الاتصال على جهاز ظاهري في Azure لمزامنة الحسابات في الموقع مع مستأجر Azure AD لاشتراك Microsoft 365 مع تدفق حركة المرور.](../media/CP-DirSyncOverview.png)
  
في الرسم التخطيطي، هناك شبكتان متصلتان بشبكة VPN من موقع إلى موقع أو اتصال ExpressRoute. توجد شبكة المحلية حيث توجد وحدات تحكم مجال AD DS، وتوجد شبكة ظاهرية من Azure مع خادم مزامنة الدليل، وهو جهاز ظاهري يعمل ب [Azure AD الاتصال](https://www.microsoft.com/download/details.aspx?id=47594). هناك تدفقان رئيسيان لحركة المرور ينشأان من خادم مزامنة الدليل:
  
-  يعمل Azure AD الاتصال وحدة تحكم المجال على الشبكة المحلية للحصول على تغييرات على الحسابات وكلمات المرور.
-  يرسل Azure AD الاتصال التغييرات التي تم إدخالها على الحسابات وكلمات المرور إلى مثيل Azure AD لاشتراكك Microsoft 365. نظرا لأن خادم مزامنة الدليل في جزء موسع من الشبكة المحلية، يتم إرسال هذه التغييرات عبر الخادم الوكيل للشبكة المحلية.
    
> [!NOTE]
> يصف هذا الحل مزامنة مجال Active Directory واحد، في غابة Active Directory واحدة. يتزامن Azure AD الاتصال كل مجالات Active Directory في غابة Active Directory مع Microsoft 365. إذا كان لديك عدة غابات Active Directory لمزامنتها مع Microsoft 365، ف راجع مزامنة الدليل متعدد الغابات مع [سيناريو Sign-On واحد](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
هناك خطوتان رئيسيتان عند نشر هذا الحل:
  
1. أنشئ شبكة ظاهرية من Azure وأنشئ اتصال VPN من موقع إلى موقع بالشبكة المحلية. لمزيد من المعلومات، راجع الاتصال شبكة المحلية [إلى شبكة Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. ثبت [Azure AD الاتصال](https://www.microsoft.com/download/details.aspx?id=47594) على جهاز ظاهري انضم إلى مجال في Azure، ثم قم بمزامنة AD DS Microsoft 365. يشمل ذلك ما يلي:
    
    إنشاء جهاز ظاهري من Azure لتشغيل Azure AD الاتصال.
    
    تثبيت [Azure AD](https://www.microsoft.com/download/details.aspx?id=47594) الاتصال.
    
    يتطلب تكوين Azure AD الاتصال بيانات الاعتماد (اسم المستخدم وكلمة المرور) لحساب مسؤول Azure AD و حساب مسؤول مؤسسة AD DS. يتم تشغيل الاتصال Azure AD على الفور وعلى أساس مستمر لمزامنة غابة AD DS Microsoft 365.
    
قبل نشر هذا الحل في الإنتاج، يمكنك استخدام الإرشادات الموجودة في تكوين قاعدة [](simulated-ent-base-configuration-microsoft-365-enterprise.md) المؤسسة الذي تم محاكاته لإعداد هذا التكوين كدليل على المبدأ أو للبرهان التوضيحي أو للتجربة.
  
> [!IMPORTANT]
> عند اكتمال تكوين Azure AD الاتصال، فإنه لا يحفظ بيانات اعتماد حساب مسؤول المؤسسة ل AD DS. 
  
> [!NOTE]
> يصف هذا الحل مزامنة غابة AD DS واحدة Microsoft 365. تمثل طبولوجيا تمت مناقشتها في هذه المقالة طريقة واحدة فقط لتنفيذ هذا الحل. قد تختلف طبولوجيا مؤسستك استنادا إلى متطلبات الشبكة الفريدة والاعتبارات الأمنية. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>التخطيط لاستضافة خادم مزامنة الدليل Microsoft 365 Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>المتطلبات الأساسية

قبل البدء، راجع المتطلبات الأساسية التالية لهذا الحل:
  
- راجع محتوى التخطيط ذي الصلة في [تخطيط شبكة Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).
    
- تأكد من أنك تلبي كل [المتطلبات](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) الأساسية لتكوين شبكة Azure الظاهرية.
    
- لديك اشتراك Microsoft 365 يتضمن ميزة تكامل Active Directory. للحصول على معلومات Microsoft 365 الاشتراكات، انتقل إلى صفحة Microsoft 365 [الاشتراك](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- توفير جهاز Azure ظاهري واحد يقوم بتشغيل Azure AD الاتصال لمزامنة غابة AD DS في الموقع مع Microsoft 365.
    
    يجب أن تكون لديك بيانات الاعتماد (الأسماء وكلمات المرور) لحساب مسؤول مؤسسة AD DS حساب مسؤول Azure AD.
    
### <a name="solution-architecture-design-assumptions"></a>افتراضات تصميم هندسة الحلول

تصف القائمة التالية اختيارات التصميم التي تم اتخاذها لهذا الحل.
  
- يستخدم هذا الحل شبكة ظاهرية واحدة من Azure مع اتصال VPN من موقع إلى موقع. تستضيف شبكة Azure الظاهرية شبكة فرعية واحدة لها خادم واحد، وهو خادم مزامنة الدليل الذي يعمل ب Azure AD الاتصال. 
    
- على الشبكة المحلية، توجد وحدة تحكم مجال وخادمات DNS.
    
- يقوم Azure AD الاتصال بمزامنة كلمة المرور المفبركة بدلا من تسجيل الدخول مرة واحدة. لا تحتاج إلى نشر بنية أساسية لخدمات اتحاد Active Directory (AD FS). لمعرفة المزيد حول مزامنة كلمة المرور وخيارات تسجيل الدخول الفردي، راجع اختيار أسلوب المصادقة المناسب لحل الهوية المختلطة ل [Azure Active Directory](/azure/active-directory/hybrid/choose-ad-authn).
    
هناك خيارات تصميم إضافية قد تفكر فيها عند نشر هذا الحل في بيئتك. وتتضمن ما يلي:
  
- إذا كانت هناك خوادم DNS موجودة في شبكة Azure ظاهرية موجودة، فحدد ما إذا كنت تريد أن يستخدمها خادم مزامنة الدليل لحل الاسم بدلا من خوادم DNS على الشبكة المحلية.
    
- إذا كانت هناك وحدات تحكم بالمجال في شبكة Azure ظاهرية موجودة، فحدد ما إذا كان تكوين مواقع وخدمات Active Directory قد يكون خيارا أفضل بالنسبة لك. يمكن لخادم مزامنة الدليل الاستعلام عن وحدات التحكم بالمجال في شبكة Azure الظاهرية للحصول على التغييرات في الحسابات وكلمات المرور بدلا من وحدات التحكم بالمجال على الشبكة المحلية.
    
## <a name="deployment-roadmap"></a>خارطة طريق النشر

تتألف عملية نشر Azure AD الاتصال على جهاز ظاهري في Azure من ثلاث مراحل:
  
- المرحلة 1: إنشاء شبكة Azure الظاهرية وتكوينها
    
- المرحلة الثانية: إنشاء جهاز Azure الظاهري وتكوينه
    
- المرحلة 3: تثبيت Azure AD وتكوينه الاتصال
    
بعد النشر، يجب أيضا تعيين مواقع وتراخيص حسابات المستخدمين الجديدة في Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>المرحلة 1: إنشاء شبكة Azure الظاهرية وتكوينها

لإنشاء شبكة Azure الظاهرية وتكوينها، أكمل المرحلة [1:](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) إعداد الشبكة المحلية والمرحلة 2: إنشاء الشبكة الظاهرية المحلية في [Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) في خارطة طريق النشر ل الاتصال شبكة المحلية إلى شبكة [Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
هذا هو التكوين الناتج.
  
![تتم استضافة المرحلة الأولى من خادم مزامنة الدليل Microsoft 365 Azure.](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
يعرض هذا الرسم البياني شبكة موقعية متصلة بشبكة ظاهرية من Azure من خلال اتصال VPN من موقع إلى موقع أو ExpressRoute.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>المرحلة الثانية: إنشاء جهاز Azure الظاهري وتكوينه

قم بإنشاء الجهاز الظاهري في Azure باستخدام الإرشادات إنشاء أول جهاز [Windows في مدخل Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). استخدم الإعدادات التالية:
  
- في جزء **الأساسيات** ، حدد الاشتراك والموقع والمجموعة الموارد نفسها التي حددتها الشبكة الظاهرية. سجل اسم المستخدم وكلمة المرور في موقع آمن. ستحتاج إلى هذه لاحقا للاتصال بالآلة الظاهرية.
    
- في الجزء **اختيار حجم** ، اختر **الحجم القياسي A2** .
    
- في الجزء **الإعدادات**، في المقطع **تخزين**، حدد نوع **التخزين** القياسي. في المقطع **الشبكة** ، حدد اسم الشبكة الظاهرية الشبكة الفرعية لاستضافة خادم مزامنة الدليل (وليس GatewaySubnet). اترك كل الإعدادات الأخرى في قيمها الافتراضية.
    
تأكد من أن خادم مزامنة الدليل يستخدم DNS بشكل صحيح من خلال التحقق من DNS الداخلي للتأكد من إضافة سجل العنوان (أ) للجهاز الظاهري مع عنوان IP الخاص به. 
  
استخدم الإرشادات الموجودة [الاتصال إلى الجهاز](/azure/virtual-machines/windows/connect-logon) الظاهري، ثم سجل الدخول للاتصال بخادم مزامنة الدليل باستخدام اتصال سطح المكتب البعيد. بعد تسجيل الدخول، انضم إلى الجهاز الافتراضي إلى مجال AD DS في الموقع.
  
للحصول على الاتصال Azure AD للوصول إلى موارد الإنترنت، يجب تكوين خادم مزامنة الدليل لاستخدام الخادم الوكيل للشبكة المحلية. يجب الاتصال بمسؤول الشبكة للحصول على أي خطوات تكوين إضافية لتنفيذها.
  
هذا هو التكوين الناتج.
  
![تتم استضافة المرحلة 2 من خادم مزامنة الدليل Microsoft 365 Azure.](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
يعرض هذا الرسم البياني الجهاز الافتراضي لمزامنة الدليل في شبكة Azure الظاهرية المحلية.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>المرحلة 3: تثبيت Azure AD وتكوينه الاتصال

أكمل الإجراء التالي:
  
1. الاتصال إلى خادم مزامنة الدليل باستخدام اتصال سطح المكتب البعيد مع حساب مجال AD DS الذي لديه امتيازات المسؤول المحلي. راجع [الاتصال إلى الجهاز الظاهري ثم تسجيل الدخول](/azure/virtual-machines/windows/connect-logon).
    
2. من خادم مزامنة الدليل، افتح المقالة إعداد مزامنة [](set-up-directory-synchronization.md) الدليل Microsoft 365 واتبع توجيهات مزامنة الدليل مع مزامنة كلمة المرور.
    
> [!CAUTION]
> ينشئ **الإعداد AAD_xxxxxxxxxxxx في** الوحدة التنظيمية للمستخدمين المحليين (OU). لا نقل هذا الحساب أو المزامنة أو إزالتها ستفشل.
  
هذا هو التكوين الناتج.
  
![تتم استضافة المرحلة 3 من خادم مزامنة الدليل Microsoft 365 Azure.](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
يعرض هذا الرسم البياني خادم مزامنة الدليل مع Azure AD الاتصال شبكة Azure الظاهرية المحلية.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>تعيين المواقع والتراخيص للمستخدمين في Microsoft 365

يضيف Azure AD الاتصال حسابات إلى اشتراك Microsoft 365 من AD DS المحلية، ولكن لكي يقوم المستخدمون تسجيل الدخول إلى Microsoft 365 واستخدام خدماته، يجب تكوين الحسابات بموقع وتراخيص. استخدم هذه الخطوات لإضافة الموقع وتنشيط التراخيص الخاصة وحسابات المستخدمين المناسبة:
  
1. سجل [الدخول إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com)، ثم انقر فوق **المسؤول**.
    
2. في التنقل الأيسر، انقر فوق <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive**</a> >  users.
3. في قائمة حسابات المستخدمين، حدد خانة الاختيار إلى جانب المستخدم الذي تريد تنشيطه.
    
4. على صفحة المستخدم، انقر فوق **تحرير** **لتراخيص المنتج**.
    
5. في صفحة **تراخيص** المنتجات، حدد موقع **المستخدم للموقع،** ثم قم بتمكين التراخيص المناسبة للمستخدم.
    
6. عند الانتهاء، انقر فوق **حفظ**، ثم انقر فوق **إغلاق** مرتين.
    
7. ارجع إلى الخطوة 3 لمستخدمين إضافيين.
    
## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 حل وهندسة](../solutions/index.yml)
  
[الاتصال شبكة المحلية إلى شبكة Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[تنزيل Azure AD الاتصال](https://www.microsoft.com/download/details.aspx?id=47594)
  
[إعداد مزامنة الدليل Microsoft 365](set-up-directory-synchronization.md)
