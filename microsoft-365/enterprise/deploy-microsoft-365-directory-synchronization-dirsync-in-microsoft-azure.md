---
title: نشر مزامنة دليل Microsoft 365 في Microsoft Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تعرف على كيفية نشر azure AD الاتصال على جهاز ظاهري في Azure لمزامنة الحسابات بين الدليل المحلي ومستأجر Azure AD.
ms.openlocfilehash: 077fe85307b5c64c5ece9d710a3ad171d04a21da
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092150"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>نشر مزامنة دليل Microsoft 365 في Microsoft Azure

الاتصال Azure Active Directory (Azure AD) (المعروف سابقا باسم أداة مزامنة الدليل أو أداة مزامنة الدليل أو أداة DirSync.exe) هو تطبيق تقوم بتثبيته على خادم منضم إلى المجال لمزامنة مستخدمي خدمات المجال Active Directory محلي (AD DS) مع مستأجر Azure AD لاشتراكك في Microsoft 365. يستخدم Microsoft 365 Azure AD لخدمة الدليل الخاصة به. يتضمن اشتراكك في Microsoft 365 مستأجر Azure AD. يمكن أيضا استخدام هذا المستأجر لإدارة هويات مؤسستك مع أحمال العمل السحابية الأخرى، بما في ذلك تطبيقات وتطبيقات SaaS الأخرى في Azure.

يمكنك تثبيت الاتصال Azure AD على خادم محلي، ولكن يمكنك أيضا تثبيته على جهاز ظاهري في Azure لهذه الأسباب:
  
- يمكنك توفير وتكوين الخوادم المستندة إلى السحابة بشكل أسرع، مما يجعل الخدمات متاحة للمستخدمين في وقت أقرب.
- يوفر Azure توفرا أفضل للموقع مع جهد أقل.
- يمكنك تقليل عدد الخوادم المحلية في مؤسستك.

