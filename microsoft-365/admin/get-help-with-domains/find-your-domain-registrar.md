---
title: البحث عن جهة تسجيل المجالات
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: b5b633ba-1e56-4a98-8ff5-2acaac63a5c8
description: تعرف على كيفية العثور على جهة تسجيل المجالات وموفر استضافة DNS باستخدام البحث في InterNIC.
ms.openlocfilehash: c7802067bc3d8397d9f7b7ddf0f6cda4dd57c38b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567343"
---
# <a name="find-your-domain-registrar"></a>البحث عن جهة تسجيل المجالات

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه.

## <a name="domain-registrar"></a>جهة تسجيل المجالات

### <a name="find-your-domain-name-registrar"></a>البحث عن جهة تسجيل أسماء المجالات

> [!NOTE]
> تعمل فقط المجالات التي تنتهي ب *.COM* و *.NET* و *.EDU* مع هذه الأداة.

1. في صفحة [البحث InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770)، في المربع **بحث Whois** ، اكتب مجالك. على سبيل المثال  *، contoso.com.*

2. حدد **الخيار المجال** ، ثم حدد **إرسال**.

3. في صفحة **نتائج بحث Whois** ، حدد موقع إدخال **جهة** التسجيل. يسرد هذا الإدخال المؤسسة التي توفر خدمة جهة تسجيل لمجالك.

## <a name="dns-hosting-provider"></a>موفر استضافة DNS

### <a name="find-your-dns-hosting-provider"></a>البحث عن موفر استضافة DNS

> [!NOTE]
> تعمل فقط المجالات التي تنتهي ب *.COM* و *.NET* و *.EDU* مع هذه الأداة.

1. في صفحة [البحث InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770)، في المربع **بحث Whois** ، اكتب مجالك. على سبيل المثال، contoso.com.

2. حدد **الخيار المجال** ، ثم حدد **إرسال**.

3. في الصفحة **نتائج بحث Whois** ، حدد موقع الإدخال **الأول خادم** الاسم.

4. انسخ معلومات خادم الاسم (NS) التي تظهر بعد النقطتين (:)، ثم اللصق في **المربع بحث في** أعلى الصفحة. حدد **Nameserver،** ثم حدد **إرسال**.

5. في صفحة **نتائج بحث Whois** ، حدد موقع إدخال **جهة** التسجيل. يسرد هذا الإدخال موفر استضافة DNS، وهو موفر DNS الذي يملك خادم الاسم لمجالك.

---

