---
title: استضافة تقارير جدار الحماية في Microsoft Defender لنقطة النهاية
description: استضافة تقارير جدار الحماية وعرضها في مدخل Microsoft 365 Defender.
keywords: windows Defender، جدار الحماية
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
ms.openlocfilehash: 4903a5f5560b6997dbca32e2f7183515868f51a5
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67106744"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>استضافة تقارير جدار الحماية في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

إذا كنت مسؤولا عموميا أو مسؤول أمان، يمكنك الآن استضافة تقارير جدار الحماية إلى [مدخل Microsoft 365 Defender](https://security.microsoft.com). تمكنك هذه الميزة من عرض تقارير جدار حماية Windows 10 Windows 11 وWindows Server 2019 وWindows Server 2022 من موقع مركزي.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يجب أن تكون قيد التشغيل Windows 10 أو Windows 11 أو Windows Server 2019 أو Windows Server 2022.
- لإلحاق الأجهزة بخدمة Microsoft Defender لنقطة النهاية، راجع [هنا](onboard-configure.md).
- لكي يبدأ <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> في تلقي البيانات، يجب تمكين **أحداث التدقيق** لجدار حماية Windows Defender باستخدام الأمان المتقدم:
  - [إفلات حزمة النظام الأساسي لتصفية التدقيق](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [تدقيق تصفية اتصال النظام الأساسي](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- قم بتمكين هذه الأحداث باستخدام محرر عناصر نهج المجموعة أو نهج الأمان المحلي أو أوامر auditpol.exe. لمزيد من المعلومات، راجع [هنا](/windows/win32/fwp/auditing-and-logging).
  - الأمران PowerShell هما:
    - `auditpol /set /subcategory:"Filtering Platform Packet Drop" /failure:enable`
    - `auditpol /set /subcategory:"Filtering Platform Connection" /failure:enable`

```powershell
param (
    [switch]$remediate
)
try {

    $categories = "Filtering Platform Packet Drop,Filtering Platform Connection"
    $current = auditpol /get /subcategory:"$($categories)" /r | ConvertFrom-Csv    
    if ($current."Inclusion Setting" -ne "failure") {
        if ($remediate.IsPresent) {
            Write-Host "Remediating. No Auditing Enabled. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})"
            $output = auditpol /set /subcategory:"$($categories)" /failure:enable
            if($output -eq "The command was successfully executed.") {
                Write-Host "$($output)"
                exit 0
            }
            else {
                Write-Host "$($output)"
                exit 1
            }
        }
        else {
            Write-Host "Remediation Needed. $($current | ForEach-Object {$_.Subcategory + ":" + $_.'Inclusion Setting' + ";"})."
            exit 1
        }
    }

}
catch {
    throw $_
} 
```

## <a name="the-process"></a>العملية

> [!NOTE]
> تأكد من اتباع الإرشادات الواردة من القسم أعلاه وتكوين أجهزتك بشكل صحيح لمشاركة المعاينة المبكرة.

- بعد تمكين الأحداث، سيبدأ Microsoft 365 Defender في مراقبة البيانات، والتي تتضمن: 
   - IP البعيد
   - منفذ بعيد
   - منفذ محلي
   - IP محلي
   - اسم الكمبيوتر
   - معالجة عبر الاتصالات الواردة والصادرة
- يمكن للمسؤولين الآن رؤية نشاط جدار حماية مضيف Windows [هنا](https://security.microsoft.com/firewall).
   - يمكن تسهيل إعداد التقارير الإضافية عن طريق تنزيل [البرنامج النصي للتقارير المخصصة](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) لمراقبة أنشطة جدار حماية Windows Defender باستخدام Power BI.
   - قد يستغرق الأمر ما يصل إلى 12 ساعة قبل أن تنعكس البيانات.

## <a name="supported-scenarios"></a>السيناريوهات المدعومة

- [تقارير جدار الحماية](#firewall-reporting)
- [من "أجهزة الكمبيوتر ذات الاتصال المحظور" إلى الجهاز](#from-computers-with-a-blocked-connection-to-device)
- [الانتقال إلى التتبع المتقدم (معاينة التحديث)](#drill-into-advanced-hunting-preview-refresh)

### <a name="firewall-reporting"></a>تقارير جدار الحماية

فيما يلي بعض الأمثلة على صفحات تقرير جدار الحماية. ستجد هنا ملخصا لنشاط التطبيقات الواردة والصادرة والتطبيقات. يمكنك الوصول إلى هذه الصفحة مباشرة بالانتقال إلى <https://security.microsoft.com/firewall>.

:::image type="content" source="images/host-firewall-reporting-page.png" alt-text="صفحة إعداد التقارير لجدار حماية المضيف" lightbox="\images\host-firewall-reporting-page.png":::

يمكن أيضا الوصول إلى هذه التقارير عن طريق الانتقال إلى **تقارير** > **أجهزة** **تقارير** >  الأمان (القسم) الموجودة في أسفل بطاقة **الاتصالات الواردة المحظورة لجدار الحماية**.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>من "أجهزة الكمبيوتر ذات الاتصال المحظور" إلى الجهاز

تدعم البطاقات العناصر التفاعلية. يمكنك التنقل في نشاط الجهاز بالنقر فوق اسم الجهاز، الذي سيقوم بتشغيل مدخل Microsoft 365 Defender في علامة تبويب جديدة، وينقلك مباشرة إلى علامة التبويب **"المخطط الزمني للجهاز**".

:::image type="content" source="images/firewall-reporting-blocked-connection.png" alt-text="أجهزة الكمبيوتر ذات صفحة اتصال محظورة" lightbox="\images\firewall-reporting-blocked-connection.png":::

يمكنك الآن تحديد علامة التبويب **"الخط الزمني** "، والتي ستمنحك قائمة بالأحداث المقترنة بهذا الجهاز.

بعد النقر فوق الزر **"عوامل التصفية** " في الزاوية العلوية اليسرى من جزء العرض، حدد نوع الحدث الذي تريده. في هذه الحالة، حدد **أحداث جدار الحماية** وسيتم تصفية الجزء إلى أحداث جدار الحماية.

:::image type="content" source="images/firewall-reporting-filters-button.png" alt-text="الزر &quot;عوامل التصفية&quot;" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>الانتقال إلى التتبع المتقدم (معاينة التحديث)

تدعم تقارير جدار الحماية التنقل من البطاقة مباشرة إلى **"التتبع المتقدم** " بالنقر فوق الزر **"فتح التتبع المتقدم** ". سيتم ملء الاستعلام مسبقا.

:::image type="content" source="images/firewall-reporting-advanced-hunting.png" alt-text="الزر &quot;فتح التتبع المتقدم&quot;" lightbox="\images\firewall-reporting-advanced-hunting.png":::

يمكن الآن تنفيذ الاستعلام، ويمكن استكشاف جميع أحداث جدار الحماية ذات الصلة من آخر 30 يوما.

لمزيد من التقارير أو التغييرات المخصصة، يمكن تصدير الاستعلام إلى Power BI لمزيد من التحليل. يمكن تسهيل إعداد التقارير المخصصة عن طريق تنزيل [البرنامج النصي للتقارير المخصصة](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) لمراقبة أنشطة جدار حماية Windows Defender باستخدام Power BI.
