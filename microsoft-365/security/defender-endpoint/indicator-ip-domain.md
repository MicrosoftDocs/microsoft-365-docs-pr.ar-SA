---
title: إنشاء مؤشرات ل IPs أو عناوين URL/المجالات
ms.reviewer: ''
description: إنشاء مؤشرات عناوين الإنترنت ومجالات URL التي تحدد الكشف عن الكيانات ومنعها واستبعادها.
keywords: ip، url، المجال، الإدارة، المسموح به، المحظور، الحظر، التنظيف، الضار، هاش الملف، عنوان ip، عناوين url، المجال
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
ms.openlocfilehash: 8865bf2138947238980b533b8b47ee9663fd5448
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63571538"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>إنشاء مؤشرات ل IPs أو عناوين URL/المجالات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

يمكن ل Defender for Endpoint حظر ما تعتبره Microsoft عناوين URL/عناوين URL ضارة، من خلال Windows Defender SmartScreen لمستعرضات Microsoft، ومن خلال حماية الشبكة للمستعرضات أو المكالمات غير الخاصة ب Microsoft التي يتم إجراءها خارج المستعرض.

وقد قامت Microsoft بإدارة مجموعة بيانات المعلومات المتعلقة بالخطر لهذا الأمر.

من خلال إنشاء مؤشرات ل IPs وعنوين URL أو المجالات، يمكنك الآن السماح ب IPs أو عناوين URL أو المجالات أو حظرها استنادا إلى معلومات المخاطر الخاصة بك. يمكنك أيضا تحذير المستخدمين بمطالبة إذا فتحوا تطبيقا خطرا. لن يمنعهم المطالبة من استخدام التطبيق، ولكن يمكنك توفير رسالة مخصصة وروابط إلى صفحة شركة تصف الاستخدام المناسب للتطبيق. لا يزال بإمكان المستخدمين تجاوز التحذير والمتابعة في استخدام التطبيق إذا لزم الأمر.

يمكنك القيام بذلك من خلال صفحة الإعدادات أو حسب مجموعات الجهاز إذا كنت تعتبر مجموعات معينة معرضة لخطر أكبر أو أقل من المجموعات الأخرى.

> [!NOTE]
> إن Inter-Domain التوجيه (CIDR) غير معتمدة.

## <a name="before-you-begin"></a>قبل البدء

من المهم فهم المتطلبات الأساسية التالية قبل إنشاء مؤشرات IPS أو عناوين URL أو المجالات:

- يعتمد السماح ب URL/IP وحظره على المكون Defender for Endpoint Network Protection لتمكينه في وضع الحظر. لمزيد من المعلومات حول إرشادات تكوين وحماية الشبكة، راجع [تمكين حماية الشبكة](enable-network-protection.md).
- يجب أن يكون إصدار عميل مكافحة البرامج الضارة 4.18.1906.x أو إصدار أحدث. 
- مدعوم على الأجهزة على أجهزة Windows 10 والإصدار 1709 أو الإصدارات الأحدث و Windows 11 و Windows Server 2016 و Windows Server 2012 R2 و Windows Server 2019 و Windows Server 2022.

    > [!NOTE]
    > Windows Server 2016 Windows Server 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows Onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) لكي تعمل هذه الميزة.

- تأكد من **تمكين مؤشرات**  \> الشبكة المخصصة في Microsoft 365 Defender **الإعدادات** \> **المتقدمة**. لمزيد من المعلومات، راجع [الميزات المتقدمة](advanced-features.md).
- للحصول على دعم المؤشرات على نظام iOS، راجع [تكوين مؤشرات مخصصة](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).

> [!IMPORTANT]
> يمكن إضافة IPs الخارجية فقط إلى قائمة المؤشرات. لا يمكن إنشاء مؤشرات ل IPs الداخلية.
> بالنسبة لسيناريوهات حماية الويب، نوصي باستخدام الإمكانات المضمنة في Microsoft Edge. Microsoft Edge على حماية الشبكة لفحص [](network-protection.md) حركة مرور الشبكة ويسمح لكتل TCP وHTTP وHTLS (TLS).
> إذا كانت هناك سياسات مؤشرات URL متضاربة، يتم تطبيق المسار الأطول. على سبيل المثال، يكون لنمط مؤشر `https://support.microsoft.com/office` URL الأسبقية على نهج مؤشر `https://support.microsoft.com`URL .

> [!NOTE]
> بالنسبة لجميع العمليات الأخرى، تستفيد سيناريوهات حماية الويب من حماية الشبكة للفحص والتنفيذ:
>
> - IP معتمد للبروتوكولات الثلاثة كلها
> - عناوين IP مفردة فقط معتمدة (لا يتم دعم كتل CIDR أو نطاقات IP)
> - يمكن حظر عناوين URL المشفرة (المسار الكامل) فقط في مستعرضات الطرف الأول (Internet Explorer، Edge)
> - يمكن حظر عناوين URL المشفرة (FQDN فقط) خارج مستعرضات الطرف الأول (Internet Explorer، Edge)
> - يمكن تطبيق كتل مسارات URL الكاملة على مستوى المجال وجميع عناوين URL غير مشفرة
>
> قد يكون هناك ما يصل إلى ساعتين من زمن زمن الوصول (عادة أقل) بين وقت اتخاذ الإجراء، وURL وIP الذي يتم حظره.

عند استخدام وضع التحذير، يمكنك تكوين عناصر التحكم التالية:

**تجاوز القدرة**:

- الزر "السماح" في Edge
- الزر "السماح" على الإعلام المنبثق (المستعرضات غير الخاصة ب Microsoft)
- تجاوز معلمة المدة على المؤشر
- تجاوز التنفيذ عبر مستعرضات Microsoft وغير Microsoft

**عنوان URL إعادة التوجيه**:

- معلمة URL إعادة التوجيه على المؤشر
- إعادة توجيه URL في Edge
- إعادة توجيه URL على الإعلام المنبثق (المستعرضات غير الخاصة ب Microsoft)

لمزيد من المعلومات، راجع [إدارة التطبيقات التي اكتشفها Microsoft Defender لنقطة النهاية](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>إنشاء مؤشر ل IPs أو عناوين URL أو المجالات من صفحة الإعدادات

1. في جزء التنقل **، حدد الإعدادات** \> **نقاط** \> **النهاية** (ضمن **القواعد**).

2. حدد عناوين **IP أو علامة التبويب عناوين URL/المجالات** .

3. حدد **إضافة عنصر**.

4. حدد التفاصيل التالية:
   - المؤشر - حدد تفاصيل الكيان وحدد انتهاء صلاحية المؤشر.
   - الإجراء - حدد الإجراء الذي يجب اتخاذه وأقدم وصفا.
   - النطاق - تحديد نطاق مجموعة الجهاز.

5. راجع التفاصيل في علامة التبويب ملخص، ثم انقر فوق **حفظ**.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إنشاء مؤشرات](manage-indicators.md)
- [إنشاء مؤشرات للملفات](indicator-file.md)
- [إنشاء مؤشرات استنادا إلى الشهادات](indicator-certificates.md)
- [إدارة المؤشرات](indicator-manage.md)
