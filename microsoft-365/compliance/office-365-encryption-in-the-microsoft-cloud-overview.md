---
title: التشفير في Microsoft Cloud
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: في هذه المقالة، اقرأ نظرة عامة حول مختلف أشكال التشفير المستخدمة للحفاظ على أمان بيانات العملاء في سحابة Microsoft.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c888c1958eb5265c31ae981e42a96eeeeb57f3ef
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63565934"
---
# <a name="encryption-in-the-microsoft-cloud"></a>التشفير في Microsoft Cloud

تكون بيانات العملاء ضمن خدمات السحابة الخاصة بالمؤسسات من Microsoft محمية بواسطة العديد من التقنيات والعمليات، بما في ذلك أشكال مختلفة من التشفير. (تتضمن بيانات العميل في هذا المستند محتوى علبة بريد Exchange Online والمحتوى الصوتي للبريد الإلكتروني وإد إدخالات التقويم ومحتوى مرفقات البريد الإلكتروني ومحتوى Skype for Business ومحتوى SharePoint عبر الإنترنت ومحتوى موقع SharePoint عبر الإنترنت والملفات المخزنة ضمن المواقع والملفات التي تم تحميلها إلى OneDrive for Business  أو Skype for Business.) تستخدم Microsoft أساليب تشفير متعددة، والبروتوكولات، والتشفيرات عبر منتجاتها وخدماتها للمساعدة في توفير مسار آمن لبيانات العملاء للتنقل عبر خدمات السحابة، وللمساعدة في حماية سرية بيانات العملاء المخزنة ضمن خدمات السحابة لدينا. تستخدم Microsoft بعض بروتوكولات التشفير الاقوى والأكثر أمانا المتوفرة لتوفير عوائق أمام الوصول غير المصرح به إلى بيانات العملاء. كما أن الإدارة المناسبة للمفاتيح هي عنصر أساسي لأفضل ممارسات التشفير، وتعمل Microsoft لضمان تأمين جميع مفاتيح التشفير المدارة من Microsoft بشكل صحيح.

