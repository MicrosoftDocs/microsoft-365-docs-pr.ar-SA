---
title: زيادة Microsoft 365 أمان Microsoft 365 بيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
- admindeeplinkSPO
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: استخدم دليل Test Lab هذا لتمكين إعدادات Microsoft 365 أمان Microsoft 365 بيئة اختبار المؤسسة.
ms.openlocfilehash: bf64bb23192eb4a4d2b3700a2b0c4390efc1f53e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63565868"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>زيادة Microsoft 365 أمان Microsoft 365 بيئة اختبار المؤسسة

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

باستخدام الإرشادات الواردة في هذه المقالة، يمكنك تكوين إعدادات Microsoft 365 إضافية لزيادة الأمان في بيئة Microsoft 365 اختبار المؤسسة.

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> انقر [هنا](../downloads/Microsoft365EnterpriseTLGStack.pdf) للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة

إذا كنت تريد فقط تكوين مستوى أمان Microsoft 365 بطريقة خفيفة بالحد الأدنى من المتطلبات، فاتبع الإرشادات الموجودة في [تكوين الأساس الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت تريد تكوين مستوى أمان Microsoft 365 في مؤسسة محاكاة، فاتبع الإرشادات الواردة في [المصادقة المرورية](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار Microsoft 365 الأمان بيئة اختبار المؤسسة المحاكاة، التي تتضمن إنترانت محاكاة متصلة بالإنترنت ومزامنة الدليل الغابات خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار الترخيص التلقائي وعضوية المجموعة واختباره في بيئة تمثل مؤسسة نموذجية. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>المرحلة 2: تكوين أمان Microsoft 365 المتزايد

في هذه المرحلة، يمكنك تمكين Microsoft 365 أمان Microsoft 365 بيئة اختبار المؤسسة. للحصول على مزيد من التفاصيل والإعدادات، راجع [تكوين المستأجر لزيادة الأمان](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>تكوين SharePoint Online لحظر التطبيقات التي لا تدعم المصادقة الحديثة

لا يمكن للتطبيقات التي لا تدعم المصادقة [](../security/office-365-security/microsoft-365-policies-configurations.md) الحديثة تطبيق تكوينات الهوية والوصول إلى الجهاز عليها، وهو عنصر هام لتأمين اشتراكك Microsoft 365 وأصوله الرقمية. 

1. انتقل <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">إلى مركز مسؤولي Microsoft 365 ثم</a> سجل الدخول إلى اشتراكك في Microsoft 365 الاختبار باستخدام حساب المسؤول العام.
    
  - إذا كنت تستخدم بيئة الاختبار Microsoft 365، ف سجل الدخول من الكمبيوتر المحلي.
    
  - إذا كنت تستخدم بيئة اختبار المؤسسة Microsoft 365، فاستخدم مدخل [Azure](https://portal.azure.com) للاتصال بالآلة الظاهرية CLIENT1، ثم سجل الدخول من CLIENT1.
 
2. على **علامة التبويب مركز مسؤولي Microsoft 365** الجديدة، ضمن **مراكز** الإدارة في جزء التنقل الأيسر **، انقر فوق** SharePoint.
3. في علامة التبويب SharePoint **مركز الإدارة الجديد**، حدد عنصر تحكم **PoliciesAccess** > .<a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank"></a>
4. حدد **التطبيقات التي لا تدعم المصادقة الحديثة**، وحدد **حظر الوصول**، ثم حدد **حفظ**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>تمكين Defender Office 365 SharePoint OneDrive for Business و Microsoft Teams

يحمي Office 365 SharePoint OneDrive وs Microsoft Teams مؤسستك من مشاركة الملفات الضارة عن غير قصد.

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز & الأمان،</a> ثم سجل الدخول باستخدام حساب المسؤول العام.

2. في جزء التنقل الأيسر، ضمن **إدارة** المخاطر، انقر فوق **نهج**، ثم انقر فوق خزينة **المرفقات**. 

3. ضمن **حماية الملفات في SharePoint، OneDrive، Microsoft Teams**. حدد **تشغيل ATP SharePoint OneDrive Microsoft Teams**.

4. انقر فوق **حفظ**.


### <a name="enable-anti-malware"></a>تمكين مكافحة البرامج الضارة

تتألف البرامج الضارة من الفيروسات وبرامج التجسس. وتصيب الفيروسات البرامج والبيانات الأخرى، وتنتشر عبر الكمبيوتر بحثا عن برامج لإصابة. تشير برامج التجسس إلى البرامج الضارة التي تجمع معلوماتك الشخصية، مثل معلومات تسجيل الدخول والبيانات الشخصية، وتعيد إرسالها إلى كاتب البرامج الضارة. 

Microsoft 365 البرامج الضارة وتصفية البريد العشوائي المضمنة التي تساعد على حماية الرسائل الواردة والداخلة من البرامج الضارة وتساعد على حمايتك من البريد العشوائي. لمزيد من المعلومات، راجع [الحماية من البريد العشوائي & الحماية من البرامج الضارة](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

للتأكد من أنه يتم تنفيذ معالجة مكافحة البرامج الضارة على الملفات ذات أنواع ملفات المرفقات الشائعة:

1. انقر فوق الزر الخلف على المستعرض للعودة إلى **صفحة النهج** .
2. انقر **فوق مكافحة البرامج الضارة**.
3. انقر نقرا مزدوجا فوق النهج المسمى **افتراضي**.
4. في نافذة **نهج مكافحة البرامج** الضارة **، انقر فوق** الإعدادات.
4. ضمن **عامل التصفية أنواع المرفقات الشائعة**، حدد **على،** ثم انقر فوق **حفظ**.


## <a name="phase-3-examine-the-security-dashboard"></a>المرحلة 3: افحص لوحة معلومات الأمان

يمكن أن تساعدك إدارة المخاطر في Microsoft 365 على التحكم في وصول الأجهزة المحمولة إلى بيانات مؤسستك وإدارتها، وتساعد على حماية مؤسستك من فقدان البيانات، وتساعد على حماية الرسائل الواردة والداخلة من البرامج الضارة والبريد العشوائي. يمكنك أيضا استخدام إدارة المخاطر لحماية سمعة مجالك وتحديد ما إذا كان المرسلون ينتحلون الحسابات من مجالك بشكل ضار أم لا. 

لرؤية لوحة معلومات الأمان:

1. إذا لزم الأمر، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز & الأمان</a> ، ثم سجل الدخول باستخدام حساب المسؤول العام.

2. في جزء التنقل الأيسر، ضمن **إدارة المخاطر**، انقر فوق **لوحة المعلومات**.

أطلع على كل البطاقات المتوفرة على لوحة المعلومات عن كثب لكي تطلع نفسك على المعلومات المتوفرة.

لمزيد من المعلومات، راجع [لوحة معلومات الأمان](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>المرحلة 4: فحص Microsoft Secure Score

تعرض Microsoft Secure Score وضع الأمان الخاص بك ك رقم، مما يشير إلى المستوى الحالي بالنسبة إلى الميزات المتوفرة في اشتراكك. كما يوفر لك قائمة إجراءات التحسين التي يمكنك اتخاذها لتحسين نقاطك.

1. أنشئ علامة تبويب جديدة في المستعرض، واذهب إلى Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">،</a> ثم انقر فوق **نقاط آمنة**.
2. على علامة **التبويب نظرة**  عامة، لاحظ نقاط الأمان الحالية وكيفية مقارنتها بالمتوسط العام والاشتراكات بعدد مماثل من التراخيص.
3. على علامة **التبويب إجراءات التحسين** ، اقرأ قائمة الإجراءات التي يمكنك اتخاذها لزيادة نقاطك.

لمزيد من المعلومات، راجع [Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>الخطوات التالية

استكشف [ميزات حماية](m365-enterprise-test-lab-guides.md#information-protection) المعلومات الإضافية وإمكانياتها في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)
