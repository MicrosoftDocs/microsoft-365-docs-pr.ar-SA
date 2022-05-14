---
title: الاستجابة لموصل تم اختراقه في Microsoft 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: تعرف على كيفية التعرف على موصل تم اختراقه والاستجابة له في Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6f32f9960655c8998abd8d9fb8fa939368373520
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419013"
---
# <a name="respond-to-a-compromised-connector"></a>الاستجابة إلى موصل مُخترق

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**

- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يتم استخدام الموصلات لتمكين تدفق البريد بين خوادم Microsoft 365 أو Office 365 والبريد الإلكتروني المتوفرة لديك في البيئة المحلية. لمزيد من المعلومات، راجع [تكوين تدفق البريد باستخدام الموصلات في Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

يتم تعريف الموصل الوارد الذي تم اختراقه على أنه عندما يقوم شخص غير مصرح له إما بتطبيق التغيير (التغييرات) على موصل وارد موجود أو إنشاء موصل وارد جديد في مستأجر Microsoft 365، بهدف إرسال رسائل البريد الإلكتروني غير المرغوب فيها أو التصيد الاحتيالي. لاحظ أن هذا ينطبق فقط على الموصلات الواردة من النوع OnPremises. 

## <a name="detect-a-compromised-connector"></a>الكشف عن موصل تم اختراقه

فيما يلي بعض خصائص الموصل المخترق:

- زيادة مفاجئة في مستوى صوت البريد الصادر. 

- عدم التطابق بين مرسلي P1 وP2 في رسائل البريد الصادرة. لمزيد من المعلومات حول مرسلي P1 وP2، راجع [كيف يتحقق EOP من صحة عنوان "من" لمنع التصيد الاحتيالي](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

- رسائل البريد الصادرة المرسلة من مجال غير متوفر أو مسجل. 

- تم حظر الموصل من إرسال البريد المرحل. 

- لم يتم إنشاء وجود موصل وارد من قبل المستخدم المقصود أو المسؤول. 

- تغيير (تغييرات) غير مصرح به في تكوين الموصل الحالي، مثل الاسم واسم المجال وعنوان IP. 

- حساب مسؤول تم اختراقه مؤخرا. لاحظ أنه يمكنك تحرير تكوين الموصل فقط إذا كان لديك حق الوصول الإداري. 

## <a name="secure-and-restore-email-function-to-a-suspected-compromised-connector"></a>تأمين وظيفة البريد الإلكتروني واستعادتها إلى موصل مخترق مشتبه به

يجب إكمال جميع الخطوات التالية لاستعادة الوصول إلى الموصل الخاص بك. تساعدك هذه الخطوات على إزالة أي إدخالات خلفية قد تكون تمت إضافتها إلى الموصل.

### <a name="step-1-identify-if-an-inbound-connector-has-been-compromised"></a>الخطوة 1: تحديد ما إذا تم اختراق موصل وارد 

#### <a name="review-recent-suspicious-connector-traffic-or-related-messages"></a>مراجعة حركة مرور الموصل المريبة الأخيرة أو الرسائل ذات الصلة

إذا كان لديك [Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md)، فانتقل مباشرة إلى https://security.microsoft.com/threatexplorer. 

1. حدد **الموصل**، وأدرج **"اسم الموصل**"، وحدد نطاق التاريخ، ثم انقر فوق **"تحديث**". 

    :::image type="content" source="../../media/connector-compromise-explorer.png" alt-text="طريقة عرض مستكشف الموصلات الواردة" lightbox="../../media/connector-compromise-explorer.png":::

2. تحديد ما إذا كان هناك أي ارتفاع غير طبيعي أو انخفاض في نسبة استخدام الشبكة للبريد الإلكتروني.

    :::image type="content" source="../../media/connector-compromise-abnormal-spike.png" alt-text="عدد رسائل البريد الإلكتروني التي تم تسليمها إلى مجلد غير هام" lightbox="../../media/connector-compromise-abnormal-spike.png":::

3. تحديد: 

    - إذا تطابق **عنوان IP المرسل** مع عنوان IP المحلي لمؤسستك. 

    - إذا تم إرسال عدد كبير من رسائل البريد الإلكتروني مؤخرا إلى مجلد **"البريد غير الهام** ". هذا مؤشر جيد لموصل تم اختراقه يتم استخدامه لإرسال البريد العشوائي. 

    - إذا كان المستلمون هم المستلمون الذين تظل مؤسستك على اتصال بهم عادة. 

    :::image type="content" source="../../media/connector-compromise-sender-ip.png" alt-text="عنوان IP للمرسل وعنوان IP المحلي لمؤسستك" lightbox="../../media/connector-compromise-sender-ip.png":::

إذا كان لديك [Microsoft Defender لـ Office 365 الخطة 1](defender-for-office-365.md) أو [Exchange Online Protection](exchange-online-protection-overview.md)، فانتقل إلى https://admin.exchange.microsoft.com/#/messagetrace. 

1. افتح تنبيه **نشاط الموصل المشبوه** في https://security.microsoft.com/alerts.  

2. حدد نشاطا ضمن **قائمة النشاط**، وانسخ **مجال الموصل** المشبوه **وعنوان IP** المكتشفين في التنبيه.

    :::image type="content" source="../../media/connector-compromise-outbound-email-details.png" alt-text="موصل يخترق تفاصيل البريد الإلكتروني الصادر" lightbox="../../media/connector-compromise-outbound-email-details.png":::
    
3. ابحث باستخدام **مجال الموصل** **وعنوان IP** في [**تتبع الرسائل**](https://admin.exchange.microsoft.com/#/messagetrace). 

    :::image type="content" source="../../media/connector-compromise-new-message-trace.png" alt-text="القائمة المنبثقة لتتبع الرسائل الجديدة" lightbox="../../media/connector-compromise-new-message-trace.png":::
    
4. في نتائج البحث عن **تتبع الرسائل** ، حدد: 

    - إذا تم مؤخرا وضع علامة على عدد كبير من رسائل البريد الإلكتروني ك **FilteredAsSpam**. هذا مؤشر جيد لموصل تم اختراقه يتم استخدامه لإرسال البريد العشوائي. 

    - إذا كان المستلمون هم المستلمون الذين تظل مؤسستك على اتصال بهم عادة. 

    :::image type="content" source="../../media/connector-compromise-message-trace-results.png" alt-text="نتائج بحث تتبع الرسائل الجديدة" lightbox="../../media/connector-compromise-message-trace-results.png":::

#### <a name="investigate-and-validate-connector-related-activity"></a>التحقق من النشاط المرتبط بالموصل والتحقق من صحته 

استخدم سطر الأوامر التالي في PowerShell للتحقق من النشاط المرتبط بالموصل والتحقق من صحته من قبل مستخدم في سجل التدقيق. لمزيد من المعلومات، راجع [استخدام برنامج نصي PowerShell للبحث في سجل التدقيق](/compliance/audit-log-search-script). 

```powershell
Search-UnifiedAuditLog -StartDate "<ExDateTime>" -EndDate "<ExDateTime>" -Operations "New-InboundConnector", "Set-InboundConnector", "Remove-InboundConnector
```

### <a name="step-2-review-and-revert-unauthorized-changes-in-a-connector"></a>الخطوة 2: مراجعة التغييرات (التغييرات) غير المصرح بها وإعادةها في موصل 

1. تسجيل الدخول https://admin.exchange.microsoft.com/. 

2. مراجعة تغيير (تغييرات) الموصل غير المصرح به وإبعاده. 

### <a name="step-3-unblock-the-connector-to-re-enable-mail-flow"></a>الخطوة 3: إلغاء حظر الموصل لإعادة تمكين تدفق البريد 

1. تسجيل الدخول https://security.microsoft.com/restrictedentities. 

2. حدد الموصل المقيد لإلغاء حظر الموصل. 

### <a name="step-4-investigate-and-remediate-potentially-compromised-administrative-user-account"></a>الخطوة 4: التحقيق في حساب المستخدم الإداري الذي يحتمل أن يكون معرضا للخطر وإصلاحه

إذا تم تحديد مستخدم له نشاط موصل غير مصرح به، يمكنك التحقق من هذا المستخدم للحصول على اختراق محتمل. لمزيد من المعلومات، راجع [الاستجابة إلى حساب بريد إلكتروني تم اختراقه](responding-to-a-compromised-email-account.md).

## <a name="more-information"></a>معلومات إضافية

- [إزالة الموصلات المحظورة](remove-blocked-connectors.md)
- [إزالة المستخدمين المحظورين](removing-user-from-restricted-users-portal-after-spam.md)