تكون بيانات العملاء المخزنة ضمن خدمات السحابة الخاصة بالمؤسسات من Microsoft محمية باستخدام شكل واحد أو أكثر من أشكال التشفير. (يتم التحقق بشكل مستقل من صحة نهج التشفير لدينا ونفاذه من قبل عدة مراجعين خارجيين، كما تتوفر تقارير عمليات التدقيق هذه على [Service Trust Portal](https://aka.ms/stp).)

توفر Microsoft تقنيات من جانب الخدمة تقوم بتشفير بيانات العملاء أثناء الراحة وعند النقل. على سبيل المثال، بالنسبة لبيانات العملاء في الوقت الباقي، يستخدم Microsoft Azure [BitLocker](/windows/device-security/bitlocker/bitlocker-overview) و [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt)، ويستخدم Microsoft 365 BitLocker و"تشفير خدمة تخزين [Azure](/azure/)" و"إدارة المفاتيح الموزعة[" (](./exchange-online-secures-email-secrets.md)DKM) Microsoft 365 تشفير الخدمة. بالنسبة لبيانات العملاء أثناء النقل، تستخدم Azure و Office 365 و Microsoft Commercial Support و Microsoft Dynamics 365 و Microsoft Power BI و Visual Studio Team Services بروتوكولات نقل آمنة قياسية، مثل أمان بروتوكول الإنترنت (IPsec) و أمان طبقة النقل (TLS) بين مراكز بيانات Microsoft وبين أجهزة المستخدمين و مراكز بيانات Microsoft.

بالإضافة إلى مستوى أمان التشفير الأساسي الذي توفره Microsoft، تتضمن خدماتنا السحابية أيضا خيارات التشفير التي يمكنك إدارتها. على سبيل المثال، يمكنك تمكين التشفير لحركة المرور بين أجهزة Azure الظاهرية (VMs) والمستخدمين. باستخدام [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/)، يمكنك استخدام بروتوكول IPsec القياسي في المجال لتشفير حركة المرور بين بوابة VPN الخاصة بالشركة و Azure. يمكنك أيضا تشفير حركة المرور بين أجهزة VMs على شبكتك الظاهرية. بالإضافة إلى ذلك، [تسمح تشفير الرسائل من Office 365 الجديدة بإرسال](set-up-new-message-encryption-capabilities.md) بريد مشفر إلى أي شخص.

باتباع معيار الأمان التشغيلي للبنية الأساسية للمفتاح العام، وهو أحد مكونات نهج [أمان Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers)، تستخدم Microsoft قدرات التشفير المضمنة في نظام Windows التشغيل للشهادات آليات المصادقة. تتضمن هذه الآليات استخدام الوحدات النمطية للتشريب التي تفي بالمعايير الفيدرالية لمعالجة [المعلومات (](https://csrc.nist.gov/publications/PubsFIPS.html) FIPS) 140-2 الخاصة ب الحكومة الأمريكية. يمكنك البحث عن أرقام شهادات NIST ذات الصلة ل Microsoft باستخدام [CMVP](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search) برنامج التحقق من وحدة التشفير النمطية.

> [ملاحظة] للوصول إلى نهج أمان Microsoft كمورد، يجب تسجيل الدخول باستخدام حساب العمل أو المدرسة. إذا لم يكن لديك اشتراك بعد، [يمكنك التسجيل للحصول على فترة تجريبية مجانية](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

إن FIPS 140-2 هو معيار مصمم خصيصا للتحقق من الوحدات النمطية للمنتجات التي تنفذ التشفير بدلا من المنتجات التي تستخدمها. يمكن اعتماد الوحدات النمطية للتشريب التي يتم تنفيذها ضمن الخدمة على أنها تلبية لمتطلبات قوة هاش وإدارة المفاتيح وما إلى ذلك. تفي الوحدات النمطية للتشفير والتشفير المستخدمة لحماية سرية البيانات أو تكاملها أو توافرها في خدمات Microsoft السحابية ب معايير FIPS 140-2.

تصادق Microsoft على الوحدات النمطية الأساسية للتشريب المستخدمة في خدماتنا السحابية مع كل إصدار جديد Windows التشغيل:

- Azure و Azure U.S. Government
- Dynamics 365 و Dynamics 365 U.S. Government
- Office 365 Office 365 الحكومة الأمريكية Office 365 الدفاع عن الحكومة الأمريكية

يتم توفير تشفير بيانات العملاء في حالة راحة من خلال تقنيات متعددة من جانب الخدمة، بما في ذلك BitLocker و DKM و تشفير خدمة تخزين Azure و تشفير الخدمة في Exchange Online و Skype for Business و OneDrive for Business و SharePoint عبر الإنترنت. Office 365 تشفير الخدمة خيارا لاستخدام مفاتيح التشفير المدارة من قبل العملاء المخزنة في مخزن مفاتيح Azure. يتوفر خيار المفتاح المدار من قبل العميل، [](./customer-key-overview.md)المسمى مفتاح العميل، Exchange Online SharePoint عبر الإنترنت Skype for Business OneDrive for Business.

بالنسبة لبيانات العملاء أثناء النقل، تتفاوض جميع خوادم Office 365 حول جلسات عمل آمنة باستخدام TLS بشكل افتراضي مع أجهزة العميل لتأمين بيانات العميل. على سبيل المثال Office 365 التفاوض بشأن جلسات عمل آمنة Skype for Business Outlook والتنقل Outlook على ويب الجوال والعملاء ومستعرضات الويب.

(تتفاوض كل الخوادم التي تواجه العميل مع TLS 1.2 بشكل افتراضي.)

## <a name="related-links"></a>الارتباطات ذات الصلة

- [التشفير في Azure](office-365-azure-encryption.md)
- [BitLocker و"إدارة المفاتيح الموزعة" (DKM) للتشفير](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Office 365 تشفير الخدمة](office-365-service-encryption.md)
- [Office 365 تشفير Skype for Business OneDrive for Business و SharePoint عبر الإنترنت Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [تشفير البيانات أثناء النقل](/compliance/assurance/assurance-encryption-in-transit)
- [ميزات التشفير المدارة من قبل العملاء](office-365-customer-managed-encryption-features.md)
- [مخاطر التشفير والحماية](office-365-encryption-risks-and-protections.md)
- [التشفير في Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)