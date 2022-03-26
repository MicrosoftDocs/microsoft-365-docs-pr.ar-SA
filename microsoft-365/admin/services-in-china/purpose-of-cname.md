---
title: ما الغرض من سجل Office 365 CNAME ل MSOID؟
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NOINDEX
description: تعرف على المزيد حول سجل CNAME 'MSOID' في Office 365 الذي يوجهك إلى أفضل خادم لعمليات المصادقة، وبالتالي ستحصل على استجابة أسرع.
monikerRange: o365-21vianet
ms.openlocfilehash: 1b053ac0df7cd770b5627b688e90641688f94141
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568401"
---
# <a name="whats-the-purpose-of-the-office-365-cname-record-for-msoid"></a>ما الغرض من سجل Office 365 CNAME ل MSOID؟

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه. 
> [!NOTE]
> ينطبق ما يلي فقط على **Office 365 التي يتم تشغيلها بواسطة 21Vianet.
  
قد تتساءل لماذا تحتاج إلى إضافة سجل CNAME "MSOID" في Office 365. هذا سجل يجب إضافته لكل المجالات المخصصة، بغض النظر عن الاشتراك الذي تستخدمه. لماذا تحتاج إليه؟ الأمر تقني بعض الشيء، ولكن بشكل أساسي، سيتم توجيهك إلى أفضل خادم لبعض عمليات المصادقة، وبالتالي ستحصل على استجابة أسرع.
  
التفاصيل التقنية: عند تشغيل تطبيق عميل يعمل مع Office 365 مثل Skype for Business Online أو Outlook أو Windows PowerShell أو Microsoft Azure Active Directory Sync، يجب أن تكون بيانات الاعتماد الخاصة بك مصادق عليه. Office 365 سجل CNAME يشير إلى نقطة نهاية المصادقة الصحيحة لموقعك، مما يضمن أوقات الاستجابة السريعة للمصادقة.
  
إذا كان سجل CNAME هذا مفقودا لمجالك، فإن هذه التطبيقات تستخدم نقطة نهاية مصادقة افتراضية في الولايات المتحدة، مما يعني أن المصادقة قد تكون أبطأ. إذا لم يتم تكوين سجل CNAME هذا بشكل صحيح— على سبيل المثال، إذا كان لديك خطأ مطبعي في "نقاط العنوان"، فلن تتمكن هذه التطبيقات من المصادقة.
  
 **إذا Office 365 إدارة سجلات DNS** لمجالك، Office 365 إعداد سجل CNAME هذا لك. 
  
 **إذا كنت تدير سجلات DNS** لمجالك لدى مضيف DNS، يمكنك إنشاء هذا السجل بنفسك باتباع الإرشادات لمضيف [DNS](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
  
إذا كنت تخطط لنشر Office 365 وتريد معرفة المزيد حول كل سجلات DNS التي قد تحتاج إلى إضافتها أو تحديثها، فاقرأ عنها في [مرجع:](../../enterprise/external-domain-name-system-records.md) سجلات نظام أسماء المجالات الخارجية Office 365.
