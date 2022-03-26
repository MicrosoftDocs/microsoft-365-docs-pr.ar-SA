---
title: Microsoft 365 خارطة طريق الأمان - أهم الأولويات
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
description: أهم التوصيات الواردة من فريق الأمان عبر الإنترنت في Microsoft لتطبيق قدرات الأمان لحماية بيئة Microsoft 365 الخاصة بك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9edfda495e1359ac5af74f86f65d33661a2f7059
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63566536"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>خارطة طريق الأمان - أهم الأولويات لأول 30 يوما أو 90 يوما أو أكثر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


تتضمن هذه المقالة أهم التوصيات الواردة من فريق الأمان الإلكتروني في Microsoft لتطبيق قدرات الأمان لحماية بيئة Microsoft 365 الخاصة بك. تم تكييف هذه المقالة من جلسة عمل Microsoft Ignite — تأمين Microsoft 365 مثل أحد محترفي الأمان الإلكتروني: أهم الأولويات لأول [30 يوما أو 90](https://www.youtube.com/watch?v=luignzNyR-o) يوما أو أكثر. تم تطوير هذه الجلسة وقدمها كل من مارك سيمز ومات كيملهار، مهندسو الأمان الإلكتروني في Enterprise.

في هذه المقالة:

- [نتائج المخطط](security-roadmap.md#Roadmap)
- [30 يوما — فوز سريع قوي](security-roadmap.md#Thirdaydays)
- [90 يوما — حماية محسنة](security-roadmap.md#Ninetydays)
- [ما بعد](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>نتائج المخطط
<a name="Roadmap"> </a>

يتم تنفيذ توصيات المخطط هذه على ثلاث مراحل بالترتيب المنطقي مع الأهداف التالية.

****

|إطار زمني|النتائج|
|---|---|
|30 يوماً|التكوين السريع: <ul><li>الحماية الأساسية للمسؤول.</li><li>التسجيل والتحليلات.</li><li>الحماية الأساسية للهوية.</li></ul> <p> تكوين المستأجر. <p> إعداد المساهمين.|
|90 يوما|الحماية المتقدمة: <ul><li>حسابات المسؤولين.</li><li>البيانات وحسابات المستخدمين.</li></ul> <p> الرؤية في التوافق، والتهديد، واحتياجات المستخدم. <p> تكييف وتنفيذ سياسات وحماية افتراضية.|
|ما بعد|ضبط السياسات الأساسية و عناصر التحكم وتنقيحها. <p> توسيع نطاق الحماية ليشمل التبعيات في الموقع. <p> التكامل مع العمليات التجارية وعمليات الأمان (القانونية، وتهديدات insider، وما إلى ذلك).|
|

## <a name="30-days--powerful-quick-wins"></a>30 يوما — فوز سريع قوي
<a name="Thirdaydays"> </a>

يمكن تنفيذ هذه المهام بسرعة وتأثيرها المنخفض على المستخدمين.

****

|المنطقة|المهام|
|---|---|
|إدارة الأمان|<ul><li>تحقق من نقاط آمنة ولاحظ نقاطك الحالية (<https://security.microsoft.com/securescore>).</li><li>قم تشغيل تسجيل التدقيق Office 365. راجع [البحث في سجل التدقيق](../../compliance/search-the-audit-log-in-security-and-compliance.md).</li><li>[قم بتكوين Microsoft 365 لزيادة الأمان](tenant-wide-setup-for-increased-security.md).</li><li>راجع لوحات المعلومات والتقارير بشكل منتظم في Microsoft 365 Defender الإلكتروني و Defender for Cloud Apps.</li></ul>|
|الحماية من المخاطر|[الاتصال Microsoft 365 Microsoft Defender لتطبيقات السحابة](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) لبدء المراقبة باستخدام سياسات الكشف عن المخاطر الافتراضية للسلوكيات الشذوذية. يستغرق إنشاء أساس للكشف عن الشذوذ سبعة أيام. <p>  تنفيذ حماية حسابات المسؤولين:<ul><li>استخدم حسابات المسؤول المخصصة لنشاط المسؤول.</li><li>فرض المصادقة متعددة العوامل (MFA) لحسابات المسؤولين.</li><li>استخدم [جهازا آمنا Windows نشاط](/windows-hardware/design/device-experiences/oem-highly-secure) المسؤول.</li></ul>|
|إدارة الهوية والوصول|<ul><li>[تمكين حماية هوية Azure Active Directory](/azure/active-directory/active-directory-identityprotection-enable).</li><li>بالنسبة لبيئات الهوية المتحدة، فرض أمان الحساب (طول كلمة المرور والعمر والتعقيدات وما إلى ذلك).</li></ul>|
|حماية المعلومات|مراجعة مثال على توصيات حماية المعلومات. تتطلب حماية المعلومات التنسيق عبر مؤسستك. بدء استخدام هذه الموارد:<ul><li>[Office 365 حماية المعلومات ل GDPR](/compliance/regulatory/gdpr)</li><li>[تكوين Teams من ثلاثة](../../solutions/configure-teams-three-tiers-protection.md) مستويات من الحماية (بما في ذلك المشاركة والتصنيف ومنع فقدان البيانات وحماية معلومات Azure)</li></ul>|
|

## <a name="90-days--enhanced-protections"></a>90 يوما — حماية محسنة
<a name="Ninetydays"> </a>

تستغرق هذه المهام وقتا أطول قليلا من أجل التخطيط لها وتنفيذها ولكنها تزيد كثيرا من وضعية الأمان.

****

|المنطقة|مهمة|
|---|---|
|إدارة الأمان|<ul><li>تحقق من "نقاط آمنة" للحصول على الإجراءات الموصى بها لبيئة (<https://security.microsoft.com/securescore>).</li><li>تابع مراجعة لوحات المعلومات والتقارير بشكل منتظم في Microsoft 365 Defender الإلكتروني و Defender for Cloud Apps وأدوات SIEM.</li><li>ابحث عن تحديثات البرامج ونفذها.</li><li>قم بإجراء عمليات محاكاة الهجمات لتصيد رسائل التصيد الاحتيالي، واستخدام كلمة المرور، وهجمات القوة الغاشمة باستخدام التدريب على محاكاة [الهجمات (](attack-simulation-training.md)المضمنة مع Office 365 [Threat Intelligence](office-365-ti.md).</li><li>ابحث عن مخاطر المشاركة من خلال مراجعة التقارير المضمنة في Defender for Cloud Apps (على علامة التبويب التحقق).</li><li>تحقق [من إدارة التوافق](../../compliance/compliance-manager.md) لمراجعة حالة اللوائح التي تنطبق على مؤسستك (مثل القانون العام لحماية المعلومات (GDPR) وNIST 800-171).</li></ul>|
|الحماية من المخاطر|تنفيذ حماية محسنة للحسابات الإدارية: <ul><li>تكوين [محطات عمل Access المميزة](/security/compass/privileged-access-devices) (PAWs) لنشاط المسؤول.</li><li>تكوين [Azure AD إدارة الهويات المتميزة](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>قم بتكوين أداة معلومات الأمان وإدارة الأحداث (SIEM) لتجميع بيانات التسجيل من Office 365 و Defender for Cloud Apps وخدمات أخرى، بما في ذلك AD FS. يخزن سجل التدقيق البيانات لمدة 90 يوما فقط. يتيح لك التقاط هذه البيانات في أداة SIEM تخزين البيانات لفترة أطول.</li></ul>|
|إدارة الهوية والوصول|<ul><li>تمكين MFA وفرضها لجميع المستخدمين.</li><li>تنفيذ مجموعة من [الوصول الشرطي والسياسات ذات الصلة](microsoft-365-policies-configurations.md).</li></ul>|
|حماية المعلومات| تكييف سياسات حماية المعلومات وتطبيقها. تتضمن هذه الموارد أمثلة: <ul><li>[Office 365 حماية المعلومات ل GDPR](/compliance/regulatory/gdpr)</li><li>[تكوين Teams من ثلاثة مستويات من الحماية](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> استخدم سياسات منع فقدان البيانات وأدوات المراقبة في Microsoft 365 البيانات المخزنة في Microsoft 365 (بدلا من Defender for Cloud Apps). <p> استخدم Defender for Cloud Apps Microsoft 365 ميزات التنبيه المتقدمة (غير منع فقدان البيانات).|
|

## <a name="beyond"></a>ما بعد
<a name="Beyond"> </a>

هذه هي تدابير أمان هامة يتم بنائها على العمل السابق.

****

|المنطقة|مهمة|
|---|---|
|إدارة الأمان|<ul><li>تابع التخطيط للتصرفات التالية باستخدام نقاط آمنة (<https://security.microsoft.com/securescore>).</li><li>تابع مراجعة لوحات المعلومات والتقارير بشكل منتظم في Microsoft 365 Defender الإلكتروني و Defender for Cloud Apps وأدوات SIEM.</li><li>تابع البحث عن تحديثات البرامج وتطبيقها.</li><li>ادمج eDiscovery في عمليات الاستجابة للتهديدات والقانونية.</li></ul>|
|الحماية من المخاطر|<ul><li>تنفيذ [الوصول الآمن المتميز](/windows-server/identity/securing-privileged-access/securing-privileged-access) (SPA) لمكونات الهوية المحلي (AD، AD FS).</li><li>استخدم Defender for Cloud Apps لمراقبة تهديدات insider.</li><li>اكتشف الظل استخدام SaaS ل IT باستخدام Defender for Cloud Apps.</li></ul>|
|إدارة الهوية والوصول|<ul><li>تحسين السياسات والعمليات التشغيلية.</li><li>استخدم Azure AD Identity Protection لتحديد تهديدات insider.</li></ul>|
|حماية المعلومات|تحسين سياسات حماية المعلومات: <ul><li>Microsoft 365 أو Office 365 الحساسية ومنع فقدان البيانات (DLP) أو Azure Information Protection.</li><li>تنبيهات ونهج Defender for Cloud Apps.</li></ul>|
|

راجع أيضا: [كيفية الحد من الهجمات الإلكترونية السريعة مثل Petya وWannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/).
