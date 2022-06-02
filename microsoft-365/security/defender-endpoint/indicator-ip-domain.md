---
title: إنشاء مؤشرات لـ IPs أو عناوين URL/المجالات
ms.reviewer: ''
description: إنشاء مؤشرات لعناوين IP وعناوين URL/المجالات التي تحدد الكشف عن الكيانات ومنعها واستبعادها.
keywords: ip، url، المجال، الإدارة، المسموح بها، المحظورة، الحظر، النظيفة، الضارة، تجزئة الملف، عنوان ip، urls، المجال
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 955f11aa44bd0defb867c25124da7c5a3769c98d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840102"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>إنشاء مؤشرات لـ IPs أو عناوين URL/المجالات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

يمكن ل Defender for Endpoint حظر ما تعتبره Microsoft عناوين IP/عناوين URL ضارة، من خلال Windows SmartScreen لمستعرضات Microsoft، ومن خلال Network Protection للمستعرضات غير التابعة ل Microsoft أو المكالمات التي تتم خارج المستعرض.

تمت إدارة بيانات تحليل ذكي للمخاطر لهذا من قبل Microsoft.

من خلال إنشاء مؤشرات لعناوين IP وعناوين URL أو المجالات، يمكنك الآن السماح بعناوين IP أو عناوين URL أو المجالات أو حظرها استنادا إلى التحليل الذكي للمخاطر. يمكنك أيضا تحذير المستخدمين بمطالبة إذا فتحوا تطبيقا محفوفا بالمخاطر. لن تمنعهم المطالبة من استخدام التطبيق ولكن يمكنك توفير رسالة مخصصة وارتباطات إلى صفحة شركة تصف الاستخدام المناسب للتطبيق. لا يزال بإمكان المستخدمين تجاوز التحذير والاستمرار في استخدام التطبيق إذا احتاجوا إليه.

يمكنك القيام بذلك من خلال صفحة الإعدادات أو حسب مجموعات الأجهزة إذا كنت تعتبر مجموعات معينة أكثر أو أقل عرضة للخطر من غيرها.

> [!NOTE]
> لا يتم اعتماد رموز التوجيه Inter-Domain (CIDR) بلا فئة لعناوين IP.

## <a name="before-you-begin"></a>قبل البدء

من المهم فهم المتطلبات الأساسية التالية قبل إنشاء مؤشرات ل IPS أو عناوين URL أو المجالات:

- يعتمد السماح ب URL/IP والحظر على حماية الشبكة لمكون Defender لنقطة النهاية لتمكينه في وضع الحظر. لمزيد من المعلومات حول حماية الشبكة وإرشادات التكوين، راجع [تمكين حماية الشبكة](enable-network-protection.md).
- يجب أن يكون إصدار عميل مكافحة البرامج الضارة 4.18.1906.x أو أحدث. 
- معتمدة على الأجهزة على Windows 10، الإصدار 1709 أو الإصدارات الأحدث، Windows 11، Windows Server 2016، Windows Server 2012 R2، Windows Server 2019، Windows Server 2022، وأجهزة Android وiOS.

    > [!NOTE]
    > يجب إلحاق Windows Server 2016 وserver Windows 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) المحلية لكي تعمل هذه الميزة.

- تأكد من تمكين **مؤشرات الشبكة المخصصة** في **Microsoft 365 Defender** \> **الإعدادات** \> **الميزات المتقدمة**. لمزيد من المعلومات، راجع [الميزات المتقدمة](advanced-features.md).
- لدعم المؤشرات على iOS، راجع [Microsoft Defender لنقطة النهاية على iOS](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).
- للحصول على دعم المؤشرات على Android، راجع [Microsoft Defender لنقطة النهاية على Android](/microsoft-365/security/defender-endpoint/android-configure#configure-custom-indicators).

> [!IMPORTANT]
> يمكن إضافة عناوين IP الخارجية فقط إلى قائمة المؤشرات. لا يمكن إنشاء مؤشرات ل IPs الداخلية.
> بالنسبة لسيناريوهات حماية الويب، نوصي باستخدام القدرات المضمنة في Microsoft Edge. يستفيد Microsoft Edge من [حماية الشبكة](network-protection.md) لفحص نسبة استخدام الشبكة ويسمح لكتل TCP وHTTP وHTTPS (TLS).
> إذا كانت هناك نهج مؤشرات URL متضاربة، يتم تطبيق المسار الأطول. على سبيل المثال، نهج مؤشر `https://support.microsoft.com/office` URL له الأسبقية على نهج `https://support.microsoft.com`مؤشر URL.

> [!NOTE]
> بالنسبة إلى جميع العمليات الأخرى، تستفيد سيناريوهات حماية الويب من حماية الشبكة للفحص والإنفاذ:
>
> - IP مدعوم لجميع البروتوكولات الثلاثة
> - يتم دعم عناوين IP الفردية فقط (لا توجد كتل CIDR أو نطاقات IP)
> - يمكن حظر عناوين URL المشفرة (المسار الكامل) فقط على مستعرضات الطرف الأول (Internet Explorer، Edge)
> - يمكن حظر عناوين URL المشفرة (FQDN فقط) خارج مستعرضات الطرف الأول (Internet Explorer، Edge)
> - يمكن تطبيق كتل مسار URL الكامل على مستوى المجال وجميع عناوين URL غير المشفرة
>
> قد يكون هناك ما يصل إلى ساعتين من زمن الانتقال (عادة أقل) بين وقت اتخاذ الإجراء، وعنوان URL وIP الذي يتم حظره.

عند استخدام وضع التحذير، يمكنك تكوين عناصر التحكم التالية:

**تجاوز القدرة**:

- الزر "السماح" في Edge
- زر السماح على الإعلام المنبثق (المستعرضات غير التابعة ل Microsoft)
- تجاوز معلمة المدة على المؤشر
- تجاوز الإنفاذ عبر مستعرضات Microsoft وغير Microsoft

**عنوان URL لإعادة التوجيه**:

- معلمة عنوان URL لإعادة التوجيه على المؤشر
- إعادة توجيه URL في Edge
- إعادة توجيه URL على الإعلام المنبثق (المستعرضات غير التابعة ل Microsoft)

لمزيد من المعلومات، راجع [تطبيقات Govern المكتشفة من قبل Microsoft Defender لنقطة النهاية](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>إنشاء مؤشر لعناوين IP أو عناوين URL أو المجالات من صفحة الإعدادات

1. في جزء التنقل، حدد **الإعدادات** \> **مؤشرات** **نقاط** \> النهاية (ضمن **القواعد**).

2. حدد **علامة التبويب عناوين IP أو عناوين URL/المجالات** .

3. حدد **إضافة عنصر**.

4. حدد التفاصيل التالية:
   - مؤشر - حدد تفاصيل الكيان وحدد انتهاء صلاحية المؤشر.
   - الإجراء - حدد الإجراء الذي يجب اتخاذه وقم بتوفير وصف.
   - النطاق - تحديد نطاق مجموعة الجهاز.

5. راجع التفاصيل في علامة التبويب "ملخص"، ثم انقر فوق **"حفظ**".

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إنشاء مؤشرات](manage-indicators.md)
- [إنشاء مؤشرات للملفات](indicator-file.md)
- [إنشاء مؤشرات استنادا إلى الشهادات](indicator-certificates.md)
- [إدارة المؤشرات](indicator-manage.md)
