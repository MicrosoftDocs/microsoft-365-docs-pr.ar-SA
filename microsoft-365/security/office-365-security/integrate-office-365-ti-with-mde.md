---
title: استخدم Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية
f1.keywords:
- NOCSH
keywords: تكامل، Microsoft Defender، Microsoft Defender لنقطة النهاية
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
description: استخدم Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية للحصول على معلومات أكثر تفصيلا حول التهديدات التي تواجه أجهزتك ومحتوى البريد الإلكتروني.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ef1f89a9b218e559855789d0beabad1bc947dad1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465916"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>استخدم Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Microsoft Defender لـ Office 365](defender-for-office-365.md) تكوينها [للعمل مع Microsoft Defender لنقطة النهاية](/windows/security/threat-protection).

يمكن Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية المساعدة في مراقبة فريق عمليات الأمان واتخاذ الإجراءات بسرعة إذا كانت أجهزة المستخدمين معرضة للخطر. على سبيل المثال، بعد تمكين التكامل، سيكون فريق عمليات الأمان قادرا على رؤية الأجهزة التي من المحتمل أن تتأثر برسالة بريد إلكتروني تم الكشف عنها، بالإضافة إلى عدد التنبيهات الأخيرة التي تم إنشاؤها لتلك الأجهزة في Microsoft Defender لنقطة النهاية.

تصف الصورة التالية شكل علامة التبويب الأجهزة  عند تمكين Microsoft Defender لنقطة النهاية الأجهزة:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="قائمة بالأجهزة التي تتضمن تنبيهات" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

في هذا المثال، يمكنك رؤية أن مستلمي رسالة البريد الإلكتروني التي تم الكشف عنها لديهم أربعة أجهزة وتنبيه واحد. يؤدي النقر فوق الارتباط لجهاز إلى فتح الصفحة الخاصة به في Microsoft 365 Defender [المدخل](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> يستبدل Microsoft 365 Defender المدخل مركز حماية Microsoft Defender. راجع [Microsoft Defender لنقطة النهاية في Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>المتطلبات

- يجب أن يكون لدى مؤسستك Microsoft Defender لـ Office 365 (أو Office 365 E5) Microsoft Defender لنقطة النهاية.

- يجب تعيين دور مسؤول الأمان أو المسؤول العام في Microsoft 365. لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).

- يجب أن يكون لديك حق الوصول إلى [المستكشف (أو الكشف في الوقت الحقيقي)](threat-explorer.md).

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>لدمج Microsoft Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية

تم Microsoft Defender لـ Office 365 دمج Microsoft Defender لنقطة النهاية في كل من Defender for Endpoint Defender لـ Office 365.

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. انتقل إلى **البريد الإلكتروني & مستكشف** \> **التعاون**. 

3. في صفحة **المستكشف**، في الزاوية العلوية اليسرى من الشاشة، حدد **MDE** الإعدادات.

3. في **Microsoft Defender لنقطة النهاية الاتصال** التي تظهر، قم **الاتصال** إلى Microsoft Defender لنقطة النهاية (![تشغيل).](../../media/scc-toggle-on.png)) ثم حدد **إغلاق**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="صفحة اتصال MDE" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. في جزء التنقل **، اختر الإعدادات**. في صفحة **الإعدادات**، اختر **نقاط النهاية**

5. في **صفحة نقاط النهاية** التي تفتح، اختر **الميزات المتقدمة**.

6. قم بالتمرير **لأسفل Office 365 اتصال "المعلومات الاستخبارية للتهديدات**"، ثم قم ب تشغيله (![قم بالتمرير إلى تشغيل).](../../media/scc-toggle-on.png)).

   عند الانتهاء، حدد **حفظ التفضيلات**.

## <a name="see-also"></a>راجع أيضًا

[قدرات التحقيق في المخاطر والاستجابة لها في Office 365](office-365-ti.md)

[Microsoft Defender لـ Office 365](defender-for-office-365.md)

[Microsoft Defender لنقطة النهاية](/windows/security/threat-protection)
