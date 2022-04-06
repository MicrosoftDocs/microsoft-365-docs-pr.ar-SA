---
title: سياسات المستندات الآمنة الموصى بها - Microsoft 365 للمؤسسات | Microsoftova dokumentacija
description: يصف هذه المقالة سياسات توصيات Microsoft حول كيفية SharePoint الوصول إلى الملفات.
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
ms.openlocfilehash: 6effe1ffefaf7faeb90258163c539cdddcec2679
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569986"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>توصيات النهج لتأمين SharePoint والملفات

تصف هذه المقالة كيفية تنفيذ Confiança zero الموصى بها ونهج الوصول إلى الأجهزة والهوية لحماية SharePoint OneDrive for Business. يعتمد هذا الإرشاد على [الهوية المشتركة ونهج الوصول إلى الأجهزة](identity-access-policies.md).

تستند هذه التوصيات إلى ثلاثة مستويات مختلفة من الأمان والحماية لملفات SharePoint التي يمكن تطبيقها بالاستناد إلى مجموعة **احتياجاتك: نقطة** البداية والمؤسسة والأمان **المتخصص**.  يمكنك معرفة المزيد حول مستويات الأمان هذه، وأنظمت تشغيل العميل الموصى بها، المشار إليها بواسطة هذه التوصيات في [النظرة العامة](microsoft-365-policies-configurations.md).

بالإضافة إلى تنفيذ هذا الإرشاد، تأكد من تكوين مواقع SharePoint ذات مقدار الحماية المناسب، بما في ذلك تعيين الأذونات المناسبة للمؤسسة ومحتوى الأمان المتخصص.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>تحديث السياسات الشائعة لتضمين SharePoint OneDrive for Business

لحماية الملفات في SharePoint OneDrive، يوضح الرسم التخطيطي التالي سياسات التحديث التي يجب تحديثها من سياسات الوصول إلى الأجهزة والهوية المشتركة.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="ملخص تحديثات النهج لحماية الوصول إلى SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

إذا قمت SharePoint عند إنشاء السياسات الشائعة، ستحتاج فقط إلى إنشاء سياسات جديدة. بالنسبة إلى سياسات الوصول الشرطي، SharePoint تتضمن OneDrive.

تقوم السياسات الجديدة بتطبيق حماية الجهاز للمؤسسة ومحتوى الأمان المتخصص من خلال تطبيق متطلبات وصول محددة SharePoint المواقع التي تحددها.

يسرد الجدول التالي السياسات التي تحتاج إما إلى مراجعتها وتحديثها أو إنشاء سياسات جديدة SharePoint. ترتبط النهج الشائعة بتعليمات التكوين المقترنة [في مقالة](identity-access-policies.md) سياسات الوصول إلى الأجهزة والهوية الشائعة.

