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
description: تعرف على كيفية إنشاء نموذج محلي على موقع SharePoint محلي SharePoint Syntex.
ms.openlocfilehash: f6eab2d081dda379d8eb2c88d762661d374a1db6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63703436"
---
# <a name="create-a-model-on-a-local-sharepoint-site-with-microsoft-sharepoint-syntex"></a>إنشاء نموذج على موقع SharePoint محلي باستخدام Microsoft SharePoint Syntex

SharePoint Syntex الآن خيارا لإنشاء نماذج وتدريبها محليا على موقع SharePoint الخاص بك. لا يمكن استخدام هذه النماذج إلا على الموقع حيث تم إنشاؤها. 

من خلال تنشيط تصنيف المستندات واستخراجها على موقع SharePoint، يتيح لك SharePoint Syntex إمكانية تصنيف الملفات في مكتبات المستندات واستخراج المعلومات من الملفات الجديدة وأتمتة الأنشطة استنادا إلى المعلومات المستخرجة.

عند تنشيط إنشاء نموذج محلي،  تضاف القوائم والمكتبات التالية إلى موقعك:

- مكتبة مستندات النماذج
- مكتبة مستندات ملفات التدريب
- قائمة قوالب الشرح
- قائمة استخدام النماذج

تتوفر هذه الميزة فقط لإنشاء [نماذج فهم المستندات](apply-a-model.md) والنماذج التي تم [تصميمها مسبقا](prebuilt-models.md). 

## <a name="create-a-model-on-a-local-site"></a>إنشاء نموذج على موقع محلي

1. من مكتبة SharePoint المستندات، حدد الملفات التي تريد تحليلها، ثم حدد **تصنيف واستخراج**.

    ![لقطة شاشة لمكتبة مستندات SharePoint مع تمييز الخيار "تصنيف" و"استخراج".](../media/content-understanding/local-model-classify-and-extract-option.png) 

2. في المرة الأولى التي تستخدم فيها هذه الميزة، تقوم بتنشيط SharePoint Syntex على موقعك. سترى الرسالة التالية.

    ![لقطة شاشة لصفحة "تنشيط معلومات تصنيف المستند واستخراجه".](../media/content-understanding/local-model-first-run-activate-message.png) 

3. حدد **تنشيط** للمتابعة. سترى الرسالة التالية.

    ![لقطة شاشة للرسالة التي تم تنشيطها لتصنيف المستند واستخراجه مع خيار إنشاء نموذج.](../media/content-understanding/local-model-activated-message.png) 

4. حدد **إنشاء نموذج**.

5. في اللوحة **إنشاء نموذج** ، اكتب اسم النموذج، وحدد نوع النموذج، ثم حدد **إنشاء**.

    ![لقطة شاشة للوحة "إنشاء نموذج".](../media/content-understanding/local-model-create-a-model.png) 

6. تابع تدريب [نموذج فهم المستند](apply-a-model.md) أو [لتكوين](prebuilt-models.md) النموذج الذي تم تصميمه مسبقا باستخدام الملفات التي حددتها.

7. عند القيام بذلك **، يتم فتح** اللوحة إضافة إلى المكتبة.

    ![لقطة شاشة للوحة "إضافة إلى المكتبة" تعرض الموقع والمكتبات المطبقة.](../media/content-understanding/local-model-add-to-library-panel.png) 

8. في اللوحة **إضافة** إلى المكتبة، سترى اسم موقع SharePoint ومكتبة المستندات التي سيتم تطبيق النموذج عليها. إذا كنت تريد تطبيق النموذج على مكتبة أخرى، فحدد العودة إلى **المكتبات**، واختر المكتبة التي تريد استخدامها. ثم حدد **إضافة**.

9. في الصفحة الرئيسية للنموذج، في المقطع **مكان** تطبيق النموذج على هذا الموقع، يمكنك رؤية المكتبات التي تم تطبيق النموذج عليها. لتطبيق النموذج على مكتبات أخرى على الموقع، حدد **تطبيق النموذج**. 

    ![لقطة شاشة للصفحة الرئيسية للنموذج تعرض المقطع "مكان تطبيق النموذج على الموقع".](../media/content-understanding/local-model-home-page.png) 

