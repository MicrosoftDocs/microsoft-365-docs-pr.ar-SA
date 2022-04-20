---
title: إدارة بيئة متعددة المواقع الجغرافية
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: يمكن للمسؤولين التعرف على كيفية إدارة خدمات SharePoint OneDrive في بيئة متعددة المناطق الجغرافية.
ms.openlocfilehash: 155eea030cfa700a009805fb66aeb74eaae617d3
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949068"
---
# <a name="administering-a-multi-geo-environment"></a>إدارة بيئة متعددة المواقع الجغرافية

فيما يلي نظرة على كيفية عمل الخدمات Microsoft 365 في بيئة متعددة المناطق الجغرافية.

## <a name="administrator-experience"></a>تجربة المسؤول

يحتوي مركز إدارة SharePoint على <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">علامة تبويب **مواقع جغرافية**</a> في جزء التنقل الأيمن الذي يتميز بخريطة مواقع جغرافية حيث يمكنك عرض مواقعك الجغرافية وإدارتها. استخدم هذه الصفحة لإضافة مواقع جغرافية للمستأجر أو حذفها.

## <a name="audit-log-search"></a>البحث في سجل التدقيق

يتوفر [سجل تدقيق](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) موحد لجميع مواقع الأقمار الصناعية من صفحة البحث في سجل التدقيق Microsoft 365. يمكنك مشاهدة جميع إدخالات سجل التدقيق من خلال المواقع الجغرافية، على سبيل المثال، ستظهر أنشطة NAM & اليورو للمستخدمين في طريقة عرض مؤسسة واحدة ثم يمكنك تطبيق عوامل التصفية الموجودة للاطلاع على أنشطة مستخدم معين.

> [!NOTE]
> Exchange أحداث تدقيق المسؤول متوفرة للموقع الافتراضي فقط.

## <a name="bcs-secure-store-apps"></a>BCS، المخزن الآمن، التطبيقات

تحتوي BCS و Secure Store و Apps على مثيلات منفصلة في كل موقع قمر صناعي، لذلك يجب على مسؤول SharePoint Online إدارة هذه الخدمات وتكوينها بشكل منفصل عن كل موقع قمر صناعي.

## <a name="compliance-admin-center"></a>مركز إدارة التوافق

