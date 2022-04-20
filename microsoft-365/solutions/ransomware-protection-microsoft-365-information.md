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
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يديرها الإنسان، برامج الفدية الضارة التي يديرها الإنسان، هومور، الهجوم الهجمي، هجوم برامج الفدية الضارة، التشفير، فيروسات التشفير، الثقة الصفرية
description: استخدم الوصول المتحكم به إلى المجلدات وMicrosoft Purview حماية البيانات وDLP Microsoft Defender for Cloud Apps لحماية البيانات الحساسة Microsoft 365.
ms.openlocfilehash: e32c214688adb60fa39fc3c392512f46ec94aecf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945120"
---
# <a name="step-5-protect-information"></a>الخطوة 5. حماية المعلومات

نظرا لأن مهاجمي برامج الفدية الضارة سينظرون أيضا في بياناتك المحلية الموجودة على الملفات وقاعدة البيانات وأنواع أخرى من الخوادم، فإن إحدى أفضل الطرق لحماية تلك البيانات هي ترحيلها إلى مستأجر Microsoft 365. بمجرد الوصول إليها، يمكن حمايتها بواسطة ميزات التخفيف والاسترداد المضمنة مثل [تعيين الإصدار وحاويات المحذوفات واستعادة الملفات](ransomware-protection-microsoft-365.md#ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365).

لتوفير حماية إضافية للمعلومات الحساسة في مستأجر Microsoft 365:

- حدد موقع معلوماتك الحساسة.
- تنفيذ أذونات صارمة وإزالة الوصول الواسع (على سبيل المثال، منع عدد كبير جدا من المستخدمين من امتلاك إمكانيات الكتابة والتحرير والحذف).
- حماية معلوماتك الحساسة.

>[!Note]
>للحصول على إرشادات نشر مفصلة لحماية المعلومات في مستأجر Microsoft 365، راجع [نشر حماية المعلومات للوائح خصوصية البيانات](information-protection-deploy.md). على الرغم من أنه مخصص للوائح خصوصية البيانات، فإن الكثير من الإرشادات تنطبق أيضا على الحماية من برامج الفدية الضارة.
>

## <a name="locate-your-sensitive-information"></a>تحديد موقع معلوماتك الحساسة

المهمة الأولى هي [تحديد أنواع المعلومات الحساسة ومواقعها](/microsoft-365/compliance/information-protection#know-your-data) في المستأجر، والتي يمكن أن تتضمن الأنواع التالية:

- الحساسه
- الملكية أو الملكية الفكرية
- منظمة، مثل هذه اللوائح الإقليمية التي تحدد حماية المعلومات الشخصية (PII)
- خطط استرداد تكنولوجيا المعلومات

لكل نوع من المعلومات الحساسة، حدد ما يلي:

- استخدام المعلومات لمؤسستك
- مقياس نسبي لقيمته النقدية إذا تم الاحتفاظ به مقابل الفدية (مثل مرتفع، متوسط، منخفض)
- موقعه الحالي، مثل مجلد OneDrive أو مجلد SharePoint أو مكان تعاون مثل فريق Microsoft Teams
- الأذونات الحالية، والتي تتكون من:

   - حسابات المستخدمين الذين لديهم حق الوصول

   - الإجراءات المسموح بها لكل حساب لديه حق الوصول 

## <a name="implement-strict-permissions-for-locations-with-sensitive-information"></a>تنفيذ أذونات صارمة للمواقع التي تحتوي على معلومات حساسة

يستخدم تطبيق أذونات صارمة داخل مستأجر Microsoft 365 مبدأ الامتياز الأقل للمواقع وأماكن الاتصالات، والتي تكون عادة في Microsoft 365 OneDrive المجلدات والمواقع والمجلدات SharePoint والفرق. 

في حين أنه من الأسهل إنشاء مواقع تخزين الملفات أو الفرق ذات الوصول الواسع (مثل الإعداد الافتراضي لكل شخص في مؤسستك)، للحصول على معلومات حساسة، يجب أن تقتصر حسابات المستخدمين المسموح بها والإجراءات المسموح بها على الحد الأدنى المطلوب لتلبية متطلبات التعاون والأعمال.

بمجرد أن يتسلل مهاجم برامج الفدية الضارة إلى المستأجر الخاص بك، يحاول تصعيد امتيازاته عن طريق المساس ببيانات اعتماد حسابات المستخدمين مع نطاقات أوسع من الأذونات عبر المستأجر الخاص بك، مثل حسابات دور المسؤول أو حسابات المستخدمين التي لديها حق الوصول إلى المعلومات الحساسة. 

استنادا إلى سلوك المهاجم النموذجي هذا، هناك مستويان من الصعوبة للمهاجم:

- **منخفضه:** يمكن للمهاجم استخدام حساب منخفض الأذونات واكتشاف معلوماتك الحساسة بسبب الوصول الواسع عبر المستأجر.
- **اعلي:** لا يمكن للمهاجم استخدام حساب منخفض الأذونات واكتشاف معلوماتك الحساسة بسبب الأذونات الصارمة. يجب عليهم تصعيد أذوناتهم عن طريق تحديد بيانات الاعتماد الخاصة بحساب لديه حق الوصول إلى موقع يتضمن معلومات حساسة ثم المساس بها، ولكن قد يتمكنون بعد ذلك فقط من القيام بمجموعة محدودة من الإجراءات.

للحصول على معلومات حساسة، يجب أن تجعل مستوى الصعوبة مرتفعا قدر الإمكان.

يمكنك التأكد من وجود أذونات صارمة في المستأجر باستخدام الخطوات التالية:

1. من الجهد المبذول [لتحديد موقع معلوماتك الحساسة](#locate-your-sensitive-information)، راجع أذونات مواقع المعلومات الحساسة. 
2. تنفيذ أذونات صارمة للمعلومات الحساسة مع تلبية متطلبات التعاون والأعمال وإعلام المستخدمين المتأثرين.
3. قم بإجراء إدارة التغيير للمستخدمين بحيث يتم إنشاء المواقع المستقبلية للمعلومات الحساسة وصيانتها بأذونات صارمة.
4. قم بتدقيق ومراقبة المواقع للحصول على معلومات حساسة لضمان عدم منح أذونات واسعة.

راجع [إعداد مشاركة الملفات الآمنة والتعاون في العمل مع Microsoft Teams](setup-secure-collaboration-with-teams.md) للحصول على إرشادات مفصلة. مثال على مكان الاتصال والتعاون مع أذونات صارمة للمعلومات الحساسة هو [فريق مع عزل أمني](/microsoft-365/solutions/secure-teams-security-isolation).

## <a name="protect-your-sensitive-information"></a>حماية معلوماتك الحساسة

لحماية معلوماتك الحساسة في حالة حصول مهاجم برامج الفدية الضارة على حق الوصول إليها:

- استخدم [الوصول المتحكم به إلى المجلدات](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) لجعل تعديل البيانات في المجلدات التي يتم التحكم فيها أكثر صعوبة على التطبيقات غير المصرح بها.

- استخدم [حماية البيانات Microsoft Purview](/microsoft-365/compliance/information-protection) وتسميات الحساسية وقم بتطبيقها على المعلومات الحساسة. يمكن تكوين تسميات الحساسية للتشفير الإضافي والأذونات باستخدام حسابات المستخدمين المحددة والإجراءات المسموح بها. لن يكون الملف المسمى بهذا النوع من وصف الحساسية الذي تم حذفه من المستأجر الخاص بك قابلا للاستخدام إلا لحساب مستخدم معرف في التسمية.

- استخدم Microsoft Purview [Data Loss Prevention (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) للكشف عن البيانات التي تحتوي على معلومات شخصية أو سرية وتحذيرها ومنع مشاركتها المحفوفة بالمخاطر أو غير المقصودة أو غير المناسبة استنادا إلى تسميات الحساسية داخليا وخارجيا.

- استخدم [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) لحظر تنزيلات المعلومات الحساسة مثل الملفات. يمكنك أيضا استخدام [نهج الكشف عن الحالات الشاذة ل Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy#ransomware-activity) للكشف عن نسبة عالية من عمليات تحميل الملفات أو أنشطة حذف الملفات.

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

يمكن أن تؤدي التغييرات الإدارية على الأذونات الواسعة إلى رفض وصول المستخدمين أو عدم القدرة على تنفيذ بعض الإجراءات.

بالإضافة إلى ذلك، لحماية المعلومات الحساسة في مستأجر Microsoft 365، قم بتدريب المستخدمين على:

- إنشاء أماكن الاتصال والتعاون بأذونات صارمة (الحد الأدنى لمجموعة حسابات المستخدمين للوصول والحد الأدنى للإجراءات المسموح بها لكل حساب). 
- تطبيق تسميات الحساسية المناسبة على المعلومات الحساسة.
- استخدام الوصول المتحكم به إلى المجلد.

## <a name="resulting-configuration"></a>التكوين الناتج

فيما يلي حماية برامج الفدية الضارة للمستأجر الخاص بك للخطوات من 1 إلى 5.

![حماية برامج الفدية الضارة لمستأجر Microsoft 365 بعد الخطوة 5](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step5.png)

## <a name="additional-ransomware-resources"></a>موارد برامج الفدية الإضافية

المعلومات الرئيسية من Microsoft:

- [التهديد المتزايد من برامج الفدية الضارة](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/)، منشور مدونة Microsoft On the Issues في 20 يوليو 2021
- [برامج الفدية الضارة التي يديرها الإنسان](/security/compass/human-operated-ransomware)
- [الحماية السريعة من برامج الفدية الضارة والمساهمة](/security/compass/protect-against-ransomware)
- [تقرير الدفاع الرقمي ل Microsoft 2021](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (راجع الصفحات 10-19)
- [برامج الفدية الضارة: تقرير تحليلات مخاطر التهديدات المنتشرة والمستمرة](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) في مدخل Microsoft 365 Defender
- نهج برامج الفدية الضارة لفريق الكشف والاستجابة (DART) من Microsoft [وأفضل الممارسات](/security/compass/incident-response-playbook-dart-ransomware-approach) [ودراسة الحالة](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [زيادة مرونة برامج الفدية الضارة مع Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [التعافي من هجوم برامج الفدية الضارة](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [البرامج الضارة والحماية من برامج الفدية الضارة](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [حماية الكمبيوتر الشخصي Windows 10 من برامج الفدية الضارة](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [التعامل مع برامج الفدية الضارة في SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [تقارير تحليلات التهديد حول برامج الفدية الضارة](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) في مدخل Microsoft 365 Defender

Microsoft 365 Defender:

- [البحث عن برامج الفدية الضارة باستخدام التتبع المتقدم](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses لهجمات برامج الفدية الضارة](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [زيادة مرونة برامج الفدية الضارة مع Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [خطة النسخ الاحتياطي والاستعادة للحماية من برامج الفدية الضارة](/security/compass/backup-plan-to-protect-against-ransomware)
- [المساعدة في الحماية من برامج الفدية الضارة باستخدام Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (فيديو مدته 26 دقيقة)
- [التعافي من اختراق الهوية النظامية](/azure/security/fundamentals/recover-from-identity-compromise)
- [الكشف المتقدم عن الهجوم متعدد المستويات في Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [اكتشاف الاندماج لبرنامج الفدية الضارة في Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [إنشاء نهج الكشف عن الحالات الشاذة في Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

منشورات مدونة فريق أمان Microsoft:

- [3 خطوات لمنع برامج الفدية الضارة والتعافي منها (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [دليل لمكافحة برامج الفدية الضارة التي يديرها الإنسان: الجزء الأول (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  الخطوات الرئيسية حول كيفية قيام فريق الكشف والاستجابة من Microsoft (DART) بإجراء التحقيقات في حوادث برامج الفدية الضارة.

- [دليل لمكافحة برامج الفدية الضارة التي يديرها الإنسان: الجزء 2 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  التوصيات وأفضل الممارسات.

- [القدرة على الصمود من خلال فهم مخاطر الأمان عبر الإنترنت: الجزء 4 - التنقل بين التهديدات الحالية (مايو 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  راجع قسم **برامج الفدية الضارة** .

- [هجمات برامج الفدية الضارة التي يديرها الإنسان: كارثة يمكن الوقاية منها (مارس 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  يتضمن تحليلات سلسلة الهجوم للهجمات الفعلية.

- [استجابة برامج الفدية الضارة - للدفع أو عدم الدفع؟ (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [يستجيب Norsk Hydro لهجوم برامج الفدية الضارة بالشفافية (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
