---
title: نوع مورد الجهاز
description: تعرف على أساليب وخصائص نوع مورد الجهاز في Microsoft Defender لنقطة النهاية.
keywords: apis، apis المعتمدة، الحصول، الأجهزة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 80ac3e9ed43de98d32fd14063261452cfd5b1372
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573409"
---
# <a name="machine-resource-type"></a>نوع مورد الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>الأساليب

<br>

****

|الأسلوب|نوع الإرجاع|الوصف|
|---|---|---|
|[أجهزة القائمة](get-machines.md)|[مجموعة](machine.md) الآلات|مجموعة قائمة [بكيانات](machine.md) الجهاز في المؤسسة.|
|[الحصول على جهاز](get-machine-by-id.md)|[جهاز](machine.md)|احصل [على جهاز](machine.md) من خلال هويته.|
|[الحصول على المستخدمين المسجلين](get-machine-log-on-users.md)|[مجموعة](user.md) المستخدمين|احصل على مجموعة [المستخدم](user.md) الذي سجل دخوله إلى [الجهاز](machine.md).|
|[الحصول على تنبيهات ذات صلة](get-machine-related-alerts.md)|[مجموعة التنبيهات](alerts.md)|احصل [على مجموعة كيانات](alerts.md) التنبيه التي تم رفعها على [الجهاز](machine.md).|
|[الحصول على البرامج المثبتة](get-installed-software.md)|[مجموعة برامج](software.md)|استرداد مجموعة من البرامج المثبتة ذات الصلة بمرجع جهاز معين.|
|[الحصول على نقاط الضعف المكتشفة](get-discovered-vulnerabilities.md)|[مجموعة نقاط الضعف](vulnerability.md)|استرداد مجموعة من نقاط الضعف المكتشفة ذات الصلة بمرجع جهاز معين.|
|[الحصول على توصيات الأمان](get-security-recommendations.md)|[مجموعة التوصيات](recommendation.md)|استرداد مجموعة من توصيات الأمان ذات الصلة بمرجع جهاز معين.|
|[إضافة علامات الجهاز أو إزالتها](add-or-remove-machine-tags.md)|[جهاز](machine.md)|إضافة علامة أو إزالتها إلى جهاز معين.|
|[البحث عن الأجهزة حسب IP](find-machines-by-ip.md)|[مجموعة](machine.md) الآلات|ابحث عن الأجهزة التي يتم تعثر عليها باستخدام IP.|
|[البحث عن الأجهزة حسب العلامة](find-machines-by-tag.md)|[مجموعة](machine.md) الآلات|البحث عن الأجهزة حسب [العلامة](machine-tags.md).|
|[فقدان KBs](get-missing-kbs-machine.md)|مجموعة KB|الحصول على قائمة بمكاتب KBs المفقودة المقترنة بم ID الجهاز|
|[تعيين قيمة الجهاز](set-device-value.md)|[مجموعة](machine.md) الآلات|تعيين [قيمة جهاز](tvm-assign-device-value.md).|
|[تحديث الجهاز](update-machine-method.md)|[مجموعة](machine.md) الآلات|الحصول على حالة تحديث جهاز.|
|

## <a name="properties"></a>الخصائص

<br>

****

|الخاصية|النوع|الوصف|
|---|---|---|
|الم id|سلسلة|[هوية](machine.md) الجهاز.|
|computerDnsName|سلسلة|[اسم](machine.md) مؤهل بالكامل للجهاز.|
|firstSeen|DateTimeOffset|التاريخ والوقت الأول حيث لاحظ Microsoft [](machine.md) Defender لنقطة النهاية الجهاز.|
|lastSeen|DateTimeOffset|وقت وتاريخ آخر تقرير تم استلامه باستخدام الجهاز الكامل. يرسل الجهاز عادة تقريرا كاملا كل 24 ساعة.|
|osPlatform|سلسلة|النظام الأساسي لنظام التشغيل.|
|onboardingstatus|سلسلة|حالة تشغيل الجهاز. القيم المحتملة هي: "تم الboarded" و"offboarded".|
|osProcessor|سلسلة|معالج نظام التشغيل. استخدم خاصية osArchitecture بدلا من ذلك.|
|الإصدار|سلسلة|إصدار نظام التشغيل.|
|osBuild|طويل قابل للبطلان|رقم إنشاء نظام التشغيل.|
|lastIpAddress|سلسلة|IP الأخير على NIC المحلي على [الجهاز](machine.md).|
|lastExternalIpAddress|سلسلة|IP الأخير الذي [يمكن للجهاز](machine.md) من خلاله الوصول إلى الإنترنت.|
|healthStatus|تعداد|[حالة](machine.md) صحة الجهاز. القيم المحتملة هي: "نشط" و"غير نشط" و"ضعيف الاتصالات" و"NoSensorData" و"NoSensorDataImpairedCommunication" و"غير معروف".|
|rbacGroupName|سلسلة|اسم مجموعة الجهاز.|
|rbacGroupId|سلسلة|"معرّف مجموعة الجهاز".|
|riskScore|تعداد قابل للبطلان|درجة المخاطر كما تم تقييمها بواسطة Microsoft Defender لنقطة النهاية. القيم المحتملة هي: "بلا" و"معلوماتي" و"منخفض" و"متوسط" و"عال".|
|aadDeviceId|Guid لتمثيل قابل للبطلان|AAD (دليل Azure النشط) الجهاز (عندما [يكون الجهاز](machine.md) AAD (دليل Azure النشط) منضما).|
|machineTags|مجموعة سلاسل|مجموعة من [علامات](machine.md) الجهاز.|
|exposureLevel|تعداد قابل للبطلان|مستوى التعرض للضوء كما تم تقييمه بواسطة Microsoft Defender لنقطة النهاية. القيم المحتملة هي: "بلا" و"منخفض" و"متوسط" و"عال".|
|deviceValue|تعداد قابل للبطلان|قيمة [الجهاز](tvm-assign-device-value.md). القيم المحتملة هي: "عادي" و"منخفض" و"عال".|
|ipAddresses|مجموعة IpAddress|مجموعة من ***كائنات IpAddress*** . راجع [الحصول على API (API) للآلات](get-machines.md).|
|osArchitecture|سلسلة|بنية نظام التشغيل. القيم المحتملة هي: "32 بت" و"64 بت". استخدم هذه الخاصية بدلا من osProcessor.|
|
