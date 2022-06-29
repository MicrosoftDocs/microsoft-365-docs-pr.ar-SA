---
title: أحدث الميزات في Microsoft Defender لـ Office 365
description: تعرف على الميزات والوظائف الجديدة المتوفرة في أحدث إصدار من Microsoft Defender لـ Office 365.
keywords: أحدث الميزات في Microsoft Defender لـ Office 365، و ga، والمتاحة بشكل عام، والقدرات، والمتاحة، والجديدة
search.appverid: met150
ms.sitesec: library
ms.pagetype: security
f1.keywords: NOCSH
ms.author: tracyp
author: msfttracyp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: conceptual
ms.custom: seo-marvel-apr2020
ms.reviewer: vippand
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 37819c0f5ea458a4f5ee25b3536e3688aabd1882
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486896"
---
# <a name="whats-new-in-microsoft-defender-for-office-365"></a>أحدث الميزات في Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على:**

- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تسرد هذه المقالة ميزات جديدة في أحدث إصدار من Microsoft Defender لـ Office 365. تتم الإشارة إلى الميزات الموجودة حاليا في المعاينة ب **(معاينة).**

تعرف على المزيد من خلال مشاهدة [هذا الفيديو](https://www.youtube.com/watch?v=Tdz6KfruDGo&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=3).

لمزيد من المعلومات حول أحدث الميزات في منتجات أمان Microsoft Defender الأخرى، راجع:

- [الجديد في Microsoft 365 Defender](../defender/whats-new.md)
- [ما الجديد في Microsoft Defender لنقطة النهاية](../defender-endpoint/whats-new-in-microsoft-defender-endpoint.md)
- [ما الجديد في Microsoft Defender for Identity](/defender-for-identity/whats-new)
- [ما الجديد في Microsoft Cloud App Security](/cloud-app-security/release-notes)


## <a name="june-2022"></a>يونيو 2022

- [يسمح الانتحال باستخدام إرسال المسؤول](allow-block-email-spoof.md#use-admin-submission-in-microsoft-365-defender): إنشاء إدخالات المرسلين المخادعة المسموح بها باستخدام قائمة السماح/الحظر للمستأجر.

- [يسمح الانتحال باستخدام إرسال المسؤول](allow-block-email-spoof.md#create-impersonated-sender-entries): تسمح الإضافة للمرسلين المنتحلين باستخدام صفحة عمليات الإرسال في Microsoft 365 Defender.

- [عرض عمليات إرسال المسؤول المحولة من إرسال المستخدم](admin-submission.md#convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission): قم بتكوين علبة البريد المخصصة لاعتراض الرسائل التي أبلغ عنها المستخدم دون إرسال الرسائل إلى Microsoft للتحليل.

- [عرض التنبيه المقترن بإرسالات المستخدم والمسؤول](admin-submission.md#view-associated-alert-for-user-and-admin-email-submissions): عرض التنبيه المقابل لكل رسالة تصيد احتيالي تم الإبلاغ عنها من قبل المستخدم وإرسال البريد الإلكتروني للمسؤول. 

- [حماية الانتحال القابلة للتكوين للمستخدمين والمجالات المخصصة وزيادة النطاق داخل النهج المحددة مسبقا](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/configurable-impersonation-protection-and-scope-for-preset/ba-p/3294459):
  - (اختر إلى) تطبيق نهج مقيدة/قياسية محددة مسبقا على المؤسسة بأكملها وتجنب عناء تحديد مستخدمين أو مجموعات أو مجالات مستلمين معينين، ومن ثم تأمين جميع مستخدمي مؤسستك المستلمين. 
  - تكوين إعدادات حماية الانتحال للمستخدمين المخصصين والمجالات المخصصة ضمن نهج مقيدة/قياسية محددة مسبقا وحماية المستخدمين المستهدفين والمجال المستهدف تلقائيا من هجمات الانتحال.

- [تبسيط تجربة العزل (الجزء الثاني) في Microsoft 365 Defender ل office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience-part-two/ba-p/3354687): يميز الميزات الإضافية لجعل تجربة العزل أكثر سهولة في الاستخدام.

## <a name="april-2022"></a>أبريل 2022

- [تقديم جدول URLClickEvents في التتبع المتقدم Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/introducing-the-urlclickevents-table-in-advanced-hunting-with/ba-p/3295096): تقديم جدول UrlClickEvents في التتبع المتقدم مع Microsoft Defender لـ Office 365.
- [تحسينات معالجة البريد الإلكتروني اليدوي](/microsoft-365/security/office-365-security/remediate-malicious-email-delivered-office-365): إحضار إجراءات إزالة البريد الإلكتروني اليدوية التي تم اتخاذها في Microsoft Defender لـ Office 365 إلى مركز الصيانة الموحد Microsoft 365 Defender (M365D) باستخدام تحقيق جديد يركز على الإجراء.
 
## <a name="march-2022"></a>مارس 2022

- [تبسيط تجربة الإرسال في Microsoft Defender لـ Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/streamlining-the-submissions-experience-in-microsoft-defender/ba-p/3152080): تقديم عملية الإرسال الموحدة والمبسطة الجديدة لتبسيط تجربتك.

## <a name="january-2022"></a>يناير 2022

- [تجارب التتبع والتحقيق المحدثة Microsoft Defender لـ Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/updated-hunting-and-investigation-experiences-for-microsoft/ba-p/3002015): تقديم لوحة ملخص البريد الإلكتروني للتجارب في Defender لـ Office 365، بالإضافة إلى تحديثات تجربة مستكشف التهديدات والكشف في الوقت الحقيقي.

## <a name="october-2021"></a>أكتوبر 2021

- [تحسين DKIM للتسليم المتقدم](configure-advanced-delivery.md): تمت إضافة دعم لإدخال مجال DKIM كجزء من تكوين محاكاة التصيد الاحتيالي لجهة خارجية.
- [آمن بشكل افتراضي](secure-by-default.md): تأمين موسع بشكل افتراضي لقواعد تدفق بريد Exchange (المعروفة أيضا بقواعد النقل).

## <a name="september-2021"></a>سبتمبر 2021

- [تحسين تجربة إعداد التقارير في Defender لـ Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/improving-the-reporting-experience-in-microsoft-defender-for/ba-p/2760898)
- [نهج العزل](quarantine-policies.md): يمكن للمسؤولين تكوين التحكم متعدد المستويات للوصول إلى المستلم إلى الرسائل المعزولة وتخصيص إعلامات البريد العشوائي للمستخدم النهائي.
  - [فيديو لتجربة المسؤول](https://youtu.be/vnar4HowfpY)
  - [فيديو لتجربة المستخدم النهائي](https://youtu.be/s-vozLO43rI)
  - يتم وصف القدرات الجديدة الأخرى القادمة إلى تجربة العزل في منشور المدونة هذا: [تبسيط تجربة العزل](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/simplifying-the-quarantine-experience/ba-p/2676388).
- تبدأ إعادة توجيه المدخل بشكل افتراضي، مع إعادة توجيه المستخدمين من الأمان & التوافق إلى Microsoft 365 Defender<https://security.microsoft.com>. لمزيد من المعلومات حول ذلك، راجع: [إعادة توجيه الحسابات من Office 365 مركز التوافق & الأمان إلى Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection)

## <a name="august-2021"></a>أغسطس 2021

- [مسؤول مراجعة الرسائل التي تم الإبلاغ عنها](admin-review-reported-message.md): يمكن للمسؤولين الآن إرسال الرسائل التي تم قالبها مرة أخرى إلى المستخدمين النهائيين بعد مراجعة الرسائل التي تم الإبلاغ عنها. يمكن تخصيص القوالب لمؤسستك واستنادا إلى حكم المسؤول أيضا.
- [تسمح الإضافة في قائمة السماح/الحظر للمستأجر](manage-tenant-allows.md): يمكنك الآن إضافة إدخالات السماح إلى قائمة السماح/الحظر للمستأجر إذا تم إرسال الرسالة المحظورة كجزء من عملية إرسال المسؤول. استنادا إلى طبيعة الكتلة، ستتم إضافة عنوان URL والملف و/أو سماح المرسل المرسل إلى قائمة السماح/الحظر للمستأجر. في معظم الحالات، تتم إضافة السماح لمنح النظام بعض الوقت والسماح به بشكل طبيعي إذا تضمن ذلك. في بعض الحالات، تدير Microsoft السماح لك.

## <a name="july-2021"></a>يوليو 2021

- [تحسينات تحليل البريد الإلكتروني في التحقيقات التلقائية](email-analysis-investigations.md)
- [التسليم المتقدم](configure-advanced-delivery.md): تقديم إمكانية جديدة لتكوين تسليم عمليات محاكاة التصيد الاحتيالي التابعة لجهات خارجية للمستخدمين والرسائل غير التصفية إلى علب بريد عمليات الأمان.
- [ارتباطات آمنة ل Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams)
- نهج تنبيه جديدة للسيناريوهات التالية: علب البريد المخترقة، التصيد الاحتيالي للنماذج، رسائل البريد الضارة التي يتم تسليمها بسبب عمليات التجاوز وتقريب ZAP
  - نشاط إعادة توجيه البريد الإلكتروني المريب
  - المستخدم مقيد من مشاركة النماذج وجمع الاستجابات
  - تم حظر النموذج بسبب محاولة التصيد الاحتيالي المحتملة
  - تم وضع علامة على النموذج وتأكيده على أنه تصيد احتيالي
  - [نهج التنبيه الجديدة ل ZAP](../../compliance/new-defender-alert-policies.md)
- يتم الآن دمج التنبيهات Microsoft Defender لـ Office 365 في Microsoft 365 Defender - [Microsoft 365 Defender "قائمة انتظار التنبيهات الموحدة" و"قائمة انتظار التنبيهات الموحدة"](../defender/investigate-alerts.md)
- يتم الآن دمج [علامات المستخدم](user-tags.md) في تجارب التنبيه Microsoft Defender لـ Office 365، بما في ذلك: قائمة انتظار التنبيهات والتفاصيل في Office 365 الأمان & Compliance، وتحديد نطاق نهج التنبيه المخصصة لعلامات المستخدم لإنشاء نهج تنبيه مستهدفة.
  - تتوفر العلامات أيضا في قائمة انتظار التنبيهات الموحدة في مدخل Microsoft 365 Defender (Microsoft Defender لـ Office 365 الخطة 2)

## <a name="june-2021"></a>يونيو 2021

- إعداد تلميح أمان الاتصال الأول الجديد ضمن نهج مكافحة التصيد الاحتيالي. يظهر تلميح الأمان هذا عندما يتلقى المستلمون أولا بريدا إلكترونيا من مرسل أو لا يتلقون غالبا بريدا إلكترونيا من مرسل. لمزيد من المعلومات حول هذا الإعداد وكيفية تكوينه، راجع المقالات التالية:
  - [تلميح أمان الاتصال الأول](set-up-anti-phishing-policies.md#first-contact-safety-tip)
  - [تكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md)
  - [تكوين نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](configure-mdo-anti-phishing-policies.md)

## <a name="aprilmay-2021"></a>أبريل/مايو 2021

- [صفحة كيان البريد الإلكتروني](mdo-email-entity-page.md): طريقة عرض موحدة من 360 درجة لرسالة بريد إلكتروني مع معلومات ثرية حول التهديدات والمصادقة والكشف وتفاصيل المتابعة وتجربة معاينة بريد إلكتروني جديدة.
- [Office 365 Management API](/office/office-365-management-api/office-365-management-activity-api-schema#email-message-events): التحديثات إلى EmailEvents (RecordType 28) لإضافة إجراء التسليم ومواقع التسليم الأصلية وأحدثها وتفاصيل الكشف المحدثة.
- [تحليلات التهديدات Defender لـ Office 365](/microsoft-365/security/defender/threat-analytics): عرض الجهات الفاعلة النشطة للمخاطر والتقنيات الشائعة وأسطح الهجوم، بالإضافة إلى تقارير واسعة من باحثي Microsoft حول الحملات الجارية.

## <a name="februarymarch-2021"></a>فبراير/مارس 2021

- تكامل معرف التنبيه (البحث باستخدام معرف التنبيه والتنقل Alert-Explorer) في [تجارب التتبع](threat-explorer.md)
- زيادة حدود تصدير السجلات من 9990 إلى 200000 في [تجارب التتبع](threat-explorer.md)
- توسيع نطاق استبقاء بيانات المستكشف (والكشف في الوقت الحقيقي) وحد البحث للمستأجرين التجريبيين من 7 (الحد السابق) إلى 30 يوما في [تجارب التتبع](threat-explorer.md)
- تسمى محاور التتبع الجديدة **المجال الذي تم انتحاله** **والمستخدم الذي تم انتحاله** داخل المستكشف (والكشف في الوقت الحقيقي) للبحث عن هجمات انتحال ضد المستخدمين أو المجالات المحمية. لمزيد من المعلومات، راجع [التفاصيل](threat-explorer.md#view-phishing-emails-sent-to-impersonated-users-and-domains). (Microsoft Defender لـ Office 365 الخطة 1 أو الخطة 2)

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender لـ Office 365 الخطة 1 والخطة 2

هل تعلم أن Microsoft Defender لـ Office 365 متوفر في خطتين؟ [تعرف على المزيد حول ما تتضمنه كل خطة](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="see-also"></a>راجع أيضًا

- [خارطة طريق Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap)
- [وصف الخدمة Microsoft Defender لـ Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)
