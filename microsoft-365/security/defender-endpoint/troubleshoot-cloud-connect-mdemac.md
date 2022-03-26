---
title: استكشاف مشاكل اتصال السحابة وإصلاحها ل Microsoft Defender لنقطة النهاية على macOS
description: يصف هذا الموضوع كيفية استكشاف مشاكل اتصال السحابة وإصلاحها ل Microsoft Defender ل Endpoint على macOS
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamf، macos، catalina، mojave، high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 677737f530e35ed52a2a1f3fe7a8d6f18c26e7b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570552"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-macos"></a>استكشاف مشاكل اتصال السحابة وإصلاحها ل Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**نظام macOS** الأساسي

يصف هذا الموضوع كيفية استكشاف مشاكل اتصال السحابة وإصلاحها ل Microsoft Defender ل Endpoint على macOS.

## <a name="run-the-connectivity-test"></a>تشغيل اختبار الاتصال
لاختبار ما إذا كان Defender for Endpoint على Mac يمكنه التواصل مع السحابة باستخدام إعدادات الشبكة الحالية، يمكنك تشغيل اختبار اتصال من سطر الأوامر:

```Bash
mdatp connectivity test
```

الإخراج المتوقع:
```Bash
Testing connection with https://cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://eu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://wu-cdn.x.cp.wd.microsoft.com/ping ... [OK]
Testing connection with https://x.cp.wd.microsoft.com/api/report ... [OK]
Testing connection with https://winatp-gw-cus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-eus.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-weu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-neu.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-ukw.microsoft.com/test ... [OK]
Testing connection with https://winatp-gw-uks.microsoft.com/test ... [OK]
Testing connection with https://eu-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://us-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://uk-v20.events.data.microsoft.com/ping ... [OK]
Testing connection with https://v20.events.data.microsoft.com/ping ... [OK]
```

إذا فشل اختبار الاتصال، فتحقق مما إذا كان الجهاز لديه اتصال بالإنترنت وإذا تم [](microsoft-defender-endpoint-mac.md#network-connections) حظر أي من نقاط النهاية المطلوبة بواسطة المنتج بواسطة وكيل أو جدار حماية.

تشير حالات الفشل التي بها خطأ في المؤشر 35 أو 60 إلى رفض تثبيت الشهادة، مما يشير إلى وجود مشكلة محتملة في فحص SSL أو HTTPS. راجع الإرشادات أدناه المتعلقة بتكوين فحص SSL.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-proxy-autoconfig-pac-or-with-web-proxy-autodiscovery-protocol-wpad"></a>خطوات استكشاف الأخطاء وإصلاحها للبيئات التي لا بها وكيل أو مع ميزة "التثدي التلقائي للوكيل" (PAC) أو باستخدام "بروتوكول الاكتشاف التلقائي لوكيل ويب" (WPAD)
استخدم الإجراء التالي لاختبار عدم حظر اتصال في بيئة بدون وكيل أو مع ميزة "التدليل التلقائي للوكيل" (PAC) أو باستخدام بروتوكول الاكتشاف التلقائي لوكيل ويب (WPAD).

إذا كان الوكيل أو جدار الحماية يمنع حركة مرور مجهولة، فتأكد من أن حركة المرور المجهولة مسموح بها في عناوين URL المدرجة سابقا.

> [!WARNING]
> إن المحترفين المصادق عليه غير معتمدين. تأكد من استخدام PAC أو WPAD أو وكيل ثابت فقط. كما أن فحص SSL وتكويلات التقاطع غير معتمدة أيضا لأسباب تتعلق بالأمن. قم بتكوين استثناء لفحص SSL وخادم الوكيل الخاص بك لتمرير البيانات مباشرة من Microsoft Defender ل Endpoint على macOS إلى عناوين URL ذات الصلة دون أي اعتراض. لن تسمح إضافة شهادة التقاطع إلى المتجر العام بالتقاطع.
لاختبار عدم حظر الاتصال: في مستعرض مثل Microsoft Edge ل Mac أو Safari افتح https://x.cp.wd.microsoft.com/api/report و https://cdn.x.cp.wd.microsoft.com/ping.

بشكل اختياري، في المحطة الطرفية، تشغيل الأمر التالي:

```Bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping' 
```

يجب أن يكون الإخراج من هذا الأمر مماثلا ل:
```bash
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```
