---
title: استضافة تقارير جدار الحماية في Microsoft Defender لنقطة النهاية
description: استضافة تقارير جدار الحماية وعرضها في Microsoft 365 Defender المدخل.
keywords: windows defender، جدار الحماية
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: e5bbdd77226f8649f2a781866fef614706e8a789
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475268"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>استضافة تقارير جدار الحماية في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

إذا كنت أحد المسؤولين، يمكنك الآن استضافة إعداد تقارير جدار الحماية Microsoft 365 Defender [المدخل](https://security.microsoft.com). تمكنك هذه الميزة من عرض Windows 10 و Windows 11 و Windows Server 2019 و Windows جدار الحماية ل Server 2022 من موقع مركزي.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يجب تشغيل Windows 10 أو Windows 11 أو Windows Server 2019 أو Windows Server 2022.
- ل علي الأجهزة المجهزه Microsoft Defender لنقطة النهاية الخدمة، راجع [هنا](onboard-configure.md).
- لكي <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل</a> لبدء تلقي البيانات، يجب تمكين "أحداث التدقيق" ل "جدار حماية Windows Defender" مع الأمان المتقدم:
  - [إسقاط حزمة النظام الأساسي لتصفية التدقيق](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [اتصال النظام الأساسي لتصفية التدقيق](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- يمكنك تمكين هذه الأحداث باستخدام نهج المجموعة كائن أو نهج الأمان المحلي أو auditpol.exe الأوامر. لمزيد من المعلومات، راجع [هنا](/windows/win32/fwp/auditing-and-logging).
  - الأمران PowerShell:
    - **auditpol /set /subcategory:"تصفية حزمة النظام الأساسي Drop" /failure:enable**
    - **auditpol /set /subcategory:"تصفية اتصال النظام الأساسي" /failure:enable**

## <a name="the-process"></a>العملية

> [!NOTE]
> تأكد من اتباع الإرشادات الواردة من المقطع أعلاه وتكوين أجهزتك بشكل صحيح للمشاركة في المعاينة المبكرة.

- بعد تمكين الأحداث، Microsoft 365 Defender البدء بمراقبة البيانات.
  - IP البعيد، المنفذ البعيد، المنفذ المحلي، IP المحلي، اسم الكمبيوتر، معالجة عبر الاتصالات الواردة والداخلة.
- يمكن للمسؤولين الآن الاطلاع على Windows جدار حماية المضيف [هنا](https://security.microsoft.com/firewall).
  - يمكن تسهيل إعداد التقارير الإضافية من خلال تنزيل البرنامج النصي ["](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall)إعداد التقارير المخصصة" لمراقبة Windows جدار الحماية ل Defender باستخدام Power BI.
  - قد يستغرق الأمر ما يصل إلى 12 ساعة قبل أن تنعكس البيانات.

## <a name="supported-scenarios"></a>السيناريوهات المعتمدة

يتم دعم السيناريوهات التالية أثناء معاينة Ring0.

### <a name="firewall-reporting"></a>الإبلاغ عن جدار الحماية

فيما يلي بعض الأمثلة لصفحات تقرير جدار الحماية. ستجد هنا ملخصا لنشاط التطبيق الصادر والداخل. يمكنك الوصول إلى هذه الصفحة مباشرة عن طريق الذهاب إلى <https://security.microsoft.com/firewall>.

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\host-firewall-reporting-page.png" alt-text="صفحة إعداد التقارير حول جدار حماية المضيف" lightbox="\images\host-firewall-reporting-page.png":::

يمكن أيضا الوصول إلى هذه التقارير عن طريق الذهاب إلى **ReportsSecurity** >  **ReportDevices** >  (مقطع) الموجود في أسفل بطاقة الاتصالات الواردة المحظورة لجدار **الحماية.**

### <a name="from-computers-with-a-blocked-connection-to-device"></a>من "أجهزة الكمبيوتر التي بها اتصال تم حظره" إلى الجهاز

تدعم البطاقات العناصر التفاعلية. يمكنك التنقل في نشاط جهاز بالنقر فوق اسم الجهاز، مما يؤدي إلى تشغيل مدخل Microsoft 365 Defender في علامة تبويب جديدة، ويأخذك مباشرة إلى علامة التبويب مخطط **زمني** للجهاز.

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\firewall-reporting-blocked-connection.png" alt-text="أجهزة الكمبيوتر التي تحتوي على صفحة اتصال تم حظرها" lightbox="\images\firewall-reporting-blocked-connection.png":::

يمكنك الآن تحديد **علامة التبويب المخطط** الزمني، التي ستعطيك قائمة بالأحداث المقترنة بهذا الجهاز.

بعد النقر فوق الزر **عوامل** التصفية في الزاوية العلوية اليسرى من جزء العرض، حدد نوع الحدث الذي تريده. في هذه الحالة، حدد **أحداث جدار** الحماية وست تمت تصفية الجزء إلى أحداث جدار الحماية.

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\firewall-reporting-filters-button.png" alt-text="الزر &quot;عوامل التصفية&quot;" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>التنقل في البحث المتقدم (تحديث المعاينة)

تدعم تقارير جدار الحماية عملية التنقيب من البطاقة مباشرة إلى **"** الصيد المتقدم" بالنقر فوق **الزر "فتح الصيد** المتقدم". سيتم ملء الاستعلام مسبقا.

> [!div class="mx-imgBorder"]
> :::image type="content" source="\images\firewall-reporting-advanced-hunting.png" alt-text="الزر &quot;فتح البحث المتقدم&quot;" lightbox="\images\firewall-reporting-advanced-hunting.png":::

يمكن الآن تنفيذ الاستعلام، ويمكن استكشاف كل أحداث جدار الحماية ذات الصلة من آخر 30 يوما.

للحصول على تقارير إضافية أو تغييرات مخصصة، يمكن تصدير الاستعلام إلى Power BI لمزيد من التحليل. يمكن تسهيل إعداد التقارير المخصصة من خلال تنزيل البرنامج النصي ["](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall)إعداد التقارير المخصصة" لمراقبة Windows جدار الحماية ل Defender باستخدام Power BI.
