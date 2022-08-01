---
title: تعريف كيان رقم بطاقة الخصم في الاتحاد الأوروبي
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة الخصم في الاتحاد الأوروبي.
ms.openlocfilehash: 53e7ea3475786032d2871092e3c7e6c39697958c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944735"
---
# <a name="eu-debit-card-number"></a>رقم بطاقة خصم الاتحاد الأوروبي

## <a name="format"></a>تنسيق

16 رقما

## <a name="pattern"></a>نمط

نمط معقد وقوي

## <a name="checksum"></a>المجموع الاختباري

نعم

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_eu_debit_card` عن المحتوى الذي يطابق النمط.
- واحد على الأقل مما يلي صحيح:
    - تم العثور على كلمة أساسية منها `Keyword_eu_debit_card` .
    - تم العثور على كلمة أساسية منها `Keyword_card_terms_dict` .
    - تم العثور على كلمة أساسية منها `Keyword_card_security_terms_dict` .
    - تم العثور على كلمة أساسية منها `Keyword_card_expiration_terms_dict` .
    - تبحث الدالة `Func_expiration_date` عن تاريخ بتنسيق التاريخ الصحيح.
- يمر المجموع الاختباري.

```xml
    <!-- EU Debit Card Number -->
    <Entity id="0e9b3178-9678-47dd-a509-37222ca96b42" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_eu_debit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_eu_debit_card" />
          <Match idRef="Keyword_card_terms_dict" />
          <Match idRef="Keyword_card_security_terms_dict" />
          <Match idRef="Keyword_card_expiration_terms_dict" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- رقم الحساب
- رقم البطاقة
- رقم البطاقة.
- رقم الأمان
- Cc #

### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- رقم acct
- acct no
- american express
- americanexpress
- americano espresso
- اميكس
- بطاقة جهاز atm
- بطاقات ال atm
- atm kaart
- بطاقة atmcard
- بطاقات atmcard
- قالب atmkaart
- atmkaarten
- بانكوتاكت
- بطاقة بنكية
- رسم بنكي
- حامل البطاقة
- حاملو البطاقات
- رقم البطاقة
- رقم البطاقة
- أرقام البطاقات
- نوع البطاقة
- cardano numerico
- حامل البطاقه
- حاملو البطاقات
- رقم البطاقة
- أرقام البطاقات
- كارتا بيانكا
- carta credito
- carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- قافزة دوارة
- كرونة دوارة
- bleue للكارت
- carte de credit
- carte de crédit
- carte di credito
- الذبذبة
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- Cb
- نسخة من نسخة
- التحقق من البطاقة
- التحقق من البطاقات
- بطاقة اختيار
- بطاقات اختيار
- chequekaart
- المعلاق
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- بطاقة ائتمان
- بطاقات الائتمان
- بطاقة ائتمان
- بطاقات الائتمان
- debetkaart
- debetkaarten
- بانككارد
- بطاقات الخصم
- بطاقة خصم
- بطاقات الخصم
- الدينو تلقائي
- نادي diners
- dinersclub
- اكتشاف
- اكتشاف البطاقة
- اكتشاف البطاقات
- بطاقة الاكتشاف
- بطاقات الاكتشاف
- débito automático
- Edc
- eigentümername
- بطاقة الخصم الأوروبي
- hoofdkaart
- hoofdkaarten
- في الفياجية
- مكتب البطاقات اليابانية
- kaartdienst في اليابان
- Jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- الكارتي
- karteninhaber
- كارتينهارس
- kartennr
- كرتنمر
- kreditkarte
- kreditkarten-nummer
- kreditkartenin fisherer
- kreditkarteninstitut
- kreditkartennummer
- kreditkartentyp
- مايسترو
- البطاقة الرئيسية
- البطاقات الرئيسية
- ماستركارد
- بطاقات رئيسية
- Mc
- نقدية غير مهيئة
- n carta
- كارتا
- no de tarjeta
- لا يوجد قرطاو
- no do cartão
- لا. de tarjeta
- لا. do cartao
- لا. do cartão
- nr carta
- Nr. كارتا
- numeri di scheda
- numero carta
- numero de cartao
- numero de carte
- numero de cartão
- numero de tarjeta
- numero della carta
- numero di carta
- numero di scheda
- numero do cartao
- numero do cartão
- numéro de carte
- كارتا nوو
- nاصفة من نوع carte
- nانهارس دي لا كارت
- nاصفة de tarjeta
- nلاهي do cartao
- nلاسم do cartão
- nلاين. do cartão
- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell'assegno
- scheda dell'atmosfera
- scheda dell'atmosfera
- scheda della بانكا
- scheda di controllo
- scheda di debito
- مصفوفة scheda
- schede'atmosfera
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- منفردا
- supporti di scheda
- supporto di scheda
- التبديل
- أجهزة atm في tarjeta
- tarjeta credito
- tarjeta de atm
- tarjeta de credito
- tarjeta de debito
- tarjeta debito
- tarjeta no
- tarjetahabiente
- tipo della scheda
- ufficio giapponese della
- scheda
- v pay
- v-pay
- فيزا
- علامة الجمع
- إلكترون
- visto
- visum
- vpay

### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- رقم تعريف البطاقة
- التحقق من البطاقة
- cardi la verifica
- سيد
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- القد. ثواني
- القد. seguranca
- القد. segurança
- القد. sicurezza
- codice di sicurezza
- codice di verifica
- الكدقل
- codigo de seguranca
- codigo de segurança
- مخطط تخطيطي
- التشفير
- صورة مشفرة
- cv2
- وسي
- cvc2
- cvn
- Cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. segurança
- código
- código de seguranca
- código de segurança
- de kaart controle
- geeft nr uit
- المشكلة رقم
- رقم المشكلة
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- لا. edizione
- لا. di sicurezza
- numero de securite
- numero de verificaero
- numero dev'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van veiligheid
- numéro de sécurité
- nالاستراد التلقائي
- número de verificação
- perno il
- كتلة تثبيت
- prufziffer
- prüfziffer
- رمز الأمان
- رقم الأمان
- رقم الأمان
- sicherheits kode
- sicherheitscode
- رقم sicherheits
- sblok sblok
- veiligheid nr
- veiligheidsaantal
- veiligheidscode
- veiligheidsnummer
- verfalldatum

### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf
- data de expira تاريخ انتهاء الصلاحية
- data de expiração
- data del exp
- data di exp
- data di scadenza
- انتهاء صلاحية البيانات em que
- scad البيانات
- بيانات scadenza
- تاريخ الصلاحية
- datum afloop
- datum van exp
- de afloop
- espira
- espira
- تاريخ exp
- exp datum
- انتهاء الصلاحيه
- تنتهي
- تنتهي
- انتهاء
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- قابل للتقييم
- صالح
- valido hasta
- بساله
- venc
- vencimento
- vencimiento
- verloopt
- ذرى
- vervaldatum
- vto
- válido hasta