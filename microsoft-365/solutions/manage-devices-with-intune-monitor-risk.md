---
title: الخطوة 6. مراقبة مخاطر الأجهزة وتوافقها مع خطوط الأمان الأساسية
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: تعرف على كيفية Microsoft Intune إلى Defender for Endpoint ومراقبة مخاطر الجهاز كشرط للوصول.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- deploy security baselines
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: f58611f555b022b69211e39f149effef925dde17
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/14/2022
ms.locfileid: "63572078"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>الخطوة 6. مراقبة مخاطر الأجهزة وتوافقها مع خطوط الأمان الأساسية

بعد نشر مؤسستك ل Microsoft Defender ل Endpoint، يمكنك الحصول على مزيد من الرؤى والحماية لأجهزتك من خلال Microsoft Intune مع Defender for Endpoint. بالنسبة للأجهزة المحمولة، يشمل ذلك القدرة على مراقبة مخاطر الجهاز كشرط للوصول. بالنسبة Windows الأجهزة، يمكنك مراقبة توافق هذه الأجهزة مع خطوط الأمان الأساسية. 

![رسم توضيحي ل Defender for Endpoint Microsoft Intune Endpoint](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

في هذا الرسم التوضيحي:
- يزيد Microsoft Defender ل Endpoint إلى حد كبير من مستوى تقدم الحماية من المخاطر للأجهزة. 
- في Microsoft Intune تسمح لك الميزة "حماية التطبيقات" بتعيين "سياسات حماية التطبيقات" وإدارة الأجهزة (بما في ذلك تغييرات التكوين)، يراقب Defender for Endpoint أجهزتك باستمرار للتحكم في التهديدات ويمكنه اتخاذ إجراء تلقائي لإدارة الهجمات. 
- يمكنك استخدام Intune للأجهزة المجهزة ل Defender لنقطة النهاية. عند القيام بذلك، يمكنك أيضا تمكين هذه الأجهزة للعمل مع منع فقدان Microsoft 365 نقطة النهاية (نقطة النهاية DLP).

تتضمن هذه المقالة الخطوات التالية:
- الاتصال Microsoft Intune إلى Defender لنقطة النهاية
- مراقبة مخاطر الجهاز
- مراقبة التوافق مع خطوط الأمان الأساسية

إذا لم يتم إعداد Defender for Endpoint بالفعل، فاعمل مع مسؤول الحماية من المخاطر لإعداد [التقييم وبيئة التجربة](../security/defender/eval-defender-endpoint-overview.md). يمكنك العمل مع مجموعة التجريبية لتجرب الإمكانات في هذه المقالة.

## <a name="connect-microsoft-intune-to-defender-for-endpoint"></a>الاتصال Microsoft Intune إلى Defender لنقطة النهاية

يمكنك تكوين تكامل Microsoft Intune مع Defender for Endpoint بطريقة بسيطة. استخدم هذه المقالة: [تكوين Microsoft Defender ل Endpoint في Intune](/mem/intune/protect/advanced-threat-protection-configure). 

![الاتصال Intune إلى Microsoft Defender ل Endpoint](../media/devices/connect-intune-to-microsoft-defender.png#lightbox)

## <a name="monitor-device-risk-as-a-condition-for-access"></a>مراقبة مخاطر الجهاز كشرط للوصول

مع نشر Microsoft Defender ل Endpoint، يمكنك الاستفادة من إشارات خطر التهديدات. يسمح لك ذلك بحظر الوصول إلى الأجهزة استنادا إلى درجة المخاطر الخاصة بها. توصي Microsoft بالسماح بالوصول إلى الأجهزة ذات درجة المخاطر المتوسطة أو أدناه.

بالنسبة لنظامي التشغيل Android وiOS/iPadOS، يمكن استخدام إشارات التهديدات ضمن "سياسات حماية التطبيق" (APP). للحصول على معلومات حول تكوين هذا، راجع [إنشاء نهج حماية التطبيق وتعيينه لتعيين مستوى مخاطر الجهاز](/mem/intune/protect/advanced-threat-protection-configure).

لكل الأنظمة الأساسية، يمكنك تعيين مستوى المخاطر في سياسات توافق الأجهزة الموجودة. راجع [إنشاء نهج التوافق وتعيينه لتعيين مستوى مخاطر الجهاز](/mem/intune/protect/advanced-threat-protection-configure).

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>نشر خطوط الأمان الأساسية ومراقبة التوافق مع هذه الإعدادات

ينطبق على: Windows 10، Windows 11

المقالة، [الخطوة 5. نشر ملفات تعريف التكوين](manage-devices-with-intune-configuration-profiles.md)، يوصي ببدء استخدام ملفات تعريف التكوين باستخدام خطوط الأمان الأساسية المتوفرة Windows 10 Windows 11. يتضمن Microsoft Defender لنقطة النهاية أيضا خطوط أساسية أمان توفر إعدادات تحسن كل عناصر التحكم في الأمان في مكدس Defender لنقطة النهاية، بما في ذلك إعدادات الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية). ويتم أيضا نشر هذه باستخدام Microsoft Intune.

وبشكل مثالي، يتم نشر الأجهزة المضمنة في Defender for Endpoint كلا الخطين الأساسيين: أساس أمان Windows Intune لتأمين Windows أولا ثم الأساس أمان Defender for Endpoint الطبقات في الأعلى لتكوين عناصر تحكم أمان Defender for Endpoint بشكل مثالي.

للاستفادة من أحدث البيانات حول المخاطر والمخاطر وتقليل التعارضات مع تطور الأساسات، طبق دائما الإصدارات الأخيرة من الأساسات عبر جميع المنتجات بمجرد إصدارها. 

باستخدام Defender لنقطة النهاية، يمكنك مراقبة التوافق مع هذه الأساسات. 

![البطاقة الخاصة بمراقبة التوافق مع خطوط الأمان الأساسية](../media/devices/secconmgmt-baseline-card.png#lightbox)

لنشر خطوط الأمان الأساسية ومراقبة التوافق مع هذه الإعدادات، استخدم الخطوات في هذا الجدول.


|الخطوة  |الوصف  |
|---------|---------|
|1     |راجع المفاهيم الأساسية وقارن بين Microsoft Defender لنقطة النهاية Windows أساسيات أمان Intune. <br><br>راجع [زيادة التوافق مع Microsoft Defender لأساس أمان نقطة النهاية](../security/defender-endpoint/configure-machines-security-baseline.md) للتعرف على التوصيات.<br><br>راجع [استخدام خطوط الأمان الأساسية لتكوين Windows في Intune ](/mem/intune/protect/security-baselines) لمراجعة قائمة خطوط الأمان الأساسية المتوفرة وكيفية تفادي التعارضات.         |
|2     |  نشر Windows أساسيات الأمان ل Intune. ربما تكون قد أنجزت ذلك بالفعل إذا اتبعت الإرشادات في [الخطوة 5. نشر ملفات تعريف التكوين](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  نشر إعدادات الأساس ل Defender لنقطة النهاية ل Intune. راجع [إدارة ملفات تعريف](/mem/intune/protect/security-baselines-configure) خط الأمان Microsoft Intune لإنشاء ملف التعريف واختيار إصدار الأساس.<br><br>يمكنك أيضا اتباع الإرشادات هنا: [مراجعة وتعيين أساس أمان Microsoft Defender لنقطة النهاية](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | في Defender for Endpoint، راجع بطاقة [أساس الأمان على إدارة تكوين الجهاز](../security/defender-endpoint/configure-machines.md).          |
| | |

## <a name="next-steps"></a>الخطوات التالية
انتقل إلى [الخطوة 7. تنفيذ DLP مع قدرات حماية المعلومات على نقاط النهاية](manage-devices-with-intune-dlp-mip.md).