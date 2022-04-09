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
ms.openlocfilehash: af165f3565e3601ac4e8118535af3913c2cb2af8
ms.sourcegitcommit: 6fefc15dd78139316597083b702286097d45d4dd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737433"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>الخطوة 6. مراقبة مخاطر الأجهزة وتوافقها مع أساسات الأمان

بعد نشر مؤسستك Pertahanan Microsoft untuk Titik Akhir، يمكنك الحصول على رؤى وحماية أكبر لأجهزتك من خلال دمج Microsoft Intune مع Defender لنقطة النهاية. بالنسبة إلى الأجهزة المحمولة، يشمل ذلك القدرة على مراقبة مخاطر الجهاز كشرط للوصول. بالنسبة للأجهزة Windows، يمكنك مراقبة توافق هذه الأجهزة مع أساسيات الأمان. 

يتضمن نشر Pertahanan Microsoft untuk Titik Akhir نقاط نهاية الإلحاق. إذا كنت تستخدم Intune إلى نقاط النهاية الإلحاقية (مستحسن)، فقد قمت بالفعل بتوصيل Microsoft Intune ب Defender لنقطة النهاية. إذا استخدمت أسلوبا مختلفا لإلحاق نقاط النهاية ب Defender لنقطة النهاية، فراجع [تكوين Pertahanan Microsoft untuk Titik Akhir في Intune](/mem/intune/protect/advanced-threat-protection-configure) للتأكد من إعداد اتصال خدمة إلى خدمة بين Intune و Pertahanan Microsoft untuk Titik Akhir. 


![Defender لنقطة النهاية والتوضيح Microsoft Intune التكامل](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

في هذا الرسم التوضيحي:
- Pertahanan Microsoft untuk Titik Akhir إلى حد كبير زيادة التطور في الحماية من التهديدات للأجهزة. 
- بينما يسمح لك Microsoft Intune بتعيين نهج حماية التطبيقات وإدارة الأجهزة (بما في ذلك تغييرات التكوين)، يراقب Defender for Endpoint أجهزتك باستمرار للتهديدات ويمكنه اتخاذ إجراء تلقائي لمعالجة الهجمات. 
- يمكنك توصيل Microsoft Intune ب Defender لنقطة النهاية لمراقبة مخاطر الجهاز والامتثال لأساسيات الأمان.

تتضمن هذه المقالة الخطوات التالية:
- مراقبة مخاطر الجهاز
- مراقبة الامتثال لخطوط الأمان الأساسية

إذا لم يتم إعداد Defender لنقطة النهاية بالفعل، فاعمل مع مسؤول الحماية من التهديدات [لإعداد بيئة التقييم والإصدار التجريبي](../security/defender/eval-defender-endpoint-overview.md). يمكنك العمل مع مجموعة الإصدار التجريبي لتجربة القدرات في هذه المقالة.

## <a name="monitor-device-risk-as-a-condition-for-access"></a>مراقبة مخاطر الجهاز كشرط للوصول

مع نشر Pertahanan Microsoft untuk Titik Akhir، يمكنك الاستفادة من إشارات مخاطر التهديد. يسمح لك هذا بحظر الوصول إلى الأجهزة استنادا إلى درجة المخاطر الخاصة بها. توصي Microsoft بالسماح بالوصول إلى الأجهزة التي تحتوي على درجة مخاطر متوسطة أو أقل.

بالنسبة لنظامي التشغيل Android وiOS/iPadOS، يمكن استخدام إشارات التهديد ضمن نهج حماية التطبيقات (APP). للحصول على معلومات حول تكوين هذا، راجع [إنشاء نهج حماية التطبيق وتعيينه لتعيين مستوى مخاطر الجهاز](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level).

بالنسبة إلى جميع الأنظمة الأساسية، يمكنك تعيين مستوى المخاطر في نهج توافق الأجهزة الحالية. راجع [إنشاء نهج وصول مشروط](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection-configure#create-a-conditional-access-policy). 

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>نشر خطوط الأمان الأساسية ومراقبة الامتثال لهذه الإعدادات

ينطبق على: Windows 10، Windows 11

المقالة، [الخطوة 5. نشر ملفات تعريف التكوين](manage-devices-with-intune-configuration-profiles.md)، توصي ببدء استخدام ملفات تعريف التكوين باستخدام خطوط الأمان الأساسية، المتوفرة Windows 10 Windows 11. يتضمن Pertahanan Microsoft untuk Titik Akhir أيضا أساسيات الأمان التي توفر إعدادات تعمل على تحسين جميع عناصر التحكم في الأمان في مكدس Defender لنقطة النهاية، بما في ذلك إعدادات الكشف عن تهديدات نقاط النهاية والرد عليها ( الكشف التلقائي والاستجابة على النقط النهائية). كما يتم توزيعها باستخدام Microsoft Intune.

من الناحية المثالية، يتم نشر الأجهزة المضمنة في Defender لنقطة النهاية على حد سواء الأساسين: أساس الأمان Windows Intune لتأمين Windows أولا ثم أساس أمان Defender لنقطة النهاية الطبقات في الأعلى لتكوين عناصر تحكم أمان Defender for Endpoint على النحو الأمثل.

للاستفادة من أحدث البيانات حول المخاطر والتهديدات وتقليل التعارضات مع تطور الخطوط الأساسية، طبق دائما أحدث إصدارات الخطوط الأساسية عبر جميع المنتجات بمجرد إصدارها. 

باستخدام Defender لنقطة النهاية، يمكنك مراقبة التوافق مع هذه الخطوط الأساسية. 

![بطاقة مراقبة الامتثال لأساسيات الأمان](../media/devices/secconmgmt-baseline-card.png#lightbox)

لنشر خطوط أساس الأمان ومراقبة التوافق مع هذه الإعدادات، استخدم الخطوات الواردة في هذا الجدول.


|خطوه  |الوصف  |
|---------|---------|
|1     |راجع المفاهيم الرئيسية وقارن بين Pertahanan Microsoft untuk Titik Akhir وأساسيات الأمان Windows Intune. <br><br>راجع [زيادة التوافق مع أساس الأمان Pertahanan Microsoft untuk Titik Akhir](../security/defender-endpoint/configure-machines-security-baseline.md) لمعرفة التوصيات.<br><br>راجع [استخدام أساسيات الأمان لتكوين أجهزة Windows في Intune ](/mem/intune/protect/security-baselines) لمراجعة قائمة أساسيات الأمان المتوفرة وكيفية تجنب التعارضات.         |
|2     |  نشر إعدادات أساس الأمان Windows Intune. ربما تكون قد أنجزت ذلك بالفعل إذا اتبعت الإرشادات الواردة في [الخطوة 5. نشر ملفات تعريف التكوين](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  نشر إعدادات خط أساس Defender لنقطة النهاية Intune. راجع [إدارة ملفات تعريف أساس الأمان في Microsoft Intune](/mem/intune/protect/security-baselines-configure) لإنشاء ملف التعريف واختيار إصدار الأساس.<br><br>يمكنك أيضا اتباع الإرشادات هنا: [مراجعة أساس الأمان Pertahanan Microsoft untuk Titik Akhir وتعيينه](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | في Defender لنقطة النهاية، راجع [بطاقة أساس الأمان على إدارة تكوين الجهاز](../security/defender-endpoint/configure-machines.md).          |


## <a name="next-steps"></a>الخطوات التالية
انتقل إلى [الخطوة 7. تنفيذ DLP مع قدرات حماية المعلومات على نقاط النهاية](manage-devices-with-intune-dlp-mip.md).