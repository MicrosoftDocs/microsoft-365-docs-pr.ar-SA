---
title: نهج المستندات الآمنة الموصى بها - Microsoft 365 for enterprise | Microsoft Docs
description: يصف النهج الخاصة بتوصيات Microsoft حول كيفية تأمين الوصول إلى ملف SharePoint.
ms.author: dansimp
author: dansimp
manager: dansimp
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
- m365solution-identitydevice
- m365solution-scenario
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: e0ca69eb4a330c4ebb067d657d0fdef8a4d09d8b
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750001"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>توصيات النهج لتأمين مواقع SharePoint وملفاته

تصف هذه المقالة كيفية تنفيذ نهج الهوية ثقة معدومة والوصول إلى الأجهزة الموصى بها لحماية SharePoint OneDrive for Business. يعتمد هذا التوجيه على [نهج الهوية والوصول إلى الجهاز الشائعة](identity-access-policies.md).

تستند هذه التوصيات إلى ثلاثة مستويات مختلفة من الأمان والحماية لملفات SharePoint التي يمكن تطبيقها استنادا إلى نقاوة احتياجاتك: **نقطة البداية** **والمؤسسة** **والأمان المتخصص**. يمكنك معرفة المزيد حول مستويات الأمان هذه، وأنظمة تشغيل العميل الموصى بها، المشار إليها من خلال هذه التوصيات في [النظرة العامة](microsoft-365-policies-configurations.md).

بالإضافة إلى تنفيذ هذه الإرشادات، تأكد من تكوين مواقع SharePoint بقدر الحماية المناسب، بما في ذلك تعيين الأذونات المناسبة لمحتوى الأمان الخاص بالمؤسسة.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>تحديث النهج الشائعة لتضمين SharePoint و OneDrive for Business

لحماية الملفات في SharePoint وOneDrive، يوضح الرسم التخطيطي التالي النهج التي يجب تحديثها من نهج الوصول إلى الأجهزة والهوية الشائعة.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="ملخص تحديثات النهج لحماية الوصول إلى SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

إذا قمت بتضمين SharePoint عند إنشاء النهج الشائعة، فستحتاج فقط إلى إنشاء النهج الجديدة. بالنسبة إلى نهج الوصول المشروط، يتضمن SharePoint OneDrive.

تطبق النهج الجديدة حماية الجهاز لمحتوى الأمان الخاص بالمؤسسة والمتخصصة من خلال تطبيق متطلبات وصول محددة على مواقع SharePoint التي تحددها.

يسرد الجدول التالي النهج التي تحتاج إلى مراجعتها وتحديثها أو إنشاء نهج جديدة ل SharePoint. ترتبط النهج الشائعة بإرشادات التكوين المقترنة في مقالة [نهج الوصول إلى الأجهزة والهوية الشائعة](identity-access-policies.md) .

