---
title: (نتائج إيجابية خاطئة) كيفية معالجة رسائل البريد الإلكتروني المشروعة التي يتم منعها من التسليم باستخدام Microsoft Defender لـ Office 365
description: خطوات معالجة حظر البريد الإلكتروني المشروع (إيجابية زائفة) بواسطة Microsoft Defender لـ Office 365 من أجل منع فقدان العمل.
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
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: abf348fd4de02f521dfa9c5f8d7c16346753c5de
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043644"
---
# <a name="how-to-handle-legitimate-emails-getting-blocked-false-positive-using-microsoft-defender-for-office-365"></a>كيفية معالجة رسائل البريد الإلكتروني المشروعة التي يتم حظرها (False Positive)، باستخدام Microsoft Defender لـ Office 365

تساعد Microsoft Defender لـ Office 365 على التعامل مع رسائل البريد الإلكتروني الهامة للأعمال المشروعة التي تم حظرها عن طريق الخطأ كتهديدات (الإيجابيات الخاطئة). يمكن أن يساعد Defender لـ Office 365 المسؤولين على فهم *سبب* حظر رسائل البريد الإلكتروني المشروعة، وكيفية حل الموقف بسرعة، ومنع حدوث حالات مماثلة في المستقبل.

## <a name="what-youll-need"></a>ما ستحتاج إليه

- Microsoft Defender لـ Office 365 الخطة 1 أو 2 (مضمنة كجزء من E5). يمكن للعملاء Exchange Online أيضا الاستفادة من هذه الميزة.
- أذونات كافية (دور مسؤول الأمان).
- من 5 إلى 10 دقائق لتنفيذ الخطوات أدناه.

## <a name="handling-legitimate-emails-in-to-junk-folder-of-end-users"></a>معالجة رسائل البريد الإلكتروني المشروعة في مجلد البريد الإلكتروني غير الهام للمستخدمين النهائيين

1. اطلب من المستخدمين الإبلاغ عن البريد الإلكتروني على أنه **ليس غير هام** باستخدام وظيفة Microsoft Message الإضافية أو أزرار Outlook.
2. يمكن للمستخدمين النهائيين أيضا إضافة المرسل إلى [**قائمة المرسلين الآمنة**](https://support.microsoft.com/en-us/office/safe-senders-in-outlook-com-470d4ee6-e3b6-402b-8cd9-a6f00eda7339) في Outlook لمنع وصول البريد الإلكتروني من هؤلاء المرسلين إلى مجلد "البريد غير الهام".
3. يمكن للمسؤولين فرز الرسائل التي أبلغ عنها المستخدم من مدخل [المحتوى الذي أبلغ عنه المستخدم](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
4. من تلك الرسائل التي تم الإبلاغ عنها، يمكن للمسؤولين إرسالها إلى [**Microsoft للتحليل**](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) وفهم سبب حظر هذا البريد الإلكتروني في المقام الأول.
5. إذا لزم الأمر، أثناء الإرسال إلى Microsoft للتحليل، يمكن للمسؤولين إنشاء [**السماح** للمرسل](/microsoft-365/security/office-365-security/manage-tenant-allows?view=o365-worldwide#add-sender-allows-using-the-submissions-portal&preserve-view=true) بخفة للتخفيف من المشكلة.
6. بمجرد توفر نتائج إرسال المسؤول، اقرأها لفهم سبب حظر رسائل البريد الإلكتروني وكيفية تحسين إعداد المستأجر *لمنع* حدوث حالات مماثلة في المستقبل.

## <a name="handling-legitimate-emails-that-are-in-quarantine-folder-of-end-users"></a>معالجة رسائل البريد الإلكتروني المشروعة الموجودة في مجلد العزل للمستخدمين النهائيين

1. يتلقى المستخدم النهائي [ملخص بريد إلكتروني](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide&preserve-view=true) حول الرسائل المعزولة وفقا للإعدادات التي قام مسؤولو الأمان بتمكينها.
2. يمكن للمستخدمين النهائيين معاينة الرسائل في العزل، وحظر المرسل، وتحرير الرسائل، وإرسال هذه الرسائل إلى Microsoft للتحليل، وطلب إصدار رسائل البريد الإلكتروني هذه من المسؤولين.

## <a name="handling-legitimate-emails-in-quarantine-folder-of-an-admin"></a>معالجة رسائل البريد الإلكتروني المشروعة في مجلد العزل لمسؤول

1. يمكن للمسؤولين عرض رسائل البريد الإلكتروني المعزولة (بما في ذلك تلك التي تطلب الإذن لطلب الإصدار) من [صفحة المراجعة](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide&preserve-view=true).
2. يمكن للمسؤولين تحرير الرسالة من العزل أثناء إرسالها إلى Microsoft للتحليل، وإنشاء السماح للتخفيف من الموقف.
3. بمجرد توفر نتائج عمليات الإرسال، يجب على المسؤولين قراءة الحكم لفهم سبب حظر رسائل البريد الإلكتروني، وكيف يمكن تحسين إعداد المستأجر لمنع حدوث حالات مماثلة في المستقبل.
