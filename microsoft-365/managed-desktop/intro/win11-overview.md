---
title: سطح المكتب المدار من Microsoft Windows 11
description: كيفية Windows 11 في الخدمة
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 494f147dad24b8c668fcb8adfc9b8a845a5fbe8f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579680"
---
# <a name="microsoft-managed-desktop-and-windows-11"></a>سطح المكتب المدار من Microsoft Windows 11

بعد الإعلان عن Windows 11، ربما بدأت Windows 11 عمليات الترحيل كجزء من جهودك لإبقاء أجهزة Windows 10 متابعتها.

توضح هذه المقالة الاعتبارات الهامة وكيفية دعم Microsoft Managed Desktop للانتقالات السلسة في بيئاتك. للحصول على معلومات حول Windows 11 نفسها، راجع Windows 11 [عامة](/windows/whats-new/windows-11).

للحصول على خطوات معينة يجب اتباعها Windows 11 على أجهزة سطح المكتب المدارة من Microsoft، راجع معاينة Windows 11 [باستخدام Microsoft Managed Desktop](../working-with-managed-desktop/test-win11-mmd.md).

## <a name="timeline-for-windows-10-and-windows-11"></a>مخطط زمني Windows 10 Windows 11

Windows 11 متوفرة بشكل عام في 4 أكتوبر 2021. إنه جاهز لنشر المستهلكين والمؤسسات، وهو نظام أساسي مدعوم بالكامل.

سنبدأ جدولة عمليات النشر لجميع أجهزة سطح المكتب المدارة من Microsoft بدءا من يناير 2023. ومع ذلك، سنوفر الدعم الكامل لأولئك الذين يرغبون في نشر Windows 11 أقرب. سنستشار المسؤولين وننصحهم بتطوير خطط ترحيل لكل مستأجر وتطبيقها استنادا إلى الجهوزية التقنية والاعتبارات المتعلقة بأعمالك.

يستمر Microsoft Managed Desktop في دعم Windows 10 بشكل متوازي حتى يصل إلى نهاية دعم المؤسسة. راجع [Windows 10 معلومات الإصدار للحصول](/windows/release-health/release-information) على معلومات حول دورة الحياة.

## <a name="assessing-pre-release-versions-of-windows-11"></a>تقييم إصدارات النسخة التجريبية من Windows 11

أكثر من 95٪ من أجهزة سطح المكتب المدارة من Microsoft مؤهلة Windows 11. قد ترغب في تجربة الترقية على أجهزة الاختبار قبل نشر الإنتاج. لمزيد من المعلومات Windows 11 متطلبات النظام، راجع Windows 11 [متطلبات النظام](/windows/whats-new/windows-11-requirements).

