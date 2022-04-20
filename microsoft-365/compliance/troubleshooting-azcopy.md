---
title: استكشاف أخطاء AzCopy وإصلاحها في eDiscovery (Premium)
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
description: استكشاف أخطاء Azure AzCopy وإصلاحها عند تحميل البيانات غير Office 365 لمعالجة الأخطاء في eDiscovery (Premium).
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: ff8f69e6efeab3e0f0e9d8ee2f739caaa40d7c85
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64991787"
---
# <a name="troubleshoot-azcopy-in-ediscovery-premium"></a>استكشاف أخطاء AzCopy وإصلاحها في eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

عند تحميل البيانات أو المستندات غير Microsoft 365 لمعالجة الأخطاء في Microsoft Purview eDiscovery (Premium)، توفر واجهة المستخدم أمر Azure AzCopy الذي يحتوي على معلمات مع موقع تخزين الملفات التي تريد تحميلها وموقع تخزين Azure الذي سيتم تحميل الملفات إليه. لتحميل المستندات، يمكنك نسخ هذا الأمر ثم تشغيله في موجه الأوامر على الكمبيوتر المحلي.  تعرض لقطة الشاشة التالية مثالا لأمر AzCopy:

![Upload ملفات غير Microsoft 365.](../media/46ba68f6-af11-4e70-bb91-5fc7973516e3.png)

عادة ما يعمل الأمر الذي يتم توفيره عند تشغيله. ومع ذلك، قد تكون هناك حالات لن يتم فيها تشغيل الأمر المعروض بنجاح. إليك بعض الأسباب المحتملة.

## <a name="the-supported-version-of-azcopy-isnt-installed-on-the-local-computer"></a>الإصدار المدعوم من AzCopy غير مثبت على الكمبيوتر المحلي

في هذا الوقت، يجب استخدام AzCopy v8.1 لتحميل البيانات غير Microsoft 365 في eDiscovery (Premium). يرجع الأمر AzCopy الذي يتم عرضه على صفحة **ملفات Upload** المعروضة في لقطة الشاشة السابقة خطأ إذا كنت لا تستخدم الإصدار 8.1 من AzCopy. لتثبيت هذا الإصدار، راجع [نقل البيانات باستخدام AzCopy v8.1 على Windows](/previous-versions/azure/storage/storage-use-azcopy).

## <a name="azcopy-isnt-installed-on-the-local-computer-or-its-not-installed-in-the-default-location"></a>لم يتم تثبيت AzCopy على الكمبيوتر المحلي أو لم يتم تثبيته في الموقع الافتراضي

إذا لم يكن AzCopy مثبتا أو تم تثبيته في موقع آخر غير موقع التثبيت الافتراضي (وهو `%ProgramFiles(x86)%`)، فقد تتلقى الخطأ التالي عند تشغيل أمر AzCopy:

> يتعذر على النظام العثور على المسار المحدد.

إذا لم يكن AzCopy مثبتا على الكمبيوتر المحلي، يمكنك العثور على معلومات التثبيت في [نقل البيانات باستخدام الإصدار 8.1 من AzCopy على Windows](/previous-versions/azure/storage/storage-use-azcopy). تأكد من تثبيته في الموقع الافتراضي.

إذا تم تثبيت AzCopy، ولكنه مثبت في موقع مختلف عن الموقع الافتراضي، يمكنك نسخ الأمر ولصقه في ملف نصي، ثم تغيير المسار إلى الموقع حيث تم تثبيت AzCopy. على سبيل المثال، إذا كان Azcopy موجودا في `%ProgramFiles%`، يمكنك تغيير الجزء الأول من الأمر من `%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy.exe` إلى `%ProgramFiles%\Microsoft SDKs\Azure\AzCopy`. بعد إجراء هذا التغيير، انسخه من الملف النصي ثم قم بتشغيل موجه الأوامر.

> [!TIP]
> إذا تم تثبيت AzCopy في موقع آخر ثم موقع التثبيت الافتراضي، ففكر في إلغاء تثبيته ثم أعد تثبيته في الموقع الافتراضي. سيساعد هذا على منع هذه المشكلة في المستقبل.