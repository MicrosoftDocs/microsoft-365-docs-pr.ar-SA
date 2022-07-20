---
title: تمكين Microsoft 365 Defender
description: تعرف على كيفية تمكين Microsoft 365 Defender والبدء في دمج حدث الأمان والاستجابة.
keywords: بدء الاستخدام، وتمكين Microsoft 365 Defender، Microsoft 365 Defender، M365، الأمان، موقع البيانات، الأذونات المطلوبة، أهلية الترخيص، صفحة الإعدادات
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
- m365solution-getstarted
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 0fa1a47bb5a4a09c22649866bb6c5c6039dc2850
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66895020"
---
# <a name="turn-on-microsoft-365-defender"></a>تمكين Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) توحيد عملية الاستجابة للحوادث من خلال دمج القدرات الرئيسية عبر Microsoft Defender لنقطة النهاية، Microsoft Defender لـ Office 365، Microsoft Defender for Cloud Apps، Microsoft Defender for Identity. تضيف هذه التجربة الموحدة ميزات قوية يمكنك الوصول إليها في مدخل Microsoft 365 Defender.

يتم تشغيل Microsoft 365 Defender تلقائيا عندما يقوم العملاء المؤهلون الذين لديهم الأذونات المطلوبة بزيارة مدخل Microsoft 365 Defender. اقرأ هذه المقالة لفهم المتطلبات الأساسية المختلفة وكيفية توفير Microsoft 365 Defender.

## <a name="check-license-eligibility-and-required-permissions"></a>التحقق من أهلية الترخيص والأذونات المطلوبة

بشكل عام، فإن ترخيص منتج أمان Microsoft 365 يحق لك استخدام Microsoft 365 Defender دون تكلفة ترخيص إضافية. نوصي بالحصول على ترخيص Microsoft 365 E5 أو E5 Security أو A5 أو A5 Security أو مجموعة صالحة من التراخيص التي توفر الوصول إلى جميع الخدمات المدعومة.

للحصول على معلومات مفصلة حول الترخيص، [اقرأ متطلبات الترخيص](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>التحقق من دورك

يجب أن تكون أحد الأدوار التالية لتشغيل Microsoft 365 Defender:

- المسؤول العام
- مسؤول الأمان
- عامل تشغيل الأمان
- القارئ العمومي
- قارئ الأمان
- مسؤول التوافق
- مسؤول بيانات التوافق
- مسؤول التطبيق
- مسؤول تطبيق السحابة

[عرض أدوارك في Azure AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>الخدمات المدعومة

Microsoft 365 Defender تجميع البيانات من الخدمات المدعومة المختلفة التي قمت بتوزيعها بالفعل. وستعالج البيانات وتخزنها مركزيا لتحديد الرؤى الجديدة وجعل مهام سير عمل الاستجابة المركزية ممكنة. وهو يقوم بذلك دون التأثير على عمليات النشر أو الإعدادات أو البيانات الحالية المقترنة بالخدمات المتكاملة.

للحصول على أفضل حماية وتحسين Microsoft 365 Defender، نوصي بنشر جميع الخدمات المدعومة القابلة للتطبيق على شبكتك. لمزيد من المعلومات، [اقرأ حول نشر الخدمات المدعومة](deploy-supported-services.md).

## <a name="onboard-to-the-service"></a>إلحاق الخدمة
يعد الإلحاق Microsoft 365 Defender أمرا بسيطا. من قائمة التنقل، حدد أي عنصر، مثل **التنبيهات & الحوادث** أو **التتبع** أو **مركز الصيانة** أو **تحليلات المخاطر** لبدء عملية الإلحاق. 

### <a name="data-center-location"></a>موقع مركز البيانات

سيقوم Microsoft 365 Defender بتخزين البيانات ومعالجتها في [نفس الموقع المستخدم من قبل Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). إذا لم يكن لديك Microsoft Defender لنقطة النهاية، يتم تحديد موقع مركز بيانات جديد تلقائيا استنادا إلى موقع خدمات أمان Microsoft 365 النشطة. يظهر موقع مركز البيانات المحدد في الشاشة.

حدد **"هل تحتاج إلى مساعدة"؟** في مدخل Microsoft 365 Defender للاتصال بدعم Microsoft حول توفير Microsoft 365 Defender في موقع مركز بيانات مختلف.

> [!NOTE]
> في الماضي، Microsoft Defender لنقطة النهاية توفيرها تلقائيا في مراكز بيانات الاتحاد الأوروبي (EU) عند تشغيلها من خلال Microsoft Defender for Cloud. سيتم توفير Microsoft 365 Defender تلقائيا في نفس مركز بيانات الاتحاد الأوروبي للعملاء الذين قاموا بتوفير Defender لنقطة النهاية بهذه الطريقة في الماضي.

### <a name="confirm-that-the-service-is-on"></a>تأكد من تشغيل الخدمة

بمجرد توفير الخدمة، فإنها تضيف:

- [إدارة الحوادث](incidents-overview.md)
- [قائمة انتظار التنبيهات](investigate-alerts.md)
- مركز إجراءات لإدارة [التحقيق والاستجابة التلقائيين](m365d-autoir.md)
- قدرات [التتبع المتقدمة](advanced-hunting-overview.md)
- تحليلات المخاطر

:::image type="content" source="../../media/overview-incident.png" alt-text="جزء التنقل في مدخل Microsoft 365 Defender مع ميزات Microsoft 365 Defender" lightbox="../../media/overview-incident.png":::
*مدخل Microsoft 365 Defender مع إدارة الحوادث والقدرات الأخرى*

### <a name="getting-microsoft-defender-for-identity-data"></a>الحصول على بيانات Microsoft Defender for Identity 
لتمكين التكامل مع Microsoft Defender for Cloud Apps، ستحتاج إلى تسجيل الدخول إلى Microsoft Defender for Cloud Apps مرة واحدة على الأقل.

## <a name="get-assistance"></a>الحصول على المساعدة

للحصول على إجابات للأسئلة الأكثر شيوعا حول تشغيل Microsoft 365 Defender، [اقرأ الأسئلة المتداولة](m365d-enable-faq.md).

يمكن لموظفي دعم Microsoft المساعدة في توفير الخدمة والموارد ذات الصلة أو إلغاء توفيرها على المستأجر الخاص بك. للحصول على المساعدة، حدد **"هل تحتاج إلى مساعدة"؟** في مدخل Microsoft 365 Defender. عند الاتصال بالدعم، ذكر Microsoft 365 Defender.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الأسئلة المتداولة](m365d-enable-faq.md)
- [متطلبات الترخيص والمتطلبات الأساسية الأخرى](prerequisites.md)
- [نشر الخدمات المعتمدة](deploy-supported-services.md)
- [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md)
- [نظرة عامة على Microsoft Defender لنقطة النهاية](../defender-endpoint/microsoft-defender-endpoint.md)
- [نظرة عامة على Defender لـ Office 365](../office-365-security/defender-for-office-365.md)
- [نظرة عامة على Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [نظرة عامة على Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)
- [تخزين البيانات Microsoft Defender لنقطة النهاية](../defender-endpoint/data-storage-privacy.md)
