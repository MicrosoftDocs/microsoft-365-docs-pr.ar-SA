---
title: الحماية من التصيد الاحتيالي
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: يمكن للمسؤولين التعرف على ميزات الحماية من التصيد الاحتيالي في Exchange Online Protection (EOP) Microsoft Defender لـ Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8d62d2a32342aa6d409e49d790af717b1ccf7d61
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438740"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>الحماية من التصيد الاحتيالي في Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*التصيد الاحتيالي* هو هجوم عبر البريد الإلكتروني يحاول سرقة المعلومات الحساسة في الرسائل التي تبدو من مرسلين شرعيين أو موثوق بهم. هناك فئات معينة من التصيد الاحتيالي. على سبيل المثال:

- يستخدم **التصيد الاحتيالي الرمح** محتوى مركزا ومخصصا مصمما خصيصا للمستلمين المستهدفين (عادة، بعد الاستطلاع على المستلمين من قبل المهاجم).

- يتم توجيه **التعبئة** إلى المديرين التنفيذيين أو أهداف القيمة العالية الأخرى داخل المؤسسة للحصول على أقصى تأثير.

- يستخدم **اختراق البريد الإلكتروني للأعمال (BEC)** المرسلين الموثوق بهم المزيفين (المسؤولين الماليين والعملاء والشركاء الموثوق بهم وما إلى ذلك) لخداع المستلمين للموافقة على المدفوعات أو تحويل الأموال أو الكشف عن بيانات العملاء. تعرف على المزيد من خلال مشاهدة [هذا الفيديو](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- برنامج **الفدية الضارة** الذي يشفر بياناتك ويطالبك بالدفع لفك تشفيرها يبدأ دائما تقريبا في رسائل التصيد الاحتيالي. لا يمكن أن تساعدك الحماية من التصيد الاحتيالي في فك تشفير الملفات المشفرة، ولكنها يمكن أن تساعد في اكتشاف رسائل التصيد الاحتيالي الأولية المرتبطة بحملة برامج الفدية الضارة. لمزيد من المعلومات حول التعافي من هجوم برامج الفدية الضارة، راجع [استرداد من هجوم برامج الفدية الضارة في Microsoft 365](recover-from-ransomware.md).

مع التعقيد المتزايد للهجمات، من الصعب حتى على المستخدمين المدربين التعرف على رسائل التصيد الاحتيالي المتطورة. لحسن الحظ، يمكن أن تساعد Exchange Online Protection (EOP) والميزات الإضافية في Microsoft Defender لـ Office 365.

## <a name="anti-phishing-protection-in-eop"></a>الحماية من التصيد الاحتيالي في EOP

يحتوي EOP (أي المؤسسات Microsoft 365 بدون Microsoft Defender لـ Office 365) على ميزات يمكن أن تساعد في حماية مؤسستك من تهديدات التصيد الاحتيالي:

- **التحليل الذكي المخادعة**: استخدم التحليل الذكي المخادعة لمراجعة المرسلين المخادعة المكتشفين في رسائل من مجالات خارجية وداخلية، والسماح أو حظر هؤلاء المرسلين المكتشفين يدويا. لمزيد من المعلومات، راجع [التحليل الذكي المخادعة في EOP](learn-about-spoof-intelligence.md).

- **نهج مكافحة التصيد الاحتيالي في EOP**: تشغيل التحليل الذكي للانتحال أو إيقاف تشغيله، وتشغيل مؤشرات المرسلين غير المصادق عليهم في Outlook أو إيقاف تشغيلها، وتحديد الإجراء للمرسلين المخادعة المحظورين. لمزيد من المعلومات، راجع [تكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md).

- **السماح بالمرسلين الذين تم تزييفهم أو حظرهم في قائمة السماح/الحظر للمستأجر**: عند تجاوز الحكم في التحليل الذكي المخادع، يصبح المرسل المخادع اسما يدويا أو إدخال حظر يظهر فقط على علامة تبويب **تزييف** الهوية في قائمة السماح/الحظر للمستأجر. يمكنك أيضا إنشاء إدخالات السماح أو الحظر يدويا للمرسلين المخادعة قبل اكتشافهم بواسطة التحليل الذكي للانتحال. لمزيد من المعلومات، راجع [إدارة قائمة السماح/الحظر للمستأجر في EOP](tenant-allow-block-list.md).

- **مصادقة البريد الإلكتروني الضمنية**: يعزز EOP عمليات التحقق القياسية من مصادقة البريد الإلكتروني للبريد الإلكتروني الوارد ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md) [وDKIM](use-dkim-to-validate-outbound-email.md) [وDMARC](use-dmarc-to-validate-email.md) مع سمعة المرسل ومحفوظات المرسل ومحفوظات المستلمين والتحليل السلوكي وغيرها من التقنيات المتقدمة للمساعدة في تحديد المرسلين المغرورين. لمزيد من المعلومات، راجع [مصادقة البريد الإلكتروني في Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>حماية إضافية من التصيد الاحتيالي في Microsoft Defender لـ Office 365

يحتوي Microsoft Defender لـ Office 365 على ميزات إضافية وأكثر تقدما لمكافحة التصيد الاحتيالي:

- **نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365**: تكوين إعدادات حماية الانتحال لمرسلي الرسائل ومجالات المرسلين المحددة وإعدادات تحليل معلومات علبة البريد وحدود التصيد الاحتيالي المتقدمة القابلة للضبط. لمزيد من المعلومات، راجع [تكوين نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](configure-mdo-anti-phishing-policies.md). لمزيد من المعلومات حول الاختلافات بين نهج مكافحة التصيد الاحتيالي في EOP ونهج مكافحة التصيد الاحتيالي في Defender لـ Office 365، راجع [نهج مكافحة التصيد الاحتيالي في Microsoft 365](set-up-anti-phishing-policies.md).
- **طرق عرض الحملة**: يحدد التعلم الآلي والأساليب الاستدائية الأخرى الرسائل التي تشارك في هجمات التصيد الاحتيالي المنسقة ضد الخدمة بأكملها والمؤسسة وتحليلها. لمزيد من المعلومات، راجع [طرق عرض الحملة في Microsoft Defender لـ Office 365](campaigns.md).
- **تدريب محاكاة الهجوم**: يمكن للمسؤولين إنشاء رسائل تصيد احتيالي مزيفة وإرسالها إلى المستخدمين الداخليين كأداة تعليمية. لمزيد من المعلومات، راجع [محاكاة هجوم التصيد الاحتيالي](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>موارد أخرى لمكافحة التصيد الاحتيالي

- للمستخدمين النهائيين: [احمي نفسك من مخططات التصيد الاحتيالي وغيرها من أشكال الاحتيال عبر الإنترنت](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [كيفية Microsoft 365 التحقق من صحة عنوان "من" لمنع التصيد الاحتيالي](how-office-365-validates-the-from-address.md).
