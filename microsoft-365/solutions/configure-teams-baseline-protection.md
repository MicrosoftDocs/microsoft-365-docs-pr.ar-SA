---
title: تكوين الفرق باستخدام حماية الأساس
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkTEAMS
- admindeeplinkSPO
recommendations: false
description: تعرف على كيفية نشر الفرق ذات مستوى أساسي من الحماية.
ms.openlocfilehash: 21fe46a9df9b67c41ff2c0a21fbbe175295e1fdf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567853"
---
# <a name="configure-teams-with-baseline-protection"></a>تكوين الفرق باستخدام حماية الأساس

في هذه المقالة، نطلع على كيفية نشر الفرق ذات مستوى أساسي من الحماية. يسمح هذا المستوى للمستخدمين بمجموعة واسعة من الخيارات للتعاون مع تحسين إدارة الأذونات وتوفير حماية أساسية من االتعاون. تتضمن الحماية الموصى بها لهذا المستوى سياسات الوصول إلى الأجهزة والهوية والحماية من البرامج الضارة. بالإضافة إلى ذلك، يمكنك تطبيق سياسات الوصول الشرطي وحماية فقدان البيانات حسب الحاجة.

## <a name="initial-protections"></a>الحماية الأولية

كخطوة أولى، نوصي بتكوين الهوية الأساسية ونهج الوصول إلى الأجهزة. راجع [توصيات النهج لتأمين Teams الدردشات والمجموعات والملفات](../security/office-365-security/teams-access-policies.md) للحصول على التفاصيل.

نوصي أيضا ب تشغيل Basic Defender Office 365 الحماية من البرامج الضارة في المستندات والمرفقات والربط. نوصيك ب تشغيل كل خيار من الخيارات في الجدول التالي.

|الخيار|معلومات|
|:------|:-----------|
|خزينة مرفقات SPO OneDrive Teams|[خزينة المرفقات](../security/office-365-security/safe-attachments.md) <p> [Defender Office 365 - SharePoint OneDrive و Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md)|
|أمان المستندات|[خزينة المستندات في Microsoft Defender Office 365](../security/office-365-security/safe-docs.md)|
|خزينة ارتباطات Teams|[Office 365 خزينة الارتباطات في Teams](../security/office-365-security/safe-links.md) <p> [الارتباطات الآمنة](../security/office-365-security/safe-links.md)|

## <a name="teams-guest-sharing"></a>Teams مشاركة الضيوف

في كل من المستويات، لدينا خيار المشاركة مع أشخاص من خارج مؤسستك. بالنسبة للمستويات الحساسة والحساسة للغاية، سيكون لدينا خيار إيقاف تشغيل مشاركة الضيف على مستوى الفريق باستخدام تسميات الحساسية. ولكن يجب تشغيل إعداد مشاركة الضيف على مستوى المؤسسة لكي تعمل مشاركة الضيف على الإطلاق في Teams.

![لقطة شاشة Teams تبديل وصول الضيف.](../media/teams-guest-access-toggle-on.png)

لتعيين إعدادات Teams وصول الضيف

