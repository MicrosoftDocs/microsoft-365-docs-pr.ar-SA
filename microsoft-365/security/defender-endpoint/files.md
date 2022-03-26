---
title: نوع مورد الملف
description: استرداد تنبيهات Microsoft Defender الأخيرة لنقطة النهاية ذات الصلة بالملفات.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، التنبيهات، الأخيرة
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
ms.openlocfilehash: 7fef64136e27b8b9a85163fe9e25fdf59ab6d2aa
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570527"
---
# <a name="file-resource-type"></a>نوع مورد الملف

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تمثيل كيان ملف في Defender for Endpoint.

## <a name="methods"></a>الأساليب

الأسلوب|نوع الإرجاع |الوصف
:---|:---|:---
[الحصول على ملف](get-file-information.md) | [ملف](files.md) | الحصول على ملف واحد 
[سرد التنبيهات ذات الصلة بالملفات](get-file-related-alerts.md) | [مجموعة التنبيهات](alerts.md) | احصل [على](alerts.md) كيانات التنبيه المقترنة بالملف.
[سرد الأجهزة ذات الصلة بالملفات](get-file-related-machines.md) | [مجموعة](machine.md) الآلات | احصل [على كيانات](machine.md) الجهاز المقترنة بالتنبيه.
[إحصائيات الملفات](get-file-statistics.md) | ملخص الإحصائيات | استرداد مستوى نقل الملفات للملف المعطى.


## <a name="properties"></a>الخصائص

|الخاصية | النوع | الوصف |
|:---|:---|:---|
|sha1 | سلسلة | هاش 1 لمحتوى الملف |
|sha256 | سلسلة | شارة Sha256 لمحتوى الملف |
|التفوق العام | طويل قابل للبطلان | نقل الملفات عبر المؤسسة |
|globalFirstObserved | DateTimeOffset | أول مرة تم فيها ملاحظة الملف |
|globalLastObserved | DateTimeOffset | آخر مرة تم فيها ملاحظة الملف |
|الحجم | طويل قابل للبطلان | حجم الملف |
|fileType | سلسلة | نوع الملف |
|isPeFile | منطقي | true إذا كان الملف قابلا للتنفيذ قابل للنقل (على سبيل المثال، "DLL" أو "EXE"، إلخ.) |
|filePublisher | سلسلة | ناشر الملفات |
|fileProductName | سلسلة | اسم المنتج |
|توقيع | سلسلة | توقيع الملف |
|مصدر | سلسلة | مصدر الملفات |
|signerHash | سلسلة | هاش شهادة التوقيع |
|isValidCertificate | منطقي | تم توقيع شهادة تم التحقق منها بنجاح من قبل وكيل Microsoft Defender for Endpoint |
|determinationType | سلسلة | نوع التحديد للملف |
|determinationValue | سلسلة | قيمة التحديد |

## <a name="json-representation"></a>تمثيل Json

```json
{
    "sha1": "4388963aaa83afe2042a46a3c017ad50bdcdafb3",
    "sha256": "413c58c8267d2c8648d8f6384bacc2ae9c929b2b96578b6860b5087cd1bd6462",
    "globalPrevalence": 180022,
    "globalFirstObserved": "2017-09-19T03:51:27.6785431Z",
    "globalLastObserved": "2020-01-06T03:59:21.3229314Z",
    "size": 22139496,
    "fileType": "APP",
    "isPeFile": true,
    "filePublisher": "CHENGDU YIWO Tech Development Co., Ltd.",
    "fileProductName": "EaseUS MobiSaver for Android",
    "signer": "CHENGDU YIWO Tech Development Co., Ltd.",
    "issuer": "VeriSign Class 3 Code Signing 2010 CA",
    "signerHash": "6c3245d4a9bc0244d99dff27af259cbbae2e2d16",
    "isValidCertificate": false,
    "determinationType": "Pua",
    "determinationValue": "PUA:Win32/FusionCore"
}
```
