---
title: مراقبة Microsoft 365 الاتصال
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: في هذه المقالة، ستتعرف على الأدوات والتقنيات التي يمكنك استخدامها لمراقبة Microsoft 365 الاتصال.
ms.openlocfilehash: 783278ad69fbe47afd6ea85fdb70c8bb0057005c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63576890"
---
# <a name="monitor-microsoft-365-connectivity"></a>مراقبة Microsoft 365 الاتصال

بعد نشر Microsoft 365، يمكنك الاحتفاظ Microsoft 365 الاتصال باستخدام بعض الأدوات والتقنيات أدناه. سترغب في فهم إرشادات "صحة الخدمة[](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity)" و"الاستمرارية" الرسمية بالإضافة إلى أفضل [ممارساتنا لاستخدام Microsoft 365 شبكة بطيئة.](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) سترغب أيضا في الحصول على تطبيق Microsoft 365 [الإلكتروني](https://blogs.office.com/2015/03/13/administer-on-the-go-with-the-updated-office-365-admin-app/) وإشارتنا المرجعية Microsoft 365 [للأعمال - تعليمات المسؤول](https://support.office.com/article/17d3ff3f-3601-466e-b5a1-482b31cfb791).
  
## <a name="monitoring-microsoft-365-connectivity"></a>مراقبة Microsoft 365 الاتصال

|نوع المراقبة |الوصف |
|:-----|:-----|
|**الحصول على إعلامات بنقاط Microsoft 365 نقاط النهاية الجديدة** <br/> |إذا كنت تقوم [Microsoft 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) نقاط النهاية، فسوف تحتاج إلى تلقي إعلامات عند نشر نقاط نهاية جديدة، يمكنك الاشتراك في موجز RSS باستخدام قارئ RSS المفضل لديك. إليك كيفية الاشتراك عبر [Outlook](https://go.microsoft.com/fwlink/p/?LinkId=532416) أو يمكنك إرسال تحديثات [موجز RSS إليك عبر البريد الإلكتروني](https://go.microsoft.com/fwlink/p/?LinkId=532417).  <br/> |
|**استخدام مركز النظام لمراقبة Microsoft 365** <br/> |إذا كنت تستخدم Microsoft System Center، يمكنك تنزيل [Microsoft System Center Operations Manager Pack](https://www.microsoft.com/download/details.aspx?id=103379) Microsoft 365 لبدء مراقبة Microsoft 365 اليوم. للحصول على إرشادات أكثر تفصيلا، الرجاء الاطلاع على دليل عمليات حزمة الإدارة. <br/> |
|**مراقبة صحة Azure ExpressRoute** <br/> |إذا كنت تريد الاتصال ب Microsoft 365 باستخدام Azure ExpressRoute ل Microsoft 365، فسوف تحتاج إلى التأكد من أنك تستخدم كل من لوحة معلومات حالة خدمة Microsoft 365 بالإضافة إلى تقليل وقت استكشاف الأخطاء وإصلاحها في [Azure Resource](https://azure.microsoft.com/blog/reduce-troubleshooting-time-with-azure-resource-health/) <br/> |
|**استخدام Azure AD الاتصال مع AD FS** <br/> |إذا كنت تستخدم AD FS ل single Sign-On مع Microsoft 365، فسوف تحتاج إلى بدء استخدام [Azure AD الاتصال Health لمراقبة البنية الأساسية ل AD FS](/azure/active-directory/hybrid/how-to-connect-health-adfs).  <br/> |
|**مراقبة Microsoft 365** <br/> |راجع إرشاداتنا حول Microsoft 365 [API.](/office/office-365-management-api/office-365-management-apis-overview)  <br/> |

إليك ارتباط مختصر يمكنك استخدامه للعودة: [https://aka.ms/monitorconnectivity365]()
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[تكوين Microsoft 365 Enterprise وتطبيقاتك](configure-services-and-applications.md)
  
[استعد مؤسستك Microsoft 365 Enterprise](get-your-organization-ready-for-office-365.md)
  
[تخطيط الشبكة وضبط الأداء Microsoft 365](network-planning-and-performance.md)
  
[Microsoft 365 التكامل مع البيئات المحلية](microsoft-365-integration.md)
  
[إدارة Microsoft 365 نقاط النهاية](managing-office-365-endpoints.md)
