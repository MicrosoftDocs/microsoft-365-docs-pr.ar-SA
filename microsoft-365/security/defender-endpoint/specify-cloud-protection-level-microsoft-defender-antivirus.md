---
title: تحديد مستوى الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender
description: قم بتعيين مستوى الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، الحماية من البرامج الضارة، الأمان، defender، السحابة، الهمة، مستوى الحماية
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
ms.openlocfilehash: 4723b84e285e508e33ca4b54a1897bbed036a897
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63579557"
---
# <a name="specify-the-cloud-protection-level"></a>تحديد مستوى الحماية السحابية

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

تعمل الحماية السحابية مع برنامج الحماية من الفيروسات من Microsoft Defender لتقديم الحماية لنقاط النهاية بشكل أسرع بكثير من التحديثات التقليدية لذكاء الأمان. يمكنك تكوين مستوى الحماية السحابية باستخدام إدارة نقاط النهاية من Microsoft (مستحسن) أو نهج المجموعة.

> [!NOTE]
> قد يؤدي **تحديد** تفاوت عال أو **عال +** أو صفري إلى الكشف عن بعض الملفات المشروعة. إذا حدث ذلك، يمكنك إلغاء حظر الملف أو النزاع الذي تم الكشف عنه في Microsoft 365 Defender المدخل.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>استخدام إدارة نقاط النهاية من Microsoft لتحديد مستوى الحماية السحابية

1. انتقل إلى إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) ثم سجل الدخول.

2. اختر **الحماية من الفيروسات لنقطة** \> **النهاية**.

3. حدد ملف تعريف برنامج الحماية من الفيروسات. (إذا لم يكن لديك ملف تعريف بعد، أو إذا كنت تريد إنشاء ملف تعريف جديد، فشاهد تكوين إعدادات تقييد الجهاز [في](/intune/device-restrictions-configure) Microsoft Intune.

4. حدد **خصائص**. بعد ذلك، إلى بجانب **إعدادات التكوين،** اختر **تحرير**.

5. قم **بتوسيع الحماية السحابية**، ثم **في قائمة مستوى** الحماية التي تم تسليمها في السحابة، حدد أحد ما يلي:

    - **غير مكون**: الحالة الافتراضية.
    - **عال**: تطبيق مستوى عال من الكشف.
    - **مرتفع بالإضافة** إلى: يستخدم المستوى **العالي** ويطبق إجراءات حماية إضافية (قد تؤثر على أداء العميل).
    - **عدم التسامح** إطلاقا: حظر جميع القابلة للتنفيذ غير المعروفة.

6. اختر **مراجعة + حفظ**، ثم اختر **حفظ**.

> [!TIP]
> هل تحتاج إلى بعض المساعدة؟ راجع الموارد التالية:
>
> - [تكوين Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [إضافة إعدادات حماية نقطة النهاية في Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>استخدام نهج المجموعة لتحديد مستوى الحماية السحابية

1. على جهاز إدارة نهج المجموعة، افتح وحدة [التحكم في إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انقر ب الماوس الأيمن فوق كائن نهج المجموعة الذي تريد تكوينه، ثم حدد **تحرير**.

3. في محرر **إدارة نهج المجموعة** ، انتقل إلى **القوالب الإدارية لتكوين** \> **الكمبيوتر**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **MpEngine**.

5. انقر نقرا مزدوجا فوق **إعداد تحديد مستوى الحماية السحابية** ثم قم بتعيينه إلى **تمكين**. حدد مستوى الحماية:

    - **غير مكون**: الحالة الافتراضية.
    - **يوفر مستوى الحظر الافتراضي** اكتشافا قويا دون زيادة خطر الكشف عن الملفات المشروعة.
    - **يوفر مستوى الحظر المتوسط** متوسطا فقط للكشف عن الثقة العالية
    - **يطبق مستوى الحظر العالي** مستوى عال من الاكتشاف مع تحسين أداء العميل (ولكن من الممكن أن يعطيك أيضا فرصة أكبر للإيجابيات الخاطئة).
    - **يطبق مستوى الحظر العالي** + قياسات الحماية الإضافية (قد تؤثر على أداء العميل وتزيد من فرصتك في الإيجابيات الخاطئة).
    - **يمنع مستوى حظر عدم التسامح إطلاقا** جميع القابلة للتنفيذ غير المعروفة.

6. حدد **موافق**.

7. نشر كائن نهج المجموعة المحدث. راجع [وحدة تحكم إدارة نهج المجموعة](/windows/win32/srvnodes/group-policy)

> [!TIP]
> هل تستخدم "كائنات نهج المجموعة" في الموقع؟ تعرف على كيفية ترجمتها في السحابة. [قم بتحليل كائنات نهج المجموعة](/mem/intune/configuration/group-policy-analytics) في الموقع باستخدام تحليلات نهج المجموعة في إدارة نقاط النهاية من Microsoft - معاينة.
  
## <a name="see-also"></a>راجع أيضًا

[لماذا يجب تمكين الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender](why-cloud-protection-should-be-on-mdav.md)
