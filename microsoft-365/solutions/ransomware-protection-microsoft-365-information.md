---
title: الخطوة 5. حماية المعلومات
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، هامور، هجوم مهين، هجوم برامج الفدية الضارة، التشفير، علم الفيروسات المشفرة، الثقة الصفرية
description: استخدم الوصول المتحكم به للمجلدات و MIP و DLP و Microsoft Defender لتطبيقات السحابة لحماية Microsoft 365 الحساسة.
ms.openlocfilehash: 0011a3c9fc0d24815818b67906b8f404a191563e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575863"
---
# <a name="step-5-protect-information"></a>الخطوة 5. حماية المعلومات

نظرا لأن مهاجمي برامج الفدية الضارة سينظرون أيضا إلى البيانات الموجودة على الملفات وقاعدة البيانات وأنواع أخرى من الخوادم، فإن إحدى أفضل الطرق لحماية تلك البيانات هي ترحيلها إلى مستأجر Microsoft 365 المستأجر. بعد ذلك، يمكن حمايتها من خلال ميزات التخفيف واسترداد المضمنة مثل الإصدار، سلة المعاد تدويرها، [واستعادة الملفات](ransomware-protection-microsoft-365.md#ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365).

لتوفير حماية إضافية للمعلومات الحساسة في Microsoft 365 المستأجر:

- حدد موقع معلوماتك الحساسة.
- تنفيذ أذونات صارمة وإزالة الوصول الواسع (على سبيل المثال، منع عدد كبير جدا من المستخدمين من امتلاك إمكانيات الكتابة والتحرير والحذف).
- حماية معلوماتك الحساسة.

>[!Note]
>للحصول على إرشادات النشر المفصلة لحماية المعلومات في Microsoft 365 المستأجر، راجع [نشر حماية المعلومات لأنظمة خصوصية البيانات](information-protection-deploy.md). على الرغم من أن هذه الإرشادات مخصصة لأنظمة خصوصية البيانات، إلا أن الكثير منها ينطبق أيضا على الحماية من برامج الفدية الضارة.
>

## <a name="locate-your-sensitive-information"></a>تحديد موقع معلوماتك الحساسة

المهمة الأولى [هي تحديد أنواع](/microsoft-365/compliance/information-protection#know-your-data) المعلومات الحساسة ومواقعها في المستأجر، والتي يمكن أن تتضمن الأنواع التالية:

- حساسة
- الملكية أو الملكية الفكرية
- منظمة، مثل هذه اللوائح الإقليمية التي تحدد حماية معلومات التعريف الشخصية (PII)
- خطط استرداد IT

لكل نوع من المعلومات الحساسة، حدد ما يلي:

- استخدام المعلومات لمنظمتك
- مقياس نسبي لقيمته النقدية إذا كان محتجزا مقابل فدية (مثل مرتفع ومتوسط ومنخفض)
- موقعه الحالي، مثل مجلد OneDrive أو SharePoint أو مكان إقامة التعاون مثل Microsoft Teams فريق
- الأذونات الحالية، التي تتكون من:

   - حسابات المستخدمين الذين لديهم حق الوصول

   - الإجراءات المسموح بها لكل حساب لديه حق الوصول 

## <a name="implement-strict-permissions-for-locations-with-sensitive-information"></a>تنفيذ أذونات صارمة للمواقع ذات المعلومات الحساسة

يستخدم تنفيذ الأذونات تقيدا داخل مستأجر Microsoft 365 الخاص بك مبدأ الامتياز الأقل للمواقع ومواقع الاتصالات، الذي يكون عادة في Microsoft 365 OneDrive مجلدا ومواقع ومجلدات SharePoint وفرق عمل. 

في حين أنه من الأسهل إنشاء مواقع تخزين ملفات أو فرق ذات وصول واسع (مثل الإعداد الافتراضي لكل شخص في مؤسستك)، للحصول على معلومات حساسة، يجب حصر حسابات المستخدمين المسموح بها والإجراءات المسموح بها بالحد الأدنى المطلوب لتلبية متطلبات التعاون والأعمال.

بمجرد وصول مهاجم برامج الفدية الضارة إلى نطاق المستأجر، يحاول تصعيد امتيازاته من خلال التأثير على بيانات اعتماد حسابات المستخدمين ذات نطاقات أوسع من الأذونات عبر المستأجر، مثل حسابات دور المسؤول أو حسابات المستخدمين التي لديها حق الوصول إلى المعلومات الحساسة. 

استنادا إلى سلوك المهاجم النموذجي هذا، هناك مستويان من الصعوبة للمهاجم:

- **منخفض:** يمكن للمهاجم استخدام حساب إذن منخفض واكتشاف معلوماتك الحساسة بسبب الوصول الواسع عبر نطاق المستأجر.
- **أعلى:** لا يمكن للمهاجم استخدام حساب أذونات منخفض واكتشاف معلوماتك الحساسة بسبب الأذونات تقيده. يجب عليهم تصعيد أذوناتهم من خلال تحديد بيانات اعتماد حساب لديه حق الوصول إلى موقع بمعلومات حساسة، ثم التأثير على بيانات اعتماده، ولكن قد يتمكن من القيام بعد ذلك فقط مجموعة محدودة من الإجراءات.

للحصول على المعلومات الحساسة، يجب أن تجعل مستوى الصعوبة مرتفعا قدر ما تستطيع.

يمكنك التأكد من وجود أذونات صارمة في المستأجر باستخدام الخطوات التالية:

1. من الجهد لتحديد [موقع معلوماتك الحساسة](#locate-your-sensitive-information)، راجع الأذونات لمواقع المعلومات الحساسة. 
2. تنفيذ أذونات صارمة للمعلومات الحساسة أثناء تلبية متطلبات التعاون والأعمال وإعلام المستخدمين المتأثرين بذلك.
3. قم بتنفيذ إدارة التغيير للمستخدمين بحيث يتم إنشاء المواقع المستقبلية للمعلومات الحساسة وصيانتها باستخدام أذونات صارمة.
4. يمكنك تدقيق المواقع ومراقبتها للحصول على معلومات حساسة لضمان عدم منح أذونات واسعة.

راجع [إعداد مشاركة الملفات الآمنة والتعاون مع](setup-secure-collaboration-with-teams.md) Microsoft Teams للحصول على إرشادات مفصلة. مثال على مكان إقامة الاتصالات والتعاون مع أذونات صارمة للمعلومات الحساسة هو فريق مع [عزلة أمنية](/microsoft-365/solutions/secure-teams-security-isolation).

## <a name="protect-your-sensitive-information"></a>حماية معلوماتك الحساسة

لحماية معلوماتك الحساسة في حالة حصول مهاجم برامج الفدية الضارة على حق الوصول إليها:

- استخدم [الوصول المتحكم به إلى](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) المجلدات لتجعل من الصعب على التطبيقات غير المصرح بها تعديل البيانات في المجلدات الخاضعة للتحكم.

- استخدم [حماية البيانات في Microsoft](/microsoft-365/compliance/information-protection) والحساسية وطبقها على المعلومات الحساسة. يمكن تكوين تسميات الحساسية لتشفير وأذونات إضافية باستخدام حسابات مستخدمين محددة والإجراءات المسموح بها. سيكون الملف المسمى بهذا النوع من تسمية الحساسية الذي يتم اقتناعه من المستأجر الخاص بك قابلا للاستخدام فقط لحساب مستخدم معرف في التسمية.

- استخدم Microsoft 365 "منع فقدان البيانات" [(DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) للكشف عن البيانات التي تحتوي على معلومات شخصية أو سرية استنادا إلى تسميات الحساسية، داخليا وخارجيا، وتحذيرها وحظرها.

- استخدم [Microsoft Defender لتطبيقات السحابة](/cloud-app-security/what-is-cloud-app-security) لحظر تنزيلات المعلومات الحساسة مثل الملفات. يمكنك أيضا استخدام سياسات الكشف عن الشذوذ [ل Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy#ransomware-activity) للكشف عن نسبة عالية من عمليات تحميل الملفات أو أنشطة حذف الملفات.

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

قد تؤدي التغييرات الإدارية التي يتم إدخالها على الأذونات العريضة إلى رفض وصول المستخدمين أو عدم تمكنهم من تنفيذ بعض الإجراءات.

بالإضافة إلى ذلك، لحماية المعلومات الحساسة في Microsoft 365 المستأجر، تدرب المستخدمين على:

- إنشاء أماكن للتواصل والتعاون باستخدام أذونات صارمة (الحد الأدنى من مجموعة حسابات المستخدمين للوصول والحد الأدنى المسموح به من الإجراءات لكل حساب). 
- تطبيق تسميات الحساسية المناسبة على المعلومات الحساسة.
- استخدام الوصول المتحكم به إلى المجلدات.

## <a name="resulting-configuration"></a>التكوين الناتج

إليك حماية برامج الفدية الضارة للمستأجر للحصول على الخطوات من 1 إلى 5.

![الحماية من برامج الفدية الضارة Microsoft 365 المستأجر بعد الخطوة 5](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step5.png)

## <a name="additional-ransomware-resources"></a>موارد برامج الفدية الضارة الإضافية

المعلومات الأساسية من Microsoft:

- [التهديدات المتزايدة التي تشكلها برامج الفدية الضارة](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/)، نشر مدونة Microsoft حول المشاكل في 20 يوليو 2021
- [برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان](/security/compass/human-operated-ransomware)
- [الحماية السريعة من برامج الفدية الضارة وافيروسات الفدية الضارة](/security/compass/protect-against-ransomware)
- [تقرير الدفاع الرقمي ل Microsoft 2021](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (راجع الصفحات من 10 إلى 19)
- [برامج الفدية الضارة: تقرير](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) تحليل التهديدات المستمرة والمستمرة في مدخل Microsoft 365 Defender
- نهج برامج الفدية الضارة الخاصة بفريق الاستجابة والكشف من Microsoft (DART) [وأفضل الممارسات](/security/compass/incident-response-playbook-dart-ransomware-approach) [و دراسة الحالة](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [زيادة مرونة برامج الفدية الضارة باستخدام Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [الاستعادة من هجوم برامج الفدية الضارة](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [الحماية من البرامج الضارة وفيروسات الفدية الضارة](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [حماية الكمبيوتر الشخصي Windows 10 من برامج الفدية الضارة](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [التعامل مع برامج الفدية الضارة في SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [تقارير تحليلات المخاطر الخاصة بفيروسات الفدية](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) الضارة في مدخل Microsoft 365 Defender

Microsoft 365 Defender:

- [البحث عن برامج الفدية الضارة مع الصيد المتقدم](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [هجوم Azure Defenses for Ransomware](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [زيادة مرونة برامج الفدية الضارة باستخدام Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [خطة النسخ الاحتياطي والاستعادة للحماية من برامج الفدية الضارة](/security/compass/backup-plan-to-protect-against-ransomware)
- [المساعدة في الحماية من برامج الفدية الضارة باستخدام Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (فيديو لمدة 26 دقيقة)
- [الاستعادة من اختراق الهوية المهينة](/azure/security/fundamentals/recover-from-identity-compromise)
- [الكشف المتقدم عن الهجمات متعددة الكواليس في Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [الكشف عن الفدية الضارة في Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender لتطبيقات السحابة:

-  [إنشاء سياسات الكشف عن الشذوذ في Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

منشورات مدونة فريق أمان Microsoft:

- [3 خطوات لمنع برامج الفدية الضارة واستردادها (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [دليل لمكافحة برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: الجزء 1 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  الخطوات الأساسية حول كيفية إدارة فريق الكشف والاستجابة (DART) من Microsoft لإجراء عمليات التحقيق في أحداث برامج الفدية الضارة.

- [دليل لمكافحة برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: الجزء 2 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  التوصيات وأفضل الممارسات.

- [أن تصبح مرنا من خلال فهم مخاطر الأمن الإلكتروني: الجزء 4 — التنقل عبر التهديدات الحالية (مايو 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  راجع قسم **برامج الفدية** الضارة.

- [هجمات برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: كارثة يمكن تفاديها (مارس 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  يتضمن تحليلات سلسلة الهجمات للهجمات الفعلية.

- [استجابة برامج الفدية الضارة - للدفع أو عدم الدفع؟ (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [تستجيب Norsk Hydro لهجمات برامج الفدية الضارة بشفافية (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
