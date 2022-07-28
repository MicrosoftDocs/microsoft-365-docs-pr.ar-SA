---
title: مرجع نهج تفادي فقدان البيانات
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 03/02/2022
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: مكون نهج DLP ومرجع التكوين
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 9184bf848a1bf23bde639767c09a66e681d5553f
ms.sourcegitcommit: 23a53b5c5e372a2a7ad5e175850224d3d464f6dd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67056559"
---
# <a name="data-loss-prevention-policy-reference"></a>مرجع نهج تفادي فقدان البيانات

تحتوي نهج تفادي فقدان البيانات في Microsoft Purview (DLP) على العديد من المكونات لتكوينها. لإنشاء نهج فعال، تحتاج إلى فهم الغرض من كل مكون وكيف يغير تكوينه سلوك النهج. توفر هذه المقالة تشريحا مفصلا لنهج DLP.

## <a name="policy-templates"></a>قوالب النهج 

يتم فرز قوالب نهج DLP مسبقا إلى أربع فئات:

- تلك التي يمكنها الكشف عن أنواع المعلومات **المالية** وحمايتها.
- تلك التي يمكنها الكشف عن أنواع المعلومات **الطبية والصحة** وحمايتها.
- تلك التي يمكنها اكتشاف أنواع معلومات **الخصوصية** وحمايتها.
- قالب **مخصص** يمكنك استخدامه لإنشاء نهج خاص بك إذا كان أحد القوالب الأخرى لا يلبي احتياجات مؤسستك.

يسرد هذا الجدول كافة قوالب النهج وأنواع المعلومات الحساسة (SIT) التي تغطيها. 

محدث: 06/23/2021

