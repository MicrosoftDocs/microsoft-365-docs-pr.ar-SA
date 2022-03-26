---
title: النشر باستخدام نظام مختلف لإدارة أجهزة المحمول (MDM) ل Microsoft Defender لنقطة النهاية على Mac
description: ثبت Microsoft Defender ل Endpoint على Mac على حلول الإدارة الأخرى.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، التثبيت، النشر، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: c8ffab850302967b9e36e841bf035cef07ad2775
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63573370"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>النشر باستخدام نظام مختلف لإدارة أجهزة المحمول (MDM) ل Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع صفحة [Microsoft Defender ل Endpoint الرئيسية على macOS](microsoft-defender-endpoint-mac.md) للحصول على وصف للمتطلبات الأساسية ومتطلبات النظام الخاصة بالإصدار الحالي للبرنامج.


## <a name="approach"></a>النهج

> [!CAUTION]

> حاليا، تدعم Microsoft رسميا Intune و JAMF فقط لنشر Microsoft Defender ل Endpoint وإدارته على macOS. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات الواردة أدناه.

إذا كانت مؤسستك تستخدم حل إدارة أجهزة المحمول (MDM) غير معتمد رسميا، فهذا لا يعني أنك غير قادر على نشر Microsoft Defender for Endpoint أو تشغيله على macOS.

لا يعتمد Microsoft Defender ل Endpoint على macOS على أي ميزات خاصة بالموردين. يمكن استخدامه مع أي حل MDM يدعم الميزات التالية:

- نشر macOS .pkg على الأجهزة المدارة.
- نشر ملفات تعريف تكوين نظام macOS على الأجهزة المدارة.
- تشغيل أداة/برنامج نصي عشوائي تم تكوينه من قبل المسؤول على الأجهزة المدارة.

تتضمن معظم حلول MDM الحديثة هذه الميزات، ومع ذلك، قد تناديها بشكل مختلف.

يمكنك نشر Defender for Endpoint بدون المتطلب الأخير من القائمة السابقة، ومع ذلك:

- لن تتمكن من تجميع الحالة بطريقة مركزية.
- إذا قررت إلغاء تثبيت Defender ل Endpoint، ستحتاج إلى تسجيل الدخول إلى جهاز العميل محليا كمسؤول.

## <a name="deployment"></a>النشر

تستخدم معظم حلول MDM النموذج نفسه لإدارة أجهزة macOS، مع مصطلحات مماثلة. استخدم [النشر المستند إلى JAMF](mac-install-with-jamf.md) كقالب.

### <a name="package"></a>الحزمة

تكوين نشر حزمة [تطبيق مطلوبة](mac-install-with-jamf.md)، مع تنزيل حزمة التثبيت (wdav.pkg) [من Microsoft 365 Defender المدخل](mac-install-with-jamf.md).

لنشر الحزمة في المؤسسة، استخدم الإرشادات المقترنة بالحل MDM.

### <a name="license-settings"></a>إعدادات الترخيص

إعداد [ملف تعريف تكوين النظام](mac-install-with-jamf.md). 

قد يسميه حل MDM شيئا مثل "ملف الإعدادات تعريف مخصص"، حيث لا يكون Microsoft Defender ل Endpoint على macOS جزءا من macOS.

استخدم قائمة الخاصية، jamf/WindowsDefenderATPOnboarding.plist، التي يمكن استخراجها من حزمة الضم التي تم [تنزيلها من Microsoft 365 Defender المدخل](mac-install-with-jamf.md).
قد يدعم النظام قائمة بممتلكات عشوائية بتنسيق XML. يمكنك تحميل ملف jamf/WindowsDefenderATPOnboarding.plist كما هو في هذه الحالة.
بدلا من ذلك، قد يتطلب منك تحويل قائمة الخاصية إلى تنسيق مختلف أولا.

عادة ما يكون لملف التعريف المخصص الخاص بك سمة المعرف أو الاسم أو المجال. يجب أن تستخدم بالضبط "com.microsoft.wdav.atp" لهذه القيمة.
تستخدمها MDM لنشر ملف الإعدادات إلى **/Library/Managed Preferences/com.microsoft.wdav.atp.plist** على جهاز عميل، ويستخدم Defender for Endpoint هذا الملف لتحميل معلومات الضبط.

### <a name="kernel-extension-policy"></a>نهج ملحق Kernel

إعداد نهج ملحق KEXT أو kernel. استخدم معرف الفريق **UBF8T346G9** للسماح بملحقات kernel التي توفرها Microsoft.

> [!CAUTION]
> إذا كانت بيئتك تتكون من أجهزة Apple Silicon (M1)، يجب ألا تتلقى هذه الأجهزة ملفات تعريف التكوين مع سياسات KEXT.
> لا تدعم Apple KEXT على هذه الأجهزة، وقد يفشل نشر ملف التعريف هذا على أجهزة M1.

### <a name="system-extension-policy"></a>نهج ملحق النظام

إعداد نهج ملحق النظام. استخدم معرف الفريق **UBF8T346G9** ووافق على معرفات المجموعة التالية:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>نهج الوصول إلى القرص الكامل

منح الوصول الكامل إلى القرص الكامل للمكونات التالية:

- Microsoft Defender لنقطة النهاية
    - المعرف: `com.microsoft.wdav`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- ملحق أمان Microsoft Defender لنقطة النهاية
    - المعرف: `com.microsoft.wdav.epsext`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>نهج ملحق الشبكة

كجزء من قدرات الكشف عن نقاط النهاية والاستجابة لها، يفحص Microsoft Defender ل Endpoint على نظام التشغيل macOS حركة مرور مآخذ التوصيل ويعيد Microsoft 365 Defender المدخل. يسمح النهج التالي لملحق الشبكة بتنفيذ هذه الوظيفة.

- نوع عامل التصفية: المكون الإضافي
- معرف مجموعة مكون إضافي: `com.microsoft.wdav`
- معرف مجموعة عوامل تصفية موفر البيانات: `com.microsoft.wdav.netext`
- تصفية المتطلبات المعينة لموفر البيانات: `identifier "com.microsoft.wdav.tunnelext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- مآخذ توصيل التصفية: `true`

## <a name="check-installation-status"></a>التحقق من حالة التثبيت

قم [بتشغيل Microsoft Defender ل Endpoint](mac-install-with-jamf.md) على جهاز عميل للتحقق من حالة التكميل.
