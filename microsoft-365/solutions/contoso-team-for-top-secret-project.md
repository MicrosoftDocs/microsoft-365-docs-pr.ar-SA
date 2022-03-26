---
title: فريق معزول لمشروع سري للغاية من شركة Contoso Corporation
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 08/14/2020
audience: ITPro
ms.topic: overview
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: Ent_Architecture
description: 'ملخص: كيف استخدم Contoso فريقا مع عزل الأمان لمشروع سري للغاية لتطوير مجموعة جديدة من المنتجات والخدمات.'
ms.openlocfilehash: 5b6bc72a6476301cf3239aeb7f68486f15ebbac8
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63569291"
---
# <a name="isolated-team-for-a-top-secret-project-of-the-contoso-corporation"></a>فريق معزول لمشروع سري للغاية من شركة Contoso Corporation

بعد وجود مدير تنفيذي خارج الموقع، أمر المدير التنفيذي لشركة Contoso تطوير مجموعة جديدة من المنتجات والخدمات التي يمكن أن تضاعف أرباح Contoso في السنوات الخمس القادمة. تم تسمية مشروع سري للغاية لتطوير خطة الأعمال والهندسة **والسوق Project 2X** وتعيين الموظفين الأساسيين عبر الشركة. 

كانت الجداول الزمنية للبحث والتطوير ضيقة، مما يعني أن التعاون يجب أن يكون فعالا وأن يوفر الاجتماعات الآمنة والمحادثات الجارية وتخزين الملفات.

كانت التسليمات الناتجة ل Project 2X هي خطط الأعمال ومواصفات المنتجات والهندسة ومواد التسويق والجداول في شكل ملفات Word Excel PowerPoint. 

نظرا للطبيعة الحساسة لهذه الملفات، كان الوصول إلى هذه الملفات:

- مقيد بأعضاء Project 2X و القيادة العليا.
- مشفر ومحمي مع أذونات للسماح بالوصول إلى أعضاء فريق Project 2X و القيادة العليا فقط، حتى لو تم توزيع الملفات خارج المجلدات الآمنة الخاصة بهم.

استخدم موظفو Contoso IT [فريقا](secure-teams-security-isolation.md) مع عزل أمان Project 2X وهذه الخطوات.

## <a name="step-1-created-a-private-team"></a>الخطوة 1: إنشاء فريق خاص

أولا، لحماية الوصول إلى موقع SharePoint الأساسي للفريق، يقوم مسؤولي تكنولوجيا المعلومات في Contoso [بتكوين SharePoint الوصول الأساسية الموصى بها](../security/office-365-security/sharepoint-file-access-policies.md).

بعد ذلك، أنشأ مسؤول تكنولوجيا معلومات Contoso فريقا خاصا جديدا Project 2X وأضاف حسابات المستخدمين الخاصة بفريق Project 2X كأعضاء. كما تم تكوين الفريق بحيث يمكن لمالكي Project 2X فقط إنشاء قنوات خاصة.

للحصول على تفاصيل التكوين، راجع [إنشاء فريق خاص](secure-teams-security-isolation.md#create-a-private-team).

## <a name="step-2-created-a-sensitivity-label-for-the-project-2x-team"></a>الخطوة 2: إنشاء تسمية حساسية لفريق Project 2X

أنشأ مسؤولو Contoso تسمية حساسية جديدة **Project 2X**:

- التشفير الممكن.
- الأذونات Co-Author المسموح بها لمجموعة Project 2X Microsoft 365 2X.
- أذونات العارض المسموح بها لمجموعة القيادة العليا.
- الوصول المحظور إلى الأجهزة غير المجهزة.

تم حماية الملفات الموجودة في **قسم** المستندات في Project 2X SharePoint بواسطة:

- أذونات الموقع، التي تسمح فقط بالأذونات الكاملة لأعضاء Project 2X Microsoft 365 وقراءة الأذونات لمجموعة القيادة العليا.
- يتم Project حساسية 2X، مع التشفير والأذونات التي تنتقل مع الملف إذا تم نقله أو نسخه من الموقع.

للحصول على تفاصيل التكوين، راجع [إنشاء تسمية حساسية](secure-teams-security-isolation.md#create-a-sensitivity-label).

## <a name="step-3-configured-the-underlying-sharepoint-site"></a>الخطوة 3: تكوين موقع SharePoint الأساسي

أولا، لحماية الوصول إلى موقع SharePoint الأساسي للفريق، يقوم مسؤولي تكنولوجيا المعلومات في Contoso [بتكوين SharePoint الوصول الأساسية الموصى بها](../security/office-365-security/sharepoint-file-access-policies.md).

بعد ذلك، تم تكوين إعدادات أذونات إضافية للموقع:

- لمنع Project مجموعة 2X من مشاركة الوصول إلى الموقع. للحصول على تفاصيل التكوين، راجع SharePoint [فريق مع عزل الأمان](secure-teams-security-isolation.md#sharepoint-settings).
- للحصول على أذونات القراءة لمجموعة القيادة العليا.

بعد ذلك، تم تكوين إعدادات أذونات إضافية للموقع لمنع Project مجموعة 2X من مشاركة الوصول إلى الموقع. 

مع إنشاء قنوات خاصة Project 2X، عطل مالك المجموعة مشاركة الضيف وحدد ارتباط المشاركة الافتراضي إلى قيمة **الأشخاص المحددين**.

إليك التكوين الناتج لفريق Project 2X مع عزل الأمان.

![التكوين الناتج لفريق Project 2X.](../media/contoso-team-for-top-secret-project.png)

 ## <a name="step-4-trained-project-2x-team-members"></a>الخطوة 4: أعضاء فريق Project 2X

لقد تدرب موظفو أمان Contoso أعضاء فريق Project 2X في دورة إلزامية تدربوا خلالها على:

- كيفية الوصول إلى Project 2X الجديد، واستخدام الاجتماعات والمحادثات، وكيفية التعاون في العمل على ملفات الفريق.
- كيفية إنشاء ملفات جديدة في الفريق وتحميل ملفات جديدة تم إنشاؤها محليا.
- كيفية تسمية الملفات باستخدام تسمية الحساسية Project 2X.
- عرض لكيفية حماية Project 2X لملف حتى عند مغادرته الفريق.

كانت النتيجة النهائية بيئة آمنة تعاون فيها Project فريق 2X في بيئة آمنة للدردشات والاجتماعات والملفات.

فيما يلي مثال لملف مخزن في موقع Project 2X مع تعيين تسمية حساسية Project 2X.

![مثال لملف مخزن في موقع Project 2X.](../media/contoso-team-for-top-secret-project-example.png)

في بعض الحالات، Project فريق 2X ملفات محمية بواسطة تسمية Project 2X إلى محرك أقراص محلي للعمل دون اتصال. 

ومع ذلك، بعد أن تمت مطالبتهم للحصول على بيانات الاعتماد عند فتحها، أدركوا خطأهم وحذفوها.

نظرا لبيئة التعاون Teams وميزات الأمان الخاصة Microsoft 365، تم الاحتفاظ بتفاصيل Project 2X سرية طوال مدة المشروع. أعلنت شركة Contoso عن خططها وهي في مرحلة طرح المنتجات والخدمات الجديدة لاسعاد عملائها ومستثمريها وبهجة منافسيها.

## <a name="next-step"></a>الخطوة التالية

[نشر فريق مع عزل الأمان](secure-teams-security-isolation.md) في مؤسستك.

