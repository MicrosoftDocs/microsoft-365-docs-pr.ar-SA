---
title: الحصول على API للتنبيهات ذات الصلة ب IP
description: استرداد مجموعة من التنبيهات ذات الصلة عنوان IP معين باستخدام Microsoft Defender لنقطة النهاية
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، ip، ذات الصلة، التنبيهات
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
ms.openlocfilehash: b46e67a6fe2d30a4b6480b88ea3a40f842227669
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63572359"
---
# <a name="get-ip-related-alerts-api"></a>الحصول على API للتنبيهات ذات الصلة ب IP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API
استرداد مجموعة من التنبيهات ذات الصلة عنوان IP معين.


## <a name="limitations"></a>القيود
1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.


## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Defender ل واجهات برمجة التطبيقات في نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Alert.read.All|"قراءة كل التنبيهات"
Application|Alert.ReadWrite.All|"قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة) | Alert.Read | "قراءة التنبيهات"
مفوض (حساب العمل أو المدرسة) | Alert.ReadWrite | "قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - ستتضمن الاستجابة التنبيهات المقترنة بالأجهزة فقط، التي يمكن للمستخدم الوصول إليها، استنادا إلى إعدادات مجموعة الأجهزة (راجع إنشاء مجموعات الأجهزة [](machine-groups.md) وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/ips/{ip}/alerts
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح الأمر وكان IP موجودا - 200 موافق مع [قائمة كيانات التنبيه](alerts.md) في الجسم. إذا كان عنوان IP غير معروف ولكنه صالح، فإنه سيرجع مجموعة فارغة.
إذا كان عنوان IP غير صالح، فإنه سيرجع HTTP 400.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/ips/10.209.67.177/alerts
```
