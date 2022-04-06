---
title: تأمين سياسات البريد الإلكتروني المستحسنة - Microsoft 365 للمؤسسات | Microsoft Docs
description: تصف هذه المقالة سياسات توصيات Microsoft حول كيفية تطبيق سياسات البريد الإلكتروني وتكوينه.
ms.author: dansimp
author: dansimp
manager: Laurawi
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- remotework
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 6ab6ff7c043dcceacfbb07d0f6fec5e974999204
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682428"
---
# <a name="policy-recommendations-for-securing-email"></a>توصيات النهج لتأمين البريد الإلكتروني

تصف هذه المقالة كيفية تنفيذ هوية الصفر الموثوق بها ونهج الوصول إلى الجهاز الموصى بها لحماية عملاء البريد الإلكتروني والبريد الإلكتروني في المؤسسة الذين يدعمون المصادقة الحديثة والوصول الشرطي. يعتمد هذا الإرشاد على [سياسات الوصول](identity-access-policies.md) إلى الأجهزة والهوية الشائعة ويتضمن أيضا بعض التوصيات الإضافية.

تستند هذه التوصيات إلى ثلاثة مستويات مختلفة من الأمان والحماية التي يمكن تطبيقها بالاستناد إلى مجموعة **احتياجاتك: نقطة** البداية والمؤسسة **والأمان المتخصص**.  يمكنك معرفة المزيد حول مستويات الأمان هذه، وأنظمت تشغيل العميل الموصى بها، المشار إليها بواسطة هذه التوصيات في مقدمة تكوينات ونهج الأمان [الموصى بها](microsoft-365-policies-configurations.md).