|الفئة|قالب | الجلوس |
|---------|---------|---------|
|الماليه| بيانات أستراليا المالية| - [رمز SWIFT](sit-defn-swift-code.md) </br> -  [رقم ملف الضريبة في أستراليا](sit-defn-australia-tax-file-number.md) </br> - [رقم الحساب البنكي في أستراليا](sit-defn-australia-bank-account-number.md) </br> - [رقم بطاقة الائتمان](sit-defn-credit-card-number.md)|
|الماليه| البيانات المالية لكندا |- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي في كندا](sit-defn-canada-bank-account-number.md)|
|الماليه| بيانات فرنسا المالية |- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sit-defn-eu-debit-card-number.md)|
|الماليه| البيانات المالية في ألمانيا |- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sit-defn-eu-debit-card-number.md)|
|الماليه| البيانات المالية في إسرائيل |- [رقم الحساب البنكي في إسرائيل](sit-defn-israel-bank-account-number.md) </br> - [رمز SWIFT](sit-defn-swift-code.md) </br> - [رقم بطاقة الائتمان](sit-defn-credit-card-number.md)|
|الماليه| البيانات المالية اليابانية |- [رقم الحساب البنكي الياباني](sit-defn-japan-bank-account-number.md)</br> - [رقم بطاقة الائتمان](sit-defn-credit-card-number.md)|
|الماليه| PCI Data Security Standard (PCI DSS)|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md)|
|الماليه| قانون مكافحة الجريمة الإلكترونية في المملكة العربية السعودية|- [رمز SWIFT](sit-defn-swift-code.md) </br> - [رقم الحساب المصرفي الدولي (IBAN)](sit-defn-international-banking-account-number.md)|
|الماليه| البيانات المالية في المملكة العربية السعودية |- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رمز SWIFT](sit-defn-swift-code.md) </br> - [رقم الحساب المصرفي الدولي (IBAN)](sit-defn-international-banking-account-number.md)|
|الماليه| البيانات المالية في المملكة المتحدة|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sit-defn-eu-debit-card-number.md) </br> - [رمز SWIFT](sit-defn-swift-code.md)|
|الماليه| البيانات المالية الأمريكية|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> - [رقم توجيه ABA](sit-defn-aba-routing.md)|
|الماليه| قواعد المستهلك في لجنة التجارة الفيدرالية (FTC) في الولايات المتحدة|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> - [رقم توجيه ABA](sit-defn-aba-routing.md)|
|الماليه| U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sit-defn-us-uk-passport-number.md) </br> -[رقم رخصة القيادة الأمريكية](sit-defn-us-drivers-license-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md)</br> - [العناوين الفعلية في الولايات المتحدة](sit-defn-us-physical-addresses.md)|
|الماليه| قانون Gramm-Leach-Bliley (GLBA) الأمريكي|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)|
|الرعاية الطبية والصحة| قانون السجلات الصحية في أستراليا (قانون HRIP) محسن |- [رقم ملف الضريبة في أستراليا](sit-defn-australia-tax-file-number.md)</br> - [رقم الحساب الطبي في أستراليا](sit-defn-australia-medical-account-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md) </br> - [كافة الشروط والأحكام الطبية](sit-defn-all-medical-terms-conditions.md) </br> - [العناوين المادية في أستراليا](sit-defn-australia-physical-addresses.md)|
|الرعاية الطبية والصحة| قانون السجلات الصحية في أستراليا (قانون HRIP)|- [رقم ملف الضريبة في أستراليا](sit-defn-australia-tax-file-number.md) </br> - [رقم الحساب الطبي في أستراليا](sit-defn-australia-medical-account-number.md)|
|الرعاية الطبية والصحة| قانون المعلومات الصحية في كندا (HIA) |- [رقم جواز سفر كندا](sit-defn-canada-passport-number.md) </br> - [رقم التأمين الاجتماعي في كندا](sit-defn-canada-social-insurance-number.md) </br> - [رقم خدمة الصحة في كندا](sit-defn-canada-health-service-number.md) </br> - [رقم التعريف الصحي الشخصي لكندا](sit-defn-canada-personal-health-identification-number.md)|
|الرعاية الطبية والصحة| قانون المعلومات الصحية الشخصية (PHIA) مانيتوبا في كندا|- [رقم التأمين الاجتماعي في كندا](sit-defn-canada-social-insurance-number.md) </br> - [رقم خدمة الصحة في كندا](sit-defn-canada-health-service-number.md) </br> - [رقم التعريف الصحي الشخصي لكندا](sit-defn-canada-personal-health-identification-number.md)|
|الرعاية الطبية والصحة| قانون الصحة الشخصية في كندا (PHIPA) في كندا |- [رقم جواز سفر كندا](sit-defn-canada-passport-number.md) </br> - [رقم التأمين الاجتماعي في كندا](sit-defn-canada-social-insurance-number.md) </br> - [رقم خدمة الصحة في كندا](sit-defn-canada-health-service-number.md) </br> - [رقم التعريف الصحي الشخصي لكندا](sit-defn-canada-personal-health-identification-number.md)|
|الرعاية الطبية والصحة| المملكة المتحدة قانون الوصول إلى التقارير الطبية|- [رقم خدمة الصحة الوطنية في المملكة المتحدة](sit-defn-uk-national-health-service-number.md) </br> - [رقم التأمين الوطني في المملكة المتحدة (NINO)](sit-defn-uk-national-insurance-number.md)|
|الرعاية الطبية والصحة| قانون التأمين الصحي (HIPAA) المحسن في الولايات المتحدة|</br> - [التصنيف الدولي الأمراض (ICD-9-CM)](sit-defn-international-classification-of-diseases-icd-9-cm.md) </br> - [التصنيف الدولي الأمراض (ICD-10-CM)](sit-defn-international-classification-of-diseases-icd-10-cm.md) </br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md) </br> - [كافة الشروط والأحكام الطبية](sit-defn-all-medical-terms-conditions.md) </br> - [العناوين الفعلية في الولايات المتحدة](sit-defn-us-physical-addresses.md)|
|الرعاية الطبية والصحة| قانون التأمين الصحي الأمريكي (HIPAA)| - [التصنيف الدولي الأمراض (ICD-9-CM)](sit-defn-international-classification-of-diseases-icd-9-cm.md) </br> - [التصنيف الدولي الأمراض (ICD-10-CM)](sit-defn-international-classification-of-diseases-icd-10-cm.md)|
|الخصوصية| قانون الخصوصية في أستراليا المحسن|- [رقم رخصة القيادة في أستراليا](sit-defn-australia-drivers-license-number.md) </br> - [رقم جواز سفر أستراليا](sit-defn-australia-passport-number.md) </br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md) </br> - [كافة الشروط والأحكام الطبية](sit-defn-all-medical-terms-conditions.md) </br> - [العناوين المادية في أستراليا](sit-defn-australia-physical-addresses.md)|
|الخصوصية| قانون الخصوصية في أستراليا|- [رقم ترخيص برامج التشغيل في أستراليا](sit-defn-australia-drivers-license-number.md)</br> - [رقم جواز سفر أستراليا](sit-defn-australia-passport-number.md)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في أستراليا|- [رقم ملف الضريبة في أستراليا](sit-defn-australia-tax-file-number.md) </br> - [رقم رخصة القيادة في أستراليا](sit-defn-australia-drivers-license-number.md)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في كندا|- [رقم رخصة القيادة في كندا](sit-defn-canada-drivers-license-number.md) </br> - [رقم الحساب البنكي في كندا](sit-defn-canada-bank-account-number.md) </br> - [رقم جواز سفر كندا](sit-defn-canada-passport-number.md) </br> - [رقم التأمين الاجتماعي في كندا](sit-defn-canada-social-insurance-number.md) </br> - [رقم خدمة الصحة في كندا](sit-defn-canada-health-service-number.md) </br> - [رقم التعريف الصحي الشخصي لكندا](sit-defn-canada-personal-health-identification-number.md)|
|الخصوصية| قانون حماية البيانات الشخصية في كندا (PIPA)|- [رقم جواز سفر كندا](sit-defn-canada-passport-number.md) </br> - [رقم التأمين الاجتماعي في كندا](sit-defn-canada-social-insurance-number.md) </br> - [رقم خدمة الصحة في كندا](sit-defn-canada-health-service-number.md) </br> - [رقم التعريف الصحي الشخصي لكندا](sit-defn-canada-personal-health-identification-number.md)|
|الخصوصية| قانون حماية البيانات الشخصية في كندا (PIPEDA)|- [رقم رخصة القيادة في كندا](sit-defn-canada-drivers-license-number.md) </br> - [رقم الحساب البنكي في كندا](sit-defn-canada-bank-account-number.md) </br> - [رقم جواز سفر كندا](sit-defn-canada-passport-number.md) </br> - [رقم التأمين الاجتماعي في كندا](sit-defn-canada-social-insurance-number.md) </br> - [رقم خدمة الصحة في كندا](sit-defn-canada-health-service-number.md) </br> - [رقم التعريف الصحي الشخصي لكندا](sit-defn-canada-personal-health-identification-number.md)|
|الخصوصية| قانون حماية البيانات في فرنسا|- [بطاقة المعرف الوطنية الفرنسية (CNI)](sit-defn-france-national-id-card.md)</br> - [رقم الضمان الاجتماعي (INSEE) في فرنسا](sit-defn-france-social-security-number.md)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في فرنسا|- [رقم الضمان الاجتماعي (INSEE) في فرنسا](sit-defn-france-social-security-number.md) </br> - [رقم رخصة القيادة في فرنسا](sit-defn-france-drivers-license-number.md) </br> - [رقم جواز سفر فرنسا](sit-defn-france-passport-number.md) </br> - [بطاقة المعرف الوطنية الفرنسية (CNI)](sit-defn-france-national-id-card.md)|
|الخصوصية| القانون العام لحماية البيانات (GDPR) المحسن|- [العناوين المادية في النمسا](sit-defn-austria-physical-addresses.md) </br> - [عناوين فعلية لبلينيا](sit-defn-belgium-physical-addresses.md) </br> - [العناوين المادية لبلغاريا](sit-defn-bulgaria-physical-addresses.md) </br> - [العناوين المادية لكرواتيا](sit-defn-croatia-physical-addresses.md) </br> - [العناوين المادية للكواية](sit-defn-cyprus-physical-addresses.md) </br> - [العناوين المادية للتشيك](sit-defn-czech-republic-physical-addresses.md)</br> - [عناوين الدانمارك المادية](sit-defn-denmark-physical-addresses.md)</br> - [العناوين المادية ل الإستونية](sit-defn-estonia-physical-addresses.md)</br> - [العناوين المادية ل فنلندا](sit-defn-finland-physical-addresses.md)</br> - [عناوين فرنسا الفعلية](sit-defn-france-physical-addresses.md)</br> - [العناوين الفعلية في ألمانيا](sit-defn-germany-physical-addresses.md)</br> - [العناوين المادية في اليونان](sit-defn-greece-physical-addresses.md)</br> - [العناوين المادية في المجر](sit-defn-hungary-physical-addresses.md)</br> - [عناوين أيرلندا المادية](sit-defn-ireland-physical-addresses.md)</br> - [العناوين المادية في إيطاليا](sit-defn-italy-physical-addresses.md)</br> - [عناوين لاتفيا المادية](sit-defn-latvia-physical-addresses.md)</br> - [العناوين المادية ليتوانية](sit-defn-lithuania-physical-addresses.md)</br> - [العناوين المادية لكسمبورج](sit-defn-luxemburg-physical-addresses.md)</br> - [عناوين مادية في أجهزة الكمبيوتر الخارجية](sit-defn-malta-physical-addresses.md)</br> - [العناوين المادية لهولندا](sit-defn-netherlands-physical-addresses.md)</br> - [العناوين المادية لبولاندا](sit-defn-poland-physical-addresses.md)</br> - [العناوين المادية البرتغالية](sit-defn-portugal-physical-addresses.md)</br> - [العناوين المادية في رومانيا](sit-defn-romania-physical-addresses.md)</br> - [العناوين المادية ل لمزوفا](sit-defn-slovakia-physical-addresses.md)</br> - [العناوين المادية السلوفينية](sit-defn-slovenia-physical-addresses.md)</br> - [العناوين الفعلية لإسبانيا](sit-defn-spain-physical-addresses.md)</br> - [العناوين الفعلية في السويد](sit-defn-sweden-physical-addresses.md)</br> - [رقم الضمان الاجتماعي في النمسا](sit-defn-austria-social-security-number.md) </br> - [رقم الضمان الاجتماعي (INSEE) في فرنسا](sit-defn-france-social-security-number.md)</br> - [رقم الضمان الاجتماعي في اليونان (AMKA)](sit-defn-greece-social-security-number.md)</br> - [رقم الضمان الاجتماعي المجري (TAGE)](sit-defn-hungary-social-security-number.md)</br> - [رقم الضمان الاجتماعي الإسباني (SSN)](sit-defn-spain-social-security-number.md)</br> - [بطاقة هوية النمسا](sit-defn-austria-identity-card.md) </br> - [بطاقة هوية هوية للسينية](sit-defn-cyprus-identity-card.md) </br> - [رقم بطاقة الهوية في ألمانيا](sit-defn-germany-identity-card-number.md)</br> - [رقم بطاقة هوية هوية في هوية هوية الأشخاص في](sit-defn-malta-identity-card-number.md)</br> - [بطاقة المعرف الوطنية الفرنسية (CNI)](sit-defn-france-national-id-card.md)</br> - [بطاقة المعرف الوطني في اليونان](sit-defn-greece-national-id-card.md)</br> - [المعرف الوطني ل فنلندا](sit-defn-finland-national-id.md)</br> - [المعرف الوطني لبولونيا (PESEL)](sit-defn-poland-national-id.md)</br> - [المعرف الوطني للسويد](sit-defn-sweden-national-id.md)</br> - [رقم التعريف الشخصي لكرواتيا (OIB)](sit-defn-croatia-personal-identification-number.md) </br> - [رقم الهوية الشخصية التشيكية](sit-defn-czech-personal-identity-number.md)</br> - [رقم التعريف الشخصي للدانمرك](sit-defn-denmark-personal-identification-number.md)</br> - [رمز التعريف الشخصي الإستوني](sit-defn-estonia-personal-identification-code.md)</br> - [رقم التعريف الشخصي في المجر](sit-defn-hungary-personal-identification-number.md)</br> - [الأشخاص الطبيعيون لرقم التعريف الوطني في أوسمبيرغ](sit-defn-luxemburg-national-identification-number-natural-persons.md)</br> - [رقم التعريف الوطني في أوسمبورغ (أشخاص غير طبيعيين)](sit-defn-luxemburg-national-identification-number-non-natural-persons.md)</br> - [الرمز المالي في إيطاليا](sit-defn-italy-fiscal-code.md)</br> - [الرمز الشخصي اللاتفي](sit-defn-latvia-personal-code.md)</br> - [رمز ليتواني الشخصي](sit-defn-lithuania-personal-code.md)</br> - [الرمز الرقمي الشخصي في رومانيا (CNP)](sit-defn-romania-personal-numeric-code.md)</br> - [رقم خدمة المواطنين الهولنديين (BSN)](sit-defn-netherlands-citizens-service-number.md)</br> - [رقم الخدمة العامة الشخصية (PPS) في أيرلندا](sit-defn-ireland-personal-public-service-number.md)</br> - [الرقم المدني الموحد لبلغاريا](sit-defn-bulgaria-uniform-civil-number.md) </br> - [الرقم الوطني لبلكيا](sit-defn-belgium-national-number.md) </br> - [DNI أسبانيا](sit-defn-spain-dni.md)</br> - [رقم مواطن رئيسي فريد في  السلوفينية](sit-defn-slovenia-unique-master-citizen-number.md)</br> - [الرقم الشخصي ل لمزوفا](sit-defn-slovakia-personal-number.md)</br> - [رقم بطاقة مواطن البرتغال](sit-defn-portugal-citizen-card-number.md)</br> - [رقم معرف الضريبة في جبهته](sit-defn-malta-tax-identification-number.md)</br> - [رقم التعريف الضريبي في النمسا](sit-defn-austria-tax-identification-number.md) </br> - [رقم التعريف الضريبي للسريبة](sit-defn-cyprus-tax-identification-number.md) </br> -[رقم التعريف الضريبي في فرنسا (numéro SPI.)](sit-defn-france-tax-identification-number.md)</br> - [رقم التعريف الضريبي في ألمانيا](sit-defn-germany-tax-identification-number.md)</br> - [رقم التعريف الضريبي اليوناني](sit-defn-greece-tax-identification-number.md)</br> - [رقم التعريف الضريبي في المجر](sit-defn-hungary-tax-identification-number.md)</br> - [رقم التعريف الضريبي في هولندا](sit-defn-netherlands-tax-identification-number.md)</br> - [رقم التعريف الضريبي في بولندا](sit-defn-poland-tax-identification-number.md)</br> - [رقم التعريف الضريبي في البرتغال](sit-defn-portugal-tax-identification-number.md)</br> - [رقم التعريف الضريبي السلوفيني](sit-defn-slovenia-tax-identification-number.md)</br> - [رقم التعريف الضريبي لإسبانيا](sit-defn-spain-tax-identification-number.md)</br> - [رقم التعريف الضريبي في السويد](sit-defn-sweden-tax-identification-number.md)</br> - [ترخيص القيادة في النمسا](sit-defn-austria-drivers-license-number.md) </br> - [رقم رخصة القيادة في بلجيكا](sit-defn-belgium-drivers-license-number.md) </br> - [رقم رخصة القيادة في بلغاريا](sit-defn-bulgaria-drivers-license-number.md) </br> - [رقم رخصة القيادة في كرواتيا](sit-defn-croatia-drivers-license-number.md) </br> - [رقم رخصة القيادة للسائق](sit-defn-cyprus-drivers-license-number.md) </br> - [رقم رخصة القيادة التشيكية](sit-defn-czech-drivers-license-number.md) </br> - [رقم رخصة القيادة في الدانمارك](sit-defn-denmark-drivers-license-number.md)</br> - [رقم رخصة القيادة الإستونية](sit-defn-estonia-drivers-license-number.md)</br> - [رقم رخصة القيادة في فنلندا](sit-defn-finland-drivers-license-number.md)</br> - [رقم رخصة قيادة فرنسا](sit-defn-france-drivers-license-number.md)</br> - [رقم رخصة القيادة الألمانية](sit-defn-germany-drivers-license-number.md)</br> - [رقم رخصة القيادة في اليونان](sit-defn-greece-drivers-license-number.md) </br> - [رقم رخصة القيادة في المجر](sit-defn-hungary-drivers-license-number.md)</br> - [رقم رخصة القيادة في أيرلندا](sit-defn-ireland-drivers-license-number.md)</br> - [رقم رخصة القيادة في إيطاليا](sit-defn-italy-drivers-license-number.md)</br> - [رقم رخصة القيادة في لاتفيا](sit-defn-latvia-drivers-license-number.md)</br> - [رقم رخصة القيادة في ليتوانا](sit-defn-lithuania-drivers-license-number.md)</br> - [رقم رخصة القيادة في Burgemburg](sit-defn-luxemburg-drivers-license-number.md)</br> - [رقم رخصة القيادة للمتجر](sit-defn-malta-drivers-license-number.md)</br> - [رقم رخصة القيادة في هولندا](sit-defn-netherlands-drivers-license-number.md)</br> - [رقم رخصة القيادة في بولندا](sit-defn-poland-drivers-license-number.md)</br> - [رقم رخصة القيادة في البرتغال](sit-defn-portugal-drivers-license-number.md)</br> - [رقم رخصة القيادة في رومانيا](sit-defn-romania-drivers-license-number.md)</br> - [رقم رخصة القيادة في  والسلوفاكية](sit-defn-slovakia-drivers-license-number.md)</br> - [رقم رخصة القيادة السلوفينية](sit-defn-slovenia-drivers-license-number.md)</br> - [رقم رخصة القيادة الإسبانية](sit-defn-spain-drivers-license-number.md)</br> - [رقم رخصة القيادة في السويد](sit-defn-sweden-drivers-license-number.md)</br> - [رقم جواز سفر النمسا](sit-defn-austria-passport-number.md) </br> - [رقم جواز سفر بلجيكا](sit-defn-belgium-passport-number.md) </br> - [رقم جواز سفر بلغاريا](sit-defn-bulgaria-passport-number.md) </br> - [رقم جواز السفر الكرواتي](sit-defn-croatia-passport-number.md) </br> - [رقم جواز السفر في بورتس](sit-defn-cyprus-passport-number.md) </br> - [رقم جواز سفر جمهورية تشيكية](sit-defn-czech-passport-number.md) </br> - [رقم جواز سفر الدانمرك](sit-defn-denmark-passport-number.md)</br> - [رقم جواز سفر بورتونيا](sit-defn-estonia-passport-number.md)</br> - [رقم جواز سفر فنلندا](sit-defn-finland-passport-number.md)</br> - [رقم جواز سفر فرنسا](sit-defn-france-passport-number.md)</br> - [رقم جواز سفر ألمانيا](sit-defn-germany-passport-number.md)</br> - [رقم جواز سفر اليونان](sit-defn-greece-passport-number.md)</br> - [رقم جواز سفر المجر](sit-defn-hungary-passport-number.md)</br> - [رقم جواز سفر أيرلندا](sit-defn-ireland-passport-number.md)</br> - [رقم جواز سفر إيطاليا](sit-defn-italy-passport-number.md)</br> - [رقم جواز سفر لاتفيا](sit-defn-latvia-passport-number.md)</br> - [رقم جواز سفر ليتوانا](sit-defn-lithuania-passport-number.md)</br> - [رقم جواز سفر أوسمبورغ](sit-defn-luxemburg-passport-number.md)</br> - [رقم جواز سفر هواء](sit-defn-malta-passport-number.md)</br> - [رقم جواز سفر هولندا](sit-defn-netherlands-passport-number.md)</br> - [جواز سفر بولندا](sit-defn-poland-passport-number.md)</br> - [رقم جواز سفر البرتغال](sit-defn-portugal-passport-number.md)</br> - [رقم جواز سفر رومانيا](sit-defn-romania-passport-number.md)</br> - [رقم جواز سفر بورتوفا](sit-defn-slovakia-passport-number.md)</br> - [رقم جواز السفر السلوفيني](sit-defn-slovenia-passport-number.md)</br> - [رقم جواز سفر إسبانيا](sit-defn-spain-passport-number.md)</br> - [رقم جواز سفر السويد](sit-defn-sweden-passport-number.md)</br> - [رقم بطاقة خصم الاتحاد الأوروبي](sit-defn-eu-debit-card-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md)|
|الخصوصية| القانون العام لحماية البيانات (GDPR)|- [رقم بطاقة خصم الاتحاد الأوروبي](sit-defn-eu-debit-card-number.md) </br> - [رقم رخصة القيادة في الاتحاد الأوروبي](sit-defn-eu-drivers-license-number.md) </br> - [رقم التعريف الوطني للاتحاد الأوروبي](sit-defn-eu-national-identification-number.md)</br> - [رقم جواز سفر الاتحاد الأوروبي](sit-defn-eu-passport-number.md) </br> - [رقم الضمان الاجتماعي في الاتحاد الأوروبي أو التعريف المكافئ](sit-defn-eu-social-security-number-equivalent-identification.md)</br> - [رقم التعريف الضريبي للاتحاد الأوروبي](sit-defn-eu-tax-identification-number.md)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في ألمانيا|- [رقم رخصة القيادة في ألمانيا](sit-defn-germany-drivers-license-number.md) </br> - [رقم جواز سفر ألمانيا](sit-defn-germany-passport-number.md)| 
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في إسرائيل|- [رقم التعريف الوطني في إسرائيل](sit-defn-israel-national-identification-number.md)| 
|الخصوصية| حماية الخصوصية في إسرائيل|- [رقم التعريف الوطني في إسرائيل](sit-defn-israel-national-identification-number.md)</br> - [رقم الحساب البنكي في إسرائيل](sit-defn-israel-bank-account-number.md)|
|الخصوصية| تم تحسين بيانات معلومات التعريف الشخصية (PII) في اليابان|- [رقم التأمين الاجتماعي الياباني (SIN)](sit-defn-japan-social-insurance-number.md)</br> - [رقم هاتفي في اليابان - شخصي](sit-defn-japan-my-number-personal.md)</br> - [رقم جواز سفر اليابان](sit-defn-japan-passport-number.md)</br> - [رقم رخصة القيادة اليابانية](sit-defn-japan-drivers-license-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md)</br> - [العناوين المادية لليابان](sit-defn-all-physical-addresses.md)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في اليابان|- [رقم التسجيل المقيم في اليابان](sit-defn-japan-resident-registration-number.md) </br> - [رقم التأمين الاجتماعي الياباني (SIN)](sit-defn-japan-social-insurance-number.md)|
|الخصوصية| حماية المعلومات الشخصية في اليابان محسنة|- [رقم التأمين الاجتماعي الياباني (SIN)](sit-defn-japan-social-insurance-number.md) </br> - [رقم هاتفي في اليابان - شخصي](sit-defn-japan-my-number-personal.md)</br> - [رقم جواز سفر اليابان](sit-defn-japan-passport-number.md) </br> - [رقم رخصة القيادة اليابانية](sit-defn-japan-drivers-license-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md)</br> - [العناوين المادية لليابان](sit-defn-all-physical-addresses.md)|
|الخصوصية| حماية المعلومات الشخصية في اليابان|- [رقم التسجيل المقيم في اليابان](sit-defn-japan-resident-registration-number.md)</br> - [رقم التأمين الاجتماعي الياباني (SIN)](sit-defn-japan-social-insurance-number.md)|
|الخصوصية| بيانات التعريف الشخصي (PII) في المملكة العربية السعودية|- [المعرف الوطني للسعودية](sit-defn-saudi-arabia-national-id.md)|
|الخصوصية| المملكة المتحدة قانون حماية البيانات|- [رقم التأمين الوطني في المملكة المتحدة (NINO)](sit-defn-uk-national-insurance-number.md) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sit-defn-us-uk-passport-number.md) </br> - [رمز SWIFT](sit-defn-swift-code.md)|
|الخصوصية| المملكة المتحدة لوائح الخصوصية والاتصالات الإلكترونية|- [رمز SWIFT](sit-defn-swift-code.md)|
|الخصوصية| المملكة المتحدة بيانات معلومات التعريف الشخصية (PII)|- [رقم التأمين الوطني في المملكة المتحدة (NINO)](sit-defn-uk-national-insurance-number.md) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sit-defn-us-uk-passport-number.md)|
|الخصوصية| المملكة المتحدة رمز الممارسة للمعلومات الشخصية عبر الإنترنت (PIOCP)|- [رقم التأمين الوطني في المملكة المتحدة (NINO)](sit-defn-uk-national-insurance-number.md) </br> - [رقم خدمة الصحة الوطنية في المملكة المتحدة](sit-defn-uk-national-health-service-number.md) </br> - [رمز SWIFT](sit-defn-swift-code.md)|
|الخصوصية| تم تحسين قانون التهيين الأمريكي|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md)</br> - [العناوين الفعلية في الولايات المتحدة](sit-defn-us-physical-addresses.md)|
|الخصوصية| قانون الهمة الأمريكية|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)|
|الخصوصية| تحسين بيانات معلومات التعريف الشخصية (PII) في الولايات المتحدة|- [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sit-defn-us-uk-passport-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md)</br> - [العناوين الفعلية في الولايات المتحدة](sit-defn-us-physical-addresses.md)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في الولايات المتحدة|- [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sit-defn-us-individual-taxpayer-identification-number.md)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sit-defn-us-uk-passport-number.md)|
|الخصوصية| تم تحسين قوانين الإعلام بخرق الولاية الأمريكية|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> -[رقم رخصة القيادة الأمريكية](sit-defn-us-drivers-license-number.md) </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)</br> - [كافة الأسماء الكاملة](sit-defn-all-full-names.md) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sit-defn-us-uk-passport-number.md)</br> - [كافة الشروط والأحكام الطبية](sit-defn-all-medical-terms-conditions.md)|
|الخصوصية| قوانين الإعلام بخرق الولاية الأمريكية|- [رقم بطاقة الائتمان](sit-defn-credit-card-number.md) </br> - [رقم الحساب البنكي الأمريكي](sit-defn-us-bank-account-number.md)</br> -[رقم رخصة القيادة الأمريكية](sit-defn-us-drivers-license-number.md) </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)|
|الخصوصية| قوانين سرية رقم الضمان الاجتماعي للولايات المتحدة|- [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sit-defn-us-social-security-number.md)|

