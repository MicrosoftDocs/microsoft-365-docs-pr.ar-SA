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
description: يمكن للمسؤولين التعرف على ميزات الحماية من التصيد الاحتيالي في Exchange Online Protection (EOP) و Microsoft Defender Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 81cd2870ff3471fbd535415229b3ced20bba1fbf
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63566561"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>الحماية من التصيد الاحتيالي في Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*التصيد الاحتيالي* هو هجوم عبر البريد الإلكتروني يحاول سرقة معلومات حساسة في الرسائل التي تبدو أنها من مرسلين شرعيين أو موثوق بهم. هناك فئات معينة من التصيد الاحتيالي. على سبيل المثال:

- **يستخدم التصيد** الاحتيالي غير المقصود محتوى مركز عليه ومخصص تم تخصيصه خصيصا للمستلمين المستهدفين (عادة، بعد الاستطلاع على المستلمين من قبل المهاجم).

- **يتم توجيه Whaling** إلى المديرين التنفيذيين أو أهداف أخرى ذات قيمة عالية داخل المؤسسة للحصول على أقصى تأثير.

- يستخدم اختراق البريد الإلكتروني للأعمال **(BEC)** المرسلين الموثوق بهم التزييف (الموظفين الماليين والعملاء والشركاء الموثوق بهم وما إلى ذلك) لتخدع المستلمين بالموافقة على المدفوعات أو تحويل الأموال أو الكشف عن بيانات العملاء. تعرف على المزيد من خلال [مشاهدة هذا الفيديو](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- **برامج الفدية الضارة** التي تقوم بتشفير بياناتك وتطالب بالدفع لفك تشفيرها تبدأ دائما في رسائل التصيد الاحتيالي. لا يمكن للحماية من التصيد الاحتيالي مساعدتك على فك تشفير الملفات المشفرة، ولكنها تساعد في الكشف عن رسائل التصيد الاحتيالي الأولية المقترنة لحملة برامج الفدية الضارة. لمزيد من المعلومات حول الاستعادة من هجوم برامج الفدية الضارة، راجع استرداد من هجوم برامج الفدية [الضارة في](recover-from-ransomware.md) Microsoft 365.

مع التعقيد المتزايد للهجمات، من الصعب على المستخدمين المدربين التعرف على رسائل التصيد الاحتيالي المعقدة. لحسن الحظ، Exchange Online Protection (EOP) والميزات الإضافية في Microsoft Defender Office 365 مساعدتك.

## <a name="anti-phishing-protection-in-eop"></a>الحماية من التصيد الاحتيالي في EOP

يحتوي EOP (أي Microsoft 365 التي لا تتضمن Microsoft Defender for Office 365) على ميزات يمكن أن تساعد في حماية مؤسستك من تهديدات التصيد الاحتيالي:

- المعلومات المنتحلة: استخدم المعلومات الاستخبارية المنتحلة لمراجعة المرسلين الذين تم اكتشافهم منتحلين في رسائل من مجالات خارجية وداخلية، والسماح أو حظر هؤلاء المرسلين المكتشفين يدويا. لمزيد من المعلومات، راجع [معلومات المعلومات المنتحلة في EOP](learn-about-spoof-intelligence.md).

- سياسات مكافحة التصيد الاحتيالي في **EOP**: تشغيل المعلومات المنتحلة أو إيقاف تشغيلها، تشغيل تحديد هوية المرسل غير المملوك في Outlook أو إيقاف تشغيله، وتحديد الإجراء للمرسلين المحظورين المخادعين. لمزيد من المعلومات، راجع [تكوين سياسات مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md).

- السماح بالمرسلين المنتحلين أو حظرهم في قائمة السماح **/** الحظر للمستأجر: عندما تطغى على القرار في معلومات المعلومات المنتحلة، يتحول المرسل المزلوف إلى إدخال السماح أو الحظر اليدوي الذي يظهر فقط على علامة التبويب انتحال  في قائمة السماح/الحظر للمستأجر. يمكنك أيضا إنشاء إدخالات السماح أو الحظر يدويا للمرسلين المنتحلين قبل اكتشافهم بواسطة المعلومات المنتحلة. لمزيد من المعلومات، راجع [إدارة قائمة السماح/الحظر للمستأجر في EOP](tenant-allow-block-list.md).

- مصادقة البريد الإلكتروني **الضمنية:** يحسن EOP عمليات التحقق القياسية من مصادقة البريد الإلكتروني للبريد الإلكتروني الوارد ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md) [وDKIM](use-dkim-to-validate-outbound-email.md) [وDMARC](use-dmarc-to-validate-email.md) مع سمعة المرسل ومحفوظات المرسلين ومحفوظات المستلمين والتحليل السلوكي والتقنيات المتقدمة الأخرى للمساعدة في تحديد المرسلين المزيفة. لمزيد من المعلومات، راجع [مصادقة البريد الإلكتروني في Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>حماية إضافية من التصيد الاحتيالي في Microsoft Defender Office 365

يحتوي Microsoft Defender for Office 365 على ميزات إضافية وأكثر تقدما لمكافحة التصيد الاحتيالي:

- سياسات مكافحة التصيد الاحتيالي في **Microsoft Defender ل Office 365**: تكوين إعدادات الحماية من انتحال الشخصية لمرسلي رسائل ومجالات مرسلين معينة وإعدادات معلومات علب البريد وعتبات التصيد الاحتيالي المتقدمة القابلة للتعديل. لمزيد من المعلومات، راجع تكوين سياسات مكافحة التصيد الاحتيالي [في Microsoft Defender Office 365](configure-mdo-anti-phishing-policies.md). لمزيد من المعلومات حول الاختلافات بين سياسات مكافحة التصيد الاحتيالي في EOP ونهج مكافحة التصيد الاحتيالي في Defender for Office 365، راجع سياسات مكافحة التصيد الاحتيالي في [Microsoft 365.](set-up-anti-phishing-policies.md)
- **طرق عرض الحملة**: يحدد التعلم الآلي والرسائل التحليلية الأخرى الرسائل المنسوبة إلى هجمات التصيد الاحتيالي المنسوبة إلى الخدمة بكاملها وضد مؤسستك وتحليلها. لمزيد من المعلومات، راجع [طرق عرض الحملات في Microsoft Defender Office 365](campaigns.md).
- **التدريب على محاكاة** الهجمات: يمكن للمسؤولين إنشاء رسائل تصيد احتيال زائف وإرسالها إلى مستخدمين داخليين كأداة تعليمية. لمزيد من المعلومات، راجع [محاكاة هجوم تصيد احتيالي](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>موارد أخرى لمكافحة التصيد الاحتيالي

- للمستخدمين النهائيين: [يمكنك حماية نفسك من مخططات التصيد الاحتيالي وأشكال الاحتيال الأخرى عبر الإنترنت](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [كيفية Microsoft 365 التحقق من صحة العنوان من لمنع التصيد الاحتيالي](how-office-365-validates-the-from-address.md).