تتطلب هذه التوصيات من المستخدمين استخدام عملاء البريد الإلكتروني الحديث، بما في ذلك Outlook لنظامي التشغيل iOS وAndroid على الأجهزة المحمولة. Outlook ل iOS وAndroid الدعم للحصول على أفضل ميزات Office 365. كما تم Outlook تطبيقات الأجهزة المحمولة هذه مع إمكانات الأمان التي تدعم استخدام الأجهزة المحمولة والعمل معا مع إمكانات الأمان السحابية الأخرى من Microsoft. لمزيد من المعلومات، راجع Outlook الأسئلة الشائعة [حول iOS وAndroid](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>تحديث السياسات الشائعة لتضمين البريد الإلكتروني

لحماية البريد الإلكتروني، يوضح الرسم التخطيطي التالي السياسات التي يجب تحديثها من سياسات الوصول إلى الأجهزة والهوية المشتركة.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="ملخص تحديثات النهج لحماية الوصول إلى Exchange." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

لاحظ إضافة نهج جديد Exchange Online عملاء ActiveSync. وهذا الأمر يجبر على استخدام Outlook المحمول.

إذا قمت Exchange Online Outlook في نطاق النهج عند إعدادها، ستحتاج فقط إلى إنشاء النهج الجديد لحظر عملاء ActiveSync. راجع السياسات المذكورة في الجدول التالي، ثم قم بإجراء الإضافات الموصى بها، أو تأكد من تضمينها بالفعل. يرتبط كل نهج بتعليمات التكوين المقترنة في نهج الوصول إلى الأجهزة [والهوية الشائعة](identity-access-policies.md).

|مستوى الحماية|السياسات|معلومات إضافية|
|---|---|---|
|**نقطة البداية**|[يتطلب MFA عندما تكون مخاطر تسجيل الدخول *متوسطة* أو *عالية*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين Exchange Online في تعيين تطبيقات السحابة|
||[حظر العملاء الذين لا يدعمون المصادقة الحديثة](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|تضمين Exchange Online في تعيين تطبيقات السحابة|
||[تطبيق سياسات حماية بيانات التطبيق](identity-access-policies.md#apply-app-data-protection-policies)|تأكد من Outlook تضمينها في قائمة التطبيقات. تأكد من تحديث النهج لكل نظام أساسي (iOS وAndroid Windows)|
||[يتطلب التطبيقات المعتمدة وحماية التطبيق](identity-access-policies.md#require-approved-apps-and-app-protection)|تضمين Exchange Online في قائمة تطبيقات السحابة|
||[حظر عملاء ActiveSync](#block-activesync-clients)|إضافة هذا النهج الجديد|
|**Enterprise**|[تتطلب MFA عندما تكون مخاطر تسجيل الدخول *منخفضة* أو *متوسطة* أو *عالية*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين Exchange Online في تعيين تطبيقات السحابة|
||[يتطلب أجهزة كمبيوتر وأجهزة *محمولة* متوافقة](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|تضمين Exchange Online في قائمة تطبيقات السحابة|
|**أمان متخصص**|[*طلب* MFA دائما](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين Exchange Online في تعيين تطبيقات السحابة|

## <a name="block-activesync-clients"></a>حظر عملاء ActiveSync

Exchange ActiveSync يمكن استخدامها لمزامنة بيانات المراسلة والتقويم على أجهزة سطح المكتب والأجهزة المحمولة.

بالنسبة للأجهزة المحمولة، يتم حظر عملاء Exchange ActiveSync القادرين على المصادقة الحديثة الذين لا يدعمون نهج حماية تطبيق Intune (أو العملاء المعتمدين غير المحددين في نهج حماية التطبيق Exchange ActiveSync) والعملاء الذين يستخدمون المصادقة الأساسية بالاستناد إلى نهج الوصول الشرطي الذي تم إنشاؤه في يتطلب التطبيقات المعتمدة وحماية [التطبيق](identity-access-policies.md#require-approved-apps-and-app-protection).

لحظر Exchange ActiveSync باستخدام المصادقة الأساسية على أجهزة أخرى، اتبع الخطوات في حظر [Exchange ActiveSync](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices) على جميع الأجهزة، مما يمنع عملاء Exchange ActiveSync الذين يستخدمون المصادقة الأساسية على الأجهزة غير المحمولة من الاتصال ب Exchange Online.

يمكنك أيضا استخدام سياسات المصادقة [لتعطيل المصادقة](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) الأساسية، مما يجبر كل طلبات وصول العميل على استخدام المصادقة الحديثة.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>تقييد الوصول إلى Exchange Online من Outlook على ويب

يمكنك تقييد قدرة المستخدمين على تنزيل المرفقات من Outlook على ويب على أجهزة غير مستخدمة. يمكن للمستخدمين على هذه الأجهزة عرض هذه الملفات وتحريرها باستخدام Office Online دون تسريب الملفات وتخزينها على الجهاز. يمكنك أيضا منع المستخدمين من رؤية المرفقات على جهاز غير إدارة.

فيما يلي الخطوات:

1. [الاتصال إلى جلسة Exchange Online Remote PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. إذا لم يكن لديك نهج علبة بريد OWA بالفعل، فنشئ واحدا باستخدام [الأمر cmdlet New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy) .
3. إذا كنت تريد السماح بعرض المرفقات دون تنزيل، فاستخدم هذا الأمر:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. إذا كنت تريد حظر المرفقات، فاستخدم هذا الأمر:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. في مدخل Azure، أنشئ نهج وصول شرطي جديد باستخدام هذه الإعدادات:

   **الواجبات** \> **المستخدمون والمجموعات**: حدد المستخدمين والمجموعات المناسبة لتضمينها واستبعادها.

   **الواجبات** \> **تطبيقات السحابة أو إجراءاتها** \> **تطبيقات السحابة** \> **تضمين** \> **تحديد التطبيقات**: **حدد Office 365 Exchange Online**

   **عناصر تحكم** \> Access **جلسة** العمل: **حدد استخدام القيود المفروضة على التطبيق**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>يتطلب أن تستخدم أجهزة iOS وAndroid Outlook

لضمان إمكانية وصول مستخدمي أجهزة iOS وAndroid إلى محتوى العمل أو المدرسة فقط باستخدام Outlook لنظامي التشغيل iOS وAndroid، تحتاج إلى نهج الوصول الشرطي الذي يستهدف هؤلاء المستخدمين المحتملين.

راجع الخطوات اللازمة لتكوين هذا النهج في إدارة الوصول إلى التعاون في المراسلة باستخدام [Outlook لنظامي التشغيل iOS وAndroid](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>إعداد تشفير الرسائل

باستخدام إمكانيات تشفير الرسائل من Office 365 (OME) الجديدة، التي تستفيد من ميزات الحماية في Azure Information Protection، يمكن لمنظمتك مشاركة البريد الإلكتروني المحمي بسهولة مع أي شخص على أي جهاز. يمكن للمستخدمين إرسال رسائل محمية وتلقيها مع مؤسسات أخرى Microsoft 365 وغير العملاء باستخدام Outlook.com وGmail وخدمات البريد الإلكتروني الأخرى.

لمزيد من المعلومات، راجع إعداد [قدرات تشفير الرسائل من Office 365 الجديدة](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>الخطوات التالية

![الخطوة 4: سياسات Microsoft 365 السحابية.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

تكوين سياسات الوصول الشرطي ل:

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
