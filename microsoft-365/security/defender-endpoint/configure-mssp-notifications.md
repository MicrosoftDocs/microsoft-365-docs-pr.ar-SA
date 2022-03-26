---
title: تكوين إعلامات التنبيهات المرسلة إلى MSSPs
description: تكوين إعلامات التنبيهات المرسلة إلى MSSPs
keywords: موفر خدمة الأمان المدار، mssp، تكوين، تكامل
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0cead78048fcf8ef25637e969aae816b7a8d8e76
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/29/2021
ms.locfileid: "63569852"
---
# <a name="configure-alert-notifications-that-are-sent-to-mssps"></a>تكوين إعلامات التنبيهات المرسلة إلى MSSPs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> يمكن القيام بهذه الخطوة بواسطة عميل MSSP أو MSSP. يجب منح MSSPs الأذونات المناسبة لتكوين هذا نيابة عن عميل MSSP.

بعد منح حق الوصول إلى المدخل، يمكن إنشاء قواعد إعلام التنبيه بحيث يتم إرسال رسائل البريد الإلكتروني إلى MSSPs عند إنشاء التنبيهات المقترنة بالمستأجر والشروط المحددة.

لمزيد من المعلومات، راجع [إنشاء قواعد لإشعارات التنبيهات](configure-email-notifications.md#create-rules-for-alert-notifications).

يجب أن تكون خانات الاختيار هذه محددة:

- **تضمين اسم المؤسسة** - سيضاف اسم العميل إلى إعلامات البريد الإلكتروني
- **تضمين ارتباط مدخل خاص** ب المستأجر - سيتضمن URL ارتباط التنبيه معلمة خاصة للمستأجر (tid=target_tenant_id) تسمح بالوصول المباشر إلى مدخل المستأجر الهدف

## <a name="related-topics"></a>المواضيع ذات الصلة

- [منح MSSP حق الوصول إلى المدخل](grant-mssp-access.md)
- [الوصول إلى مدخل عميل MSSP](access-mssp-portal.md)
- [إحضار التنبيهات من مستأجر العملاء](fetch-alerts-mssp.md)
