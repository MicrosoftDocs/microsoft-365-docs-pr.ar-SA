---
title: تمكين بيئة التقييم Microsoft Defender for Identity
description: إعداد Microsoft Defender for Identity في Microsoft 365 Defender التجربة أو بيئة الاختبار عن طريق تثبيت & تكوين جهاز الاستشعار، واكتشاف المسؤولين المحليين على أجهزة كمبيوتر أخرى.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 84b893b6689385e4137778d0d787f42428843d26
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750177"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>تمكين بيئة التقييم Microsoft Defender for Identity

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 2](eval-defender-identity-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Identity. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

استخدم الخطوات التالية لإعداد بيئة Microsoft Defender for Identity. 

:::image type="content" source="../../media/defender/m365-defender-identity-eval-enable-steps.png" alt-text="خطوات تمكين Microsoft Defender for Identity في بيئة تقييم Microsoft Defender" lightbox="../../media/defender/m365-defender-identity-eval-enable-steps.png":::

- [الخطوة 1. إعداد Defender لمثيل الهوية](#step-1-set-up-the-defender-for-identity-instance)
- [الخطوة 2. تثبيت جهاز الاستشعار وتكوينه](#step-2-install-and-configure-the-sensor)
- [الخطوة 3. تكوين سجل الأحداث وإعدادات الوكيل على الأجهزة باستخدام جهاز الاستشعار](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [الخطوة 4. السماح ل Defender for Identity بتحديد المسؤولين المحليين على أجهزة الكمبيوتر الأخرى](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>الخطوة 1. إعداد Defender لمثيل الهوية

سجل الدخول إلى مدخل Defender for Identity لإنشاء مثيلك ثم قم بتوصيل هذا المثيل ببيئة Active Directory. 

|  خطوه | الوصف     |معلومات إضافية  |
|---------|---------|---------|
|1     | إنشاء مثيل Defender for Identity        | [التشغيل السريع: إنشاء مثيل Microsoft Defender for Identity](/defender-for-identity/install-step1)        |
|2     | توصيل مثيل Defender for Identity بغاية Active Directory   | [التشغيل السريع: الاتصال ب "غابة Active Directory"](/defender-for-identity/install-step2)  |

## <a name="step-2-install-and-configure-the-sensor"></a>الخطوة 2. تثبيت جهاز الاستشعار وتكوينه

بعد ذلك، قم بتنزيل أداة استشعار Defender for Identity وتثبيتها وتكوينها على وحدات التحكم بالمجال وخوادم AD FS في بيئتك المحلية.

|  خطوه | الوصف     |معلومات إضافية  |
|---------|---------|---------|
|1     | حدد عدد أدوات استشعار Microsoft Defender for Identity التي تحتاجها.        | [تخطيط السعة Microsoft Defender for Identity](/defender-for-identity/capacity-planning)   |
|2     | تنزيل حزمة إعداد جهاز الاستشعار  |  [التشغيل السريع: تنزيل حزمة إعداد مستشعر Microsoft Defender for Identity](/defender-for-identity/install-step3)   |
|3     | تثبيت مستشعر Defender for Identity    |  [التشغيل السريع: تثبيت مستشعر Microsoft Defender for Identity](/defender-for-identity/install-step4)       |
|4     | تكوين جهاز الاستشعار       |  [تكوين إعدادات مستشعر Microsoft Defender for Identity](/defender-for-identity/install-step5)   |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>الخطوة 3. تكوين سجل الأحداث وإعدادات الوكيل على الأجهزة باستخدام جهاز الاستشعار

على الأجهزة التي قمت بتثبيت جهاز الاستشعار عليها، قم بتكوين مجموعة سجلات أحداث Windows وإعدادات وكيل الإنترنت لتمكين قدرات الكشف وتحسينها.

|  خطوه | الوصف     |معلومات إضافية  |
|---------|---------|---------|
|1     | تكوين مجموعة سجلات أحداث Windows         | [تكوين مجموعة أحداث Windows](/defender-for-identity/configure-windows-event-collection)        |
|2     | تكوين إعدادات وكيل إنترنت        | [تكوين وكيل نقطة النهاية وإعدادات الاتصال بالإنترنت لأداة استشعار Microsoft Defender for Identity](/defender-for-identity/configure-proxy)        |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>الخطوة 4. السماح ل Defender for Identity بتحديد المسؤولين المحليين على أجهزة الكمبيوتر الأخرى

يعتمد Microsoft Defender for Identity الكشف عن مسار الحركة الجانبية على الاستعلامات التي تحدد المسؤولين المحليين على أجهزة معينة. يتم تنفيذ هذه الاستعلامات باستخدام بروتوكول SAM-R، باستخدام حساب Defender for Identity Service. 

لضمان السماح لعملاء Windows وخوادمه بحساب Defender for Identity الخاص بك بتنفيذ SAM-R، يجب إجراء تعديل على نهج المجموعة لإضافة حساب خدمة Defender for Identity بالإضافة إلى الحسابات المكونة المدرجة في نهج الوصول إلى الشبكة. تأكد من تطبيق نهج المجموعة على كافة أجهزة الكمبيوتر **باستثناء وحدات التحكم بالمجال**.

للحصول على إرشادات حول كيفية القيام بذلك، راجع [تكوين Microsoft Defender for Identity لإجراء مكالمات عن بعد إلى SAM](/defender-for-identity/install-step8-samr). 

## <a name="next-steps"></a>الخطوات التالية

الخطوة 3 من 3: [Microsoft Defender for Identity التجريبية](eval-defender-identity-pilot.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender for Identity](eval-defender-identity-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
