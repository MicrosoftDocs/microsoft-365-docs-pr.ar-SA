---
title: Microsoft Defender for Identity الإعلامات في Microsoft 365 Defender
description: تعرف على كيفية تعيين Microsoft Defender for Identity الإعلامات في Microsoft 365 Defender.
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 89ed7ae50bf89c28bde81ea02e8905d0056ede53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470912"
---
# <a name="defender-for-identity-notifications-in-microsoft-365-defender"></a>Defender for Identity notifications in Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة كيفية العمل مع [Microsoft Defender for Identity الإعلامات](/defender-for-identity) في [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="health-issues-notifications"></a>إعلامات مشاكل الصحة

في Microsoft 365 Defender، يمكنك إضافة مستلمين للحصول على إعلامات بالبريد الإلكتروني حول المشاكل الصحية في Defender for Identity.

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

  :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="الخيار &quot;الهويات&quot; في العمود &quot;اسم&quot;" lightbox="../../media/defender-identity/settings-identities.png":::


1. حدد **إعلامات مشاكل الصحة**.

1. أدخل عنوان البريد الإلكتروني للمستلم. حدد **إضافة**.

   :::image type="content" source="../../media/defender-identity/health-email-recipient.png" alt-text="عنصر القائمة الفرعية إعلامات مشاكل الصحة" lightbox="../../media/defender-identity/health-email-recipient.png":::

1. عندما يكتشف Defender for Identity مشكلة في الصحة، سيتلقى المستلمون إعلاما بالبريد الإلكتروني مع التفاصيل.

   :::image type="content" source="../../media/defender-identity/health-email.png" alt-text="البريد الإلكتروني الخاص مشكلة الصحة" lightbox="../../media/defender-identity/health-email.png":::

    > [!NOTE]
    > يوفر البريد الإلكتروني ارتباطين للحصول على مزيد من التفاصيل حول المشكلة. يمكنك إما الانتقال إلى **مركز صحة MDI** أو مركز الصحة **الجديد في M365D**.

## <a name="alert-notifications"></a>إعلامات التنبيهات

في Microsoft 365 Defender، يمكنك إضافة مستلمين لإشعارات البريد الإلكتروني للتنبيهات التي تم الكشف عنها.

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="الخيار &quot;الهويات&quot;" lightbox="../../media/defender-identity/settings-identities.png":::

1. حدد **إعلامات التنبيهات**.

1. أدخل عنوان البريد الإلكتروني للمستلم. حدد **إضافة**.

   :::image type="content" source="../../media/defender-identity/alert-email-recipient.png" alt-text="عنصر القائمة الفرعية إعلامات التنبيه" lightbox="../../media/defender-identity/alert-email-recipient.png":::

## <a name="syslog-notifications"></a>إعلامات Syslog

يمكن ل Defender for Identity إعلامك عندما يكشف عن أنشطة مريبة من خلال إرسال تنبيهات الأمان وتنبيهات الأمان إلى خادم Syslog من خلال مستشعر مرشح.

> [!NOTE]
> للتعرف على كيفية دمج Defender for Identity مع Microsoft Sentinel، راجع Microsoft 365 Defender [مع Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="خيار الهويات في العمود &quot;الاسم&quot;" lightbox="../../media/defender-identity/settings-identities.png":::

1. حدد **إعلامات Syslog**.

1. لتمكين إعلام syslog، قم بتعيين تبديل خدمة **Syslog** إلى **الموضع عند** .

   :::image type="content" source="../../media/defender-identity/syslog-service.png" alt-text="خيار خدمة Syslog الذي يمكن تشغيله" lightbox="../../media/defender-identity/syslog-service.png":::

1. حدد **تكوين الخدمة**. سيتم فتح جزء حيث يمكنك إدخال تفاصيل خدمة syslog.

   :::image type="content" source="../../media/defender-identity/syslog-sensor.png" alt-text="الصفحة التي تدخل فيها تفاصيل خدمة Syslog" lightbox="../../media/defender-identity/syslog-sensor.png":::

1. أدخل التفاصيل التالية:

    - **المستشعر** - من القائمة المنسدل، اختر المستشعر الذي سيرسل التنبيهات.
    - **نقطة نهاية الخدمة** **والميناء** - أدخل عنوان IP أو اسم المجال المؤهل بالكامل (FQDN) للخادم syslog وحدد رقم المنفذ. يمكنك تكوين نقطة نهاية Syslog واحدة فقط.
    - **النقل** - حدد بروتوكول **النقل** (TCP أو UDP).
    - **تنسيق** - حدد التنسيق (RFC 3164 أو RFC 5424).

1. حدد **إرسال إعلام SIEM للاختبار** ثم تحقق من استلام الرسالة في حل البنية الأساسية ل Syslog.

1. حدد **حفظ**.

1. بعد تكوين خدمة **Syslog**، يمكنك اختيار أنواع الإعلامات (التنبيهات أو المشاكل الصحية) التي تريد إرسالها إلى خادم Syslog.

   :::image type="content" source="../../media/defender-identity/syslog-configured.png" alt-text="تم تحديد الخيار &quot;تم تكوين خدمة Syslog&quot;" lightbox="../../media/defender-identity/syslog-configured.png":::

## <a name="see-also"></a>راجع أيضًا

- [إدارة تنبيهات أمان Defender for Identity](manage-security-alerts.md)
