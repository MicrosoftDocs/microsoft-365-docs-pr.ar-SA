---
title: الحصول على الأجهزة التي تم إلحاقها Microsoft Defender لنقطة النهاية
description: تعقب إلحاق الأجهزة المدارة من Intune Microsoft Defender لنقطة النهاية وزيادة معدل الإلحاق.
keywords: إلحاق، وإدارة Intune، Microsoft Defender لنقطة النهاية، وMicrosoft Defender، Windows Defender، وإدارة التكوين
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
ms.openlocfilehash: 1e77f404b70ee770bd4d5c441362739cc7b2f13c
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622953"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>الحصول على الأجهزة التي تم إلحاقها Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

يضيف كل جهاز تم إلحاقه مستشعر الكشف عن تهديدات نقاط النهاية والرد عليها إضافي (الكشف التلقائي والاستجابة على النقط النهائية) ويزيد من الرؤية عبر نشاط الخرق في شبكتك. يضمن الإلحاق أيضا أنه يمكن التحقق من الجهاز بحثا عن المكونات الضعيفة بالإضافة إلى مشكلات تكوين الأمان ويمكن أن يتلقى إجراءات المعالجة الهامة أثناء الهجمات.

قبل أن تتمكن من تعقب إلحاق الأجهزة وإدارتها:

- [تسجيل أجهزتك في إدارة Intune](configure-machines.md#enroll-devices-to-intune-management)
- [تأكد من أن لديك الأذونات اللازمة](configure-machines.md#obtain-required-permissions)

شاهد هذا الفيديو لمعرفة كيفية إلحاق العملاء بسهولة باستخدام Microsoft Defender لنقطة النهاية.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4bGqr?rel=0]

## <a name="discover-and-track-unprotected-devices"></a>اكتشاف الأجهزة غير المحمية وتعقبها

توفر بطاقة **الإلحاق** نظرة عامة عالية المستوى على معدل الإلحاق من خلال مقارنة عدد أجهزة Windows التي تم إلحاقها بالفعل ب Defender لنقطة النهاية مقابل العدد الإجمالي لأجهزة Windows المدارة من Intune.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="بطاقة إعداد إدارة تكوين الجهاز" lightbox="images/secconmgmt_onboarding_card.png":::

*بطاقة تعرض الأجهزة الملحقة مقارنة بالعدد الإجمالي لأجهزة Windows المدارة من Intune*

> [!NOTE]
> إذا استخدمت Configuration Manager أو البرنامج النصي الإلحاقي أو أساليب الإلحاق الأخرى التي لا تستخدم ملفات تعريف Intune، فقد تواجه اختلافات في البيانات. لحل هذه الاختلافات، قم بإنشاء ملف تعريف تكوين Intune مطابق لإلحاق Defender لنقطة النهاية وتعيين ملف التعريف هذا إلى أجهزتك.

## <a name="onboard-more-devices-with-intune-profiles"></a>إلحاق المزيد من الأجهزة بملفات تعريف Intune

يوفر Defender لنقطة النهاية العديد من الخيارات [الملائمة لإلحاق أجهزة Windows](onboard-configure.md). ومع ذلك، بالنسبة للأجهزة المدارة من Intune، يمكنك الاستفادة من ملفات تعريف Intune لنشر مستشعر Defender لنقطة النهاية بسهولة لتحديد الأجهزة، مع إلحاق هذه الأجهزة للخدمة بشكل فعال.

من بطاقة **الإلحاق** ، حدد **"إلحاق المزيد من الأجهزة** " لإنشاء ملف تعريف وتعيينه على Intune. ينقلك الارتباط إلى صفحة توافق الجهاز في Intune، والتي توفر نظرة عامة مماثلة على حالة الإلحاق.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="صفحة توافق الجهاز Microsoft Defender لنقطة النهاية على إدارة أجهزة Intune" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Microsoft Defender لنقطة النهاية صفحة توافق الجهاز على إدارة أجهزة Intune*

> [!TIP]
> بدلا من ذلك، يمكنك الانتقال إلى صفحة توافق إلحاق Defender لنقطة النهاية في [مدخل Microsoft Azure](https://portal.azure.com/) من **جميع الخدمات > Intune > توافق الجهاز > Microsoft Defender ATP**.

> [!NOTE]
> إذا كنت ترغب في عرض أحدث بيانات الجهاز، فانقر فوق **قائمة الأجهزة بدون أداة استشعار ATP**.

من صفحة توافق الجهاز، قم بإنشاء ملف تعريف تكوين خصيصا لتوزيع مستشعر Defender لنقطة النهاية وتعيين ملف التعريف هذا إلى الأجهزة التي تريد إلحاقها. للقيام بذلك، يمكنك إما:

- حدد **إنشاء ملف تعريف تكوين جهاز لتكوين مستشعر ATP** للبدء بملف تعريف تكوين الجهاز المحدد مسبقا.
- إنشاء ملف تعريف تكوين الجهاز من البداية.

لمزيد من المعلومات، [اقرأ حول استخدام ملفات تعريف تكوين جهاز Intune لإلحاق الأجهزة ب Defender لنقطة النهاية](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [التأكد من تكوين أجهزتك بشكل صحيح](configure-machines.md)
- [زيادة التوافق مع أساس أمان Defender لنقطة النهاية](configure-machines-security-baseline.md)
- [تحسين نشر قواعد ASR والكشف عنها](configure-machines-asr.md)
