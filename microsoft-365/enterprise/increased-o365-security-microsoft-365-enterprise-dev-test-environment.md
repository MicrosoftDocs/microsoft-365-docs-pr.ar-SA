---
title: زيادة أمان Microsoft 365 Microsoft 365 لبيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: استخدم دليل مختبر الاختبار هذا لتمكين إعدادات أمان Microsoft 365 إضافية Microsoft 365 لبيئة اختبار المؤسسة.
ms.openlocfilehash: 4c69fadd3fb3e6744fad850e76282ea2339f48ee
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100710"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>زيادة أمان Microsoft 365 Microsoft 365 لبيئة اختبار المؤسسة

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

باستخدام الإرشادات الواردة في هذه المقالة، يمكنك تكوين إعدادات Microsoft 365 إضافية لزيادة الأمان في Microsoft 365 لبيئة اختبار المؤسسة.

![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> انقر [هنا](../downloads/Microsoft365EnterpriseTLGStack.pdf) للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة

إذا كنت تريد فقط تكوين أمان Microsoft 365 متزايد بطريقة خفيفة مع الحد الأدنى من المتطلبات، فاتبع الإرشادات في [التكوين الأساسي الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت ترغب في تكوين أمان Microsoft 365 متزايد في مؤسسة محاكاة، فاتبع الإرشادات [الواردة في مصادقة المرور](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار الأمان Microsoft 365 المتزايد بيئة اختبار المؤسسة المحاكاة، والتي تتضمن شبكة إنترانت محاكاة متصلة بالإنترنت ومزامنة الدليل لمجموعة خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار الترخيص التلقائي وعضوية المجموعة وتجربة ذلك في بيئة تمثل مؤسسة نموذجية. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>المرحلة 2: تكوين أمان Microsoft 365 المتزايد

في هذه المرحلة، يمكنك تمكين زيادة أمان Microsoft 365 Microsoft 365 لبيئة اختبار المؤسسة. لمزيد من التفاصيل والإعدادات، راجع [تكوين المستأجر لزيادة الأمان](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>تكوين SharePoint Online لحظر التطبيقات التي لا تدعم المصادقة الحديثة

لا يمكن للتطبيقات التي لا تدعم المصادقة الحديثة تطبيق [تكوينات الوصول إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) عليها، وهو عنصر مهم لتأمين اشتراكك في Microsoft 365 وأصوله الرقمية. 

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> وسجل الدخول إلى اشتراك مختبر الاختبار Microsoft 365 باستخدام حساب المسؤول العام.
    
  - إذا كنت تستخدم بيئة اختبار Microsoft 365 خفيفة الوزن، فسجل دخولك من الكمبيوتر المحلي.
    
  - إذا كنت تستخدم بيئة اختبار Microsoft 365 المؤسسة المحاكاة، فاستخدم [مدخل Microsoft Azure](https://portal.azure.com) للاتصال بالجهاز الظاهري CLIENT1، ثم سجل الدخول من CLIENT1.
 
2. على علامة التبويب **مركز مسؤولي Microsoft 365** الجديدة، ضمن **مراكز الإدارة** في جزء التنقل الأيمن، انقر فوق **SharePoint**.
3. في علامة تبويب **مركز إدارة SharePoint** الجديد، حدد <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**عنصر تحكم PoliciesAccess**</a> > .
4. حدد **التطبيقات التي لا تدعم المصادقة الحديثة**، وحدد **"حظر الوصول"**، ثم حدد **"حفظ**".


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>تمكين Defender لـ Office 365 SharePoint OneDrive for Business Microsoft Teams

Defender لـ Office 365 SharePoint OneDrive Microsoft Teams تحمي مؤسستك من مشاركة الملفات الضارة عن غير قصد.

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز توافق & الأمان</a> وسجل الدخول باستخدام حساب المسؤول العام.

2. في جزء التنقل الأيمن، ضمن **إدارة المخاطر**، انقر فوق **"نهج**"، ثم انقر فوق **"خزينة المرفقات**". 

3. ضمن **حماية الملفات في SharePoint، OneDrive، Microsoft Teams**. حدد **"تشغيل ATP" SharePoint و"OneDrive" و"Microsoft Teams**".

4. انقر فوق **حفظ**.


### <a name="enable-anti-malware"></a>تمكين مكافحة البرامج الضارة

تتكون البرامج الضارة من الفيروسات وبرامج التجسس. وتتسبب الفيروسات في إصابة البرامج والبيانات الأخرى، وتنتشر في جميع أنحاء الكمبيوتر بحثا عن برامج لإصابتها. تشير برامج التجسس إلى البرامج الضارة التي تجمع معلوماتك الشخصية، مثل معلومات تسجيل الدخول والبيانات الشخصية، وترسلها مرة أخرى إلى كاتب البرامج الضارة. 

يحتوي Microsoft 365 على إمكانات مضمنة لتصفية البرامج الضارة والبريد العشوائي التي تساعد على حماية الرسائل الواردة والصادرة من البرامج الضارة وتساعد في حمايتهم من البريد العشوائي. لمزيد من المعلومات، راجع [مكافحة البريد العشوائي & الحماية من البرامج الضارة](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

للتأكد من إجراء معالجة مكافحة البرامج الضارة على الملفات ذات أنواع ملفات المرفقات الشائعة:

1. انقر فوق الزر "الخلف" في المستعرض للعودة إلى صفحة **"النهج** ".
2. انقر فوق **مكافحة البرامج الضارة**.
3. انقر نقرا مزدوجا فوق النهج المسمى **Default**.
4. في نافذة **نهج مكافحة البرامج الضارة**، انقر فوق **الإعدادات**.
4. ضمن **عامل تصفية أنواع المرفقات الشائعة**، حدد **"تشغيل**"، ثم انقر فوق **"حفظ**".


## <a name="phase-3-examine-the-security-dashboard"></a>المرحلة 3: فحص لوحة معلومات الأمان

يمكن أن تساعدك إدارة التهديدات في Microsoft 365 على التحكم في وصول الأجهزة المحمولة إلى بيانات مؤسستك وإدارتها، والمساعدة في حماية مؤسستك من فقدان البيانات، والمساعدة في حماية الرسائل الواردة والصادرة من البرامج الضارة والبريد العشوائي. يمكنك أيضا استخدام إدارة المخاطر لحماية سمعة مجالك وتحديد ما إذا كان المرسلون ينتحلون حسابات من مجالك بشكل ضار أم لا. 

لمشاهدة لوحة معلومات الأمان:

1. إذا لزم الأمر، فانتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز توافق & الأمان</a> وسجل الدخول باستخدام حساب المسؤول العام.

2. في جزء التنقل الأيمن، ضمن **إدارة المخاطر**، انقر فوق **"لوحة المعلومات**".

ألق نظرة فاحصة على جميع البطاقات الموجودة على لوحة المعلومات للتعرف على المعلومات المقدمة.

لمزيد من المعلومات، راجع [لوحة معلومات الأمان](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>المرحلة 4: فحص نقاط Microsoft الآمنة

تعرض نقاط الأمان من Microsoft وضع الأمان كرقم، مما يشير إلى مستواك الحالي بالنسبة إلى الميزات المتوفرة في اشتراكك. كما يوفر لك قائمة بإجراءات التحسين التي يمكنك اتخاذها لتحسين درجاتك.

1. أنشئ علامة تبويب جديدة في المستعرض، وانتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، ثم انقر فوق **درجة الأمان**.
2. في علامة التبويب **"نظرة عامة**  "، لاحظ درجة الأمان الحالية وكيفية مقارنتها بالمتوسط العمومي والاشتراكات التي تحتوي على عدد مماثل من التراخيص.
3. في علامة التبويب **"تحسين الإجراءات** "، اقرأ قائمة الإجراءات التي يمكنك اتخاذها لزيادة درجاتك.

لمزيد من المعلومات، راجع [نقاط أمان Microsoft](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>الخطوات التالية

استكشف ميزات [وإمكانات إضافية لحماية المعلومات](m365-enterprise-test-lab-guides.md#information-protection) في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)
