---
title: تحديد مجموعات تعريف إضافية لفحص حركة مرور الشبكة برنامج الحماية من الفيروسات من Microsoft Defender
description: حدد مجموعات تعريف إضافية لفحص حركة مرور الشبكة برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، defender، فحص حركة مرور الشبكة
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 05/07/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: f7b940604272035dc37b170eb759fa0ec45582b6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63579594"
---
# <a name="specify-additional-definition-sets-for-network-traffic-inspection"></a>تحديد مجموعات تعريف إضافية لفحص حركة مرور الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

يمكنك تحديد مجموعات تعريف إضافية لفحص حركة مرور الشبكة باستخدام "نهج المجموعة".

## <a name="use-group-policy-to-specify-additional-definition-sets-for-network-traffic-inspection"></a>استخدام "نهج المجموعة" لتحديد مجموعات تعريف إضافية لفحص حركة مرور الشبكة

1. في نقطة نهاية إدارة نهج المجموعة، افتح وحدة [التحكم في إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انتقل إلى **Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **فحص الشبكة**.

3. حدد **تحديد مجموعات تعريف إضافية لفحص حركة مرور الشبكة**. بشكل افتراضي، يتم تعيين هذا النهج إلى **لم يتم تكوينه**.

4. لتحرير النهج، حدد **ارتباط إعداد نهج** التحرير.

5. حدد **تمكين**، ثم في المقطع **خيارات** ، حدد **إظهار...**.

6. أضف إدخالات إلى القائمة، ثم حدد **موافق**.

   يجب إدراج كل إدخال كزوج قيمة اسم، حيث يكون الاسم تمثيل سلسلة من مجموعة تعريف GUID. على سبيل المثال، يتم تعريف مجموعة التعريف GUID لتمكين اختبار معلومات الأمان كما يلي: `{b54b6ac9-a737-498e-9120-6616ad3bf590}`. لا يتم استخدام القيمة، لذلك نوصي بإعدادها إلى `0`.

7. حدد **موافق**، ثم انتشر كائن نهج المجموعة المحدث. راجع [وحدة تحكم إدارة نهج المجموعة](/windows/win32/srvnodes/group-policy).

> [!TIP]
> هل تستخدم "كائنات نهج المجموعة" في الموقع؟ تعرف على كيفية ترجمتها في السحابة. [قم بتحليل كائنات نهج المجموعة](/mem/intune/configuration/group-policy-analytics) في الموقع باستخدام تحليلات نهج المجموعة في إدارة نقاط النهاية من Microsoft - معاينة.

## <a name="related-articles"></a>المقالات ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [تمكين الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)
- [كيفية إنشاء سياسات الحماية من البرامج الضارة ونشرها: خدمة الحماية من السحابة](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)