---
title: استكشاف مشاكل اتصال السحابة وإصلاحها ل Microsoft Defender لنقطة النهاية على Linux
ms.reviewer: ''
description: تعرف على كيفية استكشاف مشاكل الاتصال السحابي وإصلاحها ل Microsoft Defender ل Endpoint على Linux
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، السحابة، الاتصال، الاتصال
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a4c279dff6fa5a5c85a2f65144a301dde75a1615
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63571499"
---
# <a name="troubleshoot-cloud-connectivity-issues-for-microsoft-defender-for-endpoint-on-linux"></a>استكشاف مشاكل اتصال السحابة وإصلاحها ل Microsoft Defender لنقطة النهاية على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="run-the-connectivity-test"></a>تشغيل اختبار الاتصال

لاختبار ما إذا كان Defender for Endpoint على Linux يمكنه التواصل مع السحابة باستخدام إعدادات الشبكة الحالية، يمكنك تشغيل اختبار اتصال من سطر الأوامر:

```bash
mdatp connectivity test
```

الإخراج المتوقع:

```output
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

إذا فشل اختبار الاتصال، فتحقق مما إذا كان الجهاز لديه اتصال بالإنترنت وإذا تم [](microsoft-defender-endpoint-linux.md#network-connections) حظر أي من نقاط النهاية المطلوبة بواسطة المنتج بواسطة وكيل أو جدار حماية.

تشير حالات الفشل ذات الخطأ curl 35 أو 60 إلى رفض تثبيت الشهادة. يرجى التحقق مما إذا كان الاتصال ضمن فحص SSL أو HTTPS. إذا كان الأمر كذلك، أضف Microsoft Defender لنقطة النهاية إلى قائمة السماح.

## <a name="troubleshooting-steps-for-environments-without-proxy-or-with-transparent-proxy"></a>خطوات استكشاف الأخطاء وإصلاحها للبيئات بدون وكيل أو وكيل شفاف

لاختبار عدم حظر اتصال في بيئة بدون وكيل أو وكيل شفاف، ادير الأمر التالي في المحطة الطرفية:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

يجب أن يكون الإخراج من هذا الأمر مماثلا ل:

```Output
OK https://x.cp.wd.microsoft.com/api/report
OK https://cdn.x.cp.wd.microsoft.com/ping
```

## <a name="troubleshooting-steps-for-environments-with-static-proxy"></a>خطوات استكشاف الأخطاء وإصلاحها للبيئات باستخدام الوكيل الثابت

> [!WARNING]
> PAC و WPAD و وكلاء المصادقة غير معتمدين. تأكد من استخدام وكيل ثابت أو وكيل شفاف فقط.
>
> كما أن فحص SSL وتكويلات التقاطع غير معتمدة أيضا لأسباب تتعلق بالأمن. قم بتكوين استثناء لفحص SSL وخادم الوكيل الخاص بك لتمرير البيانات مباشرة من Defender for Endpoint على Linux إلى عناوين URL ذات الصلة دون أي اعتراض. لن تسمح إضافة شهادة التقاطع إلى المتجر العام بالتقاطع.

إذا كان الوكيل الثابت مطلوبا، فأضف معلمة وكيل إلى الأمر أعلاه `proxy_address:port` ، حيث تتوافق مع عنوان الوكيل والميناء:

```bash
curl -x http://proxy_address:port -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

تأكد من استخدام نفس عنوان الوكيل والميناء كما تم تكوينه في `/lib/system/system/mdatp.service` الملف. تحقق من تكوين الوكيل إذا كانت هناك أخطاء من الأوامر أعلاه.

لتعيين الوكيل ل mdatp، استخدم الأمر التالي:

```bash
mdatp config proxy set --value http://address:port 
```


عند النجاح، حاول اختبار اتصال آخر من سطر الأوامر:

```bash
mdatp connectivity test
```

إذا استمرت المشكلة، فاتصل ب دعم العملاء.

## <a name="resources"></a>الموارد

- لمزيد من المعلومات حول كيفية تكوين المنتج لاستخدام وكيل ثابت، راجع تكوين [Microsoft Defender لنقطة النهاية لاكتشاف الوكيل الثابت](linux-static-proxy-configuration.md).
