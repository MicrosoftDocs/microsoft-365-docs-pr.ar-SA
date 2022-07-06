---
title: بدء استخدام لوحة معلومات تنبيهات DLP
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
description: ابدأ في تحديد التنبيهات وإدارتها لنهج منع فقدان البيانات.
ms.openlocfilehash: de980fadbc6b6091a0257c032dacab4220704f62
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625446"
---
# <a name="get-started-with-the-data-loss-prevention-alerts-dashboard"></a>بدء استخدام لوحة معلومات تنبيهات منع فقدان البيانات

يمكن أن تتخذ نهج تفادي فقدان البيانات في Microsoft Purview (DLP) إجراءات حماية لمنع المشاركة غير المقصودة للعناصر الحساسة. عند اتخاذ إجراء على عنصر حساس، يمكن إعلامك عن طريق تكوين تنبيهات ل DLP. توضح لك هذه المقالة كيفية تعريف نهج التنبيه الغنية المرتبطة بنهج منع فقدان البيانات (DLP). سترى كيفية استخدام [لوحة معلومات إدارة تنبيهات DLP](https://compliance.microsoft.com/datalossprevention?viewid=dlpalerts) في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a> لعرض التنبيهات والأحداث وبيانات التعريف المقترنة لانتهاكات نهج DLP.

إذا كنت جديدا على تنبيهات DLP، يجب مراجعة [Learn حول لوحة معلومات تنبيهات منع فقدان البيانات](dlp-alerts-dashboard-learn.md)

## <a name="before-you-begin"></a>قبل البدء

قبل البدء، تأكد من أن لديك المتطلبات الأساسية الضرورية:

-   ترخيص لوحة معلومات إدارة تنبيهات DLP
-   ترخيص لخيارات تكوين التنبيه
-   ادوار

### <a name="licensing-for-the-dlp-alert-management-dashboard"></a>ترخيص لوحة معلومات إدارة تنبيهات DLP

يمكن لجميع المستأجرين المؤهلين ل DLP الوصول إلى لوحة معلومات إدارة تنبيهات DLP. للبدء، يجب أن تكون مؤهلا ل Microsoft Purview DLP Exchange Online وSharePoint Online OneDrive for Business. لمزيد من المعلومات حول متطلبات الترخيص ل DLP، راجع [التراخيص التي توفر الحقوق للمستخدم للاستفادة من الخدمة؟](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#which-licenses-provide-the-rights-for-a-user-to-benefit-from-the-service-16).

سيرى العملاء الذين يستخدمون [DLP نقطة النهاية](endpoint-dlp-learn-about.md) المؤهلين ل [Teams DLP](dlp-microsoft-teams.md) تنبيهات نهج DLP نقطة النهاية وتنبيهات نهج DLP Teams في لوحة معلومات إدارة تنبيهات DLP.

تتوفر ميزة **معاينة المحتوى** لهذه التراخيص فقط:

- Microsoft 365 (E5)
- Office 365 (E5)
- إضافة التوافق المتقدم (E5) على
- Microsoft 365 E5/A5 حماية البيانات والحوكمة
- توافق Microsoft 365 E5/A5

### <a name="licensing-for-alert-configuration-options"></a>ترخيص لخيارات تكوين التنبيه

**تكوين تنبيه حدث واحد**: يمكن للمؤسسات التي لديها اشتراك E1 أو F1 أو G1 أو اشتراك E3 أو G3 إنشاء نهج تنبيه فقط حيث يتم تشغيل تنبيه في كل مرة يحدث فيها نشاط.

**تكوين التنبيه المجمع**: لتكوين نهج التنبيه التجميعية استنادا إلى حد، يجب عليك أحد تكوينات الترخيص هذه:

- اشتراك E5 أو G5
- اشتراك E1 أو F1 أو G1 أو اشتراك E3 أو G3 يتضمن إحدى الميزات التالية:
    - Office 365 الخطة 2 المتقدمة للحماية من التهديدات
    - التوافق في Microsoft 365 E5
    - ترخيص الوظيفة الإضافية Microsoft 365 eDiscovery و Audit

### <a name="roles"></a>ادوار

إذا كنت ترغب في عرض لوحة معلومات إدارة تنبيهات DLP أو تحرير خيارات تكوين التنبيه في نهج DLP، يجب أن تكون عضوا في إحدى مجموعات الأدوار هذه:

- مسؤول التوافق
- مسؤول بيانات التوافق
- مسؤول الأمان
- عامل تشغيل الأمان
- قارئ الأمان

للوصول إلى لوحة معلومات إدارة تنبيهات DLP، تحتاج إلى:

- إدارة التنبيهات

واثنين من هذين الدورين:

- DLP Compliance Management
- View-Only DLP Compliance Management

للوصول إلى ميزة معاينة المحتوى والمحتوى الحساس المطابق وميزات السياق، يجب أن تكون عضوا في:

- مجموعة دور عارض محتوى مستكشف المحتوى

الذي يحتوي على دور عارض محتوى تصنيف البيانات المعين مسبقا.

### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم في الوصول.

فيما يلي قائمة بالأدوار القابلة للتطبيق الموجودة في المعاينة. لمعرفة المزيد عنها، راجع ["الأدوار" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- حماية البيانات مسؤول
- محلل حماية البيانات
- حماية البيانات المحقق
- قارئ حماية البيانات

فيما يلي قائمة بمجموعات الأدوار القابلة للتطبيق الموجودة في المعاينة. لمعرفة المزيد حولها، راجع [مجموعات الأدوار في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية البيانات
- مسؤولو حماية البيانات
- حماية البيانات المحللين
- المحققون حماية البيانات
- قارئات حماية البيانات

## <a name="dlp-alert-configuration"></a>تكوين تنبيه DLP

لمعرفة كيفية تكوين تنبيه في نهج DLP، راجع [من أين تبدأ بمنع فقدان البيانات](create-test-tune-dlp-policy.md#where-to-start-with-data-loss-prevention).

> [!IMPORTANT]
> يتحكم تكوين نهج استبقاء سجل التدقيق الخاص بك في المدة التي يظل فيها التنبيه مرئيا في وحدة التحكم. راجع [إدارة نهج استبقاء سجل التدقيق](audit-log-retention-policies.md#manage-audit-log-retention-policies) لمزيد من المعلومات.

### <a name="aggregate-event-alert-configuration"></a>تجميع تكوين تنبيه الحدث

إذا كانت مؤسستك مرخصة [لخيارات تكوين التنبيه المجمعة](#licensing-for-alert-configuration-options)، فسترى هذه الخيارات عند إنشاء نهج DLP أو تحريره.

:::image type="content" source="../media/incident-reports-options-aggregated-alerts.png" alt-text="لقطة شاشة تعرض خيارات تقارير الحوادث للمستخدمين المؤهلين لخيارات تكوين التنبيه المجمعة." border="false":::

يسمح لك هذا التكوين بإعداد نهج لإنشاء تنبيه في كل مرة يتطابق فيها النشاط مع شروط النهج أو عند تجاوز حد معين، استنادا إلى عدد الأنشطة أو استنادا إلى حجم البيانات التي تم حذفها.

### <a name="single-event-alert-configuration"></a>تكوين تنبيه حدث واحد

إذا كانت مؤسستك مرخصة [لخيارات تكوين تنبيه حدث واحد](#licensing-for-alert-configuration-options)، فسترى هذه الخيارات عند إنشاء نهج DLP أو تحريره. استخدم هذا الخيار لإنشاء تنبيه يتم رفعه في كل مرة تتطابق فيها قاعدة DLP.

:::image type="content" source="../media/incident-reports-options-single-event-alerts.png" alt-text="لقطة شاشة تعرض خيارات تقارير الحوادث للمستخدمين المؤهلين لخيارات تكوين تنبيه حدث واحد." border="false":::

## <a name="investigate-a-dlp-alert"></a>التحقيق في تنبيه DLP

للعمل مع لوحة معلومات إدارة تنبيهات DLP:

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a>، انتقل إلى **منع فقدان البيانات**.
2. حدد علامة التبويب **«Alerts** » لعرض لوحة معلومات تنبيهات DLP.
3. حدد تنبيها للاطلاع على التفاصيل:

:::image type="content" source="../media/alert-details.png" alt-text="لقطة شاشة تعرض تفاصيل التنبيه على لوحة معلومات إدارة تنبيهات DLP." border="false":::

4. حدد علامة التبويب **"أحداث** " لعرض كافة الأحداث المقترنة بالتنبيه. يمكنك اختيار حدث معين لعرض تفاصيله. للحصول على قائمة ببعض تفاصيل الحدث المتوفرة، راجع، [تعرف على لوحة معلومات تنبيهات منع فقدان البيانات](dlp-alerts-dashboard-learn.md).
5. حدد **التفاصيل** لفتح صفحة **النظرة العامة** للتنبيه. توفر صفحة النظرة العامة ملخصا:
    1. ما حدث
    1. الشخص الذي نفذ الإجراءات التي تسببت في تطابق النهج
    1. معلومات حول النهج المطابق، والمزيد 

6. اختر علامة التبويب **"أحداث** " للوصول إلى:
    1. المحتوى المتضمن
    1. أنواع المعلومات الحساسة المتطابقة
    1. بيانات التعريف

7. حدد علامة التبويب **"أنواع المعلومات الحساسة** " لعرض تفاصيل حول أنواع المعلومات الحساسة المكتشفة في المحتوى. تتضمن التفاصيل الثقة والعد والمحتوى الذي يطابق نوع المعلومات الحساسة.

8. بعد التحقق من التنبيه، عد إلى علامة التبويب **"نظرة عامة** " حيث يمكنك إدارة الفرز وإدارة ترتيب التنبيه وإضافة تعليقات.

- للاطلاع على محفوظات إدارة سير العمل، اختر **سجل الإدارة**.
- بعد اتخاذ الإجراء المطلوب للتنبيه، قم بتعيين حالة التنبيه إلى **"تم الحل**".

## <a name="see-also"></a>راجع أيضًا

- [تعرف على تنبيهات منع فقدان البيانات ولوحة معلومات التنبيهات](dlp-alerts-dashboard-learn.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
