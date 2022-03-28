---
title: إعلامات Microsoft Defender for Identity في Microsoft 365 Defender
description: تعرف على كيفية تعيين إعلامات Microsoft Defender for Identity في Microsoft 365 Defender.
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.openlocfilehash: 4e8969e51673676ecf13dc579ae304622e23e75d
ms.sourcegitcommit: 1de72e5fd8af0ebc4a0dc91f47d2243498cfe5b9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575617"
---
# <a name="defender-for-identity-notifications-in-microsoft-365-defender"></a>Defender for Identity notifications in Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة كيفية العمل مع [إعلامات Microsoft Defender for Identity](/defender-for-identity) [في](/microsoft-365/security/defender/overview-security-center) Microsoft 365 Defender.

> [!IMPORTANT]
> كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="health-issues-notifications"></a>إعلامات مشاكل الصحة

في Microsoft 365 Defender، يمكنك إضافة مستلمين للحصول على إعلامات بالبريد الإلكتروني حول المشاكل الصحية في Defender for Identity.

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

    ![انتقل إلى الإعدادات، ثم الهويات.](../../media/defender-identity/settings-identities.png)

1. حدد **إعلامات مشاكل الصحة**.

1. أدخل عنوان البريد الإلكتروني للمستلم. حدد **إضافة**.

    ![أدخل عنوان البريد الإلكتروني لقضايا الصحة.](../../media/defender-identity/health-email-recipient.png)

1. عندما يكتشف Defender for Identity مشكلة في الصحة، سيتلقى المستلمون إعلاما بالبريد الإلكتروني مع التفاصيل.

    ![مثال على البريد الإلكتروني الخاص مشكلة في الصحة.](../../media/defender-identity/health-email.png)

    > [!NOTE]
    > يوفر البريد الإلكتروني ارتباطين للحصول على مزيد من التفاصيل حول المشكلة. يمكنك إما الانتقال إلى **مركز صحة MDI** أو مركز الصحة **الجديد في M365D**.

## <a name="alert-notifications"></a>إعلامات التنبيهات

في Microsoft 365 Defender، يمكنك إضافة مستلمين لإشعارات البريد الإلكتروني للتنبيهات التي تم الكشف عنها.

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

    ![انتقل إلى الإعدادات، ثم الهويات.](../../media/defender-identity/settings-identities.png)

1. حدد **إعلامات التنبيهات**.

1. أدخل عنوان البريد الإلكتروني للمستلم. حدد **إضافة**.

    ![أدخل عنوان البريد الإلكتروني للتنبيهات التي تم الكشف عنها.](../../media/defender-identity/alert-email-recipient.png)

## <a name="syslog-notifications"></a>إعلامات Syslog

يمكن ل Defender for Identity إعلامك عندما يكشف عن أنشطة مريبة من خلال إرسال تنبيهات الأمان وتنبيهات الأمان إلى خادم Syslog من خلال مستشعر مرشح.

> [!NOTE]
> للتعرف على كيفية دمج Defender for Identity مع Microsoft Sentinel، راجع Microsoft 365 Defender [مع Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

    ![انتقل إلى الإعدادات، ثم الهويات.](../../media/defender-identity/settings-identities.png)

1. حدد **إعلامات Syslog**.

1. لتمكين إعلام syslog، قم بتعيين تبديل خدمة **Syslog** إلى **الموضع عند** .

    ![تشغيل خدمة syslog.](../../media/defender-identity/syslog-service.png)

1. حدد **تكوين الخدمة**. سيتم فتح جزء حيث يمكنك إدخال تفاصيل خدمة syslog.

    ![أدخل تفاصيل خدمة syslog.](../../media/defender-identity/syslog-sensor.png)

1. أدخل التفاصيل التالية:

    - **المستشعر** - من القائمة المنسدل، اختر المستشعر الذي سيرسل التنبيهات.
    - **نقطة نهاية الخدمة** **والميناء** - أدخل عنوان IP أو اسم المجال المؤهل بالكامل (FQDN) للخادم syslog وحدد رقم المنفذ. يمكنك تكوين نقطة نهاية Syslog واحدة فقط.
    - **النقل** - حدد بروتوكول **النقل** (TCP أو UDP).
    - **تنسيق** - حدد التنسيق (RFC 3164 أو RFC 5424).

1. حدد **إرسال إعلام SIEM للاختبار** ثم تحقق من استلام الرسالة في حل البنية الأساسية ل Syslog.

1. حدد **حفظ**.

1. بعد تكوين خدمة **Syslog**، يمكنك اختيار أنواع الإعلامات (التنبيهات أو المشاكل الصحية) التي تريد إرسالها إلى خادم Syslog.

    ![تم تكوين خدمة Syslog.](../../media/defender-identity/syslog-configured.png)

## <a name="see-also"></a>راجع أيضًا

- [إدارة تنبيهات أمان Defender for Identity](manage-security-alerts.md)
