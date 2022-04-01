---
title: مرجع نهج منع فقدان البيانات
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
description: مرجع التكوين ومكون نهج DLP
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 9b9658db71ea9945cedb746ec688eff5018a4ba4
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520605"
---
# <a name="data-loss-prevention-policy-reference"></a>مرجع نهج منع فقدان البيانات

تتوفر في سياسات منع فقدان البيانات (DLP) العديد من المكونات التي يجب تكوينها. لإنشاء نهج فعال، تحتاج إلى فهم الغرض من كل مكون وكيفية تغيير تكوينه سلوك النهج. توفر هذه المقالة تحليلا مفصلا لنمع DLP.

## <a name="policy-templates"></a>قوالب النهج 

يتم فرز قوالب نهج DLP مسبقا في أربع فئات:

- تلك التي يمكنها الكشف عن أنواع المعلومات المالية **وحمايتها** .
- تلك التي يمكنها الكشف عن أنواع المعلومات الطبية **والصحية وحمايتها** .
- تلك التي يمكنها الكشف عن أنواع معلومات **الخصوصية وحمايتها** .
- قالب **مخصص** يمكنك استخدامه لإنشاء نهجك الخاص إذا لم يلبي أحد القالبين الآخرين احتياجات مؤسستك.

يسرد هذا الجدول كل قوالب النهج وأنواع المعلومات الحساسة (SIT) التي تغطيها. 

محدث: 23/06/2021

