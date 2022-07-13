---
title: نهج البريد الإلكتروني الموصى بها الآمنة - Microsoft 365 for enterprise | Microsoft Docs
description: يصف نهج توصيات Microsoft حول كيفية تطبيق نهج البريد الإلكتروني وتكويناته.
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
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: 1b3afc4988dc5d20a1c6c3e0b1a51c1ef1cf9987
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750155"
---
# <a name="policy-recommendations-for-securing-email"></a>توصيات النهج لتأمين البريد الإلكتروني

تصف هذه المقالة كيفية تنفيذ نهج الهوية والوصول إلى الأجهزة ثقة معدومة الموصى بها لحماية عملاء البريد الإلكتروني والبريد الإلكتروني المؤسسيين الذين يدعمون المصادقة الحديثة والوصول المشروط. يعتمد هذا التوجيه على [نهج الوصول إلى الأجهزة والهوية الشائعة](identity-access-policies.md) ويتضمن أيضا بعض التوصيات الإضافية.

تستند هذه التوصيات إلى ثلاثة مستويات مختلفة من الأمان والحماية التي يمكن تطبيقها بناء على نقاوة احتياجاتك: **نقطة البداية** **والمؤسسة** **والأمان المتخصص**. يمكنك معرفة المزيد حول مستويات الأمان هذه، وأنظمة تشغيل العميل الموصى بها، المشار إليها من قبل هذه التوصيات في [مقدمة نهج الأمان والتكوينات الموصى بها](microsoft-365-policies-configurations.md).