## <a name="locations"></a>مواقع

يمكن لنهج DLP العثور على العناصر التي تحتوي على معلومات حساسة عبر مواقع متعددة وحمايتها.

|موقع  |تضمين/استبعاد النطاق  |حالة البيانات  |متطلبات مسبقة إضافية |
|---------|---------|---------|---------|
|بريد Exchange الإلكتروني عبر الإنترنت |مجموعة التوزيع | البيانات في الحركة| لا |
|مواقع SharePoint عبر الإنترنت   |مواقع       | البيانات الثابتة </br> البيانات قيد الاستخدام | لا|
|حسابات OneDrive Entreprise| حساب أو مجموعة توزيع |البيانات الثابتة </br> البيانات قيد الاستخدام|لا|
|دردشة Teams ورسائل القناة     | حساب أو مجموعة توزيع |البيانات في الحركة </br> البيانات قيد الاستخدام |  لا       |
|Microsoft Defender for Cloud Apps   | مثيل تطبيق السحابة       |البيانات الثابتة         | - [استخدام نهج منع فقدان البيانات لتطبيقات السحابة غير التابعة ل Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|الاجهزه  |المستخدم أو المجموعة         |البيانات الثابتة </br>  البيانات قيد الاستخدام </br>  البيانات في الحركة         |- [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md) </br>- [البدء في منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md) </br>- [تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|المستودعات المحلية (مشاركات الملفات وSharePoint)    |مستودع         | البيانات الثابتة         | - [التعرف على الماسح الضوئي المحلي لمنع فقدان البيانات](dlp-on-premises-scanner-learn.md) </br> - [بدء استخدام الماسح الضوئي المحلي لمنع فقدان البيانات](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|Power BI| مساحات العمل | البيانات قيد الاستخدام | لا|

إذا اخترت تضمين مجموعات توزيع معينة في Exchange، فسيتم تحديد نطاق نهج DLP لأعضاء تلك المجموعة فقط. وبالمثل، فإن استبعاد مجموعة توزيع سيستبعد جميع أعضاء مجموعة التوزيع هذه من تقييم النهج. يمكنك اختيار تحديد نطاق نهج لأعضاء قوائم التوزيع ومجموعات التوزيع الديناميكي ومجموعات الأمان. لا يمكن أن يحتوي نهج DLP على أكثر من 50 من هذه التضمينات والاستثناءات.

إذا اخترت تضمين مواقع SharePoint أو حسابات OneDrive معينة أو استبعادها، فلا يمكن أن يحتوي نهج DLP على أكثر من 100 عملية تضمين واستثناءات. على الرغم من وجود هذا الحد، يمكنك تجاوز هذا الحد عن طريق تطبيق نهج على مستوى المؤسسة أو نهج ينطبق على مواقع بأكملها.

إذا اخترت تضمين حسابات أو مجموعات معينة في OneDrive أو استبعادها، فلا يمكن أن يحتوي نهج DLP على أكثر من 100 حساب مستخدم أو 50 مجموعة كتضمين أو استثناء.

### <a name="location-support-for-how-content-can-be-defined"></a>دعم الموقع لكيفية تعريف المحتوى

تكتشف نهج DLP العناصر الحساسة عن طريق مطابقتها بنوع معلومات حساسة (SIT) أو تسمية حساسية أو تسمية استبقاء. يدعم كل موقع أساليب مختلفة لتعريف المحتوى الحساس. عند دمج المواقع في نهج، يمكن تغيير كيفية تعريف المحتوى من كيفية تعريفه بواسطة موقع واحد. 

> [!IMPORTANT]
> عند تحديد مواقع متعددة لنهج ما، فإن قيمة "لا" لفئة تعريف المحتوى لها الأسبقية على القيمة "نعم". على سبيل المثال، عند تحديد مواقع SharePoint فقط، سيدعم النهج الكشف عن العناصر الحساسة بواسطة عنصر واحد أو أكثر من SIT، أو عن طريق وصف الحساسية، أو عن طريق تسمية الاستبقاء. ولكن، عند تحديد مواقع SharePoint ***ومواقع*** رسائل الدردشة والقنوات في Teams، سيدعم النهج اكتشاف العناصر الحساسة فقط بواسطة SIT.

|موقع| يمكن تعريف المحتوى بواسطة SIT| يمكن تعريف وصف الحساسية للمحتوى| يمكن تعريف المحتوى بواسطة تسمية الاستبقاء|
|---------|---------|---------|---------|
|بريد Exchange الإلكتروني عبر الإنترنت|نعم| نعم| لا|
|مواقع SharePoint عبر الإنترنت| نعم| نعم| نعم|
|حسابات OneDrive Entreprise| نعم| نعم| نعم|
|رسائل الدردشة والقناة في Teams | نعم| لا| لا|
|الاجهزه |نعم | نعم|  لا|
|Microsoft Defender for Cloud Apps | نعم| نعم| نعم|
|المستودعات المحلية| نعم| نعم| لا|
|Power BI|نعم | نعم| لا|

> [!NOTE]
> يدعم DLP (في المعاينة) استخدام المصنفات القابلة للتدريب كشرط للكشف عن المستندات الحساسة. يمكن تعريف المحتوى بواسطة المصنفات القابلة للتدريب في Exchange Online ومواقع Sharepoint Online وحسابات OneDrive Entreprise ودردشة Teams والقنوات والأجهزة. لمزيد من المعلومات، راجع [المصنفات القابلة للتدريب](classifier-learn-about.md).

> [!NOTE]
> يدعم DLP الكشف عن تسميات الحساسية على رسائل البريد الإلكتروني والمرفقات. لمزيد من المعلومات، راجع [استخدام تسميات الحساسية كشروط في نهج DLP](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>القواعد

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

القواعد هي منطق الأعمال لنهج DLP. وهي تتكون من:

- [**الشروط**](#conditions) التي عند مطابقتها، تؤدي إلى تشغيل النهج
- [**استثناءات**](#exceptions) الشروط
- [**الإجراءات التي**](#actions) يجب اتخاذها عند تشغيل النهج
- [**إعلامات المستخدم**](#user-notifications-and-policy-tips) لإعلام المستخدمين عند قيامهم بشيء ما يؤدي إلى تشغيل نهج والمساعدة في تعليمهم حول الطريقة التي تريد بها مؤسستك معاملة المعلومات الحساسة
- [**تجاوز المستخدم**](#user-overrides) عند تكوينه من قبل مسؤول، والسماح للمستخدمين بتجاوز إجراء حظر بشكل انتقائي
- [**تقارير الحوادث**](#incident-reports) التي تقوم بإعلام المسؤولين وأصحاب المصلحة الرئيسيين الآخرين عند حدوث تطابق للقاعدة
- [**خيارات إضافية**](#additional-options) تحدد أولوية تقييم القواعد ويمكن أن توقف المزيد من معالجة القواعد والنهج.

 يحتوي النهج على قاعدة واحدة أو أكثر. يتم تنفيذ القواعد بشكل تسلسلي، بدءا من قاعدة الأولوية العليا في كل نهج.

### <a name="the-priority-by-which-rules-are-processed"></a>الأولوية التي تتم بها معالجة القواعد

#### <a name="hosted-service-workloads"></a>أحمال عمل الخدمة المستضافة

بالنسبة إلى أحمال عمل الخدمة المستضافة، مثل Exchange Online وSharePoint Online OneDrive Entreprise، يتم تعيين أولوية لكل قاعدة بالترتيب الذي تم إنشاؤها به. وهذا يعني أن القاعدة التي تم إنشاؤها أولا لها الأولوية الأولى، والقاعدة التي تم إنشاؤها الثانية لها الأولوية الثانية، وهكذا.
  
![القواعد بترتيب الأولوية](../media/dlp-rules-in-priority-order.png)

عند تقييم المحتوى مقابل القواعد، تتم معالجة القواعد بترتيب الأولوية. إذا تطابق المحتوى مع قواعد متعددة، يتم فرض القاعدة الأولى التي تم تقييمها والتي تتضمن الإجراء *الأكثر* تقييدا. على سبيل المثال، إذا تطابق المحتوى مع جميع القواعد التالية، يتم فرض *القاعدة 3* لأنها القاعدة الأعلى أولوية والأكثر تقييدا:
  
- القاعدة 1: إعلام المستخدمين فقط
- القاعدة 2: إعلام المستخدمين، وتقييد الوصول، وتسمح بتجاوز المستخدم
- *القاعدة 3: إعلام المستخدمين وتقييد الوصول وعدم السماح بتجاوزات المستخدم*
- القاعدة 4: تقييد الوصول

سيتم تقييم القواعد 1 و2 و4، ولكن لن يتم تطبيقها. في هذا المثال، يتم تسجيل التطابقات لكافة القواعد في سجلات التدقيق وتظهر في تقارير DLP، على الرغم من تطبيق القاعدة الأكثر تقييدا فقط.

يمكنك استخدام قاعدة لتلبية متطلبات حماية معينة، ثم استخدام نهج DLP لتجميع متطلبات الحماية المشتركة معا، مثل جميع القواعد اللازمة للامتثال لائحة معينة.
  
على سبيل المثال، قد يكون لديك نهج DLP يساعدك على اكتشاف وجود المعلومات الخاضعة لقانون نقل التأمين الصحي والمساءلة (HIPAA). يمكن أن يساعد نهج DLP هذا في حماية بيانات HIPAA (ما) عبر جميع مواقع SharePoint Online وكافة مواقع OneDrive Entreprise (المكان) من خلال العثور على أي مستند يحتوي على هذه المعلومات الحساسة التي تتم مشاركتها مع أشخاص من خارج مؤسستك (الشروط) ثم حظر الوصول إلى المستند وإرسال إعلام (الإجراءات). يتم تخزين هذه المتطلبات كقواعد فردية وتجميعها معا كنهج DLP لتبسيط الإدارة وإعداد التقارير.
  
![يوضح الرسم التخطيطي أن نهج DLP يحتوي على مواقع وقواعد](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>لنقاط النهاية

كما يتم تعيين أولوية القواعد على نقاط النهاية وفقا للترتيب الذي تم إنشاؤها به. وهذا يعني أن القاعدة التي تم إنشاؤها أولا لها الأولوية الأولى، والقاعدة التي تم إنشاؤها الثانية لها الأولوية الثانية، وهكذا. 

عندما يتطابق ملف على نقطة نهاية مع نهج DLP متعددة، فإن القاعدة الأولى التي يتم تمكينها مع التطبيق الأكثر تقييدا على [أنشطة نقطة النهاية](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on) هي القاعدة التي يتم فرضها على المحتوى. على سبيل المثال، إذا تطابق المحتوى مع جميع القواعد التالية، فإن القاعدة 2 لها الأسبقية على القواعد الأخرى لأنها الأكثر تقييدا.

- القاعدة 1: تدقيق كافة الأنشطة فقط
- *القاعدة 2: حظر كافة الأنشطة*
- القاعدة 3: تمنع كافة الأنشطة مع خيار للمستخدم النهائي لتجاوز

في المثال أدناه، القاعدة 1 لها الأسبقية على القواعد المطابقة الأخرى لأنها الأكثر تقييدا.

- *القاعدة 1: تمنع النشاط ولا تسمح بتجاوز المستخدم*
- القاعدة 2: تمنع النشاط وتسمح بتجاوز المستخدم
- القاعدة 3: تدقيق كافة الأنشطة فقط
- القاعدة 4: عدم الإنفاذ

يتم تقييم جميع القواعد الأخرى ولكن لا يتم فرض إجراءاتها. ستظهر سجلات التدقيق القاعدة الأكثر تقييدا المطبقة على الملف. إذا كان هناك أكثر من قاعدة واحدة تتطابق وتكون مقيدة بنفس القدر، فإن أولوية النهج والقاعدة تحكم القاعدة التي سيتم تطبيقها على الملف.

### <a name="conditions"></a>الظروف

الشروط شاملة وهي المكان الذي تحدد فيه ما تريد أن تبحث عنه القاعدة والسياق الذي يتم فيه استخدام هذه العناصر. يخبرون القاعدة &#8212; عند العثور على عنصر يبدو مثل *هذا* ويتم استخدامه على *هذا* النحو &#8212; أنه مطابق ويجب اتخاذ بقية الإجراءات في النهج عليه. يمكنك استخدام الشروط لتعيين إجراءات مختلفة لمستويات مخاطر مختلفة. على سبيل المثال، قد يكون المحتوى الحساس المشترك داخليا أقل خطورة ويتطلب إجراءات أقل من المحتوى الحساس المشترك مع أشخاص من خارج المؤسسة.

> [!NOTE]
> يعتبر المستخدمون الذين لديهم حسابات غير ضيوف في Active Directory أو مستأجر Azure Active Directory للمؤسسة المضيفة أشخاصا داخل المؤسسة. 

#### <a name="content-contains"></a>يحتوي المحتوى على

 تحتوي كافة المواقع التي تدعم **المحتوى على** شرط. يمكنك تحديد مثيلات متعددة لكل نوع محتوى وتحسين الشروط بشكل أكبر باستخدام **أي من عوامل التشغيل هذه** (OR المنطقية) أو **كل هذه** (AND المنطقية):

- [أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [أوصاف الحساسية](sensitivity-labels.md)
- [تسميات الاستبقاء](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)
- [المصنفات القابلة للتدريب](classifier-learn-about.md) (في المعاينة) 

اعتمادا على [الموقع (المواقع)](#location-support-for-how-content-can-be-defined) التي تختار تطبيق النهج عليها.

ستبحث القاعدة فقط عن وجود أي **تسميات حساسية** **وتسميات استبقاء تختارها** .

لدى SITs [**مستوى ثقة**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) محدد مسبقا يمكنك تغييره إذا لزم الأمر. لمزيد من المعلومات، راجع [المزيد حول مستويات الثقة](sensitive-information-type-learn-about.md#more-on-confidence-levels).

> [!IMPORTANT]
> لدى SITs طريقتان مختلفتان لتحديد معلمات الحد الأقصى لعدد المثيلات الفريدة. لمعرفة المزيد، راجع [قيم عدد المثيلات المعتمدة ل SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>سياق الشرط

تتغير خيارات السياق المتوفرة استنادا إلى الموقع الذي تختاره. إذا حددت مواقع متعددة، فستتوفر الشروط المشتركة فقط.

##### <a name="conditions-exchange-supports"></a>يدعم تبادل الشروط

- يحتوي المحتوى على
- تتم مشاركة المحتوى من Microsoft 365
- يتم تلقي المحتوى من
- عنوان IP للمرسل هو
- قام المرسل بتجاوز تلميح النهج
- المرسل هو
- مجال المرسل هو
- يحتوي عنوان المرسل على كلمات
- يحتوي عنوان المرسل على أنماط
- تحتوي سمة AD للمرسل على كلمات أو عبارات
- سمة مرسل AD تتطابق مع الأنماط
- المرسل هو عضو في
- تعذر مسح محتوى أي مرفق بريد إلكتروني
- لم يكتمل مسح محتوى أي مرفق بريد إلكتروني
- المرفق محمي بكلمة مرور
- ملحق الملف هو
- المستلم عضو في
- مجال المستلم هو
- المستلم هو
- يحتوي عنوان المستلم على كلمات
- يتطابق عنوان المستلم مع الأنماط
- تحتوي سمة مستلم AD على كلمات أو عبارات
- تطابق سمة مستلم AD الأنماط
- يحتوي اسم المستند على كلمات أو عبارات
- اسم المستند يطابق الأنماط
- خاصية المستند هي
- حجم المستند يساوي أو أكبر من
- يحتوي محتوى المستند على كلمات أو عبارات
- يتطابق محتوى المستند مع الأنماط
- يحتوي الموضوع على كلمات أو عبارات
- أنماط مطابقة الموضوع
- يحتوي الموضوع أو النص الأساسي على كلمات أو عبارات
- نقوش مطابقة الموضوع أو النص الأساسي
- تحتوي مجموعة أحرف المحتوى على كلمات
- يحتوي الرأس على كلمات أو عبارات
- يطابق الرأس الأنماط
- حجم الرسالة يساوي أو أكبر من
- نوع الرسالة هو
- أهمية الرسالة هي

##### <a name="conditions-sharepoint-supports"></a>الشروط التي يدعمها SharePoint
 
- يحتوي المحتوى على
- تتم مشاركة المحتوى من Microsoft 365
- المستند الذي تم إنشاؤه بواسطة
- المستند الذي تم إنشاؤه بواسطة عضو في
- يحتوي اسم المستند على كلمات أو عبارات
- اسم المستند يطابق الأنماط
- تجاوز حجم المستند
- خاصية المستند هي
- ملحق الملف هو

##### <a name="conditions-onedrive-accounts-supports"></a>الشروط التي تدعمها حسابات OneDrive

- يحتوي المحتوى على
- تتم مشاركة المحتوى من Microsoft 365
- المستند الذي تم إنشاؤه بواسطة
- المستند الذي تم إنشاؤه بواسطة عضو في
- يحتوي اسم المستند على كلمات أو عبارات
- اسم المستند يطابق الأنماط
- تجاوز حجم المستند
- خاصية المستند هي
- ملحق الملف هو

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>تدعم دردشة Teams ورسائل القناة الشروط

- يحتوي المحتوى على
- تتم مشاركة المحتوى من Microsoft 365
- المرسل هو 
- مجال المرسل هو 
- مجال المستلم هو 
- المستلم هو 

##### <a name="conditions-devices-supports"></a>تدعم أجهزة الشروط

- يحتوي المحتوى على
- (معاينة) قام المستخدم بالوصول إلى موقع ويب حساس من Edge. راجع [السيناريو 6 مراقبة أنشطة المستخدم أو تقييدها على مجالات الخدمة الحساسة (معاينة)](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains-preview) لمزيد من المعلومات.
- ملحق الملف هو
- نوع الملف هو
- راجع [أنشطة نقطة النهاية التي يمكنك مراقبتها واتخاذ إجراء بشأنها](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>الشروط التي يدعمها Microsoft Defender for Cloud Apps

- يحتوي المحتوى على
- تتم مشاركة المحتوى من Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>تدعم المستودعات المحلية للشروط

- يحتوي المحتوى على
- ملحق الملف هو
- خاصية المستند هي

##### <a name="conditions-powerbi-supports"></a>الشروط التي يدعمها PowerBI

- يحتوي المحتوى على

#### <a name="condition-groups"></a>مجموعات الشروط

في بعض الأحيان تحتاج إلى قاعدة لتحديد شيء واحد فقط، مثل كل المحتوى الذي يحتوي على رقم الضمان الاجتماعي الأمريكي، والذي يتم تعريفه بواسطة SIT واحد. ولكن في العديد من السيناريوهات، حيث تكون أنواع العناصر التي تحاول تحديدها أكثر تعقيدا وبالتالي يصعب تحديدها، يلزم مزيد من المرونة في تحديد الشروط.

على سبيل المثال، لتحديد المحتوى الخاضع لقانون التأمين الصحي الأمريكي (HIPAA)، تحتاج إلى البحث عن:
  
- المحتوى الذي يحتوي على أنواع محددة من المعلومات الحساسة، مثل رقم الضمان الاجتماعي الأمريكي أو رقم وكالة إنفاذ الأدوية (DEA).
    
    و
    
- المحتوى الذي يصعب التعرف عليه، مثل الاتصالات حول رعاية المريض أو أوصاف الخدمات الطبية المقدمة. يتطلب تحديد هذا المحتوى مطابقة الكلمات الأساسية من قوائم الكلمات الأساسية الكبيرة، مثل التصنيف الدولي الأمراض (ICD-9-CM أو ICD-10-CM).
    
يمكنك تحديد هذا النوع من البيانات عن طريق تجميع الشروط واستخدام عوامل التشغيل المنطقية (AND، OR) بين المجموعات.
    
بالنسبة **إلى قانون التأمين الصحي (HIPPA) الأمريكي**، يتم تجميع الشروط كما يلي:

![شروط نهج HIPPA](../media/dlp-rules-condition-groups-booleans.png)

تحتوي المجموعة الأولى على SITs التي تحدد وفردا وتحتوي المجموعة الثانية على SITs التي تحدد التشخيص الطبي.

### <a name="exceptions"></a>الاستثناءات

في القواعد، تحدد الاستثناءات الشروط المستخدمة لاستبعاد عنصر من النهج. منطقيا، الشروط الحصرية التي يتم تقييمها بعد الشروط والسياق الشاملين. يخبرون القاعدة &#8212; عند العثور على عنصر يبدو مثل *هذا* ويتم استخدامه كما *لو* كان مطابقا ويجب اتخاذ بقية الإجراءات في النهج عليه ***إلا إذا***... &#8212; 

على سبيل المثال، وفقا لنهج HIPPA، يمكننا تعديل القاعدة لاستبعاد أي عنصر يحتوي على رقم ترخيص برامج تشغيل بلجيكا، مثل هذا:

![نهج HIPPA مع الاستثناءات](../media/dlp-rule-exceptions.png)

شروط الاستثناءات المعتمدة من قبل الموقع متطابقة مع كافة شروط التضمين مع الفرق الوحيد هو الاستباق "ما عدا إذا" لكل شرط مدعوم. إذا كانت القاعدة تحتوي على استثناءات فقط، فسيتم تطبيقها على كل رسائل البريد الإلكتروني أو الملفات التي لا تفي بمعايير الاستبعاد.

تماما كما تدعم جميع المواقع الشرط الشامل:

- يحتوي المحتوى على

سيكون الاستثناء:

- **باستثناء ما إذا كان** المحتوى يحتوي على 

### <a name="actions"></a>الاجراءات 

أي عنصر يجعلها من خلال عوامل تصفية ***conditions** _ _*_والاستثناءات_*_ الحصرية الشاملة سيكون له أي _*_إجراءات_*_ تم تعريفها في القاعدة المطبقة عليه. سيتعين عليك تكوين الخيارات المطلوبة لدعم الإجراء. على سبيل المثال، إذا قمت بتحديد Exchange باستخدام الإجراء _ *Restrict access أو encrypt the content in Microsoft 365 locations** تحتاج إلى الاختيار من بين هذه الخيارات:

- حظر المستخدمين من الوصول إلى محتوى SharePoint وOneDrive وTeams المشترك
    - حظر الجميع. سيظل مالك المحتوى والمعدل الأخير وإدارة الموقع فقط لديهم حق الوصول
    - حظر الأشخاص من خارج مؤسستك فقط. سيظل المستخدمون داخل مؤسستك يتمتعون بإمكانية الوصول.
- تشفير رسائل البريد الإلكتروني (ينطبق فقط على المحتوى في Exchange)

تعتمد الإجراءات المتوفرة في قاعدة على المواقع التي تم تحديدها. إذا حددت موقعا واحدا فقط للنهج الذي سيتم تطبيقه عليه، فسيتم سرد الإجراءات المتوفرة أدناه.

> [!IMPORTANT]
> بالنسبة إلى SharePoint Online ومواقع OneDrive Entreprise، سيتم حظر مستندات المواقع بشكل استباقي مباشرة بعد الكشف عن المعلومات الحساسة، بغض النظر عما إذا كان المستند مشتركا أم لا، لجميع المستخدمين الخارجيين، بينما سيستمر وصول المستخدمين الداخليين إلى المستند.

#### <a name="exchange-location-actions"></a>إجراءات موقع Exchange

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365
- تعيين الرؤوس
- إزالة الرأس
- إعادة توجيه الرسالة إلى مستخدمين محددين
- إعادة توجيه الرسالة للموافقة على مدير المرسل
- إعادة توجيه الرسالة للموافقة على موافقين محددين
- إضافة مستلم إلى المربع "إلى"
- إضافة مستلم إلى المربع "نسخة"
- إضافة مستلم إلى المربع "نسخة مخفية"
- إضافة مدير المرسل كمستلم
- تمت إزالة تشفير الرسائل O365 وحماية الحقوق
- موضوع البريد الإلكتروني السابق
- تعديل موضوع البريد الإلكتروني
- إضافة إخلاء مسؤولية HTML

#### <a name="sharepoint-sites-location-actions"></a>إجراءات موقع مواقع SharePoint

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365

#### <a name="onedrive-account-location-actions"></a>إجراءات موقع حساب OneDrive

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365

#### <a name="teams-chat-and-channel-messages-actions"></a>إجراءات دردشة Teams ورسائل القناة

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365

#### <a name="devices-actions"></a>إجراءات الأجهزة

<!-- - Restrict access or encrypt the content in Microsoft 365 locations-->
- (معاينة) تدقيق الأنشطة أو تقييدها عندما يصل المستخدمون إلى مواقع الويب الحساسة في مستعرض Microsoft Edge على أجهزة Windows. راجع [السيناريو 6 مراقبة أنشطة المستخدم أو تقييدها على مجالات الخدمة الحساسة (معاينة)](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains-preview) لمزيد من المعلومات.
- تدقيق الأنشطة أو تقييدها على أجهزة Windows

للاستخدام `Audit or restrict activities on Windows devices`، يجب تكوين الخيارات في **إعدادات DLP** وفي النهج الذي تريد استخدامها فيه. لمزيد من المعلومات، راجع [التطبيقات المقيدة ومجموعات التطبيقات](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) .

يوفر موقع الأجهزة العديد من النشاطات الفرعية (الشروط) والإجراءات. لمعرفة المزيد، راجع [أنشطة نقطة النهاية التي يمكنك مراقبتها واتخاذ إجراء بشأنها](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on).

عند تحديد **التدقيق أو تقييد الأنشطة على أجهزة Windows**، يمكنك تقييد أنشطة المستخدم حسب مجال الخدمة أو المستعرض، وتحديد نطاق الإجراءات التي يتخذها DLP من خلال:

- جميع التطبيقات
- حسب قائمة التطبيقات المقيدة التي تحددها
- مجموعة تطبيقات مقيدة (معاينة) تقوم بتعريفها.

##### <a name="service-domain-and-browser-activities"></a>مجال الخدمة وأنشطة المستعرض

عند تكوين **مجالات خدمة السحابة السماح/الحظر** وقائمة **المستعرضات غير المسموح بها** (راجع [قيود المستعرض والمجال على البيانات الحساسة](dlp-configure-endpoint-settings.md#browser-and-domain-restrictions-to-sensitive-data)) ويحاول المستخدم تحميل ملف محمي إلى مجال خدمة سحابية أو الوصول إليه من مستعرض غير مسموح به، يمكنك تكوين إجراء النهج إلى `Audit only`أو `Block with override`أو `Block` النشاط.

##### <a name="file-activities-for-all-apps"></a>أنشطة الملفات لكافة التطبيقات

باستخدام خيار **"أنشطة الملف" لكافة التطبيقات** ، يمكنك تحديد إما **عدم تقييد أنشطة الملف** أو **تطبيق قيود على أنشطة معينة**. عند تحديد تطبيق قيود على أنشطة معينة، يتم تطبيق الإجراءات التي تحددها هنا عندما يصل مستخدم إلى عنصر محمي من DLP. يمكنك إخبار DLP إلى `Audit only`، `Block with override`( `Block` الإجراءات) على أنشطة المستخدم هذه:

- **نسخ إلى الحافظة**
- **نسخ إلى محرك أقراص USB قابل للإزالة** 
- **نسخ إلى مشاركة شبكة**
- **طباعه**
- **النسخ أو النقل باستخدام تطبيق Bluetooth غير مسموح به**
- **خدمات سطح المكتب البعيد**


##### <a name="restricted-app-activities"></a>أنشطة التطبيق المقيدة  

تسمى سابقا تطبيقات غير مسموح بها، يمكنك تحديد قائمة التطبيقات في إعدادات DLP لنقطة النهاية التي تريد وضع قيود عليها. عندما يحاول مستخدم الوصول إلى ملف محمي ب DLP باستخدام تطبيق موجود في القائمة، يمكنك إما `Audit only`، `Block with override`أو ، أو `Block` النشاط. يتم تجاوز إجراءات DLP المحددة في **أنشطة التطبيق المقيدة** إذا كان التطبيق عضوا في مجموعة التطبيقات المقيدة. ثم يتم تطبيق الإجراءات المحددة في مجموعة التطبيقات المقيدة.

##### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>أنشطة الملفات للتطبيقات في مجموعات التطبيقات المقيدة (معاينة)

يمكنك تحديد مجموعات التطبيقات المقيدة في إعدادات DLP لنقطة النهاية وإضافة مجموعات التطبيقات المقيدة إلى نهجك. عند إضافة مجموعة تطبيقات مقيدة إلى نهج، يجب تحديد أحد الخيارات التالية:

- عدم تقييد نشاط الملف
- تطبيق قيود على كافة الأنشطة
- تطبيق قيود على نشاط معين

عند تحديد أي من خيارات *"تطبيق القيود* "، ويحاول المستخدم الوصول إلى ملف محمي ب DLP باستخدام تطبيق موجود في مجموعة التطبيقات المقيدة، يمكنك إما `Audit only`، `Block with override`أو ، أو `Block` حسب النشاط. تتجاوز إجراءات DLP التي تحددها هنا الإجراءات المحددة في **أنشطة التطبيقات المقيدة** **وأنشطة الملف لجميع التطبيقات** للتطبيق.

لمزيد من المعلومات، راجع [التطبيقات المقيدة ومجموعات التطبيقات](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) . 

#### <a name="microsoft-defender-for-cloud-apps-actions"></a>إجراءات Microsoft Defender for Cloud Apps

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365
- تقييد تطبيقات الجهات الخارجية

#### <a name="on-premises-repositories-actions"></a>إجراءات المستودعات المحلية

- تقييد الوصول إلى الملفات المحلية أو إزالتها

#### <a name="powerbi-actions"></a>إجراءات PowerBI

- إعلام المستخدمين بتلميحات حول البريد الإلكتروني والنهج
- إرسال تنبيهات إلى المسؤول

#### <a name="actions-available-when-you-combine-locations"></a>الإجراءات المتوفرة عند دمج المواقع

إذا قمت بتحديد Exchange وأي موقع واحد آخر للنهج الذي سيتم تطبيقه عليه،

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365

و

- كافة الإجراءات لموقع غير Exchange

ستكون الإجراءات متوفرة.

إذا قمت بتحديد موقعين أو أكثر من المواقع غير المشتركة في Exchange للنهج الذي سيتم تطبيقه عليه،

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365

و

- كافة الإجراءات للمواقع غير الخاصة ب Exchange 

ستكون الإجراءات متوفرة.

على سبيل المثال، إذا حددت Exchange والأجهزة كمواقع، فستتوفر هذه الإجراءات:

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365
- تدقيق الأنشطة أو تقييدها على أجهزة Windows

إذا قمت بتحديد الأجهزة Microsoft Defender for Cloud Apps، فستتوفر هذه الإجراءات:

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365
- تدقيق الأنشطة أو تقييدها على أجهزة Windows
- تقييد تطبيقات الجهات الخارجية

يعتمد ما إذا كان الإجراء ساري المفعول أم لا على كيفية تكوين وضع النهج. يمكنك اختيار تشغيل النهج في وضع الاختبار مع إظهار تلميح النهج أو بدونه عن طريق تحديد الخيار **الأول "اختباره".** يمكنك اختيار تشغيل النهج بمجرد ساعة بعد إنشائه عن طريق تحديد الخيار **"تشغيلها على الفور** "، أو يمكنك اختيار حفظه فقط والعودة إليه لاحقا عن طريق تحديد الخيار **"إيقاف تشغيله** ". 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>إعلامات المستخدم وتلميحات النهج

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

عندما يحاول مستخدم إجراء على عنصر حساس في سياق يفي بشروط القاعدة واستثناءاتها، يمكنك إعلامه بذلك من خلال رسائل البريد الإلكتروني الخاصة بإعلام المستخدم وفي التلميحات المنبثقة لنهج السياق. تعد هذه الإعلامات مفيدة لأنها تزيد من الوعي وتساعد على تعليم الأشخاص نهج DLP الخاصة بمؤسستك.

على سبيل المثال، محتوى مثل مصنف Excel على موقع OneDrive Entreprise يحتوي على معلومات تعريف شخصية (PII) تتم مشاركتها مع ضيف.

![يعرض شريط الرسائل تلميح النهج في Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!IMPORTANT]
> - يتم إرسال رسائل البريد الإلكتروني للإعلام بدون حماية.
> - يتم دعم إعلامات البريد الإلكتروني لخدمات Microsoft 365 فقط.

#### <a name="email-notifications-support-by-selected-location"></a>دعم إعلامات البريد الإلكتروني حسب الموقع المحدد

|الموقع المحدد  |إعلامات البريد الإلكتروني المدعومة  |
|---------|---------|
|الاجهزه     |- غير معتمد         |
|Exchange + الأجهزة     |- معتمد ل Exchange </br>- غير معتمد للأجهزة  |
|Exchange    |- معتمد        |
|SharePoint + الأجهزة  |- معتمد ل SharePoint </br>- غير معتمد للأجهزة         |
|SharePoint    |- معتمد |
|Exchange + SharePoint    |- معتمد ل Exchange </br>- معتمد ل SharePoint  |
|الأجهزة + SharePoint + Exchange    |- غير معتمد للأجهزة </br>- معتمد ل SharePoint </br> معتمد ل Exchange |
|الفرق    |- غير معتمد |
|OneDrive for Business   |- معتمد         |
|OneDrive Entreprise + الأجهزة     |- مدعوم ل OneDrive Entreprise </br>- غير معتمد للأجهزة         |
|Power-BI|- غير معتمد|
|Microsoft Defender for Cloud Apps|- غير معتمد|
|المستودعات المحلية|- غير معتمد|

يمكنك أيضا منح الأشخاص خيار [تجاوز النهج](#user-overrides)، بحيث لا يتم حظرهم إذا كانت لديهم حاجة عمل صالحة أو إذا كان النهج يكشف عن إيجابية خاطئة.

تختلف خيارات تكوين إعلامات المستخدم وتلميحات النهج استنادا إلى مواقع المراقبة التي حددتها. إذا قمت بتحديد:

- Exchange
- SharePoint
- OneDrive
- الدردشة والقناة في Teams
- Defender for Cloud Apps





يمكنك تمكين/تعطيل إعلامات المستخدم لتطبيقات Microsoft المختلفة، راجع [مرجع تلميحات نهج منع فقدان البيانات](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- يمكنك تمكين/تعطيل الإعلامات باستخدام تلميح نهج.
    - إعلامات البريد الإلكتروني للمستخدم الذي أرسل المحتوى أو شاركه أو عدله آخر مرة
    - إعلام أشخاص محددين

وتخصيص نص البريد الإلكتروني والموضوع ونص تلميح النهج.

![خيارات تكوين تلميح إعلام المستخدم والنهج المتوفرة ل Exchange وSharePoint وOneDrive وTeams Chat و Channel و Defender for Cloud Apps](../media/dlp-user-notification-non-devices.png)

إذا حددت الأجهزة فقط، فستحصل على جميع الخيارات نفسها المتوفرة ل Exchange وSharePoint وOneDrive وTeams Chat و Channel و Defender for Cloud Apps بالإضافة إلى خيار تخصيص عنوان الإعلام والمحتوى الذي يظهر على جهاز Windows 10.

![إعلام المستخدم وخيارات تكوين تلميح النهج المتوفرة للأجهزة](../media/dlp-user-notification-devices.png)  

يمكنك تخصيص عنوان النص ونصه باستخدام هذه المعلمات. يدعم النص الأساسي ما يلي:

|الاسم الشائع  |المعلمه  |المثال
|---------|---------|---------|
|اسم الملف     |٪٪FileName٪٪ | مستند Contoso 1 |
|اسم العملية     |٪٪ProcessName٪٪ | Word |
|اسم النهج     |٪٪PolicyName٪٪| Contoso سري للغاية |
|العمل | ٪٪AppliedActions٪٪ | لصق محتوى المستند من الحافظة إلى تطبيق آخر |

**يستبدل ٪٪AppliedActions٪٪** هذه القيم في نص الرسالة:


|اسم الإجراء الشائع |قيمة بديلة للمعلمة ٪٪AppliedActions٪٪ |
|---------|---------|
|نسخ إلى تخزين قابل للإزالة    |*الكتابة إلى مساحة تخزين قابلة للإزالة*         |
|نسخ إلى مشاركة الشبكة     |*الكتابة إلى مشاركة شبكة*         |
|طباعه     |*الطباعه*         |
|لصق من الحافظة  |*اللصق من الحافظة*         |
|نسخ عبر bluetooth   |*النقل عبر Bluetooth*         |
|فتح باستخدام تطبيق غير مسموح به     |*فتح مع هذا التطبيق*         |
|نسخ إلى سطح مكتب بعيد (RDP)     |*يتم الآن النقل إلى سطح المكتب البعيد*         |
|التحميل إلى موقع ويب غير مسموح به     |*التحميل إلى هذا الموقع*         |
|الوصول إلى العنصر عبر مستعرض غير مسموح به     |*فتح باستخدام هذا المستعرض*         |

استخدام هذا النص المخصص

*٪٪AppliedActions٪٪ اسم الملف ٪٪FileName٪٪ عبر ٪٪ProcessName٪٪ غير مسموح به من قبل مؤسستك. انقر فوق "السماح" إذا كنت تريد تجاوز النهج ٪٪PolicyName٪٪* 

ينتج هذا النص في الإعلام المخصص:

*اللصق من اسم ملف الحافظة: لا تسمح مؤسستك بلصق مستند Contoso 1 عبر WINWORD.EXE. انقر فوق الزر "السماح" إذا كنت تريد تجاوز النهج Contoso سري للغاية*
 

> [!NOTE]
> إعلامات المستخدم وتلميحات النهج غير متوفرة للموقع المحلي

> [!NOTE]
> سيتم عرض تلميح النهج فقط من أعلى أولوية، القاعدة الأكثر تقييدا. على سبيل المثال، سيتم عرض تلميح نهج من قاعدة تمنع الوصول إلى المحتوى عبر تلميح نهج من قاعدة ترسل إشعارا ببساطة. وهذا يمنع الأشخاص من رؤية تتالي تلميحات النهج.

لمعرفة المزيد حول إعلام المستخدم وتكوين تلميح النهج واستخدامه، بما في ذلك كيفية تخصيص الإعلام ونص التلميح، راجع 
- [إرسال إعلامات بالبريد الإلكتروني وإظهار تلميحات النهج لنهج DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies).
  
<!--The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.
  
In addition to sending an email notification, a user notification displays a policy tip:
  
- In Outlook and Outlook on the web.
    
- For the document on a SharePoint Online or OneDrive for Business site.
    
- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.
    
The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.
  
Here's what a policy tip looks like in a OneDrive for Business account.
  
![Policy tip for a document in a OneDrive account](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.
-->

#### <a name="blocking-and-notifications-in-sharepoint-online-and-onedrive-for-business"></a>الحظر والإعلامات في SharePoint Online OneDrive Entreprise

يعرض هذا الجدول سلوك حظر DLP وإعلامات النهج التي تم تحديد نطاقها إلى SharePoint Online OneDrive Entreprise.

|الظروف  |تكوين الإجراءات |تكوين إعلام المستخدم|تكوين تقارير الحوادث |سلوك الحظر والإعلام|
|---------|---------|---------|---------|---------|
|- **تتم مشاركة المحتوى من Microsoft 365** </br>- **مع أشخاص من خارج مؤسستي**     |لم يتم تكوين أي إجراءات         |- **تعيين إعلامات المستخدم** إلى **"تشغيل**" </br>- **إعلام المستخدمين في خدمة Office 365 بتلميح نهج** محدد </br>- **إعلام المستخدم الذي أرسل المحتوى أو شاركه أو قام آخر تعديل له بتحديده**         |- **إرسال تنبيه إلى المسؤولين عند تعيين تطابق قاعدة** إلى **"تشغيل**" </br>- **إرسال تنبيه في كل مرة يتطابق فيها نشاط مع القاعدة المعينة** إلى **"تشغيل"** </br>- **استخدام تقارير حوادث البريد الإلكتروني لإعلامك عند تعيين تطابق نهج** إلى **On**         |- سيتم إرسال الإعلامات فقط عند مشاركة ملف مع مستخدم خارجي والوصول إلى الملف من قبل مستخدم خارجي.  |
|- **تتم مشاركة المحتوى من Microsoft 365** </br>- **فقط مع أشخاص داخل مؤسستي**        | لم يتم تكوين أي إجراءات         |-  **تعيين إعلامات المستخدم** إلى **"تشغيل**"   </br>- **إعلام المستخدمين في خدمة Office 365 بتلميح نهج** محدد  </br>- **إعلام المستخدم الذي أرسل المحتوى أو شاركه أو قام آخر تعديل له بتحديده**    |  - **إرسال تنبيه إلى المسؤولين عند تعيين تطابق قاعدة** إلى **"تشغيل**" </br>- **إرسال تنبيه في كل مرة يتطابق فيها نشاط مع القاعدة** المحددة </br>- **استخدام تقارير حوادث البريد الإلكتروني لإعلامك عند تعيين تطابق نهج** إلى **On**       |- يتم إرسال الإعلامات عند تحميل ملف |
|- **تتم مشاركة المحتوى من Microsoft 365** </br>- **مع أشخاص من خارج مؤسستي**    | - **تم تحديد تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365** </br>- **حظر المستخدمين من تلقي البريد الإلكتروني أو الوصول إلى ملفات SharePoint وOneDrive وTeams المشتركة** المحددة </br>- **تحديد حظر الأشخاص من خارج مؤسستك فقط**          |- **تعيين إعلامات المستخدم** إلى **"تشغيل**" </br>- **إعلام المستخدمين في خدمة Office 365 بتلميح نهج** محدد </br>- **إعلام المستخدم الذي أرسل المحتوى أو شاركه أو قام آخر تعديل له بتحديده**  |  - **إرسال تنبيه إلى المسؤولين عند تعيين تطابق قاعدة** إلى **"تشغيل**" </br>- **إرسال تنبيه في كل مرة يتطابق فيها نشاط مع القاعدة** المحددة </br>- **استخدام تقارير حوادث البريد الإلكتروني لإعلامك عند تعيين تطابق نهج** إلى **On**             | - يتم حظر الوصول إلى ملف حساس بمجرد تحميله </br>- الإعلامات المرسلة عند مشاركة المحتوى من Microsoft 365 مع أشخاص من خارج مؤسستي         |
|- **تتم مشاركة المحتوى من Microsoft 365** </br>- **مع أشخاص من خارج مؤسستي** |  - **تم تحديد تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365** </br>- **حظر المستخدمين من تلقي البريد الإلكتروني أو الوصول إلى ملفات SharePoint وOneDrive وTeams المشتركة** المحددة </br>- **تم تحديد حظر الجميع**        | - **تعيين إعلامات المستخدم** إلى **"تشغيل**" </br>- **إعلام المستخدمين في خدمة Office 365 بتلميح نهج** محدد </br>- **إعلام المستخدم الذي أرسل المحتوى أو شاركه أو قام آخر تعديل له بتحديده**         | - **إرسال تنبيه إلى المسؤولين عند تعيين تطابق قاعدة** إلى **"تشغيل**" </br>- **إرسال تنبيه في كل مرة يتطابق فيها نشاط مع القاعدة** المحددة </br>- **استخدام تقارير حوادث البريد الإلكتروني لإعلامك عند تعيين تطابق نهج** إلى **On**        |يتم إرسال الإعلامات عند مشاركة ملف مع مستخدم خارجي ووصول مستخدم خارجي إلى هذا الملف.         |
|- **تتم مشاركة المحتوى من Microsoft 365** </br>- **مع أشخاص من خارج مؤسستي**     |- **تم تحديد تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365** </br>- **حظر الأشخاص الذين تم منحهم حق الوصول إلى المحتوى فقط من خلال الخيار "أي شخص لديه الارتباط".**         |  - **تعيين إعلامات المستخدم** إلى **"تشغيل**" </br>- **يتم تحديد إعلام المستخدمين في خدمة Office 365 بتلميح نهج**.  </br>- **إعلام المستخدم الذي أرسل المحتوى أو شاركه أو قام آخر تعديل له بتحديده**     |- **إرسال تنبيه إلى المسؤولين عند تعيين تطابق قاعدة** إلى **"تشغيل**"   </br>- **إرسال تنبيه في كل مرة يتطابق فيها نشاط مع القاعدة** المحددة </br>- **استخدام تقارير حوادث البريد الإلكتروني لإعلامك عند تعيين تطابق نهج** إلى **On**       |يتم إرسال الإعلامات بمجرد تحميل ملف         |


### <a name="user-overrides"></a>تجاوز المستخدم

الهدف من **تجاوز المستخدم** هو منح المستخدمين طريقة لتجاوز إجراءات حظر نهج DLP، مع ضبطها، على العناصر الحساسة في Exchange أو SharePoint أو OneDrive أو Teams حتى يتمكنوا من متابعة عملهم. يتم تمكين تجاوزات المستخدم فقط عند **تمكين إعلام المستخدمين في خدمات Office 365 بتلميح النهج**، لذا فإن عمليات تجاوز المستخدم تنتقل جنبا إلى جنب مع الإعلامات وتلميحات النهج. 

![خيارات تجاوز المستخدم لنهج DLP](../media/dlp-user-overrides.png)

> [!NOTE]
> لا تتوفر عمليات تجاوز المستخدم لموقع المستودعات المحلية.

عادة ما تكون عمليات تجاوز المستخدم مفيدة عندما تقوم مؤسستك بنشر نهج لأول مرة. تساعد التعليقات التي تحصل عليها من أي مبررات تجاوز وتحديد الإيجابيات الخاطئة في ضبط النهج. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- إذا كانت تلميحات النهج في القاعدة الأكثر تقييدا تسمح للأشخاص بتجاوز القاعدة، فإن تجاوز هذه القاعدة يتجاوز أيضا أي قواعد أخرى طابقها المحتوى.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
لمعرفة المزيد حول تجاوزات المستخدم، راجع:

- [عرض الضبط المرسل من قبل مستخدم لتجاوز](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>تقارير الحوادث

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

عند مطابقة قاعدة، يمكنك إرسال تقرير عن الحادث إلى مسؤول الامتثال (أو أي أشخاص تختارهم) مع تفاصيل الحدث. يتضمن التقرير معلومات حول العنصر الذي تمت مطابقته والمحتوى الفعلي الذي طابق القاعدة واسم الشخص الذي أجرى آخر تعديل للمحتوى. بالنسبة لرسائل البريد الإلكتروني، يتضمن التقرير أيضا الرسالة الأصلية التي تتطابق مع نهج DLP كمرفق.

يقوم DLP بتغذية معلومات الحادث إلى خدمات حماية معلومات Microsoft Purview الأخرى، مثل [إدارة المخاطر الداخلية](insider-risk-management.md). من أجل الحصول على معلومات الحادث إلى إدارة المخاطر الداخلية، يجب تعيين مستوى خطورة **تقارير الحوادث** إلى **مستوى عال**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

يمكن إرسال التنبيهات في كل مرة يتطابق فيها النشاط مع قاعدة، والتي يمكن أن تكون صاخبة أو يمكن تجميعها في تنبيهات أقل استنادا إلى عدد التطابقات أو حجم العناصر على مدى فترة زمنية محددة.

![إرسال تنبيه في كل مرة تتطابق فيها القاعدة أو تجمعها بمرور الوقت في تقارير أقل](../media/dlp-incident-reports-aggregation.png)

يقوم DLP بمسح البريد الإلكتروني بطريقة مختلفة عن تلك التي يقوم بها SharePoint Online أو OneDrive Entreprise العناصر. في SharePoint Online و OneDrive Entreprise، يقوم DLP بفحص العناصر الموجودة بالإضافة إلى العناصر الجديدة وإنشاء تقرير عن الحادث كلما تم العثور على تطابق. في Exchange Online، يقوم DLP بفحص رسائل البريد الإلكتروني الجديدة فقط وإنشاء تقرير إذا كان هناك تطابق في النهج. ***لا*** يقوم DLP بمسح عناصر البريد الإلكتروني الموجودة مسبقا المخزنة في علبة بريد أو أرشيف أو مطابقتها.

### <a name="additional-options"></a>خيارات إضافية

إذا كان لديك قواعد متعددة في نهج، يمكنك استخدام **الخيارات الإضافية** للتحكم في معالجة القواعد الإضافية إذا كان هناك تطابق مع القاعدة التي تقوم بتحريرها بالإضافة إلى تعيين الأولوية لتقييم القاعدة.

## <a name="see-also"></a>راجع أيضًا

- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
