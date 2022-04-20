---
title: رؤى قوائم الانتظار في لوحة معلومات تدفق البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.custom: ''
ms.localizationpriority: medium
ms.assetid: 37640c80-ce6f-47e2-afd1-bc1d3c50e637
description: يمكن للمسؤولين معرفة كيفية استخدام عنصر واجهة مستخدم Queues في لوحة معلومات تدفق البريد في مركز توافق & الأمان لمراقبة تدفق البريد غير الناجح إلى المؤسسات المحلية أو الشريكة عبر الموصلات الصادرة.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 146ce26c32f1ff80a451b85fd343990db547a131
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972640"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>رؤى قوائم الانتظار في مركز التوافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

عندما يتعذر إرسال الرسائل من مؤسستك إلى خوادم البريد الإلكتروني المحلية أو الشريكة باستخدام الموصلات، يتم وضع الرسائل في قائمة الانتظار في Microsoft 365. الأمثلة الشائعة التي تسبب هذا الشرط هي:

- تم تكوين الموصل بشكل غير صحيح.
- حدثت تغييرات في الشبكات أو جدار الحماية في بيئتك المحلية.

سيستمر Microsoft 365 في إعادة محاولة التسليم لمدة 24 ساعة. بعد 24 ساعة، ستنتهي صلاحية الرسائل وسيتم إرجاعها إلى المرسلين في تقارير عدم التسليم (المعروفة أيضا باسم التقارير بعدم التسليم أو رسائل البريد المرتد).

إذا تجاوزت وحدة تخزين البريد الإلكتروني في قائمة الانتظار الحد المحدد مسبقا (القيمة الافتراضية هي 200 رسالة)، تتوفر المعلومات في المواقع التالية:

