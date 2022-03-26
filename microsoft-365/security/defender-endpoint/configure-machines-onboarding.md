---
title: الحصول على الأجهزة المجهزة في Microsoft Defender لنقطة النهاية
description: تعقب التكوين للأجهزة المدارة من Intune إلى Microsoft Defender ل Endpoint وزيادة معدل التكوين.
keywords: onboard, Intune management, Microsoft Defender for Endpoint, Microsoft Defender, Windows Defender, configuration management
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
ms.openlocfilehash: ef0f461bef452336052018a26970bad94400fa71
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570511"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>الحصول على الأجهزة المجهزة في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

يضيف كل جهاز مضافا الكشف عن تهديدات نقاط النهاية والرد عليها إضافية (الكشف التلقائي والاستجابة على النقط النهائية) ويزيد من الرؤية فوق نشاط الخرق في شبكتك. يضمن التهيئة أيضا أنه يمكن التحقق من الجهاز من المكونات الضعيفة بالإضافة إلى مشاكل تكوين الأمان ويمكن أن يتلقى إجراءات إصلاح هامة أثناء الهجمات.

قبل أن تتمكن من تعقب الأجهزة وإدارتها:

- [تسجيل أجهزتك في إدارة Intune](configure-machines.md#enroll-devices-to-intune-management)
- [تأكد من أن لديك الأذونات اللازمة](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>اكتشاف الأجهزة غير المحمية وتعقبها

توفر  بطاقة "التكوين" نظرة عامة عالية المستوى حول معدل التكوين من خلال مقارنة عدد أجهزة Windows التي تم بالفعل اجهزتها في Defender for Endpoint مقابل العدد الإجمالي للأجهزة المدارة Windows Intune.

![بطاقة إعداد إدارة تكوين الجهاز.](images/secconmgmt_onboarding_card.png)

*بطاقة تعرض الأجهزة المجهزة مقارنة بعدد أجهزة الكمبيوتر المدارة Windows Intune*

> [!NOTE]
> إذا كنت تستخدم إدارة التكوين أو البرنامج النصي للتهيئة أو أساليب التهيئة الأخرى التي لا تستخدم ملفات تعريف Intune، فقد تواجه تعارضات في البيانات. لحل هذه التعارضات، قم بإنشاء ملف تعريف تكوين Intune مقابل ل Defender لتهيئة نقطة النهاية وتعيين ملف التعريف هذا إلى أجهزتك.

## <a name="onboard-more-devices-with-intune-profiles"></a>الأجهزة المجهزة بشكل أكبر باستخدام ملفات تعريف Intune

يوفر Defender for Endpoint العديد من الخيارات السهلة ل [Windows الأجهزة](onboard-configure.md). ومع ذلك، بالنسبة للأجهزة المدارة من Intune، يمكنك الاستفادة من ملفات تعريف Intune لنشر أداة استشعار Defender for Endpoint بشكل ملائم لتحديد الأجهزة، مع اجهزتها بشكل فعال في الخدمة.

من بطاقة **التهيئة****، حدد تهيئة** المزيد من الأجهزة لإنشاء ملف تعريف وتعيينه على Intune. ويأخذك الارتباط إلى صفحة توافق الجهاز في Intune، التي توفر نظرة عامة مماثلة على حالة التكهف.

![صفحة توافق أجهزة Microsoft Defender لنقطة النهاية على إدارة أجهزة Intune.](images/secconmgmt_onboarding_1deviceconfprofile.png)

*صفحة توافق أجهزة Microsoft Defender لنقطة النهاية على إدارة أجهزة Intune*

> [!TIP]
> بدلا من ذلك، يمكنك الانتقال إلى صفحة التوافق لتوافق تعيين نقاط النهاية في مدخل [Microsoft Azure](https://portal.azure.com/) من كل **الخدمات > Intune > توافق > Microsoft Defender ATP**.

> [!NOTE]
> إذا كنت تريد عرض أحدث بيانات الجهاز، انقر فوق قائمة **الأجهزة بدون أداة استشعار ATP**.

من صفحة توافق الجهاز، أنشئ ملف تعريف تكوين خصيصا لنشر أداة استشعار Defender لنقطة النهاية، ثم عين ملف التعريف هذا إلى الأجهزة التي تريد ا متنها. للقيام بذلك، يمكنك إما:

- حدد **إنشاء ملف تعريف تكوين الجهاز لتكوين أداة استشعار ATP** للبدء بملف تعريف تكوين جهاز محدد مسبقا.
- إنشاء ملف تعريف تكوين الجهاز من البداية.

لمزيد من المعلومات، [اقرأ حول استخدام ملفات تعريف تكوين جهاز Intune للأجهزة المجهزة على Defender لنقطة النهاية](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [التأكد من تكوين أجهزتك بشكل صحيح](configure-machines.md)
- [زيادة التوافق مع خط أساسي أمان Defender for Endpoint](configure-machines-security-baseline.md)
- [تحسين عمليات نشر قاعدة ASR واكتشافها](configure-machines-asr.md)
