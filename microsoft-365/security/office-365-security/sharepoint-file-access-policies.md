---
title: نهج المستندات الآمنة الموصى بها - Microsoft 365 | المؤسسة Microsoft Docs
description: يصف نهج توصيات Microsoft حول كيفية تأمين الوصول إلى الملفات SharePoint.
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
ms.technology: mdo
ms.openlocfilehash: 3a2a8e5be8fb78824e8670f94a2e087da9538329
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972134"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>توصيات النهج لتأمين مواقع وملفات SharePoint

تصف هذه المقالة كيفية تنفيذ نهج الهوية والوصول إلى الجهاز ثقة معدومة الموصى بها لحماية SharePoint OneDrive for Business. يعتمد هذا التوجيه على [نهج الهوية والوصول إلى الجهاز الشائعة](identity-access-policies.md).

تستند هذه التوصيات إلى ثلاثة مستويات مختلفة من الأمان والحماية لملفات SharePoint التي يمكن تطبيقها بناء على نقاوة احتياجاتك: **نقطة البداية** **والمؤسسة** **والأمان المتخصص**. يمكنك معرفة المزيد حول مستويات الأمان هذه، وأنظمة تشغيل العميل الموصى بها، المشار إليها من خلال هذه التوصيات في [النظرة العامة](microsoft-365-policies-configurations.md).

بالإضافة إلى تنفيذ هذه الإرشادات، تأكد من تكوين مواقع SharePoint بالقدر المناسب من الحماية، بما في ذلك تعيين الأذونات المناسبة لمحتوى الأمان الخاص بالمؤسسة.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>تحديث النهج الشائعة لتضمين SharePoint OneDrive for Business

لحماية الملفات في SharePoint OneDrive، يوضح الرسم التخطيطي التالي النهج التي يجب تحديثها من نهج الوصول إلى الهوية والجهاز الشائعة.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="ملخص تحديثات النهج لحماية الوصول إلى SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

إذا قمت بتضمين SharePoint عند إنشاء النهج الشائعة، فستحتاج فقط إلى إنشاء النهج الجديدة. بالنسبة إلى نهج الوصول المشروط، تتضمن SharePoint OneDrive.

تطبق النهج الجديدة حماية الجهاز لمحتوى أمان المؤسسة والمتخصص من خلال تطبيق متطلبات وصول محددة على مواقع SharePoint التي تحددها.

يسرد الجدول التالي النهج التي تحتاج إلى مراجعتها وتحديثها أو إنشاء نهج جديدة SharePoint. ترتبط النهج الشائعة بإرشادات التكوين المقترنة في مقالة [نهج الوصول إلى الأجهزة والهوية الشائعة](identity-access-policies.md) .

