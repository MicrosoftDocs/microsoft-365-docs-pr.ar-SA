---
title: تعريف كيان سلسلة الاتصال SQL Server
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
description: SQL Server تعريف كيان نوع المعلومات الحساسة لسلسلة الاتصال.
ms.openlocfilehash: 503b2bae244cec8de5da29228f6517433a162ca1
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944594"
---
# <a name="sql-server-connection-string"></a>سلسلة اتصال SQL Server

## <a name="format"></a>تنسيق

السلسلة `User Id`، `User ID`أو `uid`، أو `UserId` متبوعة بالأحرف والسلاسل الموضحة في النمط أدناه.

## <a name="pattern"></a>نمط

- السلسلة `User Id`أو `User ID`، `uid`أو ، أو `UserId`
- أي تركيبة بين 1-200 حرف أو رقم أو رموز أو أحرف خاصة أو مسافات صغيرة أو كبيرة
- السلسلة `Password` أو `pwd` المكان `pwd` الذي لا يسبقه حرف صغير
- علامة التساوي (=)
- أي حرف ليس علامة الدولار ($) أو رمز النسبة المئوية (٪)، أو أكبر من الرمز (>)، أو عند الرمز (@)، أو علامة الاقتباس (")، أو فاصلة منقوطة (;)، أو قوس أيسر([)، أو قوس أيسر ({)
- أي تركيبة من 7 إلى 128 حرفا ليست فاصلة منقوطة (;) أو شرطة مائلة للأمام (/) أو علامة اقتباس (")
- فاصلة منقوطة (;) أو علامة الاقتباس (")

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `CEP_Regex_SQLServerConnectionString` العادي عن المحتوى الذي يطابق النمط.
- لم يتم العثور على كلمة أساسية منها `CEP_GlobalFilter` .
- لا يعثر التعبير `CEP_PasswordPlaceHolder` العادي على محتوى يطابق النمط.
- لا يعثر التعبير `CEP_CommonExampleKeywords` العادي على محتوى يطابق النمط.

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- بعض كلمات المرور
- somepassword
- secretPassword
- عينه

### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- `Password` أو `pwd` متبوعة بمسافات 0-2، وعلامة المساواة (=)، ومسافات 0-2، وعلامة نجمية (*) -OR-
- `Password` أو `pwd` متبوعا ب:
    - علامة التساوي (=)
    - أقل من رمز (<)
    - أي تركيبة من 1-200 حرف عبارة عن أحرف كبيرة أو صغيرة أو أرقام أو علامة نجمية (*) أو واصلة (-) أو تسطير (_) أو حرف مسافة بيضاء
    - رمز أكبر من (>)

### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

يعرف نوع المعلومات الحساسة هذا هذه الكلمات الأساسية باستخدام تعبير عادي، وليس قائمة كلمات أساسية.

- Contoso
- Fabrikam
- Northwind
- رمل
- مربع واحد
- Localhost
- 127.0.0.1
- الاختبارات.<!--no-hyperlink-->كوم
- s-int.<!--no-hyperlink-->صافي