1. سجل دخولك إلى مركز مسؤولي Microsoft 365 في [https://admin.microsoft.com](https://admin.microsoft.com).
2. في التنقل الأيسر، انقر فوق **إظهار الكل**.
3. ضمن **مراكز الإدارة،** **انقر فوق** Teams.
4. في مركز Teams، في التنقل الأيسر، **قم بتوسيع** >  الإعدادات على مستوى <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**المؤسسةاستغتر الوصول**</a>.
5. تأكد من **تعيين** السماح بالوصول Teams الضيف إلى **"تم".**
6. قم بإجراء أي تغييرات تريدها على إعدادات الضيف الإضافية، ثم انقر فوق **حفظ**.

> [!NOTE]
> قد يستغرق الأمر ما يصل إلى 24 ساعة حتى يصبح إعداد Teams نشطا بعد تشغيل هذا الإعداد.

يتم تشغيل مشاركة الضيف بشكل افتراضي لمجموعات Office 365 و SharePoint، ولكن إذا قمت مسبقا بتغيير أي من إعدادات مشاركة الضيوف لمنظمتك، نوصي بمراجعة التعاون مع الضيوف في فريق لضمان توفر مشاركة الضيوف في Teams.[](./collaborate-as-team.md)

## <a name="site-and-file-sharing"></a>مشاركة الموقع والملفات

لتقليل مخاطر مشاركة الملفات أو المجلدات عن طريق الخطأ مع أشخاص من خارج مؤسستك، نوصي بتغيير ارتباط المشاركة الافتراضي SharePoint إلى الأشخاص في *مؤسستك فقط*. (إذا كان المستخدمون بحاجة إلى المشاركة خارجيا، وقد قمت بتمكين مشاركة الضيف، يمكنهم تغيير نوع الارتباط عند المشاركة.)

لتغيير ارتباط المشاركة الافتراضي

1. افتح مركز SharePoint، ضمن **سياسات**، حدد <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**مشاركة**</a>.
1. ضمن **ارتباطات الملفات والمجلدات**، حدد **الأشخاص فقط في مؤسستك**.
1. حدد **حفظ**.

للحصول على أفضل تجربة لمشاركة الضيوف، نوصي أيضا بتمكين SharePoint OneDrive مع [Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview).

## <a name="create-a-team"></a>إنشاء فريق

يتم إجراء تكوين إضافي لمستوى الحماية الأساسي في موقع SharePoint المقترن بفريق. [إنشاء فريق عام أو خاص](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b) قبل المتابعة إلى المقطع التالي.

## <a name="site-sharing-settings"></a>إعدادات مشاركة الموقع

بشكل افتراضي، يمكن لأعضاء موقع SharePoint دعوة الآخرين إلى الموقع. عندما يكون الموقع جزءا من فريق، يتم تضمين أعضاء الفريق كأعضاء الموقع. ومع ذلك، لا يمكن للأشخاص الذين تم إضافتهم مباشرة إلى الموقع الوصول إلى باقي أعضاء الفريق. لهذا السبب، نوصي بإدارة الأذونات حصريا من خلال الفريق.

للمساعدة في إدارة الأذونات، نوصي بتكوين الموقع المقترن للسماح فقط للملاك بمشاركة الموقع بنفسه. يعمل هذا على تبسيط إدارة الأذونات ويساعد على منع وصول الأشخاص الذين ليس لهم معرفة مالك الفريق. القيام بذلك لكل فريق يتطلب حماية الأساس.

لتحديث إعدادات مشاركة الموقع
1. في شريط الأدوات للفريق، انقر فوق **ملفات**.
2. انقر **فوق فتح في SharePoint**.
3. في شريط الأدوات الخاص SharePoint، انقر فوق أيقونة الإعدادات، ثم انقر فوق **أذونات الموقع**.
4. في جزء **أذونات** الموقع، ضمن **مشاركة الموقع**، انقر **فوق تغيير طريقة مشاركة الأعضاء**.
5. ضمن **أذونات المشاركة**، اختر مالكو الموقع وأعضائه، ويمكن للأشخاص الذين يمكنهم تحرير الأذونات مشاركة الملفات والمجلدات، ولكن يمكن لمالكي المواقع فقط مشاركة الموقع، ثم انقر فوق **حفظ**.

## <a name="additional-protections"></a>حماية إضافية

Microsoft 365 أساليب إضافية لتأمين المحتوى. فكر في ما إذا كانت الخيارات التالية ستساعد على تحسين الأمان لمنظمتك.

- يجب أن يوافق الضيوف [على شروط الاستخدام](/azure/active-directory/conditional-access/terms-of-use).
- تكوين نهج [2016 لجلسة العمل](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) للضيوف.
- يمكنك [إنشاء أنواع معلومات حساسة](../compliance/sensitive-information-type-learn-about.md) واستخدام الحماية [من فقدان](../compliance/dlp-learn-about-dlp.md) البيانات لتعيين سياسات حول الوصول إلى المعلومات الحساسة.

## <a name="see-also"></a>انظر أيضاً

[إدارة سياسات الاجتماعات في Teams](/microsoftteams/meeting-policies-in-teams)

[بدء العمل مع إدارة مخاطر insider](../compliance/insider-risk-management-configure.md)