|مستوى الحماية|السياسات|معلومات إضافية|
|---|---|---|
|**نقطة البداية**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[حظر العملاء الذين لا يدعمون المصادقة الحديثة](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[تطبيق نهج حماية بيانات APP](identity-access-policies.md#apply-app-data-protection-policies)|تأكد من تضمين جميع التطبيقات المستحسنة في قائمة التطبيقات. تأكد من تحديث النهج لكل نظام أساسي (iOS وAndroid Windows).|
||[استخدام القيود المفروضة على التطبيق في SharePoint](#use-app-enforced-restrictions-in-sharepoint)|أضف هذا النهج الجديد. وهذا يخبر Azure Active Directory (Azure AD) باستخدام الإعدادات المحددة في SharePoint. ينطبق هذا النهج على كافة المستخدمين، ولكنه يؤثر فقط على الوصول إلى المواقع المضمنة في نهج الوصول SharePoint.|
|**Enterprise**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *منخفضا* أو *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيينات تطبيقات السحابة.|
||[طلب أجهزة كمبيوتر وأجهزة *محمولة متوافقة*](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|تضمين SharePoint في قائمة تطبيقات السحابة.|
||[SharePoint نهج التحكم بالوصول](#sharepoint-access-control-policies): السماح بالوصول إلى مواقع SharePoint معينة من أجهزة غير مدارة فقط.|وهذا يمنع تحرير الملفات وتنزيلها. استخدم PowerShell لتحديد المواقع.|
|**أمان متخصص**|[*طلب المصادقة* متعددة العوامل (MFA) دائما](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[SharePoint نهج التحكم بالوصول](#use-app-enforced-restrictions-in-sharepoint): حظر الوصول إلى مواقع SharePoint معينة من أجهزة غير مدارة.|استخدم PowerShell لتحديد المواقع.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>استخدام القيود المفروضة على التطبيق في SharePoint

إذا قمت بتنفيذ عناصر التحكم بالوصول في SharePoint، يتم إنشاء نهج الوصول المشروط في Azure AD لإخبار Azure AD بفرض النهج التي تقوم بتكوينها في SharePoint. ينطبق هذا النهج بشكل افتراضي على جميع المستخدمين، ولكنه يؤثر فقط على الوصول إلى المواقع التي تحددها باستخدام PowerShell عند إنشاء عناصر التحكم بالوصول في SharePoint. يمكن أيضا تحديد نطاق النهج لمستخدمين أو مجموعات أو مواقع معينة.

لتكوين هذا النهج، راجع "حظر الوصول إلى مجموعات SharePoint مواقع مشتركة معينة أو حسابات OneDrive" أو تقييد الوصول إليها [من أجهزة غير مدارة](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>نهج التحكم في الوصول SharePoint

توصي Microsoft بحماية المحتوى في مواقع SharePoint باستخدام محتوى أمان المؤسسة والمتخصص باستخدام عناصر التحكم في الوصول إلى الجهاز. يمكنك القيام بذلك عن طريق إنشاء نهج يحدد مستوى الحماية والمواقع التي يجب تطبيق الحماية عليها.

- مواقع المؤسسة: السماح بالوصول إلى المستعرض فقط. يؤدي ذلك إلى منع المستخدمين من تحرير الملفات وتنزيلها.
- مواقع الأمان المتخصصة: حظر الوصول من الأجهزة غير المدارة.

راجع "حظر الوصول إلى مجموعات مواقع مشتركة معينة SharePoint أو حسابات OneDrive" أو تقييد [الوصول إليها من الأجهزة غير المدارة](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>كيفية عمل هذه النهج معا

من المهم أن نفهم أن أذونات الموقع SharePoint تستند عادة إلى حاجة العمل للوصول إلى المواقع. تتم إدارة هذه الأذونات من قبل مالكي المواقع ويمكن أن تكون ديناميكية للغاية. يضمن استخدام نهج الوصول إلى الأجهزة SharePoint حماية هذه المواقع، بغض النظر عما إذا كان يتم تعيين المستخدمين إلى مجموعة Azure AD المقترنة بنقطة البداية أو المؤسسة أو حماية الأمان المتخصصة.

يوفر الرسم التوضيحي التالي مثالا على كيفية حماية نهج الوصول إلى الأجهزة SharePoint الوصول إلى المواقع للمستخدم.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="مثال على كيفية حماية نهج الوصول إلى الأجهزة SharePoint المواقع" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

لدى جيمس نهج الوصول المشروط المحددة لنقطة البداية، ولكن يمكن منحه حق الوصول إلى مواقع SharePoint مع حماية أمنية للمؤسسات أو الحماية الأمنية المتخصصة.

- إذا كان جيمس يصل إلى موقع ما فهو عضو في مؤسسة أو حماية أمنية متخصصة باستخدام جهاز الكمبيوتر الخاص به، يتم منحه حق الوصول.
- إذا قام جيمس بالوصول إلى موقع حماية المؤسسة، فهو عضو في استخدام هاتفه غير المدار، والذي يسمح للمستخدمين بنقطة البداية، فسيتلقى حق الوصول إلى موقع المؤسسة فقط من خلال نهج الوصول إلى الجهاز الذي تم تكوينه لهذا الموقع.
- إذا كان جيمس يصل إلى موقع أمان متخصص فهو عضو في استخدام هاتفه غير المدار، فسيتم حظره بسبب نهج الوصول الذي تم تكوينه لهذا الموقع. يمكنه فقط الوصول إلى هذا الموقع باستخدام الكمبيوتر المدار الخاص به.

## <a name="next-step"></a>الخطوة التالية

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="الخطوة 4 - نهج تطبيقات السحابة Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

تكوين نهج الوصول المشروط من أجل:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
