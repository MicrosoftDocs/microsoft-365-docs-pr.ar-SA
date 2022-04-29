---
title: الخصوصية والبيانات الشخصية
description: تفاصيل البيانات التي تم تجميعها وتخزينها واستخدامها من قبل الخدمة
keywords: القانون العام لحماية البيانات (GDPR) والاستبقاء والحذف والتخزين والاستبقاء والمعالجة والأمان والتدقيق
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
manager: dougeby
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.topic: article
audience: Admin, ITPro
ms.localizationpriority: medium
ms.openlocfilehash: e7c9912e3890d9b13003c7f3264490f67c4fc305
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128335"
---
# <a name="privacy"></a>الخصوصية

Microsoft Managed Desktop هي خدمة تكنولوجيا المعلومات كخدمة (ITaaS) لعملاء السحابة للمؤسسات المصممة للحفاظ على أجهزة Windows للموظفين منشورة ومحدثة.

كما يوفر إدارة خدمة تكنولوجيا المعلومات والعمليات، ويراقب الأمان والاستجابة للحوادث، ودعم المستخدم. توفر هذه المقالة مزيدا من التفاصيل حول النظام الأساسي للبيانات وتوافق الخصوصية Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Managed Desktop مصادر البيانات والغرض منها

يوفر Microsoft Managed Desktop خدمته لعملاء المؤسسات، ويدير الأجهزة المسجلة للعملاء بشكل صحيح باستخدام بيانات من مصادر مختلفة.

تتضمن هذه المصادر Azure Active Directory و Microsoft Intune وMicrosoft Windows 10 Microsoft Defender لنقطة النهاية. وهي توفر عرضا شاملا للأجهزة التي يديرها Microsoft Managed Desktop. تستخدم الخدمة أيضا هذه خدمات Microsoft لتمكين Microsoft Managed Desktop لتوفير قدرات ITaaS:

