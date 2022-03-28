---
title: دالات نوع المعلومات الحساسة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: low
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: تعرف على ما تبحث عنه دالات نوع المعلومات الحساسة.
ms.openlocfilehash: d00b61aeeb435940436bd0c901edce2fef81a3e4
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63574765"
---
# <a name="sensitive-information-type-functions"></a>دالات نوع المعلومات الحساسة

يمكن أن تستخدم أنواع المعلومات الحساسة (SIT) الدالات كعناصر أساسية لتحديد العناصر الحساسة. على سبيل المثال، يستخدم نوع المعلومات الحساسة لرقم بطاقة الائتمان الدالة Func_credit_card للكشف عن رقم بطاقة الائتمان.

تشرح هذه المقالة ما تبحث عنه هذه الدالات، لمساعدتك على فهم كيفية عمل أنواع المعلومات الحساسة المحددة مسبقا. لمزيد من المعلومات، راجع [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>جدول الدالات

|اسم الدالة | إجراء الدالة | هو أداة التحقق من صحة|
|---------|----------|---------|
|Func_aba_routing|الكشف عن رقم توجيه ABA|نعم|
|Func_alabama_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ألاباما|لا|
|Func_alaska_delaware_oregon_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ألاسكا و Delaware و Oregon|لا|
|Func_alaska_drivers_license_number|الكشف عن رقم ترخيص القيادة في ألاسكا|لا|
|Func_alberta_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ألبيرتا|لا|
|Func_argentina_Unique_Tax_Key|الكشف عن مفتاح الضريبة الفريد في Argentina والتحقق من صحته|لا|
|Func_Argentina_Unique_Tax_Key|الكشف عن مفتاح الضريبة الفريد في Argentina|لا|
|Func_arizona_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل أريزونا|لا|
|Func_arkansas_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Arkansas|لا|
|Func_australian_business_number|الكشف عن رقم الأعمال في أستراليا|لا|
|Func_Australian_Company_Number|الكشف عن رقم الشركة في أستراليا|لا|
|Func_australian_medical_account_number|الكشف عن رقم الحساب الطبي في أستراليا|لا|
|Func_australian_tax_file_number|الكشف عن رقم ملف ضريبة أستراليا|نعم|
|Func_austria_eu_ssn_or_equivalent|الكشف عن رقم الضمان الاجتماعي في النمسا|لا|
|Func_austria_eu_tax_file_number|الكشف عن رقم ملف ضريبة النمسا|لا|
|Func_Austria_Value_Added_Tax|الكشف عن ضريبة القيمة المضافة في النمسا|لا|
|Func_belgium_national_number|الكشف عن الرقم الوطني لبلجيكا|لا|
|Func_belgium_value_added_tax_number|الكشف عن رقم الضريبة لضريبة القيمة المضافة في بلجيكا|لا|
|Func_brazil_cnpj|الكشف عن رقم كيان قانوني في البرازيل (CNPJ)|نعم|
|Func_brazil_cpf|الكشف عن البرازيل CPF|نعم|
|Func_brazil_rg|الكشف عن البرازيل RG|لا|
|Func_british_columbia_drivers_license_number|الكشف عن رقم ترخيص القيادة في كولومبيا البريطانية|لا|
|Func_bulgaria_eu_national_id_card|الكشف عن الرقم المدني الرسمي لبلغاريا|لا|
|Func_california_drivers_license_number|الكشف عن رقم ترخيص القيادة في كاليفورنيا|لا|
|Func_canadian_sin|الكشف عن خطيئة كندا|نعم|
|Func_chile_id_card|الكشف عن بطاقة هوية تشيلي|لا|
|Func_china_resident_id|الكشف عن الم ID المقيم في الصين|لا|
|Func_colorado_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل كولورادو|لا|
|Func_connecticut_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل كونيكت|لا|
|Func_credit_card|الكشف عن بطاقة الائتمان|نعم|
|Func_croatia_id_card|الكشف عن بطاقة هوية كرواتيا|لا|
|Func_croatia_oib_number|الكشف عن رقم OIB في كرواتيا|لا|
|Func_cyprus_eu_tax_file_number|الكشف عن رقم ملف الضرائب في قبرص|لا|
|Func_czech_id_card_new_format|الكشف عن بطاقة الم ID التشيكية بتنسيق جديد|لا|
|Func_czech_id_card|الكشف عن بطاقة الم ID التشيكية|لا|
|Func_dea_number|الكشف عن رقم DEA|نعم|
|Func_denmark_eu_tax_file_number|الكشف عن رقم التعريف الشخصي في الدانمرك|لا|
|Func_district_of_columbia_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل مقاطعة كولومبيا|لا|
|Func_estonia_eu_national_id_card|الكشف عن رمز التعريف الشخصي لإستونيا|لا|
|Func_eu_debit_card|الكشف عن بطاقة خصم الاتحاد الأوروبي|لا|
|Func_finnish_national_id|الكشف عن الم ID الوطنية الفنلندية|لا|
|Func_florida_drivers_license_number|الكشف عن رقم ترخيص القيادة في فلوريدا|لا|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|الكشف عن رقم ترخيص القيادة في فلوريدا وماريلاند وميشيغان ومينيسوتا|لا|
|Func_formatted_itin|الكشف عن ITIN (ITIN) الأمريكية التي تم تنسيقها|نعم|
|Func_fr_insee|الكشف عن فرنسا INSEE|لا|
|Func_fr_passport|الكشف عن جواز سفر فرنسا|لا|
|Func_france_eu_tax_file_number|الكشف عن رقم ملف ضريبة فرنسا|لا|
|Func_france_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في فرنسا|لا|
|Func_french_drivers_license|الكشف عن ترخيص القيادة الفرنسية|لا|
|Func_french_insee|الكشف عن INSEE الفرنسية|لا|
|Func_georgia_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل جورجيا|لا|
|Func_german_drivers_license|الكشف عن ترخيص القيادة في ألمانيا|لا|
|Func_german_passport_data|الكشف عن جواز سفر ألمانيا|لا|
|Func_german_passport|الكشف عن جواز سفر ألمانيا|لا|
|Func_germany_eu_tax_file_number|الكشف عن رقم ملف الضريبة في ألمانيا|لا|
|Func_germany_value_added_tax_number|الكشف عن رقم الضريبة للقيمة المضافة في ألمانيا|لا|
|Func_greece_eu_ssn|الكشف عن الخطيئة اليونانية (AMKA)|لا|
|Func_hawaii_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل هاواي|لا|
|Func_hong_kong_id_card|الكشف عن بطاقة هوية هونغ كونغ|لا|
|Func_hungarian_value_added_tax_number|الكشف عن رقم الضريبة لقيمة هنغاريا المضافة|لا|
|Func_hungary_eu_national_id_card|الكشف عن رقم التعريف الشخصي في هنغاريا|لا|
|Func_hungary_eu_ssn_or_equivalent|الكشف عن رقم الضمان الاجتماعي في هنغاريا|لا|
|Func_hungary_eu_tax_file_number|الكشف عن رقم ملف الضريبة في هنغاريا|لا|
|Func_iban|الكشف عن IBAN|نعم|
|Func_idaho_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Iهمو|لا|
|Func_illinois_drivers_license_number|الكشف عن رقم ترخيص القيادة في إلينوي|لا|
|Func_india_aadhaar|الكشف عن الهند aadhaar|نعم|
|Func_indiana_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل إنديانا|لا|
|Func_iowa_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Iowa|لا|
|Func_ireland_pps|الكشف عن أيرلندا PPS|لا|
|Func_israeli_national_id_number|الكشف عن رقم الم ID الوطنية في إسرائيل|لا|
|Func_italy_eu_national_id_card|الكشف عن التعليمات البرمجية المالية في إيطاليا|لا|
|Func_italy_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في إيطاليا|لا|
|Func_japanese_my_number_corporate|الكشف عن اليابان رقم شركتي|نعم|
|Func_japanese_my_number_personal|الكشف عن رقمي الشخصي في اليابان|نعم|
|Func_jp_bank_account_branch_code|الكشف عن رمز فرعي لحساب بنك اليابان|لا|
|Func_jp_bank_account|الكشف عن حساب بنكي في اليابان|لا|
|Func_jp_drivers_license_number|الكشف عن رقم ترخيص القيادة اليابانية|لا|
|Func_jp_passport|الكشف عن جواز سفر اليابان|لا|
|Func_jp_resident_registration_number|الكشف عن رقم التسجيل المقيم في اليابان|لا|
|Func_jp_sin_pre_1997|الكشف عن خطيئة اليابان قبل 1997|لا|
|Func_jp_sin|الكشف عن اليابان SIN|لا|
|Func_kansas_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل كانساس|لا|
|Func_kentucky_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Kentucky|لا|
|Func_kentucky_massachusetts_virginia_drivers_license_number|الكشف عن رقم ترخيص برنامج التشغيل Kentucky وSententucky وSententts وفيرجينيا|لا|
|Func_latvia_eu_national_id_card|الكشف عن الرمز الشخصي لاتفيا|لا|
|Func_lithuania_eu_tax_file_number|الكشف عن الرمز الشخصي لليتوانيا|لا|
|Func_louisiana_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل لويزيانا|لا|
|Func_luxemburg_eu_tax_file_number_non_natural|الكشف عن رقم التعريف الوطني ل Luxemburg (الأشخاص غير الطبيعيين)|لا|
|Func_luxemburg_eu_tax_file_number|الكشف عن رقم التعريف الوطني ل Luxemburg (الأشخاص الطبيعيون)|لا|
|Func_maine_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Maine|لا|
|Func_manitoba_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Manitoba|لا|
|Func_maryland_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ماريلاند|لا|
|Func_massachusetts_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ماساتشوستس|لا|
|Func_mexico_population_registry_code|الكشف عن رمز تسجيل عدد السكان في المكسيك|لا|
|Func_michigan_minnesota_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ميشيغان، مينيسوتا|لا|
|Func_minnesota_drivers_license_number|الكشف عن رقم ترخيص القيادة في مينيسوتا|لا|
|Func_mississippi_oklahoma_drivers_license_number|الكشف عن Mississippi، رقم ترخيص برنامج تشغيل أوكلاهوما|لا|
|Func_missouri_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل  Missouri|لا|
|Func_montana_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل مونتانا|لا|
|Func_nebraska_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل نبراسكا|لا|
|Func_netherlands_bsn|الكشف عن هولندا BSN|لا|
|Func_netherlands_eu_tax_file_number|الكشف عن رقم ملف الضرائب الهولندي|لا|
|Func_netherlands_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في هولندا|لا|
|Func_nevada_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل نيفادا|لا|
|Func_new_brunswick_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل نيو برونزويك|لا|
|Func_new_hampshire_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل هامبشير الجديد|لا|
|Func_new_jersey_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل New جيرسي|لا|
|Func_new_mexico_drivers_license_number|الكشف عن رقم ترخيص القيادة في نيو المكسيك|لا|
|Func_new_york_drivers_license_number|الكشف عن رقم ترخيص القيادة في نيويورك|لا|
|Func_new_zealand_bank_account_number|الكشف عن رقم الحساب البنكي في نيوزيلندا|لا|
|Func_new_zealand_inland_revenue_number|الكشف عن رقم الإيرادات الداخلية لنيوزيلندا|لا|
|Func_new_zealand_ministry_of_health_number|الكشف عن رقم وزارة الصحة في نيوزيلندا|لا|
|Func_newfoundland_labrador_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل نيوفاوندلاند لابرادور|لا|
|Func_newzealand_driver_license_number|الكشف عن رقم ترخيص برنامج تشغيل نيوزيلندا|لا|
|Func_newzealand_social_welfare_number|الكشف عن رقم الرعاية الاجتماعية في نيوزيلندا|لا|
|Func_north_carolina_drivers_license_number|الكشف عن رقم ترخيص القيادة في North Carolina|لا|
|Func_north_dakota_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل North Dakota|لا|
|Func_norway_id_number|الكشف عن رقم "المكتشف النرويجي"|لا|
|Func_nova_scotia_drivers_license_number|الكشف عن رقم ترخيص القيادة في نوفا سكوشيا|لا|
|Func_ohio_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل أوهايو|لا|
|Func_ontario_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل أونتاريو|لا|
|Func_pennsylvania_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل بنسيلفانيا|لا|
|Func_pesel_identification_number|الكشف عن "الم ID الوطنية البولندية" (PESEL)|لا|
|Func_poland_eu_tax_file_number|الكشف عن رقم الملف الضريبي في بولندا|لا|
|Func_polish_national_id|الكشف عن بطاقة هوية بولندا|لا|
|Func_polish_passport_number|الكشف عن رقم جواز السفر البولندي|لا|
|Func_polish_regon_number|الكشف عن رقم REGON البولندي|لا|
|Func_portugal_eu_tax_file_number|الكشف عن رقم تعريف الضريبة في البرتغال|لا|
|Func_prince_edward_island_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل جزيرة برنس إدوارد|لا|
|Func_quebec_drivers_license_number|الكشف عن رقم ترخيص القيادة في كيبيك|لا|
|Func_randomized_formatted_ssn|الكشف عن SSN الولايات المتحدة التي تم تنسيقها عشوائيا|نعم|
|Func_randomized_unformatted_ssn|الكشف عن SSN الولايات المتحدة غير المنسوجه عشوائيا|نعم|
|Func_rhode_island_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل جزيرة الرود آيلاند|لا|
|Func_romania_eu_national_id_card|الكشف عن رمز رومانيا الشخصي (CNP)|لا|
|Func_saskatchewan_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ساسكاتشوان|لا|
|Func_slovakia_eu_national_id_card|الكشف عن الرقم الشخصي في سلوفاكيا|لا|
|Func_slovenia_eu_national_id_card|الكشف عن رقم سلوفينيا الرئيسي الفريد|لا|
|Func_slovenia_eu_tax_file_number|الكشف عن رقم ملف الضريبة في سلوفينيا|لا|
|Func_south_africa_identification_number|الكشف عن رقم تعريف جنوب أفريقيا|نعم|
|Func_south_carolina_drivers_license_number|الكشف عن رقم ترخيص القيادة في جنوب كاليفورنيا|لا|
|Func_south_dakota_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل South Dakota|لا|
|Func_south_korea_resident_number|الكشف عن رقم مقيم في كوريا الجنوبية|لا|
|Func_spain_eu_DL_and_NI_number_citizen|الكشف عن أسبانيا DL و NI لمعان رقم|لا|
|Func_spain_eu_DL_and_NI_number_foreigner|الكشف عن الرقمين Spain DL و NI|لا|
|Func_spain_eu_driver لا s_license_number|الكشف عن رقم ترخيص القيادة في إسبانيا|لا|
|Func_spain_eu_tax_file_number|الكشف عن رقم الملف الضريبي لإسبانيا|لا|
|Func_spanish_social_security_number|الكشف عن رقم الضمان الاجتماعي الأسباني|لا|
|Func_ssn|دالة للكشف عن SSN الأمريكية غير العشوائية|نعم|
|Func_sweden_eu_tax_file_number|الكشف عن رقم ملف الضريبة في السويد|لا|
|Func_swedish_national_identifier|الكشف عن المعرف الوطني السويدي|نعم|
|Func_swiss_social_security_number_ahv|الكشف عن رقم الضمان الاجتماعي السويسري AHV|لا|
|Func_taiwanese_national_id|الكشف عن الم ID الوطنية التايوانية|لا|
|Func_tennessee_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل تينيسي|لا|
|Func_texas_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل تكساس|لا|
|Func_Thai_Citizen_Id|الكشف عن "المستشعر التايلاندي"|لا|
|Func_Turkish_National_Id|الكشف عن الم ID الوطنية التركية|نعم|
|Func_uk_drivers_license|الكشف عن ترخيص القيادة في المملكة المتحدة|لا|
|Func_uk_eu_tax_file_number|الكشف عن رقم الممول الفريد للمملكة المتحدة|لا|
|Func_uk_nhs_number|الكشف عن رقم NHS في المملكة المتحدة|نعم|
|Func_uk_nino|الكشف عن UK NINO|لا|
|Func_unformatted_canadian_sin|الكشف عن SIN الكندية غير المهيئة|لا|
|Func_unformatted_itin|الكشف عن ITIN الأمريكية غير المنسوجهة|نعم|
|Func_unformatted_ssn|الكشف عن SSN الولايات المتحدة غير المشتتة عشوائيا|نعم|
|Func_usa_uk_passport|الكشف عن جواز سفر الولايات المتحدة والمملكة المتحدة|نعم|
|Func_utah_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل يوتا|لا|
|Func_vermont_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Vermont|لا|
|Func_virginia_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل ولاية فيرجينيا|لا|
|Func_washington_drivers_license_number|الكشف عن رقم ترخيص القيادة في واشنطن|لا|
|Func_west_virginia_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل West Virginia|لا|
|Func_wisconsin_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Wisconsin|لا|
|Func_wyoming_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Wyoming|لا|

## <a name="func_us_date"></a>Func_us_date

Func_us_date البحث عن التواريخ بتنسيقات الولايات المتحدة الشائعة. التنسيقات الشائعة هي "شهر/يوم/سنة" و"شهر-يوم-سنة" و"شهر يوم سنة". لا تتحسس أسماء الأشهر أو اختصاراتها حالة التحسس.

أمثلة:

- 2 ديسمبر 2016
- 2 ديسمبر 2016
- ديسمبر 02 2016
- 12/2/2016
- 12/02/16
- ديسمبر 2016
- 12-2-16

أسماء الشهر المقبولة:

- الإنكليزية
  - يناير، فبراير، مارس، أبريل، مايو، يونيو، يوليو، أغسطس، سبتمبر، أكتوبر، نوفمبر، ديسمبر
  - يناير. فبراير. مارس. مايو يونيو من شهر أغسطس. سبتمبر. أكتوبر. نوفمبر.

## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates البحث عن تواريخ في E.U الشائعة. التنسيقات (ومعظم الأماكن خارج الولايات المتحدة)، مثل "يوم/شهر/سنة"، و"يوم-شهر-سنة"، و"يوم شهر سنة". لا تتحسس أسماء الأشهر أو اختصاراتها حالة التحسس.

أمثلة:

- 2 ديسمبر 2016
- 02 ديسمبر 2016
- 2 ديسمبر 16
- 2/12/2016
- 02/12/16
- 2 ديسمبر 2016
- 2-12-16

أسماء الشهر المقبولة:

- الإنكليزية
  - يناير، فبراير، مارس، أبريل، مايو، يونيو، يوليو، أغسطس، سبتمبر، أكتوبر، نوفمبر، ديسمبر
  - يناير. فبراير. مارس. مايو يونيو من شهر أغسطس. سبتمبر. أكتوبر. نوفمبر.
- الهولندية
  - januari، februari، maart، أبريل، mei، juni، juli، augustus، سبتمبر، ocktober، أكتوبر، نوفمبر، ديسمبر
  - jan feb maart apr mei jun jul أغسطس سبتمبر سبتمبر oct okt nov dec
- الفرنسية
  - janvier, février, mars, avril, mai, juin juillet, août, septembre, octobre, novembre, décembre
  - janv. févr. mars avril mai juin juil. août sept. oct. نوفمبر. déc.
- الألمانية
  - jänuar, februar, märz, april, mai, juni juli, august, September, oktober, november, dezember
  - Jan./Jän. فبراير. März Apr. Mai Juni Juli أغسطس. سبتمبر. Okt. نوفمبر. عايز.
- الإيطالية
  - gennaio, febbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre, ottobre, novembre, dicembre
  - genn. febbr. mar. أبريل. magg. giugno luglio ag. sett. ott. نوفمبر. dic.
- البرتغالية
  - janeiro,ةiro, março, março, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez
- الإسبانية
  - enero, febrero, marzo, abril, مايو, junio, julio, agosto, septiembre, octubre, noviembre, diciembre
  - enero feb. marzo abr. وnn. jul. agosto sept./set. oct. نوفمبر. dic.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (مهمل)

> [!NOTE]
> تم إهمال هذه الدالة لأنها تدعم أسماء أشهر البرتغالية فقط، والتي تم تضمينها الآن في الدالة  `Func_eu_date` أعلاه.

تبحث هذه الدالة عن تاريخ بتنسيق شائع استخدامه في اللغة البرتغالية. تنسيق هذه الدالة هو  `Func_eu_date`نفسه ، ويختلف فقط في اللغة المستخدمة.

أمثلة:

- 2 عاظ 2016
- 02 رز 2016
- 2 عاظ 16
- 2/12/2016
- 02/12/16
- 2-Dez-2016
- 2-12-16

أسماء الشهر المقبولة:

- البرتغالية
  - janeiro,ةiro, março, março, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (مهمل)

> [!NOTE]
> تم إهمال هذه الدالة لأنها تدعم أسماء أشهر الهولندية فقط، والتي تم تضمينها الآن في الدالة  `Func_eu_date` أعلاه.

تبحث هذه الدالة عن تاريخ بتنسيق شائع استخدامه في اللغة الهولندية. تنسيق هذه الدالة هو  `Func_eu_date`نفسه ، ويختلف فقط في اللغة المستخدمة.

أمثلة:

- 2 Mei 2016
- 02 mei 2016
- 2 Mei 16
- 2/12/2016
- 02/12/16
- 2-Mei-2016
- 2-12-16

أسماء الشهر المقبولة:

- الهولندية
  - januari، februari، maart، أبريل، mei، juni، juli، augustus، سبتمبر، ocktober، أكتوبر، نوفمبر، ديسمبر
  - jan feb maart apr mei jun jul أغسطس سبتمبر sept out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date عن التواريخ التي يتم استخدامها بتنسيقات شائعة استخدام بطاقات الائتمان والخصم. ستطابق هذه الدالة التواريخ بتنسيق "شهر/سنة" و"شهر-سنة" و"[اسم الشهر] السنة" و"[اختصار الشهر] السنة". لا تتحسس أسماء الأشهر أو اختصاراتها حالة التحسس.

أمثلة:

- MM/YY -- على سبيل المثال، 01/11 أو 1/11
- MM/YYYY -- على سبيل المثال، 01/2011 أو 1/2011
- MM-YY -- على سبيل المثال، 01-22 أو 1-11
- MM-YYYY - على سبيل المثال، 01-2000 أو 1-2000

تدعم التنسيقات التالية YY أو YYYY:

- Month-YYYY - على سبيل المثال يناير 2010 أو يناير 2010 أو 10 يناير أو يناير - 10
- Month YYYY -- على سبيل المثال، "يناير 2010" أو "يناير 2010" أو "10 يناير" أو "10 يناير"
- MonthYYYY - على سبيل المثال، "يناير 2010" أو "يناير 2010" أو "يناير 10" أو "يناير 10"
- Month/YYYY -- على سبيل المثال، "يناير/2010" أو "يناير/2010" أو "يناير/10" أو "يناير/10"

أسماء الشهر المقبولة:

- الإنكليزية
  - يناير، فبراير، مارس، أبريل، مايو، يونيو، يوليو، أغسطس، سبتمبر، أكتوبر، نوفمبر، ديسمبر
  - يناير فبراير أبريل يونيو يوليو أغسطس من شهر سبتمبر 1427

## <a name="func_us_address"></a>Func_us_address

Func_us_address البحث عن اسم ولاية أو اختصار بريدي يتبعه رمز بريدي صالح. يجب أن يكون الرمز البريدي أحد الرموز البريدية الصحيحة المقترنة باسم ولاية الولايات المتحدة أو اختصارها. لا يمكن الفصل بين اسم ولاية الولايات المتحدة والرمز البريدي بواسطة علامات الترقيم أو الأحرف.

أمثلة:

- واشنطن 98052
- واشنطن 98052-9998
- WA 98052
- WA 98052-9998
