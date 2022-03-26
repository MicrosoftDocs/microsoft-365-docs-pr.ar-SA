---
title: إنشاء تنبيه من API للحدث
description: تعرف على كيفية استخدام API لإنشاء تنبيه لإنشاء تنبيه جديد أعلى الحدث في Microsoft Defender لنقطة النهاية.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، التنبيه، المعلومات، الم id
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
ms.openlocfilehash: cc28ea9082e7afbb6f623e325a48119de393f075
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63573257"
---
# <a name="create-alert-api"></a>إنشاء API تنبيه

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>وصف API

إنشاء تنبيه [جديد](alerts.md) في أعلى **الحدث**.

- **إن حدث Microsoft Defender ل Endpoint مطلوب** لإنشاء التنبيه.
- تحتاج إلى توفير ثلاث معلمات من الحدث في **الطلب: وقت** الحدث ومحدد **الجهاز** **ومحدد التقرير**. راجع المثال أدناه.
- يمكنك استخدام حدث تم العثور عليه في API أو مدخل للصيد المتقدم.
- إذا كان هناك تنبيه مفتوح موجود على الجهاز نفسه بنفس العنوان، سيتم دمج التنبيه الجديد الذي تم إنشاؤه معه.
- يبدأ التحقيق التلقائي تلقائيا في التنبيهات التي يتم إنشاؤها عبر API.

## <a name="limitations"></a>القيود

1. حدود السعر ل API هذه هي 15 مكالمة في الدقيقة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن | الإذن | اسم عرض الأذونات
:---|:---|:---
Application | Alert.ReadWrite.All | "قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة) | Alert.ReadWrite | "قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "التحقيق في التنبيهات" (لمزيد من المعلومات، راجع [إنشاء أدوار وإدارتها](user-roles.md) )
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة (لمزيد من المعلومات، راجع إنشاء [مجموعات الأجهزة وإدارتها](machine-groups.md)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.
نوع المحتوى | سلسلة | application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، اعرض القيم التالية (الكل مطلوب):

الخاصية | النوع | الوصف
:---|:---|:---
eventTime | DateTime(UTC) | الوقت الدقيق للحدث كسلسلة، كما تم الحصول عليه من الصيد المتقدم. على سبيل المثال،  ```2018-08-03T16:45:21.7115183Z``` **مطلوب**.
reportId | سلسلة | تقرير عن الحدث، كما تم الحصول عليه من عملية البحث المتقدمة. **مطلوب**.
machineId | سلسلة | معرف الجهاز الذي تم التعرف على الحدث عليه. **مطلوب**.
الخطورة | سلسلة | خطورة التنبيه. قيم الخاصية هي: "منخفض" و"متوسط" و"عال". **مطلوب**.
العنوان | سلسلة | عنوان التنبيه. **مطلوب**.
الوصف | سلسلة | وصف التنبيه. **مطلوب**.
recommendedAction| سلسلة | يجب على مسؤول الأمن اتخاذ هذا الإجراء عند تحليل التنبيه. **مطلوب**.
الفئة| سلسلة | فئة التنبيه. قيم الخاصية هي: "عام"، "CommandAndControl"، "Collection"، "CredentialAccess"، "DefenseEvasion"، "Discovery"، "Exfiltration"، "Exploit"، "Execution"، "InitialAccesss"، "LateralMovement"، "Malware"، "persistence"، "PrivilegeEscalation"، "Ransomware"، "SuspiciousActivity" **مطلوبة**.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق، بالإضافة إلى كائن [تنبيه](alerts.md) جديد في هيئة الاستجابة. إذا لم يتم العثور على حدث بالخصائص المحددة (_reportId_ و _eventTime_ و _machineId_) - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

```json
{
    "machineId": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "severity": "Low",
    "title": "example",
    "description": "example alert",
    "recommendedAction": "nothing",
    "eventTime": "2018-08-03T16:45:21.7115183Z",
    "reportId": "20776",
    "category": "Exploit"
}
```