|الفئة| قالب | SIT |
|---------|---------|---------|
|المالية| بيانات أستراليا المالية| - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم الملف الضريبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم الحساب البنكي في أستراليا](sensitive-information-type-entity-definitions.md#australia-bank-account-number) </br> - [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|المالية| البيانات المالية في كندا |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي في كندا](sensitive-information-type-entity-definitions.md#canada-bank-account-number)|
|المالية| بيانات فرنسا المالية |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|المالية| البيانات المالية في ألمانيا |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|المالية| البيانات المالية في إسرائيل |- [رقم الحساب البنكي في إسرائيل](sensitive-information-type-entity-definitions.md#israel-bank-account-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|المالية| البيانات المالية اليابانية |- [رقم الحساب البنكي الياباني](sensitive-information-type-entity-definitions.md#japan-bank-account-number) </br> - [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|المالية| PCI Data Security Standard (PCI DSS)|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number)|
|المالية| قانون مكافحة الجريمة الإلكترونية في المملكة العربية السعودية|- [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم حساب الخدمات المصرفية الدولية (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban) |
|المالية| البيانات المالية للمملكة العربية السعودية |- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code) </br> - [رقم حساب الخدمات المصرفية الدولية (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban)|
|المالية| البيانات المالية للمملكة المتحدة|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|المالية| البيانات المالية الأمريكية|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم توجيه ABA](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|المالية| قواعد مستهلك لجنة التجارة الفيدرالية (FTC) الأمريكية|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم توجيه ABA](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|المالية| تم تحسين قانون Gramm-Leach-Bliley (GLBA) الأمريكي|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف الممول الفردي (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> -[رقم ترخيص القيادة الأمريكية](sensitive-information-type-entity-definitions.md#us-drivers-license-number)</br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|المالية| قانون الولايات المتحدة لGramm-Leach-Bliley (GLBA)|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف الممول الفردي (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|الصحة والرعاية الطبية| قانون السجلات الصحية في أستراليا (قانون HRIP) محسن |- [رقم الملف الضريبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم الحساب الطبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-medical-account-number) </br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [كل الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [العناوين الفعلية في أستراليا](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|الصحة والرعاية الطبية| قانون السجلات الصحية في أستراليا (قانون HRIP)|- [رقم الملف الضريبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم الحساب الطبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-medical-account-number)|
|الصحة والرعاية الطبية| قانون معلومات الصحة في كندا (HIA) |- [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم تعريف الصحة الشخصية في كندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الصحة والرعاية الطبية| قانون معلومات الصحة الشخصية في كندا (PHIA) مانيتوبا|- [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم تعريف الصحة الشخصية في كندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الصحة والرعاية الطبية| قانون كندا للصحة الشخصية (PHIPA) أونتاريو |- [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم تعريف الصحة الشخصية في كندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الصحة والرعاية الطبية| المملكة المتحدة قانون الوصول إلى التقارير الطبية|- [رقم خدمة الصحة الوطنية في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [رقم التأمين الوطني (NINO) في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino)|
|الصحة والرعاية الطبية| قانون التأمين الصحي (HIPAA) المحسن في الولايات المتحدة|</br> - [التصنيف الدولي لداءات (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [التصنيف الدولي لداءات (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm) </br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [كل الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|الصحة والرعاية الطبية| قانون التأمين الصحي في الولايات المتحدة (HIPAA)| - [التصنيف الدولي لداءات (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [التصنيف الدولي لداءات (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm)|
|الخصوصية| قانون الخصوصية في أستراليا محسن|- [رقم ترخيص القيادة في أستراليا](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [رقم جواز سفر أستراليا](sensitive-information-type-entity-definitions.md#australia-passport-number) </br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [كل الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [العناوين الفعلية في أستراليا](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|الخصوصية| قانون الخصوصية في أستراليا|- [رقم ترخيص القيادة في أستراليا](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [رقم جواز سفر أستراليا](sensitive-information-type-entity-definitions.md#australia-passport-number)|
|الخصوصية| بيانات المعلومات الشخصية (PII) في أستراليا|- [رقم الملف الضريبي في أستراليا](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [رقم ترخيص القيادة في أستراليا](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)|
|الخصوصية| بيانات المعلومات الشخصية (PII) في كندا|- [رقم ترخيص القيادة في كندا](sensitive-information-type-entity-definitions.md#canada-drivers-license-number)</br> - [رقم الحساب البنكي في كندا](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم تعريف الصحة الشخصية في كندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الخصوصية| قانون كندا حماية البيانات (PIPA)|- [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم تعريف الصحة الشخصية في كندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الخصوصية| قانون كندا حماية البيانات (PIPEDA)|- [رقم ترخيص القيادة في كندا](sensitive-information-type-entity-definitions.md#canada-drivers-license-number) </br> - [رقم الحساب البنكي في كندا](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [رقم جواز سفر كندا](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [رقم التأمين الاجتماعي في كندا](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [رقم خدمة الصحة في كندا](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [رقم تعريف الصحة الشخصية في كندا](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|الخصوصية| قانون حماية البيانات في فرنسا|- [بطاقة الهوية الوطنية الفرنسية (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni) </br> - [رقم الضمان الاجتماعي في فرنسا (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)|
|الخصوصية| بيانات المعلومات الشخصية (PII) في فرنسا|- [رقم الضمان الاجتماعي في فرنسا (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee) </br> - [رقم ترخيص القيادة في فرنسا](sensitive-information-type-entity-definitions.md#france-drivers-license-number) </br> - [رقم جواز سفر فرنسا](sensitive-information-type-entity-definitions.md#france-passport-number) </br> - [بطاقة الهوية الوطنية الفرنسية (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)|
|الخصوصية| القانون العام لحماية البيانات (GDPR) محسن|- [العناوين الفعلية في النمسا](sensitive-information-type-entity-definitions.md#austria-physical-addresses) </br> - [العناوين الفعلية لبلجيكا](sensitive-information-type-entity-definitions.md#belgium-physical-addresses)</br> - [العناوين الفعلية لبلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-physical-addresses)</br> - [العناوين الفعلية لكرواتيا](sensitive-information-type-entity-definitions.md#croatia-physical-addresses)</br> - [العناوين الفعلية لقبرص](sensitive-information-type-entity-definitions.md#cyprus-physical-addresses)</br> - [العناوين الفعلية للجمهورية التشيكية](sensitive-information-type-entity-definitions.md#czech-republic-physical-addresses)</br> - [العناوين الفعلية في الدانمرك](sensitive-information-type-entity-definitions.md#denmark-physical-addresses)</br> - [العناوين الفعلية لإستونيا](sensitive-information-type-entity-definitions.md#estonia-physical-addresses)</br> - [العناوين الفعلية لفنلندا](sensitive-information-type-entity-definitions.md#finland-physical-addresses)</br> - [عناوين فرنسا الفعلية](sensitive-information-type-entity-definitions.md#france-physical-addresses)</br> - [عناوين ألمانيا الفعلية](sensitive-information-type-entity-definitions.md#germany-physical-addresses)</br> - [العناوين الفعلية في اليونان](sensitive-information-type-entity-definitions.md#greece-physical-addresses)</br> - [العناوين الفعلية للمجر](sensitive-information-type-entity-definitions.md#hungary-physical-addresses)</br> - [عناوين أيرلندا الفعلية](sensitive-information-type-entity-definitions.md#ireland-physical-addresses)</br> - [العناوين الفعلية في إيطاليا](sensitive-information-type-entity-definitions.md#italy-physical-addresses)</br> - [العناوين الفعلية في لاتفيا](sensitive-information-type-entity-definitions.md#latvia-physical-addresses)</br> - [العناوين الفعلية في ليتوانيا](sensitive-information-type-entity-definitions.md#lithuania-physical-addresses)</br> - [العناوين الفعلية في لكسمبورغ](sensitive-information-type-entity-definitions.md#luxemburg-physical-addresses)</br> - [العناوين الفعلية في مالطا](sensitive-information-type-entity-definitions.md#malta-physical-addresses)</br> - [العناوين الفعلية لهولندا](sensitive-information-type-entity-definitions.md#netherlands-physical-addresses)</br> - [العناوين الفعلية في بولندا](sensitive-information-type-entity-definitions.md#poland-physical-addresses)</br> - [العناوين الفعلية البرتغالية](sensitive-information-type-entity-definitions.md#portugal-physical-addresses)</br> - [العناوين الفعلية لرومانيا](sensitive-information-type-entity-definitions.md#romania-physical-addresses)</br> - [العناوين الفعلية في سلوفاكيا](sensitive-information-type-entity-definitions.md#slovakia-physical-addresses)</br> - [العناوين الفعلية في سلوفينيا](sensitive-information-type-entity-definitions.md#slovenia-physical-addresses)</br> - [العناوين الفعلية لإسبانيا](sensitive-information-type-entity-definitions.md#spain-physical-addresses)</br> - [العناوين الفعلية في السويد](sensitive-information-type-entity-definitions.md#sweden-physical-addresses)</br> - [رقم الضمان الاجتماعي في النمسا](sensitive-information-type-entity-definitions.md#austria-social-security-number)</br> - [رقم الضمان الاجتماعي في فرنسا (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)</br> - [رقم الضمان الاجتماعي في اليونان (AMKA)](sensitive-information-type-entity-definitions.md#greece-social-security-number-amka)</br> - [رقم الضمان الاجتماعي المجري (TAJ)](sensitive-information-type-entity-definitions.md#hungary-social-security-number-taj)</br> - [رقم الضمان الاجتماعي (SSN) في إسبانيا](sensitive-information-type-entity-definitions.md#spain-social-security-number-ssn)</br> - [بطاقة هوية النمسا](sensitive-information-type-entity-definitions.md#austria-identity-card)</br> - [بطاقة هوية قبرص](sensitive-information-type-entity-definitions.md#cyprus-identity-card)</br> - [رقم بطاقة الهوية الألمانية](sensitive-information-type-entity-definitions.md#germany-identity-card-number)</br> - [رقم بطاقة هوية مالطا](sensitive-information-type-entity-definitions.md#malta-identity-card-number)</br> - [بطاقة الهوية الوطنية الفرنسية (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)</br> - [بطاقة الم ID الوطنية في اليونان](sensitive-information-type-entity-definitions.md#greece-national-id-card)</br> - [الم ID الوطنية لفنلندا](sensitive-information-type-entity-definitions.md#finland-national-id)</br> - [الم ID الوطنية البولندية (PESEL)](sensitive-information-type-entity-definitions.md#poland-national-id-pesel)</br> - [الم ID الوطنية في السويد](sensitive-information-type-entity-definitions.md#sweden-national-id)</br> - [رقم التعريف الشخصي (OIB) في كرواتيا](sensitive-information-type-entity-definitions.md#croatia-personal-identification-oib-number)</br> - [رقم الهوية الشخصية التشيكية](sensitive-information-type-entity-definitions.md#czech-personal-identity-number)</br> - [رقم التعريف الشخصي في الدانمرك](sensitive-information-type-entity-definitions.md#denmark-personal-identification-number)</br> - [رمز التعريف الشخصي لإستونيا](sensitive-information-type-entity-definitions.md#estonia-personal-identification-code)</br> - [رقم التعريف الشخصي في هنغاريا](sensitive-information-type-entity-definitions.md#hungary-personal-identification-number)</br> - [رقم التعريف الوطني ل Luxemburg (الأشخاص الطبيعيون)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-natural-persons)</br> - [رقم التعريف الوطني ل Luxemburg (الأشخاص غير الطبيعيين)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-non-natural-persons)</br> - [رمز إيطاليا المالي](sensitive-information-type-entity-definitions.md#italy-fiscal-code)</br> - [رمز لاتفيا الشخصي](sensitive-information-type-entity-definitions.md#latvia-personal-code)</br> - [الرمز الشخصي لليتوانيا](sensitive-information-type-entity-definitions.md#lithuania-personal-code)</br> - [رمز رومانيا الرقمي الشخصي (CNP)](sensitive-information-type-entity-definitions.md#romania-personal-numeric-code-cnp)</br> - [رقم الخدمة (BSN) في هولندا](sensitive-information-type-entity-definitions.md#netherlands-citizens-service-bsn-number)</br> - [رقم الخدمة العامة (PPS) في أيرلندا](sensitive-information-type-entity-definitions.md#ireland-personal-public-service-pps-number)</br> - [الرقم المدني الرسمي لبلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-uniform-civil-number)</br> - [الرقم الوطني لبلجيكا](sensitive-information-type-entity-definitions.md#belgium-national-number)</br> - [أسبانيا DNI](sensitive-information-type-entity-definitions.md#spain-dni)</br> - [رقم سلوفينيا الرئيسي الفريد](sensitive-information-type-entity-definitions.md#slovenia-unique-master-citizen-number)</br> - [الرقم الشخصي في سلوفاكيا](sensitive-information-type-entity-definitions.md#slovakia-personal-number)</br> - [رقم بطاقة البرتغال المهيّة](sensitive-information-type-entity-definitions.md#portugal-citizen-card-number)</br> - [رقم الم ID الضريبة في مالطا](sensitive-information-type-entity-definitions.md#malta-tax-identification-number)</br> - [رقم تعريف الضريبة في النمسا](sensitive-information-type-entity-definitions.md#austria-tax-identification-number)</br> - [رقم التعريف الضريبي لقبرص](sensitive-information-type-entity-definitions.md#cyprus-tax-identification-number)</br> - [رقم تعريف الضريبة في فرنسا (numéro SPI.)](sensitive-information-type-entity-definitions.md#france-tax-identification-number)</br> - [رقم تعريف الضريبة في ألمانيا](sensitive-information-type-entity-definitions.md#germany-tax-identification-number)</br> - [رقم تعريف الضريبة اليونانية](sensitive-information-type-entity-definitions.md#greece-tax-identification-number)</br> - [رقم تعريف الضريبة في هنغاريا](sensitive-information-type-entity-definitions.md#hungary-tax-identification-number)</br> - [رقم تعريف الضريبة في هولندا](sensitive-information-type-entity-definitions.md#netherlands-tax-identification-number)</br> - [رقم تعريف الضريبة في بولندا](sensitive-information-type-entity-definitions.md#poland-tax-identification-number)</br> - [رقم تعريف الضريبة في البرتغال](sensitive-information-type-entity-definitions.md#portugal-tax-identification-number)</br> - [رقم تعريف الضريبة في سلوفينيا](sensitive-information-type-entity-definitions.md#slovenia-tax-identification-number)</br> - [رقم تعريف الضريبة في إسبانيا](sensitive-information-type-entity-definitions.md#spain-tax-identification-number)</br> - [رقم تعريف الضريبة في السويد](sensitive-information-type-entity-definitions.md#sweden-tax-identification-number)</br> - [ترخيص القيادة في النمسا](sensitive-information-type-entity-definitions.md#austria-drivers-license-number)</br> - [رقم ترخيص القيادة في بلجيكا](sensitive-information-type-entity-definitions.md#belgium-drivers-license-number)</br> - [رقم ترخيص القيادة في بلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-drivers-license-number)</br> - [رقم ترخيص القيادة في كرواتيا](sensitive-information-type-entity-definitions.md#croatia-drivers-license-number)</br> - [رقم ترخيص القيادة في قبرص](sensitive-information-type-entity-definitions.md#cyprus-drivers-license-number)</br> - [رقم ترخيص القيادة التشيكية](sensitive-information-type-entity-definitions.md#czech-drivers-license-number)</br> - [رقم ترخيص برنامج تشغيل الدانمرك](sensitive-information-type-entity-definitions.md#denmark-drivers-license-number)</br> - [رقم ترخيص القيادة لإستونيا](sensitive-information-type-entity-definitions.md#estonia-drivers-license-number)</br> - [رقم ترخيص القيادة لفنلندا](sensitive-information-type-entity-definitions.md#finland-drivers-license-number)</br> - [رقم ترخيص القيادة الفرنسية](sensitive-information-type-entity-definitions.md#france-drivers-license-number)</br> - [رقم ترخيص القيادة الألمانية](sensitive-information-type-entity-definitions.md#germany-drivers-license-number)</br> - [رقم ترخيص برنامج تشغيل اليونان](sensitive-information-type-entity-definitions.md#greece-drivers-license-number)</br> - [رقم ترخيص القيادة في هنغاريا](sensitive-information-type-entity-definitions.md#hungary-drivers-license-number)</br> - [رقم ترخيص القيادة في أيرلندا](sensitive-information-type-entity-definitions.md#ireland-drivers-license-number)</br> - [رقم ترخيص القيادة في إيطاليا](sensitive-information-type-entity-definitions.md#italy-drivers-license-number)</br> - [رقم ترخيص القيادة في لاتفيا](sensitive-information-type-entity-definitions.md#latvia-drivers-license-number)</br> - [رقم ترخيص القيادة في ليتوانيا](sensitive-information-type-entity-definitions.md#lithuania-drivers-license-number)</br> - [رقم ترخيص برنامج تشغيل Luxemburg](sensitive-information-type-entity-definitions.md#luxemburg-drivers-license-number)</br> - [رقم ترخيص القيادة المالطية](sensitive-information-type-entity-definitions.md#malta-drivers-license-number)</br> - [رقم ترخيص برنامج التشغيل الهولندي](sensitive-information-type-entity-definitions.md#netherlands-drivers-license-number)</br> - [رقم ترخيص القيادة في بولندا](sensitive-information-type-entity-definitions.md#poland-drivers-license-number)</br> - [رقم ترخيص برنامج تشغيل البرتغال](sensitive-information-type-entity-definitions.md#portugal-drivers-license-number)</br> - [رقم ترخيص القيادة في رومانيا](sensitive-information-type-entity-definitions.md#romania-drivers-license-number)</br> - [رقم ترخيص القيادة في سلوفاكيا](sensitive-information-type-entity-definitions.md#slovakia-drivers-license-number)</br> - [رقم ترخيص القيادة في سلوفينيا](sensitive-information-type-entity-definitions.md#slovenia-drivers-license-number)</br> - [رقم ترخيص القيادة في إسبانيا](sensitive-information-type-entity-definitions.md#spain-drivers-license-number)</br> - [رقم ترخيص القيادة في السويد](sensitive-information-type-entity-definitions.md#sweden-drivers-license-number)</br> - [رقم جواز سفر النمسا](sensitive-information-type-entity-definitions.md#austria-passport-number)</br> - [رقم جواز السفر في بلجيكا](sensitive-information-type-entity-definitions.md#belgium-passport-number)</br> - [رقم جواز السفر في بلغاريا](sensitive-information-type-entity-definitions.md#bulgaria-passport-number)</br> - [رقم جواز سفر كرواتيا](sensitive-information-type-entity-definitions.md#croatia-passport-number)</br> - [رقم جواز السفر الخاص بقبرص](sensitive-information-type-entity-definitions.md#cyprus-passport-number)</br> - [رقم جواز سفر جمهورية التشيك](sensitive-information-type-entity-definitions.md#czech-passport-number)</br> - [رقم جواز السفر الدانماركي](sensitive-information-type-entity-definitions.md#denmark-passport-number)</br> - [رقم جواز سفر إستونيا](sensitive-information-type-entity-definitions.md#estonia-passport-number)</br> - [رقم جواز سفر فنلندا](sensitive-information-type-entity-definitions.md#finland-passport-number)</br> - [رقم جواز السفر الفرنسي](sensitive-information-type-entity-definitions.md#france-passport-number)</br> - [رقم جواز السفر الألماني](sensitive-information-type-entity-definitions.md#germany-passport-number)</br> - [رقم جواز سفر اليونان](sensitive-information-type-entity-definitions.md#greece-passport-number)</br> - [رقم جواز السفر المجري](sensitive-information-type-entity-definitions.md#hungary-passport-number)</br> - [رقم جواز سفر أيرلندا](sensitive-information-type-entity-definitions.md#ireland-passport-number)</br> - [رقم جواز سفر إيطاليا](sensitive-information-type-entity-definitions.md#italy-passport-number)</br> - [رقم جواز سفر لاتفيا](sensitive-information-type-entity-definitions.md#latvia-passport-number)</br> - [رقم جواز السفر الليتواني](sensitive-information-type-entity-definitions.md#lithuania-passport-number)</br> - [رقم جواز سفر للوكسمبورج](sensitive-information-type-entity-definitions.md#luxemburg-passport-number)</br> - [رقم جواز السفر المالطية](sensitive-information-type-entity-definitions.md#malta-passport-number)</br> - [رقم جواز السفر الهولندي](sensitive-information-type-entity-definitions.md#netherlands-passport-number)</br> - [جواز سفر بولندا](sensitive-information-type-entity-definitions.md#poland-passport-number)</br> - [رقم جواز سفر البرتغال](sensitive-information-type-entity-definitions.md#portugal-passport-number)</br> - [رقم جواز سفر رومانيا](sensitive-information-type-entity-definitions.md#romania-passport-number)</br> - [رقم جواز السفر السلوفاكي](sensitive-information-type-entity-definitions.md#slovakia-passport-number)</br> - [رقم جواز السفر السلوفيني](sensitive-information-type-entity-definitions.md#slovenia-passport-number)</br> - [رقم جواز سفر إسبانيا](sensitive-information-type-entity-definitions.md#spain-passport-number)</br> - [رقم جواز السفر السويدي](sensitive-information-type-entity-definitions.md#sweden-passport-number)</br> - [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number)</br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)|
|الخصوصية| القانون العام لحماية البيانات (GDPR)|- [رقم بطاقة خصم الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [رقم ترخيص القيادة في الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-drivers-license-number) </br> - [رقم التعريف الوطني في الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-national-identification-number)</br> - [رقم جواز سفر الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-passport-number) </br> - [رقم الضمان الاجتماعي أو تعريف مكافئ في الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-social-security-number-or-equivalent-identification)</br> - [رقم تعريف الضريبة في الاتحاد الأوروبي](sensitive-information-type-entity-definitions.md#eu-tax-identification-number)|
|الخصوصية| بيانات المعلومات الشخصية (PII) في ألمانيا|- [رقم ترخيص القيادة في ألمانيا](sensitive-information-type-entity-definitions.md#germany-drivers-license-number) </br> - [رقم جواز السفر الألماني](sensitive-information-type-entity-definitions.md#germany-passport-number)| 
|الخصوصية| بيانات المعلومات الشخصية (PII) في إسرائيل|- [رقم التعريف الوطني في إسرائيل](sensitive-information-type-entity-definitions.md#israel-national-identification-number)| 
|الخصوصية| حماية الخصوصية في إسرائيل|- [رقم التعريف الوطني في إسرائيل](sensitive-information-type-entity-definitions.md#israel-national-identification-number)</br> - [رقم الحساب البنكي في إسرائيل](sensitive-information-type-entity-definitions.md#israel-bank-account-number)|
|الخصوصية| تحسين بيانات المعلومات الشخصية (PII) في اليابان|- [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)</br> - [اليابان رقمي - شخصي](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [رقم جواز السفر الياباني](sensitive-information-type-entity-definitions.md#japan-passport-number)</br> - [رقم ترخيص القيادة في اليابان](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية لليابان](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|الخصوصية| بيانات المعلومات الشخصية (PII) في اليابان|- [رقم التسجيل المقيم في اليابان](sensitive-information-type-entity-definitions.md#japan-resident-registration-number) </br> - [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|الخصوصية| تحسين حماية المعلومات الشخصية في اليابان|- [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin) </br> - [اليابان رقمي - شخصي](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [رقم جواز السفر الياباني](sensitive-information-type-entity-definitions.md#japan-passport-number) </br> - [رقم ترخيص القيادة في اليابان](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية لليابان](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|الخصوصية| حماية المعلومات الشخصية في اليابان|- [رقم التسجيل المقيم في اليابان](sensitive-information-type-entity-definitions.md#japan-resident-registration-number)</br> - [رقم التأمين الاجتماعي الياباني (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|الخصوصية| بيانات التعرف الشخصي (PII) في المملكة العربية السعودية|- [الم ID الوطنية للمملكة العربية السعودية](sensitive-information-type-entity-definitions.md#saudi-arabia-national-id)|
|الخصوصية| المملكة المتحدة قانون حماية البيانات|- [رقم التأمين الوطني (NINO) في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|الخصوصية| المملكة المتحدة لوائح الخصوصية والاتصالات الإلكترونية|- [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|الخصوصية| المملكة المتحدة بيانات المعلومات الشخصية (PII)|- [رقم التأمين الوطني (NINO) في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|الخصوصية| المملكة المتحدة مدونة ممارسات المعلومات الشخصية عبر الإنترنت (PIOCP)|- [رقم التأمين الوطني (NINO) في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [رقم خدمة الصحة الوطنية في المملكة المتحدة](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [رمز SWIFT](sensitive-information-type-entity-definitions.md#swift-code)|
|الخصوصية| تعزيز قانون الولايات المتحدة في الولايات المتحدة|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف الممول الفردي (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|الخصوصية| قانون الولايات المتحدة الأمريكية|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [رقم تعريف الممول الفردي (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|الخصوصية| تحسين بيانات المعلومات الشخصية (PII) في الولايات المتحدة|- [رقم تعريف الممول الفردي (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [العناوين الفعلية في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|الخصوصية| بيانات المعلومات الشخصية (PII) في الولايات المتحدة|- [رقم تعريف الممول الفردي (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|الخصوصية| تحسين قوانين الإعلامات المتعلقة بخرق ولاية الولايات المتحدة|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[رقم ترخيص القيادة الأمريكية](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [كل الأسماء الكاملة](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [رقم جواز سفر الولايات المتحدة/المملكة المتحدة](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [كل الشروط والأحكام الطبية](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions)|
|الخصوصية| قوانين الإعلامات المتعلقة بخرق الولايات المتحدة|- [رقم بطاقة الائتمان](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [رقم الحساب البنكي الأميركي](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[رقم ترخيص القيادة الأمريكية](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|الخصوصية| قوانين سرية رقم الضمان الاجتماعي في الولايات المتحدة|- [رقم الضمان الاجتماعي (SSN) في الولايات المتحدة](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|

## <a name="locations"></a>المواقع

يمكن أن يعثر نهج DLP على العناصر التي تحتوي على معلومات حساسة وحمايتها عبر مواقع متعددة.

|الموقع  |النطاق "تضمين/استبعاد"  |حالة البيانات  |المتطلبات الأساسية الإضافية |
|---------|---------|---------|---------|
|Exchange الإلكتروني عبر الإنترنت |مجموعة التوزيع | data-in-motion| لا |
|SharePoint على الإنترنت   |المواقع       | data-at-rest </br> data-in-use | لا|
|OneDrive for Business الحسابات| حساب أو مجموعة توزيع |data-at-rest </br> data-in-use|لا|
|Teams رسائل الدردشة والقناة     | حساب أو مجموعة توزيع |data-in-motion </br> data-in-use |  لا       |
|Microsoft Defender for Cloud Apps   | مثيل تطبيق السحابة       |data-at-rest         | - [استخدام سياسات منع فقدان البيانات للتطبيقات السحابية غير الخاصة ب Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|الأجهزة  |مستخدم أو مجموعة         |data-at-rest </br>  data-in-use </br>  data-in-motion         |- [التعرف على Microsoft 365 فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention) </br>- [بدء استخدام منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention) </br>- [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|المستودعات المحليه (أسهم الملفات SharePoint)    |مستودع         | data-at-rest         | - [التعرف على Microsoft 365 فقدان البيانات](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner) </br> - [بدء استخدام الماسح الضوئي لمنع فقدان البيانات](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|PowerBI| مساحات العمل | data-in-use | لا|

إذا اخترت تضمين مجموعات توزيع معينة في Exchange، سيتم تحديد نطاق نهج DLP لأعضاء تلك المجموعة فقط. وبالمثل، فإن استبعاد مجموعة توزيع سيستبعد جميع أعضاء مجموعة التوزيع هذه من تقييم النهج. يمكنك اختيار تحديد نطاق نهج لأعضاء قوائم التوزيع ومجموعات التوزيع الديناميكية ومجموعات الأمان. لا يمكن أن يحتوي نهج DLP على أكثر من 50 من هذه التضمينات والاستثناءات.

إذا اخترت تضمين مواقع SharePoint أو حسابات OneDrive معينة أو استبعادها، فلا يمكن أن يحتوي نهج DLP على أكثر من 100 من هذه التضمينات والاستثناءات. على الرغم من وجود هذا الحد، يمكنك تجاوز هذا الحد عن طريق تطبيق نهج على مستوى المؤسسة أو نهج ينطبق على مواقع بأكملها.

إذا اخترت تضمين حسابات أو مجموعات OneDrive معينة أو استبعادها، فلا يمكن أن يحتوي نهج DLP على أكثر من 100 حساب مستخدم أو 50 مجموعة كضمان أو استثناء.

### <a name="location-support-for-how-content-can-be-defined"></a>دعم الموقع لكيفية تعريف المحتوى

تكتشف سياسات DLP العناصر الحساسة من خلال مطابقتها مع نوع معلومات حساس (SIT) أو تسمية حساسية أو تسمية استبقاء. يدعم كل موقع أساليب مختلفة لتعريف المحتوى الحساس. عندما تقوم بدمج المواقع في نهج، يمكن أن تتغير كيفية تعريف المحتوى عن كيفية تعريفه بواسطة موقع واحد. 

> [!IMPORTANT]
> عند تحديد مواقع متعددة لنمع ما، تكون الأسبقية لقيمة "لا" لفئة تعريف المحتوى على القيمة "نعم". على سبيل المثال، عند SharePoint مواقع الويب فقط، سيدعم النهج الكشف عن العناصر الحساسة بواسطة عنصر واحد أو أكثر من SIT أو تسمية الحساسية أو تسمية الاستبقاء. ولكن، عند تحديد ***SharePoint ومواقع Teams*** رسائل القناة والدردشة، فإن النهج سيدعم فقط الكشف عن العناصر الحساسة بواسطة SIT.

|الموقع| يمكن تعريف المحتوى بواسطة SIT| يمكن تعريف المحتوى كتسمية حساسية| يمكن تعريف المحتوى بواسطة تسمية استبقاء|
|---------|---------|---------|---------|
|Exchange الإلكتروني عبر الإنترنت|نعم| نعم| لا|
|SharePoint على الإنترنت| نعم| نعم| نعم|
|OneDrive for Business الحسابات| نعم| نعم| نعم|
|Teams رسائل الدردشة والقناة | نعم| لا| لا|
|الأجهزة |نعم | نعم|  لا|
|Microsoft Defender for Cloud Apps | نعم| نعم| نعم|
|المستودعات المحلي| نعم| نعم| لا|
|PowerBI|نعم | نعم| لا|

> [!NOTE]
> تدعم DLP الكشف عن تسميات الحساسية في رسائل البريد الإلكتروني والمرفقات راجع استخدام تسميات الحساسية كالشروط [في سياسات DLP](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>القواعد

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

القواعد هي منطق العمل لنهج DLP. وهي تتكون من:

- [**الشروط**](#conditions) التي يتم تشغيل النهج عند مطابقتها
- [**استثناءات**](#exceptions) الشروط
- [**الإجراءات**](#actions) التي يجب اتخاذها عند تشغيل النهج
- [**إعلامات المستخدمين**](#user-notifications-and-policy-tips) لإعلام المستخدمين عند قيامهم بشيء ما يقوم بتشغيل نهج ومساعدتهم على تعليمهم كيفية تعامل المؤسسة مع المعلومات الحساسة
- [**تجاوز المستخدم**](#user-overrides) عند تكوينه من قبل مسؤول، السماح للمستخدمين بتجاوز إجراء حظر بشكل انتقائي
- [**تقارير الحوادث التي**](#incident-reports) تخطر المسؤولين والمساهمين الرئيسيين الآخرين عند حدوث تطابق للقاعدة
- [**خيارات إضافية**](#additional-options) تحدد أولوية تقييم القواعد ويمكنها إيقاف المزيد من معالجة القواعد والسياسات.

 يحتوي النهج على قواعد واحدة أو أكثر. يتم تنفيذ القواعد بشكل تسلسلي، بدءا من القاعدة الأعلى أولوية في كل نهج.

### <a name="the-priority-by-which-rules-are-processed"></a>الأولوية التي تتم بها معالجة القواعد

#### <a name="hosted-service-workloads"></a>أحمال عمل الخدمة المستضافة

بالنسبة إلى أحمال عمل الخدمة المستضافة، مثل Exchange Online و SharePoint عبر الإنترنت و OneDrive for Business، يتم تعيين أولوية لكل قاعدة بالترتيب الذي يتم به إنشاؤها. وهذا يعني أن القاعدة التي تم إنشاؤها لها الأولوية الأولى، والقاعدة التي تم إنشاؤها الثانية لها الأولوية الثانية، وهكذا. 
  
![القواعد في ترتيب الأولوية](../media/dlp-rules-in-priority-order.png)

عند تقييم المحتوى وفقا للقواعد، تتم معالجة القواعد في ترتيب الأولوية. إذا تطابق المحتوى مع قواعد متعددة، يتم فرض القاعدة الأولى التي تم تقييمها التي لها *الإجراء* الأكثر تقييدا. على سبيل المثال، إذا تطابق المحتوى مع كل القواعد التالية، يتم فرض القاعدة *3* لأنها القاعدة الأعلى أولوية والأكثر تقييدا:
  
- القاعدة 1: يتم فقط اعريف المستخدمين
- القاعدة 2: تقوم ب تعريف المستخدمين وتقييد الوصول وتسمح بتجاوز المستخدم
- *القاعدة 3: تقوم ب تعريف المستخدمين وتقييد الوصول ولا تسمح بتجاوز المستخدم*
- القاعدة 4: تقييد الوصول

سيتم تقييم القواعد 1 و2 و4، ولكن لن يتم تطبيقها. في هذا المثال، يتم تسجيل تطابقات كافة القواعد في سجلات التدقيق كما تظهر في تقارير DLP، على الرغم من تطبيق القاعدة الأكثر تقييدا فقط.

يمكنك استخدام قاعدة لتلبية متطلبات حماية معينة، ثم استخدام نهج DLP ل تجميع متطلبات الحماية الشائعة معا، مثل كل القواعد اللازمة للامتثال لأنظمة معينة.
  
على سبيل المثال، قد يكون لديك نهج DLP يساعدك على الكشف عن وجود معلومات تخضع إلى قانون قابلية النقل والمسؤولية في التأمين الصحي (HIPAA). يمكن أن يساعد نهج DLP هذا في حماية بيانات HIPAA (ماذا) عبر كل مواقع SharePoint عبر الإنترنت وجميع مواقع OneDrive for Business (المكان) عن طريق العثور على أي مستند يحتوي على هذه المعلومات الحساسة التي تمت مشاركتها مع أشخاص من خارج مؤسستك (الشروط) ثم حظر الوصول إلى المستند وإرسال إعلام (الإجراءات). يتم تخزين هذه المتطلبات كقود فردية ويتم تجميعها معا ك نهج DLP لتبسيط الإدارة وإعداد التقارير.
  
![يعرض الرسم التخطيطي أن نهج DLP يحتوي على مواقع وقواعد](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>لنقاط النهاية

يتم أيضا تعيين الأولوية للقواعد على نقاط النهاية وفقا الترتيب الذي تم إنشاؤه به. وهذا يعني أن القاعدة التي تم إنشاؤها لها الأولوية الأولى، والقاعدة التي تم إنشاؤها الثانية لها الأولوية الثانية، وهكذا. 

عندما يتطابق ملف في نقطة نهاية مع العديد من سياسات DLP، فإن القاعدة الأولى التي يتم تمكينها مع القيود هي القاعدة التي يتم فرضها على المحتوى. على سبيل المثال، إذا تطابق المحتوى مع كل القواعد التالية، يتم فرض القاعدة 2 لأنها القاعدة ذات الأولوية الأعلى التي تم تكوينها *مع قيد*.
  
- القاعدة 1: يتم فقط اعريف المستخدمين
- *القاعدة 2: تقوم ب تعريف المستخدمين وتقييد الوصول وتسمح بتجاوز المستخدم*
- القاعدة 3: تقوم ب تعريف المستخدمين وتقييد الوصول ولا تسمح بتجاوز المستخدم
- القاعدة 4: تقييد الوصول

سيتم تقييم القواعد 1 و3 و4، ولكن لن يتم تطبيقها. في هذا المثال، يتم تسجيل تطابقات كافة القواعد في سجلات التدقيق كما تظهر في تقارير DLP، على الرغم من تطبيق القاعدة الأولى التي تتضمن قيدا فقط.

بالنسبة إلى القواعد التي يتم تطبيقها على نقاط النهاية، يمكنك الاستفادة من إمكانية إعادة ترتيب أولوية القاعدة للتأكد من تطبيق القيود التي تريد تطبيقها.

### <a name="conditions"></a>الشروط

تكون الشروط شاملة وتعرف فيها ما تريد أن تبحث عنه القاعدة وسياق يتم فيه استخدام هذه العناصر. فهي تعلم القاعدة &#8212; عندما تعثر على عنصر يشبه هذا العنصر ويستخدم على هذا &#8212; يكون  متطابقا ويجب اتخاذ باقي  الإجراءات في النهج عليه. يمكنك استخدام الشروط لتعيين إجراءات مختلفة إلى مستويات مخاطر مختلفة. على سبيل المثال، قد يكون المحتوى الحساس الذي تمت مشاركته داخليا أقل عرضة للمخاطر وقد يتطلب إجراءات أقل من المحتوى الحساس الذي تمت مشاركته مع أشخاص من خارج المؤسسة.

> [!NOTE]
> يعتبر المستخدمون الذين لديهم حسابات غير ضيوف في مستأجر Active Directory أو Azure Active Directory في المؤسسة المضيفة أشخاصا داخل المؤسسة. 

#### <a name="content-contains"></a>يحتوي المحتوى على

 تدعم كل المواقع **احتواء المحتوى** على شرط. يمكنك تحديد مثيلات متعددة لكل نوع محتوى وتحسين الشروط بشكل أكبر باستخدام أي من عوامل **التشغيل (OR** المنطقية) أو كل **هذه (** المنطقية AND):

- [أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [تسميات الحساسية](sensitivity-labels.md)
- [تسميات الاستبقاء](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

استنادا إلى [الموقع (المواقع)](#location-support-for-how-content-can-be-defined) الذي تختار تطبيق النهج عليه. 

ستبحث القاعدة فقط عن وجود أي تسميات حساسية  وتسميات **استبقاء** تختارها. 

لدى SITs مستوى ثقة معرف [**مسبقا**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) يمكنك تغييره إذا لزم الأمر. لمزيد من المعلومات، راجع [المزيد حول مستويات الثقة](sensitive-information-type-learn-about.md#more-on-confidence-levels). 

> [!IMPORTANT]
> لدى SITs طريقتان مختلفتان لتعريف معلمات الحد الأقصى لعد المثيل الفريد. لمعرفة المزيد، راجع [عدد المثيلات القيم المعتمدة ل SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>سياق الشرط

تتغير خيارات السياق المتوفرة استنادا إلى الموقع الذي تختاره. إذا حددت مواقع متعددة، فتتوفر الشروط المشتركة بين المواقع فقط.

##### <a name="conditions-exchange-supports"></a>الشروط Exchange الدعم

- يحتوي المحتوى على
- يتم مشاركة المحتوى من Microsoft 365
- يتم تلقي المحتوى من
- عنوان IP المرسل هو
- هل تجاوز المرسل تلميح النهج
- المرسل هو
- مجال المرسل هو
- يحتوي عنوان المرسل على كلمات
- يحتوي عنوان المرسل على أنماط
- تحتوي سمة AD المرسل على كلمات أو عبارات
- تطابق سمة AD المرسل الأنماط
- المرسل هو عضو في
- لا يمكن فحص أي محتوى مرفق بريد إلكتروني
- لم يكمل أي محتوى مرفق بريد إلكتروني عملية المسح الضوئي
- المرفق محمي بكلمة مرور
- ملحق الملف هو
- المستلم هو عضو في
- مجال المستلم هو
- المستلم هو
- يحتوي عنوان المستلم على كلمات
- يتطابق عنوان المستلم مع الأنماط
- تحتوي السمة AD للمستلم على كلمات أو عبارات
- تطابق سمة AD للمستلم الأنماط
- يحتوي اسم المستند على كلمات أو عبارات
- اسم المستند يتطابق مع الأنماط
- الخاصية "مستند" هي
- حجم المستند يساوي أو أكبر من
- يحتوي محتوى المستند على كلمات أو عبارات
- يتطابق محتوى المستند مع الأنماط
- يحتوي الموضوع على كلمات أو عبارات
- يتطابق الموضوع مع الأنماط
- يحتوي الموضوع أو النص النصي على كلمات أو عبارات
- يتطابق الموضوع أو الجسم مع الأنماط
- تحتوي مجموعة أحرف المحتوى على كلمات
- يحتوي الرأس على كلمات أو عبارات
- يتطابق الرأس مع الأنماط
- حجم الرسالة يساوي أو أكبر من
- نوع الرسالة هو
- أهمية الرسالة هي

##### <a name="conditions-sharepoint-supports"></a>الشروط SharePoint الدعم
 
- يحتوي المحتوى على
- يتم مشاركة المحتوى من Microsoft 365
- ملحق الملف هو
- الخاصية "مستند" هي

##### <a name="conditions-onedrive-accounts-supports"></a>الشروط OneDrive الحسابات

- يحتوي المحتوى على
- يتم مشاركة المحتوى من Microsoft 365
- ملحق الملف هو
- الخاصية "مستند" هي

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>الشروط Teams دعم رسائل الدردشة والقناة

- يحتوي المحتوى على
- يتم مشاركة المحتوى من Microsoft 365
- المرسل هو (معاينة)
- مجال المرسل هو (معاينة)
- مجال المستلم هو (معاينة)
- المستلم هو (معاينة)

##### <a name="conditions-devices-supports"></a>الشروط تدعم الأجهزة

- يحتوي المحتوى على
- راجع أنشطة [نقطة النهاية التي يمكنك مراقبتها واتخاذ إجراء بشأنها](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>الشروط Microsoft Defender for Cloud Apps الدعم

- يحتوي المحتوى على
- يتم مشاركة المحتوى من Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>دعم مستودعات الشروط المحلية

- يحتوي المحتوى على
- ملحق الملف هو
- الخاصية "مستند" هي

##### <a name="conditions-powerbi-supports"></a>الشروط التي يدعمها PowerBI

- يحتوي المحتوى على

#### <a name="condition-groups"></a>مجموعات الشرط

قد تحتاج في بعض الأحيان إلى قاعدة لتحديد شيء واحد فقط، مثل كل المحتوى الذي يحتوي على رقم الضمان الاجتماعي الأميركي، الذي يتم تعريفه بواسطة نظام SIT واحد. ولكن في العديد من السيناريوهات، حيث تكون أنواع العناصر التي تحاول تحديدها أكثر تعقيدا، وبالتالي يصعب تعريفها، يلزم توفر المزيد من المرونة في تحديد الشروط.

على سبيل المثال، لتحديد المحتوى الذي يخضع إلى قانون التأمين الصحي (HIPAA)، يجب البحث عن:
  
- المحتوى الذي يحتوي على أنواع معينة من المعلومات الحساسة، مثل رقم الضمان الاجتماعي أو رقم وكالة مكافحة المخدرات (DEA) الأمريكية.
    
    AND
    
- المحتوى الذي يصعب التعرف عليه، مثل الاتصالات حول رعاية أحد المرضى أو أوصاف الخدمات الطبية المتوفرة. يتطلب تحديد هذا المحتوى تطابق الكلمات الأساسية من قوائم الكلمات الأساسية الكبيرة، مثل التصنيف الدولي ل الطبي (ICD-9-CM أو ICD-10-CM).
    
يمكنك تحديد هذا النوع من البيانات من خلال تجميع الشروط واستخدام عوامل التشغيل المنطقية (AND و OR) بين المجموعات.
    
بالنسبة إلى **قانون التأمين الصحي (HIPPA)** في الولايات المتحدة، يتم تجميع الشروط كما يلي:

![شروط نهج HIPPA](../media/dlp-rules-condition-groups-booleans.png)

تحتوي المجموعة الأولى على  SITs التي تحدد وتحتوي المجموعة الثانية على  SITs التي تحدد التشخيصات الطبية.

### <a name="exceptions"></a>الاستثناءات

في القواعد، تحدد الاستثناءات الشروط التي يتم استخدامها لاستبعاد عنصر من النهج. منطقيا، الشروط الحصرية التي يتم تقييمها بعد الشروط الشاملة والسياقات. فهي تعلم القاعدة &#8212; عندما تعثر على عنصر يشبه هذا العنصر ويستخدم كما لو كان متطابقا ويجب أن يتم اتخاذ  باقي الإجراءات في النهج عليه إلا ***إذا كان &#8212;*** 

على سبيل المثال، مع الحفاظ على نهج HIPPA، يمكننا تعديل القاعدة لاستبعاد أي عنصر يحتوي على رقم ترخيص برامج تشغيل بلجيكا، كما يلي:

![نهج HIPPA مع الاستثناءات](../media/dlp-rule-exceptions.png)

تكون شروط الاستثناءات المعتمدة حسب الموقع متطابقة مع كل شروط التضمين مع وجود الفرق الوحيد الذي يكون معلقا ل "إلا إذا" لكل شرط معتمد. إذا احتوى أحد القواعد على استثناءات فقط، فإنه سيتم تطبيقه على كل رسائل البريد الإلكتروني أو الملفات التي لا تفي بمعايير الاستثناء.

تماما كما تدعم كل المواقع الشرط الشامل:

- يحتوي المحتوى على

سيكون الاستثناء:

- **باستثناء ما إذا** كان المحتوى يحتوي على 

### <a name="actions"></a>الإجراءات 

سيكون لأي عنصر يقوم به من خلال عوامل التصفية الشاملة ***conditions** _ والاستثناءات الحصرية أي إجراءات _**_ تم تعريفها في القاعدة المطبقة عليه._**_ يجب تكوين الخيارات المطلوبة لدعم الإجراء. على سبيل المثال، إذا حددت Exchange باستخدام الإجراء _تقييد الوصول أو تشفير المحتوى في *Microsoft 365* المواقع* ، يجب الاختيار من بين هذه الخيارات:

- حظر المستخدمين من الوصول إلى SharePoint OneDrive ومحتوى Teams المشترك
    - حظر الجميع. سيبقى حق الوصول إلى مالك المحتوى والمعدل الأخير ومسؤول الموقع فقط
    - حظر الأشخاص من خارج مؤسستك فقط. سيستمر المستخدمون داخل مؤسستك في الوصول.
- تشفير رسائل البريد الإلكتروني (ينطبق فقط على المحتوى في Exchange)

تعتمد الإجراءات المتوفرة في قاعدة ما على المواقع التي تم تحديدها. إذا قمت بتحديد موقع واحد فقط لكي يتم تطبيق النهج عليه، يتم سرد الإجراءات المتوفرة أدناه.

> [!IMPORTANT]
> بالنسبة SharePoint سيتم حظر مستندات مواقع OneDrive for Business عبر الإنترنت ومواقع الإنترنت بشكل استباقي مباشرة بعد الكشف عن المعلومات الحساسة، بغض النظر عما إذا كان المستند مشتركا أم لا، لجميع المستخدمين الخارجيين، بينما سيستمر وصول المستخدمين الداخليين إلى المستند.

#### <a name="exchange-location-actions"></a>Exchange الموقع

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع
- تعيين رؤوس
- إزالة الرأس
- إعادة توجيه الرسالة إلى مستخدمين محددين
- إعادة توجيه الرسالة للموافقة عليها إلى مدير المرسل
- إعادة توجيه الرسالة للموافقة عليها إلى موافقين محددين
- إضافة مستلم إلى المربع إلى
- إضافة مستلم إلى المربع نسخة
- إضافة مستلم إلى المربع "مستلم"
- إضافة مدير المرسل كمستلم
- تشفير الرسائل وحماية الحقوق في O365 التي تمت إزالتها
- موضوع البريد الإلكتروني المبلل مسبقا
- تعديل موضوع البريد الإلكتروني
- إضافة إخلاء المسؤولية ل HTML

#### <a name="sharepoint-sites-location-actions"></a>SharePoint مواقع الويب

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع

#### <a name="onedrive-account-location-actions"></a>OneDrive موقع الحساب

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع

#### <a name="teams-chat-and-channel-messages-actions"></a>Teams الدردشة ورسائل القناة

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع

#### <a name="devices-actions"></a>إجراءات الأجهزة

- تدقيق الأنشطة أو تقييدها على Windows الأجهزة

لاستخدام هذه الإعدادات، يجب تكوين الخيارات في إعدادات **DLP** وفي النهج الذي تريد استخدامها فيه. لمزيد من المعلومات، راجع [التطبيقات المحظورة ومجموعات](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) التطبيقات.

يوفر موقع الأجهزة العديد من الإجراءات والأفعال الفرعية. لمعرفة المزيد، راجع [أنشطة نقطة النهاية التي يمكنك مراقبتها واتخاذ إجراء بشأنها](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on).

عند تحديد **التدقيق** أو تقييد الأنشطة على أجهزة Windows، يمكنك تقييد أنشطة المستخدم حسب مجال الخدمة أو المستعرض، وتحديد نطاق الإجراءات التي يتخذها DLP من خلال:

- جميع التطبيقات
- قائمة التطبيقات المقيدة التي تحددها
- مجموعة تطبيقات مقيدة (معاينة) تحددها.

##### <a name="service-domain-and-browser-activities"></a>مجال الخدمة وأنشطة المستعرض

عند تكوين مجالات السماح **/** حظر خدمة السحابة وقائمة المستعرضات غير  المسموح بها (راجع قيود المستعرض والمجال للبيانات الحساسة [)](dlp-configure-endpoint-settings.md#browser-and-domain-restrictions-to-sensitive-data)`Audit only` ويحاول المستخدم تحميل ملف محمي إلى مجال خدمة سحابية أو الوصول إليه من مستعرض غير مسموح به، يمكنك تكوين إجراء النهج إلى أو `Block with override`أو `Block` أو النشاط.

##### <a name="file-activities-for-all-apps"></a>أنشطة الملفات لجميع التطبيقات

باستخدام **الخيار أنشطة الملف لكل التطبيقات** ، يمكنك تحديد إما عدم تقييد أنشطة **الملفات** أو تطبيق **قيود على أنشطة معينة**. عندما تحدد تطبيق قيود على أنشطة معينة، يتم تطبيق الإجراءات التي تحددها هنا عند وصول مستخدم إلى عنصر محمي من DLP. يمكنك إخبار DLP ب `Audit only`، `Block with override`و `Block` (الإجراءات) على أنشطة المستخدمين هذه:

- **نسخ إلى الحافظة**
- **النسخ إلى محرك أقراص USB قابل للإزالة** 
- **النسخ إلى مشاركة شبكة**
- **طباعة**
- **النسخ أو التنقل باستخدام تطبيق Bluetooth غير مسموح به**
- **خدمات سطح المكتب البعيد**


##### <a name="restricted-app-activities"></a>أنشطة التطبيق المقيدة  

سابقا، تعرف قائمة التطبيقات في إعدادات DLP لنقطة النهاية التي تريد وضع قيود عليها. عندما يحاول المستخدم الوصول إلى ملف محمي بواسطة DLP `Audit only`باستخدام تطبيق في القائمة، يمكنك إما أو `Block with override`أو `Block` أو النشاط. يتم تجاوز إجراءات DLP  المعرفة في أنشطة التطبيق المقيدة إذا كان التطبيق عضوا في مجموعة تطبيقات مقيدة. بعد ذلك، يتم تطبيق الإجراءات المعرفة في مجموعة التطبيقات المقيدة.

##### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>أنشطة الملفات للتطبيقات في مجموعات التطبيقات المقيدة (معاينة)

يمكنك تعريف مجموعات التطبيقات المقيدة في إعدادات DLP في نقطة النهاية وإضافة مجموعات تطبيقات مقيدة إلى سياساتك. عند إضافة مجموعة تطبيقات مقيدة إلى نهج، يجب تحديد أحد الخيارات التالية:

- عدم تقييد نشاط الملف
- تطبيق قيود على كل الأنشطة
- تطبيق قيود على نشاط معين

عند تحديد أي من خيارات تطبيق  القيود، ويحاول المستخدم الوصول إلى ملف محمي باستخدام DLP `Audit only`باستخدام تطبيق في مجموعة التطبيقات المقيدة، يمكنك إما أو `Block with override`أو `Block` حسب النشاط. تتجاوز إجراءات DLP التي تحددها هنا إجراءات التجاوز المحددة في  أنشطة التطبيق المقيدة وأنشطة **الملف لكل تطبيقات** التطبيق.

لمزيد من المعلومات، راجع [التطبيقات المحظورة ومجموعات](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) التطبيقات. 

#### <a name="microsoft-defender-for-cloud-apps-actions"></a>Microsoft Defender for Cloud Apps الإجراءات

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع
- تقييد تطبيقات  الأطراف الخارجية

#### <a name="on-premises-repositories-actions"></a>إجراءات المستودعات المحلي

- تقييد الوصول إلى الملفات الموجودة في الموقع أو إزالتها

#### <a name="powerbi-actions"></a>إجراءات PowerBI

- إعلام المستخدمين بالبريد الإلكتروني وتلميحات النهج
- إرسال تنبيهات إلى المسؤول

#### <a name="actions-available-when-you-combine-locations"></a>الإجراءات المتوفرة عند دمج المواقع

إذا قمت بتحديد Exchange وأي موقع مفرد آخر يتم تطبيق النهج عليه، ف

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع

و

- كل الإجراءات الخاصة بموقع غير Exchange

ستكون الإجراءات متوفرة.

إذا قمت بتحديد موقعين أو أكثر Exchange غير مطبقة على النهج، ف

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع

AND

- جميع الإجراءات للمواقع غير Exchange 

ستكون الإجراءات متوفرة.

على سبيل المثال، إذا حددت Exchange والأجهزة كمواد، ستكون هذه الإجراءات متوفرة:

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع
- تدقيق الأنشطة أو تقييدها على Windows الأجهزة

إذا قمت بتحديد الأجهزة Microsoft Defender for Cloud Apps، ستكون هذه الإجراءات متوفرة:

- تقييد الوصول إلى المحتوى أو تشفيره في Microsoft 365 المواقع
- تدقيق الأنشطة أو تقييدها على Windows الأجهزة
- تقييد تطبيقات  الأطراف الخارجية

يتوقف ما إذا كان أحد الإجراءات سيتوقف على كيفية تكوين وضع النهج. يمكنك اختيار تشغيل النهج في وضع الاختبار مع إظهار تلميح النهج أو بدونه عن طريق تحديد الخيار **اختباره أولا** . يمكنك اختيار تشغيل النهج بمجرد ساعة واحدة من إنشائه عن طريق تحديد الخيار تشغيل على الفور، أو يمكنك اختيار  حفظه فقط ثم الرجوع إلى النهج في وقت لاحق عن طريق تحديد الخيار إيقاف تشغيله. 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>إعلامات المستخدم وتلميحات النهج

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

عندما يحاول مستخدم إجراء على عنصر حساس في سياق يلبي الشروط والاستثناءات الخاصة بالقاعدة، يمكنك إعلامه بذلك من خلال رسائل البريد الإلكتروني الخاصة بإعلام المستخدم وفي نوافذ تلميح نهج السياق. هذه الإعلامات مفيدة لأنها تزيد من الوعي وتساعد على تعليم الأشخاص حول سياسات DLP في مؤسستك.

على سبيل المثال، محتوى مثل Excel مصنف على موقع OneDrive for Business يحتوي على معلومات تعريف شخصية (PII) تمت مشاركته مع ضيف.

![يعرض شريط الرسائل تلميح النهج في Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!NOTE]
> يتم إرسال رسائل البريد الإلكتروني الإعلامية بدون حماية.

يمكنك أيضا منح الأشخاص خيار تجاوز النهج، [](#user-overrides)بحيث لا يتم حظرهم إذا كانت لديهم حاجة أعمال صالحة أو إذا كشف النهج عن إيجابية خاطئة.

تختلف خيارات تكوين إعلامات المستخدمين وتلميحات النهج باختلاف مواقع المراقبة التي حددتها. إذا قمت بتحديد:

- Exchange
- SharePoint
- OneDrive
- Teams الدردشة والقناة
- Defender for Cloud Apps


يمكنك تمكين/تعطيل إعلامات المستخدمين لتطبيقات Microsoft المختلفة، راجع مرجع تلميحات [نهج منع فقدان البيانات](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- يمكنك تمكين/تعطيل إعلام المستخدمين **Office 365 الخدمة** باستخدام تلميح نهج.
    - إعلامات البريد الإلكتروني للمستخدم الذي أرسل المحتوى أو قام بمشاركته أو تعديله آخر مرة
    - إعلام أشخاص محددين

وخصص نص البريد الإلكتروني والموضوع ونص تلميح النهج.

![خيارات تكوين إعلام المستخدم وتلميح النهج المتوفرة Exchange و SharePoint و OneDrive و Teams الدردشة والقناة و Defender for Cloud Apps](../media/dlp-user-notification-non-devices.png)

إذا قمت بتحديد الأجهزة فقط، ستحصل على كل الخيارات نفسها المتوفرة ل Exchange و SharePoint و OneDrive و Teams الدردشة والقناة و Defender لتطبيقات السحابة بالإضافة إلى خيار تخصيص عنوان الإعلام والمحتوى الذي يظهر على جهاز Windows 10.

![خيارات تكوين تلميح النهج وإعلام المستخدم المتوفرة للأجهزة](../media/dlp-user-notification-devices.png)  

يمكنك تخصيص عنوان النص والنص الأساسي باستخدام هذه المعلمات. يدعم النص الأساسي ما يلي:

|الاسم الشائع  |المعلمة  |مثال
|---------|---------|---------|
|اسم الملف     |٪٪FileName٪٪ | Contoso doc 1 |
|اسم العملية     |٪٪ProcessName٪٪ | Word |
|اسم النهج     |٪٪PolicyName٪٪| Contoso سري للغاية |
|إجراء | ٪٪AppliedActions٪٪ | لصق محتوى المستند من الحافظة إلى تطبيق آخر |

**يستبدل ٪٪AppliedActions٪٪** هذه القيم في نص الرسالة:


|اسم الإجراء الشائع |قيمة تم استبدالها ب ٪٪AppliedActions٪٪ المعلمة |
|---------|---------|
|النسخ إلى مساحة تخزين قابلة للإزالة    |*الكتابة إلى مساحة تخزين قابلة للإزالة*         |
|النسخ إلى مشاركة الشبكة     |*الكتابة إلى مشاركة شبكة*         |
|طباعة     |*الطباعة*         |
|لصق من الحافظة  |*اللصق من الحافظة*         |
|النسخ عبر bluetooth   |*التحويل عبر Bluetooth*         |
|فتح باستخدام تطبيق غير مسموح به     |*فتح باستخدام هذا التطبيق*         |
|النسخ إلى سطح مكتب بعيد (RDP)     |*النقل إلى سطح المكتب البعيد*         |
|التحميل إلى موقع ويب غير مسموح به     |*التحميل إلى هذا الموقع*         |
|الوصول إلى العنصر عبر مستعرض غير مسموح به     |*فتح باستخدام هذا المستعرض*         |

استخدام هذا النص المخصص

*٪٪AppliedActions٪٪ اسم الملف ٪٪FileName٪٪ عبر ٪٪ProcessName٪٪ غير مسموح به من قبل مؤسستك. انقر فوق "السماح" إذا كنت تريد تجاوز النهج ٪٪PolicyName٪٪* 

ينتج هذا النص في الإعلام المخصص:

*اللصق من اسم ملف الحافظة: لا تسمح مؤسستك باستخدام Contoso doc 1 عبر WINWORD.EXE. انقر فوق الزر "السماح" إذا كنت تريد تجاوز النهج Contoso سري للغاية*
 

> [!NOTE]
> لا تتوفر إعلامات المستخدمين وتلميحات النهج للموقع

> [!NOTE]
> سيتم عرض تلميح النهج فقط من أعلى أولوية وأكثر قاعدة تقييدا. على سبيل المثال، سيتم عرض تلميح نهج من قاعدة تمنع الوصول إلى المحتوى عبر تلميح نهج من قاعدة ترسل ببساطة إعلاما. يمنع هذا الأشخاص من رؤية تتالي تلميحات النهج.

لمعرفة المزيد حول تكوين إعلام المستخدم وتلميح النهج واستخدامه، بما في ذلك كيفية تخصيص الإعلام ونص التلميح، راجع 
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

الهدف من تجاوز  المستخدم هو منح المستخدمين طريقة لتجاوز إجراءات حظر نهج DLP على العناصر الحساسة في Exchange أو SharePoint أو OneDrive أو Teams بحيث يمكنهم متابعة عملهم. يتم تمكين تجاوز المستخدم فقط عندما يتم تمكين إعلام المستخدمين في خدمات **Office 365** باستخدام تلميح نهج، وبالتالي فإن تجاوز المستخدم يتم بشكل متكاتف مع الإعلامات وتلميحات النهج. 

![خيارات تجاوز المستخدم لن نهج DLP](../media/dlp-user-overrides.png)

> [!NOTE]
> لا تتوفر تجاوزات المستخدم لموقع المستودعات المحلية.

عادة ما تكون تجاوزات المستخدم مفيدة عند طرح مؤسستك لن نهج لأول مرة. تساعد الملاحظات التي تحصل عليها من أي مبررات تجاوز وتحديد إيجابيات خاطئة في ضبط النهج. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- إذا كانت تلميحات النهج في القاعدة الأكثر تقييدا تسمح للأشخاص بتجاوز القاعدة، فإن تجاوز هذه القاعدة يتجاوز أيضا أي قواعد أخرى تطابق المحتوى.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
لمعرفة المزيد حول تجاوزات المستخدم، راجع:

- [عرض التبرير الذي تم إرساله من قبل مستخدم لتجاوز](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>تقارير الحوادث

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

عند مطابقة قاعدة، يمكنك إرسال تقرير عن حادث إلى مسؤول التوافق (أو أي أشخاص تختارهم) مع تفاصيل الحدث. يتضمن التقرير معلومات حول العنصر الذي تطابق والمحتوى الفعلي الذي تطابق مع القاعدة واسم الشخص الذي قام بتعديل المحتوى آخر مرة. بالنسبة لرسائل البريد الإلكتروني، يتضمن التقرير أيضا كمرفق الرسالة الأصلية التي تطابق نهج DLP.

يغذي DLP معلومات حادث Microsoft 365 أخرى لحماية المعلومات، مثل [إدارة مخاطر Insider في Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365). للحصول على معلومات حول الحادث لإدارة مخاطر insider، يجب تعيين مستوى خطورة تقارير الحوادث  إلى **مستوى عال**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

يمكن إرسال التنبيهات في كل مرة يتطابق فيها نشاط مع قاعدة، والتي قد تكون صاخبة أو يمكن تجميعها في تنبيهات أقل استنادا إلى عدد من تطابقات العناصر أو حجمها خلال فترة زمنية معينة.

![إرسال تنبيه في كل مرة تطابق قاعدة ما أو تجمعها مع الوقت في تقارير أقل](../media/dlp-incident-reports-aggregation.png)

تقوم DLP بفحص البريد الإلكتروني بشكل مختلف عن SharePoint عبر الإنترنت أو OneDrive for Business أخرى. في SharePoint عبر الإنترنت OneDrive for Business، يقوم DLP بفحص العناصر الموجودة بالإضافة إلى العناصر الجديدة وإنشاء تقرير حادث كلما تم العثور على تطابق. في Exchange Online، يقوم DLP بفحص رسائل البريد الإلكتروني الجديدة فقط وإنشاء تقرير إذا كان هناك تطابق في النهج. لا تقوم DLP ***بفحص*** عناصر البريد الإلكتروني الموجودة مسبقا المخزنة في علبة بريد أو أرشفة أو تطابقها.

### <a name="additional-options"></a>خيارات إضافية

إذا كان لديك قواعد متعددة في نهج ما، يمكنك استخدام الخيارات الإضافية  للتحكم في معالجة القواعد الإضافية إذا كانت هناك مطابقة للقاعدة التي تقوم بتحريرها بالإضافة إلى تعيين أولوية تقييم القاعدة.

## <a name="see-also"></a>راجع أيضًا

- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
