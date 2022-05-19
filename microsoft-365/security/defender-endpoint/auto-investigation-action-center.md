---
title: تفضل بزيارة مركز الصيانة للاطلاع على إجراءات المعالجة
description: استخدام مركز الصيانة لعرض التفاصيل والنتائج بعد تحقيق تلقائي
keywords: إجراء، مركز، مؤتمت، مؤتمت، تحقيق، استجابة، معالجة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.technology: mde
ms.openlocfilehash: 6a2cc5d4315c5dd64a852c74176272061789b1ba
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535393"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>تفضل بزيارة مركز الصيانة للاطلاع على إجراءات المعالجة

في أثناء التحقيق التلقائي وبعده، يتم تحديد إجراءات المعالجة للكشف عن التهديدات. اعتمادا على التهديد المعين وكيفية [تكوين قدرات التحقيق والمعالجة التلقائية](configure-automated-investigations-remediation.md) لمؤسستك، يتم اتخاذ بعض إجراءات المعالجة تلقائيا، بينما تتطلب إجراءات أخرى الموافقة. إذا كنت جزءا من فريق عمليات الأمان في مؤسستك، يمكنك عرض [إجراءات المعالجة](manage-auto-investigation.md#remediation-actions) المعلقة والمكتملة في **مركز الصيانة**.

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

## <a name="the-unified-action-center"></a>مركز الصيانة الموحد

مؤخرا، تم تحديث مركز الصيانة. لديك الآن تجربة مركز إجراء موحدة. للوصول إلى مركز الصيانة، انتقل إلى [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) مركز الصيانة وسجل الدخول.

:::image type="content" source="images/mde-action-center-unified.png" alt-text="صفحة مركز الصيانة في مدخل Microsoft 365 Defender" lightbox="images/mde-action-center-unified.png":::

### <a name="whats-changed"></a>ما الذي تم تغييره؟

يقارن الجدول التالي مركز الصيانة الموحد الجديد بمركز الإجراءات السابق.

|مركز الصيانة الموحد الجديد  |مركز الإجراءات السابق  |
|---------|---------|
|سرد الإجراءات المعلقة والمكتملة للأجهزة والبريد الإلكتروني في موقع واحد <br/>([Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) بالإضافة إلى [Microsoft Defender لـ Office 365](/microsoft-365/security/office-365-security/office-365-atp))|سرد الإجراءات المعلقة والمكتملة للأجهزة <br/> ([Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) فقط)   |
|يقع في:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |يقع في:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، اختر **مركز الصيانة**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="جزء التنقل إلى مركز الصيانة في مدخل Microsoft 365 Defender" lightbox="images/action-center-nav-new.png"::: | In the Microsoft 365 Defender portal, choose **Automated investigations** > **Action center**. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="إصدار أقدم من جزء التنقل إلى مركز الصيانة في مدخل Microsoft 365 Defender" lightbox="images/action-center-nav-old.png":::  |

يجمع مركز الإجراءات الموحد بين إجراءات المعالجة عبر Defender لنقطة النهاية Defender لـ Office 365. وهو يحدد لغة مشتركة لجميع إجراءات المعالجة، ويوفر تجربة تحقيق موحدة.

يمكنك استخدام مركز الصيانة الموحد إذا كان لديك الأذونات المناسبة واشتراك واحد أو أكثر من الاشتراكات التالية:

- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)
- [Defender لنقطة النهاية](microsoft-defender-endpoint.md)
- [دليل إعداد Microsoft Defender لـ Office 365](/microsoft-365/security/office-365-security/office-365-atp)
- [Defender for Business](../defender-business/mdb-overview.md)

## <a name="using-the-action-center"></a>استخدام مركز الصيانة

للوصول إلى مركز الصيانة الموحد في مدخل Microsoft 365 Defender المحسن:

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> وسجل الدخول.

2. في جزء التنقل، حدد **مركز الصيانة**.

3. استخدم **الإجراءات المعلقة** وعلامات تبويب **المحفوظات** . يلخص الجدول التالي ما ستراه في كل علامة تبويب:

   |التبويب|الوصف|
   |---|---|
   |**المعلقه**|عرض قائمة بالإجراءات التي تتطلب الانتباه. يمكنك الموافقة على الإجراءات أو رفضها كل على حدة، أو تحديد إجراءات متعددة إذا كان لها نفس نوع الإجراء (مثل **ملف العزل**). <p> **تلميح**: تأكد من [مراجعة (أو رفض) الإجراءات المعلقة والموافقة عليها في](manage-auto-investigation.md) أقرب وقت ممكن بحيث يمكن إكمال التحقيقات التلقائية في الوقت المناسب.|
   |**التاريخ**|يعمل كسجل تدقيق للإجراءات التي تم اتخاذها، مثل: <ul><li>إجراءات المعالجة التي تم اتخاذها نتيجة للتحقيقات التلقائية</li><li>إجراءات المعالجة التي وافق عليها فريق عمليات الأمان</li><li>الأوامر التي تم تشغيلها وإجراءات المعالجة التي تم تطبيقها أثناء جلسات الاستجابة المباشرة</li><li>إجراءات المعالجة التي تم اتخاذها بواسطة ميزات الحماية من التهديدات في برنامج الحماية من الفيروسات من Microsoft Defender</li></ul> <p> يوفر طريقة للتراجع عن إجراءات معينة (راجع [التراجع عن الإجراءات المكتملة](manage-auto-investigation.md#undo-completed-actions)).|

4. لتخصيص البيانات وفرزها وتصفيتها وتصديرها في مركز الصيانة، اتخذ خطوة واحدة أو أكثر من الخطوات التالية:

   :::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="مركز الصيانة مع الأعمدة وعوامل التصفية" lightbox="images/new-action-center-columnsfilters.png":::

   - حدد عنوان عمود لفرز العناصر بترتيب تصاعدي أو تنازلي.
   - استخدم عامل تصفية الفترة الزمنية لعرض بيانات اليوم أو الأسبوع أو 30 يوما أو 6 أشهر الماضية.
   - اختر الأعمدة التي تريد عرضها.
   - حدد عدد العناصر المراد تضمينها في كل صفحة من البيانات.
   - استخدم عوامل التصفية لعرض العناصر التي تريد رؤيتها فقط.
   - حدد **"تصدير** " لتصدير النتائج إلى ملف .csv.

## <a name="next-steps"></a>الخطوات التالية

- [عرض إجراءات الإصلاح والموافقة عليها](manage-auto-investigation.md)
- [راجع الدليل التفاعلي: التحقيق في التهديدات ومعالجتها باستخدام Microsoft Defender لنقطة النهاية](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>راجع أيضًا

- [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)
- [مقارنة ميزات الأمان في خطط Microsoft 365 للشركات الصغيرة والمتوسطة الحجم](../defender-business/compare-mdb-m365-plans.md)
