---
title: التوزيع باستخدام نظام إدارة الجهاز الجوال (MDM) مختلف Microsoft Defender لنقطة النهاية على Mac
description: تثبيت Microsoft Defender لنقطة النهاية على Mac على حلول إدارة أخرى.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، التوزيع، macos، catalina، mojave، high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: mavel
author: maximvelichko
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2fa64ee9822fe1f784788e2d1ead79e66eb200ef
ms.sourcegitcommit: 2d870e06e87b10d9e8ec7a7a8381353bc3bc59c7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/11/2022
ms.locfileid: "65349744"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>التوزيع باستخدام نظام إدارة الجهاز المحمول (MDM) مختلف Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع [Microsoft Defender لنقطة النهاية الرئيسية على صفحة macOS للحصول على](microsoft-defender-endpoint-mac.md) وصف للمتطلبات الأساسية ومتطلبات النظام لإصدار البرنامج الحالي.


## <a name="approach"></a>النهج

> [!CAUTION]

> حاليا، تدعم Microsoft رسميا Intune و JAMF فقط لنشر وإدارة Microsoft Defender لنقطة النهاية على macOS. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات الواردة أدناه.

إذا كانت مؤسستك تستخدم حل إدارة الجهاز الأجهزة المحمولة (MDM) غير معتمد رسميا، فهذا لا يعني أنك غير قادر على نشر Microsoft Defender لنقطة النهاية أو تشغيلها على macOS.

لا يعتمد Microsoft Defender لنقطة النهاية على macOS على أي ميزات خاصة بالمورد. يمكن استخدامه مع أي حل MDM يدعم الميزات التالية:

- نشر macOS.pkg إلى الأجهزة المدارة.
- نشر ملفات تعريف تكوين النظام macOS إلى الأجهزة المدارة.
- تشغيل أداة/برنامج نصي عشوائي تم تكوينه من قبل المسؤول على الأجهزة المدارة.

تتضمن معظم حلول MDM الحديثة هذه الميزات، ومع ذلك، فإنها قد تستدعيها بشكل مختلف.

يمكنك نشر Defender لنقطة النهاية دون المتطلبات الأخيرة من القائمة السابقة، ومع ذلك:

- لن تتمكن من جمع الحالة بطريقة مركزية.
- إذا قررت إلغاء تثبيت Defender لنقطة النهاية، فستحتاج إلى تسجيل الدخول إلى جهاز العميل محليا كمسؤول.

## <a name="deployment"></a>نشر

تستخدم معظم حلول MDM نفس النموذج لإدارة أجهزة macOS، مع مصطلحات مماثلة. استخدم [النشر المستند إلى JAMF](mac-install-with-jamf.md) كقالب.

### <a name="package"></a>حزمه

تكوين نشر [حزمة تطبيق مطلوبة](mac-install-with-jamf.md)، مع تنزيل حزمة التثبيت (wdav.pkg) من [مدخل Microsoft 365 Defender](mac-install-with-jamf.md).

لنشر الحزمة على مؤسستك، استخدم الإرشادات المقترنة بحل MDM الخاص بك.

### <a name="license-settings"></a>إعدادات الترخيص

إعداد [ملف تعريف تكوين النظام](mac-install-with-jamf.md). 

قد يسميه حل MDM شيئا مثل "ملف تعريف مخصص الإعدادات"، لأن Microsoft Defender لنقطة النهاية على macOS ليس جزءا من macOS.

استخدم قائمة الخصائص، jamf/WindowsDefenderATPOnboarding.plist، والتي يمكن استخراجها من حزمة الإلحاق التي تم تنزيلها من [مدخل Microsoft 365 Defender](mac-install-with-jamf.md).
قد يدعم النظام قائمة خصائص عشوائية بتنسيق XML. يمكنك تحميل ملف jamf/WindowsDefenderATPOnboarding.plist كما هو في هذه الحالة.
بدلا من ذلك، قد يتطلب منك تحويل قائمة الخصائص إلى تنسيق مختلف أولا.

عادة، يحتوي ملف التعريف المخصص على معرف أو اسم أو سمة مجال. يجب عليك استخدام "com.microsoft.wdav.atp" بالضبط لهذه القيمة.
يستخدمه MDM لنشر ملف الإعدادات إلى **/Library/Managed Preferences/com.microsoft.wdav.atp.plist** على جهاز عميل، ويستخدم Defender for Endpoint هذا الملف لتحميل معلومات الإلحاق.

### <a name="kernel-extension-policy"></a>نهج ملحق Kernel

إعداد نهج ملحق KEXT أو kernel. استخدم معرف الفريق **UBF8T346G9** للسماح بملحقات النواة التي توفرها Microsoft.

> [!CAUTION]
> إذا كانت بيئتك تتكون من أجهزة Apple Silicon (M1)، يجب ألا تتلقى هذه الأجهزة ملفات تعريف التكوين باستخدام نهج KEXT.
> لا تدعم Apple KEXT على هذه الأجهزة، وسيفشل نشر ملف التعريف هذا على أجهزة M1.

### <a name="system-extension-policy"></a>نهج ملحق النظام

إعداد نهج ملحق النظام. استخدم معرف الفريق **UBF8T346G9** والموافقة على معرفات المجموعة التالية:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>نهج الوصول الكامل إلى القرص

منح حق الوصول إلى القرص الكامل للمكونات التالية:

- Microsoft Defender for Endpoint
    - المعرف: `com.microsoft.wdav`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- ملحق أمان Microsoft Defender لنقطة النهاية
    - المعرف: `com.microsoft.wdav.epsext`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>نهج ملحق الشبكة

كجزء من قدرات الكشف عن نقطة النهاية والاستجابة لها، يقوم Microsoft Defender لنقطة النهاية على macOS بفحص حركة مرور مأخذ التوصيل ويبلغ عن هذه المعلومات إلى مدخل Microsoft 365 Defender. يسمح النهج التالي لملحق الشبكة بتنفيذ هذه الوظيفة.

- نوع عامل التصفية: المكون الإضافي
- معرف مجموعة المكونات الإضافية: `com.microsoft.wdav`
- تصفية معرف مجموعة عناصر موفر البيانات: `com.microsoft.wdav.netext`
- المتطلبات المعينة لموفر بيانات التصفية: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- تصفية مآخذ التوصيل: `true`

## <a name="check-installation-status"></a>التحقق من حالة التثبيت

تشغيل [Microsoft Defender لنقطة النهاية](mac-install-with-jamf.md) على جهاز عميل للتحقق من حالة الإلحاق.
