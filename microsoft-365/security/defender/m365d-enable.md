---
title: تشغيل Microsoft 365 Defender
description: تعرف على كيفية تمكين Microsoft 365 Defender وبدء تكامل حادث الأمان والاستجابة له.
keywords: بدء العمل وتمكين Microsoft 365 Defender Microsoft 365 Defender و M365 والأمان وموقع البيانات والأذونات المطلوبة وأهلية الترخيص وصفحة الإعدادات
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2a99dbaf50b582df4203fc9c8e1d04e0a3f6d807
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498620"
---
# <a name="turn-on-microsoft-365-defender"></a>تشغيل Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) عملية الاستجابة للحوادث من خلال دمج القدرات الأساسية عبر Microsoft Defender لنقطة النهاية Microsoft Defender لـ Office 365، Microsoft Defender for Cloud Apps، Microsoft Defender for Identity. تضيف هذه التجربة الموحدة ميزات فعالة يمكنك الوصول إليها في Microsoft 365 Defender المدخل.

Microsoft 365 Defender تلقائيا عند زيارة العملاء المؤهلين الذين تم منحهم الأذونات المطلوبة Microsoft 365 Defender المدخل. اقرأ هذه المقالة لفهم المتطلبات الأساسية المتنوعة وكيفية Microsoft 365 Defender هذه المقالة.

## <a name="check-license-eligibility-and-required-permissions"></a>التحقق من أهلية الترخيص والأذونات المطلوبة

وبشكل عام، Microsoft 365 ترخيص لمنتج أمان Microsoft 365 Defender دون تكلفة ترخيص إضافية. نوصي ب الحصول على ترخيص أمان Microsoft 365 E5 أو E5 Security أو A5 أو A5 أو مجموعة صالحة من التراخيص التي توفر الوصول إلى جميع الخدمات المعتمدة.

للحصول على معلومات الترخيص المفصلة [، اقرأ متطلبات الترخيص](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>التحقق من دورك

يجب أن تكون أحد الأدوار التالية لكي تقوم Microsoft 365 Defender:

- المسؤول العام
- مسؤول الأمان
- عامل تشغيل الأمان
- القارئ العام
- قارئ الأمان
- مسؤول التوافق
- مسؤول بيانات التوافق
- مسؤول التطبيق
- مسؤول تطبيق السحابة

[عرض أدوارك في Azure AD](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>الخدمات المعتمدة

Microsoft 365 Defender تجميع البيانات من الخدمات المدعمة المتنوعة التي قمت بنشرها بالفعل. سوف تقوم هذه العملية ب معالجة البيانات وتخزينها مركزيا لتحديد رؤى جديدة وجعل مهام سير عمل الاستجابة المركزية ممكنة. وهي تقوم بذلك دون التأثير على عمليات النشر أو الإعدادات أو البيانات المقترنة بالخدمات المتكاملة.

للحصول على أفضل حماية وتحسين Microsoft 365 Defender، نوصي بنشر جميع الخدمات المعتمدة القابلة للتطبيق على شبكتك. لمزيد من المعلومات، [اقرأ حول نشر الخدمات المعتمدة](deploy-supported-services.md).

## <a name="onboard-to-the-service"></a>الحافظة على الخدمة
إن عملية ال Microsoft 365 Defender بسيطة. من قائمة التنقل، حدد أي عنصر، مثل & التنبيهات أو البحث أو مركز الإجراءات أو تحليل التهديدات لبدء عملية التهيئة. 

### <a name="data-center-location"></a>موقع مركز البيانات

Microsoft 365 Defender تخزين البيانات في [الموقع](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy) نفسه الذي يستخدمه Microsoft Defender لنقطة النهاية. إذا لم يكن لديك Microsoft Defender لنقطة النهاية، يتم تحديد موقع مركز بيانات جديد تلقائيا استنادا إلى موقع الخدمات Microsoft 365 الأمان. يظهر موقع مركز البيانات المحدد في الشاشة.

حدد **هل تحتاج إلى مساعدة؟** في مدخل Microsoft 365 Defender للاتصال بدعم Microsoft حول توفير Microsoft 365 Defender في موقع مركز بيانات آخر.

> [!NOTE]
> في الماضي، Microsoft Defender لنقطة النهاية تلقائيا في مراكز بيانات الاتحاد الأوروبي (EU) عند تشغيلها من خلال Microsoft Defender for Cloud. Microsoft 365 Defender تلقائيا في مركز بيانات الاتحاد الأوروبي نفسه للعملاء الذين قاموا بتوفير Defender لنقطة النهاية بهذه الطريقة في الماضي.

### <a name="confirm-that-the-service-is-on"></a>تأكد من أن الخدمة في

بعد توفير الخدمة، تضيف:

- [إدارة الحوادث](incidents-overview.md)
- [قائمة انتظار التنبيهات](investigate-alerts.md)
- مركز إجراءات لإدارة [التحقيق التلقائي والاستجابة](m365d-autoir.md)
- [قدرات الصيد](advanced-hunting-overview.md) المتقدمة
- تحليل المخاطر

:::image type="content" source="../../media/overview-incident.png" alt-text="جزء التنقل في مدخل Microsoft 365 Defender مع Microsoft 365 Defender" lightbox="../../media/overview-incident.png":::
*Microsoft 365 Defender مدخل مع إدارة الأحداث وإمكانيات أخرى*

### <a name="getting-microsoft-defender-for-identity-data"></a>الحصول Microsoft Defender for Identity البيانات 
لتمكين التكامل مع Microsoft Defender for Cloud Apps، ستحتاج إلى تسجيل الدخول إلى Microsoft Defender for Cloud Apps مرة واحدة على الأقل.

## <a name="get-assistance"></a>الحصول على المساعدة

للحصول على إجابات على الأسئلة الأكثر شيوعا حول تشغيل Microsoft 365 Defender، [اقرأ الأسئلة الشائعة](m365d-enable-faq.md).

يمكن أن يساعد فريق دعم Microsoft في توفير الخدمة والموارد ذات الصلة أو إلغاء توفيرها للمستأجر. للحصول على المساعدة، حدد **هل تحتاج إلى مساعدة؟** في Microsoft 365 Defender المدخل. عند الاتصال بالدعم، أشر إلى Microsoft 365 Defender.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الأسئلة المتداولة](m365d-enable-faq.md)
- [متطلبات الترخيص والمتطلبات الأساسية الأخرى](prerequisites.md)
- [نشر الخدمات المعتمدة](deploy-supported-services.md)
- [Microsoft 365 Defender عامة](microsoft-365-defender.md)
- [Microsoft Defender لنقطة النهاية عامة](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender لـ Office 365 عامة](../office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps عامة](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Defender for Identity عامة](/azure-advanced-threat-protection/what-is-atp)
- [Microsoft Defender لنقطة النهاية تخزين البيانات](../defender-endpoint/data-storage-privacy.md)
