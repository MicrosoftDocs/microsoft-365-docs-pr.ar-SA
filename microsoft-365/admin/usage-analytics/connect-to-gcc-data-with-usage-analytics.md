---
title: الاتصال البيانات Microsoft 365 سحابة القطاع الحكومي (سحابة القطاع الحكومي) باستخدام "تحليلات الاستخدام"
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: تعرف على كيفية الاتصال بالبيانات في مستأجر Microsoft 365 سحابة القطاع الحكومي (سحابة القطاع الحكومي) باستخدام تطبيق قالب Microsoft 365 تحليلات الاستخدام في Power BI.
ms.openlocfilehash: 3930ffe82c998797aade84e92145adac5fa2ea98
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63579699"
---
# <a name="connect-to-microsoft-365-government-community-cloud-gcc-data-with-usage-analytics"></a>الاتصال البيانات Microsoft 365 سحابة القطاع الحكومي (سحابة القطاع الحكومي) باستخدام "تحليلات الاستخدام"

استخدم الإجراءات التالية للاتصال بالبيانات باستخدام Microsoft 365 تحليلات الاستخدام في Microsoft 365 سحابة القطاع الحكومي المستأجر (سحابة القطاع الحكومي). 

> [!NOTE]
> هذه الإرشادات مخصصة Microsoft 365 سحابة القطاع الحكومي المستأجرين. 

## <a name="before-you-begin"></a>قبل البدء

لتكوين تحليلات الاستخدام Microsoft 365 أولا: 

- يجب أن تكون Microsoft 365 عام لتمكين تجميع البيانات. 
- تحتاج إلى [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) لاستخدام ملف القالب. 
- تحتاج إلى ترخيص [Power BI Pro أو Premium](https://go.microsoft.com/fwlink/p/?linkid=845347) لنشر التقرير وعرضه. 

## <a name="step-1-make-you-organizations-data-available-for-the-microsoft-365-usage-analytics-report"></a>الخطوة 1: جعل بيانات مؤسستك متوفرة للتقرير Microsoft 365 تحليلات الاستخدام

1. في مركز مسؤولي Microsoft 365، قم بتوسيع قائمة التنقل، وحدد **تقارير**، ثم حدد **الاستخدام**. 
2. في الصفحة **تقارير الاستخدام**، في المقطع Microsoft 365 تحليلات الاستخدام **، حدد بدء الاستخدام**. 
3. ضمن **تمكين Power BI لتحليلات الاستخدام**، حدد توفير بيانات استخدام المؤسسة لتحليلات استخدام **Microsoft ل Power BI**، ثم حدد **حفظ**.

    ![اجعل بيانات المستأجر متوفرة.](../../media/usage-analytics/make-data-available.png) 



    سيبدأ هذا عملية لجعل بيانات مؤسستك يمكن الوصول إليها لهذا التقرير، وسترى رسالة تفيد أننا نعمل على تجهيز بياناتك Microsoft 365 **تحليلات الاستخدام**. تجدر الإشارة إلى أن هذه العملية قد تستغرق 24 ساعة حتى تكتمل. 

4. عندما تكون بيانات مؤسستك جاهزة، سيعرض تحديث الصفحة رسالة تفيد بأن بياناتك متوفرة الآن، كما سيوفر رقم **"الموفر** " الخاص بك. ستحتاج إلى استخدام "معر ة المستأجر" في خطوة لاحقة عند محاولة الاتصال بالبيانات الخاصة بمستأجرك. 
 
    !["مستأجر"](../../media/usage-analytics/tenant-id-gcc.png) 
 
    > [!IMPORTANT]
    > عندما تكون بياناتك متوفرة، لا تحدد الانتقال إلى **Power BI**، الذي سي نقلك إلى سوق Power BI.  لا يتوفر تطبيق القوالب لهذا التقرير سحابة القطاع الحكومي المستأجرين في سوق Power BI.  


## <a name="step-2-download-the-power-bi-template-connect-to-your-data-and-publish-the-report"></a>الخطوة 2: تنزيل قالب Power BI والاتصال بالبيانات ونشر التقرير

Microsoft 365 سحابة القطاع الحكومي المستخدمين تنزيل ملف قالب Microsoft 365 تحليلات الاستخدام واستخدامه للاتصال بالبيانات الخاصة بهم. ستحتاج إلى Power BI Desktop لفتح ملف القالب واستخدامه. 

 > [!NOTE]
 > حاليا، لا يتوفر تطبيق قالب Microsoft 365 تحليلات الاستخدام سحابة القطاع الحكومي المستأجرين في Power BI Marketplace.  

1. بعد تنزيل قالب [Power BI](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit)، افتحه باستخدام Power BI Desktop. 
2. عند مطالبتك ب **"مستأجر"**، أدخل "هوية المستأجر" التي تلقيتها عند إعداد بيانات مؤسستك لهذا التقرير في الخطوة 1. ثم حدد **تحميل**. سيستغرق تحميل البيانات عدة دقائق. 

    ![أدخل "معر ة المستأجر".](../../media/usage-analytics/add-tenant-id.png) 



3. عند اكتمال التحميل، سيتم عرض التقرير، وسترى ملخصا تنفيذيا لبياناتك. 

    ![الملخص التنفيذي.](../../media/usage-analytics/exec-summary.png) 
 

4. احفظ التغييرات التي تم إدخالها على التقرير. 
5. حدد **نشر** في القائمة Power BI Desktop لنشر التقرير إلى خدمة Power BI Online حيث يمكن عرضها. يتطلب ذلك إما ترخيصا Power BI Pro أو سعة Power BI Premium. كجزء من [عملية النشر،](/power-bi/create-reports/desktop-upload-desktop-files#to-publish-a-power-bi-desktop-dataset-and-reports) ستحتاج إلى تحديد وجهة للنشر إلى مساحة عمل متوفرة في خدمة Power BI Online.

## <a name="related-content"></a>المحتوى ذي الصلة

[حول تحليلات الاستخدام](usage-analytics.md) </br>
[الحصول على أحدث إصدار من تحليلات الاستخدام](get-the-latest-version-of-usage-analytics.md) </br>
[التنقل بين التقارير واستخدامها في Microsoft 365 تحليلات الاستخدام](navigate-and-utilize-reports.md) </br>