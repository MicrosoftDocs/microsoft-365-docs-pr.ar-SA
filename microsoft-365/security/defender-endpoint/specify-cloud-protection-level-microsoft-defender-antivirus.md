---
title: تحديد مستوى حماية السحابة برنامج الحماية من الفيروسات من Microsoft Defender
description: تعيين مستوى الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، ومكافحة البرامج الضارة، والأمان، والمدافع، والسحابة، والعدوانية، ومستوى الحماية
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.date: 08/26/2021
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 6e24be40b4ff9e57d896cf53769b578c482a2c6e
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787523"
---
# <a name="specify-the-cloud-protection-level"></a>تحديد مستوى الحماية السحابية

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

تعمل حماية السحابة مع برنامج الحماية من الفيروسات من Microsoft Defender لتوفير الحماية لنقاط النهاية الخاصة بك بشكل أسرع بكثير من خلال تحديثات التحليل الذكي للأمان التقليدية. يمكنك تكوين مستوى حماية السحابة باستخدام إدارة نقاط النهاية من Microsoft (مستحسن) أو نهج المجموعة.

> [!NOTE]
> قد يؤدي تحديد التسامح **مع High** أو **High +** أو **Zero** إلى الكشف عن بعض الملفات المشروعة. إذا حدث ذلك، يمكنك إلغاء حظر الملف المكتشف أو النزاعات التي تم الكشف عنها في مدخل Microsoft 365 Defender.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>استخدام إدارة نقاط النهاية من Microsoft لتحديد مستوى حماية السحابة

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. اختر برنامج **الحماية من الفيروسات** **لأمان** \> نقطة النهاية.

3. حدد ملف تعريف برنامج الحماية من الفيروسات. (إذا لم يكن لديك ملف تعريف بعد، أو إذا كنت تريد إنشاء ملف تعريف جديد، فراجع [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure).

4. تحديد **الخصائص**. بعد ذلك، إلى جانب **إعدادات التكوين**، اختر **"تحرير**".

5. قم بتوسيع **حماية السحابة**، ثم في قائمة **مستوى الحماية المقدمة من السحابة** ، حدد أحد الإجراءات التالية:

    - **لم يتم تكوين: الحالة** الافتراضية.
    - **عال**: يطبق مستوى قويا من الكشف.
    - **علامة الجمع العالية**: يستخدم المستوى **العالي** ويطبق مقاييس حماية إضافية (قد تؤثر على أداء العميل).
    - **عدم التسامح:** يحظر كافة الملفات التنفيذية غير المعروفة.

6. اختر **"مراجعة + حفظ**"، ثم اختر **"حفظ**".

> [!TIP]
> هل تحتاج إلى بعض المساعدة؟ راجع الموارد التالية:
>
> - [تكوين Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [إضافة إعدادات حماية نقطة النهاية في Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>استخدام نهج المجموعة لتحديد مستوى حماية السحابة

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انقر بزر الماوس الأيمن فوق الكائن نهج المجموعة الذي تريد تكوينه، ثم حدد **"تحرير**".

3. في **محرر إدارة نهج المجموعة** انتقل إلى **قوالب إدارة** **تكوين** \> الكمبيوتر.

4. قم بتوسيع الشجرة إلى **مكونات Windows** \> **برنامج الحماية من الفيروسات من Microsoft Defender** \> **MpEngine**.

5. انقر نقرا مزدوجا فوق إعداد **تحديد مستوى حماية السحابة** وقم بتعيينه إلى **ممكن**. حدد مستوى الحماية:

    - **لم يتم تكوين: الحالة** الافتراضية.
    - يوفر **مستوى الحظر الافتراضي اكتشافا** قويا دون زيادة خطر الكشف عن الملفات المشروعة.
    - يوفر **مستوى الحظر المتوسط** متوسطا فقط للكشف عن الثقة العالية
    - يطبق **مستوى الحظر العالي** مستوى قويا من الكشف أثناء تحسين أداء العميل (ولكن يمكن أن يمنحك أيضا فرصة أكبر من النتائج الإيجابية الخاطئة).
    - تطبق **High + blocking level** مقاييس حماية إضافية (قد تؤثر على أداء العميل وتزيد من فرصتك في النتائج الإيجابية الخاطئة).
    - **يمنع مستوى حظر عدم التسامح** كافة الملفات التنفيذية غير المعروفة.

6. حدد **موافق**.

7. نشر كائن نهج المجموعة المحدث. راجع [وحدة تحكم إدارة نهج المجموعة](/windows/win32/srvnodes/group-policy)

> [!TIP]
> هل تستخدم كائنات نهج المجموعة محليا؟ تعرف على كيفية ترجمتها في السحابة. [تحليل عناصر نهج المجموعة المحلية باستخدام تحليلات نهج المجموعة في إدارة نقاط النهاية من Microsoft - معاينة](/mem/intune/configuration/group-policy-analytics).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)
  
## <a name="see-also"></a>راجع أيضًا

[لماذا يجب تمكين حماية السحابة برنامج الحماية من الفيروسات من Microsoft Defender](why-cloud-protection-should-be-on-mdav.md)