| مصدر البيانات | الغرض |
| ------ | ------ |
| [Microsoft Windows 10 Enterprise](/windows/windows-10/) | إدارة تجربة إعداد الجهاز، وإدارة الاتصالات بخدمات أخرى، والدعم التشغيلي لمحترفي تكنولوجيا المعلومات. |
| [Windows Update للأعمال](/windows/deployment/update/waas-manage-updates-wufb) | يستخدم Windows 10 Enterprise البيانات التشخيصية لتوفير معلومات إضافية حول تحديث Windows 10. |
| [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) | إدارة الأجهزة والحفاظ على أمان بياناتك. تندرج مصادر البيانات التالية ضمن إدارة نقاط النهاية من Microsoft:<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/): مصادقة جميع حسابات المستخدمين وتحديد هويتها.</li><li>[Microsoft Intune](/mem/intune/): توزيع تكوينات الجهاز وإدارة الأجهزة وإدارة التطبيقات.</li><li>[تحليلات نقطة النهاية](/mem/analytics/overview): التحليلات التحليلية حول استخدام الجهاز والتطبيق.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot): توفير الجهاز ونشره.</li><li>[Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/): يوفر خدمات الأمان مثل مراقبة أمان الجهاز وبيانات التحليل الذكي للأمان.</li></ul>
| [جهاز سطح المكتب المدار من Microsoft](https://endpoint.microsoft.com/#home) | البيانات التي يوفرها العميل أو التي تم إنشاؤها بواسطة الخدمة أثناء تشغيل الخدمة. |
| [تطبيقات Microsoft 365 للمؤسسة](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| إدارة Microsoft 365 Apps.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Managed Desktop عملية البيانات وتخزينها

تعتمد Microsoft Managed Desktop على بيانات من منتجات وخدمات Microsoft متعددة لتوفير خدمتها لعملاء المؤسسات.

لحماية الأجهزة المسجلة وصيانتها، نقوم بمعالجة البيانات ونسخها من هذه الخدمات إلى Microsoft Managed Desktop. عندما نعالج البيانات، نتبع التوجيهات الموثقة التي تقدمها، كما هو مشار إليه في [شروط الخدمات عبر الإنترنت](https://www.microsoft.com/licensing/product-licensing/products) [وبيان خصوصية Microsoft](https://privacy.microsoft.com/privacystatement).

تتضمن مهام معالج Microsoft Managed Desktop ضمان السرية والأمان والمرونة المناسبة. تستخدم Microsoft Managed Desktop إجراءات إضافية للخصوصية والأمان لضمان التعامل السليم مع بيانات التعريف الشخصية.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Managed Desktop تخزين البيانات وموقع فريق العمل

Microsoft Managed Desktop تخزن بياناتها في مراكز بيانات Azure في الولايات المتحدة.

البيانات الشخصية التي يحصل عليها Microsoft Managed Desktop والخدمات الأخرى مطلوبة للحفاظ على تشغيل الخدمة. إذا تمت إزالة جهاز من Microsoft Managed Desktop، فإننا نحتفظ بالبيانات الشخصية لمدة 30 يوما كحد أقصى. ومع ذلك، يتم تخزين بيانات التنبيه، التي تم جمعها بواسطة Microsoft Defender لنقطة النهاية، لمدة 180 يوما لأغراض الأمان. لمزيد من المعلومات حول الاحتفاظ بالبيانات، راجع [استبقاء البيانات وحذفها وإتلافها في Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

توجد Microsoft Managed Desktop فرق العمليات الهندسية والعمليات الأمنية في الولايات المتحدة والهند و رومانيا.

### <a name="microsoft-windows-10-diagnostic-data"></a>بيانات تشخيصية Windows 10 Microsoft

تستخدم Microsoft Managed Desktop [Windows 10 بيانات تشخيص محسنة](/windows/privacy/windows-diagnostic-data) للحفاظ على أمان Windows وتحديثها واستكشاف الأخطاء وإصلاحها وإجراء تحسينات على المنتجات.

يتضمن إعداد البيانات التشخيصية المحسن معلومات أكثر تفصيلا حول الأجهزة المسجلة في Microsoft Managed Desktop وإعداداتها وقدراتها وحالة الجهاز. عند تحديد البيانات التشخيصية المحسنة، يتم جمع البيانات، بما في ذلك البيانات التشخيصية المطلوبة. لمزيد من المعلومات، راجع ["تغييرات Windows جمع البيانات التشخيصية](/windows/privacy/changes-to-windows-diagnostic-data-collection)" حول إعداد البيانات التشخيصية Windows 10 وجمع البيانات.

ستتغير مصطلحات البيانات التشخيصية في الإصدارات المستقبلية من Windows. تلتزم Microsoft Managed Desktop بمعالجة البيانات التي تحتاجها الخدمة فقط. في حين أن هذا يعني أن مستوى التشخيص سيتغير إلى **اختياري**، Microsoft Managed Desktop سينفذ نهج التشخيص المحدودة لضبط جمع البيانات التشخيصية المطلوبة للخدمة. لمزيد من المعلومات، راجع [التغييرات التي يتم إجراؤها على Windows جمع البيانات التشخيصية](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Managed Desktop تعالج فقط البيانات على مستوى النظام وتخزنها من Windows 10 البيانات التشخيصية الاختيارية التي تنشأ من الأجهزة المسجلة مثل موثوقية التطبيق والجهاز ومعلومات الأداء. لا تعالج Microsoft Managed Desktop البيانات الشخصية للعملاء وتخزنها مثل الدردشة ومحفوظات المستعرض أو الصوت أو النص أو بيانات الكلام.

لمزيد من المعلومات حول جمع البيانات التشخيصية ل Microsoft Windows 10، راجع قسم ["أين نخزن البيانات الشخصية ونعالجها](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule)" في بيان خصوصية Microsoft.

### <a name="microsoft-windows-update-for-business"></a>Microsoft Windows Update للأعمال

يستخدم Microsoft Windows Update للأعمال بيانات من تشخيصات Windows لتحليل حالة التحديث وحالات الفشل. تستخدم Microsoft Managed Desktop هذه البيانات وتستخدمها للتخفيف من المشاكل وحلها لضمان تحديث جميع الأجهزة المسجلة استنادا إلى إيقاع تحديث معرف مسبقا.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

يتم تخزين تحديد البيانات المستخدمة من قبل Microsoft Managed Desktop بواسطة Azure Active Directory (Azure AD) في موقع جغرافي. يستند الموقع الجغرافي إلى الموقع الذي توفره المؤسسة عند الاشتراك في Microsoft خدمات الإنترنت، مثل Microsoft Apps للمؤسسة وAzure. لمزيد من المعلومات حول مكان وجود بياناتك Azure AD، راجع [Azure Active Directory - أين توجد بياناتك؟](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune جمع البيانات ومعالجتها ومشاركتها Microsoft Managed Desktop لدعم العمليات والخدمات التجارية. لمزيد من المعلومات حول البيانات التي تم جمعها في Intune، راجع [جمع البيانات في Intune](/mem/intune/protect/privacy-data-collect)

لمزيد من المعلومات حول مواقع البيانات Microsoft Intune، راجع [مكان تخزين بيانات عميل Microsoft 365](/microsoft-365/enterprise/o365-data-locations). تحترم Intune تحديدات موقع التخزين التي أجراها المسؤول لبيانات العميل.

### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

Microsoft Defender لنقطة النهاية جمع المعلومات وتخزينها للأجهزة المسجلة في Microsoft Managed Desktop لأغراض الإدارة والتعقب وإعداد التقارير. تتضمن المعلومات التي تم جمعها ما يلي:

- بيانات الملف (مثل أسماء الملفات وحجمها وتجزئةها)
- معالجة البيانات (تشغيل العمليات، تجزئة)
- بيانات التسجيل
- بيانات اتصال الشبكة
- تفاصيل الجهاز (مثل معرفات الجهاز وأسماء الأجهزة وإصدار نظام التشغيل)

لمزيد من المعلومات حول مواقع تجميع البيانات وتخزينها في Microsoft Defender لنقطة النهاية، راجع [Microsoft Defender لنقطة النهاية تخزين البيانات والخصوصية](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps للمؤسسة

Microsoft 365 Apps للمؤسسة جمع البيانات ومشاركتها مع Microsoft Managed Desktop للتأكد من أن هذه التطبيقات محدثة بأحدث إصدار. تستند هذه التحديثات إلى قنوات تحديث معرفة مسبقا تديرها Microsoft Managed Desktop. لمزيد من المعلومات حول مواقع تجميع البيانات وتخزينها في Microsoft 365 Apps، راجع [Microsoft Defender لنقطة النهاية تخزين البيانات والخصوصية](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>إعلام بتغيير البيانات الرئيسية

يتبع Microsoft Managed Desktop عملية التحكم في التغيير كما هو موضح في إطار اتصال الخدمة لدينا.

نقوم بإعلام العملاء من خلال مركز رسائل Microsoft 365، ومدخل مسؤول Microsoft Managed Desktop بكل من الحوادث الأمنية والتغييرات الرئيسية في الخدمة.

تعتبر التغييرات في أنواع البيانات التي تم جمعها ومكان تخزينها تغييرا ماديا. سنقدم إشعارا متقدما بهذا التغيير لمدة 30 يوما على الأقل كما هو الحال في الممارسة القياسية لمنتجات وخدمات Microsoft 365. لمزيد من المعلومات، راجع [تغييرات الخدمة والاتصال](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>التوافق

وقد خضع Microsoft Managed Desktop لعمليات تدقيق خارجية واحصل على مجموعة شاملة من عروض الامتثال. يمكنك العثور على مزيد من المعلومات في [Compliance](/microsoft-365/managed-desktop/intro/compliance). تتوفر تقارير التدقيق للتنزيل في Microsoft [Service Trust Portal](https://aka.ms/stp)، الذي يعمل كمستودع مركزي ل Microsoft Enterprise Online Services. يتم سرد Microsoft Managed Desktop ضمن هذه المستندات ضمن فئة "المراقبة والإدارة".

### <a name="data-subject-requests"></a>طلبات موضوع البيانات

يتبع Microsoft Managed Desktop القانون العام لحماية البيانات (GDPR) ولوائح خصوصية CCPA، والتي تمنح مواضيع البيانات حقوقا محددة لبياناتهم الشخصية.

وتشمل هذه الحقوق ما يلي:

- الحصول على نسخ من البيانات الشخصية
- طلب تصحيحات له
- تقييد معالجتها
- حذفه
- تلقيه بتنسيق إلكتروني بحيث يمكن نقله إلى وحدة تحكم أخرى.

لمزيد من المعلومات العامة حول طلبات موضوع البيانات (DSRs)، راجع [طلبات موضوع البيانات و GDPR وCCPA](/compliance/regulatory/gdpr-data-subject-requests).

لممارسة طلبات موضوع البيانات على البيانات التي تم جمعها بواسطة نظام إدارة حالة Microsoft Managed Desktop، راجع طلبات موضوع البيانات التالية:

| طلبات موضوع البيانات | الوصف |
| ------ | ------ |
| بيانات من تنبيهات Microsoft Defender لنقطة النهاية | يمكن لمسؤول الأمان طلب حذف البيانات الشخصية المتعلقة بتنبيهات Microsoft Defender لنقطة النهاية أو استخراجها عن طريق إرسال طلب تقرير في [مدخل المسؤول](https://aka.ms/memadmin). <br><br> قم بتوفير المعلومات التالية: <br><ul><li>نوع الطلب: تغيير الطلب</li><li>الفئة: الأمان</li><li>الفئة الفرعية: أخرى</li><li>الوصف: توفير أسماء الأجهزة ذات الصلة.</li></ul> |
| بيانات من طلبات دعم Microsoft Managed Desktop | يمكن لمسؤول تكنولوجيا المعلومات طلب حذف طلبات الدعم ذات الصلة بالبيانات الشخصية أو استخراجها عن طريق إرسال طلب تقرير في [مدخل المسؤول](https://aka.ms/memadmin). <br><br> قم بتوفير المعلومات التالية: <ul><li>نوع الطلب: تغيير الطلب</li><li>الفئة: الأمان</li><li>الفئة الفرعية: أخرى</li><li>الوصف: توفير أسماء الأجهزة أو أسماء المستخدمين ذات الصلة.</li></ul>

للحصول على طلبات موضوع البيانات من منتجات أخرى ذات صلة بالخدمة، راجع المقالات التالية:

- Windows [البيانات التشخيصية](/compliance/regulatory/gdpr-dsr-windows)
- [بيانات Microsoft Intune](/compliance/regulatory/gdpr-dsr-intune)
- بيانات Azure Active [Directory](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>القانونيه

**إشعار الخصوصية من Microsoft للمستخدمين النهائيين للمنتجات التي يوفرها عملاء المؤسسة**:

يعلم [بيان خصوصية Microsoft](https://privacy.microsoft.com/privacystatement) المستخدمين بأنه عند تسجيل الدخول إلى منتجات Microsoft باستخدام حساب عمل:

1. يمكن لمؤسستهم التحكم في حساباتهم وإدارتها (بما في ذلك التحكم في الإعدادات المتعلقة بالخصوصية)، والوصول إلى بياناتهم ومعالجتها.
1. قد تقوم Microsoft بجمع البيانات ومعالجتها لتوفير الخدمة للمؤسسة والمستخدمين النهائيين.
