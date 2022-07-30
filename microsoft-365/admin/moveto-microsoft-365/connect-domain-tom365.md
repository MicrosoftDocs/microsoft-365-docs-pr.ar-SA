---
title: توصيل مجالك بـ Microsoft 365
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
- VSBFY23
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية توصيل مجالك ب Microsoft 365.
ms.openlocfilehash: b03f7fa149ed4abddeecb5ab3b89372a9f0e008f
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67085574"
---
# <a name="connect-your-domain-to-microsoft-365-for-business"></a>توصيل مجالك ب Microsoft 365 للأعمال

اطلع على [تعليمات Microsoft 365 للشركات الصغيرة](https://go.microsoft.com/fwlink/?linkid=2197659) على YouTube.

## <a name="watch-connect-your-domain-to-microsoft-365"></a>شاهد: توصيل مجالك ب Microsoft 365

اطلع على هذا الفيديو وغيره على [قناتنا على YouTube](https://go.microsoft.com/fwlink/?linkid=2198216).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LFpy?autoplay=false]

بمجرد إعداد Microsoft 365 ونقل بيانات بريدك الإلكتروني من Google Workspace، يمكنك توصيل مجالك ب Microsoft 365. 

ستحتاج أولا إلى حذف سجلات DNS الموجودة من Google، ثم يمكننا إضافة سجلات DNS جديدة من Microsoft 365.

1. سجل الدخول إلى وحدة تحكم مسؤول Google Workspace في [admin.google.com](https://admin.google.com).
1. حدد **المجالات****، وإدارة المجالات**، **وعرض التفاصيل**، **وإدارة المجال**، ثم **DNS** في التنقل الأيمن.
1. قم بالتمرير لأسفل وصولا إلى **السجلات الاصطناعية**، وافتح **Google Workspace**، وحدد **Delete**، ثم **احذف** مرة أخرى.
1. قم بالتمرير لأسفل وصولا إلى **سجلات الموارد المخصصة** واحذف أي سجلات DNS موجودة تظهر، بما في ذلك أي سجلات قمت بإنشائها مسبقا ل Microsoft 365.
1. انتقل إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com).
1. في جزء التنقل الأيمن، اختر " **إظهار كافة** > **مجالات الإعدادات** > ".<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>
1. ثم اختر مجالك الافتراضي.
1. حدد **متابعة الإعداد**، ثم للاتصال بمجالك، اختر  **"متابعة**".
1. قم بالتمرير لأسفل لعرض سجلات DNS التي يجب نسخها إلى Google.
1. افتح **سجلات MX**، وضمن **"نقاط" العنوان أو القيمة**، انسخ السجل.
1. ارجع إلى Google، وفي قسم **سجلات الموارد المخصصة** ، افتح القائمة المنسدلة لنوع السجل وحدد **MX**.
1. في الحقل **"بيانات** "، الصق السجل الذي نسخته.
1. ثم حدد **"إضافة**".
1. كرر عملية سجلات CNAME وTXT وأضف القيم في صفحة إدارة Google DNS.
1. ارجع إلى مركز مسؤولي Microsoft 365 وحدد **"متابعة**".

    اكتمل إعداد المجال.