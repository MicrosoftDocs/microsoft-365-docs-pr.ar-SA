---
title: إعداد تقارير جدار حماية المضيف في Microsoft Defender لنقطة النهاية
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
ms.openlocfilehash: b5aaad7363b42e18a0ca21e4d56d118218cec1a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63578257"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>إعداد تقارير جدار حماية المضيف في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

إذا كنت أحد المسؤولين، يمكنك الآن استضافة إعداد تقارير جدار الحماية Microsoft 365 Defender [المدخل](https://security.microsoft.com). تمكنك هذه الميزة من عرض Windows 10 و Windows 11 و Windows Server 2019 و Windows جدار الحماية ل Server 2022 من موقع مركزي.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يجب تشغيل Windows 10 أو Windows 11 أو Windows Server 2019 أو Windows Server 2022.
- لتكوين الأجهزة على خدمة Microsoft Defender for Endpoint، راجع [هنا](onboard-configure.md).
- لكي <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل</a> لبدء تلقي البيانات، يجب تمكين "أحداث التدقيق" ل "جدار حماية Windows Defender" مع الأمان المتقدم:
  - [إسقاط حزمة النظام الأساسي لتصفية التدقيق](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [اتصال النظام الأساسي لتصفية التدقيق](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- يمكنك تمكين هذه الأحداث باستخدام محرر كائن نهج المجموعة أو نهج الأمان المحلي أو auditpol.exe الأوامر. لمزيد من المعلومات، راجع [هنا](/windows/win32/fwp/auditing-and-logging).
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
> ![صفحة إعداد تقارير جدار حماية المضيف.](\images\host-firewall-reporting-page.png)

يمكن أيضا الوصول إلى هذه التقارير عن طريق الذهاب إلى **ReportsSecurity** >  **ReportDevices** >  (مقطع) الموجود في أسفل بطاقة الاتصالات الواردة المحظورة لجدار **الحماية.**

### <a name="from-computers-with-a-blocked-connection-to-device"></a>من "أجهزة الكمبيوتر التي بها اتصال تم حظره" إلى الجهاز

تدعم البطاقات العناصر التفاعلية. يمكنك التنقل في نشاط جهاز بالنقر فوق اسم الجهاز، مما يؤدي إلى تشغيل مدخل Microsoft 365 Defender في علامة تبويب جديدة، ويأخذك مباشرة إلى علامة التبويب مخطط **زمني** للجهاز.

> [!div class="mx-imgBorder"]
> ![أجهزة كمبيوتر ذات اتصال تم حظره.](\images\firewall-reporting-blocked-connection.png)

يمكنك الآن تحديد **علامة التبويب المخطط** الزمني، التي ستعطيك قائمة بالأحداث المقترنة بهذا الجهاز.

بعد النقر فوق الزر **عوامل** التصفية في الزاوية العلوية اليسرى من جزء العرض، حدد نوع الحدث الذي تريده. في هذه الحالة، حدد **أحداث جدار** الحماية وست تمت تصفية الجزء إلى أحداث جدار الحماية.

> [!div class="mx-imgBorder"]
> ![زر عوامل التصفية.](\images\firewall-reporting-filters-button.png)

### <a name="drill-into-advanced-hunting-preview-refresh"></a>التنقل في البحث المتقدم (تحديث المعاينة)

تدعم تقارير جدار الحماية عملية التنقيب من البطاقة مباشرة إلى **"** الصيد المتقدم" بالنقر فوق **الزر "فتح الصيد** المتقدم". سيتم ملء الاستعلام مسبقا.

> [!div class="mx-imgBorder"]
> ![فتح زر البحث المتقدم.](\images\firewall-reporting-advanced-hunting.png)

يمكن الآن تنفيذ الاستعلام، ويمكن استكشاف كل أحداث جدار الحماية ذات الصلة من آخر 30 يوما.

للحصول على تقارير إضافية أو تغييرات مخصصة، يمكن تصدير الاستعلام إلى Power BI لمزيد من التحليل. يمكن تسهيل إعداد التقارير المخصصة من خلال تنزيل البرنامج النصي ["](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall)إعداد التقارير المخصصة" لمراقبة Windows جدار الحماية ل Defender باستخدام Power BI.
