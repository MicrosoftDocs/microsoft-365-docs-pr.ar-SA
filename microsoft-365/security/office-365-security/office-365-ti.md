---
title: إمكانات الاستجابة للتحقيق في التهديدات & - الخطة 2 Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/09/2019
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 32405da5-bee1-4a4b-82e5-8399df94c512
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: تعرف على قدرات التحقيق في التهديدات والاستجابة لها في خطة Microsoft Defender لـ Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c972a42730f4d21b73227a8b8a9900223109d590
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972024"
---
# <a name="threat-investigation-and-response"></a>التحقيق في التهديدات والاستجابة لها

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md)

تساعد قدرات التحقيق في التهديدات والاستجابة لها في [Microsoft Defender لـ Office 365](defender-for-office-365.md) محللي الأمان والمسؤولين على حماية Microsoft 365 لمؤسستهم لمستخدمي الأعمال من خلال:

- تسهيل تحديد الهجمات الإلكترونية ومراقبتها وفهمها.
- المساعدة في معالجة التهديدات بسرعة في Exchange Online SharePoint Online OneDrive for Business Microsoft Teams.
- توفير رؤى ومعرفة لمساعدة عمليات الأمان على منع الهجمات الإلكترونية ضد مؤسستهم.
- استخدام [التحقيق التلقائي والاستجابة في Office 365](automated-investigation-response-office.md) للتهديدات الحرجة المستندة إلى البريد الإلكتروني.

توفر قدرات التحقيق في التهديدات والاستجابة رؤى حول التهديدات وإجراءات الاستجابة ذات الصلة المتوفرة في مدخل Microsoft 365 Defender. يمكن أن تساعد هذه الرؤى فريق الأمان في مؤسستك على حماية المستخدمين من الهجمات المستندة إلى البريد الإلكتروني أو الملفات. تساعد القدرات على مراقبة الإشارات وجمع البيانات من مصادر متعددة، مثل نشاط المستخدم والمصادقة والبريد الإلكتروني وأجهزة الكمبيوتر التي تم اختراقها وحوادث الأمان. يمكن لصانعي القرار في مجال الأعمال وفريق عمليات الأمان استخدام هذه المعلومات لفهم التهديدات التي تتعرض لها مؤسستك والاستجابة لها وحماية الملكية الفكرية الخاصة بك.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>التعرف على أدوات التحقيق في التهديدات والاستجابة لها

قدرات التحقيق في التهديدات والاستجابة لها في مدخل Microsoft 365 Defender هي <https://security.microsoft.com> مجموعة من الأدوات ومسير عمل الاستجابة التي تتضمن:

