---
title: Microsoft Defender for Identity VPN في Microsoft 365 Defender
description: تعرف على كيفية تجميع معلومات المحاسبة من خلال دمج VPN Microsoft Defender for Identity في Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: a5c45ecda43b32e37f7309b9a2de33810d60bd15
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469152"
---
# <a name="defender-for-identity-vpn-integration-in-microsoft-365-defender"></a>Defender for Identity VPN integration in Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة كيفية دمج [VPN مع Microsoft Defender for Identity](/defender-for-identity) في [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>كجزء من Microsoft 365 Defender، تغيرت بعض <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"></a>الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

[!INCLUDE [Product long](includes/product-long.md)] يمكن تجميع معلومات المحاسبة من حلول VPN. عند تكوينها، تتضمن صفحة ملف تعريف المستخدم معلومات من اتصالات VPN، مثل عناوين IP والمواقع التي تم إنشاء الاتصالات فيها. وهذا يكمل عملية التحقيق من خلال توفير معلومات إضافية حول نشاط المستخدم بالإضافة إلى الكشف الجديد عن اتصالات VPN غير الطبيعية. تكون المكالمة لحل عنوان IP خارجي إلى موقع مجهولة الهوية. لا يتم إرسال أي معرف شخصي في هذه المكالمة.

[!INCLUDE [Product short](includes/product-short.md)] يتكامل مع حل VPN الخاص بك من خلال الاستماع إلى أحداث محاسبة نصف القطر التي تم إعادة توجيهها إلى أدوات [!INCLUDE [Product short](includes/product-short.md)] الاستشعار. تستند هذه الآلية إلى محاسبة نصف قطرية قياسية ([RFC 2866](https://tools.ietf.org/html/rfc2866))، وموردو VPN التاليون معتمدون:

- Microsoft
- F5
- نقطة الاختيار
- Cisco ASA

## <a name="prerequisites"></a>المتطلبات الأساسية

لتمكين تكامل VPN، تأكد من تعيين المعلمات التالية:

- افتح منفذ UDP 1813 على أدوات [!INCLUDE [Product short](includes/product-short.md)] الاستشعار و/أو [!INCLUDE [Product short](includes/product-short.md)] أدوات الاستشعار مستقلة.

> [!NOTE]
>
> - من خلال **تمكين "**[!INCLUDE [Product short](includes/product-short.md)]محاسبة نصف القطر **[!INCLUDE [Product long](includes/product-long.md)]**"، سيمكن المستشعر نهج جدار الحماية Windows المسمى "استشعار" للسماح ب "محاسبة نصف القطر" الواردة على منفذ UDP 1813.
> - تكامل VPN غير معتمد في البيئات الملتزمة بمعايير معالجة المعلومات الفيدرالية (FIPS)

يستخدم المثال أدناه Microsoft التوجيه وخادم الوصول البعيد (RRAS) لوصف عملية تكوين VPN.

إذا كنت تستخدم حل VPN من جهة خارجية، فاستشارة وثائقها للحصول على إرشادات حول كيفية تمكين "محاسبة نصف القطر".

## <a name="configure-radius-accounting-on-the-vpn-system"></a>تكوين "محاسبة نصف القطر" على نظام VPN

تنفيذ الخطوات التالية على خادم RRAS.

1. افتح **وحدة التحكم التوجيه والوصول البعيد** .
1. انقر ب الماوس الأيمن فوق اسم الخادم وحدد **خصائص**.
1. في علامة **التبويب أمان** ، ضمن **موفر المحاسبة**، حدد **RADIUS Accounting** وحدد **تكوين**.

   :::image type="content" source="../../media/defender-identity/radius-setup.png" alt-text="إعداد نصف القطر" lightbox="../../media/defender-identity/radius-setup.png":::

1. في النافذة **إضافة خادم نصف** قطري، اكتب اسم **الخادم** [!INCLUDE [Product short](includes/product-short.md)] للمستشعر الأقرب (الذي لديه اتصال الشبكة). للتوفر العالي، يمكنك إضافة أدوات [!INCLUDE [Product short](includes/product-short.md)] استشعار إضافية كخادمات نصف قطرية. ضمن **المنفذ**، تأكد من تكوين الإعداد الافتراضي ل 1813. حدد **تغيير** وا اكتب سلسلة سرية مشتركة جديدة من الأحرف alphanumeric. دون السلسلة السرية المشتركة الجديدة حيث ستحتاج إلى تعبئتها لاحقا أثناء [!INCLUDE [Product short](includes/product-short.md)] التكوين. حدد المربع **إرسال حساب نصف** قطري عند تشغيل الرسائل ومحاسبتها وحدد **موافق** على كل مربعات الحوار المفتوحة.

   :::image type="content" source="../../media/defender-identity/vpn-set-accounting.png" alt-text="إعداد VPN" lightbox="../../media/defender-identity/vpn-set-accounting.png":::

## <a name="configure-vpn-in-defender-for-identity"></a>تكوين VPN في Defender for Identity

[!INCLUDE [Product short](includes/product-short.md)] تجمع بيانات VPN التي تساعد في تحديد المواقع التي تتصل منها أجهزة الكمبيوتر بالشبكة، وأن تتمكن من الكشف عن اتصالات VPN المريبة.

لتكوين بيانات VPN في [!INCLUDE [Product short](includes/product-short.md)] Microsoft 365 Defender:

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="الخيار &quot;الهويات&quot; ضمن عنصر القائمة &quot;إعدادات&quot;" lightbox="../../media/defender-identity/settings-identities.png":::

1. حدد **VPN**.
1. حدد **تمكين محاسبة نصف القطر**، وا اكتب **السرية المشتركة** التي قمت بتكوينها مسبقا على خادم VPN RRAS. ثم حدد **حفظ**.

   :::image type="content" source="../../media/defender-identity/vpn-integration.png" alt-text="تكامل VPN" lightbox="../../media/defender-identity/vpn-integration.png":::

بعد تمكين ذلك، ستستمع جميع أدوات استشعار Defender for Identity إلى المنفذ 1813 للأحداث المحاسبية نصف القطر، ويكتمل إعداد VPN الخاص بك.

بعد أن يتلقى مستشعر Defender for Identity أحداث VPN ويرسلها إلى خدمة السحابة Defender for Identity لمعناها، سيشير ملف تعريف الكيان إلى مواقع VPN وأنشطة VPN المميزة التي تم الوصول إليها في ملف التعريف سيشير إلى المواقع.

## <a name="see-also"></a>راجع أيضًا

- [التحقق من التنبيهات في Microsoft 365 Defender](../defender/investigate-alerts.md)
