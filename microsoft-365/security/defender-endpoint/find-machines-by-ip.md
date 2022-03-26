---
title: البحث عن الأجهزة حسب API الداخلي
description: البحث عن الأجهزة التي يتم تعثر عليها باستخدام IP الداخلي المطلوب في النطاق الزمني الذي يتراوح بين 15 دقيقة قبل وقت معين وبعده
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، الجهاز، IP، البحث عن الجهاز، البحث عن الجهاز، حسب ip، ip
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
ms.openlocfilehash: 702626d3e147bdd02c4988ffabbd158a44f911c7
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570461"
---
# <a name="find-devices-by-internal-ip-api"></a>البحث عن الأجهزة حسب API الداخلي

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

ابحث [عن الأجهزة](machine.md) التي تم تعثر عليها باستخدام IP الداخلي المطلوب في النطاق الزمني الذي يتراوح بين 15 دقيقة قبل وقت معين وبعده.

## <a name="limitations"></a>القيود

1. يجب أن يكون الوقت المحدد في آخر 30 يوما.
2. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.Read.All|"قراءة كل ملفات تعريف الجهاز"
Application|Machine.ReadWrite.All|"قراءة كل معلومات الجهاز وكتابتها"
مفوض (حساب العمل أو المدرسة)|Machine.Read|"قراءة معلومات الجهاز"
مفوض (حساب العمل أو المدرسة)|Machine.ReadWrite|"قراءة معلومات الجهاز وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - ستتضمن الاستجابة فقط الأجهزة التي يمكن للمستخدم الوصول إليها استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - ستتضمن الاستجابة فقط الأجهزة التي يمكن للمستخدم الوصول إليها استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/findbyip(ip='{IP}',timestamp={TimeStamp})
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح - 200 موافق مع قائمة الأجهزة في جزء الاستجابة.
إذا لم يكن الوقت في آخر 30 يوما - 400 طلب غير جيد.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines/findbyip(ip='10.248.240.38',timestamp=2019-09-22T08:44:05Z)
```
