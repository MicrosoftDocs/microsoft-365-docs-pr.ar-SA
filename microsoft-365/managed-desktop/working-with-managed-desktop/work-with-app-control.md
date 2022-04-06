---
title: استخدام عنصر تحكم التطبيق
description: تعرف على كيفية إدارة التحكم في التطبيق.
keywords: Microsoft Managed Desktop، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 99979a08a67245d471b33ce26e4b7f35790fead5
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569898"
---
# <a name="work-with-app-control"></a>استخدام عنصر تحكم التطبيق

بمجرد نشر التحكم في التطبيق في بيئتك، ستتحمل أنت Microsoft Managed Desktop عملياتك مسؤوليات مستمرة. على سبيل المثال، قد ترغب في إضافة تطبيق جديد في البيئة، أو إضافة (أو إزالة) توقيع موثوق به. لتحسين الأمان، يجب توقيع التعليمات البرمجية على جميع التطبيقات قبل تحريرها للمستخدمين. تتضمن تفاصيل ناشر التطبيق معلومات حول التوقيع.

## <a name="add-a-new-app"></a>إضافة تطبيق جديد

**لإضافة تطبيق جديد:**

1. أضف [التطبيق إلى Microsoft Intune](/mem/intune/apps/apps-win32-app-management).
1. نشر التطبيق على أي جهاز في حلقة الاختبار.
1. اختبر تطبيقك وفقا لعمليات العمل القياسية.
1. تحقق من عارض الأحداث ضمن **سجلات التطبيقات والخدمات\Microsoft\Windows\AppLocker**. ابحث عن أي **أحداث 8003** أو **8006** . تشير هذه الأحداث إلى أنه سيتم حظر التطبيق. لمزيد من المعلومات حول كل أحداث App Locker ومعانيها، راجع استخدام عارض الأحداث [مع AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/using-event-viewer-with-applocker).
1. إذا وجدت أي من هذه الأحداث، فافتح طلب توقيع باستخدام Microsoft Managed Desktop العمليات.

## <a name="add-or-remove-a-trusted-signer"></a>إضافة (أو إزالة) توقيع موثوق به

عند فتح طلب توقيع، ستحتاج أولا إلى توفير بعض تفاصيل الناشر المهمة.

**لإضافة (أو إزالة) توقيع موثوق به:**

1. [جمع تفاصيل الناشر](#gather-publisher-details).
1. افتح تذكرة مع Microsoft Managed Desktop لطلب قاعدة التوقيع وتضمين التفاصيل التالية:  
    - اسم التطبيق
    - إصدار التطبيق
    - الوصف
    - تغيير النوع ("إضافة" أو "إزالة")  
    - Publisher التفاصيل (على سبيل المثال: `O=<publisher name>,L=<location>,S=State,C=Country`)

> [!NOTE]
> لإزالة الثقة في أحد التطبيقات، اتبع الخطوات نفسها، ولكن قم بتعيين **النوع تغيير** *لإزالته*.

ستنشر العمليات تدريجيا سياسات لمجموعات النشر باتباع هذا الجدول:

|مجموعة النشر|نوع النهج|التوقيت|
|---|---|---|
|اختبار|التدقيق|اليوم 0|
|أولا|فرض|اليوم الأول|
|سريع|فرض|اليوم الثاني|
|واسع|فرض|اليوم الثالث|

يمكنك إيقاف النشر مؤقتا أو التراجع فيه في أي وقت أثناء عملية النشر. لإيقاف مؤقت أو التراجع، افتح طلب دعم آخر باستخدام Microsoft Managed Desktop العمليات.

> [!NOTE]
> إذا قمت بإيقاف إصدار قاعدة موقع مؤقتا، فيجب إما التراجع عن هذه القاعدة أو إكمالها قبل بدء عملية نشر أخرى.

## <a name="gather-publisher-details"></a>جمع تفاصيل الناشر

**للوصول إلى بيانات الناشر لتطبيق ما:**

1. ابحث عن Microsoft Managed Desktop في حلقة الاختبار التي تم تطبيق نهج وضع التدقيق عليها.
1. حاول تثبيت التطبيق على الجهاز.
1. افتح عارض الأحداث على هذا الجهاز.
1. في عارض الأحداث، انتقل إلى سجلات التطبيقات والخدمات **\Microsoft\Windows**، ثم حدد **AppLocker**.
1. ابحث عن **أي حدث 8003** أو **8006** ، ثم انسخ المعلومات من الحدث:
    - اسم التطبيق
    - إصدار التطبيق
    - الوصف
    - Publisher التفاصيل (على سبيل المثال: `O=<publisher name>, L=<location>, S=State, C=Country`)
