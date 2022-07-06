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
description: في هذه المقالة، اقرأ نظرة عامة على أشكال التشفير المختلفة المستخدمة للحفاظ على أمان بيانات العملاء في سحابة Microsoft.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3105da5d17b1656ffa0d29da4f4aa02c9a9f9064
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633906"
---
# <a name="encryption-in-the-microsoft-cloud"></a>التشفير في Microsoft Cloud

تتم حماية بيانات العملاء داخل خدمات Microsoft السحابية للمؤسسات من خلال العديد من التقنيات والعمليات، بما في ذلك أشكال مختلفة من التشفير. (تتضمن بيانات العميل في هذا المستند محتوى علبة بريد Exchange Online والنص الأساسي للبريد الإلكتروني وإدخالات التقويم ومحتوى مرفقات البريد الإلكتروني، وإذا كان ذلك ممكنا، Skype for Business المحتوى) ومحتوى موقع SharePoint Online والملفات المخزنة داخل المواقع والملفات التي تم تحميلها إلى OneDrive for Business أو Skype for Business.) تستخدم Microsoft أساليب تشفير متعددة وبروتوكولات وعبارات عبر منتجاتها وخدماتها للمساعدة في توفير مسار آمن لبيانات العملاء للتنقل عبر خدماتنا السحابية، وللمساعدة في حماية سرية بيانات العملاء المخزنة داخل خدمات السحابة. تستخدم Microsoft بعض أقوى بروتوكولات التشفير المتاحة وأكثرها أمانا لتوفير حواجز ضد الوصول غير المصرح به إلى بيانات العملاء. تعد إدارة المفاتيح المناسبة أيضا عنصرا أساسيا في أفضل ممارسات التشفير، وتعمل Microsoft لضمان تأمين جميع مفاتيح التشفير التي تديرها Microsoft بشكل صحيح.

