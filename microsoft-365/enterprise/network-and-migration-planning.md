---
title: تخطيط الشبكة والترحيل Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: تحتوي هذه المقالة على ارتباطات إلى معلومات حول تخطيط الشبكة واختبارها وترحيلها إلى Office 365.
ms.openlocfilehash: 6288c9afae66206b7284f751f8a63381ab8451e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077450"
---
# <a name="network-and-migration-planning-for-office-365"></a>تخطيط الشبكة والترحيل Office 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

تحتوي هذه المقالة على ارتباطات إلى معلومات حول تخطيط الشبكة واختبارها والترحيل إلى Office 365.
  
قبل النشر للمرة الأولى أو الترحيل إلى Office 365، يمكنك استخدام المعلومات الموجودة في هذه المواضيع لتقدير النطاق الترددي الذي تحتاجه ثم لاختبار والتحقق من أن لديك ما يكفي من النطاق الترددي للنشر أو الترحيل إلى Office 365.

تشكل هذه المقالة جزءا من [تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md).

للحصول على خطوات لتحسين شبكتك Microsoft 365 وغيرها من الأنظمة الأساسية والخدمات السحابية من Microsoft، راجع ملصق [Microsoft Cloud Networking for Enterprise Architects](../solutions/cloud-architecture-models.md).
   
## <a name="estimate-network-bandwidth-requirements"></a>تقدير متطلبات النطاق الترددي للشبكة
<a name="EstimateBandwidthRequirements"> </a>

قد يؤدي استخدام Office 365 إلى زيادة استخدام دائرة الإنترنت الخاصة بمؤسستك. من المهم تحديد ما إذا كان مقدار النطاق الترددي المتوفر حاليا كافيا للتعامل مع الزيادة المقدرة بمجرد توزيع Office 365 بالكامل مع ترك سعة 20٪ على الأقل للتعامل مع ازدحام الأيام.
  
لتقدير النطاق الترددي، استخدم الخطوات التالية:
  
1. تقييم عدد العملاء الذين سيستخدمون كل خروج إنترنت. اسمح لشبكتنا متعددة التيرابت بمعالجة أكبر قدر ممكن من الاتصال. 
    
2. تحديد الخدمات والميزات Office 365 التي ستتوفر للعملاء لاستخدامها. من المحتمل أن يكون لديك مجموعات من الأشخاص الذين لديهم خدمات أو ملفات تعريف استخدام مختلفة.
    
3. قياس استخدام الشبكة لمجموعة تجريبية من العملاء. تأكد من أن عملاء الإصدار التجريبي هم ممثلون لملفات التعريف المختلفة للأشخاص في المؤسسة بالإضافة إلى المواقع الجغرافية المختلفة. يمكنك التحقق من نتائجك مقابل حاسباتنا القديمة [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) [Microsoft Teams](/microsoftteams/prepare-network) أو [دراسة الحالة](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) التي قمنا بها على شبكتنا الخاصة. 
    
4. استخدم القياسات من مجموعة الإصدار التجريبي لإقران احتياجات المؤسسة بأكملها وإعادة الاختبار للتحقق من صحة التقديرات قبل إجراء أي تغييرات على شبكتك.
    
## <a name="test-your-existing-network"></a>اختبار شبكتك الحالية
<a name="calculators"> </a>

 **أدوات الشبكة.** اختبار النطاق الترددي للإنترنت والتحقق من صحته لتحديد قيود التنزيل والتحميل وزمن الانتقال. ستساعدك هذه الأدوات على تحديد قدرات شبكتك للتهحيل وكذلك بعد نشرك بالكامل. 
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): يختبر الاتصال في بيئة Exchange Online الخاصة بك.
    
