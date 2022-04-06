---
title: الحصول على API (API) الأجهزة ذات الصلة بالمجال
description: تعرف على كيفية استخدام API للحصول على الأجهزة ذات الصلة بالمجال للحصول على الأجهزة التي تتواصل مع مجال أو منه في Microsoft Defender لنقطة النهاية.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، المجال، ذات الصلة، الأجهزة
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
ms.openlocfilehash: 179b3bf9ecd1ff7f7045f386d740eff4e83a12c9
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63583112"
---
# <a name="get-domain-related-machines-api"></a>الحصول على API (API) الأجهزة ذات الصلة بالمجال

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد مجموعة من [الأجهزة](machine.md) التي تم توصيلها إلى عنوان مجال معين أو منه.

## <a name="limitations"></a>القيود

1. يمكنك الاستعلام عن الأجهزة التي تم تحديثها آخر مرة وفقا لفترة الاستبقاء التي تم تكوينها.
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
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (لمزيد من المعلومات، راجع [إنشاء أدوار وإدارتها](user-roles.md)
> - ستتضمن الاستجابة فقط الأجهزة التي يمكن للمستخدم الوصول إليها، استنادا إلى إعدادات مجموعة الأجهزة (لمزيد من المعلومات، راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/domains/{domain}/machines
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح المجال وكان موجودا - 200 موافق [مع قائمة كيانات](machine.md) الجهاز. إذا لم يكن المجال موجودا - 200 موافق مع مجموعة فارغة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/domains/api.securitycenter.microsoft.com/machines
```
