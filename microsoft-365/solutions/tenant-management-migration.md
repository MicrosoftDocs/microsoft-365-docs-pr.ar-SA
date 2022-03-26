---
title: الخطوة 4. الترحيل لمستأجري Microsoft 365 للمؤسسات
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: ترحيل الأجهزة Windows وتطبيقات Office العميل Office خوادم المستأجرين Microsoft 365 المستأجرين.
ms.openlocfilehash: 1892ae3da900f1c940866a2b2a3c70c1d6cb5db3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63569101"
---
# <a name="step-4-migration-for-your-microsoft-365-for-enterprise-tenants"></a>الخطوة 4. الترحيل لمستأجري Microsoft 365 للمؤسسات

تحتوي معظم مؤسسات المؤسسات على بيئة غير متجانسة تتضمن إصدارات متعددة من أنظمة التشغيل وبرامج العميل وبرامج الخادم. Microsoft 365 للمؤسسات الإصدارات الأكثر أمانا من المكونات الأساسية للبنية الأساسية ل IT. وتتضمن أيضا ميزات الإنتاجية التي تم تصميمها للاستفادة من تقنيات السحابة.

لتكبير قيمة الأعمال Microsoft 365 مجموعة المنتجات المتكاملة للمؤسسة، ابدأ في تخطيط استراتيجية لترحيل هذه الإصدارات وتنفيذها:

| من | إلى |
|:-------|:-----|
| Windows 7 Windows 8.1 | Windows 10 Enterprise |
| Office العميل المثبتة على أجهزة العامل | Microsoft 365 Apps for enterprise |
| Office منتجات الخادم المثبتة على الخوادم المحلية | خدماتهم المستندة إلى السحابة المكافئة في Microsoft 365 |
|  |  |

## <a name="migrating-to-windows-10"></a>عملية التهجر إلى Windows 10

تتضمن Microsoft 365 ترخيص المؤسسة ترخيصا Windows 10 Enterprise. لترحيل أجهزتك التي تعمل Windows 7 أو Windows 8.1، يمكنك القيام بالترقية في مكانها. انتهى الدعم Windows 7 يناير *14، 2020*. 

للحصول على أساليب إضافية لتثبيت Windows 10 Enterprise ترقية في مكان ما، راجع Windows 10 [النشر](/windows/deployment/windows-10-deployment-scenarios). يمكنك أيضا [التخطيط Windows 10 النشر](/windows/deployment/planning/) بنفسك.

## <a name="migrating-to-microsoft-365-apps-for-enterprise"></a>عملية التهجر إلى Microsoft 365 Apps for enterprise

Microsoft 365 الخاص بالمؤسسة Microsoft 365 Apps for enterprise، وهو إصدار من منتجات عميل Office (Word و PowerPoint و Excel و Outlook) التي تم تثبيتها وتحديثها من سحابة Microsoft. لمزيد من المعلومات، راجع [حول Microsoft 365 Apps for enterprise](/deployoffice/about-microsoft-365-apps).

بدلا من إبقاء أجهزة الكمبيوتر الخاصة بك محدثة Office 2019 أو الإصدارات الأقدم، يمكنك اتباع الخطوات التالية:

1. احصل على ترخيص Microsoft 365 للمستخدمين وتعيينه.
2. إلغاء تثبيت Office 2013 أو Office 2016 على أجهزة الكمبيوتر الخاصة بهم.
3. ثبت Microsoft 365 Apps for enterprise بشكل فردي أو أثناء عملية طرح ل IT. لمزيد من المعلومات، راجع [دليل النشر Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

Microsoft 365 Apps for enterprise تثبيت كل من تحديثات الأمان وتحديثات الميزات الجديدة تلقائيا ويمكنه الاستفادة من الخدمات المستندة إلى السحابة في Microsoft 365 لتحسين الأمان والإنتاجية.

## <a name="migrating-on-premises-servers-and-data-to-microsoft-365"></a>نقل الخوادم والبيانات إلى Microsoft 365

Microsoft 365 للمؤسسات إصدارات مستندة إلى السحابة من خدمات خادم Office التي تستخدم بعض الأدوات نفسها كالإصدارات المحلية من برامج خادم Office، مثل مستعرضات الويب Outlook العميل. يتم تحديث هذه الخدمات المستندة إلى السحابة تلقائيا للميزات الجديدة والأمان. بعد الترحيل، يمكن لقسم قسم المعلومات توفير الوقت المستغرق لصيانة الخوادم الداخلية وتحديثها.

استخدم الموارد التالية للحصول على معلومات حول عملية نقل المستخدمين والبيانات لأحمال عمل Microsoft 365 معينة:

- [نقل علب البريد من علب البريد المحلية Exchange Server إلى Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [ترحيل SharePoint البيانات من SharePoint Server إلى SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)
- [ترحيل Skype for Business Online إلى Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

## <a name="transition-your-entire-organization"></a>نقل مؤسستك بكاملها

للحصول على صورة أفضل حول كيفية نقل مؤسستك بكاملها إلى المنتجات والخدمات في Microsoft 365 للمؤسسات، قم بتنزيل ملصق الانتقال هذا:

[![صورة تعرض ملصق الانتقال إلى Microsoft 365.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

يعد هذا الملصق الذي من صفحتين طريقة سريعة لجرد البنية الأساسية الحالية. استخدمه للحصول على إرشادات حول الانتقال إلى منتج أو خدمة في Microsoft 365 للمؤسسة. وهو يعرض Windows والمنتجات Office والبنية الأساسية وعناصر الأمان الأخرى مثل إدارة الأجهزة والحماية من الهوية والتهديدات وحماية المعلومات والتوافق.

## <a name="results-of-step-4"></a>نتائج الخطوة 4

بالنسبة ل الترحيل لمستأجر Microsoft 365، لقد حددت ما يلي:

- الأجهزة التي يتم تشغيلها Windows 7 أو Windows 8.1 والخطط لتحديثها إلى Windows 10 Enterprise.
- الأجهزة التي تقوم بتشغيل Office العميل وخطط تحديثها إلى Microsoft 365 للمؤسسات.
- ما هي الخدمات المحلية Office التي يجب ترحيلها إلى خدمات الخادم Microsoft 365 مماثلة لخطة ترحيلها وبياناتها.

فيما يلي مثال لمستأجر مع ترحيل مكتمل للخوادم الداخلية.

![مثال لمستأجر مع ترحيل مكتمل للخوادم الداخلية.](../media/tenant-management-overview/tenant-management-tenant-build-step4.png)

في هذا الرسم التوضيحي، يكون في المؤسسة:

- ترحيل علب بريدها Exchange Server المحلية إلى Exchange Online.
- ترحيل مواقع الخادم وبياناته SharePoint موقع الخادم SharePoint في Microsoft 365.

## <a name="ongoing-maintenance-for-migration"></a>الصيانة المستمرة ل الترحيل

بشكل مستمر، قد تحتاج إلى:

- استنادا إلى حالة ترحيل علبة Exchange البريد، استمر في Exchange Online الانتقال إلى مؤسستك.
- استنادا إلى حالة الترحيل SharePoint الموقع، تابع عملية الانتقال إلى SharePoint في Microsoft 365 إلى مؤسستك.

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 5. نشر إدارة الأجهزة والتطبيقات.](../media/tenant-management-overview/tenant-management-step-grid-device-mgmt.png)](tenant-management-device-management.md)

تابع إدارة [الأجهزة والتطبيقات](tenant-management-device-management.md) لنشر إدارة الأجهزة والتطبيقات.