بالنسبة لأجهزة سطح المكتب المدارة من Microsoft، يمكنك إضافة أجهزة إلى [مجموعة Windows 11 اختبار الأجهزة](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#add-devices-to-the-windows-11-test-group). تتلقى هذه المجموعة Windows 11 التوفر العام بالإضافة إلى تكوين أساسي لسطح المكتب المدار من Microsoft. بمجرد إضافته إلى مجموعة الأجهزة، اسمح لجهاز ما من يوم إلى يومين لالتقاط الإعدادات الجديدة وعرضها Windows 11.

بالنسبة للأجهزة التي لا يديرها Microsoft Managed Desktop، يمكنك قراءة [إدارة نقاط النهاية للتعرف على](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/endpoint-manager-simplifies-upgrades-to-windows-11/ba-p/2771886) كيفية نشر Windows 11. إذا كان لديك أجهزة تعمل Windows 11 واللاحقة وتسجلها في Microsoft Managed Desktop، فلن تعود إلى Windows 10.

## <a name="support-for-pre-release-windows-11-devices"></a>دعم أجهزة الإصدار Windows 11 الإصدارات المسبقة

بالنسبة إلى الأشخاص الذين Windows 11 الاختبار قبل التوفر العام، قد تكون الأجهزة قد تم تثبيت الإصدارات المعاينة عليها.

لن يتم عرض أجهزة سطح المكتب المدارة من Microsoft في هذه الحالة Windows 11 التوفر العام. ومع ذلك، سيبقى الجهاز مدعوما لحل المشاكل التي واجهتها. يراقب سطح المكتب المدار من Microsoft جميع الأجهزة المدارة للتنبيهات، وسيستجيب لأي تنبيهات بغض النظر عما إذا كان الجهاز يعمل Windows 11 إصدار معاينة.

نظرا لأننا نلتزم بمساعدتك على الترحيل إلى Windows 11 مع البقاء منتجا، فإننا نشجعك على الإبلاغ عن عيوب تواجهها مع النظام الأساسي. نحن نولي الأولوية:

- العيوب التي تمنع إنتاجية المستخدم عند النشر الواسع Windows 11.
- العيوب التي تمنع إنتاجية المستخدم على Windows 10 الأجهزة.

## <a name="testing-application-compatibility"></a>اختبار توافق التطبيقات

إن توافق التطبيقات هو أحد أكثر المشاكل شيوعا في أي عملية ترحيل ل النظام الأساسي بسبب احتمال حدوث انقطاعات في الإنتاجية. نحن نستخدم العديد من الإجراءات الاستباقية والتفاعلية لمساعدتك على الشعور بالثقة بشأن الانتقالات السلسة للتطبيقات Windows 11.

### <a name="proactive-measures"></a>التدابير الاستباقية

فيما يلي بعض التدابير الاستباقية:

| التدابير الاستباقية | الوصف |
| ----- | ----- |
| التطبيقات الشائعة | تختبر Microsoft بشكل مكثف تطبيقات المؤسسة وجناحها الأكثر شيوعا التي تم نشرها على Windows 11 جديدة. نحن نعمل مع ناشري البرامج الخارجيين وفرق المنتجات الداخلية لحل أي مشاكل تم اكتشافها أثناء الاختبار. لمزيد من المعلومات حول جهد اختبار التوافق الاستباقي، راجع مدونة [توافق التطبيقات](https://blogs.windows.com/windowsexperience/2019/01/15/application-compatibility-in-the-windows-ecosystem/).
| تطبيقات خط العمل | [Test Base](https://www.microsoft.com/en-us/testbase) هو مورد يمكن لناشري التطبيقات لمسؤولي تقنيات المعلومات استخدامه لإرسال التطبيقات و حالات الاختبار ل Microsoft لتشغيلها على جهاز ظاهري يعمل Windows 11 في بيئة Azure آمنة.<br><br>تتوفر النتائج ورؤى الاختبار وتحليل الانحدار لكل تنفيذ اختبار على مدخل Azure خاص. سيساعدك Microsoft Managed Desktop على تحديد أولويات تطبيقات خط العمل للتحقق من الصحة استنادا إلى بيانات استخدام التطبيقات والموثوقية. لمزيد من المعلومات حول Test Base، راجع [Test Base for Microsoft 365](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/test-base-for-microsoft-365-microsoft-ignite-2021-updates/ba-p/2185566). |

### <a name="reactive-measures"></a>قياسات التفاعل

إذا واجهت مشاكل تتعلق بتوافق التطبيق في بيئات الاختبار أو الإنتاج، يمكنك تلقي دعم بدون تكلفة عن طريق فتح [طلب دعم](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#report-issues).

بالنسبة Windows 11، يتضمن الدعم أي وظائف مع التطبيقات التالية التي يتم تشغيلها على أحدث إصدار من أنظمة التشغيل:

- Office
- Microsoft Edge
- الفرق
- تطبيقات خط العمل

يشرك Microsoft App Assure ناشري التطبيقات مباشرة لتحديد أولويات مشاكل توافق التطبيقات وحلها عند الحاجة.
