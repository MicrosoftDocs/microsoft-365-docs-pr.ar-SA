---
title: مثال على هجوم البريد الإلكتروني للتصيد الاحتيالي
description: خطوة من خلال مثال تحليل هجوم التصيد الاحتيالي.
keywords: الحوادث والتنبيهات والتحقيق والارتباط والهجوم والأجهزة والأجهزة والمستخدمين والهويات والهوية وعلبة البريد والبريد الإلكتروني و365 وmicrosoft وm365
search.product: eADQiWindows 10XVcnh
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
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: dcf620cfaeb1d33665538d16d080e72745b96e42
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66892892"
---
# <a name="example-of-a-phishing-email-attack"></a>مثال على هجوم البريد الإلكتروني للتصيد الاحتيالي

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن أن تساعد Microsoft 365 Defender في اكتشاف المرفقات الضارة التي يتم تسليمها عبر البريد الإلكتروني. نظرا لأن [مركز الأمان والتوافق Office 365](https://protection.office.com/) يتكامل مع Microsoft 365 Defender، يمكن أن يكون لدى محللي الأمان رؤية على التهديدات الواردة من Office 365، مثل من خلال مرفقات البريد الإلكتروني.

على سبيل المثال، تم تعيين حادث متعدد المراحل لمحلل.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="حدث متعدد المراحل" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-incident.png":::

في علامة تبويب **التنبيهات** الخاصة بالحادث، يتم عرض التنبيهات من Defender لـ Office 365 Microsoft Defender for Cloud Apps. يمكن للمحلل التنقل لأسفل في تنبيهات Defender لـ Office 365 عن طريق تحديد تنبيهات رسائل البريد الإلكتروني. يتم عرض تفاصيل التنبيه على الجزء الجانبي.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="تنبيه بالبريد الإلكتروني" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png":::
 
من خلال التمرير لأسفل، يتم عرض مزيد من المعلومات، تظهر الملفات الضارة والمستخدم الذي تأثر.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="تأثير المستخدم والملف لتنبيه البريد الإلكتروني" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-impact.png":::
  
يؤدي تحديد **صفحة التنبيه "فتح** " إلى أخذك إلى التنبيه المحدد حيث يمكن عرض المعلومات المختلفة بمزيد من التفصيل عن طريق تحديد الارتباط. يمكن عرض رسالة البريد الإلكتروني الفعلية عن طريق تحديد **عرض الرسائل في المستكشف** باتجاه أسفل اللوحة.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="تفاصيل التنبيه" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png"::: 

يؤدي ذلك إلى نقل المحلل إلى صفحة إدارة المخاطر حيث يتم عرض موضوع البريد الإلكتروني والمستلم والمرسل ومعلومات أخرى. **يخبر ZAP** ضمن **الإجراءات الخاصة** المحلل أنه تم تنفيذ ميزة الإزالة التلقائية لمدة صفر ساعة. يكشف ZAP تلقائيا عن الرسائل الضارة ورسائل البريد العشوائي ويزيلها من علب البريد في جميع أنحاء المؤسسة. لمزيد من المعلومات، راجع [الإزالة التلقائية لمدة صفر ساعة (ZAP) في Exchange Online](../office-365-security/zero-hour-auto-purge.md).

يمكن اتخاذ إجراءات أخرى على رسائل محددة عن طريق تحديد **الإجراءات**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="الإجراءات الأخرى التي يمكن اتخاذها على رسائل البريد الإلكتروني" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-actions.png"::: 

## <a name="next-step"></a>الخطوة التالية

راجع مسار التحقيق [في الهجوم المستند إلى الهوية](first-incident-path-identity.md) .

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الحوادث](incidents-overview.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
