---
title: نشر المصادقة المتحدة عالية التوفر Microsoft 365 Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'ملخص: تكوين المصادقة المتحدة عالية التوفر لاشتراكك Microsoft 365 Microsoft Azure.'
ms.openlocfilehash: 70d597663a1920706dbab164dda05b7142f7fd04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572856"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>نشر المصادقة المتحدة عالية التوفر Microsoft 365 Azure

وتتضمن هذه المقالة ارتباطات إلى الإرشادات خطوة بخطوة لنشر المصادقة المتحدة عالية التوفر ل Microsoft Microsoft 365 في خدمات البنية الأساسية Azure مع هذه الأجهزة الظاهرية:
  
- خادمان وكيلان لتطبيق ويب
    
- خادما خدمات اتحاد Active Directory (AD FS)
    
- اثنين من وحدات تحكم المجال المتماثلة
    
- خادم مزامنة دليل واحد يعمل ب Azure AD الاتصال
    
إليك التكوين، مع أسماء العنصر النائب لكل خادم.
  
**مصادقة أكثر توفرا للمصادقة الخارجية Microsoft 365 الأساسية في Azure**

![التكوين النهائي للتوفر العالي Microsoft 365 المصادقة الخارجية في Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
توجد كل الأجهزة الظاهرية في شبكة Azure ظاهرية واحدة (VNet). 
  
> [!NOTE]
> لا تعتمد المصادقة الخارجية للمستخدمين الفرديين على أي موارد المحلية. ومع ذلك، إذا لم يكن الاتصال المحلي متوفرا، لن تتلقى وحدات التحكم بالمجال في VNet تحديثات حسابات المستخدمين والمجموعات التي تم إدخالها في خدمات مجال Active Directory المحلية (AD DS). للتأكد من عدم حدوث ذلك، يمكنك تكوين توفر عال للاتصال داخل الموقع. لمزيد من المعلومات، راجع الاتصالية عبر الموقع و [VNet-to-VNet المتوفرة بشكل كبير](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
يوجد كل زوج من الأجهزة الظاهرية لدور معين في الشبكة الفرعية الخاصة به وفي مجموعة التوفر الخاصة به.
  
> [!NOTE]
> نظرا لأن VNet هذا متصل بالشبكة المحلية، لا يتضمن هذا التكوين jumpbox أو مراقبة الأجهزة الظاهرية على شبكة فرعية للإدارة. لمزيد من المعلومات، راجع [تشغيل Windows VMs لهندسة من المستوى N](/azure/guidance/guidance-compute-n-tier-vm). 
  
نتيجة هذا التكوين هي أنه سيكون لديك مصادقة متكاتف لجميع مستخدمي Microsoft 365، حيث يمكنهم استخدام بيانات اعتماد AD DS الخاصة بهم لتسجيل الدخول بدلا من حساب Microsoft 365 الخاص بهم. تستخدم البنية الأساسية للمصادقة الخارجية مجموعة زائدة من الخوادم التي يتم نشرها بسهولة أكبر في خدمات البنية الأساسية ل Azure، بدلا من نشرها في شبكة Edge المحلية.
  
## <a name="bill-of-materials"></a>فاتورة المواد

يتطلب تكوين الأساس هذا المجموعة التالية من خدمات Azure ومكوناتها:
  
- سبعة أجهزة ظاهرية
    
- شبكة ظاهرية واحدة عبر الموقع مع أربع شبكات فرعية
    
- أربع مجموعات موارد
    
- ثلاث مجموعات توفر
    
- اشتراك Azure واحد
    
فيما يلي الأجهزة الظاهرية والأحجام الافتراضية لهذا التكوين.
  
|**عنصر**|**وصف الجهاز الظاهري**|**صورة معرض Azure**|**الحجم الافتراضي**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |وحدة تحكم المجال الأولى  <br/> |Windows Datacenter ل Server 2016  <br/> |D2  <br/> |
|2.  <br/> |وحدة تحكم المجال الثاني  <br/> |Windows Datacenter ل Server 2016  <br/> |D2  <br/> |
|3.  <br/> |خادم Azure AD الاتصال Azure  <br/> |Windows Datacenter ل Server 2016  <br/> |D2  <br/> |
|4.  <br/> |خادم AD FS الأول  <br/> |Windows Datacenter ل Server 2016  <br/> |D2  <br/> |
|5.  <br/> |خادم AD FS الثاني  <br/> |Windows Datacenter ل Server 2016  <br/> |D2  <br/> |
|6.  <br/> |خادم وكيل تطبيق ويب الأول  <br/> |Windows Datacenter ل Server 2016  <br/> |D2  <br/> |
|7.  <br/> |الخادم الوكيل الثاني لتطبيق ويب  <br/> |Windows Datacenter ل Server 2016  <br/> |D2  <br/> |
   
لحساب التكاليف المقدرة لهذا التكوين، راجع حاسبة [أسعار Azure](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>مراحل النشر

يمكنك نشر حمل العمل هذا في المراحل التالية:
  
- [المرحلة 1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md). إنشاء مجموعات الموارد وحسابات التخزين ومجموعات التوفر وشبكة ظاهرية متعددة الأماكن.
    
- [المرحلة 2: تكوين وحدات التحكم بالمجال](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). إنشاء وحدات تحكم مجال AD DS المتماثلة وخادم مزامنة الدليل وتكوينها.
    
- [المرحلة 3: تكوين خوادم AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). إنشاء خادمي AD FS وتكوينهم.
    
- [المرحلة 4: تكوين محترفي تطبيقات الويب](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). إنشاء الخادمين الوكيلين لتطبيق ويب وتكوينهم.
    
- [المرحلة 5: تكوين المصادقة الخارجية Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). تكوين المصادقة الخارجية لاشتراكك في Microsoft 365.
    
توفر هذه المقالات دليلا وصفيا ومرحليا لهنية محددة مسبقا لإنشاء مصادقة وظيفية ومتوفرة بشكل كامل Microsoft 365 في خدمات البنية الأساسية في Azure. ضع ما يلي في الاعتبار:
  
- إذا كنت من ذوي الخبرة في تطبيق AD FS، لا تتردد في تكييف الإرشادات في المرحلتين 3 و4 وبناء مجموعة الخوادم الأكثر ملاءمة لاحتياجاتك.
    
- إذا كان لديك بالفعل نشر سحابي مختلط من Azure مع شبكة ظاهرية موجودة عبر المواقع المحلية، لا تتردد في تكييف الإرشادات أو تخطيها في المرحلتين 1 و2 وضع خادمي وكيل AD FS وتطبيق ويب على الشبكات الفرعية المناسبة.
    
لإنشاء بيئة تطوير/اختبار أو إثبات المبدأ لهذا التكوين، راجع الهوية المتحدة لبيئة Microsoft 365 تطوير[/اختبار.](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
## <a name="next-step"></a>الخطوة التالية

ابدأ تكوين حمل العمل هذا [بالمرحلة 1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
