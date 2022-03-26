---
title: إضافة دعم للبريد الإلكتروني الوارد المجهول عبر IPv6
f1.keywords:
- NOCSH
author: chrisda
ms.author: chrisda
manager: chrisda
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b68df621-0a5f-4824-8abc-41e0c4fd1398
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤول معرفة كيفية تكوين الدعم للبريد الإلكتروني الوارد المجهول من مصادر IPv6 في Exchange Online Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78b2e653aa284e34af2315ac696d7390dce71884
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63566754"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>إضافة دعم للبريد الإلكتروني الوارد المجهول عبر IPv6 في Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 المؤسسات التي Exchange Online علب البريد المحلية Exchange Online Protection مستقلة (EOP) بدون علب بريد Exchange Online البريد الإلكتروني الوارد المجهول عبر IPv6. يجب أن يلبي خادم البريد الإلكتروني IPv6 المصدر كلا من المتطلبات التالية:

- يجب أن يكون عنوان IPv6 المصدر سجل بحث DNS عكسيا صالحا (PTR) يسمح للوجهة البحث عن اسم المجال من عنوان IPv6.

- يجب أن يمر المرسل إما بالتحقق من SPF (المعرف في [RFC 7208](https://tools.ietf.org/html/rfc7208)) أو التحقق [من صحة DKIM](http://dkim.org/) (المعرفة في [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

قبل أن تتمكن مؤسستك من تلقي بريد إلكتروني وارد مجهول عبر IPv6، يجب على المسؤول الاتصال بدعم Microsoft وطلبه. للحصول على إرشادات حول كيفية فتح طلب دعم، راجع الاتصال ب دعم [منتجات الأعمال - تعليمات المسؤول](../../admin/get-help-support.md).

بعد تمكين دعم رسالة IPv6 الواردة المجهولة في مؤسستك، ستخوض الرسالة عملية تصفية الرسائل العادية التي توفرها الخدمة.

## <a name="troubleshooting"></a>استكشاف الأخطاء وإصلاحها

- إذا لم يكن لدى خادم البريد الإلكتروني المصدر سجل بحث عكسي ل IPv6 DNS، سيتم رفض الرسائل بالخطأ التالي:

  > 450 4.7.25 الخدمة غير متوفرة، يجب أن يكون لإرسال عنوان IPv6 [2a01:111:f200:2004::240] سجل DNS عكسي.

- إذا لم يجتاز المرسل التحقق من صحة SPF أو DKIM، سيتم رفض الرسائل بالخطأ التالي:

  > 450 4.7.26 الخدمة غير متوفرة، يجب أن تمر الرسالة المرسلة عبر IPv6 [2a01:111:f200:2004::240] بالتحقق من صحة SPF أو DKIM.

- إذا حاولت تلقي رسائل IPv6 مجهولة الهوية قبل الاشتراك، سيتم رفض الرسالة بالخطأ التالي:

  > 550 5.2.1 الخدمة غير متوفرة، [contoso.com] لا تقبل البريد الإلكتروني عبر IPv6.

## <a name="related-topics"></a>المواضيع ذات الصلة

[دعم التحقق من صحة الرسائل الموقعة على DKIM](support-for-validation-of-dkim-signed-messages.md)
