---
title: تقييم الوصول المتحكم به إلى المجلد
description: تعرف على كيف يمكن أن يساعد الوصول المتحكم به إلى المجلدات على حماية الملفات من أن يتم تغييرها بواسطة التطبيقات الضارة.
keywords: الحماية من المخاطر، windows 10، windows 11، windows defender، برامج الفدية الضارة، الحماية، التقييم، الاختبار، العرض التوضيحي، تجربة
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: 85e2da73fd54bd4d24e5ab8c4d104e33b5b4d877
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63571502"
---
# <a name="evaluate-controlled-folder-access"></a>تقييم الوصول المتحكم به إلى المجلد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[إن الوصول المتحكم به إلى](controlled-folders.md) المجلدات هو ميزة تساعد على حماية مستنداتك وملفاتك من التعديل بواسطة التطبيقات المريبة أو الضارة. يتم دعم الوصول المتحكم به إلى المجلدات على Windows Server 2019 Windows Server 2022 و Windows 10 و Windows 11 العملاء.

وهو مفيد على وجه الخصوص في المساعدة على الحماية من برامج [الفدية](https://www.microsoft.com/wdsi/threats/ransomware) الضارة التي تحاول تشفير ملفاتك وحمايتها.

تساعدك هذه المقالة على تقييم الوصول المتحكم به إلى المجلدات. وهو يشرح كيفية تمكين وضع التدقيق بحيث يمكنك اختبار الميزة مباشرة في مؤسستك.

> [!TIP]
> يمكنك أيضا زيارة موقع سيناريو العرض التوضيحي ل Microsoft Defender ل Endpoint على [](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) demo.wd.microsoft.com للتأكد من أن الميزة تعمل وترى كيفية عملها.

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

## <a name="use-audit-mode-to-measure-impact"></a>استخدام وضع التدقيق لقياس التأثير

تمكين الوصول إلى المجلد المتحكم به في وضع التدقيق لرؤية سجل لما كان سيحدث  إذا تم تمكينه بالكامل. اختبر كيفية عمل الميزة في مؤسستك للتأكد من أنها لا تؤثر على تطبيقات خط العمل. يمكنك أيضا الحصول على فكرة حول عدد محاولات تعديل الملفات المريبة التي تحدث عادة خلال فترة زمنية معينة.

لتمكين وضع التدقيق، استخدم cmdlet التالي في PowerShell:

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> إذا كنت تريد التدقيق الكامل في كيفية عمل الوصول إلى المجلدات الخاضعة للتحكم في مؤسستك، ستحتاج إلى استخدام أداة إدارة لنشر هذا الإعداد على الأجهزة في الشبكة (الأجهزة).
يمكنك أيضا استخدام نهج المجموعة أو Intune أو إدارة أجهزة المحمول (MDM) أو إدارة نقاط النهاية من Microsoft لتكوين الإعداد ونشره، كما هو موضح في موضوع الوصول إلى المجلدات الذي يتم التحكم [فيه.](controlled-folders.md)

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>مراجعة أحداث الوصول إلى المجلدات الخاضعة للتحكم في Windows الحدث

تظهر أحداث الوصول إلى المجلدات التي يتم التحكم بها التالية في Windows الحدث ضمن Microsoft/Windows/Windows Defender/Operational.

"معرّف الحدث" | الوصف
-|-
 5007 | حدث عند تغيير الإعدادات
 1124 | حدث الوصول إلى المجلدات التي تم تدقيقها
 1123 | حدث الوصول إلى المجلدات المحظورة التي تم التحكم فيها

> [!TIP]
> يمكنك تكوين اشتراك Windows ["إعادة توجيه الأحداث"](/windows/win32/wec/setting-up-a-source-initiated-subscription) لتجميع السجلات مركزيا. 

## <a name="customize-protected-folders-and-apps"></a>تخصيص المجلدات والتطبيقات المحمية

أثناء التقييم، قد ترغب في إضافة إلى قائمة المجلدات المحمية، أو السماح لتطبيقات معينة بتعديل الملفات.

راجع [حماية المجلدات](controlled-folders.md) المهمة باستخدام إمكانية الوصول إلى المجلدات الخاضعة للتحكم لتكوين الميزة باستخدام أدوات الإدارة، بما في ذلك موفري خدمة تكوين نهج المجموعة و PowerShell و MDM (CSPs).

## <a name="see-also"></a>راجع أيضًا

* [حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات](controlled-folders.md)
* [تقييم Microsoft Defender لنقطة النهاية](evaluate-mde.md)
* [استخدام وضع التدقيق](audit-windows-defender.md)
