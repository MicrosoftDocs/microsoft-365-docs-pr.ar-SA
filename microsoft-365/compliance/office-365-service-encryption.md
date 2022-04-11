---
title: تشفير الخدمة
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.date: 10/3/2019
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: 'ملخص: فهم مرونة البيانات في Microsoft Office 365.'
ms.openlocfilehash: 9b569bc30a9d7d8485fe0004cf46ba39277c47ae
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760790"
---
# <a name="service-encryption"></a>تشفير الخدمة

بالإضافة إلى استخدام التشفير على مستوى وحدة التخزين، Exchange Online Microsoft Teams SharePoint Online OneDrive for Business أيضا استخدام تشفير الخدمة لتشفير بيانات العميل. يسمح تشفير الخدمة باثنين من خيارات الإدارة الرئيسية:

## <a name="microsoft-managed-keys"></a>المفاتيح المدارة من قبل Microsoft
تدير Microsoft جميع مفاتيح التشفير بما في ذلك مفاتيح الجذر لتشفير الخدمة. يتم تمكين هذا الخيار حاليا بشكل افتراضي ل Exchange Online أو SharePoint Online أو OneDrive for Business. توفر المفاتيح المدارة من قبل Microsoft تشفير الخدمة الافتراضي ما لم تقرر الإلحاق باستخدام Customer Key. إذا قررت في وقت لاحق التوقف عن استخدام مفتاح العميل دون اتباع مسار إزالة البيانات، فستبقى بياناتك مشفرة باستخدام المفاتيح التي تديرها Microsoft. يتم تشفير بياناتك دائما على هذا المستوى الافتراضي كحد أدنى. 

## <a name="customer-key"></a>مفتاح العميل
يمكنك توفير مفاتيح الجذر المستخدمة مع تشفير الخدمة وتدير هذه المفاتيح باستخدام azure Key Vault. تدير Microsoft جميع المفاتيح الأخرى. يسمى هذا الخيار مفتاح العميل، وهو متوفر حاليا Exchange Online SharePoint Online و OneDrive for Business. (يشار إليه سابقا باسم التشفير المتقدم باستخدام BYOK. راجع [تحسين الشفافية والتحكم لعملاء Office 365](https://www.microsoft.com/en-us/microsoft-365/blog/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) للإعلان الأصلي.)

يوفر تشفير الخدمة فوائد متعددة:

- يوفر طبقة حماية إضافية أعلى BitLocker.

- يوفر فصل مسؤولي نظام التشغيل Windows عن الوصول إلى بيانات التطبيق المخزنة أو المعالجة بواسطة نظام التشغيل.

- يتضمن خيار "مفتاح العميل" الذي يمكن الخدمات متعددة المستأجرين من توفير إدارة المفاتيح لكل مستأجر.

- يعزز قدرة Microsoft 365 على تلبية متطلبات العملاء الذين لديهم متطلبات امتثال محددة فيما يتعلق بالتشفير.

باستخدام مفتاح العميل، يمكنك إنشاء مفاتيح التشفير الخاصة بك باستخدام وحدة خدمة الأجهزة المحلية (HSM) أو Azure Key Vault (AKV). بغض النظر عن كيفية إنشاء المفتاح، يمكنك استخدام AKV للتحكم في مفاتيح التشفير المستخدمة من قبل Office 365 وإدارتها. بمجرد تخزين المفاتيح في AKV، يمكن استخدامها كجذر لإحدى سلاسل المفاتيح التي تقوم بتشفير بيانات علبة البريد أو الملفات.

ميزة أخرى لمفتاح العميل هي التحكم الذي لديك على قدرة Microsoft على معالجة بياناتك. إذا كنت تريد إزالة البيانات من Office 365، على سبيل المثال، إذا كنت تريد إنهاء الخدمة مع Microsoft أو إزالة جزء من البيانات المخزنة في السحابة، يمكنك القيام بذلك واستخدام مفتاح العميل كعنصر تحكم تقني. تضمن إزالة البيانات عدم تمكن أي شخص، بما في ذلك Microsoft، من الوصول إلى البيانات أو معالجتها. مفتاح العميل هو بالإضافة إلى ذلك ومتمم ل Customer Lockbox الذي تستخدمه للتحكم في الوصول إلى بياناتك من قبل موظفي Microsoft.

لمعرفة كيفية إعداد مفتاح العميل Microsoft 365 ل Exchange Online، Microsoft Teams، SharePoint Online، بما في ذلك مواقع الفريق، OneDrive for Business، راجع المقالات التالية:

- [تشفير الخدمة باستخدام مفتاح العميل](customer-key-overview.md)

- [إعداد مفتاح العميل](customer-key-set-up.md)

- [إدارة مفتاح العميل](customer-key-manage.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [فهم مفتاح التوفر](customer-key-availability-key-understand.md)
