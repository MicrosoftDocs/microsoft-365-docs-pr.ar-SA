---
title: إعداد Microsoft 365 Business Premium
description: تعرف على كيفية إعداد Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/01/2022
ms.service: o365-administration
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 5b6f187f93e8a135bfb67c78509553d2963b011b
ms.sourcegitcommit: b67385243fb56ad20f2a6f1c40be46f5691c1c2a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705633"
---
# <a name="set-up-microsoft-365-business-premium"></a>إعداد Microsoft 365 Business Premium

لديك العديد من الخيارات لإعداد Microsoft 365 Business Premium. يمكنك:

- [استخدام تجربة إعداد موجهة للإعداد والتكوين الأساسيين](#guided-process-for-basic-setup)
- [العمل مع شريك، مثل موفر حلول الحوسبة السحابية من Microsoft (CSP)](#work-with-a-microsoft-partner)
- [العمل من خلال عملية الإعداد يدويا](#manual-setup-and-configuration)


استخدم هذه المقالة كدليل.

## <a name="guided-process-for-basic-setup"></a>عملية إرشادية للإعداد الأساسي

Microsoft 365 Business Premium عملية إرشادية للإعداد الأساسي. تتضمن المهام الاتصال والمجال المخصص وإضافة المستخدمين وتعيين التراخيص وتثبيت Outlook على الأجهزة المحمولة ومراجعة إعدادات حماية البيانات وتطبيق نهج حماية تطبيق الأجهزة المحمولة. 

لمعرفة كيفية عمل الإعداد الموجه، شاهد الفيديو التالي: <br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

بعد الانتهاء من الإعداد الموجه، هناك خطوات إضافية يجب إكمالها للمساعدة على ضمان إعداد قدرات الأمان والتوافق الخاصة بك وتطبيقها بشكل صحيح. تتضمن هذه الخطوات ما يلي:

- [تأمين أجهزة Windows](m365bp-secure-windows-devices.md)
- [نشر تطبيقات Microsoft 365](../admin/setup/install-applications.md)
- [إعداد قدرات Defender for Business الجديدة وتكوينها](../security/defender-business/mdb-setup-configuration.md)

[تعرف على المزيد حول الاختلافات بين عملية الإعداد الموجهة وصفحة الإعداد](../admin/setup/o365-setup-wizard-and-setup-page.md).

> [!TIP]
> راجع القسم التالي للحصول على مزيد من التفاصيل حول إعداد Microsoft 365 Business Premium.


## <a name="work-with-a-microsoft-partner"></a>العمل مع شريك Microsoft

لدى Microsoft قائمة تتضمن موفري الحلول المخولا لبيع العروض، بما في ذلك Microsoft 365 Business Premium. 

للعثور على موفر حل في منطقتك، عليك اتباع الخطوات التالية:

1. انتقل إلى **صفحة موفري حلول Microsoft** ([https://www.microsoft.com/solution-providers](https://www.microsoft.com/solution-providers)).
 
2. في مربع البحث، قم بتعبئة موقعك وحجم الشركة. 

3. في المربع **البحث عن المنتجات والخدمات والمهارات والصناعات** ، ضع `Microsoft 365`، ثم حدد **الانتقال**.

4. راجع قائمة النتائج. حدد موفرا لمعرفة المزيد حول خبراته والخدمات التي يوفرها.

راجع أيضا [البحث عن شريكك أو البائع](../admin/manage/find-your-partner-or-reseller.md).

## <a name="manual-setup-and-configuration"></a>الإعداد والتكوين اليدوي

إذا كنت تفضل إكمال عملية الإعداد والتكوين يدويا، فاستخدم الجدول التالي كدليل:

| المرحلة  | مهمة  | الموارد لمعرفة المزيد  |
|---------|---------|---------|
| **التخطيط**     | التخطيط لعملية الإعداد والتكوين  | [التخطيط لإعداد Microsoft 365 للأعمال](../admin/setup/plan-your-setup.md)   |
|  | مراجعة المتطلبات | [Microsoft 365 Business Premium المتطلبات](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:overviewtab) |
| **الإعداد الأساسي**     | استخدم مجالا مخصصا مثل `rob@contoso.com` Microsoft 365 | [إضافة مجال إلى Microsoft 365](../admin/setup/add-domain.md) |
|      | إضافة مستخدمين وتعيين تراخيص في Microsoft 365      | [إضافة مستخدمين وتعيين تراخيص في الوقت نفسه](../admin/add-users/add-users.md)        |
|  | تعيين أدوار المسؤولين للمستخدمين الذين سي يؤدون وظائف معينة، مثل: <br/>- إدارة الميزات<br/>- إدارة حسابات المستخدمين<br/>- إدارة الأجهزة<br/>- عرض معلومات الأمان والتوافق في مؤسستك أو إدارتها | [التعرف على أدوار المسؤولين](../admin/add-users/about-admin-roles.md) <br/><br/> [تعيين أدوار المسؤولين](../admin/add-users/assign-admin-roles.md)  |
|  | تثبيت Microsoft 365 Apps (مثل Word Excel PowerPoint والمزيد) | [تثبيت تطبيقات ](../admin/setup/install-applications.md)Office |
| **تأمين مؤسستك** | الرجوع إلى أهم 10 أيام لتأمين اشتراكك في Microsoft 365 |  [أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](../admin/security-and-compliance/secure-your-business-data.md) |
|  | طلب من الجميع استخدام أسلوب تحقق إضافي عند تسجيل الدخول إلى Microsoft 365 | [إعداد المصادقة متعددة العوامل](../admin/security-and-compliance/set-up-multi-factor-authentication.md) | 
| **حماية البريد الإلكتروني والمحتوى** |  إعداد حماية متقدمة من التصيد الاحتيالي للحماية من هجمات التصيد الاحتيالي الضارة المستندة إلى انتحال الشخصية وهجمة التصيد الاحتيالي الأخرى | [حماية بريدك الإلكتروني من هجمات التصيد الاحتيالي](../admin/security-and-compliance/secure-your-business-data.md) |
|   | إعداد مرفقات خزينة لحماية مؤسستك من مرفقات البريد الإلكتروني الضارة | [الحماية من المرفقات والملفات الضارة خزينة المرفقات](../admin/security-and-compliance/secure-your-business-data.md) |
|  | إعداد ارتباطات خزينة للحماية من مواقع الويب الضارة (عناوين URL) في رسائل البريد الإلكتروني Office المستندات | [إعداد ارتباطات خزينة](../admin/security-and-compliance/secure-your-business-data.md) |
|  | إعداد سياسات منع فقدان البيانات لحماية المعلومات الحساسة من المشاركة | [إعداد ميزات التوافق](../admin/security-and-compliance/set-up-compliance.md) |
| **إدارة الأجهزة وحمايتها** | تأمين أجهزة Windows مؤسستك | [تأمين Windows آمنة](m365bp-secure-windows-devices.md) <br/><br/>[تعيين إعدادات حماية التطبيقات أو تحريرها Windows 10 الأجهزة](../admin/devices/protection-settings-for-windows-10-devices.md) |
|   | تأمين Microsoft 365 على الأجهزة المحمولة | [تعيين إعدادات حماية التطبيق لأجهزة Android أو iOS](../admin/devices/app-protection-settings-for-android-and-ios.md) |
|  | إعداد Microsoft Defender for Business (عند توفره للمستأجر) | [نظرة عامة حول Microsoft Defender for Business](../security/defender-business/mdb-overview.md)<br/><br/>[استخدام المعالج لإعداد Defender for Business](../security/defender-business/mdb-use-wizard.md) |
| **تخزين الملفات ومحتوى التهجر** | إعداد تخزين الملفات وكيفية عمل المشاركة لمنظمتك | [إعداد تخزين الملفات ومشاركتها في Microsoft 365](../admin/setup/set-up-file-storage-and-sharing.md) |
| | استيراد البريد الإلكتروني وجهات الاتصال أو ترحيلها | [ترحيل البريد الإلكتروني وجهات الاتصال إلى Microsoft 365](../admin/setup/migrate-email-and-contacts-admin.md) |
|  | نقل ملفات الشركة التي يحتاج الجميع إلى الوصول إليها SharePoint (يستبدل SharePoint عادة استخدام مشاركة ملف أو محرك أقراص شبكة) | [نقل الملفات إلى SharePoint](../admin/setup/files-to-sharepoint.md) |
|  | نقل ملفات العمل الموجودة، مثل ملفات العمل الشخصية أو ملفات العمل الحساسة، إلى OneDrive | [نقل الملفات إلى OneDrive](../admin/setup/files-to-onedrive.md) |
| **تدريب المسؤولين وفريق الأمان** | تعرف على كيفية استخدام مركز الإدارة | [نظرة عامة على مركز مسؤولي Microsoft 365](../admin/admin-overview/admin-center-overview.md) |
|  | استخدام مكتبة الفيديو التدريبية المجانية لمسؤولي Microsoft 365 | [مكتبة فيديو تدريب المسؤول](../admin/admin-video-library.yml)  |
|  | تعرف على كيفية استخدام مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | [بدء استخدام مدخل Microsoft 365 Defender](../security/defender-business/mdb-get-started.md) |

> [!TIP]
> هل تحتاج إلى بعض المساعدة؟ فكر في [الحصول على المساعدة في العمل Microsoft 365](https://support.microsoft.com/en-us/office/business-assist-for-microsoft-365-37deb8fe-61cc-4cf9-9ad1-1c8d93475070)

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول Microsoft Defender for Business](../security/defender-business/mdb-overview.md) (مضمن الآن مع Microsoft 365 Business Premium!)

- [اشتراكات الأعمال ووثائق الفوترة](../commerce/index.yml)

- [نظرة عامة Microsoft 365 المنارة](../lighthouse/m365-lighthouse-overview.md) (ل Microsoft CSPs)

- [أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](../admin/security-and-compliance/secure-your-business-data.md)
