---
title: الحصول على KBs مفقود بواسطة معرف الجهاز
description: استرداد تحديثات الأمان المفقودة حسب معرف الجهاز
keywords: واجهة برمجة التطبيقات، وواجهة برمجة تطبيقات الرسم البياني، وواجهة برمجة التطبيقات المدعومة، والحصول على، وقائمة، وملف، ومعلومات، ومعرف الجهاز، وواجهة برمجة تطبيقات إدارة الثغرات الأمنية & التهديد، وواجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية tvm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 2d8200d93b3cab7acff237113a2c98d8571be1a7
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020110"
---
# <a name="get-missing-kbs-by-device-id"></a>الحصول على KBs مفقود بواسطة معرف الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> هل تريد تجربة إدارة الثغرات الأمنية في Microsoft Defender؟ تعرف على المزيد حول كيفية التسجيل في [الإصدار التجريبي من المعاينة العامة إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/get-defender-vulnerability-management.md).

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد كيلوبايت (تحديثات الأمان) المفقودة حسب معرف الجهاز

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/{machineId}/getmissingkbs
```
## <a name="permissions"></a>الأذونات

الإذن التالي مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md).

نوع الإذن | اذن | اسم عرض الإذن
:---|:---|:---
Application | Software.Read.All | 'قراءة معلومات برنامج إدارة المخاطر والثغرات الأمنية'

## <a name="request-header"></a>عنوان الطلب

الاسم|نوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا نجحت، يرجع هذا الأسلوب 200 OK، مع فقدان بيانات kb للجهاز المحدد في النص الأساسي.

## <a name="example"></a>المثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines/2339ad14a01bd0299afb93dfa2550136057bff96/getmissingkbs 
```

### <a name="response"></a>استجابه

فيما يلي مثال على الاستجابة.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicProductFixDto)",
    "value": [
        {
            "id": "4540673",
            "name": "March 2020 Security Updates",
            "productsNames": [
                "windows_10",
                "edge",
                "internet_explorer"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 1,
            "cveAddressed": 97
        }
        ]
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة الثغرات الأمنية & المخاطر المستندة إلى المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [مخزون برامج المخاطر & الثغرات الأمنية](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