يتطلب هذا الحل الاتصال بين شبكتك المحلية وشبكة Azure الظاهرية. لمزيد من المعلومات، راجع [الاتصال شبكة محلية إلى شبكة Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> تصف هذه المقالة مزامنة مجال واحد في غابة واحدة. يقوم Azure AD الاتصال بمزامنة جميع مجالات AD DS في غابة Active Directory مع Microsoft 365. إذا كان لديك العديد من غابات Active Directory للمزامنة مع Microsoft 365، فراجع ["مزامنة الدليل متعدد الغابات" مع "سيناريو Sign-On مفرد](/azure/active-directory/hybrid/whatis-hybrid-identity)". 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>نظرة عامة حول نشر مزامنة الدليل Microsoft 365 في Azure

يوضح الرسم التخطيطي التالي الاتصال Azure AD قيد التشغيل على جهاز ظاهري في Azure (خادم مزامنة الدليل) الذي يقوم بمزامنة غابة AD DS المحلية إلى اشتراك Microsoft 365.
  
![أداة الاتصال Azure AD على جهاز ظاهري في Azure تقوم بمزامنة الحسابات المحلية مع مستأجر Azure AD لاشتراك Microsoft 365 مع تدفق نسبة استخدام الشبكة.](../media/CP-DirSyncOverview.png)
  
في الرسم التخطيطي، هناك شبكتان متصلتان بواسطة VPN من موقع إلى موقع أو اتصال ExpressRoute. هناك شبكة محلية حيث توجد وحدات تحكم مجال AD DS، وهناك شبكة Azure ظاهرية مع خادم مزامنة الدليل، وهو جهاز ظاهري يقوم بتشغيل [Azure AD الاتصال](https://www.microsoft.com/download/details.aspx?id=47594). هناك تدفقان رئيسيان لنسبة استخدام الشبكة تنشأان من خادم مزامنة الدليل:
  
-  يستعلم Azure AD الاتصال عن وحدة تحكم بالمجال على الشبكة المحلية لإجراء تغييرات على الحسابات وكلمات المرور.
-  يرسل azure AD الاتصال التغييرات إلى الحسابات وكلمات المرور إلى مثيل Azure AD لاشتراكك في Microsoft 365. نظرا لأن خادم مزامنة الدليل موجود في جزء موسع من الشبكة المحلية، يتم إرسال هذه التغييرات من خلال الخادم الوكيل للشبكة المحلية.
    
> [!NOTE]
> يصف هذا الحل مزامنة مجال Active Directory واحد، في غابة Active Directory واحدة. يقوم Azure AD الاتصال بمزامنة جميع مجالات Active Directory في غابة Active Directory مع Microsoft 365. إذا كان لديك العديد من غابات Active Directory للمزامنة مع Microsoft 365، فراجع ["مزامنة الدليل متعدد الغابات" مع "سيناريو Sign-On مفرد](/azure/active-directory/hybrid/whatis-hybrid-identity)". 
  
هناك خطوتان رئيسيتان عند نشر هذا الحل:
  
1. إنشاء شبكة Azure ظاهرية وإنشاء اتصال VPN من موقع إلى موقع بشبكتك المحلية. لمزيد من المعلومات، راجع [الاتصال شبكة محلية إلى شبكة Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. قم بتثبيت [الاتصال Azure AD](https://www.microsoft.com/download/details.aspx?id=47594) على جهاز ظاهري منضم إلى المجال في Azure، ثم قم بمزامنة AD DS المحلي مع Microsoft 365. ويشمل ذلك ما يلي:
    
    إنشاء جهاز ظاهري من Azure لتشغيل الاتصال Azure AD.
    
    تثبيت وتكوين [الاتصال Azure AD](https://www.microsoft.com/download/details.aspx?id=47594).
    
    يتطلب تكوين Azure AD الاتصال بيانات الاعتماد (اسم المستخدم وكلمة المرور) لحساب مسؤول Azure AD وحساب مسؤول مؤسسة AD DS. تعمل الاتصال Azure AD على الفور وعلى أساس مستمر لمزامنة غابة AD DS المحلية مع Microsoft 365.
    
قبل نشر هذا الحل في الإنتاج، يمكنك استخدام الإرشادات في [التكوين الأساسي لمحاكاة المؤسسة](simulated-ent-base-configuration-microsoft-365-enterprise.md) لإعداد هذا التكوين كدليل على المفهوم، أو للنماذج التوضيحية، أو للتجريب.
  
> [!IMPORTANT]
> عند اكتمال تكوين الاتصال Azure AD، فإنه لا يحفظ بيانات اعتماد حساب مسؤول مؤسسة AD DS. 
  
> [!NOTE]
> يصف هذا الحل مزامنة غابة AD DS واحدة إلى Microsoft 365. يمثل المخطط الذي تمت مناقشته في هذه المقالة طريقة واحدة فقط لتنفيذ هذا الحل. قد يختلف تخطيط مؤسستك بناء على متطلبات الشبكة الفريدة واعتبارات الأمان. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>التخطيط لاستضافة خادم مزامنة الدليل Microsoft 365 في Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>المتطلبات الأساسية

قبل البدء، راجع المتطلبات الأساسية التالية لهذا الحل:
  
- راجع محتوى التخطيط ذي الصلة في [تخطيط شبكة Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).
    
- تأكد من تلبية جميع [المتطلبات الأساسية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) لتكوين شبكة Azure الظاهرية.
    
- لديك اشتراك Microsoft 365 يتضمن ميزة تكامل Active Directory. للحصول على معلومات حول اشتراكات Microsoft 365، انتقل إلى [صفحة الاشتراك Microsoft 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- قم بتوفير جهاز Azure ظاهري واحد يقوم بتشغيل الاتصال Azure AD لمزامنة غابة AD DS المحلية مع Microsoft 365.
    
    يجب أن يكون لديك بيانات الاعتماد (الأسماء وكلمات المرور) لحساب مسؤول مؤسسة AD DS وحساب مسؤول Azure AD.
    
### <a name="solution-architecture-design-assumptions"></a>افتراضات تصميم بنية الحل

تصف القائمة التالية خيارات التصميم التي تم إجراؤها لهذا الحل.
  
- يستخدم هذا الحل شبكة Azure ظاهرية واحدة مع اتصال VPN من موقع إلى موقع. تستضيف شبكة Azure الظاهرية شبكة فرعية واحدة تحتوي على خادم واحد، وهو خادم مزامنة الدليل الذي يقوم بتشغيل Azure AD الاتصال. 
    
- على الشبكة المحلية، توجد وحدة تحكم بالمجال وخوادم DNS.
    
- يقوم Azure AD الاتصال بإجراء مزامنة تجزئة كلمة المرور بدلا من تسجيل الدخول الأحادي. ليس عليك نشر بنية أساسية خدمات الأمان المشترك لـ Active Directory (AD FS). لمعرفة المزيد حول مزامنة تجزئة كلمة المرور وخيارات تسجيل الدخول الأحادي، راجع [اختيار أسلوب المصادقة الصحيح لحل الهوية المختلطة ل Azure Active Directory](/azure/active-directory/hybrid/choose-ad-authn).
    
هناك خيارات تصميم إضافية قد تفكر فيها عند نشر هذا الحل في بيئتك. وتتضمن ما يلي:
  
- إذا كانت هناك خوادم DNS موجودة في شبكة Azure ظاهرية موجودة، فحدد ما إذا كنت تريد أن يستخدمها خادم مزامنة الدليل لتحليل الاسم بدلا من خوادم DNS على الشبكة المحلية.
    
- إذا كانت هناك وحدات تحكم بالمجال في شبكة Azure ظاهرية موجودة، فحدد ما إذا كان تكوين مواقع وخدمات Active Directory خيارا أفضل لك. يمكن لخادم مزامنة الدليل الاستعلام عن وحدات التحكم بالمجال في شبكة Azure الظاهرية للتغييرات في الحسابات وكلمات المرور بدلا من وحدات التحكم بالمجال على الشبكة المحلية.
    
## <a name="deployment-roadmap"></a>مخطط التوزيع

يتكون نشر الاتصال Azure AD على جهاز ظاهري في Azure من ثلاث مراحل:
  
- المرحلة 1: إنشاء وتكوين شبكة Azure الظاهرية
    
- المرحلة 2: إنشاء جهاز Azure الظاهري وتكوينه
    
- المرحلة 3: تثبيت وتكوين الاتصال Azure AD
    
بعد التوزيع، يجب أيضا تعيين مواقع وتراخيص لحسابات المستخدمين الجديدة في Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>المرحلة 1: إنشاء وتكوين شبكة Azure الظاهرية

لإنشاء وتكوين شبكة Azure الظاهرية، أكمل [المرحلة 1: إعداد الشبكة المحلية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) [والمرحلة 2: إنشاء الشبكة الظاهرية الداخلية في Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) في مخطط توزيع [الاتصال شبكة محلية إلى شبكة Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
هذا هو التكوين الناتج.
  
![المرحلة 1 من خادم مزامنة الدليل Microsoft 365 المستضافة في Azure.](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
يوضح هذا الشكل شبكة اتصال محلية متصلة بشبكة Azure ظاهرية من خلال اتصال VPN من موقع إلى موقع أو ExpressRoute.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>المرحلة 2: إنشاء جهاز Azure الظاهري وتكوينه

إنشاء الجهاز الظاهري في Azure باستخدام الإرشادات [إنشاء أول جهاز ظاهري Windows في مدخل Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098). استخدم الإعدادات التالية:
  
- في جزء **Basics** ، حدد نفس الاشتراك والموقع ومجموعة الموارد مثل الشبكة الظاهرية الخاصة بك. تسجيل اسم المستخدم وكلمة المرور في موقع آمن. ستحتاج إليها لاحقا للاتصال بالجهاز الظاهري.
    
- في الجزء **"اختيار حجم** "، اختر الحجم **القياسي A2** .
    
- في جزء **الإعدادات**، في قسم **التخزين**، حدد نوع التخزين **القياسي**. في قسم **الشبكة** ، حدد اسم الشبكة الظاهرية والشبكة الفرعية لاستضافة خادم مزامنة الدليل (وليس GatewaySubnet). اترك كافة الإعدادات الأخرى عند قيمها الافتراضية.
    
تحقق من أن خادم مزامنة الدليل يستخدم DNS بشكل صحيح عن طريق التحقق من DNS الداخلي للتأكد من إضافة سجل العنوان (A) للجهاز الظاهري مع عنوان IP الخاص به. 
  
استخدم الإرشادات الموجودة في [الاتصال إلى الجهاز الظاهري وسجل الدخول](/azure/virtual-machines/windows/connect-logon) للاتصال بخادم مزامنة الدليل باستخدام اتصال سطح المكتب البعيد. بعد تسجيل الدخول، انضم إلى الجهاز الظاهري إلى مجال AD DS المحلي.
  
لكي يتمكن Azure AD الاتصال من الوصول إلى موارد الإنترنت، يجب تكوين خادم مزامنة الدليل لاستخدام الخادم الوكيل للشبكة المحلية. يجب عليك الاتصال بمسؤول الشبكة للحصول على أي خطوات تكوين إضافية لتنفيذها.
  
هذا هو التكوين الناتج.
  
![المرحلة 2 من خادم مزامنة الدليل Microsoft 365 المستضافة في Azure.](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
يوضح هذا الشكل الجهاز الظاهري لخادم مزامنة الدليل في شبكة Azure الظاهرية الداخلية.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>المرحلة 3: تثبيت وتكوين الاتصال Azure AD

أكمل الإجراء التالي:
  
1. الاتصال إلى خادم مزامنة الدليل باستخدام اتصال سطح المكتب البعيد مع حساب مجال AD DS الذي يحتوي على امتيازات المسؤول المحلي. راجع [الاتصال إلى الجهاز الظاهري وتسجيل الدخول](/azure/virtual-machines/windows/connect-logon).
    
2. من خادم مزامنة الدليل، افتح [إعداد مزامنة الدليل لمقالة Microsoft 365](set-up-directory-synchronization.md) واتبع توجيهات مزامنة الدليل مع مزامنة تجزئة كلمة المرور.
    
> [!CAUTION]
> ينشئ برنامج الإعداد حساب **AAD_xxxxxxxxxxxx** في الوحدة التنظيمية للمستخدمين المحليين (OU). لا تقم بنقل هذا الحساب أو إزالته أو ستفشل المزامنة.
  
هذا هو التكوين الناتج.
  
![المرحلة 3 من خادم مزامنة الدليل Microsoft 365 المستضافة في Azure.](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
يوضح هذا الشكل خادم مزامنة الدليل مع الاتصال Azure AD في شبكة Azure الظاهرية الداخلية.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>تعيين مواقع وتراخيص للمستخدمين في Microsoft 365

يضيف Azure AD الاتصال حسابات إلى اشتراكك في Microsoft 365 من AD DS المحلي، ولكن لكي يقوم المستخدمون بتسجيل الدخول إلى Microsoft 365 واستخدام خدماته، يجب تكوين الحسابات بموقع وتراخيص. استخدم هذه الخطوات لإضافة الموقع وتنشيط التراخيص لحسابات المستخدمين المناسبة:
  
1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com)، ثم انقر فوق **"المسؤول**".
    
2. في جزء التنقل الأيمن، انقر فوق <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive**</a> >  users.
3. في قائمة حسابات المستخدمين، حدد خانة الاختيار إلى جانب المستخدم الذي تريد تنشيطه.
    
4. في الصفحة الخاصة بالمستخدم، انقر فوق **"تحرير تراخيص** **المنتج**".
    
5. في صفحة **تراخيص المنتج** ، حدد موقعا **للمستخدم للموقع،** ثم قم بتمكين التراخيص المناسبة للمستخدم.
    
6. عند الاكتمال، انقر فوق **"حفظ"**، ثم انقر فوق **"إغلاق"** مرتين.
    
7. ارجع إلى الخطوة 3 للمستخدمين الإضافيين.
    
## <a name="see-also"></a>راجع أيضًا

[مركز الحلول والهندسة من Microsoft 365](../solutions/index.yml)
  
[الاتصال شبكة محلية إلى شبكة Microsoft Azure الظاهرية](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[تنزيل الاتصال Azure AD](https://www.microsoft.com/download/details.aspx?id=47594)
  
[إعداد مزامنة الدليل Microsoft 365](set-up-directory-synchronization.md)
