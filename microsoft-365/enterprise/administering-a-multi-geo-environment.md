---
title: إدارة بيئة متعددة الجغرافيا
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
description: يمكن للمسؤولين التعرف على كيفية إدارة SharePoint والخدمات OneDrive في بيئة متعددة الجغرافيا.
ms.openlocfilehash: 126b5de915fba7168b3895bbb05ccef6dcad749b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63576888"
---
# <a name="administering-a-multi-geo-environment"></a>إدارة بيئة متعددة الجغرافيا

إليك نظرة على كيفية عمل Microsoft 365 في بيئة متعددة الجغرافيا.

## <a name="administrator-experience"></a>تجربة المسؤول

يضم SharePoint إدارة الموقع الجغرافي علامة تبويب <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank"></a> مواقع جغرافية في شريط التنقل الأيسر الذي يتميز بخريطة مواقع جغرافية حيث يمكنك عرض المواقع الجغرافية وإدارتها. استخدم هذه الصفحة لإضافة مواقع جغرافية للمستأجر أو حذفها.

## <a name="audit-log-search"></a>البحث في سجل التدقيق

يتوفر سجل [تدقيق موحد](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) لكل مواقع الأقمار الصناعية من صفحة البحث في Microsoft 365 التدقيق. يمكنك رؤية كل إدخالات سجل التدقيق من مواقع جغرافية مختلفة، على سبيل المثال، سوف تظهر أنشطة مستخدمي NAM & EUR في طريقة عرض مؤسسة واحدة، ثم يمكنك تطبيق عوامل تصفية موجودة لرؤية أنشطة مستخدم معين.

> [!NOTE]
> Exchange أحداث تدقيق المسؤول للموقع الافتراضي فقط.

## <a name="bcs-secure-store-apps"></a>BCS، المتجر الآمن، التطبيقات

تحتوي كل من BCS وSe secure Store والتطبيقات على مثيلات منفصلة في كل موقع قمر صناعي، وبالتالي يجب على مسؤول SharePoint Online إدارة هذه الخدمات وتكوينها بشكل منفصل عن كل موقع قمر صناعي.

## <a name="compliance-admin-center"></a>مركز إدارة التوافق

