---
title: تقييم حماية الشبكة
description: تعرف على كيفية عمل حماية الشبكة عن طريق اختبار السيناريوهات الشائعة التي تحمي منها.
keywords: حماية الشبكة، مهاجمات، موقع ويب ضار، ip، مجال، مجالات، تقييم، اختبار، عرض توضيحي
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
ms.collection:
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 4c9c0618db34df38168dca881117288832abf4a5
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717835"
---
# <a name="evaluate-network-protection"></a>تقييم حماية الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

تساعد [حماية الشبكة](network-protection.md) الموظفين على منع الموظفين من استخدام أي تطبيق للوصول إلى المجالات الخطرة التي قد تستضيف رسائل التصيد الاحتيالي وعمليات الاستغلال والمحتوى الضار الآخر على الإنترنت.

تساعدك هذه المقالة على تقييم حماية الشبكة من خلال تمكين الميزة وتوجيهك إلى موقع اختبار. المواقع الموجودة في مقالة التقييم هذه ليست ضارة. إنها مواقع ويب تم إنشاؤها بشكل خاص تتظاهر بأنها ضارة. سيقوم الموقع بنسخ السلوك الذي قد يحدث إذا قام مستخدم بزيارة موقع أو مجال ضار.

## <a name="enable-network-protection-in-audit-mode"></a>تمكين حماية الشبكة في وضع التدقيق

تمكين حماية الشبكة في وضع التدقيق لمعرفة عناوين IP والمجالات التي كان سيتم حظرها. يمكنك التأكد من أنه لا يؤثر على تطبيقات خط العمل، أو الحصول على فكرة عن عدد مرات حدوث الكتل.

1. اكتب **powershell** في قائمة البدء، وانقر بزر **الماوس الأيمن فوق Windows PowerShell** وحدد **"تشغيل كمسؤول"**
2. أدخل cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

### <a name="visit-a-fake-malicious-domain"></a>زيارة مجال ضار (مزيف)

1. افتح Internet Explorer أو Google Chrome أو أي مستعرض آخر من اختيارك.

2. الانتقال إل [https://smartscreentestratings2.net](https://smartscreentestratings2.net)

    سيتم السماح باتصال الشبكة وسيتم عرض رسالة اختبار.
    
    :::image type="content" source="images/np-notif.png" alt-text="إعلام حظر الاتصال" lightbox="images/np-notif.png":::

> [!NOTE]
> يمكن أن تكون اتصالات الشبكة ناجحة على الرغم من حظر موقع بواسطة حماية الشبكة. لمعرفة المزيد، راجع [حماية الشبكة والتصاق TCP ثلاثي الاتجاهات](network-protection.md#network-protection-and-the-tcp-three-way-handshake).

## <a name="review-network-protection-events-in-windows-event-viewer"></a>مراجعة أحداث حماية الشبكة في Windows عارض الأحداث

لمراجعة التطبيقات التي كان سيتم حظرها، افتح عارض الأحداث وقم بالتصفية لمعرف الحدث 1125 في سجل Microsoft-Windows-Windows Defender/Operational. يسرد الجدول التالي كافة أحداث حماية الشبكة.

| معرف الحدث | توفير/مصدر | الوصف |
|---|---|---|
| 5007 | Windows Defender (تشغيلي) | حدث عند تغيير الإعدادات |
| 1125 | Windows Defender (تشغيلي) | حدث عند تدقيق اتصال الشبكة |
| 1126 | Windows Defender (تشغيلي) | حدث عند حظر اتصال الشبكة |

## <a name="see-also"></a>راجع أيضًا

- [حماية الشبكة](network-protection.md)

- [حماية الشبكة والتصاق TCP ثلاثي الاتجاهات](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [تمكين حماية الشبكة](enable-network-protection.md)

- [استكشاف أخطاء حماية الشبكة وإصلاحها](troubleshoot-np.md)
