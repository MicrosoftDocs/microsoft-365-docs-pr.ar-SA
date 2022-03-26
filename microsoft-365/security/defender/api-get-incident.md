---
title: الحصول على API للحادث
description: تعرف على كيفية استخدام API للحصول على أحداث للحصول على حادث واحد في Microsoft 365 Defender.
keywords: apis، api للرسم البياني، apis المعتمدة، الحصول، ملف، هاش
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 8861dc3752d2c4cc798bc83475f6a51f8245191a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575548"
---
# <a name="get-incident-information-api"></a>الحصول على معلومات حول الحادث API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد حادث معين بواسطة المرجع الخاص به

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه.

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Incident.read.All|"قراءة كل الأحداث"
Application|Incident.ReadWrite.All|"قراءة كل الأحداث وكتابتها"
مفوض (حساب العمل أو المدرسة)|Incident.Read|"أحداث القراءة"
مفوض (حساب العمل أو المدرسة)|Incident.ReadWrite|"أحداث القراءة والكتابة"

> [!NOTE]
>
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات"
> - ستتضمن الاستجابة فقط الأحداث التي يتم عرض المستخدم لها

## <a name="http-request"></a>طلب HTTP

```console
GET .../api/incidents/{id}
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
---|---|---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجحت هذه الطريقة، ترجع هذه الطريقة 200 موافق، وترجع كيان الحادث في هيئة الاستجابة.
إذا لم يتم العثور على أي حادث بالمحدد - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.security.microsoft.com/api/incidents/{id}
```
