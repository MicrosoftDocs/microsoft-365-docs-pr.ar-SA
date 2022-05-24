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
description: يمكن مسؤول معرفة كيفية تكوين الدعم للبريد الإلكتروني الوارد المجهول من مصادر IPv6 في Exchange Online Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 093ab458e8894105536e1c3dd46d2c911de440fd
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649088"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>إضافة دعم للبريد الإلكتروني الوارد المجهول عبر IPv6 في Microsoft 365

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تدعم Microsoft 365 المؤسسات التي تحتوي على علب بريد Exchange Online والمؤسسات المستقلة Exchange Online Protection (EOP) التي لا تحتوي على علب بريد Exchange Online البريد الإلكتروني الوارد المجهول عبر IPv6. يجب أن يفي خادم البريد الإلكتروني IPv6 المصدر بكل من المتطلبات التالية:

- يجب أن يحتوي عنوان IPv6 المصدر على سجل بحث عكسي صحيح ل DNS (PTR) يسمح للوجهة بالبحث عن اسم المجال من عنوان IPv6.

- يجب أن يجتاز المرسل إما التحقق من SPF (المعرف في [RFC 7208](https://tools.ietf.org/html/rfc7208)) أو [التحقق من DKIM](http://dkim.org/) (المعرف في [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

قبل أن تتمكن مؤسستك من تلقي البريد الإلكتروني الوارد المجهول عبر IPv6، يحتاج المسؤول إلى الاتصال بدعم Microsoft وطلبه. للحصول على إرشادات حول كيفية فتح طلب دعم، راجع [الاتصال بدعم منتجات الأعمال - مسؤول التعليمات](../../admin/get-help-support.md).

بعد تمكين دعم رسائل IPv6 الواردة المجهولة في مؤسستك، ستنتقل الرسالة إلى تصفية الرسائل العادية التي توفرها الخدمة.

## <a name="troubleshooting"></a>استكشاف الأخطاء وإصلاحها

- إذا لم يكن لخادم البريد الإلكتروني المصدر سجل بحث DNS عكسي ل IPv6، فسيتم رفض الرسائل بالخطأ التالي:

  > 450 4.7.25 الخدمة غير متوفرة، يجب أن يكون لدى إرسال عنوان IPv6 [2a01:111:f200:2004::240] سجل DNS عكسي.

- إذا لم يقم المرسل بتمرير التحقق من صحة SPF أو DKIM، فسيتم رفض الرسائل مع الخطأ التالي:

  > 450 4.7.26 الخدمة غير متوفرة، يجب أن تمر الرسالة المرسلة عبر IPv6 [2a01:111:f200:2004::240] بالتحقق من صحة SPF أو DKIM.

- إذا حاولت تلقي رسائل IPv6 مجهولة قبل الاشتراك، فسيتم رفض الرسالة بالخطأ التالي:

  > 550 5.2.1 الخدمة غير متوفرة، [contoso.com] لا تقبل البريد الإلكتروني عبر IPv6.

## <a name="related-topics"></a>المواضيع ذات الصلة

[دعم التحقق من صحة الرسائل الموقعة من DKIM](support-for-validation-of-dkim-signed-messages.md)
