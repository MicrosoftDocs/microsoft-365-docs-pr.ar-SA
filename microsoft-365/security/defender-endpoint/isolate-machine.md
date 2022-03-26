---
title: API للجهاز "عزل"
description: تعرف على كيفية استخدام API لجهاز عزل لعزل جهاز من الوصول إلى شبكة خارجية في Microsoft Defender ل Endpoint.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، جهاز معزول
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
ms.openlocfilehash: 52063135280d9e91ca531546b4ae03cf5b42ccbf
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63575798"
---
# <a name="isolate-machine-api"></a>API للجهاز "عزل"

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

عزل جهاز من الوصول إلى شبكة خارجية.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - يتوفر عزل كامل للأجهزة Windows 10 والإصدار 1703 وعلى Windows 11.
> - يتوفر عزل انتقائي للأجهزة Windows 10 والإصدار 1709 أو الإصدارات الأحدث وعلى Windows 11.
> - عند عزل جهاز، يتم السماح ببعض العمليات والوجهات فقط. وبالتالي، لن تتمكن الأجهزة التي تقف خلف خدمة VPN كاملة من الوصول إلى خدمة سحابة Microsoft Defender for Endpoint بعد عزل الجهاز. نوصي باستخدام VPN مقسم للانقسام ل Microsoft Defender لنقطة النهاية برنامج الحماية من الفيروسات من Microsoft Defender البيانات ذات الصلة بالحماية المستندة إلى السحابة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.Isolate|'جهاز عزل'
مفوض (حساب العمل أو المدرسة)|Machine.Isolate|'جهاز عزل'

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "إجراءات المعالجة النشطة" (راجع إنشاء أدوار وإدارتها [للحصول على](user-roles.md) مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/isolate
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
تعليق|سلسلة|التعليق على إقران الإجراء. **مطلوب**.
IsolationType|سلسلة|نوع العزل. القيم المسموح بها هي: "كامل" أو "انتقائي".

**يتحكم IsolationType** في نوع العزل الذي يجب القيام به ويمكن أن يكون واحدا من ما يلي:

- كامل: عزل كامل
- انتقائي: تقييد مجموعة محدودة فقط من التطبيقات من الوصول إلى الشبكة (راجع عزل [الأجهزة من](respond-machine-alerts.md#isolate-devices-from-the-network) الشبكة للحصول على مزيد من التفاصيل)

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 201 - رمز الاستجابة الذي تم إنشاؤه و"إجراء [الجهاز](machineaction.md) " في هيئة الاستجابة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/isolate
```

```json
{
  "Comment": "Isolate machine due to alert 1234",
  "IsolationType": "Full" 
}
```

- حرر جهازا من عزله، راجع [تحرير الجهاز من عزله](unisolate-machine.md).
