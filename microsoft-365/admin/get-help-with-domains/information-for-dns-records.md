---
title: جمع المعلومات التي تحتاجها لإنشاء سجلات DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: جمع القيم/المعلومات التي تحتاجها لإنشاء سجلات DNS لتوصيل مجالك باشتراكك في Microsoft 365.
ms.openlocfilehash: 653161734a8b0a2f188c8f8a54909ed86bf3fd5f
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67083986"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>جمع المعلومات التي تحتاجها لإنشاء سجلات DNS

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>الخطوة 1: البحث عن قيمة سجل TXT والتحقق

::: moniker range="o365-worldwide"

1. في مركز مسؤولي Microsoft 365، انتقل إلى صفحة **"مجالات الإعدادات**\>".<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى صفحة **"مجالات الإعدادات**>".<a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank"></a>

::: moniker-end
    
2. في صفحة **"المجالات"** ، حدد مجالك، ثم حدد **"بدء الإعداد**". ستعود إلى معالج إعداد المجالات للاطلاع على القيمة المحددة التي تحتاج إلى إضافتها.
    
3. في صفحة **التحقق من المجال** ، حدد **إضافة سجل TXT إلى سجلات DNS للمجال**، ثم حدد **"متابعة**".
    
4. نسخ **قيمة TXT** المعروضة. يبدو مثل هذا: **MS=msXXXXXXXX.** 
    
5. انتقل إلى [إضافة سجلات DNS لتوصيل مجالك](create-dns-records-at-any-dns-hosting-provider.md)، واتبع الخطوات لإضافة سجلات في موقع ويب لمضيف DNS.
    
6. اتبع الخطوات لإنشاء سجل TXT (أو سجل MX) لدى مضيف DNS، ثم تحقق من المجال مرة أخرى في Microsoft 365.

7. قم بإزالة سجل TXT (أو سجل MX) من مضيف DNS بمجرد التحقق من المجال في Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>الخطوة 2: البحث عن قيمة سجل MX للبريد الإلكتروني والمزيد

::: moniker range="o365-worldwide"

1. في مركز مسؤولي Microsoft 365، انتقل إلى صفحة **"مجالات الإعدادات**\>".<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى صفحة **"مجالات الإعدادات**>".<a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank"></a>

::: moniker-end
    
2. في صفحة **المجالات** ، حدد مجالك.
    
3. اختر  **"إدارة DNS**"، وحدد **"المزيد من الخيارات** > **إضافة DNS" وحدد** **"متابعة** " لرؤية سجلات DNS لإضافتها.
    
    ستحتاج إلى الاحتفاظ بهذه المعلومات متوفرة أثناء إجراء تغييرات على مضيف DNS، حتى تتمكن من نسخ القيم ولصقها.
    
    تعتمد مجموعات سجلات DNS المدرجة على الصفحة على اختياراتك المدرجة ضمن **الغرض من المجال**.
    
4. انتقل إلى [إضافة سجلات DNS لتوصيل مجالك](create-dns-records-at-any-dns-hosting-provider.md)، واتبع الخطوات لإضافة سجلات في موقع ويب لمضيف DNS.

5. اتبع الخطوات لإنشاء السجلات لدى مضيف DNS.

## <a name="related-content"></a>المحتويات ذات الصلة

[الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml) (مقالة)\
[البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS‏](find-and-fix-issues.md) (مقالة)/
[إدارة المجالات](/admin) (صفحة الارتباط)