يوجد مركز توافق مركزي واحد لمستأجر متعدد المناطق الجغرافية: [مركز إدارة Microsoft Purview](https://compliance.microsoft.com/).

## <a name="ediscovery"></a>eDiscovery

بشكل افتراضي، سيتمكن مدير eDiscovery أو مسؤول مستأجر متعدد المناطق الجغرافية من إجراء eDiscovery فقط في الموقع المركزي لذلك المستأجر. يجب على المسؤول العام Office 365 تعيين أذونات eDiscovery Manager للسماح للآخرين بتنفيذ eDiscovery وتعيين معلمة "Region" في عامل تصفية أمان التوافق المعمول به لتحديد المنطقة لإجراء eDiscovery كموقع قمر صناعي، وإلا فلن يتم تنفيذ eDiscovery لموقع القمر الصناعي. لتكوين عامل تصفية أمان التوافق لمنطقة ما، راجع [تكوين Office 365 Multi-Geo eDiscovery](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>علب بريد Exchange

يتم نقل علب بريد المستخدمين Exchange تلقائيا إذا تم تغيير PDL الخاصة بهم. عند إنشاء علبة بريد جديدة، يتم توفيرها إلى PDL الخاص بالمستخدم أو إلى الموقع المركزي إذا لم يتم تعيين قيمة ل PDL الخاص بالمستخدم.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>نهج منع فقدان البيانات (DLP) حماية البيانات (IP)

يمكنك تعيين نهج IP DLP الخاصة بك OneDrive for Business، SharePoint، Exchange في مركز الأمان والتوافق، وتحديد نطاق النهج حسب الحاجة للمستأجر بأكمله أو للمستخدمين القابلين للتطبيق. على سبيل المثال: إذا كنت ترغب في تحديد نهج لمستخدم في موقع قمر صناعي، فحدد تطبيق النهج على OneDrive معينة وأدخل عنوان url OneDrive للمستخدم. راجع [نظرة عامة على نهج منع فقدان البيانات](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) للحصول على إرشادات عامة في إنشاء نهج DLP.

تتم مزامنة نهج DLP تلقائيا بناء على إمكانية تطبيقها على كل موقع جغرافي.

لا يعد تنفيذ نهج حماية البيانات وMicrosoft Purview لمنع فقدان البيانات لجميع المستخدمين في موقع جغرافي خيارا متوفرا في واجهة المستخدم، بدلا من ذلك يجب تحديد الحسابات المعمول بها للنهج أو تطبيق النهج بشكل عام على جميع الحسابات.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

ستستخدم Power Apps التي تم إنشاؤها لموقع القمر الصناعي نقطة النهاية الموجودة في الموقع المركزي للمستأجر. Microsoft Power Apps ليست خدمة متعددة المناطق الجغرافية. 

## <a name="power-automate"></a>Power Automate

ستستخدم التدفقات التي تم إنشاؤها لموقع القمر الصناعي نقطة النهاية الموجودة في الموقع الجغرافي الافتراضي للمستأجر.  Power Automate ليست خدمة متعددة المناطق الجغرافية. 

## <a name="sharepoint-storage-quota"></a>الحصة النسبية للتخزين SharePoint

بشكل افتراضي، تشترك جميع المواقع الجغرافية لبيئة متعددة المناطق الجغرافية في حصة تخزين المستأجر المتوفرة.  يمكنك أيضا إدارة الحصة النسبية للتخزين عن طريق تخصيص حصة نسبية محددة لموقع جغرافي معين. لمزيد من المعلومات، راجع [SharePoint الحصص النسبية للتخزين في البيئات متعددة المناطق الجغرافية](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>تقاسم

يمكن للمسؤولين تعيين نهج المشاركة لكل موقع من مواقعهم وإدارتها. ستحترم مواقع OneDrive والمواقع SharePoint في كل موقع جغرافي إعدادات المشاركة الجغرافية المحددة المقابلة فقط. (على سبيل المثال، يمكنك السماح [بالمشاركة الخارجية](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) لموقعك المركزي، ولكن ليس لموقع القمر الصناعي أو العكس.) لاحظ أن إعدادات المشاركة لا تسمح بتكوين قيود المشاركة بين المواقع الجغرافية.

## <a name="stream"></a>تيار

يتم تخزين مقاطع الفيديو التي تم تحميلها إلى Stream في دردشة 1:1 في OneDrive الشخص الذي يقوم بتحميلها. يتم تخزين تسجيلات الاجتماع في OneDrive لكل حاضر يسجل الاجتماع.

## <a name="taxonomy"></a>التصنيف

نحن ندعم [تصنيفا](/sharepoint/managed-metadata) موحدا لبيانات التعريف التي تديرها المؤسسة عبر المواقع الجغرافية، مع استضافة الرئيس في الموقع المركزي لشركتك. نوصي بإدارة التصنيف العالمي الخاص بك من الموقع المركزي وإضافة مصطلحات خاصة بالموقع فقط إلى تصنيف موقع القمر الصناعي. وستتزامن شروط التصنيف العالمية مع مواقع الأقمار الصناعية.

راجع [إدارة بيانات التعريف في مستأجر متعدد المناطق الجغرافية](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) للحصول على تفاصيل إضافية وإرشادات المطور.

## <a name="user-profile-application"></a>تطبيق ملف تعريف المستخدم

يوجد [تطبيق ملف تعريف مستخدم](/sharepoint/manage-user-profiles) في كل موقع جغرافي. تتم استضافة معلومات ملف تعريف كل مستخدم في موقعه الجغرافي ومتاحة للمسؤول لذلك الموقع الجغرافي.

إذا كان لديك خصائص ملف تعريف مخصصة، فإننا نوصي باستخدام مخطط ملف التعريف نفسه عبر المناطق الجغرافية وتعبئة خصائص ملف التعريف المخصص إما في جميع المواقع الجغرافية أو عند الحاجة. للحصول على إرشادات حول كيفية ملء بيانات ملف تعريف المستخدم برمجيا، يرجى الرجوع إلى [واجهة برمجة تطبيقات تحديث ملف تعريف المستخدم المجمع](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

راجع [العمل مع ملفات تعريف المستخدمين في مستأجر متعدد المناطق الجغرافية](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) للحصول على تفاصيل إضافية وإرشادات المطور.

## <a name="yammer"></a>Yammer

Yammer ليس حمل عمل متعدد المناطق الجغرافية. سيتم وضع Yammer مؤشرات الترابط المخزنة في Yammer في الموقع المركزي للمستأجر. تقوم Yammer بنشر تغيير تخزين الملفات الذي سيخزن ملفات Yammer داخل SharePoint. سيتم وضع Yammer الملفات المخزنة في SharePoint موقع SharePoint المقترن بمجموعة Yammer. تستند SharePoint مواقع المجموعات إلى منطق PDL كما هو موضح في [مواقع ومجموعات SharePoint](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
