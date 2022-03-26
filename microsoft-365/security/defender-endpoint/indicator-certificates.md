---
title: إنشاء مؤشرات استنادا إلى الشهادات
ms.reviewer: ''
description: إنشاء مؤشرات تستند إلى شهادات تعرف الكشف عن الكيانات ومنعها واستبعادها.
keywords: ioc، الشهادة، الشهادات، الإدارة، المسموح به، المحظور، الحظر، التنظيف، الضار، هاش الملف، عنوان ip، عناوين url، المجال
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7140b5714dd3660fe8dead37c3b6341d026fbb7c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63573383"
---
# <a name="create-indicators-based-on-certificates"></a>إنشاء مؤشرات استنادا إلى الشهادات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

يمكنك إنشاء مؤشرات للشهادات. تتضمن بعض حالات الاستخدام الشائعة ما يلي:

- السيناريوهات التي تحتاج فيها إلى نشر تقنيات الحظر، مثل قواعد تقليل [](attack-surface-reduction.md) مساحة الهجوم والوصول المتحكم به إلى المجلدات ولكن تحتاج إلى السماح بالسلوكيات من التطبيقات الموقعة بإضافة الشهادة في قائمة السماح.[](controlled-folders.md)
- حظر استخدام تطبيق موقع معين عبر مؤسستك. من خلال إنشاء مؤشر لحظر شهادة التطبيق، سيمنع Windows Defender AV عمليات تنفيذ الملفات (الحظر والتحري) ويتصرف "التحقيق التلقائي" و"المعالجة" بالطريقة نفسها.

## <a name="before-you-begin"></a>قبل البدء

من المهم فهم المتطلبات التالية قبل إنشاء مؤشرات للشهادات:

- تتوفر هذه الميزة إذا كانت مؤسستك برنامج الحماية من الفيروسات لـ Windows Defender تم تمكين الحماية المستندة إلى السحابة. لمزيد من المعلومات، راجع [إدارة الحماية المستندة إلى السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
- يجب أن يكون إصدار عميل مكافحة البرامج الضارة 4.18.1901.x أو إصدار أحدث.
- مدعوم على الأجهزة على أجهزة Windows 10 والإصدار 1703 أو الإصدارات الأحدث و Windows Server 2019 و Windows Server 2016 و Windows Server 2012 R2 و Windows Server 2022.
    
    >[!NOTE]
    >Windows Server 2016 Windows Server 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows Onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) لكي تعمل هذه الميزة. 

- يجب أن تكون تعريفات الحماية من الفيروسات والتهديدات م أحدث.
- تدعم هذه الميزة حاليا إدخال . CER أو . ملحقات ملفات PEM.

> [!IMPORTANT]
>
> - شهادة ورقة صالحة هي شهادة توقيع ذات مسار مصادقة صالح ويجب أن يتم تسلسلها إلى مرجع الشهادة الجذر (CA) الموثوق به من قبل Microsoft. بدلا من ذلك، يمكن استخدام شهادة مخصصة (موقعة ذاتيا) طالما أنها موثوق بها من قبل العميل (يتم تثبيت شهادة الجذر CA ضمن الجهاز المحلي 'المرجع الموثق الجذر المرجع').
> - لا يتم تضمين الأطفال أو أحد الوالدين لشهادات السماح/الحظر IOCs في وظيفة السماح/حظر IoC، بل يتم دعم شهادات أوراق العمل فقط.
> - لا يمكن حظر الشهادات الموقعة من Microsoft.

## <a name="create-an-indicator-for-certificates-from-the-settings-page"></a>إنشاء مؤشر للشهادات من صفحة الإعدادات:

> [!IMPORTANT]
> قد يستغرق إنشاء شهادة IoC وإزالتها ما يصل إلى 3 ساعات.

1. في جزء التنقل **، حدد الإعدادات** \> **نقاط** \> **النهاية** (ضمن **القواعد**).

2. حدد **إضافة مؤشر**.

3. حدد التفاصيل التالية:
   - المؤشر - حدد تفاصيل الكيان وحدد انتهاء صلاحية المؤشر.
   - الإجراء - حدد الإجراء الذي يجب اتخاذه وأقدم وصفا.
   - النطاق - تحديد نطاق مجموعة الجهاز.

4. راجع التفاصيل في علامة التبويب ملخص، ثم انقر فوق **حفظ**.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إنشاء مؤشرات](manage-indicators.md)
- [إنشاء مؤشرات للملفات](indicator-file.md)
- [إنشاء مؤشرات ل IPs أو عناوين URL/المجالات](indicator-ip-domain.md)
- [إدارة المؤشرات](indicator-manage.md)
