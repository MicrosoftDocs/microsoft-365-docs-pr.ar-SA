---
title: التعرّف على عوائق المعلومات
description: تعرف على حواجز المعلومات في Microsoft Purview.
keywords: Microsoft 365 وMicrosoft Purview والامتثال وحواجز المعلومات
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 72a53580222b315f86fd397e391b026937b8035b
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287167"
---
# <a name="learn-about-information-barriers"></a>التعرّف على عوائق المعلومات

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تتضمن خدمات Microsoft السحابية إمكانات قوية للاتصال والتعاون. ولكن لنفترض أنك تريد تقييد الاتصال والتعاون بين مجموعتين لتجنب حدوث تعارض في الاهتمام في مؤسستك. أو ربما تريد تقييد الاتصال والتعاون بين أشخاص معينين داخل مؤسستك من أجل حماية المعلومات الداخلية. Microsoft 365 تمكين التواصل والتعاون عبر المجموعات والمؤسسات، هل هناك طريقة لتقييد الاتصال والتعاون بين مجموعات معينة من المستخدمين عند الضرورة؟ مع حواجز معلومات Microsoft Purview (IB)، يمكنك!

تدعم Microsoft Teams SharePoint Online و OneDrive for Business حواجز المعلومات. بافتراض أن [اشتراكك](#required-licenses-and-permissions) يتضمن حواجز المعلومات أو مسؤول الامتثال أو مسؤول حواجز المعلومات يمكن أن يحدد النهج للسماح بالاتصالات بين مجموعات المستخدمين في Microsoft Teams أو منعها. يمكن استخدام نهج حاجز المعلومات لحالات مثل هذه:

- يجب ألا يتصل المستخدم في مجموعة التاجر اليومي بالملفات أو يشاركها مع فريق التسويق
- يجب ألا يقوم موظفو الشؤون المالية الذين يعملون على معلومات سرية للشركة بتوصيل الملفات أو مشاركتها مع مجموعات معينة داخل مؤسستهم
- يجب ألا يتصل الفريق الداخلي الذي يحتوي على مواد سرية تجارية أو يدردش عبر الإنترنت مع أشخاص في مجموعات معينة داخل مؤسستهم
- يجب على فريق البحث الاتصال أو الدردشة عبر الإنترنت فقط مع فريق تطوير المنتجات
- يجب ألا تتم مشاركة موقع لمجموعة التاجر اليومي أو الوصول إليه من قبل أي شخص خارج مجموعة التاجر اليومي

> [!IMPORTANT]
> حواجز المعلومات ***فقط تدعم** _ القيود ثنائية الاتجاه. يمكن للقيود، مثل التسويق، التواصل والتعاون مع تجار اليوم، ولكن يتعذر على المتداولين اليومي التواصل والتعاون مع التسويق _*_غير مدعوم_**.

بالنسبة إلى جميع هذه السيناريوهات النموذجية (وأكثر من ذلك)، يمكن تعريف نهج حاجز المعلومات لمنع الاتصالات والتعاون أو السماح بها في Microsoft Teams SharePoint Online و OneDrive. يمكن أن تمنع هذه النهج الأشخاص من الاتصال أو الدردشة مع الأشخاص الذين لا ينبغي عليهم إجراء محادثة معهم، أو تمكين الأشخاص من التواصل مع مجموعات معينة فقط في Microsoft Teams. مع تطبيق نهج حاجز المعلومات، كلما حاول المستخدمون الذين تغطيهم هذه النهج التواصل والتعاون مع الآخرين في Microsoft Teams، يتم إجراء عمليات التحقق من SharePoint Online أو OneDrive لمنع (أو السماح) بالاتصال والتعاون (كما هو محدد بواسطة نهج حواجز المعلومات).

لمعرفة المزيد حول تجربة المستخدم مع حواجز المعلومات، راجع:

- [حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [حواجز المعلومات في OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> حاليا، لا تنطبق حواجز المعلومات على اتصالات البريد الإلكتروني. بالإضافة إلى ذلك، فإن حواجز المعلومات مستقلة عن [حدود الامتثال](set-up-compliance-boundaries.md).<p> قبل تحديد نهج حاجز المعلومات وتطبيقها، تأكد من أن مؤسستك ليس لديها [نهج دفتر عناوين Exchange](/exchange/address-books/address-book-policies/address-book-policies) سارية المفعول. (تستند حواجز المعلومات إلى نهج دفتر العناوين.)

## <a name="what-happens-with-information-barriers"></a>ماذا يحدث مع حواجز المعلومات

عندما تكون نهج حاجز المعلومات في مكانها، لن يتمكن الأشخاص الذين لا يجب عليهم الاتصال بالملفات أو مشاركتها مع مستخدمين محددين آخرين من العثور على هؤلاء المستخدمين أو تحديدهم أو الدردشة معهم أو الاتصال معهم. مع حواجز المعلومات، يتم إجراء عمليات فحص لمنع الاتصال والتعاون غير المصرح به.

تنطبق حواجز المعلومات على Microsoft Teams (الدردشات والقنوات)، SharePoint عبر الإنترنت OneDrive. في Microsoft Teams، تحدد نهج حاجز المعلومات الأنواع التالية من الاتصالات غير المصرح بها وتمنعها:

- البحث عن مستخدم
- إضافة عضو إلى فريق
- بدء جلسة محادثة مع شخص ما
- بدء دردشة جماعية
- دعوة شخص ما للانضمام إلى اجتماع
- مشاركة شاشة
- إجراء مكالمة
- مشاركة ملف مع مستخدم آخر
- الوصول إلى الملف من خلال ارتباط المشاركة

إذا تم تضمين الأشخاص المعنيين في نهج حاجز المعلومات لمنع النشاط، فلن يتمكنوا من المتابعة. بالإضافة إلى ذلك، من المحتمل أن يكون كل شخص مضمن في سياسة حاجز المعلومات محظورا من التواصل مع الآخرين في Microsoft Teams. عندما يكون الأشخاص المتأثرون بنهج حاجز المعلومات جزءا من نفس الفريق أو الدردشة الجماعية، فقد تتم إزالتهم من جلسات الدردشة هذه وقد لا يسمح بالمزيد من التواصل مع المجموعة.

لمعرفة المزيد حول تجربة المستخدم مع حواجز المعلومات، راجع [حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

في SharePoint Online و OneDrive، تحدد نهج حاجز المعلومات الأنواع التالية من التعاون غير المصرح به وتمنعها:

- إضافة عضو إلى موقع
- الوصول إلى الموقع أو المحتوى من قبل مستخدم
- مشاركة الموقع أو المحتوى مع مستخدم آخر
- البحث في موقع

لمعرفة المزيد حول تجربة المستخدم مع حواجز المعلومات، راجع [حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>التراخيص والأذونات المطلوبة

قبل البدء باستخدام IB، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) وأي وظائف إضافية. للوصول إلى IB واستخدامه، يجب أن يكون لدى مؤسستك أحد الاشتراكات أو الوظائف الإضافية التالية:

- اشتراك Microsoft 365 E5/A5 (إصدار مدفوع أو تجريبي)
- اشتراك Office 365 E5/A5/A3/A1 (إصدار مدفوع أو تجريبي)
- خدمات الامتثال المتطورة في Office 365 الوظيفة الإضافية (لم تعد متوفرة للاشتراكات الجديدة)
- اشتراك Microsoft 365 E3/A3/A1 + الوظيفة الإضافية Microsoft 365 E5/A5 Compliance
- اشتراك Microsoft 365 E3/A3/A1 + الوظيفة الإضافية Microsoft 365 E5/A5 Insider Risk Management

لمزيد من المعلومات، راجع [إرشادات الترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

[لتعريف نهج حاجز المعلومات أو تحريرها](information-barriers-policies.md)، يجب تعيين أحد الأدوار التالية:

- مسؤول عام Microsoft 365
- مسؤول عام Office 365
- مسؤول التوافق
- إدارة الامتثال ل IB

(لمعرفة المزيد حول الأدوار والأذونات، راجع [الأذونات في مركز التوافق & الأمان Office 365](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).)

يجب أن تكون على دراية ب PowerShell cmdlets من أجل تحديد نهج حاجز المعلومات أو التحقق من صحتها أو تحريرها. على الرغم من أننا نقدم العديد من الأمثلة على PowerShell cmdlets في [المقالة الإرشادية](information-barriers-policies.md)، ستحتاج إلى معرفة تفاصيل أخرى، مثل المعلمات، لمؤسستك.

## <a name="next-steps"></a>الخطوات التالية

- [تعرف على المزيد حول حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [تعرف على المزيد حول حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [تعرف على المزيد حول حواجز المعلومات في OneDrive](/onedrive/information-barriers)
- [راجع السمات التي يمكن استخدامها لنهج حاجز المعلومات](information-barriers-attributes.md)
- [تحديد نهج لحواجز المعلومات](information-barriers-policies.md)
- [تحرير (أو إزالة) نهج حاجز المعلومات](information-barriers-edit-segments-policies.md)
