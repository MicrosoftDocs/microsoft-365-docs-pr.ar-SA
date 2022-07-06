---
title: استخدام أداة تصدير eDiscovery في Microsoft Edge
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: يجب تمكين دعم ClickOnce لاستخدام أحدث إصدار من Microsoft Edge لتنزيل نتائج البحث من البحث في المحتوى وeDiscovery في مركز الأمان والتوافق.
ms.openlocfilehash: f93ab1da1b76d435cc1ce684aa459b4c131dfff8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630378"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>استخدام أداة تصدير eDiscovery في Microsoft Edge

نتيجة للتغييرات الأخيرة في الإصدار الأحدث من Microsoft Edge، لم يعد دعم ClickOnce ممكنا بشكل افتراضي. لمتابعة استخدام أداة تصدير eDiscovery لتنزيل نتائج البحث في المحتوى أو eDiscovery، تحتاج إما إلى استخدام [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) أو تمكين دعم ClickOnce في أحدث إصدار من Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>تمكين دعم ClickOnce في Microsoft Edge

1. في Microsoft Edge، انتقل إلى **edge://flags/#edge-click-once**.

2. إذا تم تعيين القيمة الموجودة إلى **"افتراضي"** أو **"معطل"** في القائمة المنسدلة، فقم بتغييرها إلى **"ممكن".**

   ![حدد ممكن من القائمة المنسدلة.](../media/ClickOnceimage1.png)

3. قم بالتمرير لأسفل إلى أسفل نافذة المستعرض وانقر فوق **"إعادة تشغيل** " لإعادة تشغيل Edge.

   ![انقر فوق "إعادة التشغيل".](../media/ClickOnceimage2.png)

**ملاحظه:** يمكن للمؤسسات استخدام نهج المجموعة لتعطيل دعم ClickOnce. للتحقق مما إذا كان هناك نهج تنظيمي لدعم ClickOnce، انتقل إلى **edge://policy**. تظهر لقطة الشاشة التالية أنه تم تمكين ClickOnce عبر المؤسسة بأكملها. إذا تم تعيين قيمة النهج هذه إلى **خطأ**، فستحتاج إلى الاتصال بمسؤول في مؤسستك.

![قائمة نهج Edge التنظيمية.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>تثبيت أداة تصدير eDiscovery وتشغيلها

1. انقر فوق **"تنزيل النتائج** " على صفحة القائمة المنبثقة لتصدير في "البحث في المحتوى" أو حالة eDiscovery.

   ![انقر فوق "تنزيل النتائج" على صفحة القائمة المنبثقة لتنزيل نتائج البحث.](../media/ClickOnceExport1.png)

2. ستتم مطالبتك بتأكيد لبدء تشغيل الأداة، انقر فوق **"فتح**".

   ![انقر فوق "فتح" لبدء تشغيل "أداة تصدير eDiscovery".](../media/ClickOnceimage4.png)

   إذا لم يتم تثبيت أداة تصدير eDiscovery، فستتم مطالبتك بتحذير أمان، 

   ![انقر فوق "تثبيت" لتثبيت "أداة تصدير eDiscovery".](../media/ClickOnceimage5.png)

3. انقر فوق **تثبيت**. بعد تثبيتها، سيتم تشغيل أداة التصدير تلقائيا.

لمزيد من المعلومات، راجع المواضيع التالية:

- [تصدير نتائج البحث في المحتوى](export-search-results.md)

- [كيفية تمكين علامات التجربة في Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