تتطلب هذه التوصيات من المستخدمين استخدام عملاء البريد الإلكتروني الحديثين، بما في ذلك Outlook for iOS وAndroid على الأجهزة المحمولة. يوفر Outlook لنظامي التشغيل iOS وAndroid الدعم لأفضل ميزات Office 365. كما تم تصميم تطبيقات Outlook للأجهزة المحمولة هذه مع إمكانات الأمان التي تدعم استخدام الأجهزة المحمولة وتعمل مع قدرات الأمان السحابية الأخرى من Microsoft. لمزيد من المعلومات، راجع [الأسئلة المتداولة حول Outlook for iOS وAndroid](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>تحديث النهج الشائعة لتضمين البريد الإلكتروني

لحماية البريد الإلكتروني، يوضح الرسم التخطيطي التالي النهج التي يجب تحديثها من نهج الوصول إلى الأجهزة والهوية الشائعة.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="ملخص تحديثات النهج لحماية الوصول إلى Microsoft Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

لاحظ إضافة نهج جديد Exchange Online لحظر عملاء ActiveSync. يفرض هذا استخدام Outlook للأجهزة المحمولة.

إذا قمت بتضمين Exchange Online وOutlook في نطاق النهج عند إعدادهما، فستحتاج فقط إلى إنشاء نهج جديد لحظر عملاء ActiveSync. راجع النهج المدرجة في الجدول التالي وقم بإجراء الإضافات الموصى بها، أو تأكد من تضمينها بالفعل. يرتبط كل نهج بإرشادات التكوين المقترنة في [نهج الوصول إلى الهوية والجهاز الشائعة](identity-access-policies.md).

|مستوى الحماية|السياسات|معلومات إضافية|
|---|---|---|
|**نقطة البداية**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين Exchange Online في تعيين تطبيقات السحابة|
||[حظر العملاء الذين لا يدعمون المصادقة الحديثة](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|تضمين Exchange Online في تعيين تطبيقات السحابة|
||[تطبيق نهج حماية بيانات APP](identity-access-policies.md#apply-app-data-protection-policies)|تأكد من تضمين Outlook في قائمة التطبيقات. تأكد من تحديث النهج لكل نظام أساسي (iOS وAndroid وWindows)|
||[طلب التطبيقات المعتمدة وحماية التطبيقات](identity-access-policies.md#require-approved-apps-and-app-protection)|تضمين Exchange Online في قائمة تطبيقات السحابة|
||[حظر عملاء ActiveSync](#block-activesync-clients)|إضافة هذا النهج الجديد|
|**Enterprise**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *منخفضا* أو *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين Exchange Online في تعيين تطبيقات السحابة|
||[طلب أجهزة كمبيوتر وأجهزة *محمولة متوافقة*](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|تضمين Exchange Online في قائمة تطبيقات السحابة|
|**أمان متخصص**|[*طلب المصادقة* متعددة العوامل (MFA) دائما](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين Exchange Online في تعيين تطبيقات السحابة|

## <a name="block-activesync-clients"></a>حظر عملاء ActiveSync

يمكن استخدام Exchange ActiveSync لمزامنة بيانات المراسلة والتقويم على أجهزة سطح المكتب والأجهزة المحمولة.

بالنسبة إلى الأجهزة المحمولة، يتم حظر عملاء Exchange ActiveSync الحديثة القادرة على المصادقة التي لا تدعم نهج حماية تطبيقات Intune (أو العملاء المدعومين غير المحددين في نهج حماية التطبيقات) وعملاء Exchange ActiveSync الذين يستخدمون المصادقة الأساسية استنادا إلى نهج الوصول المشروط الذي تم إنشاؤه في ["طلب التطبيقات المعتمدة وحماية التطبيقات](identity-access-policies.md#require-approved-apps-and-app-protection)".

لحظر Exchange ActiveSync باستخدام المصادقة الأساسية على أجهزة أخرى، اتبع الخطوات الواردة في [حظر Exchange ActiveSync على جميع الأجهزة](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices)، مما يمنع عملاء Exchange ActiveSync الذين يستخدمون المصادقة الأساسية على الأجهزة غير المحمولة من الاتصال Exchange Online.

يمكنك أيضا استخدام نهج المصادقة [لتعطيل المصادقة الأساسية](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online)، ما يفرض على كافة طلبات وصول العميل استخدام المصادقة الحديثة.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>تقييد الوصول إلى Exchange Online من Outlook على ويب

يمكنك تقييد قدرة المستخدمين على تنزيل المرفقات من Outlook على ويب على أجهزة غير مدارة. يمكن للمستخدمين على هذه الأجهزة عرض هذه الملفات وتحريرها باستخدام Office Online دون تسريب الملفات وتخزينها على الجهاز. يمكنك أيضا حظر المستخدمين من رؤية المرفقات على جهاز غير مدار.

فيما يلي الخطوات:

1. [الاتصال Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. إذا لم يكن لديك بالفعل نهج علبة بريد OWA، قم بإنشاء واحد باستخدام [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy) cmdlet.
3. إذا كنت تريد السماح بعرض المرفقات ولكن بدون تنزيل، فاستخدم هذا الأمر:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. إذا كنت تريد حظر المرفقات، فاستخدم هذا الأمر:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. في مدخل Microsoft Azure، قم بإنشاء نهج وصول مشروط جديد باستخدام هذه الإعدادات:

   **تعيينات** \> **المستخدمون والمجموعات**: حدد المستخدمين والمجموعات المناسبة لتضمينها واستبعادها.

   **تعيينات** \> **تطبيقات أو إجراءات السحابة** \> **تطبيقات السحابة** \> **تشمل** \> **تحديد التطبيقات**: حدد **Office 365 Exchange Online**

   **عناصر التحكم في** \> الوصول **جلسة العمل**: تحديد **القيود المفروضة على استخدام التطبيق**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>مطالبة أجهزة iOS وAndroid باستخدام Outlook

للتأكد من أن مستخدمي أجهزة iOS وAndroid يمكنهم الوصول إلى محتوى العمل أو المؤسسة التعليمية فقط باستخدام Outlook لنظامي التشغيل iOS وAndroid، تحتاج إلى نهج الوصول المشروط الذي يستهدف هؤلاء المستخدمين المحتملين.

راجع الخطوات لتكوين هذا النهج في [إدارة الوصول إلى تعاون المراسلة باستخدام Outlook لنظامي التشغيل iOS وAndroid](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>إعداد تشفير الرسائل

باستخدام تشفير الرسائل في Microsoft Purview، الذي يستفيد من ميزات الحماية في Azure حماية البيانات، يمكن لمؤسستك مشاركة البريد الإلكتروني المحمي بسهولة مع أي شخص على أي جهاز. يمكن للمستخدمين إرسال رسائل محمية وتلقيها مع مؤسسات Microsoft 365 الأخرى بالإضافة إلى غير العملاء الذين يستخدمون Outlook.com وGmail وخدمات البريد الإلكتروني الأخرى.

لمزيد من المعلومات، راجع [إعداد قدرات تشفير رسائل Office 365 جديدة](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>الخطوات التالية

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="نهج تطبيقات سحابة Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

تكوين نهج الوصول المشروط من أجل:

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
