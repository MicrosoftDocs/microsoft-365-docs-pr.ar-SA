---
title: التشفير في Microsoft Dynamics 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: تعرف على كيفية استخدام Microsoft لتقنية التشفير لحماية بيانات العملاء في Microsoft Dynamics 365 أثناء العمل في قاعدة بيانات Microsoft وأثناء نقلها.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ba3dbef73b7674364f19e83befdbb8cdfe417ad6
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63568591"
---
# <a name="encryption-in-microsoft-dynamics-365"></a>التشفير في Microsoft Dynamics 365

تستخدم Microsoft تقنية التشفير لحماية بيانات العملاء في Dynamics 365 أثناء العمل في مركز بيانات Microsoft وأثناء نقلها بين أجهزة المستخدمين مراكز البيانات لدينا. يتم تشفير الاتصالات المنشأة بين العملاء مراكز بيانات Microsoft، كما يتم تأمين كل نقاط النهاية العامة باستخدام TLS القياسي في المجال. تنشئ TLS اتصالا محسنا من المستعرض إلى الخادم بشكل فعال للمساعدة على ضمان سرية البيانات وتكاملها بين أسطح المكتب و مراكز البيانات. بعد تنشيط تشفير البيانات، لا يمكن إيقاف تشغيله. لمزيد من المعلومات، راجع [تشفير البيانات على مستوى الحقل](/previous-versions/dynamicscrm-2016/developers-guide/dn481562(v=crm.8)).

يستخدم Dynamics 365 تشفير مستوى Microsoft SQL Server قياسيا من أجل مجموعة من سمات الكيانات الافتراضية التي تحتوي على معلومات حساسة، مثل أسماء المستخدمين وكلمات مرور البريد الإلكتروني. يمكن أن تساعد هذه الميزة المؤسسات على تلبية متطلبات التوافق المقترنة ب FIPS 140-2. تشفير البيانات على مستوى الحقل مهم بشكل خاص في السيناريوهات التي تستفيد من [](/previous-versions/dynamicscrm-2016/administering-dynamics-365/hh699800(v=crm.8))موجه البريد الإلكتروني Microsoft Dynamics CRM، الذي يجب أن يخزن أسماء المستخدمين وكلمات المرور لتمكين التكامل بين مثيل Dynamics 365 وخدمة بريد إلكتروني.

تستخدم كل مثيلات Dynamics 365 [Microsoft SQL Server](/sql/relational-databases/security/encryption/transparent-data-encryption) تشفير البيانات الشفاف (TDE) لتنفيذ تشفير البيانات في الوقت الحقيقي عند كتابتها على القرص (في وضع آخر). يقوم TDE بتشفير SQL Server البيانات و Azure SQL و Azure SQL بيانات Data Warehouse. بشكل افتراضي، تقوم Microsoft بتخزين مفاتيح تشفير قاعدة البيانات وإدارتها لمثيلات Dynamics 365. (يتم إنشاء المفاتيح المستخدمة بواسطة Dynamics 365 for Financials بواسطة .NET Framework API لحماية البيانات.)

توفر ميزة إدارة المفاتيح في مركز إدارة Dynamics 365 للمسؤولين إمكانية الإدارة الذاتية لمفاتيح تشفير قاعدة البيانات المقترنة بمثيلات Dynamics 365. (تتوفر مفاتيح تشفير قاعدة البيانات المدارة ذاتيا فقط في تحديث شهر يناير 2017 ل Microsoft Dynamics 365 وقد لا تكون متوفرة للإصدارات الأحدث. لمزيد من المعلومات، راجع [إدارة مفاتيح التشفير لمثيل Dynamics 365 (عبر الإنترنت](/dynamics365/customer-engagement/admin/manage-encryption-keys-instance)). تدعم ميزة الإدارة الرئيسية ملفات مفاتيح تشفير PFX و BYOK، مثل تلك المخزنة في HSM. (لمزيد من المعلومات حول إنشاء مفتاح محمي HSM ونقله عبر الإنترنت، راجع كيفية إنشاء مفاتيح [محمية HSM ونقلها ل Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys).)

لاستخدام خيار مفتاح تشفير التحميل، ستحتاج إلى مفتاح التشفير العام والخاص.

تأخذ ميزة الإدارة الأساسية تعقيدات إدارة مفاتيح التشفير باستخدام Azure Key Vault لتخزين مفاتيح التشفير بشكل آمن. يساعد Azure Key Vault على حماية مفاتيح التشفير وأسرارها التي تستخدمها التطبيقات والخدمات السحابية. لا تتطلب ميزة الإدارة الرئيسية أن يكون لديك اشتراك Azure Key Vault وفي معظم الحالات، لا حاجة للوصول إلى مفاتيح التشفير المستخدمة ل Dynamics 365 داخل المخزن.
