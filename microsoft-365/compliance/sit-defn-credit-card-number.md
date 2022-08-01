---
title: تعريف كيان رقم بطاقة الائتمان
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
description: تعريف كيان نوع المعلومات الحساسة لرقم بطاقة الائتمان.
ms.openlocfilehash: 0d75c0af6c67c1d617db9f7f28fbc63c27e4d05a
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944362"
---
# <a name="credit-card-number"></a>رقم بطاقة الائتمان

## <a name="format"></a>تنسيق

من 14 إلى 19 رقما يمكن تنسيقها أو عدم تنسيقها (ddddddddd) والتي يجب أن تجتاز اختبار Luhn.

## <a name="pattern"></a>نمط

الكشف عن البطاقات من جميع العلامات التجارية الرئيسية في جميع أنحاء العالم، بما في ذلك فيز، و MasterCard، وD discover Card، وJCB، و American Express، وبطاقات الهدايا، وبطاقات diner، و Rupay و China UnionPay.

## <a name="checksum"></a>المجموع الاختباري

نعم، التحقق من Luhn

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- تبحث الدالة `Func_credit_card` عن المحتوى الذي يطابق النمط.
- أحد الشروط التالية صحيح:
  - تم العثور على كلمة أساسية منها `Keyword_cc_verification` .
  - تم العثور على كلمة أساسية منها `Keyword_cc_name` .
  - تبحث الدالة `Func_expiration_date` عن تاريخ بتنسيق التاريخ الصحيح.
- يمر المجموع الاختباري.

سياسة DLP لديها ثقة منخفضة في أنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، في حدود 300 حرف:

- تبحث الدالة `Func_credit_card` عن المحتوى الذي يطابق النمط.
- يمر المجموع الاختباري.

```xml
<!-- Credit Card Number -->
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_credit_card" />
  </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- التحقق من البطاقة
- رقم تعريف البطاقة
- cvn
- سيد
- cvc2
- cvv2
- كتلة تثبيت
- رمز الأمان
- رقم الأمان
- رقم الأمان
- رقم المشكلة
- المشكلة رقم
- صورة مشفرة
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- رقم sicherheits
- verfalldatum
- codice di verifica
- القد. sicurezza
- cod sicurezza
- n autorizzzzzzone
- código
- الكدقل
- القد. ثواني
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- القد. seguranca
- القد. segurança
- cód. seguranca
- cód segurança
- cod seguranca
- cod segurança
- cód seguranca
- número de verificação
- numero de verificaero
- ablauf
- gültig bis
- gültigkeitsdatum
- gultig bis
- gultigkeitsdatum
- scadenza
- scad البيانات
- fecha de expiracion
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expira تاريخ انتهاء الصلاحية
- انتهاء صلاحية البيانات em que
- صالح
- بساله
- vencimento
- المعاملات
- رقم المعاملة
- رقم المرجع
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

### <a name="keyword_cc_name"></a>Keyword_cc_name

- اميكس
- american express
- americanexpress
- americano espresso
- فيزا
- ماستركارد
- البطاقة الرئيسية
- Mc
- بطاقات رئيسية
- البطاقات الرئيسية
- نادي العشاء
- نادي diners
- dinersclub
- اكتشاف
- اكتشاف البطاقة
- بطاقة الاكتشاف
- اكتشاف البطاقات
- JCB
- علامة تجارية
- مكتب البطاقات اليابانية
- كرونة دوارة
- الذبذبة
- بطاقة ائتمان
- Cc #
- نسخة#:

- تاريخ انتهاء الصلاحية
- تاريخ exp
- تاريخ انتهاء الصلاحية
- تاريخ انتهاء الصلاحية
- تاريخ الا exp
- انتهاء صلاحية التاريخ
- بطاقة بنكية
- بانككارد
- رقم البطاقة
- رقم البطاقة
- رقم البطاقة
- أرقام البطاقات
- أرقام البطاقات
- بطاقة ائتمان
- بطاقات الائتمان
- بطاقات الائتمان
- نسخة من نسخة
- حامل البطاقة
- حامل البطاقه
- حاملو البطاقات
- حاملو البطاقات
- التحقق من البطاقة
- بطاقة اختيار
- التحقق من البطاقات
- بطاقات اختيار
- بانككارد
- بطاقة خصم
- بطاقات الخصم
- بطاقات الخصم
- بطاقة جهاز atm
- بطاقة atmcard
- بطاقات ال atm
- بطاقات atmcard
- enroute
- طريقها
- نوع البطاقة
- Cardmember Acct
- حساب cardmember
- Cardno
- بطاقة الشركة
- بطاقات الشركة
- نوع البطاقة
- رقم حساب البطاقة
- حساب عضو البطاقة
- Cardmember Acct.
- رقم البطاقة.
- رقم البطاقة
- رقم البطاقة
- قافزة دوارة
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nانهارس دي لا كارت
- nاصفة من نوع carte
- kreditkarte
- الكارتي
- karteninhaber
- كارتينهارس
- kreditkartenin fisherer
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- كرتنمر
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- carta credito
- ن. كارتا
- n carta
- Nr. كارتا
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- أجهزة atm في tarjeta
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nاصفة de tarjeta
- لا. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetahabiente
- cartão de crédito
- cartão de credito
- cartao de crédito
- cartao de credito
- cartão de débito
- cartao de débito
- cartão de debito
- cartao de debito
- débito automático
- الدينو تلقائي
- número do cartão
- numero do cartão
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nلاسم do cartão
- nلاهي do cartao
- nلاين. do cartão
- no do cartão
- لا يوجد قرطاو
- لا. do cartão
- لا. do cartao
- rupay
- الدفع الموحد
- الدفع الموحد
- diner's
- داينرز
- クレジットカード番号
- クレジットカードナンバー
- クレジットカード＃
- クレジットカード
- クレジット
- クレカ
- カード番号
- カードナンバー
- カード＃
- アメックス
- アメリカンエクスプレス
- アメリカン エクスプレス
- الفيزاカード
- الفيزا カード
- マスターカード
- マスター カード
- マスター
- ダイナースクラブ
- ダイナース クラブ
- ダイナース
- 有効期限
- 期限
- キャッシュカード
- キャッシュ カード
- カード名義人
- カードの名義人
- カードの名義
- デビット カード
- デビットカード
- 中国银联
- 银联