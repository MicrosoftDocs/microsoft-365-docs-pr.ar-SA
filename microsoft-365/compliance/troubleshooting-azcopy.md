---
title: استكشاف الأخطاء في AzCopy في Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: استكشاف أخطاء Azure AzCopy وإصلاحها عند تحميل بيانات Office 365 معالجة الأخطاء في Advanced eDiscovery.
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: 45f82482f92e740383eca774671f1abd55535675
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63567155"
---
# <a name="troubleshoot-azcopy-in-advanced-ediscovery"></a>استكشاف الأخطاء في AzCopy في Advanced eDiscovery

عند تحميل بيانات أو مستندات غير Microsoft 365 من أجل تصحيح الأخطاء في Advanced eDiscovery، توفر واجهة المستخدم أمر Azure AzCopy الذي يحتوي على معلمات مع موقع تخزين الملفات التي تريد تحميلها وموقع تخزين Azure الذي سيتم تحميل الملفات فيه. لتحميل المستندات، انسخ هذا الأمر ثم قم بتشغيله في موجه الأوامر على الكمبيوتر المحلي.  تعرض لقطة الشاشة التالية مثالا عن أمر AzCopy:

![Upload الملفات غير Microsoft 365.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

عادة ما يعمل الأمر الذي يتم توفيره عند تشغيله. ومع ذلك، قد تكون هناك حالات لا يتم فيها تشغيل الأمر المعروض بنجاح. إليك بعض الأسباب المحتملة.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>لم يتم تثبيت الإصدار المعتمد من AzCopy على الكمبيوتر المحلي

في هذا الوقت، يجب استخدام AzCopy v8.1 لتحميل البيانات غير Microsoft 365 في Advanced eDiscovery. يرجع الأمر AzCopy الذي يتم عرضه على **صفحة** ملفات Upload الموجودة في لقطة الشاشة السابقة خطأ إذا كنت لا تستخدم AzCopy v8.1. لتثبيت هذا الإصدار، راجع [نقل البيانات باستخدام AzCopy v8.1 على Windows](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>AzCopy غير مثبت على الكمبيوتر المحلي أو أنه غير مثبت في الموقع الافتراضي

إذا لم يكن AzCopy مثبتا أو كان مثبتا في موقع آخر غير موقع التثبيت الافتراضي ( `%ProgramFiles(x86)%`وهو )، فقد تتلقى الخطأ التالي عند تشغيل الأمر AzCopy:

> يتعذر على النظام العثور على المسار المحدد.

إذا لم يكن AzCopy مثبتا على الكمبيوتر المحلي، يمكنك العثور على معلومات التثبيت في نقل البيانات باستخدام [AzCopy v8.1 على Windows](/previous-versions/azure/storage/storage-use-azcopy). تأكد من تثبيته في الموقع الافتراضي.

إذا تم تثبيت AzCopy، ولكنه مثبت في موقع مختلف عن الموقع الافتراضي، يمكنك نسخ الأمر ولصقه في ملف نصي، ثم تغيير المسار إلى الموقع حيث تم تثبيت AzCopy. على سبيل المثال، إذا كان Azcopy `%ProgramFiles%`موجودا في ، يمكنك تغيير الجزء الأول من الأمر من `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` إلى `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. بعد إجراء هذا التغيير، انسخه من الملف النصي ثم قم بتشغيله موجه الأوامر.

> [!TIP]
> إذا تم تثبيت AzCopy في موقع آخر، فقم ب إلغاء تثبيته ثم إعادة تثبيته في الموقع الافتراضي. سيساعد ذلك في منع هذه المشكلة في المستقبل.