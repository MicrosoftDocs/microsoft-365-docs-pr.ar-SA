---
title: الترحيل من خدمة حماية تابعة لجهة خارجية إلى Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: تعرف على الطريقة الصحيحة للتنقل من خدمات الحماية أو الأجهزة الأخرى مثل Google Postini أو Barracuda Spam و Virus Firewall أو Cisco IronPort Microsoft Defender لـ Office 365 الحماية.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2f67135e2b8a3700a2fb6a6e24fc4f66696db2e3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098703"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>الترحيل من خدمة حماية أو جهاز تابع لجهة خارجية إلى Microsoft Defender لـ Office 365

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)

إذا كان لديك بالفعل خدمة حماية أو جهاز موجود تابع لجهة خارجية يقع أمام Microsoft 365، يمكنك استخدام هذا الدليل بترحيل حمايتك إلى Microsoft Defender لـ Office 365 للحصول على فوائد تجربة إدارة موحدة، وتكلفة محتملة أقل (باستخدام المنتجات التي تدفع ثمنها بالفعل)، ومنتج مكتمل مع أمان متكامل  حمايه. لمزيد من المعلومات، راجع [Microsoft Defender لـ Office 365](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

يوفر هذا الدليل خطوات محددة وقابلة للتنفيذ لل ترحيلك، ويفترض الحقائق التالية:

- لديك بالفعل علب بريد Microsoft 365، ولكنك تستخدم حاليا خدمة أو جهازا تابعا لجهة خارجية لحماية البريد الإلكتروني. يتدفق البريد من الإنترنت عبر خدمة الحماية قبل التسليم إلى مؤسستك Microsoft 365، والحماية Microsoft 365 منخفضة قدر الإمكان (لا يتم إيقاف تشغيلها تماما؛ على سبيل المثال، يتم دائما فرض الحماية من البرامج الضارة).

  :::image type="content" source="../../media/mdo-migration-before.png" alt-text="يتدفق البريد من الإنترنت عبر خدمة الحماية أو الجهاز التابع لجهة خارجية قبل التسليم إلى Microsoft 365" lightbox="../../media/mdo-migration-before.png":::

- أنت خارج مرحلة التحقيق والنظر للحماية من قبل Defender لـ Office 365. إذا كنت بحاجة إلى تقييم Defender لـ Office 365 لتحديد ما إذا كان مناسبا لمؤسستك، نوصيك بالنظر في الخيارات الموضحة في [Try Microsoft Defender لـ Office 365](try-microsoft-defender-for-office-365.md).

- لقد اشتريت بالفعل تراخيص Defender لـ Office 365.

- تحتاج إلى إيقاف خدمة الحماية الحالية التابعة لجهة خارجية، مما يعني أنك ستحتاج في نهاية المطاف إلى توجيه سجلات MX لمجالات البريد الإلكتروني إلى Microsoft 365. عند الانتهاء، سيتدفق البريد من الإنترنت مباشرة إلى Microsoft 365 وستتم حمايته بشكل حصري بواسطة Exchange Online Protection (EOP) Defender لـ Office 365.

  :::image type="content" source="../../media/mdo-migration-after.png" alt-text="يتدفق البريد من الإنترنت إلى Microsoft 365" lightbox="../../media/mdo-migration-after.png":::

يعد القضاء على خدمة الحماية الحالية لصالح Defender لـ Office 365 خطوة كبيرة لا يجب أن تأخذها بخفة، ولا يجب عليك التسرع في إجراء التغيير. ستساعدك الإرشادات الواردة في دليل الترحيل هذا على نقل حمايتك بطريقة منظم مع الحد الأدنى من التعطيل للمستخدمين.

يتم توضيح خطوات الترحيل عالية المستوى جدا في الرسم التخطيطي التالي. يتم سرد الخطوات الفعلية في المقطع [المسمى عملية الترحيل](#the-migration-process) لاحقا في هذه المقالة.

:::image type="content" source="../../media/mdo-migration-overview.png" alt-text="عملية الترحيل من حل أو جهاز حماية تابع لجهة خارجية إلى Defender لـ Office 365" lightbox="../../media/mdo-migration-overview.png":::

## <a name="why-use-the-steps-in-this-guide"></a>لماذا تستخدم الخطوات الواردة في هذا الدليل؟

في صناعة تكنولوجيا المعلومات، تكون المفاجآت سيئة بشكل عام. سيؤدي ببساطة عكس سجلات MX للإشارة إلى Microsoft 365 دون اختبار مسبق ومدروس إلى حدوث العديد من المفاجآت. على سبيل المثال:

- من المحتمل أن تكون أنت أو المهام السابقة قد قضيت الكثير من الوقت والجهد في تخصيص خدمة الحماية الحالية لتسليم البريد الأمثل (بمعنى آخر، حظر ما يجب حظره، والسماح بما يجب السماح به). من المؤكد تقريبا أنه لا يلزم كل تخصيص في خدمة الحماية الحالية في Defender لـ Office 365. من الممكن جدا أيضا أن يقدم Defender لـ Office 365 مشاكل جديدة (السماح أو الكتل) لم تحدث أو لم تكن مطلوبة في خدمة الحماية الحالية.
- يحتاج مكتب المساعدة وموظفي الأمان إلى معرفة ما يجب فعله في Defender لـ Office 365. على سبيل المثال، إذا اشتكى مستخدم من رسالة مفقودة، فهل يعرف مكتب المساعدة مكانها أو كيفية البحث عنها؟ من المحتمل أن يكونوا على دراية بالأدوات الموجودة في خدمة الحماية الحالية، ولكن ماذا عن الأدوات الموجودة في Defender لـ Office 365؟

في المقابل، إذا اتبعت الخطوات الواردة في دليل الترحيل هذا، فستحصل على الفوائد الملموسة التالية لل ترحيلك:

- الحد الأدنى من التعطيل للمستخدمين.
- البيانات الموضوعية من Defender لـ Office 365 التي يمكنك استخدامها أثناء الإبلاغ عن تقدم الترحيل إلى الإدارة ونجاحه.
- المشاركة المبكرة والتعليمات لمكتب المساعدة وموظفي الأمان.

كلما تعرفت أكثر على كيفية تأثير Defender لـ Office 365 على مؤسستك، كان الانتقال أفضل للمستخدمين وموظفي مكتب المساعدة وموظفي الأمان والإدارة.

يوفر لك دليل الترحيل هذا خطة "لتشغيل الطلب" تدريجيا حتى تتمكن من مراقبة واختبار كيفية تأثير Defender لـ Office 365 على المستخدمين والبريد الإلكتروني الخاص بهم حتى تتمكن من التفاعل بسرعة مع أي مشكلات تواجهها.

## <a name="the-migration-process"></a>عملية الترحيل

يمكن تقسيم عملية الترحيل من خدمة حماية تابعة لجهة خارجية إلى Defender لـ Office 365 إلى ثلاث مراحل كما هو موضح في الجدول التالي:

:::image type="content" source="../../media/phase-diagrams/migration-phases.png" alt-text="عملية الترحيل إلى Defender لـ Office 365" lightbox="../../media/phase-diagrams/migration-phases.png":::

|المرحله|الوصف|
|---|---|
|[التحضير لل ترحيلك](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[جرد الإعدادات في خدمة الحماية الموجودة](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[تحقق من تكوين الحماية الموجود في Microsoft 365](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[التحقق من تكوين توجيه البريد](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[نقل الميزات التي تقوم بتعديل الرسائل إلى Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[تعريف البريد العشوائي وتجارب المستخدم المجمعة](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[تحديد حسابات الأولوية وتعيينها](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[إعداد Defender لـ Office 365](migrate-to-defender-for-office-365-setup.md)|<ol><li>[إنشاء مجموعات توزيع للمستخدمين التجريبيين](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[تكوين إرسال المستخدم لتقارير رسائل المستخدم](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[الاحتفاظ بقاعدة تدفق البريد SCL=-1 أو إنشاؤها](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[تكوين التصفية المحسنة للموصلات](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[إنشاء نهج حماية تجريبية](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[إلحاق Defender لـ Office 365](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[بدء إلحاق Teams الأمان](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(اختياري) إعفاء مستخدمي الإصدار التجريبي من التصفية حسب خدمة الحماية الموجودة](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[ضبط التحليل الذكي للانتحال](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[ضبط حماية الانتحال وذكاء علبة البريد](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[استخدام البيانات من عمليات إرسال المستخدم لقياسها وضبطها](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(اختياري) إضافة المزيد من المستخدمين إلى الإصدار التجريبي الخاص بك والتكرار](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[توسيع حماية Microsoft 365 لكافة المستخدمين وإيقاف تشغيل قاعدة تدفق البريد SCL=-1](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[تبديل سجلات MX](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>الخطوة التالية

- تابع إلى [المرحلة 1: التحضير](migrate-to-defender-for-office-365-prepare.md).
