---
title: مخطط الأمان Microsoft 365 - أهم الأولويات
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 08/20/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
ms.assetid: 28c86a1c-e4dd-4aad-a2a6-c768a21cb352
description: أهم التوصيات من فريق الأمان عبر الإنترنت في Microsoft لتنفيذ قدرات الأمان لحماية بيئة Microsoft 365 الخاصة بك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b39edc8adbe16d7f085ca9fec9f30d45f484838
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974246"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>مخطط الأمان - أهم الأولويات لأول 30 يوما و90 يوما وما بعدها

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

تتضمن هذه المقالة أهم التوصيات من فريق الأمان عبر الإنترنت في Microsoft لتنفيذ قدرات الأمان لحماية بيئة Microsoft 365 الخاصة بك. تم تكييف هذه المقالة من جلسة عمل Microsoft Ignite — [Microsoft 365 آمنة مثل محترف الأمان عبر الإنترنت: أهم الأولويات لأول 30 يوما و90 يوما وما بعدها](https://www.youtube.com/watch?v=luignzNyR-o). تم تطوير هذه الجلسة وتقديمها من قبل Mark Simos و Matt Kemelhar، مهندسي الأمان السيبراني للمؤسسات.

في هذه المقالة:

- [نتائج المخطط](security-roadmap.md#Roadmap)
- [30 يوما — مكسب سريع قوي](security-roadmap.md#Thirdaydays)
- [90 يوما — حماية محسنة](security-roadmap.md#Ninetydays)
- [وراء](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>نتائج المخطط
<a name="Roadmap"> </a>

يتم تنظيم توصيات المخطط هذه عبر ثلاث مراحل بترتيب منطقي مع الأهداف التالية.

|الإطار الزمني|نتائج|
|---|---|
|30 يوماً|التكوين السريع: <ul><li>الحماية الأساسية للمسؤول.</li><li>التسجيل والتحليلات.</li><li>الحماية الأساسية للهوية.</li></ul> <p> تكوين المستأجر. <p> إعداد أصحاب المصلحة.|
|90 يوما|الحماية المتقدمة: <ul><li>حسابات المسؤول.</li><li>البيانات وحسابات المستخدمين.</li></ul> <p> الرؤية في التوافق، والتهديدات، واحتياجات المستخدم. <p> تكييف وتنفيذ السياسات والحماية الافتراضية.|
|وراء|ضبط وتحسين السياسات وعناصر التحكم الرئيسية. <p> توسيع نطاق الحماية لتشمل التبعيات المحلية. <p> التكامل مع العمليات التجارية والأمنية (القانونية، والتهديدات الداخلية، وما إلى ذلك).|

## <a name="30-days--powerful-quick-wins"></a>30 يوما — مكسب سريع قوي
<a name="Thirdaydays"> </a>

يمكن إنجاز هذه المهام بسرعة ولها تأثير منخفض على المستخدمين.

|منطقه|المهام|
|---|---|
|إدارة الأمان|<ul><li>تحقق من درجة الأمان ودون درجاتك الحالية (<https://security.microsoft.com/securescore>).</li><li>تشغيل تسجيل التدقيق Office 365. راجع [البحث في سجل التدقيق](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[تكوين Microsoft 365 لزيادة الأمان](tenant-wide-setup-for-increased-security.md).</li><li>راجع لوحات المعلومات والتقارير بانتظام في مدخل Microsoft 365 Defender و Defender for Cloud Apps.</li></ul>|
|الحماية من التهديدات|[الاتصال Microsoft 365 إلى Microsoft Defender for Cloud Apps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) لبدء المراقبة باستخدام نهج الكشف عن التهديدات الافتراضية للسلوكيات الشاذة. يستغرق إنشاء خط أساسي للكشف عن الشذوذ سبعة أيام. <p>  تنفيذ الحماية لحسابات المسؤول:<ul><li>استخدام حسابات المسؤول المخصصة لنشاط المسؤول.</li><li>فرض المصادقة متعددة العوامل (MFA) لحسابات المسؤول.</li><li>استخدام [جهاز Windows آمن للغاية](/windows-hardware/design/device-experiences/oem-highly-secure) لنشاط المسؤول.</li></ul>|
|إدارة الهوية والوصول|<ul><li>[تمكين Azure Active Directory Identity Protection](/azure/active-directory/active-directory-identityprotection-enable).</li><li>بالنسبة لبيئات الهوية المتحدة، قم بفرض أمان الحساب (طول كلمة المرور والعمر والتعقيد وما إلى ذلك).</li></ul>|
|حماية المعلومات|مراجعة مثال توصيات حماية المعلومات. تتطلب حماية المعلومات التنسيق عبر مؤسستك. ابدأ باستخدام هذه الموارد:<ul><li>[Office 365 حماية البيانات القانون العام لحماية البيانات (GDPR)](/compliance/regulatory/gdpr)</li><li>[تكوين Teams بثلاثة مستويات من الحماية](../../solutions/configure-teams-three-tiers-protection.md) (بما في ذلك المشاركة والتصنيف ومنع فقدان بيانات Microsoft Purview وAzure حماية البيانات)</li></ul>|

## <a name="90-days--enhanced-protections"></a>90 يوما — حماية محسنة
<a name="Ninetydays"> </a>

تستغرق هذه المهام وقتا أطول قليلا للتخطيط والتنفيذ ولكنها تزيد بشكل كبير من وضع الأمان الخاص بك.

|منطقه|المهمه|
|---|---|
|إدارة الأمان|<ul><li>تحقق من درجة الأمان للإجراءات الموصى بها للبيئة الخاصة بك (<https://security.microsoft.com/securescore>).</li><li>استمر في مراجعة لوحات المعلومات والتقارير بانتظام في مدخل Microsoft 365 Defender و Defender for Cloud Apps وأدوات SIEM.</li><li>ابحث عن تحديثات البرامج ونفذها.</li><li>إجراء عمليات محاكاة الهجوم للتصيد الاحتيالي الرمح، ورش كلمة المرور، والهجمات بكلمة مرور القوة الغاشمة باستخدام [تدريب محاكاة الهجوم](attack-simulation-training.md) (مضمن مع [Office 365 Threat Intelligence](office-365-ti.md).</li><li>ابحث عن مشاركة المخاطر من خلال مراجعة التقارير المضمنة في Defender for Cloud Apps (على علامة التبويب "التحقيق").</li><li>تحقق من [Compliance Manager](../../compliance/compliance-manager.md) لمراجعة حالة اللوائح التي تنطبق على مؤسستك (مثل GDPR، NIST 800-171).</li></ul>|
|الحماية من التهديدات|تنفيذ الحماية المحسنة لحسابات المسؤولين: <ul><li>تكوين [محطات عمل الوصول المتميز](/security/compass/privileged-access-devices) (PAWs) لنشاط المسؤول.</li><li>تكوين [إدارة الهويات المتميزة Azure AD](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>تكوين أداة إدارة معلومات الأمان والأحداث (SIEM) لجمع بيانات التسجيل من Office 365 و Defender for Cloud Apps وخدمات أخرى، بما في ذلك AD FS. يخزن سجل التدقيق البيانات لمدة 90 يوما فقط. يتيح لك تسجيل هذه البيانات في أداة SIEM تخزين البيانات لفترة أطول.</li></ul>|
|إدارة الهوية والوصول|<ul><li>تمكين المصادقة متعددة العوامل (MFA) وفرضها لجميع المستخدمين.</li><li>تنفيذ مجموعة من [الوصول المشروط والنهج ذات الصلة](microsoft-365-policies-configurations.md).</li></ul>|
|حماية المعلومات| تكييف نهج حماية المعلومات وتنفيذها. تتضمن هذه الموارد أمثلة: <ul><li>[Office 365 حماية البيانات القانون العام لحماية البيانات (GDPR)](/compliance/regulatory/gdpr)</li><li>[تكوين Teams مع ثلاثة مستويات من الحماية](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> استخدم نهج منع فقدان البيانات وأدوات المراقبة في Microsoft Purview للبيانات المخزنة في Microsoft 365 (بدلا من Defender for Cloud Apps). <p> استخدم Defender for Cloud Apps مع Microsoft 365 لميزات التنبيه المتقدمة (بخلاف منع فقدان البيانات).|

## <a name="beyond"></a>وراء
<a name="Beyond"> </a>

هذه هي تدابير الأمان الهامة التي تستند إلى العمل السابق.

|منطقه|المهمه|
|---|---|
|إدارة الأمان|<ul><li>تابع التخطيط للإجراءات التالية باستخدام درجة الأمان (<https://security.microsoft.com/securescore>).</li><li>استمر في مراجعة لوحات المعلومات والتقارير بانتظام في مدخل Microsoft 365 Defender و Defender for Cloud Apps وأدوات SIEM.</li><li>تابع البحث عن تحديثات البرامج وتنفيذها.</li><li>دمج eDiscovery في عمليات الاستجابة القانونية والتهديدات.</li></ul>|
|الحماية من التهديدات|<ul><li>تنفيذ [الوصول المتميز الآمن](/windows-server/identity/securing-privileged-access/securing-privileged-access) (SPA) لمكونات الهوية المحلية (AD، AD FS).</li><li>استخدم Defender for Cloud Apps لمراقبة التهديدات الداخلية.</li><li>اكتشف استخدام Shadow IT SaaS باستخدام Defender for Cloud Apps.</li></ul>|
|إدارة الهوية والوصول|<ul><li>تحسين السياسات والعمليات التشغيلية.</li><li>استخدم Azure AD Identity Protection لتحديد التهديدات الداخلية.</li></ul>|
|حماية المعلومات|تحسين نهج حماية المعلومات: <ul><li>Microsoft 365 وصف الحساسية Office 365 والوقاية من فقدان البيانات (DLP) أو Azure حماية البيانات.</li><li>سياسات وتنبيهات Defender for Cloud Apps.</li></ul>|

راجع أيضا: [كيفية التخفيف من الهجمات الإلكترونية السريعة مثل Petya وWannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
