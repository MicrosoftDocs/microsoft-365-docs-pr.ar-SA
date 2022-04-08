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
ms.openlocfilehash: d6bc24f313d1998979a460bcd41e87ccbe8abc5c
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/07/2022
ms.locfileid: "64704912"
---
# <a name="data-loss-prevention-policy-reference"></a>مرجع نهج تفادي فقدان البيانات

تحتوي نهج منع فقدان البيانات (DLP) على العديد من المكونات التي يجب تكوينها. لإنشاء نهج فعال، تحتاج إلى فهم الغرض من كل مكون وكيف يغير تكوينه سلوك النهج. توفر هذه المقالة تشريحا مفصلا لنهج DLP.

## <a name="policy-templates"></a>قوالب النهج 

يتم فرز قوالب نهج DLP مسبقا إلى أربع فئات:

- تلك التي يمكنها الكشف عن أنواع المعلومات **المالية** وحمايتها.
- تلك التي يمكنها الكشف عن أنواع المعلومات **الطبية والصحة** وحمايتها.
- تلك التي يمكنها اكتشاف أنواع معلومات **الخصوصية** وحمايتها.
- قالب **مخصص** يمكنك استخدامه لإنشاء نهج خاص بك إذا كان أحد القوالب الأخرى لا يلبي احتياجات مؤسستك.

يسرد هذا الجدول كافة قوالب النهج وأنواع المعلومات الحساسة (SIT) التي تغطيها. 

محدث: 06/23/2021

