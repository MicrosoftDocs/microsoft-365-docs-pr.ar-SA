---
title: نشر مصادقة موحدة عالية التوفر Microsoft 365 في Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'ملخص: تكوين مصادقة موحدة عالية التوفر لاشتراكك في Microsoft 365 في Microsoft Azure.'
ms.openlocfilehash: 64fc02e6ecaa400da6d6130cb9ae630279102fcc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093405"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>نشر مصادقة موحدة عالية التوفر Microsoft 365 في Azure

تحتوي هذه المقالة على ارتباطات إلى الإرشادات المفصلة خطوة بخطوة لنشر المصادقة الموحدة عالية التوفر ل Microsoft Microsoft 365 في خدمات البنية الأساسية ل Azure مع هذه الأجهزة الظاهرية:
  
- خادمان وكيلان لتطبيق ويب
    
- خادمان خدمات الأمان المشترك لـ Active Directory (AD FS)
    
- وحدتا تحكم بالمجال للنسخة المتماثلة
    
- خادم مزامنة دليل واحد يقوم بتشغيل Azure AD الاتصال
    
فيما يلي التكوين، مع أسماء العناصر النائبة لكل خادم.
  
**مصادقة موحدة عالية التوفر للبنية الأساسية Microsoft 365 في Azure**

![التكوين النهائي للتوفر العالي Microsoft 365 البنية الأساسية للمصادقة الموحدة في Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
جميع الأجهزة الظاهرية موجودة في شبكة Azure ظاهرية واحدة داخلية (VNet). 
  
> [!NOTE]
> لا تعتمد المصادقة الموحدة للمستخدمين الفرديين على أي موارد محلية. ومع ذلك، إذا أصبح الاتصال الداخلي غير متوفر، فلن تتلقى وحدات التحكم بالمجال في VNet تحديثات لحسابات المستخدمين والمجموعات التي تم إجراؤها في خدمات المجال Active Directory محلي (AD DS). للتأكد من عدم حدوث ذلك، يمكنك تكوين قابلية وصول عالية للاتصال الداخلي. لمزيد من المعلومات، راجع [الاتصال عبر الأماكن و VNet-to-VNet عالي التوفر](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
كل زوج من الأجهزة الظاهرية لدور معين موجود في شبكته الفرعية ومجموعة التوفر الخاصة به.
  
> [!NOTE]
> لأن هذه الشبكة الظاهرية متصلة بالشبكة المحلية، لا يتضمن هذا التكوين jumpbox أو مراقبة الأجهزة الظاهرية على شبكة فرعية للإدارة. لمزيد من المعلومات، راجع [تشغيل الأجهزة الظاهرية Windows للبنية متعددة المستويات](/azure/guidance/guidance-compute-n-tier-vm). 
  
نتيجة هذا التكوين هي أنه سيكون لديك مصادقة موحدة لجميع مستخدمي Microsoft 365، حيث يمكنهم استخدام بيانات اعتماد AD DS لتسجيل الدخول بدلا من حساب Microsoft 365 الخاص بهم. تستخدم البنية الأساسية للمصادقة الموحدة مجموعة متكررة من الخوادم التي يتم نشرها بسهولة أكبر في خدمات البنية الأساسية ل Azure، بدلا من شبكة الحافة المحلية.
  
## <a name="bill-of-materials"></a>فاتورة المواد

يتطلب تكوين الأساس هذا المجموعة التالية من خدمات ومكونات Azure:
  
- سبعة أجهزة ظاهرية
    
- شبكة ظاهرية واحدة عبر أماكن العمل مع أربع شبكات فرعية
    
- أربع مجموعات موارد
    
- ثلاث مجموعات توفر
    
- اشتراك Azure واحد
    
فيما يلي الأجهزة الظاهرية وأحجامها الافتراضية لهذا التكوين.
  
|**البند**|**وصف الجهاز الظاهري**|**صورة معرض Azure**|**الحجم الافتراضي**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |وحدة التحكم بالمجال الأول  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |وحدة التحكم بالمجال الثانية  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |خادم الاتصال Azure AD  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |خادم AD FS الأول  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |خادم AD FS الثاني  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |خادم وكيل تطبيق الويب الأول  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |خادم وكيل تطبيق الويب الثاني  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
لحساب التكاليف المقدرة لهذا التكوين، راجع [حاسبة أسعار Azure](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>مراحل النشر

يمكنك نشر حمل العمل هذا في المراحل التالية:
  
- [المرحلة 1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md). إنشاء مجموعات الموارد وحسابات التخزين ومجموعات التوفر وشبكة ظاهرية مشتركة.
    
- [المرحلة 2: تكوين وحدات التحكم بالمجال](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). إنشاء وتكوين وحدات تحكم مجال AD DS للنسخة المتماثلة وخادم مزامنة الدليل.
    
- [المرحلة 3: تكوين خوادم AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). إنشاء وتكوين خادمي AD FS.
    
- [المرحلة 4: تكوين وكلاء تطبيق الويب](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). إنشاء وتكوين خادمي وكيل تطبيق الويب.
    
- [المرحلة 5: تكوين المصادقة الموحدة Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). تكوين المصادقة الموحدة لاشتراكك في Microsoft 365.
    
توفر هذه المقالات دليلا توجيهيا ومرحليا لبنية معرفة مسبقا لإنشاء مصادقة موحدة وظيفية وعالية التوفر Microsoft 365 في خدمات البنية الأساسية ل Azure. ضع ما يلي في الاعتبار:
  
- إذا كنت منفذ AD FS من ذوي الخبرة، لا تتردد في تكييف الإرشادات في المراحل 3 و4 وإنشاء مجموعة من الخوادم التي تناسب احتياجاتك بشكل أفضل.
    
- إذا كان لديك بالفعل نشر سحابة مختلطة في Azure مع شبكة ظاهرية موجودة عبر أماكن العمل، لا تتردد في تكييف الإرشادات أو تخطيها في المرحلتين 1 و2 ووضع AD FS وخوادم وكيل تطبيق الويب على الشبكات الفرعية المناسبة.
    
لبناء بيئة تطوير/اختبار أو إثبات صحة هذا التكوين، راجع [الهوية الموحدة لبيئة التطوير/الاختبار Microsoft 365 الخاصة بك](federated-identity-for-your-microsoft-365-dev-test-environment.md).
  
## <a name="next-step"></a>الخطوة التالية

ابدأ تكوين حمل العمل هذا مع [المرحلة 1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
