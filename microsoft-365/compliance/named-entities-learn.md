---
title: التعرف على الكيانات المسماة (معاينة)
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
description: تعرف على كيفية مساعدة الكيانات المسماة في الكشف عن العناصر الحساسة التي تحتوي على أسماء الأشخاص والعناوين الفعلية والمصطلحات الطبية عبر سياسات منع فقدان البيانات
ms.openlocfilehash: 79f375fecf09a6f7ffe4c1a97b8d6864fbfb3e13
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63579964"
---
# <a name="learn-about-named-entities-preview"></a>التعرف على الكيانات المسماة (معاينة)

> [!IMPORTANT]
> يتم طرح ميزة الكيانات المسماة وستظهر في المستأجر عندما تكون متوفرة لك. تحقق من ذلك في مستكشف المحتوى وفي تدفق تأليف نهج منع فقدان البيانات (DLP). 

*الكيانات المسماة* هي [أنواع معلومات حساسة](sensitive-information-type-learn-about.md) (SIT). إنها عبارة عن قاموس معقد ومصنفات مستندة إلى نقش يمكنك استخدامها للكشف عن أسماء الأشخاص والعناوين الفعلية والشروط والأحكام الطبية. يمكنك الاطلاع عليها في مركز التوافق > **تصنيف > الحساسة**. فيما يلي قائمة جزئية بالقائمة التي يمكنك فيها استخدام SITs:

- [سياسات منع فقدان البيانات (DLP)](dlp-learn-about-dlp.md) 
- [تسميات الحساسية](sensitivity-labels.md)
- [إدارة مخاطر Insider](insider-risk-management-solution-overview.md)
- [Microsoft Defender لتطبيقات السحابة](/cloud-app-security/what-is-cloud-app-security)

تستخدم DLP الكيانات المسماة بشكل خاص في قوالب النهج المحسنة، وهي نهج DLP التي تم تكوينها مسبقا والتي يمكنك تخصيصها لتلبية احتياجات مؤسستك. يمكنك أيضا [إنشاء سياسات DLP](create-test-tune-dlp-policy.md) الخاصة بك من قالب [فارغ](create-a-dlp-policy-from-a-template.md) واستخدام كيان مسمى SIT كشرط.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>أمثلة على كيانات مسماة SITs

تأتي SITs للكيان المسمى في نوعين *من* النكهات، مجمعة وغير *متشابكة*

تكتشف كيانات SITS المسماة المجمعة كل التطابقات المحتملة. استخدمها كمعايع واسعة في نهج DLP للكشف عن العناصر الحساسة.

لدى كيانات كيانات مسماة غير مفبركة تركيز أضيق، مثل بلد واحد. استخدمها عندما تحتاج إلى نهج DLP بنطاق كشف أضيق.
 
فيما يلي بعض الأمثلة على كيانات مسماة SITs. يمكنك العثور على كل 52 منها في مركز التوافق > **تصنيف > المعلومات الحساسة**.

|كيان مسمى |الوصف  |مجمعة/غير مختلطه  |
|---------|---------|---------|
|كل الأسماء الكاملة    |الكشف عن جميع المطابقات المحتملة للأسماء الكاملة         |   مجمعة      |
|كل العناوين الفعلية    |الكشف عن كل تطابقات العناوين الفعلية المحتملة     | مجمعة |
|كل الشروط والأحكام الطبية    |الكشف عن جميع تطابقات الشروط والأحكام الطبية المحتملة |مجمعة |
|العناوين الفعلية في أستراليا |  الكشف عن الأنماط المرتبطة والعناوين الفعلية من أستراليا. |إلغاء تشابك |
|شروط اختبار الدم     |الكشف عن المصطلحات المتعلقة باختبارات الدم، مثل 'hCG'. شروط اللغة الإنجليزية فقط.      |إلغاء تشابك |
|أسماء الأدوية للعلامة التجارية     |الكشف عن أسماء الأدوية التي تحمل علامة تجارية، مثل 'Tylenol'. شروط اللغة الإنجليزية فقط.         |إلغاء تشابك |

## <a name="examples-of-enhanced-dlp-policies"></a>أمثلة على سياسات DLP المحسنة

فيما يلي بعض الأمثلة حول سياسات DLP المحسنة التي تستخدم كيانات مسماة SITs. يمكنك العثور على كل هذه ال 10 في مركز التوافق > فقدان البيانات > **إنشاء نهج**. يمكن استخدام القوالب المحسنة في DLP والتسميات التلقائية.

|فئة النهج  |قالب  |الوصف  |
|---------|---------|---------|
|المالية|تم تحسين قانون Gramm-Leach-Bliley (GLBA) الأمريكي         |يساعد على الكشف عن وجود معلومات تخضع ل قانون Gramm-Leach-Bliley (GLBA)، بما في ذلك معلومات مثل أرقام الضمان الاجتماعي أو أرقام بطاقات الائتمان. يوسع هذا القالب المحسن القالب الأصلي من خلال الكشف أيضا عن الأسماء الكاملة للأشخاص، الولايات المتحدة/المملكة المتحدة. رقم جواز السفر، رقم ترخيص القيادة الأمريكية والعناوين الفعلية الأمريكية.         |
| الصحة والرعاية الطبية   |قانون السجلات الصحية في أستراليا (قانون HRIP) محسن         |يساعد على الكشف عن وجود المعلومات التي تعتبر عادة خاضعة ل قانون السجلات الصحية وخصوصية المعلومات (HRIP) في أستراليا، مثل رقم الحساب الطبي و رقم الملف الضريبي. يوسع هذا القالب المحسن القالب الأصلي من خلال الكشف أيضا عن الأسماء الكاملة للأشخاص والشروط والأحكام الطبية والعناوين الفعلية في أستراليا.         |
|الخصوصية   |القانون العام لحماية البيانات (GDPR) محسن         | يساعد على الكشف عن وجود معلومات شخصية للأفراد داخل الاتحاد الأوروبي للمساعدة في الوفاء بالالتزامات المتعلقة بالخصوصية ل GDPR. يكشف هذا القالب المحسن عن الأسماء الكاملة للأشخاص وعناوينهم الفعلية للبلدان في الاتحاد الأوروبي.        |


## <a name="next-steps"></a>الخطوات التالية

- [استخدام الكيانات المسماة في سياسات منع فقدان البيانات (معاينة)](named-entities-use.md)


## <a name="for-further-information"></a>لمزيد من المعلومات
<!--- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md)
- [إنشاء نوع معلومات حساسة مخصصة](create-a-custom-sensitive-information-type.md)
- [إنشاء نوع معلومات حساسة مخصصة في PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [سياسات منع فقدان البيانات (DLP)](data-loss-prevention-policies.md) 
- [تسميات الحساسية](sensitivity-labels.md)
- [تسميات الاستبقاء](retention.md)
- [توافق الاتصالات](communication-compliance.md)
- [سياسات التصفية التلقائية](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md) 
