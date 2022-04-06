---
title: الترحيل من خدمة حماية جهة خارجية إلى Microsoft Defender لـ Office 365
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
description: تعرف على الطريقة الصحيحة للترحيل من خدمات الحماية أو الأجهزة الخاصة ب جهة خارجية مثل Google Postini أو جدار الحماية من الفيروسات والبريد العشوائي ل Barracuda أو Cisco IronPort Microsoft Defender لـ Office 365 الحماية.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ba82621e76665ee94d2a182e777ad1d222ef8e56
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477028"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>الترحيل من خدمة حماية أو جهاز جهة خارجية إلى Microsoft Defender لـ Office 365

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)

إذا كان لديك بالفعل خدمة حماية موجودة من جهة خارجية أو جهاز موجود أمام Microsoft 365، يمكنك استخدام هذا الدليل لترحيل حمايتك إلى Microsoft Defender لـ Office 365 للحصول على مزايا تجربة الإدارة المدمجة، والتكلفة المنخفضة المحتملة (باستخدام المنتجات التي تدفع مقابلها بالفعل)، ومنتج بالغ مع أمان متكامل  الحماية. لمزيد من المعلومات، راجع [Microsoft Defender Office](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

يوفر هذا الدليل خطوات محددة قابلة للتنفيذ ل الترحيل، ويفترض الحقائق التالية:

- لديك علب بريد Microsoft 365، ولكنك تستخدم حاليا خدمة أو جهازا من جهة خارجية لحماية البريد الإلكتروني. ينساب البريد من الإنترنت عبر خدمة الحماية قبل التسليم إلى مؤسسة Microsoft 365، والحماية من Microsoft 365 منخفضة قدر الإمكان (لا يتم إيقاف تشغيلها تماما؛ على سبيل المثال، يتم دائما فرض الحماية من البرامج الضارة).

  :::image type="content" source="../../media/mdo-migration-before.png" alt-text="ينساب البريد من الإنترنت عبر خدمة الحماية أو الجهاز الخاص ب جهة خارجية قبل التسليم إلى Microsoft 365" lightbox="../../media/mdo-migration-before.png":::

- أنت خارج مرحلة التحقيق والنظر في الحماية من خلال Defender لـ Office 365. إذا كنت بحاجة إلى تقييم Defender لـ Office 365 لتحديد ما إذا كان ذلك صحيحا لمنظمتك، فإننا ننصحك بأن تفكر [في وضع التقييم](office-365-evaluation.md).

- لقد اشتريت تراخيص Defender لـ Office 365 مسبقا.

- أنت بحاجة إلى إيقاف خدمة الحماية الحالية الخاصة بك، مما يعني أنك ستحتاج في النهاية إلى الإشارة إلى سجلات MX لمجالات بريدك الإلكتروني Microsoft 365. عندما تنجز المهمة، سيتدفق البريد من الإنترنت مباشرة إلى Microsoft 365 وستحميه بشكل حصري Exchange Online Protection (EOP) Defender لـ Office 365.

  :::image type="content" source="../../media/mdo-migration-after.png" alt-text="ينساب البريد من الإنترنت إلى Microsoft 365" lightbox="../../media/mdo-migration-after.png":::

تعد إزالة خدمة الحماية الحالية لصالح Defender لـ Office 365 خطوة كبيرة يجب ألا تتهاون فيها، ولا يجب أن تسرع في إجراء التغيير. ستساعدك الإرشادات في دليل الترحيل هذا على نقل حمايتك بطريقة منظمة بأقل قدر من الانقطاع للمستخدمين.

يتم توضيح خطوات الترحيل عالية المستوى جدا في الرسم التخطيطي التالي. يتم سرد الخطوات الفعلية في المقطع المسمى [عملية الترحيل](#the-migration-process) لاحقا في هذه المقالة.

:::image type="content" source="../../media/mdo-migration-overview.png" alt-text="عملية الترحيل من حل حماية جهة خارجية أو جهاز إلى Defender لـ Office 365" lightbox="../../media/mdo-migration-overview.png":::

## <a name="why-use-the-steps-in-this-guide"></a>لماذا تستخدم الخطوات في هذا الدليل؟

في مجال تكنولوجيا المعلومات، تكون المفاجآت سيئة بشكل عام. ما عليك سوى عكس سجلات MX لتشير إلى Microsoft 365 دون اختبار مسبق ومدروس سينتج عنه الكثير من المفاجآت. على سبيل المثال:

- ربما أمضيت أنت أو من سبقك الكثير من الوقت والجهد في تخصيص خدمة الحماية الحالية للحصول على أفضل تسليم للبريد (بتعبير آخر، حظر ما يجب حظره والسماح بما يجب السماح به). من المؤكد تقريبا أن كل التخصيصات في خدمة الحماية الحالية غير مطلوبة في Defender لـ Office 365. من المحتمل جدا أيضا أن Defender لـ Office 365 مشاكل جديدة (السماح أو الكتل) لم تحدث أو لم تكن مطلوبة في خدمة الحماية الحالية.
- يحتاج موظفو مكتب المساعدة والأمان إلى معرفة ما يجب فعله في Defender لـ Office 365. على سبيل المثال، إذا اشتكى مستخدم من رسالة مفقودة، فهل يعلم مكتب المساعدة مكان البحث عنها أو كيفية البحث عنها؟ من المرجح أن تكون على دراية بالأدوات الموجودة في خدمة الحماية الحالية، ولكن ماذا عن الأدوات الموجودة في Defender لـ Office 365؟

في المقابل، إذا كنت تتبع الخطوات في دليل الترحيل هذا، فسوف تحصل على الفوائد المحتملة التالية ل الترحيل:

- الحد الأدنى من الانقطاع للمستخدمين.
- البيانات الهدف من Defender لـ Office 365 التي يمكنك استخدامها عند تقديم تقرير حول تقدم عملية الترحيل إلى الإدارة والنجاح الذي حققته.
- المشاركة المبكرة والتعليمات الخاصة بعاملين في مكتب المساعدة والأمان.

كلما تعرفت على كيفية تأثير Defender لـ Office 365 على مؤسستك، كان الانتقال أفضل للمستخدمين والعاملين في مكتب المساعدة ومستخدمي الأمان والإدارة.

يوفر لك دليل الترحيل هذا خطة ل "تشغيل الطلب" تدريجيا بحيث يمكنك مراقبة كيفية تأثير Defender لـ Office 365 على المستخدمين والبريد الإلكتروني الخاص بهم واختباره حتى تتمكن من التفاعل بسرعة مع أي مشاكل تواجهها.

## <a name="the-migration-process"></a>عملية الترحيل

يمكن تقسيم عملية عملية ارحل من خدمة حماية جهة خارجية إلى Defender لـ Office 365 إلى ثلاث مراحل كما هو موضح في الجدول التالي:

:::image type="content" source="../../media/phase-diagrams/migration-phases.png" alt-text="عملية عملية عملية إعادة Defender لـ Office 365" lightbox="../../media/phase-diagrams/migration-phases.png":::

|المرحلة|الوصف|
|---|---|
|[التحضير ل الترحيل](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[جرد الإعدادات في خدمة الحماية الحالية](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[تحقق من تكوين الحماية الموجود في Microsoft 365](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[التحقق من تكوين توجيه البريد](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[نقل الميزات التي تقوم بتعديل الرسائل إلى Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[تعريف البريد العشوائي وتجارب المستخدمين المجمعة](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[تحديد حسابات الأولوية وتحديدها](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[إعداد Defender لـ Office 365](migrate-to-defender-for-office-365-setup.md)|<ol><li>[إنشاء مجموعات توزيع لمستخدمي التجربة](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[تكوين إرسال المستخدم لتقارير رسائل المستخدم](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[المحافظة على قاعدة تدفق البريد SCL=-1 أو إنشاؤها](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[تكوين التصفية المحسنة للموصلات](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[إنشاء سياسات حماية تجريبية](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Onboard to Defender لـ Office 365](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[بدء عملية ا متنوأ أمان Teams](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(اختياري) إعفاء مستخدمي التجربة من التصفية حسب خدمة الحماية الحالية](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[ضبط المعلومات المنتحلة](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[ضبط حماية انتحال الشخصية وذكاء علبة البريد](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[استخدام البيانات من إرسالات المستخدمين لقياسها وضبطها](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(اختياري) إضافة المزيد من المستخدمين إلى التجربة والتكرير](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[توسيع Microsoft 365 الحماية لجميع المستخدمين إيقاف تشغيل قاعدة تدفق البريد SCL=-1](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[تبديل سجلات MX](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>الخطوة التالية

- تابع إلى [المرحلة 1: التحضير](migrate-to-defender-for-office-365-prepare.md).
