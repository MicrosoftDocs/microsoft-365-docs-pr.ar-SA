---
title: الخطوة 6. مراقبة مخاطر الأجهزة وتوافقها مع أساسات الأمان
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: تعرف على كيفية توصيل Microsoft Intune ب Defender لنقطة النهاية ومراقبة مخاطر الجهاز كشرط للوصول.
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
ms.openlocfilehash: e64006873c3419b9c6d93d3b367a5753f5478738
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651400"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>الخطوة 6. مراقبة مخاطر الأجهزة وتوافقها مع أساسات الأمان

بعد نشر مؤسستك Microsoft Defender لنقطة النهاية، يمكنك الحصول على رؤى وحماية أكبر لأجهزتك من خلال دمج Microsoft Intune مع Defender لنقطة النهاية. بالنسبة إلى الأجهزة المحمولة، يشمل ذلك القدرة على مراقبة مخاطر الجهاز كشرط للوصول. بالنسبة للأجهزة Windows، يمكنك مراقبة توافق هذه الأجهزة مع أساسيات الأمان. 

ملاحظة: يتضمن نشر Microsoft Defender لنقطة النهاية نقاط نهاية الإلحاق. لمزيد من المعلومات حول إلحاق الأجهزة Microsoft 365 capabilties، راجع [تسجيل الأجهزة مقابل أجهزة الإلحاق](manage-devices-with-intune-overview.md#enrolling-devices-vs-onboarding-devices).  

![Defender لنقطة النهاية والتوضيح Microsoft Intune التكامل](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

في هذا الرسم التوضيحي:
- Microsoft Defender لنقطة النهاية إلى حد كبير من تطوير الحماية من التهديدات للأجهزة. 
- بينما يسمح لك Microsoft Intune بتعيين نهج حماية التطبيقات وإدارة الأجهزة (بما في ذلك تغييرات التكوين)، يراقب Defender for Endpoint أجهزتك باستمرار للتهديدات ويمكنه اتخاذ إجراء تلقائي لمعالجة الهجمات. 
- يمكنك استخدام Intune لإلحاق الأجهزة ب Defender لنقطة النهاية. عند القيام بذلك، فإنك تقوم أيضا بتمكين هذه الأجهزة للعمل مع قدرات التوافق Microsoft 365، بما في ذلك منع فقدان بيانات نقطة النهاية (DLP).

تتضمن هذه المقالة الخطوات التالية:
- الاتصال Microsoft Intune إلى Defender لنقطة النهاية
- مراقبة مخاطر الجهاز
- مراقبة الامتثال لخطوط الأمان الأساسية

إذا لم يتم إعداد Defender لنقطة النهاية بالفعل، فاعمل مع مسؤول الحماية من التهديدات [لإعداد بيئة التقييم والإصدار التجريبي](../security/defender/eval-defender-endpoint-overview.md). يمكنك العمل مع مجموعة الإصدار التجريبي لتجربة القدرات في هذه المقالة.

## <a name="connect-microsoft-intune-to-defender-for-endpoint"></a>الاتصال Microsoft Intune إلى Defender لنقطة النهاية

يعد تكوين تكامل Microsoft Intune مع Defender لنقطة النهاية أمرا بسيطا. استخدم هذه [المقالة: تكوين Microsoft Defender لنقطة النهاية في Intune](/mem/intune/protect/advanced-threat-protection-configure). 

![الاتصال Intune إلى Microsoft Defender لنقطة النهاية](../media/devices/connect-intune-to-microsoft-defender.png#lightbox)

## <a name="monitor-device-risk-as-a-condition-for-access"></a>مراقبة مخاطر الجهاز كشرط للوصول

مع نشر Microsoft Defender لنقطة النهاية، يمكنك الاستفادة من إشارات مخاطر التهديد. يسمح لك هذا بحظر الوصول إلى الأجهزة استنادا إلى درجة المخاطر الخاصة بها. توصي Microsoft بالسماح بالوصول إلى الأجهزة التي تحتوي على درجة مخاطر متوسطة أو أقل.

بالنسبة لنظامي التشغيل Android وiOS/iPadOS، يمكن استخدام إشارات التهديد ضمن نهج حماية التطبيقات (APP). للحصول على معلومات حول تكوين هذا، راجع [إنشاء نهج حماية التطبيق وتعيينه لتعيين مستوى مخاطر الجهاز](/mem/intune/protect/advanced-threat-protection-configure).

بالنسبة إلى جميع الأنظمة الأساسية، يمكنك تعيين مستوى المخاطر في نهج توافق الأجهزة الحالية. راجع [إنشاء نهج التوافق وتعيينه لتعيين مستوى مخاطر الجهاز](/mem/intune/protect/advanced-threat-protection-configure).

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>نشر خطوط الأمان الأساسية ومراقبة الامتثال لهذه الإعدادات

ينطبق على: Windows 10، Windows 11

المقالة، [الخطوة 5. نشر ملفات تعريف التكوين](manage-devices-with-intune-configuration-profiles.md)، توصي ببدء استخدام ملفات تعريف التكوين باستخدام خطوط الأمان الأساسية، المتوفرة Windows 10 Windows 11. تتضمن Microsoft Defender لنقطة النهاية أيضا أساسيات الأمان التي توفر إعدادات تعمل على تحسين جميع عناصر التحكم في الأمان في مكدس Defender لنقطة النهاية، بما في ذلك إعدادات الكشف عن تهديدات نقاط النهاية والرد عليها ( الكشف التلقائي والاستجابة على النقط النهائية). كما يتم توزيعها باستخدام Microsoft Intune.

من الناحية المثالية، يتم نشر الأجهزة المضمنة في Defender لنقطة النهاية على حد سواء الأساسين: Windows أساس أمان Intune لتأمين Windows أولا ثم أساس أمان Defender لنقطة النهاية الطبقات العليا لتكوين عناصر تحكم أمان Defender لنقطة النهاية على النحو الأمثل.

للاستفادة من أحدث البيانات حول المخاطر والتهديدات وتقليل التعارضات مع تطور الخطوط الأساسية، طبق دائما أحدث إصدارات الخطوط الأساسية عبر جميع المنتجات بمجرد إصدارها. 

باستخدام Defender لنقطة النهاية، يمكنك مراقبة التوافق مع هذه الخطوط الأساسية. 

![بطاقة مراقبة الامتثال لأساسيات الأمان](../media/devices/secconmgmt-baseline-card.png#lightbox)

لنشر خطوط أساس الأمان ومراقبة التوافق مع هذه الإعدادات، استخدم الخطوات الواردة في هذا الجدول.


|خطوه  |الوصف  |
|---------|---------|
|1     |راجع المفاهيم الرئيسية وقارن بين Microsoft Defender لنقطة النهاية وخطوط أمان Intune Windows. <br><br>راجع [زيادة التوافق مع أساس الأمان Microsoft Defender لنقطة النهاية](../security/defender-endpoint/configure-machines-security-baseline.md) لمعرفة التوصيات.<br><br>راجع [استخدام خطوط أساس الأمان لتكوين أجهزة Windows في Intune ](/mem/intune/protect/security-baselines) لمراجعة قائمة أساسيات الأمان المتوفرة وكيفية تجنب التعارضات.         |
|2     |  نشر إعدادات أساس الأمان Windows ل Intune. ربما تكون قد أنجزت ذلك بالفعل إذا اتبعت الإرشادات الواردة في [الخطوة 5. نشر ملفات تعريف التكوين](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  نشر إعدادات خط أساس Defender لنقطة النهاية ل Intune. راجع [إدارة ملفات تعريف أساس الأمان في Microsoft Intune](/mem/intune/protect/security-baselines-configure) لإنشاء ملف التعريف واختيار إصدار الأساس.<br><br>يمكنك أيضا اتباع الإرشادات هنا: [مراجعة أساس الأمان Microsoft Defender لنقطة النهاية وتعيينه](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | في Defender لنقطة النهاية، راجع [بطاقة أساس الأمان على إدارة تكوين الجهاز](../security/defender-endpoint/configure-machines.md).          |
| | |

## <a name="next-steps"></a>الخطوات التالية
انتقل إلى [الخطوة 7. تنفيذ DLP مع قدرات حماية المعلومات على نقاط النهاية](manage-devices-with-intune-dlp-mip.md).