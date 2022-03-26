---
title: إضافة API علامات الجهاز أو إزالتها
description: تعرف على كيفية استخدام API لإضافة علامات الجهاز أو إزالتها لإضافة علامة إلى جهاز أو إزالتها في Microsoft Defender لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، العلامات، علامات الجهاز
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
ms.openlocfilehash: 2ec34011d00e77c5e32f58567a0b705cf7c0dc1c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570489"
---
# <a name="add-or-remove-machine-tags-api"></a>إضافة API علامات الجهاز أو إزالتها

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1 ](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2 ](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

إضافة علامة أو إزالتها إلى جهاز [معين](machine.md).

## <a name="limitations"></a>القيود

1. يمكنك النشر على الأجهزة التي رأيتها آخر مرة وفقا لفترة الاستبقاء التي تم تكوينها.

2. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Defender ل واجهات برمجة التطبيقات في نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.ReadWrite.All|"قراءة كل معلومات الجهاز وكتابتها"
مفوض (حساب العمل أو المدرسة)|Machine.ReadWrite|"قراءة معلومات الجهاز وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "إدارة إعداد الأمان". للحصول على مزيد من المعلومات (راجع [إنشاء أدوار وإدارتها](user-roles.md) )
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الجهاز (راجع [إنشاء مجموعات](machine-groups.md) الجهاز وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/tags
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة|النوع|الوصف
:---|:---|:---
القيمة|سلسلة|اسم العلامة. **مطلوب**.
الإجراء|تعداد|إضافة أو إزالة. القيم المسموح بها هي: "إضافة" أو "إزالة". **مطلوب**.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 - رمز استجابة موافق والآلة المحدثة في هيئة الاستجابة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال لطلب يضيف علامة الجهاز.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/tags
```

```json
{
  "Value" : "test Tag 2",
  "Action": "Add"
}
```

- لإزالة علامة الجهاز، قم بتعيين الإجراء إلى "إزالة" بدلا من "إضافة" في جزء الطلب.