|مستوى الحماية|السياسات|معلومات إضافية|
|---|---|---|
|**نقطة البداية**|[يتطلب MFA عندما تكون مخاطر تسجيل الدخول *متوسطة* أو *عالية*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[حظر العملاء الذين لا يدعمون المصادقة الحديثة](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[تطبيق سياسات حماية بيانات التطبيق](identity-access-policies.md#apply-app-data-protection-policies)|تأكد من تضمين جميع التطبيقات المستحسنة في قائمة التطبيقات. تأكد من تحديث النهج لكل نظام أساسي (iOS وAndroid Windows).|
||[استخدام القيود المفروضة على التطبيق في SharePoint](#use-app-enforced-restrictions-in-sharepoint)|أضف هذا النهج الجديد. هذا يخبر Azure Active Directory (Azure AD) باستخدام الإعدادات المحددة في SharePoint. ينطبق هذا النهج على جميع المستخدمين، ولكنه يؤثر فقط على الوصول إلى المواقع المضمنة في SharePoint الوصول.|
|**Enterprise**|[تتطلب MFA عندما تكون مخاطر تسجيل الدخول *منخفضة* أو *متوسطة* أو *عالية*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيينات تطبيقات السحابة.|
||[يتطلب أجهزة كمبيوتر وأجهزة *محمولة* متوافقة](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|قم بتضمين SharePoint في قائمة تطبيقات السحابة.|
||[SharePoint التحكم بالوصول](#sharepoint-access-control-policies): السماح بالوصول فقط إلى المستعرض إلى مواقع SharePoint معينة من الأجهزة غير التي يتم التحكم فيها.|يمنع ذلك تحرير الملفات وتنزيلها. استخدم PowerShell لتحديد المواقع.|
|**أمان متخصص**|[*طلب* MFA دائما](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تضمين SharePoint في تعيين تطبيقات السحابة.|
||[SharePoint التحكم بالوصول](#use-app-enforced-restrictions-in-sharepoint): حظر الوصول إلى مواقع SharePoint معينة من الأجهزة غير التي يتم التحكم فيها.|استخدم PowerShell لتحديد المواقع.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>استخدام القيود المفروضة على التطبيق في SharePoint

إذا قمت بتنفيذ عناصر تحكم الوصول في SharePoint، يتم إنشاء سياسات الوصول الشرطي في Azure AD لإخبار Azure AD بفرض السياسات التي تقوم بتكوينها في SharePoint. بشكل افتراضي، ينطبق هذا النهج على جميع المستخدمين، ولكنه يؤثر فقط على الوصول إلى المواقع التي تحددها باستخدام PowerShell عند إنشاء عناصر التحكم بالوصول في SharePoint. يمكن أيضا تحديد نطاق النهج لمستخدمين معينين أو مجموعات أو مواقع معينة.

لتكوين هذا النهج، راجع "حظر الوصول إلى مجموعات مواقع SharePoint مواقع OneDrive محددة أو تقييد الوصول إليها" في التحكم في الوصول من الأجهزة غير التي يتم التحكم [فيها](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>SharePoint التحكم بالوصول

توصي Microsoft بحماية المحتوى في SharePoint المواقع باستخدام محتوى أمان خاص للمؤسسات مع عناصر التحكم بالوصول إلى الجهاز. يمكنك القيام بذلك عن طريق إنشاء نهج يحدد مستوى الحماية والمواقع لتطبيق الحماية عليها.

- مواقع المؤسسات: السماح بالوصول إلى المستعرض فقط. يمنع ذلك المستخدمين من تحرير الملفات وتنزيلها.
- مواقع الأمان المتخصصة: حظر الوصول من الأجهزة غير المجهزة.

راجع "حظر الوصول إلى مجموعات مواقع SharePoint مواقع OneDrive محددة أو تقييد الوصول إليها" في التحكم في الوصول من الأجهزة غير [التي يتم التحكم فيها](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>كيفية عمل هذه السياسات معا

من المهم فهم أن أذونات SharePoint تستند عادة إلى حاجة الأعمال للوصول إلى المواقع. يدير مالكو المواقع هذه الأذونات ويمكن أن تكون ديناميكية إلى حد كبير. يضمن SharePoint الوصول إلى الأجهزة الحماية لهذه المواقع، بغض النظر عما إذا تم تعيين مستخدمين إلى مجموعة Azure AD مقترنة بنقطة البداية أو المؤسسة أو حماية الأمان المتخصصة.

يوفر الرسم التوضيحي التالي مثالا حول كيفية SharePoint الوصول إلى الأجهزة لحماية الوصول إلى المواقع للمستخدم.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="مثال حول كيفية حماية SharePoint الوصول إلى الأجهزة للمواقع" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

تم تعيين نهج الوصول الشرطي إلى جيمس نقطة البداية، ولكن يمكن منحه حق الوصول إلى مواقع SharePoint مع حماية أمان خاصة أو خاصة بالمؤسسة.

- إذا كان بارس قد حق الوصول إلى موقع عضو فيه مع حماية أمان خاصة أو مؤسسة باستخدام الكمبيوتر الشخصي الخاص به، يتم منح حق الوصول الخاص به.
- إذا كان جيمس يقوم بالوصول إلى موقع حماية المؤسسة فهو عضو في استخدام هاتفه غير المستخدم، المسموح به لمستخدمي نقاط البداية، سيتلقى حق الوصول فقط إلى موقع المؤسسة من خلال المستعرض بسبب نهج الوصول إلى الجهاز الذي تم تكوينه لهذا الموقع.
- إذا كان بارس قد حق الوصول إلى موقع أمان متخصص وهو عضو في استخدام هاتفه غير الذي لم يتم إدارة هاتفه، سيتم حظره بسبب نهج الوصول الذي تم تكوينه لهذا الموقع. يمكنه الوصول إلى هذا الموقع فقط باستخدام جهاز الكمبيوتر المدار الخاص به.

## <a name="next-step"></a>الخطوة التالية

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="الخطوة 4 - سياسات تطبيقات Microsoft 365 السحابة" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::


تكوين سياسات الوصول الشرطي ل:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
