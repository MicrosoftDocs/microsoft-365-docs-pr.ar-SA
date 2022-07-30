---
title: ترحيل ملفات Google إلى Microsoft 365 للأعمال
f1.keywords:
- NOCSH
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
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية ترحيل ملفات Google إلى Microsoft 365 للأعمال باستخدام SharePoint Migration Manager.
ms.openlocfilehash: 55dd5740192914b89e7be1da070b97b4f6983c97
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67085536"
---
# <a name="migrate-google-files-to-microsoft-365-for-business-with-migration-manager"></a>ترحيل ملفات Google إلى Microsoft 365 للأعمال باستخدام Migration Manager

اطلع على [تعليمات Microsoft 365 للشركات الصغيرة](https://go.microsoft.com/fwlink/?linkid=2197659) على YouTube.

## <a name="watch-migrate-google-files-to-microsoft-365-for-business"></a>مشاهدة: ترحيل ملفات Google إلى Microsoft 365 للأعمال

اطلع على هذا الفيديو وغيره على [قناتنا على YouTube](https://go.microsoft.com/fwlink/?linkid=2198217).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWSx43?autoplay=false]

عند الانتقال إلى Microsoft 365 للأعمال من Google Workspace، ستحتاج إلى ترحيل ملفاتك من Google Drive. يمكنك استخدام SharePoint Migration Manager لنقل الملفات من محركات الأقراص الشخصية والمشتركة. يوفر لك هذا الفيديو وملخص الخطوات المطلوبة نظرة عامة حول كيفية القيام بذلك. للمزيد من المعلومات، راجع [ترحيل مساحة عمل Google إلى Microsoft 365 باستخدام إدارة الترحيل](/sharepointmigration/mm-google-overview).

> [!NOTE]
> سيقوم Migration Manager بعمل نسخة من الملفات ونقل النسخ إلى Microsoft 365 للأعمال. ستبقى الملفات الأصلية في Google Drives أيضا.

## <a name="before-you-start"></a>قبل البدء

يجب أن يكون جميع المستخدمين قد سجلوا الدخول إلى Microsoft 365 للأعمال وإعداد OneDrive for Business الخاصة بهم. للقيام بذلك، انتقل إلى [office.com](https://office.com)، وسجل الدخول باستخدام بيانات اعتماد Microsoft 365 للأعمال، ثم اختر OneDrive.

## <a name="install-the-microsoft-365-migration-app"></a>تثبيت تطبيق ترحيل Microsoft 365

استخدم الخطوات التالية لتثبيت تطبيق Microsoft 365 Migration في بيئة Google Workspace. 
1. في مركز مسؤول SharePoint، حدد **الترحيل**.
2. في صفحة **الترحيل** ، في قسم **Google Workspace** ، حدد **Get Started**.
3. في صفحة **"ترحيل محتوى Google Workspace" إلى صفحة Microsoft 365** ، حدد **"الاتصال بمساحة عمل Google**".
4. حدد **التثبيت والتخويل**.
5. في صفحة **Google Workspace Marketplace** ، حدد **تسجيل الدخول** وأدخل بيانات اعتماد مسؤول Google Workspace.
6. حدد **"تثبيت المجال**".
7. حدد **متابعة**.
8. حدد خانة الاختيار، ثم حدد **"السماح**".
9. عند اكتمال التثبيت، حدد **«Done»**.
10. ارجع إلى صفحة **تثبيت تطبيق الترحيل** ، وحدد **"التالي**".
11. حدد **تسجيل الدخول إلى Google Workspace**، ثم أدخل بيانات اعتماد مسؤول Google Workspace.
12. حدد **إنهاء**.

## <a name="select-and-scan-your-drives"></a>تحديد محركات الأقراص وفحصها

بعد تثبيت تطبيق ترحيل Microsoft 365 في بيئة Google، يمكنك الآن تحديد محركات الأقراص التي تريد ترحيلها ثم فحصها للتأكد من أنها آمنة للنسخ إلى Microsoft 365.

1. في علامة التبويب **"فحص** "، حدد محركات أقراص Google التي تريد نسخها إلى Microsoft 365.
2. حدد **الفحص**. عند اكتمال الفحص، ستظهر محركات الأقراص حالة الفحص " **جاهز للرحل**".
3. حدد **"نسخ" لل ترحيل**.

## <a name="start-the-migration"></a>بدء الترحيل

بعد تحديد محركات الأقراص التي تريد ترحيلها وفحصها، استخدم الخطوات التالية بترحيلها.

1. في علامة التبويب **"ترحيل** "، تحقق من المسارات الوجهة لمحركات الأقراص التي تريد ترحيلها. قم بتحريرها إذا لزم الأمر.
2. حدد محركات الأقراص التي تريد ترحيلها، ثم حدد **"ترحيل**". 
3. عند اكتمال الترحيل بنجاح، سيظهر كل محرك أقراص **حالة ترحيل** **مكتملة**.