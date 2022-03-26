---
title: جمع المعلومات التي تحتاج إليها لإنشاء سجلات DNS
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
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: اجمع القيم/المعلومات التي تحتاج إليها لإنشاء سجلات DNS لتوصيل مجالك باشتراكك Microsoft 365.
ms.openlocfilehash: 672d57babb1b26e42b3fd24da8c9dc841223e41f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567548"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>جمع المعلومات التي تحتاج إليها لإنشاء سجلات DNS

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>الخطوة 1: البحث عن قيمة سجل TXT والتحقق

::: moniker range="o365-worldwide"

1. في مركز مسؤولي Microsoft 365، **انتقل إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">المجالات</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، **انتقل إلى الإعدادات** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">المجالات</a>.

::: moniker-end
    
2. في صفحة **المجالات** ، حدد مجالك، ثم حدد **بدء الإعداد**. سوف تعود إلى معالج إعداد المجالات لرؤية القيمة المحددة التي تحتاج إلى إضافتها.
    
3. في صفحة **التحقق من المجال** ، حدد **إضافة سجل TXT إلى سجلات DNS** للمجال، ثم حدد **متابعة**.
    
4. انسخ **قيمة TXT المعروضة** . يبدو كما يلي: **MS=msXXXXXXXX**. 
    
5. انتقل إلى [إضافة سجلات DNS](create-dns-records-at-any-dns-hosting-provider.md) لتوصيل مجالك، واتبع الخطوات لإضافة سجلات إلى موقع ويب لمضيف DNS.
    
6. اتبع الخطوات اللازمة لإنشاء سجل TXT (أو سجل MX) لدى مضيف DNS، ثم تحقق من المجال مرة أخرى في Microsoft 365.

7. قم بإزالة سجل TXT (أو سجل MX) من مضيف DNS بمجرد التحقق من المجال في Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>الخطوة 2: البحث عن قيمة سجل MX للبريد الإلكتروني والمزيد

::: moniker range="o365-worldwide"

1. في مركز مسؤولي Microsoft 365، **انتقل إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">المجالات</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، **انتقل إلى الإعدادات** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">المجالات</a>.

::: moniker-end
    
2. في صفحة **المجالات** ، حدد مجالك.
    
3. اختر **إدارة DNS،** وحدد **خيارات إضافية** >  **إضافة DNS** الخاص **بك وحدد** متابعة لرؤية سجلات DNS التي تريد إضافتها.
    
    وسترغب في الاحتفاظ بهذه المعلومات متوفرة أثناء إجراء تغييرات لدى مضيف DNS، بحيث يمكنك نسخ القيم ولصقها.
    
    تعتمد مجموعات سجلات DNS المدرجة على الصفحة على اختياراتك المدرجة ضمن **غرض المجال**.
    
4. انتقل إلى [إضافة سجلات DNS](create-dns-records-at-any-dns-hosting-provider.md) لتوصيل مجالك، واتبع الخطوات لإضافة سجلات إلى موقع ويب لمضيف DNS.

5. اتبع الخطوات اللازمة لإنشاء السجلات لدى مضيف DNS.

## <a name="related-content"></a>المحتوى ذي الصلة

[الأسئلة الشائعة حول المجالات](../setup/domains-faq.yml) (مقالة)\
[البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS](find-and-fix-issues.md) (مقالة)\
[إدارة المجالات](/admin) (صفحة الارتباط)