---
title: استكشاف المشاكل المتعلقة بحماية الشبكة وإصلاحها
description: الموارد وعينة التعليمات البرمجية لاستكشاف المشكلات المتعلقة بحماية الشبكة وإصلاحها في Microsoft Defender لنقطة النهاية.
keywords: استكشاف الأخطاء وإصلاحها، والخطأ، وإصلاحها، وwindows defender eg، و asr، والقواعد، والوركين، واستكشاف الأخطاء وإصلاحها، والتدقيق، والاستبعاد، والإيجابية الخاطئة، والمعطلة، والحظر، Microsoft Defender لنقطة النهاية
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
ms.openlocfilehash: fbb3a9e038dcd9f342065d538762b41c0673f7e6
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783150"
---
# <a name="troubleshoot-network-protection"></a>استكشاف أخطاء حماية الشبكة وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

توفر هذه المقالة معلومات استكشاف الأخطاء وإصلاحها [لحماية الشبكة](network-protection.md)، في حالات، مثل:

- تمنع حماية الشبكة موقع ويب آمن (إيجابي زائف)
- فشل حماية الشبكة في حظر موقع ويب ضار مريب أو معروف (سلبي خاطئ)

هناك أربع خطوات لاستكشاف هذه المشاكل وإصلاحها:

1. تأكيد المتطلبات الأساسية
2. استخدام وضع التدقيق لاختبار القاعدة
3. إضافة استثناءات للقاعدة المحددة (للإيجابيات الخاطئة)
4. إرسال سجلات الدعم

## <a name="confirm-prerequisites"></a>تأكيد المتطلبات الأساسية

ستعمل حماية الشبكة فقط على الأجهزة التي تتضمن الشروط التالية:

> [!div class="checklist"]
>
> - يتم تشغيل نقاط النهاية Windows 10 Pro أو إصدار Enterprise، الإصدار 1709 أو الإصدارات الأحدث.
> - تستخدم نقاط النهاية برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات الوحيد. [تعرف على ما يحدث عند استخدام حل الحماية من الفيروسات غير](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility) التابع ل Microsoft.
> - يتم تمكين [الحماية في الوقت الحقيقي](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus).
> - يتم تمكين [الحماية التي توفرها السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus).
> - لم يتم تمكين وضع التدقيق. استخدم [نهج المجموعة](enable-network-protection.md#group-policy) لتعيين القاعدة إلى **معطل** (القيمة: **0**).

## <a name="use-audit-mode"></a>استخدام وضع التدقيق

يمكنك تمكين حماية الشبكة في وضع التدقيق ثم زيارة موقع ويب أنشأناه لعرض الميزة. سيتم السماح بكافة اتصالات موقع الويب بواسطة حماية الشبكة ولكن سيتم تسجيل حدث للإشارة إلى أي اتصال كان سيتم حظره إذا تم تمكين حماية الشبكة.

1. تعيين حماية الشبكة إلى **وضع التدقيق**.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection AuditMode
   ```

2. قم بتنفيذ نشاط الاتصال الذي يسبب مشكلة (على سبيل المثال، محاولة زيارة الموقع أو الاتصال بعنوان IP الذي تقوم به أو لا تريد حظره).

3. [راجع سجلات أحداث حماية الشبكة](network-protection.md#review-network-protection-events-in-windows-event-viewer) لمعرفة ما إذا كانت الميزة ستحظر الاتصال إذا تم تعيينه إلى **Enabled**.

   إذا كانت حماية الشبكة لا تحظر اتصالا تتوقع أنه يجب حظره، فقم بتمكين الميزة.

   ```PowerShell
   Set-MpPreference -EnableNetworkProtection Enabled
   ```

## <a name="report-a-false-positive-or-false-negative"></a>الإبلاغ عن قيمة سلبية خاطئة أو إيجابية خاطئة

إذا قمت باختبار الميزة باستخدام موقع العرض التوضيحي ووضع التدقيق، وتعمل حماية الشبكة على سيناريوهات تم تكوينها مسبقا، ولكنها لا تعمل كما هو متوقع لاتصال معين، فاستخدم [نموذج الإرسال المستند إلى الويب Windows Defender Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) للإبلاغ عن إيجابية سلبية أو خاطئة لحماية الشبكة. باستخدام اشتراك E5، يمكنك أيضا [توفير ارتباط إلى أي تنبيه مقترن](alerts-queue.md).

راجع [النتائج الإيجابية/السلبيات الخاطئة للعنوان في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md).

## <a name="add-exclusions"></a>إضافة استثناءات

خيارات الاستبعاد الحالية هي:

1. إعداد مؤشر سماح مخصص.
2. استخدام استثناءات IP: `Add-MpPreference -ExclusionIpAddress 192.168.1.1`
3. استبعاد عملية بأكملها. لمزيد من المعلومات، راجع [برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md). 

## <a name="collect-diagnostic-data-for-file-submissions"></a>تجميع البيانات التشخيصية الخاصة بإرسالات الملفات

عند الإبلاغ عن مشكلة تتعلق بحماية الشبكة، يطلب منك جمع البيانات التشخيصية وإرسالها التي يمكن أن تستخدمها فرق الدعم والهندسة في Microsoft للمساعدة في استكشاف المشكلات وإصلاحها.

1. افتح موجه أوامر غير مقيد وغير إلى دليل Windows Defender:

   ```console
   cd c:\program files\windows defender
   ```

2. تشغيل هذا الأمر لإنشاء سجلات التشخيص:

   ```console
   mpcmdrun -getfiles
   ```

3. إرفاق الملف بنموذج الإرسال. بشكل افتراضي، يتم حفظ سجلات التشخيص في `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

## <a name="resolve-connectivity-issues-with-network-protection-for-e5-customers"></a>حل مشكلات الاتصال باستخدام حماية الشبكة (لعملاء E5)

نظرا للبيئة التي يتم فيها تشغيل حماية الشبكة، يتعذر على Microsoft رؤية إعدادات وكيل نظام التشغيل. في بعض الحالات، يتعذر على عملاء حماية الشبكة الوصول إلى خدمة السحابة. لحل مشكلات الاتصال مع حماية الشبكة، قم بتكوين أحد مفاتيح التسجيل التالية بحيث تصبح حماية الشبكة على دراية بتكوين الوكيل:

```powershell
Set-MpPreference -ProxyServer <proxy IP address: Port>
```

---OR---

```powershell
Set-MpPreference -ProxyPacUrl <Proxy PAC url>
```

يمكنك تكوين مفتاح التسجيل باستخدام PowerShell أو إدارة نقاط النهاية من Microsoft أو نهج المجموعة. فيما يلي بعض الموارد لمساعدتك:

- [العمل باستخدام مفاتيح التسجيل](/powershell/scripting/samples/working-with-registry-keys)
- [تكوين إعدادات العميل المخصصة Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client)
- [استخدام إعدادات نهج المجموعة لإدارة Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-group-policies)

## <a name="see-also"></a>راجع أيضًا

- [حماية الشبكة](network-protection.md)
- [حماية الشبكة والتصاق TCP ثلاثي الاتجاهات](network-protection.md#network-protection-and-the-tcp-three-way-handshake)
- [تقييم حماية الشبكة](evaluate-network-protection.md)
- [تمكين حماية الشبكة](enable-network-protection.md)
- [معالجة الإيجابيات/السلبيات الخاطئة في Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)
