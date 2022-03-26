---
title: إمكانات الاستجابة & المخاطر - Microsoft Defender Office 365 الخطة 2
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
description: تعرف على قدرات الاستجابة والتحري عن المخاطر في Microsoft Defender Office 365 الخطة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ce7541010999b87e49880446594a79593a16a30a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63565941"
---
# <a name="threat-investigation-and-response"></a>التحقيق في التهديدات والاستجابة لها

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 2](defender-for-office-365.md)


تساعد قدرات الاستجابة والتحري عن المخاطر في [Microsoft Defender for Office 365](defender-for-office-365.md) محللي الأمان والمسؤولين على حماية Microsoft 365 لمستخدمي الشركات من خلال:

- سهولة التعرف على الهجمات الإلكترونية ومراقبتها وفهمها.
- المساعدة على معالجة التهديدات بسرعة في Exchange Online SharePoint عبر الإنترنت OneDrive for Business Microsoft Teams.
- توفير معارف ورؤى لمساعدة عمليات الأمان على منع الهجمات الإلكترونية ضد مؤسساتها.
- استخدام الاستجابة [والتحري التلقائي في](automated-investigation-response-office.md) Office 365 المخاطر الهامة المستندة إلى البريد الإلكتروني.

توفر قدرات الاستجابة والتحري عن المخاطر معلومات متعمقة حول التهديدات والإجراءات ذات الصلة بالاستجابة المتوفرة في مدخل Microsoft 365 Defender. بإمكان هذه المعلومات أن تساعد فريق الأمان في مؤسستك على حماية المستخدمين من الهجمات المستندة إلى البريد الإلكتروني أو الملفات. تساعد هذه الإمكانات على مراقبة الإشارات وجمع البيانات من مصادر متعددة، مثل نشاط المستخدم والمصادقة والبريد الإلكتروني و أجهزة الكمبيوتر الشخصية التي تم اختراقها والحوادث المتعلقة الأمان. يمكن لصانعي قرارات الأعمال وفريق عمليات الأمان استخدام هذه المعلومات لفهم التهديدات التي تواجه مؤسستك والاستجابة لها وحماية الملكية الفكرية الخاصة بك.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>التعرف على أدوات الاستجابة والتحري عن المخاطر

قدرات الاستجابة والتحري عن المخاطر في مدخل Microsoft 365 Defender هي <https://security.microsoft.com> مجموعة من الأدوات ومسيرات سير عمل الاستجابة التي تتضمن:

