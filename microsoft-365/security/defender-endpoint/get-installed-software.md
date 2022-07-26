---
title: الحصول على البرامج المثبتة
description: استرداد مجموعة من البرامج المثبتة المتعلقة بمعرف جهاز معين.
keywords: واجهة برمجة التطبيقات، وواجهة برمجة تطبيقات الرسم البياني، وواجهة برمجة التطبيقات المدعومة، والحصول على، وقائمة، وملف، ومعلومات، ومخزون البرامج، والبرامج المثبتة لكل جهاز، وواجهة برمجة تطبيقات إدارة الثغرات الأمنية & التهديد، وواجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية tvm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 215f1e18b22a0dca1aedcfdbe355e4a65e0b8664
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020088"
---
# <a name="get-installed-software"></a>الحصول على البرامج المثبتة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> هل تريد تجربة إدارة الثغرات الأمنية في Microsoft Defender؟ تعرف على المزيد حول كيفية التسجيل في [الإصدار التجريبي من المعاينة العامة إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/get-defender-vulnerability-management.md).

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

استرداد مجموعة من البرامج المثبتة المتعلقة بمعرف جهاز معين.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
:---|:---|:---
Application |Software.Read.All|'قراءة معلومات برنامج إدارة المخاطر والثغرات الأمنية'
مفوض (حساب العمل أو المؤسسة التعليمية)|Software.Read|'قراءة معلومات برنامج إدارة المخاطر والثغرات الأمنية'

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/{machineId}/software
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا نجحت، ترجع هذه الطريقة 200 موافق مع معلومات البرنامج المثبتة في النص الأساسي.

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/software
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
"@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Software",
"value": [
        {
"id": "microsoft-_-internet_explorer",
"name": "internet_explorer",
"vendor": "microsoft",
"weaknesses": 67,
"publicExploit": true,
"activeAlert": false,
"exposedMachines": 42115,
"impactScore": 46.2037163
        }
    ]
}
```

## <a name="see-also"></a>راجع أيضًا

- [إدارة الثغرات الأمنية & المخاطر المستندة إلى المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [مخزون برامج المخاطر & الثغرات الأمنية](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
