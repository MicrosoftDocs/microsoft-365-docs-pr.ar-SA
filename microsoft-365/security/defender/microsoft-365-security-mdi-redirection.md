---
title: إعادة توجيه الحسابات من Microsoft Defender for Identity إلى Microsoft 365 Defender
description: كيفية إعادة توجيه الحسابات والجلسات من Defender for Identity إلى Microsoft 365 Defender.
keywords: Microsoft 365 Defender، بدء استخدام Microsoft 365 Defender، إعادة توجيه مركز الأمان
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: b5c122f01d37d066e0f20bf817ca45ad5c57480b
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "66857358"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-identity-to-microsoft-365-defender"></a>إعادة توجيه الحسابات من Microsoft Defender for Identity إلى Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

يشرح هذا الدليل كيفية توجيه الحسابات إلى Microsoft 365 Defender عن طريق تمكين إعادة التوجيه التلقائي من مدخل Microsoft Defender for Identity السابق (portal.atp.azure.com)، إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

## <a name="what-to-expect"></a>ما يجب توقعه

بمجرد تمكين إعادة التوجيه التلقائي، سيتم توجيه الحسابات التي تصل إلى مدخل Microsoft Defender for Identity السابق في portal.atp.azure.com تلقائيا إلى مدخل Microsoft 365 Defender في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">security.microsoft.com</a>.

## <a name="when-does-this-take-effect"></a>متى يدخل هذا الإجراء حيز التنفيذ؟

بمجرد تمكينه، قد يدخل هذا التحديث حيز التنفيذ على الفور تقريبا لبعض الحسابات. ولكن قد تستغرق إعادة التوجيه وقتا أطول ليتم نشرها إلى كل حساب في مؤسستك. لن يتم إخراج الحسابات في جلسات العمل النشطة أثناء تطبيق هذا الإعداد من جلسة العمل الخاصة بها وسيتم توجيهها فقط إلى Microsoft 365 Defender بعد إنهاء جلسة العمل الحالية وتسجيل الدخول مرة أخرى.  

### <a name="set-up-portal-redirection"></a>إعداد إعادة توجيه المدخل

لبدء توجيه الحسابات إلى Microsoft 365 Defender:

1. تأكد من أنك مسؤول عام أو لديك أذونات مسؤول الأمان في Azure Active Directory.

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

1. انتقل إلى **إعادة توجيه** المدخل **العام** > **للهويات الإعدادات** >  >  أو [انقر هنا](https://security.microsoft.com/preferences2/portal_redirection).

    :::image type="content" source="../../media/portal-redirection.png" alt-text="إعادة توجيه المدخل."lightbox="../../media/portal-redirection.png":::

1. قم بتبديل إعداد إعادة التوجيه التلقائي إلى **"تشغيل**".

>[!IMPORTANT]
>لن يؤدي تمكين هذا الإعداد إلى إنهاء جلسات عمل المستخدم النشطة. سيتم توجيه الحسابات التي تعمل في جلسة عمل نشطة أثناء تطبيق هذا الإعداد فقط إلى Microsoft 365 Defender بعد إنهاء جلسة العمل الحالية وتسجيل الدخول مرة أخرى.

>[!NOTE]
>يجب أن تكون مسؤولا عاما أو لديك أذونات مسؤول الأمان في Azure Active Directory لتمكين هذا الإعداد أو تعطيله.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>هل يمكنني العودة إلى استخدام المدخل السابق؟

إذا لم يكن هناك شيء يعمل من أجلك أو إذا كان هناك أي شيء لا يمكنك إكماله من خلال Microsoft 365 Defender، نريد أن نسمع عنه. إذا واجهت أي مشاكل في إعادة التوجيه، فنحن نشجعك على إعلامنا باستخدام نموذج تقديم الملاحظات.

للعودة إلى مدخل Microsoft Defender for Identity السابق:

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> كمسؤول عام أو باستخدام أذونات مسؤول الأمان في Azure Active directory وحسابها.

2. انتقل إلى **إعادة توجيه** المدخل **العام** > **للهويات الإعدادات** >  >  أو [افتح الصفحة هنا](https://security.microsoft.com/preferences2/portal_redirection).  

3. قم بتبديل إعداد إعادة التوجيه التلقائي إلى **إيقاف التشغيل**.

يمكن تمكين هذا الإعداد مرة أخرى في أي وقت.

بمجرد التعطيل، لن يتم توجيه الحسابات إلى security.microsoft.com.

## <a name="related-information"></a>المعلومات ذات الصلة

- [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md)
- [حول Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender)
- [بوابات الأمان ومراكز الإدارة في Microsoft](portals.md)
