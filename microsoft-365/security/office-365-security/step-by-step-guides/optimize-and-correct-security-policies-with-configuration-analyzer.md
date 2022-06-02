---
title: تحسين نهج الأمان وتصحيحها باستخدام محلل التكوين
description: خطوات تحسين نهج الأمان وتصحيحها باستخدام محلل التكوين. محلل التكوين هو موقع مركزي وجزء واحد من الزجاج لإدارة نهج أمان البريد الإلكتروني التي قمت بتكوينها في المستأجر وعرضها.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: dcb40c0abd619291da2f05fdfa362c03f853181e
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842370"
---
# <a name="optimize-and-correct-security-policies-with-configuration-analyzer"></a>تحسين نهج الأمان وتصحيحها باستخدام محلل التكوين

محلل التكوين هو موقع مركزي وجزء واحد من الزجاج لإدارة نهج أمان البريد الإلكتروني التي قمت بتكوينها في المستأجر وعرضها. يمكنك إجراء مقارنة جنبا إلى جنب لإعداداتك مع الإعدادات الموصى بها القياسية والضيقة، وتطبيق التوصيات وعرض التغييرات التاريخية التي أثرت على وضعك.

## <a name="what-youll-need"></a>ما ستحتاج إليه
- Microsoft Defender لـ Office 365 الخطة 1
- أذونات كافية (دور مسؤول الأمان)
- 5 دقائق لتنفيذ الخطوات أدناه.

## <a name="compare-settings-and-apply-recommendations"></a>مقارنة الإعدادات وتطبيق التوصيات
1. انتقل إلى [https://security.microsoft.com/configurationAnalyzer](https://security.microsoft.com/configurationAnalyzer).
1. اختر **إما توصيات قياسية** أو **توصيات صارمة** من القائمة العلوية استنادا إلى المقارنة جنبا إلى جنب التي تريد إجراؤها.
1. سيتم عرض التوصيات لتغييرات النهج. (إذا كان ذلك ممكنا)
1. يمكنك بعد ذلك تحديد توصية، ولاحظ الإجراء الموصى به، والنهج الذي تنطبق عليه التوصية، وتعيين الاسم & التكوين الحالي وما إلى ذلك.
1. مع تحديد توصية، يمكنك الضغط **على تطبيق التوصية** ثم **موافق** على رسالة التأكيد التي تظهر.
1. إذا كنت ترغب في تحرير نهج يدويا، أو تأكيد الإعدادات مباشرة داخل النهج، يمكنك الضغط على **نهج View** بدلا من **تطبيق التوصية** التي ستقوم بتحميل علامة تبويب جديدة واصطحابك مباشرة إلى النهج المتأثر للسهولة.

## <a name="view-historical-configuration-changes"></a>عرض تغييرات التكوين التاريخية

بينما في **محلل التكوين** يمكنك تحديد **تحليل انحراف التكوين والمحفوظات** من شريط القوائم العلوي.

ستعرض لك الصفحة التي يتم تحميلها التعديلات على نهج الأمان الخاصة بك في الإطار الزمني المحدد بواسطة عوامل التصفية، بالإضافة إلى بيانات حول التغيير وإذا زاد أو قلل من وضعك العام.

لمعرفة المزيد من التفاصيل حول محلل التكوين، راجع [محلل التكوين لنهج الأمان - Office 365 | Microsoft Docs](../../office-365-security/configuration-analyzer-for-security-policies.md).
