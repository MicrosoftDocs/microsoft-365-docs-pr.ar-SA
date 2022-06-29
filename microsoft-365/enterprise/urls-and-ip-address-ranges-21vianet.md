---
title: عناوين URL ونطاقات عناوين IP Office 365 المشغلة بواسطة 21Vianet
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/01/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
ms.custom: seo-marvel-apr2020
f1.keywords:
- NOCSH
description: تسرد هذه المقالة نطاقات عناوين URL وعناوين IP Office 365 عند تشغيلها بواسطة 21Vianet في الصين.
hideEdit: true
ms.openlocfilehash: e99a89e511faef069f0856e046ea1898e896b3c1
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489892"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>عناوين URL ونطاقات عناوين IP Office 365 المشغلة بواسطة 21Vianet

 *ينطبق على: Office 365 المشغلة بواسطة 21Vianet - مسؤول Small Business، Office 365 المشغلة بواسطة 21Vianet - مسؤول*

**ملخص**: تنطبق نقاط النهاية التالية (FQDNs والمنافذ وعناوين URL وIPv4 وIPv6 على Office 365 المشغلة بواسطة 21 Vianet وهي مصممة لتقديم خدمات الإنتاجية للمؤسسات باستخدام هذه الخطط فقط.
  
 **Office 365 نقاط النهاية:** Office 365 جميع [أنحاء العالم (بما في ذلك GCC)](urls-and-ip-address-ranges.md)  |  *المشغلة بواسطة 21 Vianet* |  [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) |  [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |
  
**تاريخ التحديث الأخير:** 06/01/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [اشتراك في سجلّ التغييرات](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

**التنزيل:** كل الوجهات المطلوبة والاختيارية في قائمة [تنسيق JSON](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) واحدة.

ابدأ ب [إدارة نقاط نهاية Office 365](managing-office-365-endpoints.md) لفهم توصياتنا لإدارة اتصال الشبكة باستخدام هذه البيانات. يتم تحديث بيانات نقاط النهاية كما تقتضي الحاجة في بداية كل شهر باستخدام عناوين IP وعناوين URL الجديدة المنشورة قبل 30 يوما من تنشيطها. يسمح هذا للعملاء الذين ليس لديهم تحديثات تلقائية حتى الآن بإكمال عملياتهم قبل أن يكون الاتصال الجديد مطلوبا. قد يتم أيضا تحديث نقاط النهاية خلال الشهر إذا لزم الأمر لمعالجة تصعيد الدعم أو أحداث الأمان أو المتطلبات التشغيلية الفورية الأخرى. يتم إنشاء كافة البيانات المعروضة في هذه الصفحة أدناه من خدمات ويب المستندة إلى REST. إذا كنت تستخدم برنامج نصي أو جهاز شبكة للوصول إلى هذه البيانات، فيجب الانتقال إلى [خدمة ويب](microsoft-365-ip-web-service.md) مباشرة.

تسرد بيانات نقطة النهاية أدناه متطلبات الاتصال من جهاز المستخدم إلى Office 365. ولا يتضمن اتصالات الشبكة من Microsoft إلى شبكة عملاء، تسمى أحيانا اتصالات الشبكة المختلطة أو الواردة.

يتم تجميع نقاط النهاية في أربع مناطق خدمة. يمكن تحديد مناطق الخدمة الثلاث الأولى بشكل مستقل للاتصال. منطقة الخدمة الرابعة هي تبعية شائعة (تسمى Microsoft 365 Common وOffice) ويجب أن يكون لديها دائما اتصال بالشبكة.

أعمدة البيانات المعروضة هي:

- **معرف**: رقم معرف الصف، المعروف أيضا بمجموعة نقاط النهاية. هذا المعرف هو نفسه الذي يتم إرجاعه بواسطة خدمة ويب لمجموعة نقاط النهاية.

- **الفئة**: توضح ما إذا كانت مجموعة نقاط النهاية مصنفة على أنها "تحسين" أو "السماح" أو "افتراضي". يمكنك القراءة حول هذه الفئات وإرشادات إدارتها في [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). يسرد هذا العمود أيضا مجموعات نقاط النهاية المطلوبة للاتصال بالشبكة. بالنسبة لمجموعات نقاط النهاية غير المطلوبة للاتصال بالشبكة، نوفر ملاحظات في هذا الحقل للإشارة إلى الوظائف التي قد تكون مفقودة إذا تم حظر مجموعة نقاط النهاية. إذا كنت تقوم باستبعاد منطقة خدمة بأكملها، فإن مجموعات نقاط النهاية المدرجة كمطلوبة لا تتطلب الاتصال.

- **ER** : هذا **نعم** إذا كانت مجموعة نقاط النهاية مدعومة عبر Azure ExpressRoute مع بادئات مسار Office 365. يتوافق مجتمع BGP الذي يتضمن بادئات المسار المعروضة مع منطقة الخدمة المدرجة. عندما تكون ER **لا**، فهذا يعني أن ExpressRoute غير معتمد لمجموعة نقاط النهاية هذه. ومع ذلك، لا يجب افتراض أنه لم يتم الإعلان عن مسارات لمجموعة نقاط نهاية حيث يكون ER **لا**.

- **عناوين**: تسرد أسماء مجالات FQDN أو أحرف البدل ونطاقات عناوين IP لمجموعة نقاط النهاية. لاحظ أن نطاق عنوان IP يكون بتنسيق CIDR وقد يتضمن العديد من عناوين IP الفردية في الشبكة المحددة.
 
- **المنافذ**: يسرد منافذ TCP أو UDP التي تم دمجها مع العناوين لتكوين نقطة نهاية الشبكة. قد تلاحظ وجود بعض التكرارات في نطاقات عناوين IP حيث توجد منافذ مختلفة مدرجة.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]