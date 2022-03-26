---
title: الاتصال مجالك Microsoft 365
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية توصيل مجالك Microsoft 365.
ms.openlocfilehash: d54b3bbf00dd0cf37006924e2884f2861c345d3e
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/15/2022
ms.locfileid: "63572133"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>الاتصال مجالك Microsoft 365 للأعمال

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

بعد إعداد بيانات البريد Microsoft 365 من Google Workspace، يمكنك توصيل مجالك Microsoft 365. 

ستحتاج أولا إلى حذف سجلات DNS الموجودة من Google، ثم يمكننا إضافة سجلات DNS جديدة من Microsoft 365.

## <a name="try-it"></a>جرب ذلك!

1. سجل دخولك إلى وحدة تحكم مسؤول Google Workspace [في admin.google.com](https://admin.google.com).
1. حدد **المجالات،** **وإدارة المجالات**، وعرض **التفاصيل****، وإدارة المجال**، ثم **DNS** في التنقل الأيسر.
1. قم بالتمرير لأسفل وصولا إلى **السجلات الاصطناعية**، وافتح **Google Workspace**، وحدد **حذف**، ثم **حذف مرة** أخرى.
1. قم **بالتمرير** لأسفل وصولا إلى سجلات الموارد المخصصة واحذف أي سجلات DNS موجودة تظهر، بما في ذلك أي سجلات قد تكون أنشأتها مسبقا Microsoft 365.
1. انتقل [إلى مركز مسؤولي Microsoft 365.](https://admin.microsoft.com)
1. في التنقل الأيسر، **اختر إظهار** >  **الكل** >  الإعدادات <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
1. ثم اختر مجالك الافتراضي.
1. حدد **متابعة الإعداد**، ثم، لتوصيل مجالك، اختر  **متابعة**.
1. قم بالتمرير لأسفل لعرض سجلات DNS التي يجب نسخها إلى Google.
1. افتح **سجلات MX**، و ضمن **نقاط العنوان أو القيمة**، انسخ السجل.
1. قم بالعودة إلى Google، وفي المقطع **سجلات** الموارد المخصصة، افتح منسدلة نوع السجل وحدد **MX**.
1. في الحقل **بيانات** ، اللصق السجل الذي نسخته.
1. ثم حدد **إضافة**.
1. كرر عملية سجلات CNAME وTXT وأضف القيم في صفحة إدارة Google DNS.
1. ارجع إلى مركز مسؤولي Microsoft 365 وحدد **متابعة**.

    اكتمل إعداد مجالك.