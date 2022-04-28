---
title: مراقبة اتصال Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 8/4/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 53cdb60c-a6b2-4848-b3ff-e7b75dc3fd1f
description: في هذه المقالة، ستتعرف على الأدوات والتقنيات التي يمكنك استخدامها لمراقبة الاتصال Microsoft 365 وصيانته.
ms.openlocfilehash: 0e7c18a10dc851596af6a652fb80c9c72852ee0d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093296"
---
# <a name="monitor-microsoft-365-connectivity"></a>مراقبة اتصال Microsoft 365

بمجرد نشر Microsoft 365، يمكنك الحفاظ على اتصال Microsoft 365 باستخدام بعض الأدوات والتقنيات أدناه. ستحتاج إلى فهم الإرشادات الرسمية [لصحة الخدمة والاستمرارية](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity) بالإضافة إلى [أفضل ممارساتنا لاستخدام Microsoft 365 على شبكة بطيئة](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166). ستحتاج أيضا إلى الحصول على [تطبيق مسؤول Microsoft 365](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) ووضع إشارة مرجعية [على Microsoft 365 للأعمال - تعليمات المسؤول](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>مراقبة اتصال Microsoft 365

|نوع المراقبة |الوصف |
|:-----|:-----|
|**يتم إعلامك بنقاط نهاية Microsoft 365 الجديدة** <br/> |إذا كنت [تدير نقاط نهاية Microsoft 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)، فسترغب في تلقي إعلامات عندما ننشر نقاط نهاية جديدة، يمكنك الاشتراك في موجز RSS الخاص بنا باستخدام قارئ RSS المفضل لديك. فيما يلي كيفية [الاشتراك عبر Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) أو يمكنك [إرسال تحديثات موجز ويب ل RSS إليك عبر البريد الإلكتروني](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**استخدام System Center لمراقبة Microsoft 365** <br/> |إذا كنت تستخدم مركز نظام Microsoft، يمكنك تنزيل [حزمة إدارة إدارة عمليات مركز نظام Microsoft Microsoft 365](https://www.microsoft.com/download/details.aspx?id=103379) لبدء مراقبة Microsoft 365 اليوم. للحصول على إرشادات أكثر تفصيلا، يرجى مراجعة دليل عمليات حزمة الإدارة. <br/> |
|**مراقبة صحة Azure ExpressRoute** <br/> |إذا كنت تتصل Microsoft 365 باستخدام Azure ExpressRoute Microsoft 365، فسترغب في التأكد من أنك تستخدم كل من لوحة معلومات حماية الخدمة Microsoft 365 وكذلك [وقت استكشاف الأخطاء وإصلاحها في Azure مع حماية Azure Resource](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**استخدام Azure AD الاتصال Health مع AD FS** <br/> |إذا كنت تستخدم AD FS Sign-On واحد مع Microsoft 365، فسترغب في البدء [في استخدام Azure AD الاتصال Health لمراقبة البنية الأساسية ل AD FS](/azure/active-directory/hybrid/how-to-connect-health-adfs).  <br/> |
|**مراقبة Microsoft 365 برمجيا** <br/> |راجع إرشاداتنا حول [واجهة برمجة تطبيقات إدارة Microsoft 365](/office/office-365-management-api/office-365-management-apis-overview).  <br/> |

فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[تكوين خدمات وتطبيقات Microsoft 365 Enterprise](configure-services-and-applications.md)
  
[تحضير مؤسستك Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[تخطيط الشبكة وضبط الأداء Microsoft 365](network-planning-and-performance.md)
  
[تكامل Microsoft 365 مع البيئات المحلية](microsoft-365-integration.md)
  
[إدارة نقاط نهاية Microsoft 365](managing-office-365-endpoints.md)
