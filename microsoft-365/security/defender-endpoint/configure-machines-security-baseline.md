---
title: زيادة التوافق مع Microsoft Defender لنقطة النهاية أساسيات الأمان
description: يحدد Microsoft Defender لنقطة النهاية الأمان الأساسي عناصر التحكم في الأمان لتوفير الحماية المثلى.
keywords: إدارة Intune، Microsoft Defender لنقطة النهاية، Microsoft Defender، Microsoft Defender لنقطة النهاية ASR، أساس الأمان
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1980567c93364f35923a9a7f2433733e05878e61
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467962"
---
# <a name="increase-compliance-to-the-microsoft-defender-for-endpoint-security-baseline"></a>زيادة التوافق مع Microsoft Defender لنقطة النهاية أساسيات الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

تضمن خطوط الأمان الأساسية تكوين ميزات الأمان وفقا وإرشادات كل من خبراء الأمان Windows النظام. عند النشر، يحدد خط أساسي أمان Defender for Endpoint عناصر تحكم أمان Defender لنقطة النهاية لتوفير الحماية المثلى.

لفهم خطوط الأمان الأساسية وكيفية تعيينها في Intune باستخدام ملفات تعريف التكوين، [اقرأ الأسئلة الشائعة هذه](/intune/security-baselines#q--a).

قبل أن تتمكن من نشر التوافق مع خطوط الأمان الأساسية وتعقبه:

- [تسجيل أجهزتك في إدارة Intune](configure-machines.md#enroll-devices-to-intune-management)
- [تأكد من أن لديك الأذونات اللازمة](configure-machines.md#obtain-required-permissions)

## <a name="compare-the-microsoft-defender-for-endpoint-and-the-windows-intune-security-baselines"></a>مقارنة Microsoft Defender لنقطة النهاية Windows أمان Intune

يوفر Windows أساسي أمان Intune مجموعة شاملة من الإعدادات الموصى بها المطلوبة لتكوين الأجهزة التي تعمل Windows بشكل آمن، بما في ذلك إعدادات المستعرض وإعدادات PowerShell وإعدادات بعض ميزات الأمان مثل برنامج الحماية من الفيروسات من Microsoft Defender. في المقابل، يوفر الأساس Defender لنقطة النهاية الإعدادات التي تحسن كل عناصر التحكم في الأمان في مكدس Defender لنقطة النهاية، بما في ذلك إعدادات الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية) بالإضافة إلى الإعدادات الموجودة أيضا في Windows  خط أمان Intune الأساسي. لمزيد من المعلومات حول كل أساس، راجع:

- [Windows أساسيات الأمان ل Intune](/intune/security-baseline-settings-windows)
- [Microsoft Defender لنقطة النهاية الأساسي ل Intune](/intune/security-baseline-settings-defender-atp)

وبشكل مثالي، يتم نشر الأجهزة المضمنة في Defender for Endpoint كلا الخطين الأساسيين: أساس أمان Windows Intune لتأمين Windows أولا ثم الأساس أمان Defender for Endpoint الطبقات في الأعلى لتكوين عناصر تحكم أمان Defender for Endpoint بشكل مثالي. للاستفادة من أحدث البيانات حول المخاطر والمخاطر وتقليل التعارضات مع تطور الأساسات، طبق دائما الإصدارات الأخيرة من الأساسات عبر جميع المنتجات بمجرد إصدارها.

> [!NOTE]
> تم تحسين أساس أمان Defender لنقطة النهاية للأجهزة الفعلية ولا يوصى حاليا باستخدامه على الأجهزة الظاهرية (VMs) أو نقاط نهاية VDI. قد تؤثر بعض إعدادات الأساس على الجلسات التفاعلية البعيدة على البيئات الظاهرية.

## <a name="monitor-compliance-to-the-defender-for-endpoint-security-baseline"></a>مراقبة التوافق مع خط أساسي أمان Defender لنقطة النهاية

توفر **بطاقة الأمان الأساسية** لإدارة [](configure-machines.md) تكوين الجهاز نظرة عامة على التوافق عبر Windows 10 والأجهزة Windows 11 التي تم تعيينها لأساس أمان Defender لنقطة النهاية.

:::image type="content" source="images/secconmgmt_baseline_card.png" alt-text="بطاقة الأساس &quot;الأمان&quot;" lightbox="images/secconmgmt_baseline_card.png":::

*بطاقة تعرض التوافق مع خط أساسي أمان Defender for Endpoint*

يتم منح كل جهاز أحد أنواع الحالة التالية:

- **مطابقة الأساس**: تتطابق إعدادات الجهاز مع كل الإعدادات في الأساس.
- **لا يطابق الأساس**: إعداد جهاز واحد على الأقل لا يطابق الخط الأساسي.
- **تكوين غير صحيح**: لم يتم تكوين إعداد أساسي واحد على الأقل بشكل صحيح على الجهاز وهو في حالة تعارض أو خطأ أو حالة معلقة.
- **غير قابل** للتطبيق: إعداد أساسي واحد على الأقل غير قابل للتطبيق على الجهاز.

لمراجعة أجهزة معينة، حدد **تكوين أساس الأمان** على البطاقة. سيتولى هذا الأمر إدارة أجهزة Intune. من هناك، حدد **حالة الجهاز** لأسماء الأجهزة ووضعها.

> [!NOTE]
> قد تواجه تعارضات في البيانات المجمعة المعروضة على صفحة إدارة تكوين الجهاز وتلك المعروضة على شاشات النظرة العامة في Intune.

## <a name="review-and-assign-the-microsoft-defender-for-endpoint-security-baseline"></a>مراجعة الأساس الأمني Microsoft Defender لنقطة النهاية وتعيينه

تعمل إدارة تكوين الأجهزة على مراقبة توافق Windows 10 الأساسي فقط Windows 11 والأجهزة التي تم تعيين خط Microsoft Defender لنقطة النهاية الأساسي الخاص بها. يمكنك مراجعة الأساس بشكل ملائم وتعيينه إلى الأجهزة على إدارة أجهزة Intune.

1. حدد **تكوين أساس الأمان على** بطاقة **خط الأمان الأساسي** للذهاب إلى إدارة أجهزة Intune. يتم عرض نظرة عامة مماثلة حول توافق الأساس.

   > [!TIP]
   > بدلا من ذلك، يمكنك الانتقال إلى أساس أمان Defender for Endpoint في مدخل Microsoft Azure من جميع الخدمات **> Intune > أمان** > أساسيات أمان > Microsoft Defender ATP.

2. إنشاء ملف تعريف جديد.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile1.png" alt-text="علامة التبويب &quot;إنشاء ملف تعريف&quot; في Microsoft Defender لنقطة النهاية نظرة عامة حول أمان Intune" lightbox="images/secconmgmt_baseline_intuneprofile1.png":::<br>
   *Microsoft Defender لنقطة النهاية نظرة عامة حول خط الأمان الأساسي في Intune*

3. أثناء إنشاء ملف التعريف، يمكنك مراجعة إعدادات معينة وضبطها على الأساس.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile2.png" alt-text="خيارات أساس الأمان أثناء إنشاء ملف التعريف على Intune" lightbox="images/secconmgmt_baseline_intuneprofile2.png":::<br>
   *خيارات أساس الأمان أثناء إنشاء ملف التعريف على Intune*

4. تعيين ملف التعريف إلى مجموعة الأجهزة المناسبة.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile3.png" alt-text="ملفات تعريف خط الأمان الأساسي على Intune" lightbox="images/secconmgmt_baseline_intuneprofile3.png":::<br>
   *تعيين ملف تعريف أساسيات الأمان على Intune*

5. أنشئ ملف التعريف لحفظه ونشره إلى مجموعة الأجهزة المعينة.

   :::image type="content" source="images/secconmgmt_baseline_intuneprofile4.png" alt-text="تعيين أساس الأمان على Intune" lightbox="images/secconmgmt_baseline_intuneprofile4.png":::<br>
   *إنشاء ملف تعريف أساسيات الأمان على Intune*

> [!TIP]
> توفر خطوط الأمان الأساسية في Intune طريقة ملائمة لتأمين أجهزتك وحمايتها بشكل شامل. [تعرف على المزيد حول خطوط الأمان الأساسية في Intune](/intune/security-baselines).

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [التأكد من تكوين أجهزتك بشكل صحيح](configure-machines.md)
- [الحصول على الأجهزة المجهزة Microsoft Defender لنقطة النهاية](configure-machines-onboarding.md)
- [تحسين عمليات نشر قاعدة ASR واكتشافها](configure-machines-asr.md)