- استخدم [مساعد الإصلاح والدعم Microsoft Office 365](https://diagnostics.office.com/#/Download?env=SOC) لإصلاح مشاكل Outlook Office 365. 

- [Microsoft 365 أداة اختبار اتصال الشبكة](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool): اختبار اتصال الشبكة Microsoft 365.
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>أفضل الممارسات لتخطيط الشبكة وتحسين أداء الترحيل Office 365
<a name="BestPractices"> </a>

أتعمق قليلا في أفضل هذه الممارسات للحصول على مزيد من المعلومات حول تحسين تجربة Office 365.
  
1. هل تريد البدء في مساعدة المستخدمين على الفور؟ اطلع على [أفضل الممارسات لاستخدام Office 365 على شبكة بطيئة](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) للحصول على تلميحات حول استخدام Office 365، بما في ذلك SharePoint Online و Exchange Online وLync Online، عندما لا تعمل شبكتك فقط. ترتبط هذه المقالة بتحميلات المحتوى على TechNet Support.office.com لتحسين تجربة Office 365 وتتضمن معلومات حول الطرق السهلة لتخصيص صفحات الويب وكيفية تعيين إعدادات Internet Explorer للحصول على أفضل تجربة Office 365. 
    
2. اقرأ [Office 365 مبادئ اتصال الشبكة](./microsoft-365-network-connectivity-principles.md) لفهم مبادئ الاتصال لإدارة نسبة استخدام الشبكة Office 365 بأمان والحصول على أفضل أداء ممكن. ستساعدك هذه المقالة على فهم أحدث الإرشادات لتحسين اتصال الشبكة Office 365 بشكل آمن. 
    
3. يمكنك تحسين أداء ترحيل البريد من خلال إدارة جدول تحديثات Windows بعناية. يمكنك تحديث أجهزة الكمبيوتر العميلة على دفعات والتأكد من تحديث جميع أجهزة الكمبيوتر العميلة قبل الترحيل إلى Office 365 لتنظيم استخدام النطاق الترددي للشبكة. لمزيد من المعلومات، راجع [تحديث أسطح المكتب وتكوينها يدويا Office 365 للحصول على آخر التحديثات](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 نسبة استخدام الشبكة أفضل أداء عند معاملتها كخدمة إنترنت موثوق بها ويسمح لها بتجاوز الكثير من التصفية والمسح الضوئي التقليديين الذي تضعه بعض المؤسسات على نسبة استخدام الشبكة لخدمات الإنترنت غير الموثوق بها. يتضمن هذا عادة إزالة المعالجة الصادرة مثل مصادقة المستخدم الوكيل وفحص حزم البيانات، بالإضافة إلى ضمان الخروج المحلي إلى الإنترنت باستخدام ترجمة عنوان الشبكة المناسبة (NAT) وسعة النطاق الترددي الكافية للتعامل مع طلبات الشبكة المتزايدة. راجع [إدارة نقاط النهاية Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) للحصول على إرشادات إضافية حول تكوين الشبكة للتعامل مع Office 365 كخدمة إنترنت موثوق بها على شبكتك.
    
1. تأكد من [إدارة نقاط النهاية Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). تؤدي نسبة استخدام الشبكة الإضافية التي ستنتقل إلى Office 365 إلى زيادة اتصالات الوكيل الصادرة بالإضافة إلى زيادة في نسبة استخدام الشبكة الآمنة عبر TLS/SSL.
    
2. إذا تطلب وكلاءك الخارجيون مصادقة المستخدم، فقد تواجه اتصالا بطيئا أو فقدانا للوظائف. يمكن أن يؤدي تجاوز متطلبات المصادقة لمجالات Office 365 إلى تقليل هذا الحمل.
    
3. إذا كان لديك عدد كبير من التقويمات وعلب البريد المشتركة، فقد ترى زيادة في عدد الاتصالات من Outlook إلى Exchange. على سبيل المثال، قد يفتح عميل Outlook ما يصل إلى اتصالين إضافيين لكل تقويم مشترك قيد الاستخدام. في هذه الحالة، تأكد من أن وكيل الخروج يمكنه معالجة الاتصالات، أو تجاوز الوكيل للاتصالات Office 365 Outlook.
    
4. تحديد الحد الأقصى لعدد الأجهزة المدعومة لعنوان IP عام وكيفية موازنة التحميل عبر عناوين IP متعددة. لمزيد من المعلومات، راجع [دعم NAT مع Office 365](nat-support-with-microsoft-365.md).
    
5. إذا كنت تقوم بفحص الاتصالات الصادرة من أجهزة الكمبيوتر على الشبكة، فإن تجاوز هذه التصفية إلى مجالات Office 365 سيؤدي إلى تحسين الاتصال والأداء. بالإضافة إلى ذلك، غالبا ما يؤدي تجاوز الفحص الصادر إلى إزالة الحاجة إلى خروج إنترنت واحد وتمكين خروج الإنترنت المحلي لطلبات الشبكة الموجهة Office 365.
    
6. يجد بعض العملاء أن إعدادات الشبكة الداخلية قد تؤثر على الأداء. الإعدادات مثل الحد الأقصى لحجم وحدة الإرسال (MTU) والتفاوض التلقائي للشبكة أو الكشف التلقائي والمسارات دون المستوى الأمثل إلى الإنترنت هي الأماكن الشائعة التي يجب البحث عنها.
    
## <a name="network-planning-reference-for-office-365"></a>مرجع تخطيط الشبكة Office 365
<a name="NetReference"> </a>

تحتوي هذه المواضيع على معلومات مرجعية مفصلة Office 365 الشبكة.
  
- [إدارة نقاط نهاية Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [شبكات تسليم المحتوى](content-delivery-networks.md)
    
- [سجلات نظام أسماء المجالات الخارجية Office 365](external-domain-name-system-records.md)
    
- [دعم IPv6 في خدمات Office 365](ipv6-support.md)
    
- [مبادئ اتصال الشبكة Office 365](./microsoft-365-network-connectivity-principles.md)
    
- [التخطيط لأجهزة الشبكة التي تتصل بخدمات Office 365](plan-for-network-devices.md)
    
- [إرشادات الإعداد لخدمات Office 365](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على Microsoft 365 Enterprise](microsoft-365-overview.md)
