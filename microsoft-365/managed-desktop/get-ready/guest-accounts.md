---
title: المتطلبات الأساسية الخاصة وحسابات الضيوف
description: إرشادات تكوين حسابات الضيوف وكيفية ضبطها
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 80770c6c122cc4e2892c22a43f185ffbac40c637
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63577057"
---
# <a name="prerequisites-for-guest-accounts"></a>المتطلبات الأساسية الخاصة وحسابات الضيوف

## <a name="external-collaboration-settings"></a>إعدادات التعاون الخارجي

يوصي Microsoft Managed Desktop التكوين التالي في مؤسسة Azure AD للوصول إلى حساب الضيف. يمكنك ضبط هذه الإعدادات في مدخل [Azure](https://portal.azure.com) ضمن **الهويات الخارجية / إعدادات التعاون الخارجي**:

| الإعداد | تعيين إلى |
| ------ | ------ |
| وصول الضيف | يتمتع الضيوف بالوصول المحدود إلى خصائص كائنات الدليل وعضوياتها. |
| إعدادات دعوة الضيف | يمكن للمستخدمين الأعضاء والمستخدمين المعينين لأدوار إدارة معينة دعوة الضيوف بما في ذلك الضيوف الذين لديهم أذونات الأعضاء |

يتطلب Microsoft Managed Desktop التكوين التالي في مؤسسة Azure AD للوصول إلى حساب الضيف. يمكنك ضبط هذا الإعداد في مدخل [Azure](https://portal.azure.com) ضمن **الهويات الخارجية / إعدادات التعاون الخارجي**:

| الإعداد | الخيار |
| ------ | ------ |
| قيود التعاون | حدد أي من هذه الخيارات: <ul><li>إذا حددت **السماح بإرسال الدعوات إلى أي مجال (الأكثر شمولا)،** فلا يتطلب أي تكوين آخر.</li><li>إذا حددت **رفض الدعوات** للمجالات المحددة، فتأكد من عدم إدراج Microsoft.com في المجالات الهدف.</li><li>إذا حددت **السماح بالدعوات** للمجالات المحددة فقط (الأكثر تقييدا)، فتأكد من إدراج Microsoft.com في المجالات الهدف.</li><ul>

إذا قمت بتعيين قيود تتفاعل مع هذه الإعدادات، فتأكد من استبعاد حسابات خدمة Azure Active Directory **Modern Workplace**. على سبيل المثال، إذا كان لديك نهج وصول شرطي يمنع حسابات الضيوف من الوصول إلى مدخل Intune، فاستبعد المجموعة **حسابات خدمة مكان** العمل الحديثة من هذا النهج.

لمزيد من المعلومات، راجع [تمكين التعاون الخارجي B2B وإدارة الأشخاص الذين يمكنهم دعوة الضيوف](/azure/active-directory/external-identities/delegate-invitations#to-configure-external-collaboration-settings).

## <a name="unlicensed-intune-admin"></a>مسؤول Intune غير مرخص

يجب **تمكين** الإعداد السماح بالوصول إلى المسؤولين غير مرخصين. بدون تمكين هذا الإعداد، يمكن أن تحدث الأخطاء عند محاولة الوصول إلى مؤسسة Azure AD للخدمة. يمكنك تمكين هذا الإعداد بأمان من دون القلق بشأن الآثار المترتبة على الأمان. يتم تعريف نطاق الوصول بالأدوار المعينة للمستخدمين، بما في ذلك موظفي العمليات لدينا.

**لتمكين هذا الإعداد:**

1. انتقل إلى إدارة نقاط النهاية من Microsoft [الإدارة](https://go.microsoft.com/fwlink/?linkid=2109431).
2. انتقل إلى **إدارة المستأجر،** وحدد **أدوار**. بعد ذلك، حدد **ترخيص المسؤول**.
3. في المقطع **السماح بالوصول إلى المسؤولين** غير مرخصين، حدد **نعم**.

> [!IMPORTANT]
> لا يمكنك التراجع عن هذا الإعداد بعد تحديد **نعم**.

لمزيد من المعلومات، راجع [المسؤولين غير](/mem/intune/fundamentals/unlicensed-admins) مرخصين في Microsoft Intune.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>خطوات الاستعداد لسطح المكتب المدار من Microsoft

1. مراجعة [المتطلبات الأساسية لسطح المكتب المدار من Microsoft](prerequisites.md).
1. تشغيل [أدوات تقييم الجهوزية](readiness-assessment-tool.md).
1. شراء [Company Portal](../get-started/company-portal.md).
1. مراجعة المتطلبات الأساسية الخاصة وحسابات الضيوف (هذه المقالة).
1. تحقق [من تكوين الشبكة](network.md).
1. [إعداد الشهادات وملفات تعريف الشبكة](certs-wifi-lan.md).
1. [إعداد وصول المستخدم إلى البيانات](authentication.md).
1. [تحضير التطبيقات](apps.md).
1. [إعداد محركات أقراص تم تعيينها](mapped-drives.md).
1. [تحضير موارد الطباعة](printing.md).
1. أسماء [أجهزة العنوان](address-device-names.md).
