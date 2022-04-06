---
title: ملاحظات إصدار API ل Microsoft Defender لنقطة النهاية
description: ملاحظات الإصدار للتحديثات التي تم إصدارها إلى مجموعة نقاط نهاية Microsoft Defender ل واجهات برمجة التطبيقات.
keywords: ملاحظات إصدار API لنقطة النهاية ل Microsoft Defender، mde، واجهات برمجة التطبيقات، Microsoft Defender ل API نقطة النهاية، التحديثات، الملاحظات، الإصدار
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
ms.openlocfilehash: 2c34add5968021d6a31bffc80ec16e0ebed9baf0
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583044"
---
# <a name="microsoft-defender-for-endpoint-api-release-notes"></a>ملاحظات إصدار API ل Microsoft Defender لنقطة النهاية

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تسرد المعلومات التالية التحديثات التي تم تحديثها ل واجهات برمجة تطبيقات نقطة النهاية ل Microsoft Defender والتواريخ التي تم إصدارها.

> [!TIP]
> موجز RSS: يتم إعلامك عند تحديث هذه الصفحة عن طريق نسخ عنوان URL التالي ولصقه في قارئ الموجز:
>
> ```http
> /api/search/rss?search=%22Release+notes+for+updates+made+to+the+Microsoft+Defender+for+Endpoint+set+of+APIs%22&locale=en-us&facet=&%24filter=scopes%2Fany%28t%3A+t+eq+%27Windows+10%27%29
> ```

## <a name="release-notes---newest-to-oldest-ddmmyyyy"></a>ملاحظات الإصدار - من أحدث إلى أقدم (dd.mm.yyyyy)

### <a name="06102021"></a>06.10.2021

- طريقة API لتقييم التصدير المضافة - تقييم نقاط الضعف في برنامج _تصدير دلتا (استجابة JSON)_ تصدير أساليب التقييم [وخصائصه لكل جهاز](get-assessment-methods-properties.md).

### <a name="05252021"></a>05.25.2021

- إضافة أساليب تقييم جديدة ل API [Export وخصائصها لكل جهاز](get-assessment-methods-properties.md).

### <a name="03052021"></a>03.05.2021

- إضافة API جديدة: [أساليب نشاط الإصلاح وخصائصه](get-remediation-methods-properties.md).

### <a name="10022021"></a>10.02.2021

- إضافة API جديدة: [تنبيهات التحديث الدفعي](batch-update-alerts.md).

### <a name="25012021"></a>25.01.2021

- قيود السعر المحدثة [ل API للصيد المتقدم](run-advanced-query-api.md) من 15 إلى 45 طلبا في الدقيقة.

### <a name="21012021"></a>21.01.2021

- إضافة API جديدة: [البحث عن الأجهزة حسب العلامة](machine-tags.md).
- إضافة API جديدة: [استيراد المؤشرات](import-ti-indicators.md).

### <a name="03012021"></a>03.01.2021

- دليل تنبيه محدث: تم إضافة ***detectionStatus** _, _*_parentProcessFilePath_*_ و_ *_parentProcessFileName_** الخصائص.
- كيان [التنبيه المحدث](alerts.md): ***خاصيةid المضافة التي تم إضافتها*** .

### <a name="15122020"></a>15.12.2020

- كيان [الجهاز المحدث](machine.md) : إضافة ***قائمة IpInterfaces*** . راجع [قائمة الأجهزة](get-machines.md).

### <a name="04112020"></a>04.11.2020

- إضافة API جديدة: [تعيين قيمة الجهاز](set-device-value.md).
- كيان [الجهاز المحدث](machine.md) : ***خاصية deviceValue*** المضافة.

### <a name="01092020"></a>01.09.2020

- الخيار المضاف لتوسيع كيان التنبيه مع الدليل المرتبط به. راجع [تنبيهات القائمة](get-alerts.md).
