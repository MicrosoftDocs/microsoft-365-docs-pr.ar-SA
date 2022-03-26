---
title: الاستجابة إلى تهديدات الويب في Microsoft Defender لنقطة النهاية
description: الاستجابة للتنبيهات المتعلقة بمواد الويب الضارة وغير المرغوب فيها. فهم كيفية إعلام المستخدمين بالحماية من المخاطر على الويب من خلال مستعرضات الويب الخاصة بهم Windows الإعلامات
keywords: حماية الويب، الحماية من المخاطر على الويب، استعراض الويب، التنبيهات، الاستجابة، الأمان، التصيد الاحتيالي، البرامج الضارة، استغلال، مواقع الويب، حماية الشبكة، Edge، Internet Explorer، Chrome، Firefox، مستعرض ويب، الإعلامات، المستخدمون النهائيون، إعلامات Windows، صفحة الحظر،
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
ms.openlocfilehash: cefeb36b43b0c59663935b0dd3a0155e80e44f33
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63575774"
---
# <a name="respond-to-web-threats"></a>الاستجابة إلى تهديدات الويب

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

تتيح لك حماية الويب في Microsoft Defender for Endpoint التحقق من التنبيهات ذات الصلة بمواد ويب ومواقع الويب الضارة والاستجابة لها في قائمة المؤشرات المخصصة.

## <a name="view-web-threat-alerts"></a>عرض تنبيهات تهديدات الويب

ينشئ Microsoft Defender ل Endpoint التنبيهات [التالية لنشاط](manage-alerts.md) ويب ضار أو مريب:

- **اتصال مريب تم** حظره بواسطة حماية الشبكة: يتم إنشاء هذا التنبيه عندما تتوقف محاولة الوصول إلى موقع ويب ضار أو موقع ويب في قائمة المؤشرات المخصصة عن  طريق حماية الشبكة في *وضع الحظر*
- **اتصال مريب تم** اكتشافه بواسطة حماية الشبكة: يتم إنشاء هذا التنبيه عند اكتشاف محاولة الوصول إلى موقع ويب ضار أو موقع ويب في قائمة المؤشرات المخصصة بواسطة حماية الشبكة في وضع *التدقيق فقط*

يوفر كل تنبيه المعلومات التالية:

- الجهاز الذي حاول الوصول إلى موقع ويب المحظور
- التطبيق أو البرنامج المستخدم لإرسال طلب الويب
- URL أو URL ضار في قائمة المؤشرات المخصصة
- الإجراءات الموصى بها للمستجيبين

![صورة تنبيه مرتبط بحماية تهديدات الويب.](images/wtp-alert.png)

> [!NOTE]
> لتقليل حجم التنبيهات، يدمج Microsoft Defender for Endpoint الكشف عن تهديدات الويب للمجال نفسه على الجهاز نفسه كل يوم إلى تنبيه واحد. يتم إنشاء تنبيه واحد فقط وتحسب في تقرير [حماية الويب](web-protection-monitoring.md).

## <a name="inspect-website-details"></a>فحص تفاصيل موقع ويب

يمكنك التعمق أكثر عن طريق تحديد عنوان URL أو مجال موقع ويب في التنبيه. يفتح ذلك صفحة حول عنوان URL أو مجال معين يتضمن معلومات متنوعة، بما في ذلك:

- الأجهزة التي حاولت الوصول إلى موقع ويب
- الأحداث والتنبيهات المتعلقة بالموقع
- مدى تكرار رؤية موقع ويب في الأحداث في مؤسستك

    ![صورة لصفحة تفاصيل كيان URL أو المجال.](images/wtp-website-details.png)

[تعرف على المزيد حول URL أو صفحات كيان المجال](investigate-domain.md)

## <a name="inspect-the-device"></a>فحص الجهاز

يمكنك أيضا التحقق من الجهاز الذي حاول الوصول إلى عنوان URL المحظور. عند تحديد اسم الجهاز على صفحة التنبيه، يتم فتح صفحة تحتوي على معلومات شاملة حول الجهاز.

[معرفة المزيد حول صفحات كيان الجهاز](investigate-machines.md)

## <a name="web-browser-and-windows-notifications-for-end-users"></a>مستعرض ويب Windows للمستخدمين النهائيين

باستخدام حماية الويب في Microsoft Defender لنقطة النهاية، سيتم منع المستخدمين النهائيين من زيارة مواقع الويب الضارة أو غير المرغوب فيها باستخدام Microsoft Edge أو مستعرضات أخرى. ونظرا لتنفيذ الحظر بواسطة [حماية الشبكة](network-protection.md)، سيشاهدون خطأ عاما من مستعرض الويب. كما سيشاهدون إعلاما من Windows.

![صورة Microsoft Edge الخطأ 403 وإعلام Windows.](images/wtp-browser-blocking-page.png)
 *تم حظر تهديدات الويب على Microsoft Edge*

![صورة لمستعرض ويب Chrome تعرض تحذير اتصال آمن Windows ويب.](images/wtp-chrome-browser-blocking-page.png)
 *تم حظر تهديدات الويب على Chrome*

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول حماية الويب](web-protection-overview.md)
- [تصفية محتوى ويب](web-content-filtering.md)
- [الحماية من المخاطر على الويب](web-threat-protection.md)
- [مراقبة أمان الويب](web-protection-monitoring.md)
