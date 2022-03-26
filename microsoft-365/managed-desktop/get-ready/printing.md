---
title: إعداد موارد الطباعة لسطح المكتب المدار من Microsoft
description: خطوات مهمة للتأكد من عمل الطباعة بسلاسة
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: a66075637a15eb39eda38e318070af2bcbdc8fe6
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/08/2022
ms.locfileid: "63567820"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>إعداد موارد الطباعة لسطح المكتب المدار من Microsoft

عندما تكون جاهزا للتسجيل في Microsoft Managed Desktop، يجب تقييم متطلبات الطباعة وتحديد النهج المناسب  بيئتك. لديك ثلاثة خيارات:

| الخيار | الوصف |
| ------ | ------ |
| نشر حل Microsoft Universal Print | حل Microsoft Universal Print لسهولة اكتشاف الطابعات لأجهزة سطح المكتب المدارة من Microsoft. لمزيد من المعلومات، راجع [ما هي الطباعة العالمية](/universal-print/fundamentals/universal-print-whatis). |
| نشر الطابعات مباشرة باستخدام برنامج نصي مخصص في PowerShell | اتبع الخطوات في القسم [إعداد الطابعات المحلية](#set-up-local-printers) . |
| استخدام حل طباعة سحابية غير Microsoft | استخدم حل الطباعة السحابية غير Microsoft المتوافق مع Windows 10 الأجهزة والمنضم إلى مجال Azure Active Directory. يجب أن يلبي الحل متطلبات البرنامج لسطح المكتب المدار من Microsoft. لمزيد من المعلومات، راجع [متطلبات تطبيق Microsoft Managed Desktop](../service-description/mmd-app-requirements.md). |

في كل الخيارات أعلاه، إذا لم تتوفر برامج تشغيل الطابعة من Microsoft Update أو Microsoft Store، فيجب الحصول عليها بنفسك، وحزمها للنشر على أجهزة Microsoft Managed Desktop باستخدام Microsoft Intune. لمزيد من المعلومات، راجع [Intune مستقل - إدارة تطبيق Win32](/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>إعداد الطابعات المحلية

تفترض الإرشادات التالية أنك قمت بإعداد موارد الطباعة وقررت نشر الطابعات باستخدام برنامج PowerShell نصي مخصص.

**لنشر الطابعات باستخدام برنامج PowerShell نصي مخصص:**

1. انتقل إلى مدخل Microsoft Managed Desktop.
1. أرسل طلبا سمي نشر *الطابعة* في **قسم** طلبات > الدعم من مدخل المسؤول.
1. توفير التفاصيل التالية:
    - جميع مسارات UNC إلى مواقع الطابعات المشتركة التي يجب نشرها لأجهزة سطح المكتب المدارة من Microsoft.
    - مجموعات المستخدمين التي تتطلب الوصول إلى هذه الطابعات المشتركة.
1. باستخدام مدخل المسؤول، سنعلمك عند اكتمال الطلب. في البداية، سنقوم بنشر التكوين فقط على الأجهزة في مجموعة نشر الاختبار.
1. اختبر وتأكد مما إذا كان التكوين يعمل كما تتوقع أم لا.
1. قم بالرد باستخدام علامة **التبويب** مناقشة في طلب الدعم لتعرفنا عند إكمال الاختبار.
1. سنقوم بعد ذلك بنشر التكوين إلى مجموعات النشر الأخرى.

## <a name="steps-to-get-ready"></a>خطوات الاستعداد

1. مراجعة [المتطلبات الأساسية لسطح المكتب المدار من Microsoft](prerequisites.md).
1. تشغيل [أدوات تقييم الجهوزية](readiness-assessment-tool.md).
1. شراء [Company Portal](../get-started/company-portal.md).
1. مراجعة [المتطلبات الأساسية الخاصة وحسابات الضيوف](guest-accounts.md).
1. تحقق [من تكوين الشبكة](network.md).
1. [إعداد الشهادات وملفات تعريف الشبكة](certs-wifi-lan.md).
1. [إعداد وصول المستخدم إلى البيانات](authentication.md).
1. [تحضير التطبيقات](apps.md).
1. [إعداد محركات أقراص تم تعيينها](mapped-drives.md).
1. إعداد موارد الطباعة (هذه المقالة).
1. أسماء [أجهزة العنوان](address-device-names.md).