|الفئة| قالب | الجلوس |
|---------|---------|---------|
|الماليه| بيانات أستراليا المالية| - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم ملف الضريبة في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم الحساب البنكي في أستراليا](sensitive-information-type-entity-definitions.md#australia-bank-account-number) </br> - [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|الماليه| البيانات المالية لكندا |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي في كندا](sensitive-information-type-entity-definitions.md#canada-bank-account-number)|
|الماليه| بيانات فرنسا المالية |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|الماليه| البيانات المالية في ألمانيا |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|الماليه| البيانات المالية في إسرائيل |- [رقم الحساب البنكي في إسرائيل](sensitive-information-type-entity-definitions.md#israel-bank-account-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|الماليه| البيانات المالية اليابانية |- [رقم الحساب البنكي الياباني](sensitive-information-type-entity-definitions.md#japan-bank-account-number) </br> - [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|الماليه| PCI Data Security Standard (PCI DSS)|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|الماليه| قانون مكافحة الجريمة الإلكترونية في المملكة العربية السعودية|- [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم الحساب المصرفي الدولي (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban) |
|الماليه| البيانات المالية في المملكة العربية السعودية |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم الحساب المصرفي الدولي (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban)|
|الماليه| البيانات المالية في المملكة المتحدة|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|الماليه| البيانات المالية الأمريكية|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم توجيه ABA](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|الماليه| قواعد المستهلك في لجنة التجارة الفيدرالية (FTC) في الولايات المتحدة|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم توجيه ABA](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|الماليه| U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> -[رقم رخصة القيادة الأمريكية](sensitive-information-type-entity-definitions.md#us-drivers-license-number)</br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|الماليه| قانون Gramm-Leach-Bliley (GLBA) الأمريكي|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|الرعاية الطبية والصحة| قانون السجلات الصحية في أستراليا (قانون HRIP) محسن |- [رقم ملف الضريبة في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم الحساب الطبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-medical-account-number) </br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [كافة الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [العناوين المادية في أستراليا](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|الرعاية الطبية والصحة| قانون السجلات الصحية في أستراليا (قانون HRIP)|- [رقم ملف الضريبة في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم الحساب الطبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-medical-account-number)|
|الرعاية الطبية والصحة| قانون المعلومات الصحية في كندا (HIA) |- [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم التعريف الصحي الشخصي لكندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الرعاية الطبية والصحة| قانون المعلومات الصحية الشخصية (PHIA) مانيتوبا في كندا|- [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم التعريف الصحي الشخصي لكندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الرعاية الطبية والصحة| قانون الصحة الشخصية في كندا (PHIPA) في كندا |- [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم التعريف الصحي الشخصي لكندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الرعاية الطبية والصحة| بريطانيا. قانون الوصول إلى التقارير الطبية|- [رقم خدمة الصحة الوطنية في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [رقم التأمين الوطني في المملكة المتحدة (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino)|
|الرعاية الطبية والصحة| قانون التأمين الصحي (HIPAA) المحسن في الولايات المتحدة|</br> - [التصنيف الدولي الأمراض (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [التصنيف الدولي الأمراض (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm) </br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [كافة الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|الرعاية الطبية والصحة| قانون التأمين الصحي الأمريكي (HIPAA)| - [التصنيف الدولي الأمراض (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [التصنيف الدولي الأمراض (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm)|
|الخصوصية| قانون الخصوصية في أستراليا المحسن|- [رقم رخصة القيادة في أستراليا](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [رقم جواز سفر أستراليا](sensitive-information-type-entity-definitions.md#australia-passport-number) </br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [كافة الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [العناوين المادية في أستراليا](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|الخصوصية| قانون الخصوصية في أستراليا|- [رقم رخصة القيادة في أستراليا](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [رقم جواز سفر أستراليا](sensitive-information-type-entity-definitions.md#australia-passport-number)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في أستراليا|- [رقم ملف الضريبة في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم رخصة القيادة في أستراليا](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في كندا|- [رقم رخصة القيادة في كندا](sensitive-information-type-entity-definitions.md#canada-drivers-license-number)</br> - [رقم الحساب البنكي في كندا](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم التعريف الصحي الشخصي لكندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الخصوصية| قانون حماية البيانات الشخصية في كندا (PIPA)|- [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم التعريف الصحي الشخصي لكندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الخصوصية| قانون حماية البيانات الشخصية في كندا (PIPEDA)|- [رقم رخصة القيادة في كندا](sensitive-information-type-entity-definitions.md#canada-drivers-license-number) </br> - [رقم الحساب البنكي في كندا](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم التعريف الصحي الشخصي لكندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الخصوصية| قانون حماية البيانات في فرنسا|- [بطاقة المعرف الوطنية الفرنسية (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni) </br> - [رقم الضمان الاجتماعي (INSEE) في فرنسا](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في فرنسا|- [رقم الضمان الاجتماعي (INSEE) في فرنسا](sensitive-information-type-entity-definitions.md#france-social-security-number-insee) </br> - [رقم رخصة القيادة في فرنسا](sensitive-information-type-entity-definitions.md#france-drivers-license-number) </br> - [رقم جواز سفر فرنسا](sensitive-information-type-entity-definitions.md#france-passport-number) </br> - [بطاقة المعرف الوطنية الفرنسية (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)|
|الخصوصية| القانون العام لحماية البيانات (GDPR) المحسن|- [العناوين المادية في النمسا](sensitive-information-type-entity-definitions.md#austria-physical-addresses) </br> - [عناوين فعلية لبلينيا](sensitive-information-type-entity-definitions.md#belgium-physical-addresses)</br> - [العناوين المادية لبلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-physical-addresses)</br> - [العناوين المادية لكرواتيا](sensitive-information-type-entity-definitions.md#croatia-physical-addresses)</br> - [العناوين المادية للكواية](sensitive-information-type-entity-definitions.md#cyprus-physical-addresses)</br> - [العناوين المادية للتشيك](sensitive-information-type-entity-definitions.md#czech-republic-physical-addresses)</br> - [عناوين الدانمارك المادية](sensitive-information-type-entity-definitions.md#denmark-physical-addresses)</br> - [العناوين المادية ل الإستونية](sensitive-information-type-entity-definitions.md#estonia-physical-addresses)</br> - [العناوين المادية ل فنلندا](sensitive-information-type-entity-definitions.md#finland-physical-addresses)</br> - [عناوين فرنسا الفعلية](sensitive-information-type-entity-definitions.md#france-physical-addresses)</br> - [العناوين الفعلية في ألمانيا](sensitive-information-type-entity-definitions.md#germany-physical-addresses)</br> - [العناوين المادية في اليونان](sensitive-information-type-entity-definitions.md#greece-physical-addresses)</br> - [العناوين المادية في المجر](sensitive-information-type-entity-definitions.md#hungary-physical-addresses)</br> - [عناوين أيرلندا المادية](sensitive-information-type-entity-definitions.md#ireland-physical-addresses)</br> - [العناوين المادية في إيطاليا](sensitive-information-type-entity-definitions.md#italy-physical-addresses)</br> - [عناوين لاتفيا المادية](sensitive-information-type-entity-definitions.md#latvia-physical-addresses)</br> - [العناوين المادية ليتوانية](sensitive-information-type-entity-definitions.md#lithuania-physical-addresses)</br> - [العناوين المادية لكسمبورج](sensitive-information-type-entity-definitions.md#luxemburg-physical-addresses)</br> - [عناوين مادية في أجهزة الكمبيوتر الخارجية](sensitive-information-type-entity-definitions.md#malta-physical-addresses)</br> - [العناوين المادية لهولندا](sensitive-information-type-entity-definitions.md#netherlands-physical-addresses)</br> - [العناوين المادية لبولاندا](sensitive-information-type-entity-definitions.md#poland-physical-addresses)</br> - [العناوين المادية البرتغالية](sensitive-information-type-entity-definitions.md#portugal-physical-addresses)</br> - [العناوين المادية في رومانيا](sensitive-information-type-entity-definitions.md#romania-physical-addresses)</br> - [العناوين المادية ل لمزوفا](sensitive-information-type-entity-definitions.md#slovakia-physical-addresses)</br> - [العناوين المادية السلوفينية](sensitive-information-type-entity-definitions.md#slovenia-physical-addresses)</br> - [العناوين الفعلية لإسبانيا](sensitive-information-type-entity-definitions.md#spain-physical-addresses)</br> - [العناوين الفعلية في السويد](sensitive-information-type-entity-definitions.md#sweden-physical-addresses)</br> - [رقم الضمان الاجتماعي في النمسا](sensitive-information-type-entity-definitions.md#austria-social-security-number)</br> - [رقم الضمان الاجتماعي (INSEE) في فرنسا](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)</br> - [رقم الضمان الاجتماعي في اليونان (AMKA)](sensitive-information-type-entity-definitions.md#greece-social-security-number-amka)</br> - [رقم الضمان الاجتماعي المجري (TAGE)](sensitive-information-type-entity-definitions.md#hungary-social-security-number-taj)</br> - [رقم الضمان الاجتماعي الإسباني (SSN)](sensitive-information-type-entity-definitions.md#spain-social-security-number-ssn)</br> - [بطاقة هوية النمسا](sensitive-information-type-entity-definitions.md#austria-identity-card)</br> - [بطاقة هوية هوية للسينية](sensitive-information-type-entity-definitions.md#cyprus-identity-card)</br> - [رقم بطاقة الهوية في ألمانيا](sensitive-information-type-entity-definitions.md#germany-identity-card-number)</br> - [رقم بطاقة هوية هوية في هوية هوية الأشخاص في](sensitive-information-type-entity-definitions.md#malta-identity-card-number)</br> - [بطاقة المعرف الوطنية الفرنسية (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)</br> - [بطاقة المعرف الوطني في اليونان](sensitive-information-type-entity-definitions.md#greece-national-id-card)</br> - [المعرف الوطني ل فنلندا](sensitive-information-type-entity-definitions.md#finland-national-id)</br> - [المعرف الوطني لبولونيا (PESEL)](sensitive-information-type-entity-definitions.md#poland-national-id-pesel)</br> - [المعرف الوطني للسويد](sensitive-information-type-entity-definitions.md#sweden-national-id)</br> - [رقم التعريف الشخصي لكرواتيا (OIB)](sensitive-information-type-entity-definitions.md#croatia-personal-identification-oib-number)</br> - [رقم الهوية الشخصية التشيكية](sensitive-information-type-entity-definitions.md#czech-personal-identity-number)</br> - [رقم التعريف الشخصي للدانمرك](sensitive-information-type-entity-definitions.md#denmark-personal-identification-number)</br> - [رمز التعريف الشخصي الإستوني](sensitive-information-type-entity-definitions.md#estonia-personal-identification-code)</br> - [رقم التعريف الشخصي في المجر](sensitive-information-type-entity-definitions.md#hungary-personal-identification-number)</br> - [رقم التعريف الوطني في أوسمبورغ (الأشخاص الطبيعيون)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-natural-persons)</br> - [رقم التعريف الوطني في أوسمبورغ (أشخاص غير طبيعيين)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-non-natural-persons)</br> - [الرمز المالي في إيطاليا](sensitive-information-type-entity-definitions.md#italy-fiscal-code)</br> - [الرمز الشخصي اللاتفي](sensitive-information-type-entity-definitions.md#latvia-personal-code)</br> - [رمز ليتواني الشخصي](sensitive-information-type-entity-definitions.md#lithuania-personal-code)</br> - [الرمز الرقمي الشخصي في رومانيا (CNP)](sensitive-information-type-entity-definitions.md#romania-personal-numeric-code-cnp)</br> - [رقم خدمة المواطنين الهولنديين (BSN)](sensitive-information-type-entity-definitions.md#netherlands-citizens-service-bsn-number)</br> - [رقم الخدمة العامة الشخصية (PPS) في أيرلندا](sensitive-information-type-entity-definitions.md#ireland-personal-public-service-pps-number)</br> - [الرقم المدني الموحد لبلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-uniform-civil-number)</br> - [الرقم الوطني لبلكيا](sensitive-information-type-entity-definitions.md#belgium-national-number)</br> - [DNI أسبانيا](sensitive-information-type-entity-definitions.md#spain-dni)</br> - [رقم مواطن رئيسي فريد في  السلوفينية](sensitive-information-type-entity-definitions.md#slovenia-unique-master-citizen-number)</br> - [الرقم الشخصي ل لمزوفا](sensitive-information-type-entity-definitions.md#slovakia-personal-number)</br> - [رقم بطاقة مواطن البرتغال](sensitive-information-type-entity-definitions.md#portugal-citizen-card-number)</br> - [رقم معرف الضريبة في جبهته](sensitive-information-type-entity-definitions.md#malta-tax-identification-number)</br> - [رقم التعريف الضريبي في النمسا](sensitive-information-type-entity-definitions.md#austria-tax-identification-number)</br> - [رقم التعريف الضريبي للسريبة](sensitive-information-type-entity-definitions.md#cyprus-tax-identification-number)</br> - [رقم التعريف الضريبي في فرنسا (numéro SPI.)](sensitive-information-type-entity-definitions.md#france-tax-identification-number)</br> - [رقم التعريف الضريبي في ألمانيا](sensitive-information-type-entity-definitions.md#germany-tax-identification-number)</br> - [رقم التعريف الضريبي اليوناني](sensitive-information-type-entity-definitions.md#greece-tax-identification-number)</br> - [رقم التعريف الضريبي في المجر](sensitive-information-type-entity-definitions.md#hungary-tax-identification-number)</br> - [رقم التعريف الضريبي في هولندا](sensitive-information-type-entity-definitions.md#netherlands-tax-identification-number)</br> - [رقم التعريف الضريبي في بولندا](sensitive-information-type-entity-definitions.md#poland-tax-identification-number)</br> - [رقم التعريف الضريبي في البرتغال](sensitive-information-type-entity-definitions.md#portugal-tax-identification-number)</br> - [رقم التعريف الضريبي السلوفيني](sensitive-information-type-entity-definitions.md#slovenia-tax-identification-number)</br> - [رقم التعريف الضريبي لإسبانيا](sensitive-information-type-entity-definitions.md#spain-tax-identification-number)</br> - [رقم التعريف الضريبي في السويد](sensitive-information-type-entity-definitions.md#sweden-tax-identification-number)</br> - [ترخيص القيادة في النمسا](sensitive-information-type-entity-definitions.md#austria-drivers-license-number)</br> - [رقم رخصة القيادة في بلجيكا](sensitive-information-type-entity-definitions.md#belgium-drivers-license-number)</br> - [رقم رخصة القيادة في بلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-drivers-license-number)</br> - [رقم رخصة القيادة في كرواتيا](sensitive-information-type-entity-definitions.md#croatia-drivers-license-number)</br> - [رقم رخصة القيادة للسائق](sensitive-information-type-entity-definitions.md#cyprus-drivers-license-number)</br> - [رقم رخصة القيادة التشيكية](sensitive-information-type-entity-definitions.md#czech-drivers-license-number)</br> - [رقم رخصة القيادة في الدانمارك](sensitive-information-type-entity-definitions.md#denmark-drivers-license-number)</br> - [رقم رخصة القيادة الإستونية](sensitive-information-type-entity-definitions.md#estonia-drivers-license-number)</br> - [رقم رخصة القيادة في فنلندا](sensitive-information-type-entity-definitions.md#finland-drivers-license-number)</br> - [رقم رخصة قيادة فرنسا](sensitive-information-type-entity-definitions.md#france-drivers-license-number)</br> - [رقم رخصة القيادة الألمانية](sensitive-information-type-entity-definitions.md#germany-drivers-license-number)</br> - [رقم رخصة القيادة في اليونان](sensitive-information-type-entity-definitions.md#greece-drivers-license-number)</br> - [رقم رخصة القيادة في المجر](sensitive-information-type-entity-definitions.md#hungary-drivers-license-number)</br> - [رقم رخصة القيادة في أيرلندا](sensitive-information-type-entity-definitions.md#ireland-drivers-license-number)</br> - [رقم رخصة القيادة في إيطاليا](sensitive-information-type-entity-definitions.md#italy-drivers-license-number)</br> - [رقم رخصة القيادة في لاتفيا](sensitive-information-type-entity-definitions.md#latvia-drivers-license-number)</br> - [رقم رخصة القيادة في ليتوانا](sensitive-information-type-entity-definitions.md#lithuania-drivers-license-number)</br> - [رقم رخصة القيادة في Burgemburg](sensitive-information-type-entity-definitions.md#luxemburg-drivers-license-number)</br> - [رقم رخصة القيادة للمتجر](sensitive-information-type-entity-definitions.md#malta-drivers-license-number)</br> - [رقم رخصة القيادة في هولندا](sensitive-information-type-entity-definitions.md#netherlands-drivers-license-number)</br> - [رقم رخصة القيادة في بولندا](sensitive-information-type-entity-definitions.md#poland-drivers-license-number)</br> - [رقم رخصة القيادة في البرتغال](sensitive-information-type-entity-definitions.md#portugal-drivers-license-number)</br> - [رقم رخصة القيادة في رومانيا](sensitive-information-type-entity-definitions.md#romania-drivers-license-number)</br> - [رقم رخصة القيادة في  والسلوفاكية](sensitive-information-type-entity-definitions.md#slovakia-drivers-license-number)</br> - [رقم رخصة القيادة السلوفينية](sensitive-information-type-entity-definitions.md#slovenia-drivers-license-number)</br> - [رقم رخصة القيادة الإسبانية](sensitive-information-type-entity-definitions.md#spain-drivers-license-number)</br> - [رقم رخصة القيادة في السويد](sensitive-information-type-entity-definitions.md#sweden-drivers-license-number)</br> - [رقم جواز سفر النمسا](sensitive-information-type-entity-definitions.md#austria-passport-number)</br> - [رقم جواز سفر بلجيكا](sensitive-information-type-entity-definitions.md#belgium-passport-number)</br> - [رقم جواز سفر بلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-passport-number)</br> - [رقم جواز السفر الكرواتي](sensitive-information-type-entity-definitions.md#croatia-passport-number)</br> - [رقم جواز السفر في بورتس](sensitive-information-type-entity-definitions.md#cyprus-passport-number)</br> - [رقم جواز سفر جمهورية تشيكية](sensitive-information-type-entity-definitions.md#czech-passport-number)</br> - [رقم جواز سفر الدانمرك](sensitive-information-type-entity-definitions.md#denmark-passport-number)</br> - [رقم جواز سفر بورتونيا](sensitive-information-type-entity-definitions.md#estonia-passport-number)</br> - [رقم جواز سفر فنلندا](sensitive-information-type-entity-definitions.md#finland-passport-number)</br> - [رقم جواز سفر فرنسا](sensitive-information-type-entity-definitions.md#france-passport-number)</br> - [رقم جواز سفر ألمانيا](sensitive-information-type-entity-definitions.md#germany-passport-number)</br> - [رقم جواز سفر اليونان](sensitive-information-type-entity-definitions.md#greece-passport-number)</br> - [رقم جواز سفر المجر](sensitive-information-type-entity-definitions.md#hungary-passport-number)</br> - [رقم جواز سفر أيرلندا](sensitive-information-type-entity-definitions.md#ireland-passport-number)</br> - [رقم جواز سفر إيطاليا](sensitive-information-type-entity-definitions.md#italy-passport-number)</br> - [رقم جواز سفر لاتفيا](sensitive-information-type-entity-definitions.md#latvia-passport-number)</br> - [رقم جواز سفر ليتوانا](sensitive-information-type-entity-definitions.md#lithuania-passport-number)</br> - [رقم جواز سفر أوسمبورغ](sensitive-information-type-entity-definitions.md#luxemburg-passport-number)</br> - [رقم جواز سفر هواء](sensitive-information-type-entity-definitions.md#malta-passport-number)</br> - [رقم جواز سفر هولندا](sensitive-information-type-entity-definitions.md#netherlands-passport-number)</br> - [جواز سفر بولندا](sensitive-information-type-entity-definitions.md#poland-passport-number)</br> - [رقم جواز سفر البرتغال](sensitive-information-type-entity-definitions.md#portugal-passport-number)</br> - [رقم جواز سفر رومانيا](sensitive-information-type-entity-definitions.md#romania-passport-number)</br> - [رقم جواز سفر بورتوفا](sensitive-information-type-entity-definitions.md#slovakia-passport-number)</br> - [رقم جواز السفر السلوفيني](sensitive-information-type-entity-definitions.md#slovenia-passport-number)</br> - [رقم جواز سفر إسبانيا](sensitive-information-type-entity-definitions.md#spain-passport-number)</br> - [رقم جواز سفر السويد](sensitive-information-type-entity-definitions.md#sweden-passport-number)</br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number)</br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)|
|الخصوصية| القانون العام لحماية البيانات (GDPR)|- [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [رقم رخصة القيادة في الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-drivers-license-number) </br> - [رقم التعريف الوطني للاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-national-identification-number)</br> - [رقم جواز سفر الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-passport-number) </br> - [رقم الضمان الاجتماعي في الاتحاد الأوروبي أو التعريف المكافئ](sensitive-information-type-entity-definitions.md#eu-social-security-number-or-equivalent-identification)</br> - [رقم التعريف الضريبي للاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-tax-identification-number)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في ألمانيا|- [رقم رخصة القيادة في ألمانيا](sensitive-information-type-entity-definitions.md#germany-drivers-license-number) </br> - [رقم جواز سفر ألمانيا](sensitive-information-type-entity-definitions.md#germany-passport-number)| 
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في إسرائيل|- [رقم التعريف الوطني في إسرائيل](sensitive-information-type-entity-definitions.md#israel-national-identification-number)| 
|الخصوصية| حماية الخصوصية في إسرائيل|- [رقم التعريف الوطني في إسرائيل](sensitive-information-type-entity-definitions.md#israel-national-identification-number)</br> - [رقم الحساب البنكي في إسرائيل](sensitive-information-type-entity-definitions.md#israel-bank-account-number)|
|الخصوصية| تم تحسين بيانات معلومات التعريف الشخصية (PII) في اليابان|- [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)</br> - [رقم هاتفي في اليابان - شخصي](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [رقم جواز سفر اليابان](sensitive-information-type-entity-definitions.md#japan-passport-number)</br> - [رقم رخصة القيادة اليابانية](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين المادية لليابان](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في اليابان|- [رقم التسجيل المقيم في اليابان](sensitive-information-type-entity-definitions.md#japan-resident-registration-number) </br> - [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|الخصوصية| حماية المعلومات الشخصية في اليابان محسنة|- [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin) </br> - [رقم هاتفي في اليابان - شخصي](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [رقم جواز سفر اليابان](sensitive-information-type-entity-definitions.md#japan-passport-number) </br> - [رقم رخصة القيادة اليابانية](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين المادية لليابان](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|الخصوصية| حماية المعلومات الشخصية في اليابان|- [رقم التسجيل المقيم في اليابان](sensitive-information-type-entity-definitions.md#japan-resident-registration-number)</br> - [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|الخصوصية| بيانات التعريف الشخصي (PII) في المملكة العربية السعودية|- [المعرف الوطني للسعودية](sensitive-information-type-entity-definitions.md#saudi-arabia-national-id)|
|الخصوصية| بريطانيا. قانون حماية البيانات|- [رقم التأمين الوطني في المملكة المتحدة (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|الخصوصية| بريطانيا. لوائح الخصوصية والاتصالات الإلكترونية|- [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|الخصوصية| بريطانيا. بيانات معلومات التعريف الشخصية (PII)|- [رقم التأمين الوطني في المملكة المتحدة (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|الخصوصية| بريطانيا. رمز الممارسة للمعلومات الشخصية عبر الإنترنت (PIOCP)|- [رقم التأمين الوطني في المملكة المتحدة (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [رقم خدمة الصحة الوطنية في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|الخصوصية| تم تحسين قانون التهيين الأمريكي|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|الخصوصية| قانون الهمة الأمريكية|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|الخصوصية| تحسين بيانات معلومات التعريف الشخصية (PII) في الولايات المتحدة|- [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|الخصوصية| بيانات معلومات التعريف الشخصية (PII) في الولايات المتحدة|- [رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|الخصوصية| تم تحسين قوانين الإعلام بخرق الولاية الأمريكية|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[رقم رخصة القيادة الأمريكية](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [كافة الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [كافة الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions)|
|الخصوصية| قوانين الإعلام بخرق الولاية الأمريكية|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأمريكي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[رقم رخصة القيادة الأمريكية](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|الخصوصية| قوانين سرية رقم الضمان الاجتماعي للولايات المتحدة|- [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|

## <a name="locations"></a>مواقع

يمكن لنهج DLP العثور على العناصر التي تحتوي على معلومات حساسة عبر مواقع متعددة وحمايتها.

|موقع  |تضمين/استبعاد النطاق  |حالة البيانات  |متطلبات مسبقة إضافية |
|---------|---------|---------|---------|
|Exchange عبر الإنترنت |مجموعة التوزيع | البيانات في الحركة| لا |
|مواقع SharePoint عبر الإنترنت   |مواقع       | البيانات الثابتة </br> البيانات قيد الاستخدام | لا|
|حسابات OneDrive for Business| حساب أو مجموعة توزيع |البيانات الثابتة </br> البيانات قيد الاستخدام|لا|
|Teams رسائل الدردشة والقنوات     | حساب أو مجموعة توزيع |البيانات في الحركة </br> البيانات قيد الاستخدام |  لا       |
|Microsoft Defender for Cloud Apps   | مثيل تطبيق السحابة       |البيانات الثابتة         | - [استخدام نهج منع فقدان البيانات لتطبيقات السحابة غير التابعة ل Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|الاجهزه  |المستخدم أو المجموعة         |البيانات الثابتة </br>  البيانات قيد الاستخدام </br>  البيانات في الحركة         |- [تعرف على Microsoft 365 منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention) </br>- [البدء في منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention) </br>- [تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|المستودعات المحلية (مشاركات الملفات SharePoint)    |مستودع         | البيانات الثابتة         | - [تعرف على الماسح الضوئي المحلي لمنع فقدان البيانات Microsoft 365](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner) </br> - [بدء استخدام الماسح الضوئي المحلي لمنع فقدان البيانات](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|PowerBI| مساحات العمل | البيانات قيد الاستخدام | لا|

إذا اخترت تضمين مجموعات توزيع معينة في Exchange، فسيتم تحديد نطاق نهج DLP فقط لأعضاء تلك المجموعة. وبالمثل، فإن استبعاد مجموعة توزيع سيستبعد جميع أعضاء مجموعة التوزيع هذه من تقييم النهج. يمكنك اختيار تحديد نطاق نهج لأعضاء قوائم التوزيع ومجموعات التوزيع الديناميكي ومجموعات الأمان. لا يمكن أن يحتوي نهج DLP على أكثر من 50 من هذه التضمينات والاستثناءات.

إذا اخترت تضمين مواقع SharePoint معينة أو حسابات OneDrive معينة أو استبعادها، فلا يمكن أن يحتوي نهج DLP على أكثر من 100 من هذه التضمينات والاستثناءات. على الرغم من وجود هذا الحد، يمكنك تجاوز هذا الحد عن طريق تطبيق نهج على مستوى المؤسسة أو نهج ينطبق على مواقع بأكملها.

إذا اخترت تضمين حسابات أو مجموعات OneDrive معينة أو استبعادها، فلا يمكن أن يحتوي نهج DLP على أكثر من 100 حساب مستخدم أو 50 مجموعة كتضمين أو استثناء.

### <a name="location-support-for-how-content-can-be-defined"></a>دعم الموقع لكيفية تعريف المحتوى

تكتشف نهج DLP العناصر الحساسة عن طريق مطابقتها بنوع معلومات حساسة (SIT) أو تسمية حساسية أو تسمية استبقاء. يدعم كل موقع أساليب مختلفة لتعريف المحتوى الحساس. عند دمج المواقع في نهج، يمكن تغيير كيفية تعريف المحتوى من كيفية تعريفه بواسطة موقع واحد. 

> [!IMPORTANT]
> عند تحديد مواقع متعددة لنهج ما، فإن قيمة "لا" لفئة تعريف المحتوى لها الأسبقية على القيمة "نعم". على سبيل المثال، عند تحديد مواقع SharePoint فقط، سيدعم النهج الكشف عن العناصر الحساسة بواسطة عنصر واحد أو أكثر من SIT، أو عن طريق تسمية الحساسية، أو عن طريق تسمية الاستبقاء. ولكن، عند تحديد مواقع SharePoint ***ومواقع*** Teams رسائل الدردشة والقنوات، سيدعم النهج الكشف عن العناصر الحساسة فقط عن طريق SIT.

|موقع| يمكن تعريف المحتوى بواسطة SIT| يمكن تعريف وصف الحساسية للمحتوى| يمكن تعريف المحتوى بواسطة تسمية الاستبقاء|
|---------|---------|---------|---------|
|Exchange عبر الإنترنت|نعم| نعم| لا|
|مواقع SharePoint عبر الإنترنت| نعم| نعم| نعم|
|حسابات OneDrive for Business| نعم| نعم| نعم|
|Teams رسائل الدردشة والقناة | نعم| لا| لا|
|الاجهزه |نعم | نعم|  لا|
|Microsoft Defender for Cloud Apps | نعم| نعم| نعم|
|المستودعات المحلية| نعم| نعم| لا|
|PowerBI|نعم | نعم| لا|

> [!NOTE]
> يدعم DLP الكشف عن تسميات الحساسية على رسائل البريد الإلكتروني والمرفقات انظر، [استخدم تسميات الحساسية كشروط في نهج DLP](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

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
- [**إعلامات المستخدم**](#user-notifications-and-policy-tips) لإعلام المستخدمين عند قيامهم بشيء ما يؤدي إلى تشغيل نهج والمساعدة في تعليمهم حول كيفية معاملة مؤسستك للمعلومات الحساسة
- [**تجاوز المستخدم**](#user-overrides) عند تكوينه من قبل مسؤول، والسماح للمستخدمين بتجاوز إجراء حظر بشكل انتقائي
- [**تقارير الحوادث**](#incident-reports) التي تقوم بإعلام المسؤولين وأصحاب المصلحة الرئيسيين الآخرين عند حدوث تطابق للقاعدة
- [**خيارات إضافية**](#additional-options) تحدد أولوية تقييم القواعد ويمكن أن توقف المزيد من معالجة القواعد والنهج.

 يحتوي النهج على قاعدة واحدة أو أكثر. يتم تنفيذ القواعد بشكل تسلسلي، بدءا من قاعدة الأولوية العليا في كل نهج.

### <a name="the-priority-by-which-rules-are-processed"></a>الأولوية التي تتم بها معالجة القواعد

#### <a name="hosted-service-workloads"></a>أحمال عمل الخدمة المستضافة

بالنسبة لأحمال عمل الخدمة المستضافة، مثل Exchange Online SharePoint عبر الإنترنت OneDrive for Business، يتم تعيين أولوية لكل قاعدة بالترتيب الذي يتم إنشاؤها به. وهذا يعني أن القاعدة التي تم إنشاؤها أولا لها الأولوية الأولى، والقاعدة التي تم إنشاؤها الثانية لها الأولوية الثانية، وهكذا. 
  
![القواعد بترتيب الأولوية](../media/dlp-rules-in-priority-order.png)

عند تقييم المحتوى مقابل القواعد، تتم معالجة القواعد بترتيب الأولوية. إذا تطابق المحتوى مع قواعد متعددة، يتم فرض القاعدة الأولى التي تم تقييمها والتي تتضمن الإجراء *الأكثر* تقييدا. على سبيل المثال، إذا تطابق المحتوى مع جميع القواعد التالية، يتم فرض *القاعدة 3* لأنها القاعدة الأعلى أولوية والأكثر تقييدا:
  
- القاعدة 1: إعلام المستخدمين فقط
- القاعدة 2: إعلام المستخدمين، وتقييد الوصول، وتسمح بتجاوز المستخدم
- *القاعدة 3: إعلام المستخدمين وتقييد الوصول وعدم السماح بتجاوزات المستخدم*
- القاعدة 4: تقييد الوصول

سيتم تقييم القواعد 1 و2 و4، ولكن لن يتم تطبيقها. في هذا المثال، يتم تسجيل التطابقات لكافة القواعد في سجلات التدقيق وتظهر في تقارير DLP، على الرغم من تطبيق القاعدة الأكثر تقييدا فقط.

يمكنك استخدام قاعدة لتلبية متطلبات حماية معينة، ثم استخدام نهج DLP لتجميع متطلبات الحماية المشتركة معا، مثل جميع القواعد اللازمة للامتثال لائحة معينة.
  
على سبيل المثال، قد يكون لديك نهج DLP يساعدك على اكتشاف وجود المعلومات الخاضعة لقانون نقل التأمين الصحي والمساءلة (HIPAA). يمكن أن يساعد نهج DLP هذا في حماية بيانات HIPAA (ما) عبر جميع مواقع SharePoint Online وكافة مواقع OneDrive for Business (المكان) من خلال العثور على أي مستند يحتوي على هذه المعلومات الحساسة التي تتم مشاركتها مع أشخاص من خارج مؤسستك (الشروط) ثم حظر الوصول إلى المستند وإرسال إعلام (الإجراءات). يتم تخزين هذه المتطلبات كقواعد فردية وتجميعها معا كنهج DLP لتبسيط الإدارة وإعداد التقارير.
  
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

بالنسبة لنقاط النهاية، يمكنك تكوين الإجراءات التي يتخذها DLP لجميع الأنشطة المدعومة في قاعدة واحدة لمجموعة معينة من شروط التضمين.

### <a name="conditions"></a>الظروف

الشروط شاملة وهي المكان الذي تحدد فيه ما تريد أن تبحث عنه القاعدة والسياق الذي يتم فيه استخدام هذه العناصر. يخبرون القاعدة &#8212; عند العثور على عنصر يبدو مثل *هذا* ويتم استخدامه على *هذا* النحو &#8212; أنه مطابق ويجب اتخاذ بقية الإجراءات في النهج عليه. يمكنك استخدام الشروط لتعيين إجراءات مختلفة لمستويات مخاطر مختلفة. على سبيل المثال، قد يكون المحتوى الحساس المشترك داخليا أقل خطورة ويتطلب إجراءات أقل من المحتوى الحساس المشترك مع أشخاص من خارج المؤسسة.

> [!NOTE]
> يعتبر المستخدمون الذين لديهم حسابات غير ضيوف في Active Directory أو مستأجر Azure Active Directory للمؤسسة المضيفة أشخاصا داخل المؤسسة. 

#### <a name="content-contains"></a>يحتوي المحتوى على

 تحتوي كافة المواقع التي تدعم **المحتوى على** شرط. يمكنك تحديد مثيلات متعددة لكل نوع محتوى وتحسين الشروط بشكل أكبر باستخدام **أي من عوامل التشغيل هذه** (OR المنطقية) أو **كل هذه** (AND المنطقية):

- [أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [أوصاف الحساسية](sensitivity-labels.md)
- [تسميات الاستبقاء](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

اعتمادا على [الموقع (المواقع)](#location-support-for-how-content-can-be-defined) التي تختار تطبيق النهج عليها. 

ستبحث القاعدة فقط عن وجود أي **تسميات حساسية** **وتسميات استبقاء تختارها** . 

لدى SITs [**مستوى ثقة**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) محدد مسبقا يمكنك تغييره إذا لزم الأمر. لمزيد من المعلومات، راجع [المزيد حول مستويات الثقة](sensitive-information-type-learn-about.md#more-on-confidence-levels). 

> [!IMPORTANT]
> لدى SITs طريقتان مختلفتان لتحديد معلمات الحد الأقصى لعدد المثيلات الفريدة. لمعرفة المزيد، راجع [قيم عدد المثيلات المعتمدة ل SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>سياق الشرط

تتغير خيارات السياق المتوفرة استنادا إلى الموقع الذي تختاره. إذا حددت مواقع متعددة، فستتوفر الشروط المشتركة فقط.

##### <a name="conditions-exchange-supports"></a>الشروط التي يدعمها Exchange

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

##### <a name="conditions-sharepoint-supports"></a>تدعم الشروط SharePoint
 
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

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>الشروط Teams تدعم رسائل الدردشة والقنوات

- يحتوي المحتوى على
- تتم مشاركة المحتوى من Microsoft 365
- المرسل هو 
- مجال المرسل هو 
- مجال المستلم هو 
- المستلم هو 

##### <a name="conditions-devices-supports"></a>تدعم أجهزة الشروط

- يحتوي المحتوى على
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

- حظر المستخدمين من الوصول إلى محتوى SharePoint المشتركة OneDrive Teams
    - حظر الجميع. سيظل مالك المحتوى والمعدل الأخير وإدارة الموقع فقط لديهم حق الوصول
    - حظر الأشخاص من خارج مؤسستك فقط. سيظل المستخدمون داخل مؤسستك يتمتعون بإمكانية الوصول.
- تشفير رسائل البريد الإلكتروني (ينطبق فقط على المحتوى في Exchange)

تعتمد الإجراءات المتوفرة في قاعدة على المواقع التي تم تحديدها. إذا حددت موقعا واحدا فقط للنهج الذي سيتم تطبيقه عليه، فسيتم سرد الإجراءات المتوفرة أدناه.

> [!IMPORTANT]
> بالنسبة SharePoint عبر الإنترنت ومواقع OneDrive for Business سيتم حظر المستندات بشكل استباقي بعد الكشف عن المعلومات الحساسة مباشرة، بغض النظر عما إذا كان المستند مشتركا أم لا، لجميع المستخدمين الخارجيين، بينما سيظل بإمكان المستخدمين الداخليين الوصول إلى المستند.

#### <a name="exchange-location-actions"></a>إجراءات الموقع Exchange

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

#### <a name="teams-chat-and-channel-messages-actions"></a>Teams إجراءات رسائل المحادثة والقناة

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365

#### <a name="devices-actions"></a>إجراءات الأجهزة

- تدقيق الأنشطة أو تقييدها على أجهزة Windows

لاستخدام هذه الإعدادات، يجب تكوين الخيارات في **إعدادات DLP** وفي النهج الذي تريد استخدامها فيه. لمزيد من المعلومات، راجع [التطبيقات المقيدة ومجموعات التطبيقات](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) .

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

- كافة الإجراءات الخاصة بالموقع غير Exchange

ستكون الإجراءات متوفرة.

إذا قمت بتحديد موقعين أو أكثر من المواقع غير Exchange للنهج الذي سيتم تطبيقه عليه،

- تقييد الوصول إلى المحتوى أو تشفيره في مواقع Microsoft 365

و

- كافة الإجراءات للمواقع غير Exchange 

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

على سبيل المثال، محتوى مثل مصنف Excel على موقع OneDrive for Business يحتوي على معلومات تعريف شخصية (PII) تتم مشاركتها مع ضيف.

![يعرض شريط الرسائل تلميح النهج في Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!NOTE]
> يتم إرسال رسائل البريد الإلكتروني للإعلام بدون حماية.

يمكنك أيضا منح الأشخاص خيار [تجاوز النهج](#user-overrides)، بحيث لا يتم حظرهم إذا كانت لديهم حاجة عمل صالحة أو إذا كان النهج يكشف عن إيجابية خاطئة.

تختلف خيارات تكوين إعلامات المستخدم وتلميحات النهج استنادا إلى مواقع المراقبة التي حددتها. إذا قمت بتحديد:

- Exchange
- SharePoint
- OneDrive
- Teams الدردشة والقناة
- Defender for Cloud Apps


يمكنك تمكين/تعطيل إعلامات المستخدم لتطبيقات Microsoft المختلفة، راجع [مرجع تلميحات نهج منع فقدان البيانات](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- يمكنك تمكين/تعطيل **إعلام المستخدمين في خدمة Office 365** مع تلميح نهج.
    - إعلامات البريد الإلكتروني للمستخدم الذي أرسل المحتوى أو شاركه أو عدله آخر مرة
    - إعلام أشخاص محددين

وتخصيص نص البريد الإلكتروني والموضوع ونص تلميح النهج.

![خيارات تكوين تلميح إعلام المستخدم والنهج المتوفرة Exchange، SharePoint، OneDrive، Teams الدردشة والقناة، و Defender لتطبيقات السحابة](../media/dlp-user-notification-non-devices.png)

إذا قمت بتحديد الأجهزة فقط، فستحصل على جميع الخيارات نفسها المتوفرة ل Exchange، SharePoint، OneDrive، Teams الدردشة والقناة و Defender لتطبيقات السحابة بالإضافة إلى خيار تخصيص عنوان الإعلام والمحتوى الذي يظهر على جهاز Windows 10.

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
|نسخ عبر bluetooth   |*نقل عبر Bluetooth*         |
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

يقوم DLP بتغذية معلومات الحادث إلى خدمات حماية المعلومات Microsoft 365 الأخرى، مثل [إدارة المخاطر من Insider في Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365). من أجل الحصول على معلومات الحادث إلى إدارة المخاطر الداخلية، يجب تعيين مستوى خطورة **تقارير الحوادث** إلى **مستوى عال**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

يمكن إرسال التنبيهات في كل مرة يتطابق فيها النشاط مع قاعدة، والتي يمكن أن تكون صاخبة أو يمكن تجميعها في تنبيهات أقل استنادا إلى عدد التطابقات أو حجم العناصر على مدى فترة زمنية محددة.

![إرسال تنبيه في كل مرة تتطابق فيها القاعدة أو تجمعها بمرور الوقت في تقارير أقل](../media/dlp-incident-reports-aggregation.png)

يقوم DLP بمسح البريد الإلكتروني بشكل مختلف عن SharePoint العناصر المتصلة أو OneDrive for Business. في SharePoint Online و OneDrive for Business، يقوم DLP بمسح العناصر الموجودة بالإضافة إلى العناصر الجديدة وإنشاء تقرير عن الحادث كلما تم العثور على تطابق. في Exchange Online، يقوم DLP بفحص رسائل البريد الإلكتروني الجديدة فقط وإنشاء تقرير إذا كان هناك تطابق في النهج. ***لا*** يقوم DLP بمسح عناصر البريد الإلكتروني الموجودة مسبقا المخزنة في علبة بريد أو أرشيف أو مطابقتها.

### <a name="additional-options"></a>خيارات إضافية

إذا كان لديك قواعد متعددة في نهج، يمكنك استخدام **الخيارات الإضافية** للتحكم في معالجة القواعد الإضافية إذا كان هناك تطابق مع القاعدة التي تقوم بتحريرها بالإضافة إلى تعيين الأولوية لتقييم القاعدة.

## <a name="see-also"></a>راجع أيضًا

- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