تتم حماية بيانات العميل المخزنة داخل خدمات السحابة المؤسسية من Microsoft باستخدام شكل واحد أو أكثر من أشكال التشفير. (يتم التحقق من صحة نهج التشفير وإنفاذه بشكل مستقل من قبل العديد من مدققي الجهات الخارجية، وتتوفر تقارير عمليات التدقيق هذه على [Service Trust Portal](https://aka.ms/stp).)

توفر Microsoft تقنيات من جانب الخدمة تقوم بتشفير بيانات العملاء الثابتة والمتنقلة. على سبيل المثال، بالنسبة إلى بيانات العملاء الثابتة، يستخدم Microsoft Azure [BitLocker](/windows/device-security/bitlocker/bitlocker-overview) [وDM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt)، ويستخدم Microsoft 365 BitLocker [وتشفير خدمة تخزين Azure](/azure/) [وإدارة المفاتيح الموزعة](./exchange-online-secures-email-secrets.md) (DKM) وتشفير خدمة Microsoft 365. بالنسبة لبيانات العملاء المتنقلة، تستخدم Azure Office 365 والدعم التجاري من Microsoft وMicrosoft Dynamics 365 وMicrosoft Power BI وVisual Studio Team Services بروتوكولات النقل الآمن القياسية في الصناعة، مثل أمان بروتوكول الإنترنت (IPsec) وأمان طبقة النقل (TLS)، بين مراكز بيانات Microsoft وبين أجهزة المستخدم ومراكز بيانات Microsoft.

بالإضافة إلى المستوى الأساسي لأمان التشفير الذي توفره Microsoft، تتضمن خدمات السحابة أيضا خيارات التشفير التي يمكنك إدارتها. على سبيل المثال، يمكنك تمكين التشفير لنسبة استخدام الشبكة بين أجهزة Azure الظاهرية (VMs) ومستخدميها. باستخدام [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/)، يمكنك استخدام بروتوكول IPsec القياسي في الصناعة لتشفير نسبة استخدام الشبكة بين بوابة VPN الخاصة بالشركة وAzure. يمكنك أيضا تشفير نسبة استخدام الشبكة بين الأجهزة الظاهرية على شبكتك الظاهرية. بالإضافة إلى ذلك، تسمح لك [إمكانيات تشفير الرسائل Office 365 الجديدة](set-up-new-message-encryption-capabilities.md) بإرسال بريد مشفر إلى أي شخص.

باتباع معيار الأمان التشغيلي للمفتاح العام للبنية الأساسية، وهو أحد مكونات [نهج أمان Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers)، تستخدم Microsoft قدرات التشفير المضمنة في نظام التشغيل Windows للشهادات وآليات المصادقة. تتضمن هذه الآليات استخدام وحدات التشفير التي تفي [بمعايير معالجة المعلومات الفيدرالية](https://csrc.nist.gov/publications/PubsFIPS.html) (FIPS) 140-2 لحكومة الولايات المتحدة. يمكنك البحث عن أرقام شهادات NIST ذات الصلة ل Microsoft باستخدام [برنامج التحقق من صحة وحدة التشفير CMVP](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> [ملاحظة] للوصول إلى نهج أمان Microsoft كمورد، يجب تسجيل الدخول باستخدام حساب العمل أو المؤسسة التعليمية. إذا لم يكن لديك اشتراك بعد، [يمكنك التسجيل للحصول على إصدار تجريبي مجاني](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2 هو معيار مصمم خصيصا للتحقق من صحة وحدات المنتج التي تنفذ التشفير بدلا من المنتجات التي تستخدمها. يمكن اعتماد وحدات التشفير التي يتم تنفيذها داخل الخدمة على أنها تلبي متطلبات قوة التجزئة وإدارة المفاتيح وما إلى ذلك. تتوافق وحدات التشفير والشفرات المستخدمة لحماية سرية البيانات أو تكاملها أو توفرها في خدمات Microsoft السحابية مع معيار FIPS 140-2.

تقوم Microsoft بالمصادقة على وحدات التشفير الأساسية المستخدمة في خدماتنا السحابية مع كل إصدار جديد من نظام التشغيل Windows:

- Azure وAzure U.S. Government
- Dynamics 365 و Dynamics 365 U.S. Government
- Office 365، Office 365 حكومة الولايات المتحدة، Office 365 الدفاع الحكومي الأمريكي

يتم توفير تشفير بيانات العملاء الثابتة من خلال تقنيات متعددة من جانب الخدمة، بما في ذلك BitLocker وDKM وAzure Storage Service Encryption وتشفير الخدمة في Exchange Online Skype for Business OneDrive for Business وSharePoint Online. يتضمن تشفير الخدمة Office 365 خيارا لاستخدام مفاتيح التشفير التي يديرها العميل والمخزنة في Key Vault Azure. يتوفر خيار المفتاح المدار بواسطة العميل، [المسمى Customer Key](./customer-key-overview.md)، Exchange Online وSharePoint Online Skype for Business OneDrive for Business.

بالنسبة لبيانات العملاء المتنقلة، تتفاوض جميع خوادم Office 365 على جلسات عمل آمنة باستخدام TLS بشكل افتراضي مع أجهزة العميل لتأمين بيانات العميل. على سبيل المثال، سيقوم Office 365 بالتفاوض بشأن جلسات عمل آمنة Skype for Business وOutlook Outlook على ويب وعملاء الأجهزة المحمولة ومستعرضات الويب.

(تتفاوض جميع الخوادم التي تواجه العملاء مع TLS 1.2 بشكل افتراضي.)

## <a name="related-links"></a>الارتباطات ذات الصلة

- [التشفير في Azure](office-365-azure-encryption.md)
- [BitLocker و"إدارة المفاتيح الموزعة" (DKM) للتشفير](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [تشفير خدمة Office 365](office-365-service-encryption.md)
- [تشفير Office 365 ل Skype for Business OneDrive for Business وSharePoint Online و Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [تشفير البيانات المتنقلة](/compliance/assurance/assurance-encryption-in-transit)
- [ميزات التشفير المدارة من قبل العميل](office-365-customer-managed-encryption-features.md)
- [مخاطر التشفير وحمايتها](office-365-encryption-risks-and-protections.md)
- [التشفير في Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)
