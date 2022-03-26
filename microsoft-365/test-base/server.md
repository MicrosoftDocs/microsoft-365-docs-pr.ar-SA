---
title: Windows تطبيق الخادم
description: كيفية التحقق من صحة اختبار تطبيق windows server
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 99868e53e98bded9139ecedea9c9d62e9d48fd2f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63571736"
---
# <a name="windows-server-application-testing"></a>Windows تطبيق الخادم

باستخدام Test Base Microsoft 365، يمكنك الآن التحقق من صحة تطبيقاتك مقابل Windows Server 2016 و2019، بما في ذلك Server Core!

للبدء في التحقق من صحة التطبيقات التي تم تحميلها مقابل تحديثات الإصدارات المسبقة لنظامي التشغيل Windows Server 2016 و2019 على Test Base for Microsoft 365، يرجى الالتزام بالخطوات التالية:

1. سجل دخولك إلى مدخل الخدمة الذاتية. من قائمة التنقل الموجودة على الجانب الأيمن، حدد `Upload new package` ضمن `Package catalogue` وملئ تفاصيل الاختبار.

2. حدد `Security updates` كنوع تحديث نظام التشغيل:

   ![حدد تحديثات الأمان.](Media/selecting-security-updates.png)

3. ضمن إصدارات نظام التشغيل التي يجب اختبارها، حدد إصدارات نظام التشغيل القابلة للتطبيق. يمكنك تحديد Windows نظام تشغيل الخادم أو مجموعة من إصدارات نظام تشغيل الخادم والعميل.

   ![حدد إصدار نظام التشغيل.](Media/selecting-OS-versions.png)

4. قم بتوفير المعلومات الأخرى المطلوبة ومراجعة التفاصيل المتوفرة وتحميل حزمة التطبيق. بعد التحميل، يمكنك عرض حالة الحزمة على علامة التبويب قائمة إدارة الحزم.

5. لعرض نتائج الاختبار والنتائج الدقيقة من التحقق من صحة التطبيق مقابل تحديثات أمان الإصدارات المسبقة ل Windows Server 2016 و2019، انتقل إلى صفحة ملخص الاختبار أو صفحة نتائج تحديث الأمان.

   ![عرض نتائج الاختبار.](Media/access-test-results.png)

التقدم إلى المقالة التالية للبدء باستخدام **الاختبار الوظيفي**
> [!div class="nextstepaction"]
> [الخطوة التالية](functional.md)
