---
title: جهة تسجيل المجالات التي لها قيود على الإعداد
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- MET150
ROBOTS: NOINDEX
description: تقدم بعض جهة تسجيل المجالات خدمات محدودة، مما يعني أن جميع ميزات Microsoft لن تعمل مع كل مجال.
ms.openlocfilehash: 2d192f03c5a586e4355c1f9a08d312a07af3d501
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575042"
---
# <a name="domain-registrars-with-setup-limitations"></a>جهة تسجيل المجالات التي لها قيود على الإعداد

[إنشاء سجلات DNS في DNSMadeEasy ل Microsoft](#create-dns-records-at-dnsmadeeasy-for-microsoft)\
[إنشاء سجلات DNS في easyDNS ل Microsoft](#create-dns-records-at-easydns-for-microsoft)\
[إنشاء سجلات DNS في Freenom ل Microsoft](#create-dns-records-at-freenom-for-microsoft)\
[إنشاء سجلات DNS في MyDomain ل Microsoft](#create-dns-records-at-mydomain-for-microsoft)\
[إنشاء سجلات DNS ل Microsoft Windows DNS المستندة إلى](#create-dns-records-for-microsoft-using-windows-based-dns)\
[إنشاء سجلات DNS عند إدارة مجالك بواسطة Google (eNom)](#create-dns-records-when-your-domain-is-managed-by-google-enom)\
[إنشاء سجلات DNS في 1&IONOS ل Microsoft](#create-dns-records-at-11-ionos-for-microsoft)

لدى بعض جهة تسجيل المجالات قيود ملحوظة على الخدمة، مما يعني أن جميع ميزات Microsoft لن تعمل مع كل مجال. يتم تحديد قيود معينة لبعض المسجلين في هذه المقالة. 

## <a name="create-dns-records-at-dnsmadeeasy-for-microsoft"></a>إنشاء سجلات DNS في DNSMadeEasy ل Microsoft

بالنسبة إلى حسابات DNSMadeEasy، تم شراء المجال الذي أضفته من جهة تسجيل مجالات منفصلة. لا يقدم DNSMadeEasy خدمات تسجيل المجالات. إن قدرتك على تسجيل الدخول في DNSMadeEasy وإنشاء سجل DNS دليل كاف على الملكية.

## <a name="create-dns-records-at-easydns-for-microsoft"></a>إنشاء سجلات DNS في easyDNS ل Microsoft

لا تتوفر سجلات SRV حاليا ضمن أي حزمة خدمة easyDNS. قد تحتاج إلى الترقية إلى مستوى خدمة أعلى باستخدام easyDNS لإضافة سجلات SRV المطلوبة Teams.

## <a name="create-dns-records-at-freenom-for-microsoft"></a>إنشاء سجلات DNS في Freenom ل Microsoft

لا يدعم موقع ويب Freenom إضافة سجلات SRV، مما يعني أن Teams البريد الإلكتروني وميزات البريد الإلكتروني لن تعمل. بغض النظر عن خطة Microsoft التي تستخدمها، هناك قيود ملحوظة على الخدمة، وقد ترغب في التبديل إلى موفر آخر لاستضافة DNS.

## <a name="create-dns-records-at-mydomain-for-microsoft"></a>إنشاء سجلات DNS في MyDomain ل Microsoft

لا يدعم موقع MyDomain على الويب سجلات SRV، مما يعني أن Teams البريد الإلكتروني وميزات البريد الإلكتروني لن تعمل. بغض النظر عن خطة Microsoft التي تستخدمها، إذا كنت تدير سجلات DNS في MyDomain، فهناك قيود ملحوظة على الخدمة، وقد ترغب في التبديل إلى موفر آخر لاستضافة DNS.

## <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>إنشاء سجلات DNS ل Microsoft Windows DNS المستندة إلى

انتقل إلى الصفحة التي تحتوي على سجلات DNS لمجالك. إذا كنت تعمل في Windows Server 2008، فاذهب إلى **بدء**، **تشغيل**. إذا كنت تعمل في Windows Server 2012، فاضغط على Windows **وr****.** اكتب **dnsmgmnt.msc**، ثم حدد **موافق**. في إدارة DNS، قم بتوسيع **اسم خادم DNS**، مناطق  **البحث إلى الأمام**. حدد مجالك. أنت الآن جاهز لإنشاء سجلات DNS.

## <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>إنشاء سجلات DNS عند إدارة مجالك بواسطة Google (eNom)

إذا اشتريت مجالك من خلال Google أثناء التسجيل للحصول على حساب Google Apps for Work، فإن سجلات DNS تدار بواسطة Google ولكنها مسجلة مع eNom. يمكنك الوصول إلى eNom، وإنشاء DNS، من خلال صفحة Google Domains.

## <a name="create-dns-records-at-11-ionos-for-microsoft"></a>إنشاء سجلات DNS في 1&IONOS ل Microsoft

1&IONOS أن يكون للمجال سجل MX وسجل CNAME من المستوى الأعلى. وهذا يحد من الطرق التي يمكنك من خلالها تكوين Exchange Online Microsoft. يوجد حل بديل، ولكننا نوصي باستخدامه فقط إذا كان لديك بالفعل خبرة في إنشاء مجال فرعي في 1&1 IONOS.

إذا اخترت إدارة سجلات Microsoft DNS في 1&1 IONOS، فاتبع الخطوات الواردة في هذه المقالة للتحقق من مجالك ول إعداد سجلات DNS للبريد الإلكتروني و Skype for Business Online وما إلى ذلك.

1&IONOS حل بديل بحيث يمكنك استخدام سجل MX مع سجلات CNAME المطلوبة لخدمات البريد الإلكتروني من Microsoft. يتطلب هذا الحل البديل إنشاء مجموعة من المناطق الفرعية في 1&IONOS، وتعيينها إلى سجلات CNAME.

> [!NOTE]
> تأكد من توفر اثنين على الأقل من المناطق الفرعية قبل بدء هذا الإجراء. نوصي بهذا الحل فقط إذا كان لديك بالفعل خبرة في إنشاء مجال فرعي في 1&IONOS.

### <a name="basic-cname-records"></a>سجلات CNAME الأساسية

1.  للبدء، انتقل إلى صفحة المجالات في 1&IONOS. سيطلب منك تسجيل الدخول.

1.  حدد **إدارة المجالات**.

1.  في صفحة مركز المجالات، ابحث عن المجال الذي تريد تحديثه، ثم حدد **إدارة المجالات الفرعية**. ستقوم الآن بإنشاء اثنين من مجالات العمل الفرعية مع تعيين قيمة الاسم  المستعار لكل منهما (هذا مطلوب لأن 1&1 IONOS يدعم سجل CNAME واحد فقط من المستوى الأعلى، ولكن Microsoft تتطلب سجلات CNAME متعددة.)

1.  أولا، ستنشئ المعرف الفرعي Autodiscover. في المقطع **نظرة عامة على مجال فرعي** ، حدد **إنشاء مجال فرعي**.

1.  في المربع **إنشاء مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة **إنشاء مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف قيمة **الاسم المستعار** في خطوة لاحقة.)

    |إنشاء منطقة فرعية|الاسم المستعار|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1.  حدد **إنشاء منطقة فرعية**.

1.  في **المقطع نظرة** عامة على مجال فرعي، حدد موقع مجال autodiscover الفرعي الذي أنشأته للتو، ثم حدد عنصر تحكم اللوحة (v) لهذا مجال فرعي.

1.  في المنطقة **الإعدادات**، حدد **تحرير DNS الإعدادات**.

1.  في المقطع **سجلات A/AAAA (عناوين IP)،** في منطقة **عنوان IP (سجل)،** حدد **CNAME**.

1. في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها.

    |إنشاء منطقة فرعية|الاسم المستعار|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1. حدد خانة الاختيار ل **إخلاء** المسؤولية أنا على علم.

1. حدد **حفظ**.

### <a name="additional-cname-records"></a>سجلات CNAME إضافية

تمكن سجلات CNAME الإضافية في الإجراء التالي Skype for Business عبر الإنترنت. استخدم الخطوات نفسها التي استخدمتها لسجلي CNAME الذي أنشأته بالفعل.

**إنشاء الناحية الفرعية الثالثة (Lyncdiscover)**

1.  في المقطع **نظرة عامة على القطاع الفرعي** ، حدد **إنشاء موقع فرعي**.

1.  في المربع **إنشاء مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة **إنشاء مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف قيمة **الاسم المستعار** في خطوة لاحقة.)

    |إنشاء منطقة فرعية|الاسم المستعار|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  حدد **إنشاء منطقة فرعية**.

1.  في صفحة مركز المجالات، حدد **إدارة المجالات الفرعية**.

1.  في **القسم نظرة** عامة على مجال فرعي، ابحث عن مجال lyncdiscover الفرعي الذي أنشأته للتو، ثم حدد عنصر تحكم اللوحة (v) لهذا مجال فرعي. في المنطقة **الإعدادات**، حدد **تحرير DNS الإعدادات**.

1.  في المقطع **سجلات A/AAAA (عناوين IP)،** في منطقة **عنوان IP (سجل)،** حدد **CNAME**.

1.  في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها.

    |إنشاء منطقة فرعية|الاسم المستعار|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  حدد خانة **الاختيار ل إخلاء** المسؤولية أنا على علم، ثم حدد **حفظ**.

1.  في مربع **الحوار تحرير DNS الإعدادات**، حدد **نعم**.

**إنشاء العالم الفرعي الرابع (SIP)**

1.  في المقطع **نظرة عامة على مجال فرعي** ، حدد **إنشاء مجال فرعي**.

1.  في المربع **إنشاء مجال** فرعي للمربع الفرعي الجديد، اكتب القيمة **إنشاء مجال** فرعي فقط من الجدول التالي أو قم بنسخها ولصقها. (تضيف القيمة **الاسم المستعار** في خطوة لاحقة.)

    |إنشاء منطقة فرعية|الاسم المستعار|
    |:----|:----|
    |sip|sipdir.online.lync.com|  

1.  حدد **إنشاء منطقة فرعية**.

1.  في صفحة مركز المجالات، حدد **إدارة المجالات الفرعية**.

1.  في **القسم نظرة** عامة على مجال فرعي، ابحث عن مجال sip الفرعي الذي أنشأته للتو، ثم حدد عنصر تحكم اللوحة (v) لذلك مجال العمل الفرعي. <br/> في المنطقة **الإعدادات**، حدد **تحرير DNS الإعدادات**.

1.  في المقطع **سجلات A/AAAA (عناوين IP)،** في منطقة **عنوان IP (سجل)،** حدد **CNAME**.

1.  في المربع **الاسم المستعار:** اكتب القيمة **الاسم** المستعار فقط من الجدول التالي أو انسخها واللصق بها.

    |إنشاء منطقة فرعية|الاسم المستعار|
    |:----|:----|
    |sip|sipdir.online.lync.com|

1.  حدد خانة **الاختيار ل إخلاء** المسؤولية أنا على علم، ثم حدد **حفظ**.

1.  في مربع **الحوار تحرير DNS الإعدادات**، حدد **نعم**.

### <a name="cname-records-needed-for-mdm"></a>سجلات CNAME المطلوبة ل MDM

اتبع الإجراء الذي استخدمته لسجلات CNAME الأربعة الأخرى ولكن مع توفير هذه القيم:

|إنشاء منطقة فرعية|الاسم المستعار|
|:----|:----|
|enterpriseregistration|enterpriseregistration.windows.net|
|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|
