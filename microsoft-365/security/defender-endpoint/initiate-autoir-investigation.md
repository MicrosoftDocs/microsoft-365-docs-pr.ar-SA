---
title: بدء تشغيل API "التحقيق"
description: استخدم API هذه لبدء التحقيق على جهاز.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، التحقيق
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
ms.openlocfilehash: efffd6bdb0ab6db5b17a8d6beab09a0d84f5ff6c
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63572288"
---
# <a name="start-investigation-api"></a>بدء تشغيل API "التحقيق"

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

ابدأ التحقيق التلقائي على جهاز.

لمزيد من المعلومات، راجع [نظرة عامة حول عمليات البحث](automated-investigations.md) التلقائية.

## <a name="limitations"></a>القيود

1. حدود السعر ل API هذه هي 50 مكالمة في الساعة.

## <a name="requirements-for-air"></a>متطلبات AIR

يجب أن يكون لدى مؤسستك Defender for Endpoint (راجع [الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية](minimum-requirements.md).

حاليا، تدعم AIR إصدارات نظام التشغيل التالية فقط:

- Windows Server 2019
- Windows Server 2022
- Windows 10، الإصدار 1709 (إصدار نظام التشغيل 16299.1085 مع [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) أو إصدار أحدث
- Windows 10، الإصدار 1803 (إصدار نظام التشغيل 17134.704 مع [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) أو إصدار أحدث
- Windows 10 الإصدار [1803 أو](/windows/release-information/status-windows-10-1809-and-windows-server-2019) الإصدارات الأحدث
- Windows 11

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Alert.ReadWrite.All|"قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة)|Alert.ReadWrite|"قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "إجراءات المعالجة النشطة" (راجع إنشاء أدوار وإدارتها [للحصول على](user-roles.md) مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.security.microsoft.com/api/machines/{id}/startInvestigation
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

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 201 - التعليمات البرمجية للاستجابة التي تم إنشاؤها والتحري [في هيئة](investigation.md) الاستجابة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```https
POST https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/startInvestigation
```

```json
{
  "Comment": "Test investigation"
}
```
