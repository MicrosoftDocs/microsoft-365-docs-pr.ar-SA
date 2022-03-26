---
title: الحصول على API للتنبيهات ذات الصلة بالمستخدم
description: استرداد مجموعة من التنبيهات ذات الصلة بمحدد مستخدم معين باستخدام Microsoft Defender لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، الحصول، المستخدم، ذات الصلة، التنبيهات
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
ms.openlocfilehash: 11811996ef369c7850030871abdb6a5082546de8
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63575789"
---
# <a name="get-user-related-alerts-api"></a>الحصول على API للتنبيهات ذات الصلة بالمستخدم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد مجموعة من التنبيهات ذات الصلة بمرجع مستخدم معين.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Alert.read.All|"قراءة كل التنبيهات"
Application|Alert.ReadWrite.All|"قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة) | Alert.Read | "قراءة التنبيهات"
مفوض (حساب العمل أو المدرسة) | Alert.ReadWrite | "قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات". لمزيد من المعلومات، راجع [إنشاء أدوار وإدارتها](user-roles.md).
> - ستتضمن الاستجابة التنبيهات المقترنة بالأجهزة فقط، التي يمكن للمستخدم الوصول إليها، استنادا إلى إعدادات مجموعة الأجهزة (راجع إنشاء مجموعات الأجهزة [](machine-groups.md) وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/users/{id}/alerts
```

**لا يكون الم ID هو UPN الكامل، ولكنه اسم المستخدم فقط. (على سبيل المثال، لاسترداد تنبيهات user1@contoso.com /api/users/user1/alerts)**

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح و كان المستخدم موجودا - 200 موافق. إذا لم يكن المستخدم موجودا - 200 موافق مع مجموعة فارغة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/users/user1/alerts
```
