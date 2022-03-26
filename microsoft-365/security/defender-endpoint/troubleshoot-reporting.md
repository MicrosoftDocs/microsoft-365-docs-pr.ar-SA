---
title: استكشاف المشاكل المتعلقة بأدوات إعداد التقارير وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender
description: تحديد المشاكل الشائعة وحلها عند محاولة الإبلاغ عن حالة الحماية برنامج الحماية من الفيروسات من Microsoft Defender في تحديث التوافق
keywords: استكشاف الأخطاء وإصلاحها وإصلاحها وتحديث التوافق وoms وشاشة العرض والتقارير برنامج الحماية من الفيروسات من Microsoft Defender
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
ms.openlocfilehash: e17f50eb02fa6fbc3c34526ca064543b7afbdea2
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63571628"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>استكشاف الأخطاء وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender التقارير في تحديث التوافق

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> في 31 مارس 2020، برنامج الحماية من الفيروسات من Microsoft Defender ميزة "تحديث التوافق". يمكنك الاستمرار في تعريف سياسات التوافق الأمني ومراجعتها [باستخدام](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) إدارة نقاط النهاية من Microsoft، مما يسمح بالتحكم بشكل أضبط في ميزات الأمان وتحديثاته.

يمكنك استخدام برنامج الحماية من الفيروسات من Microsoft Defender مع تحديث التوافق. سترى حالة تراخيص E3 وB و F1 و VL و Pro الجديدة. ومع ذلك، بالنسبة إلى تراخيص E5، ستحتاج إلى استخدام [مدخل Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). لمعرفة المزيد حول خيارات الترخيص، راجع Windows 10 [ترخيص المنتج](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

عند [استخدام Windows تحديث](/windows/deployment/update/update-compliance-using#wdav-assessment) التحليلات للحصول على تقارير حول حالة حماية الأجهزة أو نقاط النهاية في شبكتك التي تستخدم برنامج الحماية من الفيروسات من Microsoft Defender، قد تواجه مشاكل أو مشاكل.

عادة ما تكون المؤشرات الأكثر شيوعا لمشكلة ما هي:

- لن ترى سوى عدد صغير أو مجموعة فرعية من جميع الأجهزة التي كنت تتوقع رؤياها
- لا يمكنك رؤية أي أجهزة على الإطلاق
- التقارير والمعلومات التي تراها قديمة (أقدم من بضعة أيام)

للحصول على رموز الخطأ وم IDs الأحداث الشائعة ذات الصلة برنامج الحماية من الفيروسات من Microsoft Defender الخدمة غير المرتبطة بتحديث التوافق، راجع برنامج الحماية من الفيروسات من Microsoft Defender [الأحداث](troubleshoot-microsoft-defender-antivirus.md).

هناك ثلاث خطوات لا استكشاف هذه المشاكل وإصلاحها:

1. تأكد من أنك قد أوفيت بكل المتطلبات الأساسية
2. التحقق من اتصالك بالخدمة المستندة إلى Windows Defender المستندة إلى السحابة
3. إرسال سجلات الدعم

> [!IMPORTANT]
> يستغرق عادة ظهور الأجهزة في تحديث التوافق 3 أيام.

## <a name="confirm-prerequisites"></a>تأكيد المتطلبات الأساسية

لكي تظهر الأجهزة بشكل صحيح في "توافق التحديث"، يجب أن تفي ببعض المتطلبات الأساسية لكل من خدمة "تحديث التوافق" برنامج الحماية من الفيروسات من Microsoft Defender:

>[!div class="checklist"]
>
> - تستخدم نقاط النهاية برنامج الحماية من الفيروسات من Microsoft Defender تطبيق الحماية من الفيروسات الوحيد. [سيؤدي استخدام أي تطبيق آخر لمكافحة الفيروسات برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md) تعطيل نفسه ولن يتم إعداد التقارير حول نقطة النهاية في تحديث التوافق.
> - [يتم تمكين الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md).
> - يمكن أن تتصل نقاط [النهاية برنامج الحماية من الفيروسات من Microsoft Defender السحابة](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - إذا كانت نقطة النهاية قيد التشغيل Windows 10 1607 أو إصدار سابق، Windows 10 البيانات التشخيصية إلى [المستوى المحسن](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level).
> - لقد انتهت 3 أيام منذ تلبية جميع المتطلبات

"يمكنك استخدام برنامج الحماية من الفيروسات من Microsoft Defender مع تحديث التوافق. سترى حالة تراخيص E3 وB و F1 و VL و Pro الجديدة. ومع ذلك، بالنسبة إلى تراخيص E5، ستحتاج إلى استخدام مدخل Microsoft Defender لنقطة النهاية (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). لمعرفة المزيد حول خيارات الترخيص، راجع Windows 10 ترخيص المنتج"

إذا تم كل المتطلبات الأساسية أعلاه، فقد تحتاج إلى المتابعة إلى الخطوة التالية لتجميع المعلومات التشخيصية وإرسالها إلينا.

> [!div class="nextstepaction"]
> [تجميع البيانات التشخيصية لا استكشاف الأخطاء وإصلاحها في "تحديث التوافق"](collect-diagnostic-data.md)


## <a name="related-topics"></a>المواضيع ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
