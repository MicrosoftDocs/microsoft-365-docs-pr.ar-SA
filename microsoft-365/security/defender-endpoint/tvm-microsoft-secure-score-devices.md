---
title: Microsoft Secure Score للأجهزة
description: تعرض نقاطك للأجهزة حالة تكوين الأمان الجماعي للأجهزة عبر التطبيقات ونظام التشغيل والشبكات والحسابات و عناصر التحكم في الأمان.
keywords: Microsoft Secure Score للأجهزة، Microsoft Defender لنقطة النهاية Microsoft Secure Score للأجهزة، نقاط آمنة، نقاط تكوين، إدارة المخاطر والثغرات الأمنية، عناصر تحكم الأمان، فرص التحسين، نقاط تكوين الأمان مع مرور الوقت، وضع الأمان، الأساس
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
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1d63e240c0698273807421a4121061630b8f3951
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499518"
---
# <a name="microsoft-secure-score-for-devices"></a>Microsoft Secure Score للأجهزة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

> [!NOTE]
> أصبحت نقاط التكوين الآن جزءا من إدارة المخاطر والثغرات الأمنية Microsoft Secure Score للأجهزة.

تكون نقاطك للأجهزة مرئية في لوحة إدارة المخاطر والثغرات الأمنية [الرئيسية](tvm-dashboard-insights.md) Microsoft 365 Defender المدخل. تعني النتيجة الأعلى ل Microsoft Secure Score للأجهزة أن نقاط النهاية الخاصة بك أكثر مرونة من هجمات تهديدات الأمان الإلكتروني. وهو يعكس حالة تكوين الأمان الجماعي للأجهزة عبر الفئات التالية:

- Application
- نظام التشغيل
- الشبكة
- الحسابات
- عناصر التحكم في الأمان

حدد فئة للذهاب إلى صفحة [**توصيات**](tvm-security-recommendation.md) الأمان وعرض التوصيات ذات الصلة.

## <a name="how-it-works"></a>كيفية عمل ذلك

> [!NOTE]
> يدعم Microsoft Secure Score للأجهزة حاليا التكوينات التي تم تعيينها عبر نهج المجموعة. بسبب دعم Intune الجزئي الحالي، قد تظهر التكوينات التي تم تعيينها من خلال Intune على أنها تكوين غير صحيح. اتصل بمسؤول تكنولوجيا المعلومات للتحقق من حالة التكوين الفعلي في حال كانت مؤسستك تستخدم Intune لإدارة التكوين الآمن.

البيانات الموجودة في بطاقة Microsoft Secure Score for Devices هي نتاج عملية اكتشاف ثغرة مستمرة ومهمة. يتم تجميعها مع تقييمات اكتشاف التكوين التي تقوم باستمرار:

- مقارنة التكوينات المجمعة بمقياس الأداء المجمع لاكتشاف الأصول التي تم تكوينها بشكل غير صحيح
- تكوينات الخريطة لنقاط الضعف التي يمكن إصلاحها أو إصلاحها جزئيا (تقليل المخاطر)
- تجميع معايير تكوين أفضل الممارسات والمحافظة عليها (الموردون، موجزات الأمان، فرق الأبحاث الداخلية)
- تجميع التغييرات في حالة تكوين عنصر التحكم في الأمان ومراقبتها من جميع الأصول

## <a name="improve-your-security-configuration"></a>تحسين تكوين الأمان

تحسين تكوين الأمان من خلال معالجة المشاكل من قائمة توصيات الأمان. بينما تفعل ذلك، يتحسن أداء Microsoft Secure Score للأجهزة وتصبح مؤسستك أكثر مرونة في مواجهة تهديدات الأمان الإلكتروني ونقاط الضعف.

1. من بطاقة Microsoft Secure Score للأجهزة في إدارة المخاطر والثغرات الأمنية المعلومات، حدد إحدى الفئات. ستشاهد قائمة التوصيات ذات الصلة بهذه الفئة. سيأخذك إلى صفحة [**توصيات**](tvm-security-recommendation.md) الأمان. إذا كنت تريد الاطلاع على كل توصيات الأمان، بمجرد الوصول إلى صفحة توصيات الأمان، أمسح حقل البحث.

2. حدد عنصر في القائمة. سيتم فتح لوحة المعلومات من خلال تفاصيل ذات صلة بالتوصية. حدد **خيارات المعالجة**.

   :::image type="content" source="images/security-controls.png" alt-text="توصيات الأمان ذات الصلة ب عناصر التحكم في الأمان" lightbox="images/security-controls.png":::

3. اقرأ الوصف لفهم سياق المشكلة وما يجب فعله بعد ذلك. حدد تاريخ الاستحقاق، وأضف الملاحظات، وحدد تصدير كل بيانات نشاط المعالجة إلى **CSV** حتى تتمكن من إرفاقه ببريد إلكتروني للمتابعة.

4. **إرسال الطلب**. سترى رسالة تأكيد بأن مهمة الإصلاح قد تم إنشاؤها.

   :::image type="content" source="images/remediation-task-created.png" alt-text="تأكيد إنشاء مهمة &quot;المعالجة&quot;" lightbox="images/remediation-task-created.png":::

5. احفظ ملف CSV.

   :::image type="content" source="images/tvm_save_csv_file.png" alt-text="الصفحة التي تحتوي على خيار حفظ ملف CSV" lightbox="images/tvm_save_csv_file.png":::

6. أرسل بريدا إلكترونيا للمتابعة إلى مسؤول تكنولوجيا المعلومات واسمح باحتوائك على الوقت الذي قمت بتم فيه نشر المعالجة في النظام.

7. راجع بطاقة **Microsoft Secure Score للأجهزة** مرة أخرى على لوحة المعلومات. سينخفض عدد توصيات عناصر التحكم في الأمان. عند تحديد **عناصر تحكم الأمان** للعودة إلى صفحة توصيات الأمان،  لن يتم إدراج العنصر الذي قمت بتعالجه هناك بعد الآن. يجب أن تزيد "نقاط Microsoft الآمنة للأجهزة".

> [!IMPORTANT]
>لتعزيز معدلات الكشف عن تقييم الضعف، قم بتنزيل تحديثات الأمان الإلزامية التالية ونشرها في شبكتك:
>
> - 19H1 العملاء | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)
> - عملاء RS5 | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
> - عملاء RS4 | [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
> - عملاء RS3 | [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
>
> لتنزيل تحديثات الأمان:
>
> 1. انتقل إلى [كتالوج Microsoft Update](https://www.catalog.update.microsoft.com/home.aspx).
> 2. مفتاح في رقم KB لتحديث الأمان الذي تحتاج إلى تنزيله، ثم انقر فوق **بحث**.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [لوحة المعلومات](tvm-dashboard-insights.md)
- [درجة التعرض للضوء](tvm-exposure-score.md)
- [توصيات الأمان](tvm-security-recommendation.md)
