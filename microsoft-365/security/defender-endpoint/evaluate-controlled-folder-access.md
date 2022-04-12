---
title: تقييم الوصول المتحكم به إلى المجلد
description: تعرف على كيفية مساعدة الوصول المتحكم به إلى المجلدات في حماية الملفات من التغيير بواسطة التطبيقات الضارة.
keywords: الحماية من الاستغلال، windows 10، windows 11، windows defender، برامج الفدية الضارة، الحماية، التقييم، الاختبار، العرض التوضيحي، حاول
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
ms.openlocfilehash: 4ccb91f0a8c181697eb525dd8f5576e6f6cdc0d1
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789811"
---
# <a name="evaluate-controlled-folder-access"></a>تقييم الوصول المتحكم به إلى المجلد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[الوصول إلى المجلدات التي يتم التحكم فيها](controlled-folders.md) هي ميزة تساعد على حماية المستندات والملفات من التعديل من قبل التطبيقات المشبوهة أو الضارة. يتم دعم الوصول إلى المجلدات التي يتم التحكم فيها على عملاء Windows Server 2019 و Windows Server 2022 و Windows 10 و Windows 11.

وهو مفيد بشكل خاص في المساعدة على الحماية من [برامج الفدية الضارة](https://www.microsoft.com/wdsi/threats/ransomware) التي تحاول تشفير ملفاتك والاحتفاظ بها.

تساعدك هذه المقالة على تقييم الوصول المتحكم به إلى المجلد. يشرح كيفية تمكين وضع التدقيق حتى تتمكن من اختبار الميزة مباشرة في مؤسستك.

> [!TIP]
> يمكنك أيضا زيارة موقع سيناريو العرض التوضيحي Microsoft Defender لنقطة النهاية على [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لتأكيد عمل الميزة ومعرفة كيفية عملها.

> [!NOTE]
> تم إهمال الموقع التجريبي ل Defender لنقطة النهاية في demo.wd.microsoft.com وستتم إزالته في المستقبل.

## <a name="use-audit-mode-to-measure-impact"></a>استخدام وضع التدقيق لقياس التأثير

تمكين الوصول إلى المجلد المتحكم به في وضع التدقيق لمشاهدة سجل لما كان *سيحدث* إذا تم تمكينه بالكامل. اختبر كيفية عمل الميزة في مؤسستك للتأكد من أنها لا تؤثر على تطبيقات خط العمل. يمكنك أيضا الحصول على فكرة عن عدد محاولات تعديل الملفات المشبوهة التي تحدث بشكل عام على مدى فترة زمنية معينة.

لتمكين وضع التدقيق، استخدم PowerShell cmdlet التالي:

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> إذا كنت تريد التدقيق الكامل في كيفية عمل الوصول إلى المجلدات التي يتم التحكم فيها في مؤسستك، فستحتاج إلى استخدام أداة إدارة لنشر هذا الإعداد على الأجهزة في الشبكة (الشبكات).
يمكنك أيضا استخدام نهج المجموعة أو Intune أو إدارة الأجهزة المحمولة (MDM) أو إدارة نقاط النهاية من Microsoft لتكوين الإعداد ونشره، كما هو موضح في [موضوع الوصول إلى المجلد الرئيسي الذي يتم التحكم فيه](controlled-folders.md).

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>مراجعة أحداث الوصول إلى المجلدات التي يتم التحكم فيها في Windows عارض الأحداث

تظهر أحداث الوصول إلى المجلدات التي يتم التحكم فيها التالية في Windows عارض الأحداث ضمن مجلد Microsoft/Windows/Windows Defender/Operational.

معرف الحدث | الوصف
-|-
 5007 | حدث عند تغيير الإعدادات
 1124 | حدث الوصول إلى المجلدات المتحكم فيها الذي تم تدقيقه
 1123 | حدث الوصول إلى المجلدات المتحكم فيها المحظور

> [!TIP]
> يمكنك تكوين [اشتراك Windows Event Forwarding](/windows/win32/wec/setting-up-a-source-initiated-subscription) لتجميع السجلات مركزيا. 

## <a name="customize-protected-folders-and-apps"></a>تخصيص المجلدات والتطبيقات المحمية

أثناء التقييم، قد ترغب في الإضافة إلى قائمة المجلدات المحمية، أو السماح لتطبيقات معينة بتعديل الملفات.

راجع [حماية المجلدات الهامة مع الوصول المتحكم به إلى المجلدات](controlled-folders.md) لتكوين الميزة باستخدام أدوات الإدارة، بما في ذلك موفري خدمات تكوين نهج المجموعة وPowerShell وMDM (CSPs).

## <a name="see-also"></a>راجع أيضًا

* [حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات](controlled-folders.md)
* [تقييم Microsoft Defender لنقطة النهاية](evaluate-mde.md)
* [استخدام وضع التدقيق](audit-windows-defender.md)