- [Explorer](#explorer)
- [الأحداث](#incidents)
- [أتمتة المحاكاة في التدريب على محاكاة الهجوم](attack-simulation-training.md)
- [التحقيق التلقائي والاستجابة (AIR)](automated-investigation-response-office.md)

### <a name="explorer"></a>Explorer

استخدم [المستكشف (والكشف في الوقت الحقيقي) لتحليل التهديدات](threat-explorer.md) ، ورؤية حجم الهجمات بمرور الوقت، وتحليل البيانات حسب مجموعات التهديد، والبنية الأساسية للمهاجمين، والمزيد. المستكشف (يشار إليه أيضا باسم مستكشف التهديدات) هو مكان البداية لسير عمل التحقيق الخاص بمحلل الأمان.

:::image type="content" source="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png" alt-text="صفحة مستكشف المخاطر" lightbox="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png":::

لعرض هذا التقرير واستخدامه في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **مستكشف** التعاون \> **& البريد الإلكتروني**. أو للانتقال مباشرة إلى صفحة **المستكشف** ، استخدم <https://security.microsoft.com/threatexplorer>.

## <a name="office-365-threat-intelligence-connection"></a>اتصال Office 365 تحليل ذكي للمخاطر

لا تتوفر هذه الميزة إلا إذا كان لديك اشتراك نشط في Office 365 E5 أو الوظيفة الإضافية «Threat Intelligence». لمزيد من المعلومات، راجع صفحة منتج Office 365 Enterprise E5.

عند تشغيل هذه الميزة، ستتمكن من دمج البيانات من Microsoft Defender لـ Office 365 في Microsoft 365 Defender لإجراء تحقيق أمني شامل عبر علب بريد Office 365 وأجهزة Windows.

> [!NOTE]
> ستحتاج إلى الحصول على الترخيص المناسب لتمكين هذه الميزة.

لتلقي تكامل الجهاز السياقي في Office 365 تحليل ذكي للمخاطر، ستحتاج إلى تمكين إعدادات Defender لنقطة النهاية في لوحة معلومات الأمان & Compliance.

### <a name="incidents"></a>الأحداث

استخدم قائمة الحوادث (وهذا ما يسمى أيضا «التحقيقات») لمشاهدة قائمة بحوادث أمان الطيران. يتم استخدام الحوادث لتتبع التهديدات مثل رسائل البريد الإلكتروني المشبوهة، وإجراء مزيد من التحقيق والمعالجة.

:::image type="content" source="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png" alt-text="قائمة حوادث التهديد الحالية في Office 365" lightbox="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png":::

لعرض قائمة الحوادث الحالية لمؤسستك في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **الحوادث & التنبيهات** \> **الحوادث**. أو للانتقال مباشرة إلى صفحة **الحوادث** ، استخدم <https://security.microsoft.com/incidents>.

:::image type="content" source="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png" alt-text="صفحة المراجعة في مركز توافق & الأمان" lightbox="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png":::

### <a name="attack-simulation-training"></a>أتمتة المحاكاة في التدريب على محاكاة الهجوم

استخدم التدريب على محاكاة الهجوم لإعداد الهجمات الإلكترونية الواقعية وتشغيلها في مؤسستك، وتحديد الأشخاص المعرضين للخطر قبل أن يؤثر الهجوم السيبراني الحقيقي على عملك. لمعرفة المزيد، راجع [محاكاة هجوم التصيد الاحتيالي](attack-simulation-training.md).

لعرض هذه الميزة واستخدامها في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **تدريب محاكاة Email** **& collaborationAttack** > . أو للانتقال مباشرة إلى صفحة **التدريب على محاكاة الهجوم** ، استخدم <https://security.microsoft.com/attacksimulator?viewid=overview>.

### <a name="automated-investigation-and-response"></a>التحقيق التلقائي والاستجابة (AIR)

استخدم قدرات التحقيق والاستجابة التلقائية لتوفير الوقت والجهد لربط المحتوى والأجهزة والأشخاص المعرضين للخطر من التهديدات في مؤسستك. يمكن أن تبدأ عمليات AIR كلما تم تشغيل تنبيهات معينة، أو عند بدء تشغيلها من قبل فريق عمليات الأمان. لمعرفة المزيد، راجع [التحقيق التلقائي والاستجابة في Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>عناصر واجهة مستخدم التحليل الذكي للمخاطر

كجزء من عرض Microsoft Defender لـ Office 365 الخطة 2، يمكن لمحللين أمنيين مراجعة التفاصيل حول تهديد معروف. وهذا مفيد لتحديد ما إذا كانت هناك إجراءات/خطوات وقائية إضافية يمكن اتخاذها للحفاظ على أمان المستخدمين.

:::image type="content" source="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png" alt-text="يعرض جزء اتجاهات الأمان معلومات حول التهديدات الأخيرة" lightbox="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png":::

## <a name="how-do-we-get-these-capabilities"></a>كيف يمكننا الحصول على هذه القدرات؟

يتم تضمين Microsoft 365 قدرات التحقيق في التهديدات والاستجابة لها في Microsoft Defender لـ Office 365 الخطة 2، المضمنة في Enterprise E5 أو كوظيفة إضافية لاشتراكات معينة. لمعرفة المزيد، راجع [Defender لـ Office 365 الخطة 1 والخطة 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="required-roles-and-permissions"></a>الأدوار والأذونات المطلوبة

يستخدم Microsoft Defender لـ Office 365 التحكم في الوصول استنادا إلى الدور. يتم تعيين الأذونات من خلال أدوار معينة في Azure Active Directory أو مركز مسؤولي Microsoft 365 أو مدخل Microsoft 365 Defender.

> [!TIP]
> على الرغم من أنه يمكن تعيين بعض الأدوار، مثل مسؤول الأمان، في مدخل Microsoft 365 Defender، ففكر في استخدام إما مركز مسؤولي Microsoft 365 أو Azure Active Directory بدلا من ذلك. للحصول على معلومات حول الأدوار ومجموعات الأدوار والأذونات، راجع الموارد التالية:
>
> - [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
> - [الأدوار المضمنة في Azure AD](/azure/active-directory/roles/permissions-reference)

|Activity|الأدوار والأذونات|
|---|---|
|استخدام لوحة معلومات إدارة الثغرات الأمنية & المخاطر (أو [لوحة معلومات الأمان](security-dashboard.md) الجديدة <p> عرض معلومات حول التهديدات الأخيرة أو الحالية|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان**</li><li>**قارئ الأمان**</li></ul> <p> يمكن تعيين هذه الأدوار إما في Azure Active Directory (<https://portal.azure.com>) أو مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>).|
|استخدام [المستكشف (والكشف في الوقت الحقيقي)](threat-explorer.md) لتحليل التهديدات|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان**</li><li>**قارئ الأمان**</li></ul> <p> يمكن تعيين هذه الأدوار إما في Azure Active Directory (<https://portal.azure.com>) أو مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>).|
|عرض الحوادث (يشار إليها أيضا باسم التحقيقات) <p> إضافة رسائل بريد إلكتروني إلى حدث|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان**</li><li>**قارئ الأمان**</li></ul> <p> يمكن تعيين هذه الأدوار إما في Azure Active Directory (<https://portal.azure.com>) أو مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>).|
|تشغيل إجراءات البريد الإلكتروني في حادث <p> البحث عن رسائل البريد الإلكتروني المشبوهة وحذفها|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان** بالإضافة إلى دور **البحث والإزالة**</li></ul> <p> يمكن تعيين أدوار **المسؤول العام** ومسؤول **الأمان** إما في Azure Active Directory (<https://portal.azure.com>) أو مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>). <p> يجب تعيين دور **البحث والإزالة** في **أدوار التعاون & البريد الإلكتروني** في مدخل Microsoft 36 Defender (<https://security.microsoft.com>).|
|دمج Microsoft Defender لـ Office 365 الخطة 2 مع Microsoft Defender لنقطة النهاية <p> تكامل Microsoft Defender لـ Office 365 الخطة 2 مع خادم SIEM|إما **دور المسؤول العام** أو **مسؤول الأمان** المعين في Azure Active Directory (<https://portal.azure.com>) أو مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>). <p> --- **Plus** --- <p> دور مناسب تم تعيينه في تطبيقات إضافية (مثل [مركز حماية Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/user-roles) أو خادم SIEM).|

## <a name="next-steps"></a>الخطوات التالية

- [تعرف على متعقبات التهديدات - جديد وجدير بالملاحظة](threat-trackers.md)
- [البحث عن رسائل البريد الإلكتروني الضارة التي تم تسليمها والتحقيق فيها (Office 365 التحقيق في التهديدات والاستجابة لها)](investigate-malicious-email-that-was-delivered.md)
- [دمج Office 365 التحقيق في التهديدات والاستجابة لها مع Microsoft Defender لنقطة النهاية](integrate-office-365-ti-with-mde.md)
- [محاكاة هجوم تصيد احتيالي](attack-simulation-training.md)
