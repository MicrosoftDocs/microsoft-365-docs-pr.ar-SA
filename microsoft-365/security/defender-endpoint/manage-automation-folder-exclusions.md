---
title: إدارة استثناءات مجلدات التنفيذ التلقائي
description: أضف استثناءات مجلدات التنفيذ التلقائي للتحكم في الملفات التي يتم استبعادها من التحقيق التلقائي.
keywords: الإدارة والأتمتة والاستبعاد والحظر والتنظيف والضارة
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
ms.technology: mde
ms.openlocfilehash: 54c0f7f67b62216eae4264c8e7a55c0e34c82fb0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63569836"
---
# <a name="manage-automation-folder-exclusions"></a>إدارة استثناءات مجلدات التنفيذ التلقائي

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationexclusionfolder-abovefoldlink)

تسمح لك استثناءات مجلدات التنفيذ التلقائي بتحديد المجلدات التي سيتخطىها التحقيق التلقائي.

يمكنك التحكم في السمات التالية حول المجلد الذي تريد تخطيه:

- **المجلدات**: يمكنك تحديد مجلد ومجلداته الفرعية التي يجب تخطيها.

  > [!NOTE]
  > في هذا الوقت، لا يتم دعم استخدام البطاقات البرية كطريقة لاستبعاد الملفات الموجودة ضمن الدليل.

- **ملحقات الملفات**: يمكنك تحديد الملحقات التي يجب استبعادها في دليل معين. الملحقات هي طريقة لمنع مهاجم من استخدام مجلد مستبعد لإخفاء استغلال. تحدد الملحقات بشكل صريح الملفات التي يجب تجاهلها.

- **أسماء الملفات**: يمكنك تحديد أسماء الملفات التي تريد استبعادها في دليل معين. الأسماء هي طريقة لمنع مهاجم من استخدام مجلد مستبعد لإخفاء استغلال. تحدد الأسماء بوضوح الملفات التي يجب تجاهلها.

## <a name="add-an-automation-folder-exclusion"></a>إضافة استثناء مجلد تلقائي

1. في جزء التنقل **، حدد الإعدادات** \> **"التنفيذ** \>  \> التلقائي لقواعد نقاط **النهاية**".

2. انقر **فوق استثناء مجلد جديد**.

3. أدخل تفاصيل المجلد:

    - المجلد
    - الملحقات
    - أسماء الملفات
    - الوصف

4. انقر فوق **حفظ**.

> [!NOTE]
> ستفشل أوامر الاستجابة المباشرة لتجميع الملفات المستبعدة أو فحصها باستخدام الخطأ: "تم استبعاد الملف". بالإضافة إلى ذلك، ستتجاهل عمليات البحث التلقائية العناصر المستبعدة.

## <a name="edit-an-automation-folder-exclusion"></a>تحرير استثناء مجلد التنفيذ التلقائي

1. في جزء التنقل **، حدد الإعدادات** \> **"التنفيذ** \>  \> التلقائي لقواعد نقاط **النهاية**".
2. انقر **فوق** تحرير على استثناء المجلد.
3. قم بتحديث تفاصيل القاعدة وانقر فوق **حفظ**.

## <a name="remove-an-automation-folder-exclusion"></a>إزالة استثناء مجلد التنفيذ التلقائي

1. في جزء التنقل **، حدد الإعدادات** \> **"التنفيذ** \>  \> التلقائي لقواعد نقاط **النهاية**".
2. انقر **فوق إزالة الاستثناء**.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة القوائم المسموح بها/المحظورة الخاصة بالأتمتة](manage-indicators.md)
- [إدارة عمليات تحميل الملفات التلقائية](manage-automation-file-uploads.md)