يوجد مركز توافق مركزي واحد لمستأجر متعدد الجغرافيا: Microsoft 365 [إدارة التوافق](https://compliance.microsoft.com/).

## <a name="ediscovery"></a>eDiscovery

بشكل افتراضي، سيكون مدير eDiscovery أو مسؤول مستأجر متعدد الجغرافيا قادرا على إدارة eDiscovery فقط في الموقع المركزي لذلك المستأجر. يجب على المسؤول العام ل Office 365 تعيين أذونات eDiscovery Manager للسماح للآخرين بتنفيذ eDiscovery وتعيين معلمة "المنطقة" في عامل تصفية أمان التوافق المعمول به لتحديد المنطقة لإجراء eDiscovery كمواقف أقمار صناعية، وإلا لن يتم تنفيذ eDiscovery لموقع القمر الصناعي. لتكوين عامل تصفية أمان التوافق للمنطقة، راجع تكوين Office 365 [EDiscovery متعدد الجغرافيا](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Exchange علب البريد

يتم نقل Exchange البريد الخاصة بالمستخدمين تلقائيا إذا تم تغيير PDL الخاص بهم. عند إنشاء علبة بريد جديدة، يتم توفيرها إلى PDL الخاص بالمستخدم أو إلى الموقع المركزي إذا لم يتم تعيين أي قيمة ل PDL الخاص بالمستخدم.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>نهج منع فقدان البيانات (DLP) لحماية المعلومات (IP)

يمكنك تعيين سياسات IP DLP ل OneDrive for Business و SharePoint و Exchange في مركز الأمان والتوافق، ونهج تحديد الموقع حسب الحاجة للمستأجر بكامله أو للمستخدمين الساريين. على سبيل المثال: إذا كنت تريد تحديد نهج لمستخدم في موقع القمر الصناعي، فحدد لتطبيق النهج على موقع OneDrive وأدخل عنوان url الخاص OneDrive المستخدم. راجع [نظرة عامة حول سياسات منع فقدان](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) البيانات للحصول على إرشادات عامة حول إنشاء سياسات DLP.

يتم مزامنة سياسات DLP تلقائيا استنادا إلى إمكانية تطبيقها على كل موقع جغرافي.

لا يمثل تنفيذ نهج الحماية من فقدان البيانات وحماية المعلومات لجميع المستخدمين في موقع جغرافي خيارا متوفرا في واجهة المستخدم، بدلا من ذلك يجب تحديد الحسابات القابلة للتطبيق الخاصة النهج أو تطبيق النهج بشكل عمومي على كل الحسابات.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

ستستخدم تطبيقات Power التي تم إنشاؤها لموقع القمر الصناعي نقطة النهاية الموجودة في الموقع المركزي للمستأجر. Microsoft Power Apps ليست خدمة متعددة الجغرافيا. 

## <a name="power-automate"></a>Power Automate

تستخدم التدفقات التي تم إنشاؤها لموقع القمر الصناعي نقطة النهاية الموجودة في الموقع الجغرافي الافتراضي للمستأجر.  Power Automate ليست خدمة Multi-Geo. 

## <a name="sharepoint-storage-quota"></a>SharePoint التخزين النسبية

بشكل افتراضي، تشارك كل المواقع الجغرافية لبيئة متعددة الجغرافيا الحصة النسبية المتوفرة للتخزين للمستأجر.  يمكنك أيضا إدارة الحصة النسبية للتخزين عن طريق تخصيص حصة محددة لموقع جغرافي معين. لمزيد من المعلومات، [راجع SharePoint النسبية للتخزين في بيئات متعددة الجغرافيا](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>المشاركة

يمكن للمسؤولين تعيين سياسات المشاركة وإدارتها لكل موقع من مواقعهم. سيحترم OneDrive المواقع SharePoint في كل موقع جغرافي إعدادات المشاركة الخاصة جغرافيا المطابقة فقط. (على سبيل المثال، يمكنك السماح بالمشاركة [الخارجية](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) لموقعك المركزي، ولكن ليس لموقع القمر الصناعي أو العكس.) لاحظ أن إعدادات المشاركة لا تسمح بتكوين قيود المشاركة بين المواقع الجغرافية.

## <a name="stream"></a>Stream

يتم تخزين ملفات الفيديو التي تم تحميلها إلى Stream في دردشة 1:1 في OneDrive الشخص الذي قام بتحميله. يتم تخزين تسجيلات الاجتماع في OneDrive لكل حاضر يسجل الاجتماع.

## <a name="taxonomy"></a>Taxonomy

نحن ندعم تصنيفا موحدا لبيانات التعريف المدارة من قبل المؤسسة عبر المواقع الجغرافية، مع استضافة الفئة الرئيسية في الموقع المركزي للشركة.[](/sharepoint/managed-metadata) نوصيك بإدارة موقعك العام من الموقع المركزي وإضافة مصطلحات خاصة بموقع معين فقط إلى "موقع القمر الصناعي". سيتم مزامنة المصطلحات العالمية الخاصة بالضريبة على الاقمار الصناعية مع مواقع الاقمار الصناعية.

راجع [إدارة بيانات التعريف في مستأجر متعدد](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) الجغرافيا للحصول على مزيد من التفاصيل وإرشادات المطور.

## <a name="user-profile-application"></a>تطبيق ملف تعريف المستخدم

يوجد تطبيق [ملف تعريف مستخدم](/sharepoint/manage-user-profiles) في كل موقع جغرافي. يتم استضافة معلومات ملف تعريف كل مستخدم في موقعه الجغرافي ومتوفرة للمسؤول لهذا الموقع الجغرافي.

إذا كانت لديك خصائص ملف تعريف مخصصة، فإننا نوصي باستخدام مخطط ملف التعريف نفسه عبر المناطق الجغرافية و ملء خصائص ملف التعريف المخصص إما في كل المواقع الجغرافية أو عند الحاجة. للحصول على إرشادات تتعلق بكيفية تعبئة بيانات ملف تعريف المستخدم برمجيا، الرجاء الرجوع إلى واجهة برمجة [API](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online) لتحديث ملف تعريف المستخدم المجمع.

راجع [استخدام ملفات تعريف المستخدمين في مستأجر](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) متعدد الجغرافيا للحصول على تفاصيل إضافية وإرشادات المطور.

## <a name="yammer"></a>Yammer

Yammer حمل عمل متعدد الجغرافيا. Yammer المواضيع المخزنة في Yammer في الموقع المركزي للمستأجر. Yammer عن تغيير تخزين الملفات الذي سيخزن Yammer داخل SharePoint. Yammer الملفات المخزنة في SharePoint موقع SharePoint المقترن بالمجموعة Yammer. SharePoint مواقع المجموعات على منطق PDL كما هو موضح [في SharePoint المجموعات والمواقع](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
