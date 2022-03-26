---
title: بدء استخدام لوحة معلومات تنبيهات منع فقدان البيانات
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: بدء استخدام تعريف التنبيهات وإدارتها لنهج منع فقدان البيانات.
ms.openlocfilehash: d295a04c27231b937ca552feb06628f857528e34
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/02/2022
ms.locfileid: "63575482"
---
# <a name="get-started-with-the-data-loss-prevention-alert-dashboard"></a>بدء استخدام لوحة معلومات تنبيهات منع فقدان البيانات

يمكن أن تتخذ سياسات منع فقدان البيانات (DLP) إجراءات حماية لمنع المشاركة غير المقصودة للعناصر الحساسة. عند اتخاذ إجراء على عنصر حساس، يمكن إعلامك عن طريق تكوين تنبيهات ل DLP. توضح لك هذه المقالة كيفية تعريف سياسات التنبيه الغنية المرتبطة ونهج منع فقدان البيانات (DLP). ستشاهد كيفية استخدام لوحة معلومات إدارة [تنبيهات DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) في مركز التوافق في Microsoft 365 لعرض التنبيهات والأحداث والبيانات التعريفية المقترنة بانتهاكات نهج DLP.<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a>

إذا كنت جديدا في تنبيهات DLP، يجب مراجعة [التعرف على لوحة معلومات تنبيهات منع فقدان البيانات](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>قبل البدء

قبل البدء، تأكد من أن لديك المتطلبات الأساسية الضرورية:

-   ترخيص لوحة معلومات إدارة تنبيهات DLP
-   ترخيص خيارات تكوين التنبيه
-   الأدوار

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>ترخيص لوحة معلومات إدارة تنبيهات DLP

يمكن لجميع المستأجرين المؤهلين Office 365 DLP الوصول إلى لوحة معلومات إدارة تنبيهات DLP. للبدء، يجب أن تكون مؤهلا للحصول على Office 365 DLP Exchange Online SharePoint عبر الإنترنت OneDrive for Business. لمزيد من المعلومات حول متطلبات الترخيص Office 365 DLP، راجع ما هي التراخيص التي توفر حقوق المستخدم للاستفادة [من الخدمة؟](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

سيشاهد العملاء الذين يستخدمون [DLP](endpoint-dlp-learn-about.md) نقطة النهاية [المؤهلين Teams DLP](dlp-microsoft-teams.md) تنبيهات نهج DLP لنقطة النهاية وتنبيهات نهج DLP Teams DLP في لوحة معلومات إدارة تنبيهات DLP.

تتوفر **ميزة معاينة** المحتوى فقط لهذه التراخيص:

- Microsoft 365 (E5)
- Office 365 (E5)
- إضافة التوافق المتقدم (E5)
- Microsoft 365 E5/A5 حماية المعلومات والحوكمة
- Microsoft 365 E5/توافق A5

### <a name="licensing-for-alert-configuration-options"></a>ترخيص خيارات تكوين التنبيه

تكوين **تنبيه** حدث واحد: يمكن أن تقوم المؤسسات التي لديها اشتراك E1 أو F1 أو G1 أو اشتراك E3 أو G3 بإنشاء سياسات تنبيه فقط عند تشغيل تنبيه في كل مرة يحدث فيها نشاط.

**تكوين تنبيه مجمع**: لتكوين سياسات تنبيه مجمعة استنادا إلى حد، يجب أن تكون أحد تكوينات الترخيص هذه:

- اشتراك E5 أو G5
- اشتراك E1 أو F1 أو G1 أو اشتراك E3 أو G3 الذي يتضمن إحدى الميزات التالية:
    - Office 365 المتقدمة للحماية من المخاطر 2
    - التوافق في Microsoft 365 E5
    - Microsoft 365 الوظائف الإضافية ل eDiscovery والتدقيق

### <a name="roles"></a>الأدوار

إذا كنت تريد عرض لوحة معلومات إدارة تنبيهات DLP أو تحرير خيارات تكوين التنبيه في نهج DLP، فيجب أن تكون عضوا في إحدى مجموعات الدور التالية:

- مسؤول التوافق
- مسؤول بيانات التوافق
- مسؤول الأمان
- عامل تشغيل الأمان
- قارئ الأمان

للوصول إلى لوحة معلومات إدارة تنبيهات DLP، ستحتاج إلى:

- إدارة التنبيهات

ومن هذين الدورين:

- إدارة توافق DLP
- View-Only إدارة توافق DLP

للوصول إلى ميزة معاينة المحتوى وميزات السياق والمحتوى الحساس المطابق، يجب أن تكون عضوا في:

- مجموعة الدور "عارض محتويات مستكشف المحتوى"

التي تم تعيين دور عارض محتوى تصنيف البيانات لها مسبقا.

### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم بالوصول.

فيما يلي قائمة بأدوار حماية البيانات في Microsoft (MIP) في المعاينة. لمعرفة المزيد حولها، راجع [الأدوار في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- مسؤول حماية المعلومات
- محلل حماية المعلومات
- حماية المعلوماتمحقق
- قارئ حماية المعلومات

فيما يلي قائمة مجموعات دور MIP التي تكون في المعاينة. لمعرفة المزيد حول، راجع [مجموعات الدور في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية المعلومات
- مسؤولو حماية المعلومات
- محللو حماية المعلومات
- الباحثون عن حماية المعلومات
- قراء حماية المعلومات

## <a name="dlp-alert-configuration"></a>تكوين تنبيه DLP

لمعرفة كيفية تكوين تنبيه في نهج DLP، راجع مكان [البدء بمنع فقدان البيانات](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> يتحكم تكوين نهج استبقاء سجل تدقيق المؤسسات في المدة التي يظل فيها التنبيه مرئيا في وحدة التحكم. لمزيد من المعلومات، راجع [إدارة سياسات استبقاء](audit-log-retention-policies.md#manage-audit-log-retention-policies) سجل التدقيق.

### <a name="aggregate-event-alert-configuration"></a>تكوين تنبيه الحدث التجميعي

إذا كانت المؤسسة مرخصة [للحصول على](#licensing-for-alert-configuration-options) خيارات تكوين تنبيه مجمعة، فسوف ترى هذه الخيارات عند إنشاء نهج DLP أو تحريره.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="لقطة شاشة تعرض خيارات لتقارير الأحداث للمستخدمين المؤهلين للحصول على خيارات تكوين تنبيه مجمعة." border="false":::

يسمح لك هذا التكوين بإعداد نهج لإنشاء تنبيه في كل مرة يتطابق فيها نشاط مع شروط النهج أو عند تجاوز حد معين، استنادا إلى عدد الأنشطة أو استنادا إلى حجم البيانات التي تم اقتناءها.

### <a name="single-event-alert-configuration"></a>تكوين تنبيه حدث واحد

إذا كانت المؤسسة مرخصة للحصول [](#licensing-for-alert-configuration-options)على خيارات تكوين تنبيه حدث واحد، سترى هذه الخيارات عند إنشاء نهج DLP أو تحريره. استخدم هذا الخيار لإنشاء تنبيه يتم رفعه في كل مرة تحدث فيها مطابقة لقاعدة DLP.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="لقطة شاشة تعرض خيارات لتقارير الأحداث للمستخدمين المؤهلين للحصول على خيارات تكوين تنبيه حدث واحد." border="false":::

## <a name="investigate-a-dlp-alert"></a>التحقق من تنبيه DLP

للعمل باستخدام لوحة معلومات إدارة تنبيهات DLP:

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365،</a> انتقل إلى **منع فقدان البيانات**.
2. حدد علامة **التبويب تنبيهات** لعرض لوحة معلومات تنبيهات DLP.
3. حدد تنبيها لرؤية التفاصيل:

:::image type="content" source="../media/alert-details.png" alt-text="لقطة شاشة تعرض تفاصيل التنبيه على لوحة معلومات إدارة تنبيهات DLP." border="false":::

4. حدد **علامة التبويب** الأحداث لعرض كل الأحداث المقترنة بالتنبيه. يمكنك اختيار حدث معين لعرض تفاصيله. للحصول على قائمة ببعض تفاصيل الحدث المتوفرة، راجع التعرف على لوحة معلومات تنبيهات منع فقدان [البيانات](dlp-alerts-dashboard-learn.md).
5. حدد **تفاصيل** لفتح صفحة **نظرة عامة** للتنبيه. توفر صفحة النظرة العامة ملخصا:
    1. لما حدث
    1. الأشخاص الذين ينفذون الإجراءات التي تسببت في تطابق النهج
    1. معلومات حول النهج المطابق والمزيد 

6. اختر **علامة التبويب** الأحداث للوصول إلى:
    1. المحتوى المحتوي
    1. أنواع المعلومات الحساسة متطابقة
    1. بيانات التعريف

7. حدد علامة **التبويب أنواع المعلومات الحساسة** لعرض تفاصيل حول أنواع المعلومات الحساسة التي تم الكشف عنها في المحتوى. تتضمن التفاصيل الثقة والعد والمحتوى الذي يتطابق مع نوع المعلومات الحساسة.

8. بعد التحقق من التنبيه، ارجع إلى علامة  التبويب نظرة عامة حيث يمكنك إدارة الفرز وإدارة ترتيب التنبيه وإضافة التعليقات.

- لرؤية محفوظات إدارة سير العمل، اختر **سجل الإدارة**.
- بعد اتخاذ الإجراء المطلوب للتنبيه، قم بتعيين حالة التنبيه إلى **تم الحل**.

## <a name="see-also"></a>راجع أيضًا

- [التعرف على تنبيهات منع فقدان البيانات لوحة معلومات التنبيهات](dlp-alerts-dashboard-learn.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