- [المستكشف](#explorer)
- [الأحداث](#incidents)
- [التدريب على محاكاة الهجمات](attack-simulation-training.md)
- [إجراء عمليات التحقيق والاستجابة التلقائية](automated-investigation-response-office.md)

### <a name="explorer"></a>المستكشف

استخدم [المستكشف (والكشف](threat-explorer.md) في الوقت الحقيقي) لتحليل التهديدات، وشاهد حجم الهجمات مع مرور الوقت، وتحليل البيانات حسب العائلات التي تواجه تهديدات، والبنية الأساسية للمهاجمين، والمزيد. المستكشف (يشار إليه أيضا باسم "مستكشف التهديدات") هو مكان البداية لسير عمل التحقيق الخاص بأي محلل أمان.

![مستكشف التهديدات.](../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png)

لعرض هذا التقرير واستخدامه في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **البريد الإلكتروني & مستكشف** \> **التعاون**. أو، انتقل مباشرة إلى صفحة **المستكشف** ، استخدم <https://security.microsoft.com/threatexplorer>.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 "المعلومات الاستخبارية للتهديدات"

لا تتوفر هذه الميزة إلا إذا كان لديك اشتراك نشط Office 365 E5 أو الوظائف الإضافية Threat Intelligence. لمزيد من المعلومات، راجع صفحة Office 365 Enterprise E5.

عند تشغيل هذه الميزة، ستكون قادرا على تضمين بيانات من Microsoft Defender ل Office 365 في Microsoft 365 Defender لإجراء تحقيق أمان شامل عبر علب بريد Office 365 وأجهزة Windows أخرى.

> [!NOTE]
> ستحتاج إلى الترخيص المناسب لتمكين هذه الميزة.

لتلقي تكامل الجهاز السياقي في Office 365 المخاطر، ستحتاج إلى تمكين إعدادات Defender لنقطة النهاية في لوحة معلومات التوافق & الأمان.

### <a name="incidents"></a>الأحداث

استخدم القائمة "أحداث" (تسمى هذه أيضا "التحقيق") لمشاهدة قائمة بالحوادث الأمنية في رحلة الطيران. يتم استخدام الحوادث لتعقب التهديدات مثل رسائل البريد الإلكتروني المريبة، وإجراء المزيد من عمليات التحقيق والتدريب.

![قائمة أحداث التهديدات الحالية في Office 365.](../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png)

لعرض قائمة الأحداث الحالية لمنظمتك في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى أحداث & **التنبيهات** \> **.** أو، انتقل مباشرة **إلى صفحة الأحداث** ، استخدم <https://security.microsoft.com/incidents>.

![في مركز التوافق & الأمان، اختر مراجعة إدارة \> المخاطر.](../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png)

### <a name="attack-simulation-training"></a>التدريب على محاكاة الهجمات

استخدم التدريب على محاكاة الهجمات لإعداد الهجمات الإلكترونية الواقعية وتشغيلها في مؤسستك، وتحديد الأشخاص الضعاف قبل أن يؤثر هجوم إلكتروني حقيقي على أعمالك. لمعرفة المزيد، راجع [محاكاة هجوم تصيد احتيالي](attack-simulation-training.md).

لعرض هذه الميزة واستخدامها في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى البريد الإلكتروني & **التدريب** >  **على المحاكاة**. أو، انتقل مباشرة إلى صفحة التدريب على **محاكاة** الهجمات، استخدم <https://security.microsoft.com/attacksimulator?viewid=overview>.

### <a name="automated-investigation-and-response"></a>إجراء عمليات التحقيق والاستجابة التلقائية

استخدم قدرات الاستجابات والتحريات التلقائية (AIR) لتوفير الوقت والجهد الذي يرتبط بالمحتوى والأجهزة و الأشخاص المعرضين للمخاطر في مؤسستك. يمكن أن تبدأ عمليات AIR كلما تم تشغيل تنبيهات معينة، أو عند بدء تشغيلها من قبل فريق عمليات الأمان. لمعرفة المزيد، راجع [إجراء عمليات التحقيق والاستجابة التلقائية في Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>عناصر واجهة مستخدم المعلومات الخاصة بالخطر

كجزء من عرض Microsoft Defender Office 365 الخطة 2، يمكن لمحللو الأمان مراجعة التفاصيل حول خطر معروف. هذا مفيد لتحديد ما إذا كان هناك المزيد من الإجراءات/الخطوات الوقائية التي يمكن اتخاذها للحفاظ على أمان المستخدمين.

![تظهر اتجاهات الأمان معلومات حول التهديدات الأخيرة.](../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png)

## <a name="how-do-we-get-these-capabilities"></a>كيف يمكننا الحصول على هذه الإمكانات؟

Microsoft 365 قدرات الاستجابة والتحري عن المخاطر في Microsoft Defender Office 365 الخطة 2، المضمنة في Enterprise E5 أو كعينة إضافية لاشتراكات معينة. لمعرفة المزيد، راجع [Defender for Office 365 1 الخطة 1 الخطة 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="required-roles-and-permissions"></a>الأدوار والأذونات المطلوبة

يستخدم Microsoft Defender for Office 365 التحكم بالوصول المستند إلى الدور. يتم تعيين الأذونات من خلال أدوار معينة في Azure Active Directory أو مركز مسؤولي Microsoft 365 أو مدخل Microsoft 365 Defender.

> [!TIP]
> على الرغم من أنه يمكن تعيين بعض الأدوار، مثل مسؤول الأمان، في مدخل Microsoft 365 Defender، يمكنك استخدام مركز مسؤولي Microsoft 365 أو Azure Active Directory بدلا من ذلك. للحصول على معلومات حول الأدوار ومجموعات الأدوار والأذونات، راجع الموارد التالية:
>
> - [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
> - [أدوار Azure AD المضمنة](/azure/active-directory/roles/permissions-reference)

<br>

****

|Activity|الأدوار والأذونات|
|---|---|
|استخدام لوحة معلومات إدارة & المخاطر (أو لوحة [معلومات الأمان الجديدة](security-dashboard.md) <p> عرض معلومات حول التهديدات الأخيرة أو الحالية|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان**</li><li>**قارئ الأمان**</li></ul> <p> يمكن تعيين هذه الأدوار في Azure Active Directory (<https://portal.azure.com>) أو في مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>).|
|استخدام [المستكشف (والكشف في الوقت الحقيقي)](threat-explorer.md) لتحليل التهديدات|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان**</li><li>**قارئ الأمان**</li></ul> <p> يمكن تعيين هذه الأدوار في Azure Active Directory (<https://portal.azure.com>) أو في مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>).|
|عرض الأحداث (يشار إليها أيضا باسم "التحقيق") <p> إضافة رسائل بريد إلكتروني إلى حادث|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان**</li><li>**قارئ الأمان**</li></ul> <p> يمكن تعيين هذه الأدوار في Azure Active Directory (<https://portal.azure.com>) أو في مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>).|
|تشغيل إجراءات البريد الإلكتروني في حادث <p> البحث عن رسائل البريد الإلكتروني المريبة وحذفها|أحد الإجراءات التالية: <ul><li>**المسؤول العام**</li><li>**مسؤول الأمان** بالإضافة إلى **دور البحث و الازدحام**</li></ul> <p> يمكن **تعيين أدوار المسؤول** العام ومسؤول الأمان إما في Azure Active Directory (<https://portal.azure.com>) أو في مركز مسؤولي Microsoft 365 ().<https://admin.microsoft.com> <p> يجب **تعيين** دور البحث و الازدحام في دور & البريد الإلكتروني **في** مدخل Microsoft 36 Defender (<https://security.microsoft.com>).|
|دمج Microsoft Defender Office 365 2 مع Microsoft Defender لنقطة النهاية <p> دمج Microsoft Defender Office 365 2 مع خادم SIEM|إما دور **المسؤول** العام أو مسؤول  الأمان المعين في Azure Active Directory (<https://portal.azure.com>) أو مركز مسؤولي Microsoft 365 ().<https://admin.microsoft.com> <p> --- **بالإضافة إلى** --- <p> دور مناسب تم تعيينه في تطبيقات إضافية (مثل مركز حماية Microsoft Defender [](/windows/security/threat-protection/microsoft-defender-atp/user-roles) خادم SIEM).|
|

## <a name="next-steps"></a>الخطوات التالية

- [تعرف على متعقبات التهديدات - جديد و جدير بالملاحظة](threat-trackers.md)
- [البحث عن البريد الإلكتروني الضار الذي تم تسليمه (Office 365 والرد عليه)](investigate-malicious-email-that-was-delivered.md)
- [دمج Office 365 المخاطر والاستجابة لها مع Microsoft Defender لنقطة النهاية](integrate-office-365-ti-with-mde.md)
- [محاكاة هجوم تصيد احتيالي](attack-simulation-training.md)
