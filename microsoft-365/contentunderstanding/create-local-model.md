---
title: إنشاء نموذج على موقع SharePoint محلي باستخدام Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: تعرف على كيفية إنشاء نموذج محلي على موقع SharePoint محلي باستخدام SharePoint Syntex.
ms.openlocfilehash: bcd3f1f086af3982cb4a3ecc5fe754cf82f09a70
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535371"
---
# <a name="create-a-model-on-a-local-sharepoint-site-with-microsoft-sharepoint-syntex"></a>إنشاء نموذج على موقع SharePoint محلي باستخدام Microsoft SharePoint Syntex

يوفر SharePoint Syntex الآن خيارا لإنشاء النماذج وتدريبها محليا على موقع SharePoint الخاص بك. يمكن استخدام هذه النماذج فقط على الموقع الذي تم إنشاؤها فيه. 

من خلال تنشيط تصنيف المستندات واستخراجها على موقع SharePoint الخاص بك، يتيح لك SharePoint Syntex تصنيف الملفات في مكتبات المستندات، واستخراج المعلومات من الملفات الجديدة، وأتمتة الأنشطة استنادا إلى المعلومات المستخرجة.

عند تنشيط إنشاء النموذج المحلي، ستتم إضافة القوائم والمكتبات التالية إلى موقعك:

- مكتبة مستندات النماذج
- مكتبة مستندات ملفات التدريب
- قائمة قوالب التفسير
- قائمة استخدام النموذج

تتوفر هذه الميزة فقط لإنشاء [نماذج فهم المستندات](apply-a-model.md) [والنماذج التي تم إنشاؤها مسبقا](prebuilt-models.md). 

## <a name="create-a-model-on-a-local-site"></a>إنشاء نموذج على موقع محلي

1. من مكتبة مستندات SharePoint، حدد الملفات التي تريد تحليلها، ثم حدد **"تصنيف" و"استخراج**".

    ![لقطة شاشة لمكتبة مستندات SharePoint مع تمييز خيار التصنيف والاستخراج.](../media/content-understanding/local-model-classify-and-extract-option.png) 

2. في المرة الأولى التي تستخدم فيها هذه الميزة، تقوم بتنشيط SharePoint Syntex على موقعك. سترى الرسالة التالية.

    ![لقطة شاشة لصفحة تنشيط تصنيف المستندات واستخراجها.](../media/content-understanding/local-model-first-run-activate-message.png) 

    > [!NOTE]
    > يجب أن يكون لديك الإذن "إدارة موقع ويب" لتنفيذ مهام الإدارة وإدارة المحتوى للموقع. سيكون هذا مالك موقع. بمجرد تنشيط الميزة، سيتمكن أي شخص لديه إذن "إدارة القوائم" من إنشاء النماذج وإدارتها.

3. حدد **"تنشيط** " للمتابعة. سترى الرسالة التالية.

    ![لقطة شاشة لرسالة تنشيط تصنيف المستند واستخراجه مع خيار إنشاء نموذج.](../media/content-understanding/local-model-activated-message.png) 

4. حدد **إنشاء نموذج**.

5. في لوحة **إنشاء نموذج** ، اكتب اسم النموذج، وحدد نوع النموذج، ثم حدد **Create**.

    ![Screenshot of the Create a model panel.](../media/content-understanding/local-model-create-a-model.png) 

6. تابع [لتدريب نموذج فهم المستند أو](apply-a-model.md) [لتكوين النموذج الذي تم إنشاؤه مسبقا](prebuilt-models.md) باستخدام الملفات التي حددتها.

7. عند الانتهاء، يتم فتح لوحة **"إضافة إلى المكتبة** ".

    ![لقطة شاشة للوحة إضافة إلى المكتبة تعرض الموقع والمكتبات المطبقة.](../media/content-understanding/local-model-add-to-library-panel.png) 

8. في لوحة "**إضافة إلى المكتبة**"، سترى اسم موقع SharePoint ومكتبة المستندات التي سيتم تطبيق النموذج عليها. إذا كنت تريد تطبيق النموذج على مكتبة مختلفة، فحدد **"العودة إلى المكتبات**"، واختر المكتبة التي تريد استخدامها. ثم حدد **"إضافة**".

9. في الصفحة الرئيسية للنموذج، في " **مكان تطبيق النموذج" على قسم الموقع هذا** ، يمكنك مشاهدة المكتبات التي تم تطبيق النموذج عليها. لتطبيق النموذج على مكتبات أخرى على الموقع، حدد **تطبيق النموذج**. 

    ![لقطة شاشة للصفحة الرئيسية للنموذج تعرض مكان تطبيق النموذج على قسم الموقع.](../media/content-understanding/local-model-home-page.png) 

