---
title: (سلبيات خاطئة) كيفية معالجة رسائل البريد الإلكتروني الضارة التي يتم تسليمها إلى المستلمين باستخدام Microsoft Defender لـ Office 365
description: خطوات التعامل مع رسائل البريد الإلكتروني الضارة الواردة إلى المستخدمين النهائيين وعلب الوارد (ك "سلبيات خاطئة") مع Microsoft Defender لـ Office 365 لمنع فقدان الأعمال.
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
manager: jarogers
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: d9827af44cb7ea6f573f453fd1db6ac1c2de79d6
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842362"
---
# <a name="how-to-handle-malicious-emails-that-are-delivered-to-recipients-false-negatives-using-microsoft-defender-for-office-365"></a>كيفية معالجة رسائل البريد الإلكتروني الضارة التي يتم تسليمها إلى المستلمين (السلبيات الخاطئة)، باستخدام Microsoft Defender لـ Office 365

تساعد Microsoft Defender لـ Office 365 على التعامل مع رسائل البريد الإلكتروني الضارة (السلبية الخاطئة) التي يتم تسليمها إلى المستلمين والتي تعرض إنتاجيتك المؤسسية للخطر.
يمكن أن يساعدك Defender لـ Office 365 على فهم سبب تسليم رسائل البريد الإلكتروني، وكيفية حل الموقف بسرعة، وكيفية منع حدوث حالات مماثلة في المستقبل.

## <a name="what-youll-need"></a>ما ستحتاج إليه

- Microsoft Defender لـ Office 365 الخطة 1 و2 (مضمنة كجزء من E3 وE5). يمكن لعملاء EOP أيضا الاستفادة من هذا.
- أذونات كافية (دور مسؤول الأمان).
- من 5 إلى 10 دقائق لتنفيذ الخطوات أدناه.

## <a name="handling-malicious-emails-in-the-inbox-folder-of-end-users"></a>معالجة رسائل البريد الإلكتروني الضارة في مجلد علبة الوارد للمستخدمين النهائيين
1. اطلب من المستخدمين الإبلاغ عن البريد الإلكتروني على أنه **تصيد احتيالي** أو **غير هام** باستخدام وظيفة Microsoft Message الإضافية أو وظيفة Microsoft Phish الإضافية أو أزرار Outlook.
2. يمكن للمستخدمين النهائيين أيضا إضافة المرسل إلى [قائمة مرسلي الحظر](https://support.microsoft.com/en-us/office/block-a-mail-sender-b29fd867-cac9-40d8-aed1-659e06a706e4#:~:text=1%20On%20the%20Home%20tab%2C%20in%20the%20Delete,4%20Click%20OK%20in%20both%20open%20dialog%20boxes..) في Outlook لمنع وصول رسائل البريد الإلكتروني من بريد هذا المرسل إلى علب الوارد.
3. يمكن للمسؤولين فرز الرسائل التي أبلغ عنها المستخدم من [مدخل المحتوى الذي أبلغ عنه المستخدم](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft) .
4. من تلك الرسائل التي تم الإبلاغ عنها، يمكن للمسؤولين **الإرسال إلى** [Microsoft لتحليلها](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal) لمعرفة سبب السماح بهذا البريد الإلكتروني في المقام الأول.
5. إذا لزم الأمر، أثناء الإرسال إلى Microsoft للتحليل، يمكن [للمسؤولين إنشاء كتلة للمرسل](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide) للتخفيف من المشكلة.
6. بمجرد توفر نتائج عمليات الإرسال، اقرأ الحكم لفهم سبب السماح برسائل البريد الإلكتروني، وكيف يمكن تحسين إعداد المستأجر لمنع حدوث حالات مماثلة في المستقبل.

## <a name="handling-malicious-emails-in-junk-folder-of-end-users"></a>معالجة رسائل البريد الإلكتروني الضارة في مجلد غير هام للمستخدمين النهائيين

1. اطلب من المستخدمين الإبلاغ عن البريد الإلكتروني على أنه **تصيد احتيالي** باستخدام وظيفة Microsoft Message الإضافية أو وظيفة Microsoft Phish الإضافية أو أزرار Outlook.
2. يمكن للمسؤولين فرز الرسائل التي أبلغ عنها المستخدم من مدخل [المحتوى الذي أبلغ عنه المستخدم](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft) .
3. من تلك الرسائل التي تم الإبلاغ عنها، يمكن للمسؤولين **إرسالها إلى** [Microsoft للتحليل](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal) ومعرفة سبب السماح بهذا البريد الإلكتروني في المقام الأول.
4. إذا لزم الأمر، أثناء الإرسال إلى Microsoft للتحليل، يمكن [للمسؤولين إنشاء كتلة للمرسل](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide) للتخفيف من المشكلة.
5. بمجرد توفر نتائج عمليات الإرسال، اقرأ الحكم لفهم سبب السماح برسائل البريد الإلكتروني، وكيف يمكن تحسين إعداد المستأجر لمنع حدوث حالات مماثلة في المستقبل.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-end-users"></a>معالجة رسائل البريد الإلكتروني الضارة المنتقل إليها في مجلد العزل للمستخدمين النهائيين

1. يتلقى المستخدمون [النهائيون ملخص بريد إلكتروني](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide) حول الرسائل المعزولة وفقا للإعدادات التي قام المسؤولون بتمكينها.
2. يمكن للمستخدمين النهائيين معاينة الرسائل في العزل، وحظر المرسل، وإرسال هذه الرسائل إلى Microsoft للتحليل.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-admins"></a>معالجة رسائل البريد الإلكتروني الضارة المنتقل إليها في مجلد العزل للمسؤولين
1. يمكن للمسؤولين عرض رسائل البريد الإلكتروني المعزولة (بما في ذلك تلك التي تطلب الإذن لطلب الإصدار) من [صفحة المراجعة](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide).
2. يمكن للمسؤولين إرسال أي رسائل ضارة أو مشبوهة إلى Microsoft لتحليلها، وإنشاء كتلة للتخفيف من الموقف في انتظار الحكم.
3. بمجرد توفر نتائج عمليات الإرسال، اقرأ الحكم لمعرفة سبب السماح برسائل البريد الإلكتروني، وكيف يمكن تحسين إعداد المستأجر لمنع حدوث حالات مماثلة في المستقبل.
