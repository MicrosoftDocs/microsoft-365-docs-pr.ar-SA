---
title: تقييم حماية الشبكة
description: تعرف على كيفية عمل حماية الشبكة من خلال اختبار السيناريوهات الشائعة التي تحميها.
keywords: حماية الشبكة، استغلالات، موقع ويب ضار، ip، مجال، مجالات، تقييم، اختبار، عرض توضيحي
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365solution-scenario
ms.date: ''
ms.openlocfilehash: fb46d0c03aaaaad016ca13be5bfa26a19887794c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63571476"
---
# <a name="evaluate-network-protection"></a>تقييم حماية الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[تساعد حماية](network-protection.md) الشبكة على منع الموظفين من استخدام أي تطبيق للوصول إلى مجالات خطيرة قد تستضيف رسائل التصيد الاحتيالي والمستغلين والمحتويات الضارة الأخرى على الإنترنت.

تساعدك هذه المقالة على تقييم حماية الشبكة من خلال تمكين الميزة وتوجيهك إلى موقع اختبار. المواقع في مقالة التقييم هذه ليست ضارة. إنها مواقع ويب تم إنشاؤها خصيصا وتدعي أنها ضارة. سيكرر الموقع السلوك الذي قد يحدث إذا قام مستخدم بزيارة موقع أو مجال ضار.

> [!TIP]
> يمكنك أيضا زيارة موقع سيناريوهات العرض التوضيحي ل Microsoft [Defender على demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لمعرفة كيفية عمل ميزات الحماية الأخرى.

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

## <a name="enable-network-protection-in-audit-mode"></a>تمكين حماية الشبكة في وضع التدقيق

تمكين حماية الشبكة في وضع التدقيق لمعرفة عناوين IP والمجالات التي سيتم حظرها. يمكنك التأكد من عدم تأثيره على تطبيقات خط العمل، أو الحصول على فكرة حول عدد مرات حدوث الكتل.

1. اكتب **powershell** في قائمة البدء، وانقر ب الماوس **الأيمن فوق Windows PowerShell** وحدد **تشغيل كمسؤول**
2. أدخل cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>زيارة مجال ضار (زائف)

1. افتح Internet Explorer أو Google Chrome أو أي مستعرض آخر من اختيارك.

2. انتقل إلى [https://smartscreentestratings2.net](https://smartscreentestratings2.net).

    سيتم السماح باتصال الشبكة وستعرض رسالة اختبار.
    
    ![مثال إعلام يفيد بحظر الاتصال: تسبب مسؤول تكنولوجيا المعلومات أمن Windows لحظر اتصال الشبكة هذا. اتصل بمكتب المساعدة في IT.](images/np-notif.png)

> [!NOTE]
> يمكن أن تكون اتصالات الشبكة ناجحة على الرغم من حظر الموقع بواسطة حماية الشبكة. لمعرفة المزيد، راجع [حماية الشبكة ومصافحة TCP ثلاثية.](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

## <a name="review-network-protection-events-in-windows-event-viewer"></a>مراجعة أحداث حماية الشبكة في Windows الحدث

لمراجعة التطبيقات التي كان سيتم حظرها، افتح "عارض الأحداث" وتصفية "لمعر 1125 الحدث" في سجل Microsoft-Windows-Windows Defender/التشغيلية. يسرد الجدول التالي كل أحداث حماية الشبكة.

| "معرّف الحدث" | توفير/مصدر | الوصف |
|---|---|---|
| 5007 | Windows Defender (التشغيل) | حدث عند تغيير الإعدادات |
| 1125 | Windows Defender (التشغيل) | حدث عند تدقيق اتصال شبكة |
| 1126 | Windows Defender (التشغيل) | حدث عند حظر اتصال شبكة |

## <a name="see-also"></a>راجع أيضًا

- [حماية الشبكة](network-protection.md)

- [حماية الشبكة ومصافحة TCP ثلاثية](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [تمكين حماية الشبكة](enable-network-protection.md)

- [استكشاف مشاكل حماية الشبكة وإصلاحها](troubleshoot-np.md)
