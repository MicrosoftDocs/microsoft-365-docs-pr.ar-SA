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
ms.openlocfilehash: 54bae9fa0203d76c598c4dee337ee15f24a2fc24
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566741"
---
# <a name="service-encryption"></a>تشفير الخدمة

بالإضافة إلى استخدام التشفير على مستوى Exchange Online، Microsoft Teams، SharePoint عبر الإنترنت، OneDrive for Business استخدام تشفير الخدمة لتشفير بيانات العملاء. يتيح تشفير الخدمة خيارين رئيسيين للإدارة:

## <a name="microsoft-managed-keys"></a>المفاتيح المدارة من Microsoft
تدير Microsoft كل مفاتيح التشفير بما في ذلك المفاتيح الجذر لتشفير الخدمة. يتم تمكين هذا الخيار حاليا بشكل افتراضي Exchange Online أو SharePoint أو OneDrive for Business. توفر المفاتيح المدارة من Microsoft تشفير الخدمة الافتراضي إلا إذا قررت التكميل باستخدام "مفتاح العميل". إذا قررت، في وقت لاحق، التوقف عن استخدام "مفتاح العميل" دون اتباع مسار إزالة البيانات، فإن بياناتك تبقى مشفرة باستخدام المفاتيح المدارة من Microsoft. يتم تشفير بياناتك دائما في هذا المستوى الافتراضي كحد أدنى. 

## <a name="customer-key"></a>مفتاح العميل
يمكنك توفير المفاتيح الجذر المستخدمة مع تشفير الخدمة وإدارة هذه المفاتيح باستخدام Azure Key Vault. تدير Microsoft كل المفاتيح الأخرى. يسمى هذا الخيار "مفتاح العميل"، وهو متوفر حاليا Exchange Online SharePoint عبر الإنترنت OneDrive for Business. (يشار إليه سابقا بالتشفير المتقدم باستخدام BYOK. راجع [تحسين الشفافية والتحكم Office 365 لعملاء الإعلانات](https://www.microsoft.com/en-us/microsoft-365/blog/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) الأصلية.)

يوفر تشفير الخدمة فوائد متعددة:

- يوفر طبقة حماية إضافية في أعلى BitLocker.

- يوفر فصل Windows عن الوصول إلى بيانات التطبيق المخزنة أو المعالجة بواسطة نظام التشغيل.

- يتضمن خيار "مفتاح العميل" الذي يمكن الخدمات متعددة المستأجرين من توفير إدارة مفتاح لكل مستأجر.

- يحسن من قدرة Microsoft 365 لتلبية متطلبات العملاء الذين لديهم متطلبات توافق معينة فيما يتعلق بالتشفير.

باستخدام "مفتاح العميل"، يمكنك إنشاء مفاتيح التشفير الخاصة بك باستخدام وحدة نمطية لخدمة الأجهزة (HSM) أو مخزن مفاتيح Azure (AKV). بغض النظر عن كيفية إنشاء المفتاح، يمكنك استخدام AKV للتحكم في مفاتيح التشفير المستخدمة بواسطة Office 365. بمجرد تخزين المفاتيح في AKV، يمكن استخدامها ك الجذر لأحد سلسلة المفاتيح التي تشفر بيانات علبة البريد أو ملفاتها.

هناك فائدة أخرى من "مفتاح العميل" وهي التحكم الذي تملكه على قدرة Microsoft على معالجة بياناتك. إذا كنت تريد إزالة البيانات من Office 365، مثل إذا كنت تريد إنهاء الخدمة مع Microsoft أو إزالة جزء من البيانات المخزنة في السحابة، يمكنك القيام بذلك واستخدام "مفتاح العميل" كع تحكم تقني. تضمن إزالة البيانات عدم إمكانية وصول أي شخص، بما في ذلك Microsoft، إلى البيانات أو معالجة البيانات. "مفتاح العميل" هو إضافة إلى مربع تأمين العميل الذي تستخدمه للتحكم في الوصول إلى بياناتك من قبل موظفي Microsoft.

للتعرف على كيفية إعداد "مفتاح العميل" Microsoft 365 Exchange Online و Microsoft Teams و SharePoint عبر الإنترنت، بما في ذلك مواقع الفريق OneDrive for Business، راجع المقالات التالية:

- [تشفير الخدمة باستخدام "مفتاح العميل"](customer-key-overview.md)

- [إعداد مفتاح العميل](customer-key-set-up.md)

- [إدارة مفتاح العميل](customer-key-manage.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [فهم مفتاح التوفر](customer-key-availability-key-understand.md)
