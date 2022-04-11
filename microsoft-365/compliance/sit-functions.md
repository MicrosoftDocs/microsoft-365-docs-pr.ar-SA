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
ms.openlocfilehash: 7c2ce289cab93e4a0491cbf13379c169a01e7fbf
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760240"
---
# <a name="sensitive-information-type-functions"></a>دالات نوع المعلومات الحساسة

يمكن لأنواع المعلومات الحساسة (SIT) استخدام الدالات كعناصر أساسية لتحديد العناصر الحساسة. على سبيل المثال، يستخدم نوع المعلومات الحساسة لرقم بطاقة الائتمان الدالة Func_credit_card للكشف عن رقم بطاقة الائتمان.

تشرح هذه المقالة ما تبحث عنه هذه الدالات، لمساعدتك على فهم كيفية عمل أنواع المعلومات الحساسة المعرفة مسبقا. لمزيد من المعلومات، راجع [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>جدول الدالات

|اسم الدالة | إجراء الدالة | هو مدقق|
|---------|----------|---------|
|Func_aba_routing|الكشف عن رقم توجيه ABA|نعم|
|Func_alabama_drivers_license_number|الكشف عن رقم رخصة القيادة في ألاباما|لا|
|Func_alaska_delaware_oregon_drivers_license_number|الكشف عن رقم رخصة القيادة في ألاسكا وديلاوير وأوريغن|لا|
|Func_alaska_drivers_license_number|الكشف عن رقم رخصة القيادة في ألاسكا|لا|
|Func_alberta_drivers_license_number|الكشف عن رقم رخصة القيادة في ألبرتا|لا|
|Func_argentina_Unique_Tax_Key|الكشف عن المفتاح الضريبي الفريد للارجنتين والتحقق من صحته|لا|
|Func_Argentina_Unique_Tax_Key|الكشف عن مفتاح الضريبة الفريد في الأرجنتين|لا|
|Func_arizona_drivers_license_number|الكشف عن رقم رخصة القيادة في أريزونا|لا|
|Func_arkansas_drivers_license_number|الكشف عن رقم رخصة قيادة Arkansas|لا|
|Func_australian_business_number|الكشف عن رقم عمل أستراليا|لا|
|Func_Australian_Company_Number|الكشف عن رقم شركة أستراليا|لا|
|Func_australian_medical_account_number|الكشف عن رقم الحساب الطبي في أستراليا|لا|
|Func_australian_tax_file_number|الكشف عن رقم ملف الضريبة في أستراليا|نعم|
|Func_austria_eu_ssn_or_equivalent|الكشف عن رقم الضمان الاجتماعي في النمسا|لا|
|Func_austria_eu_tax_file_number|الكشف عن رقم الملف الضريبي في النمسا|لا|
|Func_Austria_Value_Added_Tax|الكشف عن ضريبة القيمة المضافة في النمسا|لا|
|Func_belgium_national_number|الكشف عن الرقم الوطني في بلجيكا|لا|
|Func_belgium_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في بلجيكا|لا|
|Func_brazil_cnpj|الكشف عن رقم الكيان القانوني البرازيلي (CNPJ)|نعم|
|Func_brazil_cpf|الكشف عن CPF في البرازيل|نعم|
|Func_brazil_rg|الكشف عن RG البرازيل|لا|
|Func_british_columbia_drivers_license_number|الكشف عن رقم رخصة القيادة في بريتامبيا البريطانية|لا|
|Func_bulgaria_eu_national_id_card|الكشف عن الرقم المدني الموحد لبلغاريا|لا|
|Func_california_drivers_license_number|الكشف عن رقم رخصة القيادة في كاليفورنيا|لا|
|Func_canadian_sin|الكشف عن خطية كندا|نعم|
|Func_chile_id_card|الكشف عن بطاقة معرف تشيلي|لا|
|Func_china_resident_id|الكشف عن معرف مقيم في الصين|لا|
|Func_colorado_drivers_license_number|الكشف عن رقم رخصة القيادة في كولارادو|لا|
|Func_connecticut_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Connecticut|لا|
|Func_credit_card|الكشف عن بطاقة الائتمان|نعم|
|Func_croatia_id_card|الكشف عن بطاقة معرف الكرواتية|لا|
|Func_croatia_oib_number|الكشف عن رقم OIB لكرواتيا|لا|
|Func_cyprus_eu_tax_file_number|الكشف عن رقم الملف الضريبي ل "ضرائب" في "كانو"|لا|
|Func_czech_id_card_new_format|الكشف عن بطاقة المعرف التشيكي بتنسيق جديد|لا|
|Func_czech_id_card|الكشف عن بطاقة المعرف التشيكي|لا|
|Func_dea_number|الكشف عن رقم DEA|نعم|
|Func_denmark_eu_tax_file_number|الكشف عن رقم التعريف الشخصي للدانمرك|لا|
|Func_district_of_columbia_drivers_license_number|الكشف عن رقم رخصة القيادة لمنطقة كولومبيا|لا|
|Func_estonia_eu_national_id_card|الكشف عن رمز التعريف الشخصي الإستوني|لا|
|Func_eu_debit_card|الكشف عن بطاقة خصم الاتحاد الأوروبي|لا|
|Func_finnish_national_id|الكشف عن المعرف الوطني الفنلندي|لا|
|Func_florida_drivers_license_number|الكشف عن رقم رخصة القيادة في ولاية فلوريدا|لا|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|الكشف عن رقم رخصة القيادة في فلوريدا، ماجنجن، ميشغان، مينيسوتا|لا|
|Func_formatted_itin|الكشف عن تنسيق ITIN في الولايات المتحدة|نعم|
|Func_fr_insee|الكشف عن France INSEE|لا|
|Func_fr_passport|الكشف عن جواز سفر فرنسا|لا|
|Func_france_eu_tax_file_number|الكشف عن رقم ملف الضريبة في فرنسا|لا|
|Func_france_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة ل فرنسا|لا|
|Func_french_drivers_license|الكشف عن رخصة القيادة الفرنسية|لا|
|Func_french_insee|الكشف عن INSEE الفرنسية|لا|
|Func_georgia_drivers_license_number|الكشف عن رقم رخصة القيادة في Georgia|لا|
|Func_german_drivers_license|الكشف عن رخصة القيادة في ألمانيا|لا|
|Func_german_passport_data|الكشف عن جواز سفر ألمانيا|لا|
|Func_german_passport|الكشف عن جواز سفر ألمانيا|لا|
|Func_germany_eu_tax_file_number|الكشف عن رقم ملف الضريبة في ألمانيا|لا|
|Func_germany_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في ألمانيا|لا|
|Func_greece_eu_ssn|الكشف عن خطية اليونان (AMKA)|لا|
|Func_hawaii_drivers_license_number|الكشف عن رقم رخصة القيادة في هاواي|لا|
|Func_hong_kong_id_card|الكشف عن بطاقة معرف هونغ كونغ|لا|
|Func_hungarian_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في المجر|لا|
|Func_hungary_eu_national_id_card|الكشف عن رقم التعريف الشخصي في المجر|لا|
|Func_hungary_eu_ssn_or_equivalent|الكشف عن رقم الضمان الاجتماعي في المجر|لا|
|Func_hungary_eu_tax_file_number|الكشف عن رقم الملف الضريبي في المجر|لا|
|Func_iban|الكشف عن IBAN|نعم|
|Func_idaho_drivers_license_number|الكشف عن رقم رخصة قيادة Idaho|لا|
|Func_illinois_drivers_license_number|الكشف عن رقم رخصة القيادة في إلينوي|لا|
|Func_india_aadhaar|الكشف عن الهند aadhaar|نعم|
|Func_indiana_drivers_license_number|الكشف عن رقم رخصة القيادة في إنديانا|لا|
|Func_iowa_drivers_license_number|الكشف عن رقم رخصة قيادة Iowa|لا|
|Func_ireland_pps|الكشف عن PPS في أيرلندا|لا|
|Func_israeli_national_id_number|الكشف عن رقم المعرف الوطني في إسرائيل|لا|
|Func_italy_eu_national_id_card|الكشف عن التعليمات البرمجية المالية في إيطاليا|لا|
|Func_italy_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في إيطاليا|لا|
|Func_japanese_my_number_corporate|الكشف عن شركة أرقامي في اليابان|نعم|
|Func_japanese_my_number_personal|الكشف عن رقمي الشخصي في اليابان|نعم|
|Func_jp_bank_account_branch_code|الكشف عن رمز فرع الحساب البنكي الياباني|لا|
|Func_jp_bank_account|الكشف عن الحساب البنكي الياباني|لا|
|Func_jp_drivers_license_number|الكشف عن رقم رخصة القيادة اليابانية|لا|
|Func_jp_passport|الكشف عن جواز سفر اليابان|لا|
|Func_jp_resident_registration_number|الكشف عن رقم التسجيل المقيم في اليابان|لا|
|Func_jp_sin_pre_1997|الكشف عن خطية اليابان قبل عام 1997|لا|
|Func_jp_sin|الكشف عن SIN في اليابان|لا|
|Func_kansas_drivers_license_number|الكشف عن رقم رخصة قيادة Kansas|لا|
|Func_kentucky_drivers_license_number|الكشف عن رقم رخصة القيادة في كنتاكي|لا|
|Func_kentucky_massachusetts_virginia_drivers_license_number|الكشف عن رقم رخصة القيادة Kentucky، وSals، وSedigns، وSomaoma|لا|
|Func_latvia_eu_national_id_card|الكشف عن التعليمات البرمجية الشخصية في لاتفيا|لا|
|Func_lithuania_eu_tax_file_number|الكشف عن التعليمات البرمجية الشخصية ليتوانية|لا|
|Func_louisiana_drivers_license_number|الكشف عن رقم رخصة القيادة في لويزيانا|لا|
|Func_luxemburg_eu_tax_file_number_non_natural|الكشف عن رقم التعريف الوطني ل Unityemburg (أشخاص غير طبيعيين)|لا|
|Func_luxemburg_eu_tax_file_number|الكشف عن رقم التعريف الوطني ل Unityemburg (الأشخاص الطبيعيين)|لا|
|Func_maine_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Maine|لا|
|Func_manitoba_drivers_license_number|الكشف عن رقم رخصة القيادة في Manitoba|لا|
|Func_maryland_drivers_license_number|الكشف عن رقم رخصة القيادة في Excel|لا|
|Func_massachusetts_drivers_license_number|الكشف عن رقم رخصة القيادة في هاس|لا|
|Func_mexico_population_registry_code|الكشف عن رمز سجل السكان في المكسيك|لا|
|Func_michigan_minnesota_drivers_license_number|الكشف عن رقم رخصة القيادة في ميشغان، مينيسوتا|لا|
|Func_minnesota_drivers_license_number|الكشف عن رقم رخصة القيادة في Minnesota|لا|
|Func_mississippi_oklahoma_drivers_license_number|الكشف عن مسيسيبي، رقم رخصة القيادة في أوكلاهيوما|لا|
|Func_missouri_drivers_license_number|الكشف عن رقم رخصة القيادة الخاصة ب Missouri|لا|
|Func_montana_drivers_license_number|الكشف عن رقم رخصة القيادة في Montana|لا|
|Func_nebraska_drivers_license_number|الكشف عن رقم رخصة قيادة Nebraska|لا|
|Func_netherlands_bsn|الكشف عن BSN في هولندا|لا|
|Func_netherlands_eu_tax_file_number|الكشف عن رقم ملف الضريبة في هولندا|لا|
|Func_netherlands_value_added_tax_number|الكشف عن رقم ضريبة القيمة المضافة في هولندا|لا|
|Func_nevada_drivers_license_number|الكشف عن رقم رخصة قيادة Nevada|لا|
|Func_new_brunswick_drivers_license_number|الكشف عن رقم رخصة القيادة الجديدة في بروانزهاي|لا|
|Func_new_hampshire_drivers_license_number|الكشف عن رقم رخصة القيادة ل New Hamp paris|لا|
|Func_new_jersey_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل New Sentiment|لا|
|Func_new_mexico_drivers_license_number|الكشف عن رقم رخصة قيادة NewExico|لا|
|Func_new_york_drivers_license_number|الكشف عن رقم رخصة القيادة في نيويورك|لا|
|Func_new_zealand_bank_account_number|الكشف عن رقم الحساب البنكي في نيوزيلندا|لا|
|Func_new_zealand_inland_revenue_number|الكشف عن رقم الإيرادات الداخلية لنيوزيلندا|لا|
|Func_new_zealand_ministry_of_health_number|الكشف عن عدد الأرقام الصحية في نيوزيلندا|لا|
|Func_newfoundland_labrador_drivers_license_number|الكشف عن رقم رخصة قيادة Newfoundland Labrador|لا|
|Func_newzealand_driver_license_number|الكشف عن رقم رخصة القيادة في نيوزيلندا|لا|
|Func_newzealand_social_welfare_number|الكشف عن رقم الرعاية الاجتماعية في نيوزيلندا|لا|
|Func_north_carolina_drivers_license_number|الكشف عن رقم رخصة القيادة في North County|لا|
|Func_north_dakota_drivers_license_number|الكشف عن رقم رخصة القيادة في شمال Dakota|لا|
|Func_norway_id_number|الكشف عن رقم معرف النرويج|لا|
|Func_nova_scotia_drivers_license_number|الكشف عن رقم رخصة قيادة Nova Scotia|لا|
|Func_ohio_drivers_license_number|الكشف عن رقم رخصة القيادة في مقاطعة هاو|لا|
|Func_ontario_drivers_license_number|الكشف عن رقم رخصة القيادة في Excel|لا|
|Func_pennsylvania_drivers_license_number|الكشف عن رقم رخصة القيادة في باسل|لا|
|Func_pesel_identification_number|الكشف عن المعرف الوطني لبولونيا (PESEL)|لا|
|Func_poland_eu_tax_file_number|الكشف عن رقم الملف الضريبي في بولندا|لا|
|Func_polish_national_id|الكشف عن بطاقة هوية في بولندا|لا|
|Func_polish_passport_number|الكشف عن رقم جواز السفر البولندي|لا|
|Func_polish_regon_number|الكشف عن رقم REGON البولندي|لا|
|Func_portugal_eu_tax_file_number|الكشف عن رقم التعريف الضريبي في البرتغال|لا|
|Func_prince_edward_island_drivers_license_number|الكشف عن رقم رخصة القيادة في جزيرة إدوارد|لا|
|Func_quebec_drivers_license_number|الكشف عن رقم رخصة القيادة في كيبيك|لا|
|Func_randomized_formatted_ssn|الكشف عن SSN الأمريكية المنسقة عشوائيا|نعم|
|Func_randomized_unformatted_ssn|الكشف عن SSN الأمريكية العشوائية غير المنسقة|نعم|
|Func_rhode_island_drivers_license_number|الكشف عن رقم رخصة قيادة جزيرة Rhode|لا|
|Func_romania_eu_national_id_card|الكشف عن التعليمات البرمجية الرقمية الشخصية في رومانيا (CNP)|لا|
|Func_saskatchewan_drivers_license_number|الكشف عن رقم رخصة قيادة Saskatchewan|لا|
|Func_slovakia_eu_national_id_card|الكشف عن الرقم الشخصي في تلقائيا|لا|
|Func_slovenia_eu_national_id_card|الكشف عن رقم المواطنين الرئيسي الفريد ل والسلوفينية|لا|
|Func_slovenia_eu_tax_file_number|الكشف عن رقم ملف الضريبة في  والسلوفينية|لا|
|Func_south_africa_identification_number|الكشف عن رقم تعريف جنوب أفريقيا|نعم|
|Func_south_carolina_drivers_license_number|الكشف عن رقم رخصة القيادة في جنوب ساوثهايكار|لا|
|Func_south_dakota_drivers_license_number|الكشف عن رقم رخصة القيادة في جنوب Dakota|لا|
|Func_south_korea_resident_number|الكشف عن الرقم المقيم في كوريا الجنوبية|لا|
|Func_spain_eu_DL_and_NI_number_citizen|الكشف عن أسبانيا DL وNI number citizen|لا|
|Func_spain_eu_DL_and_NI_number_foreigner|الكشف عن رقم DL و NI الإسباني|لا|
|s_license_number Func_spain_eu_driver|الكشف عن رقم رخصة القيادة الإسبانية|لا|
|Func_spain_eu_tax_file_number|الكشف عن رقم ملف الضريبة في إسبانيا|لا|
|Func_spanish_social_security_number|الكشف عن رقم الضمان الاجتماعي الأسباني|لا|
|Func_ssn|دالة للكشف عن SSN الأمريكية المنسقة غير العشوائية|نعم|
|Func_sweden_eu_tax_file_number|الكشف عن رقم ملف ضريبة السويد|لا|
|Func_swedish_national_identifier|الكشف عن المعرف الوطني السويدية|نعم|
|Func_swiss_social_security_number_ahv|الكشف عن رقم الضمان الاجتماعي في سويسرا AHV|لا|
|Func_taiwanese_national_id|الكشف عن المعرف الوطني التايواني|لا|
|Func_tennessee_drivers_license_number|الكشف عن رقم رخصة قيادة تينيسي|لا|
|Func_texas_drivers_license_number|الكشف عن رقم رخصة القيادة في تكساس|لا|
|Func_Thai_Citizen_Id|الكشف عن معرف المواطنين التايلاندي|لا|
|Func_Turkish_National_Id|الكشف عن المعرف الوطني التركية|نعم|
|Func_uk_drivers_license|الكشف عن رخصة القيادة في المملكة المتحدة|لا|
|Func_uk_eu_tax_file_number|الكشف عن رقم المعرف الفريد في المملكة المتحدة|لا|
|Func_uk_nhs_number|الكشف عن رقم NHS في المملكة المتحدة|نعم|
|Func_uk_nino|الكشف عن NINO في المملكة المتحدة|لا|
|Func_unformatted_canadian_sin|الكشف عن SIN الكندية غير المنسقة|لا|
|Func_unformatted_itin|الكشف عن ITIN الأمريكية غير المنسقة|نعم|
|Func_unformatted_ssn|الكشف عن SSN الأمريكية غير المنسقة غير العشوائية|نعم|
|Func_usa_uk_passport|الكشف عن جواز سفر الولايات المتحدة والمملكة المتحدة|نعم|
|Func_utah_drivers_license_number|الكشف عن رقم رخصة القيادة في يوتا|لا|
|Func_vermont_drivers_license_number|الكشف عن رقم رخصة القيادة في Ver sentiment|لا|
|Func_virginia_drivers_license_number|الكشف عن رقم رخصة القيادة في ولاية فيرجينا|لا|
|Func_washington_drivers_license_number|الكشف عن رقم رخصة القيادة في واشنطن|لا|
|Func_west_virginia_drivers_license_number|الكشف عن رقم رخصة القيادة في West Germany|لا|
|Func_wisconsin_drivers_license_number|الكشف عن رقم رخصة القيادة في Wisconsin|لا|
|Func_wyoming_drivers_license_number|الكشف عن رقم ترخيص برنامج تشغيل Wyoming|لا|

## <a name="func_us_date"></a>Func_us_date

تبحث Func_us_date عن تواريخ بتنسيقات أمريكية شائعة. التنسيقات الشائعة هي "شهر/يوم/سنة"، و"شهر-يوم-سنة"، و"سنة يوم شهر". أسماء الأشهر أو اختصاراتها ليست حساسة لحالة الأحرف.

امثله:

- 2 ديسمبر 2016
- 2 ديسمبر 2016
- 02 ديسمبر 2016
- 12/2/2016
- 12/02/16
- 2-2016 ديسمبر
- 12-2-16

أسماء الأشهر المقبولة:

- الإنكليزية
  - يناير، فبراير، مارس، أبريل، مايو، يونيو، يوليو، أغسطس، سبتمبر، أكتوبر، نوفمبر، ديسمبر
  - يناير. فبراير مارس، أبريل، مايو يوليو، أغسطس. سبتمبر. 2010. ديسمبر.

## <a name="func_eu_date"></a>Func_eu_date

يبحث Fund_eu_dates عن التواريخ في E.U الشائعة التنسيقات (ومعظم الأماكن خارج الولايات المتحدة)، مثل "يوم/شهر/سنة" و"يوم-شهر-سنة" و"سنة شهر اليوم". أسماء الأشهر أو اختصاراتها ليست حساسة لحالة الأحرف.

امثله:

- 2 ديسمبر 2016
- 02 ديسمبر 2016
- 2 ديسمبر 16
- 2/12/2016
- 02/12/16
- 2-ديسمبر 2016
- 2-12-16

أسماء الأشهر المقبولة:

- الإنكليزية
  - يناير، فبراير، مارس، أبريل، مايو، يونيو، يوليو، أغسطس، سبتمبر، أكتوبر، نوفمبر، ديسمبر
  - يناير. فبراير مارس، أبريل، مايو يوليو، أغسطس. سبتمبر. 2010. ديسمبر.
- الهولندية
  - يناير، فيبراري، مارت، أبريل، mei، juni، juli، أغسطس، سبتمبر، ocktober، أكتوبر، نوفمبر، ديسمبر
  - jan feb maart apr mei jun jul aug sep oct okt nov dec
- الفرنسية
  - janvier, février, mars, avril, mai, juin juillet, août, cmembre, octobre, novembre, décembre
  - jan févr. mars avril mai juin juil. août سبتمبر. اكتوبر. نوفمبر. déc.
- الألمانية
  - jänuar، februar، märz، April، mai، juni juli، أغسطس، سبتمبر، oktober، نوفمبر، dezember
  - يناير/جان. فبراير. März Apr. Mai Juli Juli Aug. سبتمبر. Okt. Nov. Dez.
- الإيطالية
  - gennaio, febbraio, marzo, aprile, mag gi giugno, luanoo, agosto, settembre, ottobre, novembre, dicembre
  - genn. febbr. مارس. ابريل. المكبر. giugno luleno ag. sett. اوت. نوفمبر. dic.
- البرتغالية
  - janeiro,iro, março, ago, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez
- الإسبانية
  - enero, febrero, marzo, abril, junio, julio, agosto, octubre, noviembre, diciembre
  - enero feb. marzo abr. jun. يوليو. agosto./set. اكتوبر. نوفمبر. dic.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (مهمل)

> [!NOTE]
> تم إهمال هذه الدالة لأنها تدعم أسماء الأشهر البرتغالية فقط، والتي يتم تضمينها الآن في الدالة  `Func_eu_date` أعلاه.

تبحث هذه الدالة عن تاريخ بالتنسيق المستخدم بشكل شائع في اللغة البرتغالية. تنسيق هذه الدالة هو نفسه  `Func_eu_date`، يختلف فقط في اللغة المستخدمة.

امثله:

- 2 Dez 2016
- 02 dez 2016
- 2 Dez 16
- 2/12/2016
- 02/12/16
- 2-Dez-2016
- 2-12-16

أسماء الأشهر المقبولة:

- البرتغالية
  - janeiro,iro, março, ago, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul ago set out nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (مهمل)

> [!NOTE]
> تم إهمال هذه الدالة لأنها تدعم أسماء الأشهر الهولندية فقط، والتي تم تضمينها الآن في الدالة  `Func_eu_date` أعلاه.

تبحث هذه الدالة عن تاريخ بالتنسيق المستخدم عادة باللغة الهولندية. تنسيق هذه الدالة هو نفسه  `Func_eu_date`، يختلف فقط في اللغة المستخدمة.

امثله:

- 2 Mei 2016
- 02 mei 2016
- 2 Mei 16
- 2/12/2016
- 02/12/16
- 2-Mei-2016
- 2-12-16

أسماء الأشهر المقبولة:

- الهولندية
  - يناير، فيبراري، مارت، أبريل، mei، juni، juli، أغسطس، سبتمبر، ocktober، أكتوبر، نوفمبر، ديسمبر
  - jan feb maart apr mei jun jul aug sep out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

تبحث Func_expiration_date عن التواريخ بتنسيقات شائعة الاستخدام بواسطة بطاقات الائتمان والخصم. ستتطابق هذه الدالة مع التواريخ بتنسيق "شهر/سنة" و"شهر-سنة" و"[اسم الشهر] السنة" و"[اختصار الشهر] السنة". أسماء الأشهر أو اختصاراتها ليست حساسة لحالة الأحرف.

امثله:

- MM/YY -- على سبيل المثال، 01/11 أو 1/11
- MM/YYYY -- على سبيل المثال، 01/2011 أو 1/2011
- MM-YY -- على سبيل المثال، 01-22 أو 1-11
- MM-YYYY -- على سبيل المثال، 01-2000 أو 1-2000

تدعم التنسيقات التالية YY أو YYYY:

- شهر-سنة - على سبيل المثال، يناير-2010 أو يناير-2010 أو 10 يناير أو يناير-10
- الشهر YYY -- على سبيل المثال، "يناير 2010" أو "يناير 2010" أو "10 يناير" أو "10 يناير"
- شهر سنة - على سبيل المثال، "يناير 2010" أو "يناير 2010" أو "يناير 10" أو "يناير 10"
- شهر/سنة - على سبيل المثال، "يناير/2010" أو "يناير/2010" أو "يناير/10" أو "يناير/10"

أسماء الأشهر المقبولة:

- الإنكليزية
  - يناير، فبراير، مارس، أبريل، مايو، يونيو، يوليو، أغسطس، سبتمبر، أكتوبر، نوفمبر، ديسمبر
  - يناير فبراير مارس مايو يونيو يوليو أغسطس أكتوبر 2011

## <a name="func_us_address"></a>Func_us_address

Func_us_address تبحث عن اسم ولاية أمريكية أو اختصار بريدي متبوعا برمز بريدي صالح. يجب أن يكون الرمز البريدي أحد الرموز البريدية الصحيحة المقترنة باسم حالة الولايات المتحدة أو اختصارها. لا يمكن فصل اسم الحالة الأمريكية والرمز البريدي بعلامات ترقيم أو أحرف.

امثله:

- واشنطن 98052
- واشنطن 98052-9998
- WA 98052
- WA 98052-9998