|مستوى الحماية|السياسات|معلومات إضافية|
|---|---|---|
|**نقطة البداية**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[حظر العملاء الذين لا يدعمون المصادقة الحديثة](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[تطبيق نهج حماية بيانات APP](identity-access-policies.md#apply-app-data-protection-policies)|تأكد من تضمين جميع التطبيقات المستحسنة في قائمة التطبيقات. تأكد من تحديث النهج لكل نظام أساسي (iOS وAndroid وWindows).|
||[استخدام القيود المفروضة على التطبيق في SharePoint](#use-app-enforced-restrictions-in-sharepoint)|أضف هذا النهج الجديد. وهذا يخبر Azure Active Directory (Azure AD) باستخدام الإعدادات المحددة في SharePoint. ينطبق هذا النهج على كافة المستخدمين، ولكنه يؤثر فقط على الوصول إلى المواقع المضمنة في نهج الوصول إلى SharePoint.|
|**Enterprise**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *منخفضا* أو *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيينات تطبيقات السحابة.|
||[طلب أجهزة كمبيوتر وأجهزة *محمولة متوافقة*](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|تضمين SharePoint في قائمة تطبيقات السحابة.|
||[نهج التحكم في الوصول إلى SharePoint](#sharepoint-access-control-policies): السماح بالوصول إلى مواقع SharePoint معينة من أجهزة غير مدارة فقط.|وهذا يمنع تحرير الملفات وتنزيلها. استخدم PowerShell لتحديد المواقع.|
|**أمان متخصص**|[*طلب المصادقة* متعددة العوامل (MFA) دائما](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[نهج التحكم في الوصول إلى SharePoint](#use-app-enforced-restrictions-in-sharepoint): حظر الوصول إلى مواقع SharePoint معينة من أجهزة غير مدارة.|استخدم PowerShell لتحديد المواقع.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>استخدام القيود المفروضة على التطبيق في SharePoint

إذا قمت بتطبيق عناصر التحكم بالوصول في SharePoint، يتم إنشاء نهج الوصول المشروط في Azure AD لإخبار Azure AD بفرض النهج التي تقوم بتكوينها في SharePoint. ينطبق هذا النهج بشكل افتراضي على جميع المستخدمين، ولكنه يؤثر فقط على الوصول إلى المواقع التي تحددها باستخدام PowerShell عند إنشاء عناصر التحكم بالوصول في SharePoint. يمكن أيضا تحديد نطاق النهج لمستخدمين أو مجموعات أو مواقع معينة.

لتكوين هذا النهج، راجع "حظر الوصول إلى مجموعات مواقع SharePoint أو حسابات OneDrive معينة أو تقييده" في [الوصول إلى Control من الأجهزة غير المدارة](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>نهج التحكم في الوصول إلى SharePoint

توصي Microsoft بحماية المحتوى في مواقع SharePoint باستخدام محتوى أمان المؤسسة والمتخصص باستخدام عناصر التحكم في الوصول إلى الجهاز. يمكنك القيام بذلك عن طريق إنشاء نهج يحدد مستوى الحماية والمواقع التي يجب تطبيق الحماية عليها.

- مواقع المؤسسة: السماح بالوصول إلى المستعرض فقط. يؤدي ذلك إلى منع المستخدمين من تحرير الملفات وتنزيلها.
- مواقع الأمان المتخصصة: حظر الوصول من الأجهزة غير المدارة.

راجع "حظر الوصول إلى مجموعات مواقع SharePoint أو حسابات OneDrive معينة أو تقييده" في [الوصول إلى Control من الأجهزة غير المدارة](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>كيفية عمل هذه النهج معا

من المهم أن نفهم أن أذونات موقع SharePoint تستند عادة إلى حاجة العمل للوصول إلى المواقع. تتم إدارة هذه الأذونات من قبل مالكي المواقع ويمكن أن تكون ديناميكية للغاية. يضمن استخدام نهج الوصول إلى أجهزة SharePoint الحماية لهذه المواقع، بغض النظر عما إذا كان قد تم تعيين المستخدمين إلى مجموعة Azure AD مقترنة بنقطة البداية أو المؤسسة أو حماية الأمان المتخصصة.

يوفر الرسم التوضيحي التالي مثالا على كيفية حماية نهج الوصول إلى أجهزة SharePoint للوصول إلى المواقع لمستخدم.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="مثال على كيفية حماية نهج الوصول إلى أجهزة SharePoint للمواقع" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

لدى جيمس نهج الوصول المشروط المعينة لنقطة البداية، ولكن يمكن منحه حق الوصول إلى مواقع SharePoint مع حماية أمان المؤسسة أو الحماية الأمنية المتخصصة.

- إذا كان جيمس يصل إلى موقع ما فهو عضو في مؤسسة أو حماية أمنية متخصصة باستخدام جهاز الكمبيوتر الخاص به، يتم منحه حق الوصول.
- إذا قام جيمس بالوصول إلى موقع حماية المؤسسة، فهو عضو في استخدام هاتفه غير المدار، والذي يسمح للمستخدمين بنقطة البداية، فسيتلقى حق الوصول إلى موقع المؤسسة فقط من خلال نهج الوصول إلى الجهاز الذي تم تكوينه لهذا الموقع.
- إذا كان جيمس يصل إلى موقع أمان متخصص فهو عضو في استخدام هاتفه غير المدار، فسيتم حظره بسبب نهج الوصول الذي تم تكوينه لهذا الموقع. يمكنه فقط الوصول إلى هذا الموقع باستخدام الكمبيوتر المدار الخاص به.

## <a name="next-step"></a>الخطوة التالية

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="الخطوة 4 - نهج تطبيقات سحابة Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

تكوين نهج الوصول المشروط من أجل:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
