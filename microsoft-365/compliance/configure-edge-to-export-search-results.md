---
title: استخدم أداة تصدير eDiscovery في Microsoft Edge
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: يجب تمكين ClickOnce من استخدام أحدث إصدار من Microsoft Edge لتنزيل نتائج البحث من البحث في المحتوى و eDiscovery في مركز الأمان والتوافق.
ms.openlocfilehash: bd42ebffce326e4abe4943ff4187fc2bd960ff65
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 09/12/2021
ms.locfileid: "63566150"
---
# <a name="use-the-ediscovery-export-tool-in-microsoft-edge"></a>استخدم أداة تصدير eDiscovery في Microsoft Edge

نتيجة التغييرات الأخيرة التي تم إدخالها على الإصدار الأحدث من Microsoft Edge، ClickOnce يتم تمكين الدعم بشكل افتراضي. لمواصلة استخدام أداة تصدير eDiscovery لتنزيل نتائج بحث المحتوى أو بحث eDiscovery، ستحتاج إما إلى استخدام [Microsoft Internet Explorer](https://support.microsoft.com/help/17621/internet-explorer-downloads) أو تمكين دعم ClickOnce في أحدث إصدار من Microsoft Edge.

## <a name="enable-clickonce-support-in-microsoft-edge"></a>تمكين ClickOnce في Microsoft Edge

1. في Microsoft Edge، **انتقل إلى edge://flags/#edge-click-once**.

2. إذا تم تعيين القيمة الموجودة إلى **افتراضي** أو **معطل** في القائمة المنسدلة، فغيرها إلى **تمكين**.

   ![حدد تمكين من القائمة المنسدلة.](../media/ClickOnceimage1.png)

3. قم بالتمرير لأسفل إلى أسفل نافذة المستعرض وانقر فوق **إعادة تشغيل** لإعادة تشغيل Edge.

   ![انقر فوق إعادة تشغيل.](../media/ClickOnceimage2.png)

**ملاحظة:** يمكن أن تستخدم المؤسسات "نهج المجموعة" لتعطيل ClickOnce الدعم. للتحقق مما إذا كان هناك نهج تنظيمي ClickOnce الدعم، **انتقل إلى edge://policy**. تظهر لقطة الشاشة التالية أنه ClickOnce في المؤسسة بكاملها. إذا تم تعيين قيمة النهج هذه إلى **خطأ**، ستحتاج إلى الاتصال بمسؤول في مؤسستك.

![قائمة سياسات المؤسسة في Edge.](../media/ClickOnceimage3.png)

## <a name="install-and-run-the-ediscovery-export-tool"></a>تثبيت أداة تصدير eDiscovery وتشغيلها

1. انقر **فوق تنزيل النتائج** على صفحة النشرة من خلال عملية تصدير في البحث في المحتوى أو حالة eDiscovery.

   ![انقر فوق تنزيل النتائج على صفحة النشرة flyout لتنزيل نتائج البحث.](../media/ClickOnceExport1.png)

2. سيتم مطالبتك بتأكيد على بدء تشغيل الأداة، انقر فوق **فتح**.

   ![انقر فوق فتح لفتح أداة تصدير eDiscovery.](../media/ClickOnceimage4.png)

   إذا لم تكن أداة تصدير eDiscovery مثبتة، سيتم مطالبتك بتحذير أمان، 

   ![انقر فوق تثبيت لتثبيت أداة تصدير eDiscovery.](../media/ClickOnceimage5.png)

3. انقر فوق **تثبيت**. بعد تثبيتها، سيتم تشغيل أداة التصدير تلقائيا.

لمزيد من المعلومات، راجع المواضيع التالية:

- [تصدير نتائج البحث في المحتوى](export-search-results.md)

- [كيفية تمكين علامة التجربة في Microsoft Edge](https://microsoftedgesupport.microsoft.com/hc/articles/360034075294-How-to-enable-experiment-flags-in-Microsoft-Edge-Insider-channels)
