---
title: استكشاف المشاكل المتعلقة بحماية الشبكة وإصلاحها
description: الموارد ونموذج التعليمات البرمجية لا استكشاف المشاكل وإصلاحها باستخدام حماية الشبكة في Microsoft Defender لنقطة النهاية.
keywords: استكشاف الأخطاء وإصلاحها والخطأ وإصلاحها و windows defender eg و asr والقواعد والوركين وإصلاحها والتدقيق والاستبعاد والإيجابية الخاطئة والكسر والحظر و Microsoft Defender ل Endpoint
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 169a05fdde96ec780bf5e626d81846c9c2d37f26
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570717"
---
# <a name="troubleshoot-network-protection"></a>استكشاف مشاكل حماية الشبكة وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

توفر هذه المقالة معلومات حول استكشاف الأخطاء وإصلاحها لحماية [](network-protection.md)الشبكة، في حالات مثل:

- تمنع حماية الشبكة موقع ويب آمن (إيجابية خاطئة)
- فشل حماية الشبكة في حظر موقع ويب ضار مريب أو معروف (سالب خطأ)

هناك أربع خطوات يمكن من خلالها استكشاف هذه المشاكل وإصلاحها:

1. تأكيد المتطلبات الأساسية
2. استخدام وضع التدقيق لاختبار القاعدة
3. إضافة استثناءات للقاعدة المحددة (للموجبة الخاطئة)
4. إرسال سجلات الدعم

## <a name="confirm-prerequisites"></a>تأكيد المتطلبات الأساسية

ستعمل حماية الشبكة فقط على الأجهزة التي لها الشروط التالية:

> [!div class="checklist"]
>
> - يتم تشغيل نقاط النهاية Windows 10 Pro أو إصدار Enterprise، الإصدار 1709 أو الإصدارات الأحدث.
> - تستخدم نقاط النهاية برنامج الحماية من الفيروسات من Microsoft Defender تطبيق الحماية من الفيروسات الوحيد. [تعرف على ما يحدث عند استخدام حل](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility) برنامج الحماية من الفيروسات غير Microsoft.
> - [يتم تمكين الحماية](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) في الوقت الحقيقي.
> - [يتم تمكين الحماية التي يتم تسليمها](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) من السحابة.
> - وضع التدقيق غير ممكن. استخدم [نهج المجموعة](enable-network-protection.md#group-policy) لتعيين القاعدة إلى **معطل** (القيمة: **0**).

## <a name="use-audit-mode"></a>استخدام وضع التدقيق

يمكنك تمكين حماية الشبكة في وضع التدقيق ثم زيارة موقع ويب أنشأناه ل عرض هذه الميزة. سيتم السماح بجميع اتصالات موقع ويب بواسطة حماية الشبكة ولكن سيتم تسجيل حدث للإشارة إلى أي اتصال كان سيتم حظره إذا تم تمكين حماية الشبكة.

1. تعيين حماية الشبكة إلى **وضع التدقيق**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. قم بتنفيذ نشاط الاتصال الذي يسبب مشكلة (على سبيل المثال، محاولة زيارة الموقع، أو الاتصال عنوان IP الذي تقوم به أو لا تريد حظره).

3. [راجع سجلات أحداث حماية](network-protection.md#review-network-protection-events-in-windows-event-viewer) الشبكة لمعرفة ما إذا كانت الميزة قد حظرت الاتصال إذا تم تعيينها إلى **تمكين**.

   إذا كانت حماية الشبكة لا تمنع اتصالا تتوقع أن يتم حظره، فمكن الميزة.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>الإبلاغ عن سالب موجب أو خطأ خطأ

إذا كنت قد اختبرت الميزة باستخدام موقع العرض التوضيحي ومع وضع التدقيق، وكانت حماية الشبكة تعمل على سيناريوهات تم تكوينها مسبقا، ولكنها لا تعمل كما هو متوقع لاتصال معين، فاستخدم نموذج الإرسال المستند إلى الويب ل [Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) للتقارير عن خطأ سالب أو خطأ إيجابي لحماية الشبكة. باستخدام اشتراك E5، يمكنك أيضا توفير [ارتباط إلى أي تنبيه مقترن](alerts-queue.md).

راجع [عنوان الموجبة/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md).

## <a name="add-exclusions"></a>إضافة استثناءات
خيارات الاستثناء الحالية هي:

1.  إعداد مؤشر السماح المخصص.
2.  استخدام استثناءات IP: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3.  باستثناء عملية كاملة. لمزيد من المعلومات، [راجع برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md). 


## <a name="collect-diagnostic-data-for-file-submissions"></a>تجميع البيانات التشخيصية لملفات الإرسال

عندما تقوم ب الإبلاغ عن مشكلة تتعلق بحماية الشبكة، سيطلب منك تجميع البيانات التشخيصية التي يمكن استخدامها بواسطة فرق الدعم والهندسة من Microsoft وإرسالها للمساعدة في استكشاف المشاكل وإصلاحها.

1. افتح موجه أوامر غير مرفأ ثم غيره إلى Windows Defender:

   ```console
   cd c:\program files\windows defender
   ```

2. قم بتشغيل هذا الأمر لإنشاء سجلات التشخيص:

   ```console
   mpcmdrun -getfiles
   ```

3. أرفق الملف ب نموذج الإرسال. بشكل افتراضي، يتم حفظ سجلات التشخيص في `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>حل مشاكل الاتصال مع حماية الشبكة (لعملاء E5)

نظرا إلى البيئة التي يتم فيها تشغيل حماية الشبكة، يتعذر على Microsoft رؤية إعدادات وكيل نظام التشغيل. في بعض الحالات، يتعذر على عملاء حماية الشبكة الوصول إلى الخدمة السحابية. لحل مشاكل الاتصال باستخدام حماية الشبكة، قم بتكوين أحد مفاتيح التسجيل التالية بحيث تصبح حماية الشبكة على علم بتكوين الوكيل:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

يمكنك تكوين مفتاح التسجيل باستخدام PowerShell أو إدارة نقاط النهاية من Microsoft أو نهج المجموعة. فيما يلي بعض الموارد لمساعدتك:

- [استخدام مفاتيح التسجيل](/powershell/scripting/samples/working-with-registry-keys)
- [تكوين إعدادات العميل المخصصة Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [استخدم إعدادات نهج المجموعة لإدارة Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>راجع أيضًا

- [حماية الشبكة](network-protection.md)
- [حماية الشبكة ومصافحة TCP ثلاثية](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [تقييم حماية الشبكة](evaluate-network-protection.md)
- [تمكين حماية الشبكة](enable-network-protection.md)
- [معالجة الإيجابيات/السلبيات الخاطئة في Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
