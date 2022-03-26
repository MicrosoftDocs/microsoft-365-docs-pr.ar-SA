---
title: كيف Exchange Online تأمين أسرار بريدك الإلكتروني
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 07/01/2019
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 989ba10c-f73f-4efb-ad1b-af3322e5f376
ms.collection:
- M365-security-compliance
description: بالإضافة إلى مركز Office 365 الذي يوفر معلومات الأمان والخصوصية والتوافق ل Microsoft 365، قد ترغب في معرفة كيفية مساعدة Microsoft في حماية السرية التي تخزنها في مراكز البيانات الخاصة بها. نستخدم تقنية تسمى إدارة المفاتيح الموزعة (DKM).
ms.openlocfilehash: a1d939ebfc1ecba1e7cb8b97111f677f754894b1
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63568558"
---
# <a name="how-exchange-online-secures-your-email-secrets"></a>كيف Exchange Online تأمين أسرار بريدك الإلكتروني

تصف هذه المقالة كيف تقوم Microsoft بتأمين أسرار بريدك الإلكتروني في مراكز البيانات الخاصة بها.
  
## <a name="how-do-we-secure-secret-information-provided-by-you"></a>كيف يمكننا تأمين المعلومات السرية التي توفرها أنت؟

بالإضافة إلى مركز Office 365 الذي يوفر معلومات الأمان والخصوصية والتوافق ل [Office 365](./get-started-with-service-trust-portal.md)، قد ترغب في معرفة كيف تساعد Microsoft في حماية السرية التي تقدمها في مراكز البيانات الخاصة بها. نستخدم تقنية تسمى إدارة المفاتيح الموزعة (DKM).
  
[إدارة المفاتيح الموزعة](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) (DKM) هي وظيفة من جانب العميل تستخدم مجموعة من المفاتيح السرية لتشفير المعلومات وفك تشفيرها. يمكن لأعضاء مجموعة أمان معينة فقط في خدمات مجال Active Directory الوصول إلى هذه المفاتيح لفك تشفير البيانات المشفرة بواسطة DKM. في Exchange Online، لا يشكل جزء من مجموعة الأمان هذه سوى حسابات خدمة معينة يتم تشغيل Exchange عمليات الأمان هذه بموجبها. كجزء من إجراء التشغيل القياسي في مركز البيانات، لا يتم منح أي بشري بيانات اعتماد تعد جزءا من مجموعة الأمان هذه، وبالتالي لا يمكن للانسان الوصول إلى المفاتيح التي يمكنها فك تشفير هذه السرية.
  
لأغراض تصحيح الأخطاء أو استكشاف الأخطاء وإصلاحها أو التدقيق، يجب على مسؤول مركز البيانات طلب وصول عال للحصول على بيانات اعتماد مؤقتة تكون جزءا من مجموعة الأمان. تتطلب هذه العملية مستويات متعددة من الموافقة القانونية. إذا تم منح حق الوصول، يتم تسجيل كل الأنشطة وتدقيقها. بالإضافة إلى ذلك، لا يتم منح حق الوصول إلا لفترة زمنية معينة تنتهي صلاحيتها تلقائيا بعد ذلك.
  
لمزيد من الحماية، تتضمن تقنية DKM عملية الالتفاف التلقائي للمفتاح وأرشفته. يضمن ذلك أيضا أنه يمكنك الاستمرار في الوصول إلى المحتوى الأقدم دون الحاجة إلى الاعتماد على المفتاح نفسه إلى أجل غير مسمى.
  
## <a name="where-does-exchange-online-make-use-of-dkm"></a>أين Exchange Online استخدام DKM؟

تستخدم Microsoft ["إدارة المفاتيح الموزعة](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)" لتشفير أسرارك في مراكز Exchange Online البيانات. على سبيل المثال:
  
- بيانات اعتماد حساب البريد الإلكتروني للحسابات المتصلة. الحسابات المتصلة هي حسابات جهة خارجية مثل Hotmail وGmail و Yahoo! حسابات البريد.

- مفتاح العميل. إذا كنت تستخدم تشفير [الخدمة مع "مفتاح العميل](customer-key-overview.md)"، فسوف تستخدم [مخزن مفاتيح Azure](/azure/key-vault/key-vault-whatis) لحماية أسرارك.

## <a name="related-topics"></a>المواضيع ذات الصلة

[التشفير في Office 365](encryption.md)
  
[تفاصيل المراجع التقنية حول التشفير](technical-reference-details-about-encryption.md)
  
[ضمان الخدمة في مركز توافق &amp; الأمان](./service-assurance.md)
