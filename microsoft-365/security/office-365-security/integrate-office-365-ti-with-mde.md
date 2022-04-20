---
title: استخدام Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية
f1.keywords:
- NOCSH
keywords: التكامل، وMicrosoft Defender، Microsoft Defender لنقطة النهاية
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 12/02/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: استخدم Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية للحصول على معلومات أكثر تفصيلا حول التهديدات التي تتعرض لها أجهزتك ومحتوى البريد الإلكتروني.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8df364538e6a799557956a8d624b0561c626e4fd
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971099"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>استخدام Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

يمكن تكوين [Microsoft Defender لـ Office 365](defender-for-office-365.md) للعمل مع [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection).

يمكن أن يساعد دمج Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية فريق عمليات الأمان على مراقبة واتخاذ الإجراءات بسرعة إذا كانت أجهزة المستخدمين في خطر. على سبيل المثال، بمجرد تمكين التكامل، سيتمكن فريق عمليات الأمان من رؤية الأجهزة التي يحتمل أن تتأثر برسالة بريد إلكتروني تم اكتشافها، بالإضافة إلى عدد التنبيهات الأخيرة التي تم إنشاؤها لهذه الأجهزة في Microsoft Defender لنقطة النهاية.

تصور الصورة التالية الشكل الذي تبدو عليه علامة التبويب **"الأجهزة**" عند تمكين تكامل Microsoft Defender لنقطة النهاية:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="قائمة بالأجهزة التي تحتوي على تنبيهات" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

في هذا المثال، يمكنك أن ترى أن مستلمي رسالة البريد الإلكتروني المكتشفة لديهم أربعة أجهزة وواحد لديه تنبيه. يؤدي النقر فوق الارتباط لجهاز إلى فتح صفحته في [مدخل Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> يستبدل مدخل Microsoft 365 Defender مركز حماية Microsoft Defender. راجع [Microsoft Defender لنقطة النهاية في Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>الاحتياجات

- يجب أن يكون لدى مؤسستك Microsoft Defender لـ Office 365 (أو Office 365 E5) Microsoft Defender لنقطة النهاية.

- يجب أن يكون لديك دور المسؤول العام أو مسؤول الأمان المعين في Microsoft 365. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- يجب أن يكون لديك حق الوصول إلى [Explorer (أو عمليات الكشف في الوقت الحقيقي).](threat-explorer.md)

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>لدمج Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية

يتم إعداد دمج Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية في كل من Defender لنقطة النهاية Defender لـ Office 365.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. انتقل إلى **مستكشف** التعاون \> **& البريد الإلكتروني**.

3. في صفحة **المستكشف**، في الزاوية العلوية اليسرى من الشاشة، حدد **MDE الإعدادات**.

3. في **القائمة المنبثقة للاتصال Microsoft Defender لنقطة النهاية** التي تظهر، قم بتشغيل **الاتصال إلى Microsoft Defender لنقطة النهاية** (![التبديل.](../../media/scc-toggle-on.png)) ثم حدد **"إغلاق**".

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="صفحة اتصال MDE" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. في جزء التنقل، اختر **الإعدادات**. في صفحة **الإعدادات**، اختر **نقاط النهاية**

5. في صفحة **نقاط النهاية** التي يتم فتحها، اختر **الميزات المتقدمة**.

6. قم بالتمرير لأسفل **Office 365 اتصال تحليل ذكي للمخاطر**، ثم قم بتشغيله (![تشغيل.](../../media/scc-toggle-on.png)).

   عند الانتهاء، حدد **"حفظ التفضيلات**".

## <a name="see-also"></a>راجع أيضًا

[قدرات التحقيق في التهديدات والاستجابة لها في Office 365](office-365-ti.md)

[Microsoft Defender لـ Office 365](defender-for-office-365.md)

[مشكلات الأداء في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection)
