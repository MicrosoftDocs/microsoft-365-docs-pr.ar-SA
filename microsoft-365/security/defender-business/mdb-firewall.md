---
title: جدار الحماية في Microsoft Defender for Business
description: تعرف على Windows Defender في Microsoft Defender for Business، بما في ذلك إعدادات التكوين
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 92db1711fa5aefb8920c35a8665cf322b3f0f5ef
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63578581"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>جدار الحماية في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

يتضمن Microsoft Defender for Business قدرات جدار الحماية [Windows جدار الحماية ل Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). تساعد حماية جدار الحماية على حماية الأجهزة باستخدام القواعد التي تحدد حركة مرور الشبكة المسموح بإدخالها أو تدفقها من الأجهزة. 

يمكنك استخدام حماية جدار الحماية لتحديد ما إذا كنت تريد السماح بالاتصالات أو حظرها على الأجهزة في مواقع مختلفة. على سبيل المثال، يمكن أن تسمح إعدادات جدار الحماية للاتصالات الواردة على الأجهزة المتصلة بالشبكة الداخلية للشركة، ولكنها تمنع هذه الاتصالات عندما يكون الجهاز على شبكة مع أجهزة غير صحيحة.

**تصف هذه المقالة**:

- [إعدادات جدار الحماية الافتراضية في Defender for Business](#default-firewall-settings-in-defender-for-business)

- [إعدادات جدار الحماية التي يمكنك تكوينها في Defender for Business](#firewall-settings-you-can-configure-in-defender-for-business)

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="default-firewall-settings-in-defender-for-business"></a>إعدادات جدار الحماية الافتراضية في Defender for Business

يتضمن Microsoft Defender for Business إعدادات ونهج جدار الحماية الافتراضية للمساعدة في حماية أجهزة شركتك من اليوم الأول. بمجرد أن يتم استخدام أجهزة شركتك في Microsoft Defender for Business، يعمل نهج جدار الحماية الافتراضي كما يلي:

- يتم السماح للاتصالات الصادرة من الأجهزة بشكل افتراضي، بغض النظر عن الموقع.
- عندما تكون الأجهزة متصلة بشبكة شركتك، يتم حظر كل الاتصالات الواردة بشكل افتراضي.
- عندما تكون الأجهزة متصلة بشبكة عامة أو بشبكة خاصة، يتم حظر كل الاتصالات الواردة بشكل افتراضي.

في Microsoft Defender for Business، يمكنك تعريف استثناءات لحظر الاتصالات الواردة أو السماح بها. يمكنك تعريف هذه الاستثناءات عن طريق إنشاء قواعد مخصصة. راجع [إدارة القواعد المخصصة لنهج جدار الحماية](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>إعدادات جدار الحماية التي يمكنك تكوينها في Defender for Business

يتضمن Microsoft Defender for Business حماية جدار الحماية Windows جدار الحماية ل Defender. يسرد الجدول التالي الإعدادات التي يمكن تكوينها لحماية جدار الحماية في Microsoft Defender for Business. <br/><br/>

| الإعداد | الوصف |
|--|--|
| **شبكة المجال** | ينطبق ملف تعريف شبكة المجال على شبكة الشركة. تنطبق إعدادات جدار الحماية لشبكة مجالك على الاتصالات الواردة التي يتم بدءها على أجهزة أخرى على الشبكة نفسها. بشكل افتراضي، يتم تعيين الاتصالات الواردة إلى **حظر الكل**.  |
| **الشبكة العامة** | ينطبق ملف تعريف الشبكة العامة على شبكة يمكنك استخدامها في موقع عام، مثل مقهى أو مطار. تنطبق إعدادات جدار الحماية للشبكات العامة على الاتصالات الواردة التي يتم بدءها على أجهزة أخرى على الشبكة نفسها. نظرا لأن الشبكة العامة قد تتضمن أجهزة لا تعرفها أو لا تثق بها، يتم تعيين الاتصالات الواردة إلى **حظر الكل** بشكل افتراضي.  |
| **شبكة خاصة** | ينطبق ملف تعريف الشبكة الخاص على شبكة في موقع خاص، مثل الصفحة الرئيسية. تنطبق إعدادات جدار الحماية للشبكات الخاصة على الاتصالات الواردة التي يتم بدءها على أجهزة أخرى على الشبكة نفسها. بشكل عام، على شبكة خاصة، من المفترض أن جميع الأجهزة الأخرى على الشبكة نفسها هي أجهزة موثوق بها. ومع ذلك، بشكل افتراضي، يتم تعيين الاتصالات الواردة إلى **حظر الكل**. |
| **القواعد المخصصة** | [تسمح لك](mdb-custom-rules-firewall.md) القواعد المخصصة بحظر اتصالات معينة أو السماح بها. على سبيل المثال، افترض أنك تريد حظر كل الاتصالات الواردة على الأجهزة المتصلة بشبكة خاصة، باستثناء الاتصالات عبر تطبيق معين على جهاز. في هذه الحالة، يمكنك تعيين شبكة **خاصة** لحظر كل الاتصالات الواردة، ثم إضافة قاعدة مخصصة لتعريف الاستثناء. <br/><br/>يمكنك استخدام القواعد المخصصة لتعريف استثناءات لملفات أو تطبيقات معينة أو عنوان بروتوكول الإنترنت (IP) أو نطاق من عناوين IP. <br/><br/>استنادا إلى نوع القاعدة المخصصة التي تقوم بإنشاءها، فيما يلي بعض الأمثلة على القيم التي يمكنك استخدامها: <br/><br/>مسار ملف التطبيق: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: عنوان IPv4/IPv6 صالح، مثل `192.168.1.0` أو `192.168.1.0/24` <br/><br/>IP: نطاق عناوين IPv4/IPv6 صالح، تم تنسيقه مثل `192.168.1.0-192.168.1.9` (بدون أي مسافات مضمنة) |

## <a name="next-steps"></a>الخطوات التالية

- [إدارة إعدادات جدار الحماية في Microsoft Defender for Business](mdb-custom-rules-firewall.md)

- [معرفة المزيد حول Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)