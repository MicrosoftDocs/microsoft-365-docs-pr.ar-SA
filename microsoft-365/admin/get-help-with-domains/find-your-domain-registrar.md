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
ms.custom:
- VSBFY23
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: b5b633ba-1e56-4a98-8ff5-2acaac63a5c8
description: تعرف على كيفية العثور على جهة تسجيل المجالات وموفر استضافة DNS باستخدام بحث InterNIC.
ms.openlocfilehash: 2bfb4fc831d23751ab558dd833c49f84cb17c4c5
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67086397"
---
# <a name="find-your-domain-registrar"></a>البحث عن جهة تسجيل المجالات

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

## <a name="domain-registrar"></a>جهة تسجيل المجالات

### <a name="find-your-domain-name-registrar"></a>البحث عن جهة تسجيل أسماء المجالات

> [!NOTE]
> تعمل المجالات التي تنتهي *.COM* *و.NET* *و.EDU* فقط مع هذه الأداة.

1. في [صفحة البحث في InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770)، في المربع **"بحث Whois"** ، اكتب مجالك. على سبيل المثال،  *contoso.com.*

2. حدد خيار **"المجال** "، ثم حدد **"إرسال**".

3. في صفحة **نتائج بحث Whois** ، حدد موقع إدخال **جهة التسجيل** . يسرد هذا الإدخال المؤسسة التي توفر خدمة جهة تسجيل المجالات لمجالك.

## <a name="dns-hosting-provider"></a>موفر استضافة DNS

### <a name="find-your-dns-hosting-provider"></a>البحث عن موفر استضافة DNS

> [!NOTE]
> تعمل المجالات التي تنتهي *.COM* *و.NET* *و.EDU* فقط مع هذه الأداة.

1. في [صفحة البحث في InterNIC](https://go.microsoft.com/fwlink/p/?LinkId=402770)، في المربع **"بحث Whois"** ، اكتب مجالك. على سبيل المثال، contoso.com.

2. حدد خيار **"المجال** "، ثم حدد **"إرسال**".

3. في الصفحة **"نتائج بحث Whois** "، حدد موقع الإدخال الأول **لخادم الاسم** .

4. انسخ معلومات خادم الأسماء (NS) التي تظهر بعد علامة النقطتين (:)، ثم الصقها في مربع **البحث** في أعلى الصفحة. حدد **خادم الأسماء**، ثم حدد **"إرسال**".

5. في صفحة **نتائج بحث Whois** ، حدد موقع إدخال **جهة التسجيل** . يسرد هذا الإدخال موفر استضافة DNS، موفر DNS الذي يمتلك خادم الاسم لمجالك.

---

