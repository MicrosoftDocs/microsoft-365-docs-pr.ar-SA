---
title: تعرف على الكيانات المسماة
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: تعرف على كيفية مساعدة الكيانات المسماة في اكتشاف العناصر الحساسة التي تحتوي على أسماء الأشخاص والعناوين المادية والمصطلحات الطبية عبر نهج منع فقدان البيانات
ms.openlocfilehash: 013d2453190c692eeb3ae9a0dfd48437bded1f0c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633488"
---
# <a name="learn-about-named-entities"></a>تعرف على الكيانات المسماة

*الكيانات المسماة* هي [أنواع معلومات حساسة](sensitive-information-type-learn-about.md) (SIT). إنها قاموس معقد وتصنيفات مستندة إلى الأنماط يمكنك استخدامها للكشف عن أسماء الأشخاص والعناوين المادية والمصطلحات والشروط الطبية. يمكنك رؤيتها في **تصنيف البيانات مدخل التوافق في Microsoft Purview > > أنواع المعلومات الحساسة**. فيما يلي قائمة جزئية بالمكان الذي يمكنك فيه استخدام SITs:


- [نهج تفادي فقدان البيانات في Microsoft Purview (DLP)](dlp-learn-about-dlp.md) 
- [تسميات الحساسية](sensitivity-labels.md)
- [إدارة المخاطر الداخلية](insider-risk-management-solution-overview.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [حماية المعلومات في Microsoft Purview](apply-sensitivity-label-automatically.md)
- [إدارة دورة حياة البيانات](information-governance.md)
- [إدارة السجلات](records-management.md)
- [Microsoft Purview eDiscovery](ediscovery.md)
- [Microsoft Priva](/privacy/priva/priva-overview.md)
- [تتطابق البيانات الدقيقة مع أنواع المعلومات الحساسة](sit-learn-about-exact-data-match-based-sits.md)

يستخدم DLP بشكل خاص الكيانات المسماة في *قوالب النهج المحسنة*، وهي نهج DLP تم تكوينها مسبقا يمكنك تخصيصها لاحتياجات مؤسستك. يمكنك أيضا [إنشاء نهج DLP الخاصة بك](create-test-tune-dlp-policy.md) من [قالب فارغ](create-a-dlp-policy-from-a-template.md) واستخدام كيان مسمى SIT كشرط.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>أمثلة على  SITs للكيان المسمى

تأتي SITs للكيان المسمى في نوعين، *مجمعين* *وغير مضمنين*

تكتشف  SITs للكيان المجمع المسمى جميع التطابقات المحتملة. استخدمها كمعايير واسعة في نهج DLP للكشف عن العناصر الحساسة.

تتمتع كيانات SITs المسماة غير المكررة بتركيز أضيق، مثل بلد واحد. استخدمها عندما تحتاج إلى نهج DLP مع نطاق اكتشاف أضيق.
 
فيما يلي بعض الأمثلة على  SITs للكيان المسمى. يمكنك العثور عليها جميعا في [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md).

|الوحدة المسماة |الوصف  |مجمع/غير مجمع  |
|---------|---------|---------|
|كافة الأسماء الكاملة    |الكشف عن كافة التطابقات المحتملة للأسماء الكاملة         |   المجمعه      |
|كافة العناوين الفعلية    |الكشف عن كافة التطابقات المحتملة للعناوين الفعلية     | المجمعه |
|جميع الشروط والأحكام الطبية    |الكشف عن جميع التطابقات المحتملة للشروط والأحكام الطبية |المجمعه |
|العناوين المادية في أستراليا |  الكشف عن الأنماط المتعلقة بالعناوين المادية من أستراليا. مضمن في كافة العناوين الفعلية SIT. |غير متكتم |
|شروط اختبار الدم     |الكشف عن المصطلحات المتعلقة باختبارات الدم، مثل "hCG". المصطلحات الإنجليزية فقط. مضمنة في جميع الشروط والأحكام الطبية SIT      |غير متكتم |
|أسماء أدوية العلامة التجارية     |الكشف عن أسماء أدوية العلامة التجارية، مثل 'Tylenol'. المصطلحات الإنجليزية فقط. مضمنة في جميع الشروط والأحكام الطبية.         |غير متكتم |

## <a name="examples-of-enhanced-dlp-policies"></a>أمثلة على نهج DLP المحسنة

فيما يلي بعض الأمثلة على نهج DLP المحسنة التي تستخدم SITs الكيان المسمى. يمكنك العثور على كل 10 منها في **مدخل التوافق في Microsoft Purview > منع فقدان البيانات > إنشاء نهج**. يمكن استخدام القوالب المحسنة في DLP والتسمية التلقائية.

|فئة النهج  |قالب  |الوصف  |
|---------|---------|---------|
|الماليه|U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced         |يساعد على اكتشاف وجود المعلومات الخاضعة لقانون Gramm-Leach-Bliley (GLBA)، بما في ذلك معلومات مثل أرقام الضمان الاجتماعي أو أرقام بطاقات الائتمان. يوسع هذا القالب المحسن الأصل عن طريق الكشف أيضا عن الأسماء الكاملة للأشخاص، U.S./U.K. رقم جواز السفر ورقم رخصة القيادة الأمريكية والعناوين المادية الأمريكية.         |
| الرعاية الطبية والصحة   |قانون السجلات الصحية في أستراليا (قانون HRIP) محسن         |يساعد على اكتشاف وجود المعلومات التي تعتبر عادة خاضعة لقانون خصوصية السجلات الصحية والمعلومات (HRIP) في أستراليا، مثل رقم الحساب الطبي ورقم الملف الضريبي. يمتد هذا القالب المحسن إلى الأصل من خلال الكشف أيضا عن الأسماء الكاملة للأشخاص والأحكام والشروط الطبية والعناوين المادية في أستراليا.         |
|الخصوصية   |القانون العام لحماية البيانات (GDPR) المحسن         | يساعد على الكشف عن وجود معلومات شخصية للأفراد داخل الاتحاد الأوروبي للمساعدة في الوفاء بالتزامات خصوصية القانون العام لحماية البيانات . يكشف هذا القالب المحسن عن الأسماء الكاملة للأشخاص والعناوين المادية للبلدان في الاتحاد الأوروبي.        |


## <a name="next-steps"></a>الخطوات التالية

- [استخدام الكيانات المسماة في نهج تفادي فقدان البيانات](named-entities-use.md)


## <a name="for-further-information"></a>لمزيد من المعلومات

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)
- [إنشاء نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md)
- [إنشاء نوع معلومات حساسة مخصص في PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [نهج منع فقدان البيانات (DLP)](data-loss-prevention-policies.md) 
- [تسميات الحساسية](sensitivity-labels.md)
- [تسميات الاستبقاء](retention.md)
- [توافق الاتصالات](communication-compliance.md)
- [نهج التسمية التلقائية](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md) 
