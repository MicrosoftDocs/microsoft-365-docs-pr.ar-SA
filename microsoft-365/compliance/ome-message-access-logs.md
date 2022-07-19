---
title: سجل نشاط مدخل الرسالة المشفرة
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/12/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: تتوفر سجلات الوصول للرسائل المشفرة التي يتم استردادها من خلال مدخل الرسائل المشفرة.
ms.openlocfilehash: 50656d1695d8fc3d6e81de6afc03b3f4e3c5ccee
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/13/2022
ms.locfileid: "66857287"
---
# <a name="encrypted-message-portal-activity-log-by-microsoft-purview-advanced-message-encryption-preview"></a>سجل نشاط مدخل الرسالة المشفرة بواسطة تشفير الرسائل المتقدم ل Microsoft Purview (معاينة)

تتوفر سجلات الوصول للرسائل المشفرة من خلال مدخل الرسائل المشفرة الذي يسمح لمؤسستك بتحديد وقت قراءة الرسائل وإعادة توجيهها من قبل المستلمين الخارجيين. لضمان توفر السجلات لأي مستلمين خارجيين، يجب تطبيق قالب علامة تجارية مخصص على رسائل البريد الإلكتروني المحمية التي ترسلها مؤسستك إلى المستلمين الخارجيين الذين يفرضون تجربة المدخل. راجع [إضافة العلامة التجارية لمؤسستك إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md).

## <a name="enabling-message-access-audit-logs-in-powershell"></a>تمكين سجلات تدقيق الوصول إلى الرسائل في PowerShell

يمكن تمكين سجل الوصول باستخدام Exchange Online PowerShell. تحدد المعلمة *-EnablePortalTrackingLogs* Set-IrmConfiguration ما إذا كان يجب تمكين سجلات التدقيق للوصول إلى مدخل الرسالة المشفرة. القيم الصحيحة هي:

- $true: تشغيل ميزة التدقيق.
- $false: إيقاف تشغيل ميزة التدقيق

مثال: Set-IrmConfiguration -EnablePortalTrackingLogs $true

To learn more, see [Set-IRMConfiguration (ExchangePowerShell)](/powershell/module/exchange/set-irmconfiguration).

## <a name="message-access-audit-information"></a>معلومات تدقيق الوصول إلى الرسائل

يحتوي سجل الوصول على إدخالات للرسائل المرسلة عبر مدخل الرسائل المشفرة لأنواع الأنشطة التالية:

- الطابع الزمني لتسجيل دخول المستخدم الخارجي وطريقة المصادقة
- قراءة المستخدم الخارجي للرسائل أو المرفقات
- تنزيل المرفقات
- ردود البريد وإعادة توجيهها

لمزيد من المعلومات حول مخطط سجل الوصول إلى الرسائل، راجع [البحث في سجل التدقيق في مدخل التوافق](search-the-audit-log-in-security-and-compliance.md#encrypted-message-portal-activities).

## <a name="search-for-events-in-the-message-access-logs"></a>البحث عن الأحداث في سجلات الوصول إلى الرسائل

لعرض الأحداث التي تم التقاطها في سجلات الوصول إلى الرسالة:

1. في مدخل التوافق في Microsoft Purview، ضمن **"Solutions**"، حدد **"Audit**".
1. ضمن **"بحث"**، انقر فوق القائمة المنسدلة **للأنشطة** واكتب أنشطة مدخل الرسائل المشفرة.
1. ضمن أنشطة مدخل الرسالة المشفرة، حدد أنواع الأحداث لاستخدامها في البحث. تعيين نطاق التاريخ للبحث (الافتراضي هو الأسبوع السابق)، يمكنك أيضا إضافة مستخدم معين في مؤسستك بشكل اختياري للبحث. عندما تصبح جاهزا، حدد **"بحث**".
1. حدد حدثا من القائمة لعرض خصائص التدقيق.
