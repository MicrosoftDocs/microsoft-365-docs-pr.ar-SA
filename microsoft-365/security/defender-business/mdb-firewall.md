---
title: جدار الحماية في Microsoft Defender for Business
description: تعرف على Windows Defender Firewall في Microsoft Defender for Business، بما في ذلك إعدادات التكوين
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 77c2042ace89a133b9be8995ef817c1fe3766a07
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861389"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>جدار الحماية في Microsoft Defender for Business

> [!NOTE]
> تم تضمين Microsoft Defender for Business الآن في [Microsoft 365 Business Premium](../../business-premium/index.md). 

يتضمن Microsoft Defender for Business قدرات جدار الحماية مع [جدار حماية Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). تساعد حماية جدار الحماية على تأمين الأجهزة باستخدام القواعد التي تحدد نسبة استخدام الشبكة المسموح لها بإدخالها أو تدفقها من الأجهزة. 

يمكنك استخدام حماية جدار الحماية لتحديد ما إذا كان يجب السماح بالاتصالات أو حظرها على الأجهزة في مواقع مختلفة. على سبيل المثال، يمكن أن تسمح إعدادات جدار الحماية بالاتصالات الواردة على الأجهزة المتصلة بالشبكة الداخلية لشركتك، ولكنها تمنع هذه الاتصالات عندما يكون الجهاز على شبكة مع أجهزة غير موثوق بها.

**تصف هذه المقالة**:

- [إعدادات جدار الحماية الافتراضية في Defender for Business](#default-firewall-settings-in-defender-for-business)
- [إعدادات جدار الحماية التي يمكنك تكوينها في Defender for Business](#firewall-settings-you-can-configure-in-defender-for-business)

>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

## <a name="default-firewall-settings-in-defender-for-business"></a>إعدادات جدار الحماية الافتراضية في Defender for Business

تتضمن Microsoft Defender for Business نهج جدار الحماية الافتراضية وإعداداتها للمساعدة في حماية أجهزة شركتك من اليوم الأول. بمجرد إلحاق أجهزة شركتك Microsoft Defender for Business، يعمل نهج جدار الحماية الافتراضي كما يلي:

- يسمح بالاتصالات الصادرة من الأجهزة بشكل افتراضي، بغض النظر عن الموقع.
- عندما تكون الأجهزة متصلة بشبكة شركتك، يتم حظر جميع الاتصالات الواردة بشكل افتراضي.
- عندما تكون الأجهزة متصلة بشبكة عامة أو شبكة خاصة، يتم حظر كافة الاتصالات الواردة بشكل افتراضي.

في Microsoft Defender for Business، يمكنك تحديد استثناءات لحظر الاتصالات الواردة أو السماح بها. يمكنك تعريف هذه الاستثناءات عن طريق إنشاء قواعد مخصصة. راجع [إدارة القواعد المخصصة لنهج جدار الحماية](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>إعدادات جدار الحماية التي يمكنك تكوينها في Defender for Business

تتضمن Microsoft Defender for Business حماية جدار الحماية من خلال جدار حماية Windows Defender. يسرد الجدول التالي الإعدادات التي يمكن تكوينها لحماية جدار الحماية في Microsoft Defender for Business.

| اعداد | الوصف |
|--|--|
| **شبكة المجال** | ينطبق ملف تعريف شبكة المجال على شبكة شركتك. تنطبق إعدادات جدار الحماية لشبكة المجال على الاتصالات الواردة التي يتم بدئها على أجهزة أخرى موجودة على نفس الشبكة. بشكل افتراضي، يتم تعيين الاتصالات الواردة إلى **"حظر الكل**".  |
| **شبكة عامة** | ينطبق ملف تعريف الشبكة العامة على شبكة يمكنك استخدامها في موقع عام، مثل المقهى أو المطار. تنطبق إعدادات جدار الحماية للشبكات العامة على الاتصالات الواردة التي يتم بدئها على الأجهزة الأخرى الموجودة على نفس الشبكة. نظرا لأن الشبكة العامة يمكن أن تتضمن أجهزة لا تعرفها أو لا تثق بها، يتم تعيين الاتصالات الواردة إلى **"حظر الكل"** بشكل افتراضي.  |
| **شبكة خاصة** | ينطبق ملف تعريف الشبكة الخاصة على شبكة في موقع خاص، مثل منزلك. تنطبق إعدادات جدار الحماية للشبكات الخاصة على الاتصالات الواردة التي يتم بدئها على الأجهزة الأخرى الموجودة على نفس الشبكة. بشكل عام، على شبكة خاصة، من المفترض أن جميع الأجهزة الأخرى على نفس الشبكة هي أجهزة موثوق بها. ومع ذلك، بشكل افتراضي، يتم تعيين الاتصالات الواردة إلى **"حظر الكل**". |
| **القواعد المخصصة** | تسمح لك [القواعد المخصصة](mdb-custom-rules-firewall.md) بحظر اتصالات معينة أو السماح بها. على سبيل المثال، افترض أنك تريد حظر كافة الاتصالات الواردة على الأجهزة المتصلة بشبكة خاصة، باستثناء الاتصالات من خلال تطبيق معين على جهاز. في هذه الحالة، يمكنك تعيين **شبكة خاصة** لحظر كافة الاتصالات الواردة، ثم إضافة قاعدة مخصصة لتعريف الاستثناء. <br/><br/>يمكنك استخدام قواعد مخصصة لتعريف استثناءات لملفات أو تطبيقات معينة أو عنوان بروتوكول إنترنت (IP) أو مجموعة من عناوين IP. <br/><br/>استنادا إلى نوع القاعدة المخصصة التي تقوم بإنشائه، إليك بعض الأمثلة على القيم التي يمكنك استخدامها: <br/><br/>مسار ملف التطبيق: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: عنوان IPv4/IPv6 صالح، مثل `192.168.11.0` أو `192.168.1.0/24` <br/><br/>IP: نطاق عنوان IPv4/IPv6 صالح، منسق مثل `192.168.1.0-192.168.1.9` (مع عدم تضمين مسافات) |

## <a name="next-steps"></a>الخطوات التالية

- [إدارة إعدادات جدار الحماية في Microsoft Defender for Business](mdb-custom-rules-firewall.md)
- [تعرف على المزيد حول جدار حماية Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
- [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)
- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)