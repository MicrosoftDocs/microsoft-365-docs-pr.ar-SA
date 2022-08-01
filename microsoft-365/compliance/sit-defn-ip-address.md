---
title: تعريف كيان عنوان IP
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
description: تعريف كيان نوع المعلومات الحساسة لعنوان IP.
ms.openlocfilehash: 19c883cccdc45682514bcd553f1b8e4a09d90e12
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944568"
---
# <a name="ip-address"></a>عنوان IP

## <a name="format"></a>تنسيق

### <a name="ipv4"></a>IPv4:
النمط المعقد الذي يمثل إصدارات عناوين IPv4 المنسقة (الفترات) وغير المنسقة (بدون نقاط)

### <a name="ipv6"></a>IPv6:
النمط المعقد الذي يمثل أرقام IPv6 المنسقة (التي تتضمن نقطتين)

## <a name="pattern"></a>نمط

## <a name="checksum"></a>المجموع الاختباري

لا

## <a name="definition"></a>تعريف

بالنسبة إلى IPv6، يتمتع نهج DLP بثقة عالية بأنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ipv6_address` العادي عن المحتوى الذي يطابق النمط.
- لم يتم العثور على كلمة أساسية منها `Keyword_ipaddress` .

بالنسبة إلى IPv4، يتمتع نهج DLP بثقة عالية بأنه اكتشف هذا النوع من المعلومات الحساسة إذا كان، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ipv4_address` العادي عن المحتوى الذي يطابق النمط.
- تم العثور على كلمة أساسية منها `Keyword_ipaddress` .

بالنسبة إلى IPv6، يتمتع نهج DLP بثقة عالية بأنه تم الكشف عن هذا النوع من المعلومات الحساسة إذا، على مقربة من 300 حرف:

- يبحث التعبير `Regex_ipv6_address` العادي عن المحتوى الذي يطابق النمط.
- لم يتم العثور على كلمة أساسية منها `Keyword_ipaddress` .

```xml
    <!-- IP Address -->
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>الكلمات الرئيسيه

### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (هذه الكلمة الأساسية حساسة لحالة الأحرف)
- عنوان ip
- عناوين ip
- بروتوكول الإنترنت
- IP-כתובת ה