- رؤى **قوائم الانتظار** في [لوحة معلومات تدفق البريد](mail-flow-insights-v2.md) في [مركز التوافق & الأمان](https://protection.office.com). لمزيد من المعلومات، راجع [نتيجة تحليلات قوائم الانتظار في قسم لوحة معلومات تدفق البريد](#queues-insight-in-the-mail-flow-dashboard) في هذه المقالة.

- يتم عرض تنبيه في **التنبيهات الأخيرة** في لوحة معلومات التنبيهات في [مركز التوافق & الأمان](https://protection.office.com) (**لوحة معلومات** **التنبيهات** \> أو<https://protection.office.com/alertsdashboard>).

  :::image type="content" source="../../media/mfi-queued-messages-alert.png" alt-text="التنبيهات الأخيرة في لوحة معلومات التنبيهات في مركز توافق & الأمان" lightbox="../../media/mfi-queued-messages-alert.png":::

- سيتلقى المسؤولون إعلاما بالبريد الإلكتروني استنادا إلى تكوين نهج التنبيه الافتراضي المسمى **"الرسائل" الذي تم تأخيره**. لتكوين إعدادات الإعلام لهذا التنبيه، راجع القسم التالي.

  لمزيد من المعلومات حول نهج التنبيه، راجع [نهج التنبيه في مركز التوافق & الأمان](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>تخصيص تنبيهات قائمة الانتظار

1. في [مركز توافق & الأمان](https://protection.office.com)، انتقل إلى **نهج تنبيه** **التنبيهات** \> أو افتح <https://protection.office.com/alertpolicies>.

2. في صفحة **نهج التنبيه** ، ابحث عن النهج المسمى **"الرسائل" وحدده وقد تم تأخيره**.

3. في القائمة المنبثقة **للرسالة التي يتم فتحها** ، يمكنك تشغيل التنبيه أو إيقاف تشغيله وتكوين إعدادات الإعلام.

   :::image type="content" source="../../media/mfi-queued-messages-alert-policy.png" alt-text="تم تأخير تفاصيل التنبيه &quot;الرسائل&quot;" lightbox="../../media/mfi-queued-messages-alert-policy.png":::

   - **الحالة**: يمكنك تشغيل التنبيه أو إيقاف تشغيله.

   - **مستلمو البريد الإلكتروني** **والحد الأقصى للإعلام اليومي**: انقر فوق **"تحرير** " لتكوين الإعدادات التالية:

4. لتكوين إعدادات الإعلام، انقر فوق **"تحرير**". في القائمة المنبثقة **"تحرير النهج** " التي تظهر، قم بتكوين الإعدادات التالية:

   - **إرسال إعلامات بالبريد الإلكتروني**: القيمة الافتراضية قيد التشغيل.
   - **مستلمو البريد الإلكتروني**: القيمة الافتراضية هي **TenantAdmins**.
   - **حد الإعلام اليومي**: القيمة الافتراضية **ليست حدا**.
   - **الحد**: القيمة الافتراضية هي 200.

     :::image type="content" source="../../media/mfi-queued-messages-alert-policy-notification-settings.png" alt-text="تم تأخير إعدادات الإعلامات في التنبيه &quot;الرسائل&quot;" lightbox="../../media/mfi-queued-messages-alert-policy-notification-settings.png":::

5. عند الانتهاء، انقر فوق **"حفظ** **وإغلاق**".

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>رؤى قوائم الانتظار في لوحة معلومات تدفق البريد

حتى إذا لم تتجاوز وحدة تخزين الرسائل في قائمة الانتظار الحد وقمت بإنشاء تنبيه، فلا يزال بإمكانك استخدام رؤى **قوائم الانتظار** في [لوحة معلومات تدفق البريد](mail-flow-insights-v2.md) لرؤية الرسائل التي تم وضعها في قائمة الانتظار لأكثر من ساعة واحدة، واتخاذ إجراء قبل أن يصبح عدد الرسائل المدرجة في قائمة الانتظار كبيرا جدا.

:::image type="content" source="../../media/mfi-queues-widget.png" alt-text="عنصر واجهة مستخدم قوائم الانتظار في لوحة معلومات تدفق البريد في مركز التوافق & الأمان" lightbox="../../media/mfi-queues-widget.png":::

إذا نقرت فوق عدد الرسائل على عنصر واجهة المستخدم، فستظهر قائمة منبثقة **للرسائل موضوعة في قائمة الانتظار** مع المعلومات التالية:

- **عدد الرسائل في قائمة الانتظار**
- **اسم الموصل**: حدد اسم الموصل لإدارة الموصل في مركز إدارة Exchange (EAC) في <https://admin.exchange.microsoft.com/#/connectors>.
- **وقت بدء قائمة الانتظار**
- **انتهت صلاحية الرسائل الأقدم**
- **الخادم الوجهة**
- **عنوان IP الأخير**
- **الخطأ الأخير**
- **كيفية الإصلاح**: تتوفر المشاكل والحلول الشائعة. إذا كان الارتباط " **إصلاح" متوفرا الآن** ، فانقر فوقه لإصلاح المشكلة. وإلا، فانقر فوق أي ارتباطات متوفرة للحصول على مزيد من المعلومات حول الخطأ والحلول المحتملة.

:::image type="content" source="../../media/mfi-queues-details.png" alt-text="التفاصيل بعد النقر فوق نتيجة تحليلات قوائم الانتظار في لوحة معلومات تدفق البريد" lightbox="../../media/mfi-queues-details.png":::

يتم عرض القائمة المنبثقة نفسها بعد النقر فوق **قائمة انتظار "عرض"** في تفاصيل تنبيه " **الرسائل** ".

:::image type="content" source="../../media/mfi-queued-messages-alert-details.png" alt-text="تم تأخير تنبيه تفاصيل الرسائل في مركز توافق & الأمان" lightbox="../../media/mfi-queued-messages-alert-details.png":::

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول نتائج التحليلات الأخرى في لوحة معلومات تدفق البريد، راجع [رؤى تدفق البريد في مركز التوافق & الأمان](mail-flow-insights-v2.md).
