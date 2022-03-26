---
title: الحصول على API للتنبيهات ذات الصلة بالملفات
description: تعرف على كيفية استخدام API للحصول على تنبيهات ذات صلة بالملف للحصول على مجموعة من التنبيهات ذات الصلة بنقطة توقف ملف معين في Microsoft Defender لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، الحصول، ملف، هاش
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
ms.openlocfilehash: b88fc9add77a790c21b3851e3e80f02681308195
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63572360"
---
# <a name="get-file-related-alerts-api"></a>الحصول على API للتنبيهات ذات الصلة بالملفات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد مجموعة من التنبيهات ذات الصلة بhhة ملف معين.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.
2. يتم دعم الدالة SHA-1 Hash (وليس MD5 أو SHA-256).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Defender ل واجهات برمجة التطبيقات في نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Alert.read.All|"قراءة كل التنبيهات"
Application|Alert.ReadWrite.All|"قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة)|Alert.Read|"قراءة التنبيهات"
مفوض (حساب العمل أو المدرسة)|Alert.ReadWrite|"قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - ستتضمن الاستجابة التنبيهات المقترنة بالأجهزة فقط، التي يمكن للمستخدم الوصول إليها، استنادا إلى إعدادات مجموعة الأجهزة (راجع إنشاء مجموعات الأجهزة [](machine-groups.md) وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/files/{id}/alerts
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح الملف وكان موجودا - 200 موافق مع [قائمة كيانات التنبيه](alerts.md) في الجسم. إذا لم يكن الملف موجودا - 200 موافق مع مجموعة فارغة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/files/6532ec91d513acc05f43ee0aa3002599729fd3e1/alerts
```
