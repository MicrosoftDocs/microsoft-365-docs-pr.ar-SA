---
title: إدارة قوالب الاتصالات الوصية في مكتبة الاتصالات في eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: يمكنك إضافة قوالب اتصالات الوصي (مثل قالب لإعلامات الاحتجاز) في eDiscovery (Premium) حتى يمكن استخدامها في أي حالة في مؤسستك.
ms.openlocfilehash: be8311a9687eb4edb9cc44e15264808a2a05a69a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945142"
---
# <a name="manage-custodian-communications-templates-in-ediscovery-premium"></a>إدارة قوالب الاتصالات الوصية في eDiscovery (Premium)

عندما تقوم أنت أو مستخدمون آخرون بإنشاء إعلام احتجاز أو أنواع أخرى من اتصالات الوصي، كان عليك إنشاء مستند الاتصال من البداية باستخدام محرر الاتصالات على علامة التبويب **Communications** في حالة eDiscovery (Premium). لقد أصدرنا الآن ميزة جديدة تتيح لك إنشاء قوالب اتصالات يمكن استخدامها لإنشاء الاتصالات في أي حال في مؤسستك. بعد إنشاء قوالب الاتصالات، تكون متوفرة لاستخدامها في حالة ما. وهذا يعني أن المساعدين القانونيين أو المستخدمين الآخرين الذين ينشئون اتصالات الوصي ليس عليهم البدء من البداية لإنشاء إعلام. بدلا من ذلك، يمكنهم تحديد قالب لإنشاء الإعلام الذي يتم إرساله إلى أمين.

تشرح هذه المقالة كيفية إنشاء قوالب اتصالات على مستوى المؤسسة وتحديدها عند إنشاء إعلام وصي جديد لحالة eDiscovery معينة (Premium).

## <a name="before-you-create-templates-in-the-communications-library"></a>قبل إنشاء قوالب في مكتبة الاتصالات

- يجب أن تكون مسؤول eDiscovery في مؤسستك لإضافة قوالب أو إزالتها في مكتبة الاتصالات في eDiscovery (Premium). لمزيد من المعلومات، راجع [تعيين أذونات eDiscovery في مدخل توافق Microsoft Purview](assign-ediscovery-permissions.md)  

- يمكن أن تحتوي مؤسستك على 50 قالبا كحد أقصى في مكتبة الاتصالات.

## <a name="create-a-communications-template"></a>إنشاء قالب اتصالات

1. في مدخل التوافق، انتقل إلى [eDiscovery (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764)، ثم انقر فوق **إعدادات eDiscovery (Premium**).

   ![تحديد إعدادات eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. في صفحة **الإعدادات**، حدد علامة تبويب **مكتبة الاتصالات**.

3. في صفحة **مكتبة الاتصالات** ، انقر فوق **"إنشاء**".

4. اتبع الإجراء لإنشاء اتصال أمين. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إنشاء إعلام احتجاز قانوني](create-hold-notification.md).

   > [!NOTE]
   > خطوات إنشاء قالب اتصالات هي نفسها سير العمل لإنشاء إعلام داخل حالة. الفرق الوحيد هو أنه عند إنشاء قالب، لا تحدد مسؤول إصدار ولا تعين أمناء. يتم تحديد مسؤول إصدار وتعيين أمناء عند استخدام قالب اتصالات لإنشاء إعلام أمين لحالة ما.

5. بعد إنشاء قالب، يتم عرضه على صفحة **مكتبة الاتصالات** .

   ![القوالب المعروضة في مكتبة الاتصالات](..\media\AeDCommunicationsLibrary1.png)

يمكنك أنت أو مسؤولو eDiscovery الآخرون تحرير قالب اتصالات. لا تؤثر أي تغييرات تجريها على قالب على أي إعلامات تم إنشاؤها مسبقا باستخدام هذا القالب أو تعدلها. سيتم تطبيق هذه التغييرات فقط على الإعلامات الجديدة التي تم إنشاؤها باستخدام القالب المحدث.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>استخدام قالب اتصالات لإنشاء إعلام أمين

بعد إنشاء واحد أو أكثر من قوالب الاتصالات في مكتبة الاتصالات، يمكن تحديد هذه القوالب لإنشاء إعلام أمين في حالة ما.

لتحديد قالب:

1. في مدخل التوافق، انتقل إلى **eDiscovery > Advanced** لعرض قائمة الحالات في مؤسستك.

2. حدد حالة، وانقر فوق علامة التبويب **"اتصالات"** ، ثم انقر فوق **"اتصال جديد**".

3. في صفحة **"Name communication** "، استخدم القائمة المنسدلة **"Select communication template** " لتحديد قالب اتصالات لاستخدامه لإنشاء إعلام الوصي.

   يتم عرض قائمة القوالب في مكتبة الاتصالات الخاصة بالمؤسسة في القائمة المنسدلة.

   ![يتم عرض القوالب من مكتبة الاتصالات في القائمة المنسدلة.](..\media\AeDCommunicationsTemplates1.png)
