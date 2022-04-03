---
title: تمكين بيئة التقييم ل Microsoft Defender for Identity
description: قم بإعداد Microsoft Defender for Identity في Microsoft 365 Defender تجريبية أو بيئة تجريبية عن طريق تثبيت & المستشعر واكتشاف المسؤولين المحليين على أجهزة الكمبيوتر الأخرى.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: ac5c1a1bb541dee61155a55f23a78533c2b5360c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579670"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>تمكين بيئة التقييم ل Microsoft Defender for Identity

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 2](eval-defender-identity-overview.md) في عملية إعداد بيئة التقييم ل Microsoft Defender for Identity. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

استخدم الخطوات التالية لإعداد بيئة Microsoft Defender for Identity. 

![خطوات لتمكين Microsoft Defender for Identity في بيئة التقييم Microsoft Defender.](../../media/defender/m365-defender-identity-eval-enable-steps.png)

- [الخطوة 1. إعداد مثيل Defender for Identity](#step-1-set-up-the-defender-for-identity-instance)
- [الخطوة 2. تثبيت المستشعر وتكوينه](#step-2-install-and-configure-the-sensor)
- [الخطوة 3. تكوين إعدادات سجل الأحداث والوكيل على الأجهزة باستخدام المستشعر](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [الخطوة 4. السماح ل Defender for Identity بتحديد المسؤولين المحليين على أجهزة الكمبيوتر الأخرى](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>الخطوة 1. إعداد مثيل Defender for Identity

سجل الدخول إلى مدخل Defender for Identity لإنشاء المثيل ثم قم بتوصيل هذا المثيل ببيئة Active Directory. 

|  |الخطوة     |معلومات إضافية  |
|---------|---------|---------|
|1     | إنشاء مثيل Defender for Identity        | [التشغيل السريع: إنشاء مثيل Microsoft Defender for Identity](/defender-for-identity/install-step1)        |
|2     | الاتصال مثيل Defender for Identity إلى غابة Active Directory   | [سريع: الاتصال إلى "غابة Active Directory"](/defender-for-identity/install-step2)  |
| | |

## <a name="step-2-install-and-configure-the-sensor"></a>الخطوة 2. تثبيت المستشعر وتكوينه

بعد ذلك، قم بتنزيل مستشعر Defender for Identity وتثبيته وتكوينه على وحدات تحكم المجال وخادمات AD FS في بيئتك المحلية.

|  |الخطوة     |معلومات إضافية  |
|---------|---------|---------|
|1     | حدد عدد أدوات استشعار Microsoft Defender for Identity التي تحتاج إليها.        | [تخطيط السعة ل Microsoft Defender for Identity](/defender-for-identity/capacity-planning)   |
|2     | تنزيل حزمة إعداد المستشعر  |  [التشغيل السريع: تنزيل حزمة إعداد مستشعر Microsoft Defender for Identity](/defender-for-identity/install-step3)   |
|3     | تثبيت مستشعر Defender for Identity    |  [التشغيل السريع: تثبيت مستشعر Microsoft Defender for Identity](/defender-for-identity/install-step4)       |
|4     | تكوين المستشعر       |  [تكوين إعدادات مستشعر الهوية ل Microsoft Defender ](/defender-for-identity/install-step5)   |
|   |         |         |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>الخطوة 3. تكوين إعدادات سجل الأحداث والوكيل على الأجهزة باستخدام المستشعر

على الأجهزة التي قمت بتثبيت المستشعر عليها، قم Windows مجموعة سجلات الأحداث وإعدادات وكيل الإنترنت لتمكين قدرات الكشف وتحسينها.

|  |الخطوة     |معلومات إضافية  |
|---------|---------|---------|
|1     | تكوين مجموعة Windows الأحداث         | [تكوين Windows الحدث](/defender-for-identity/configure-windows-event-collection)        |
|2     | تكوين إعدادات وكيل الإنترنت        | [تكوين إعدادات اتصال الإنترنت ووكيل نقطة النهاية ل Microsoft Defender ل "مستشعر الهوية"](/defender-for-identity/configure-proxy)        |
|   |         |         |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>الخطوة 4. السماح ل Defender for Identity بتحديد المسؤولين المحليين على أجهزة الكمبيوتر الأخرى

يعتمد الكشف عن مسار الحركة اللاحقة ل Microsoft Defender for Identity على الاستعلامات التي تعرف المسؤولين المحليين على أجهزة معينة. يتم تنفيذ هذه الاستعلامات باستخدام بروتوكول SAM-R، باستخدام حساب خدمة Defender for Identity Service. 

لضمان Windows العملاء وخادمات الويب الخاصة بك تسمح لحساب Defender for Identity الخاص بك بتنفيذ SAM-R، يجب إجراء تعديل على نهج المجموعة لإضافة حساب خدمة Defender for Identity بالإضافة إلى الحسابات المكونة المدرجة في نهج الوصول إلى الشبكة. تأكد من تطبيق سياسات المجموعة على كل أجهزة الكمبيوتر **باستثناء وحدات التحكم بالمجال**.

للحصول على إرشادات حول كيفية القيام بذلك، راجع [تكوين Microsoft Defender للهوية للقيام مكالمات عن بعد ب SAM](/defender-for-identity/install-step8-samr). 

## <a name="next-steps"></a>الخطوات التالية

الخطوة 3 من 3: [تجريبي ل Microsoft Defender for Identity](eval-defender-identity-pilot.md)

العودة إلى نظرة عامة حول [تقييم Microsoft Defender for Identity](eval-defender-identity-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)