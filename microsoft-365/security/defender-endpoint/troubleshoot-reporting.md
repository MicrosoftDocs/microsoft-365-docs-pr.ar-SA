---
title: استكشاف المشكلات المتعلقة بأدوات إعداد التقارير برنامج الحماية من الفيروسات من Microsoft Defender وإصلاحها
description: تحديد المشاكل الشائعة وحلها عند محاولة الإبلاغ في حالة الحماية برنامج الحماية من الفيروسات من Microsoft Defender في Update Compliance
keywords: استكشاف الأخطاء وإصلاحها، والخطأ، والإصلاح، وتحديث التوافق، وoms، والمراقبة، وتقرير، برنامج الحماية من الفيروسات من Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: bf65bb13ab45d127bf2302464f1948437e1fe02d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417963"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>استكشاف الأخطاء وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender التقارير في تحديث التوافق

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> [!IMPORTANT]
> في 31 مارس 2020، ستتم إزالة ميزة إعداد التقارير برنامج الحماية من الفيروسات من Microsoft Defender لتوافق التحديث. يمكنك الاستمرار في تحديد ومراجعة نهج التوافق الأمني باستخدام [إدارة نقاط النهاية من Microsoft](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)، ما يسمح بتحكم أدق في ميزات الأمان والتحديثات.

يمكنك استخدام برنامج الحماية من الفيروسات من Microsoft Defender مع توافق التحديث. سترى حالة تراخيص E3 وB وF1 وVL Pro. ومع ذلك، بالنسبة لتراخيص E5، تحتاج إلى استخدام [مدخل Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). لمعرفة المزيد حول خيارات الترخيص، راجع [Windows 10 خيارات ترخيص المنتجات](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

عند استخدام [Windows Analytics Update Compliance للحصول على تقارير حول حالة حماية الأجهزة أو نقاط النهاية](/windows/deployment/update/update-compliance-using#wdav-assessment) في شبكتك التي تستخدم برنامج الحماية من الفيروسات من Microsoft Defender، قد تواجه مشاكل أو مشاكل.

عادة ما تكون المؤشرات الأكثر شيوعا للمشكلة هي:

- ترى فقط عددا صغيرا أو مجموعة فرعية من جميع الأجهزة التي كنت تتوقع رؤيتها
- لا يمكنك رؤية أي أجهزة على الإطلاق
- التقارير والمعلومات التي تراها قديمة (أقدم من بضعة أيام)

للحصول على رموز الأخطاء الشائعة ومعرف الأحداث المتعلقة بخدمة برنامج الحماية من الفيروسات من Microsoft Defender غير المرتبطة بتوافق التحديث، راجع [أحداث برنامج الحماية من الفيروسات من Microsoft Defender](troubleshoot-microsoft-defender-antivirus.md).

هناك ثلاث خطوات لاستكشاف هذه المشاكل وإصلاحها:

1. تأكد من أنك استوفيت جميع المتطلبات الأساسية
2. التحقق من اتصالك بخدمة Windows Defender المستندة إلى السحابة
3. إرسال سجلات الدعم

> [!IMPORTANT]
> يستغرق ظهور الأجهزة عادة في Update Compliance 3 أيام.

## <a name="confirm-prerequisites"></a>تأكيد المتطلبات الأساسية

لكي تظهر الأجهزة بشكل صحيح في "توافق التحديث"، يجب عليك تلبية بعض المتطلبات الأساسية لكل من خدمة "توافق التحديث" ول برنامج الحماية من الفيروسات من Microsoft Defender:

>[!div class="checklist"]
>
> - تستخدم نقاط النهاية برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات الوحيد. [سيؤدي استخدام أي تطبيق آخر من تطبيقات الحماية من الفيروسات إلى تعطيل برنامج الحماية من الفيروسات من Microsoft Defender نفسه](microsoft-defender-antivirus-compatibility.md) ولن يتم الإبلاغ عن نقطة النهاية في Update Compliance.
> - [يتم تمكين الحماية التي توفرها السحابة](enable-cloud-protection-microsoft-defender-antivirus.md).
> - يمكن [لنقاط النهاية الاتصال بالسحابة برنامج الحماية من الفيروسات من Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - إذا كانت نقطة النهاية قيد التشغيل Windows 10 الإصدار 1607 أو إصدار سابق، [فيجب تعيين البيانات التشخيصية Windows 10 إلى المستوى المحسن](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level).
> - لقد مر 3 أيام منذ استيفاء جميع المتطلبات

"يمكنك استخدام برنامج الحماية من الفيروسات من Microsoft Defender مع توافق التحديث. سترى حالة تراخيص E3 وB وF1 وVL Pro. ومع ذلك، بالنسبة لتراخيص E5، تحتاج إلى استخدام مدخل Microsoft Defender لنقطة النهاية (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). لمعرفة المزيد حول خيارات الترخيص، راجع Windows 10 خيارات ترخيص المنتجات"

إذا تم استيفاء جميع المتطلبات الأساسية المذكورة أعلاه، فقد تحتاج إلى المتابعة إلى الخطوة التالية لجمع معلومات التشخيص وإرسالها إلينا.

> [!div class="nextstepaction"]
> [تجميع البيانات التشخيصية لاستكشاف أخطاء التوافق مع التحديث وإصلاحها](collect-diagnostic-data.md)

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
