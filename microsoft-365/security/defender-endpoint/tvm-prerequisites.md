---
title: المتطلبات & الأذونات - إدارة المخاطر والثغرات الأمنية
description: قبل البدء في استخدام إدارة المخاطر والثغرات الأمنية، تأكد من أن لديك التكوينات والأذونات ذات الصلة.
keywords: متطلبات & إدارة الثغرات الأمنية أذونات إدارة المخاطر والثغرات الأمنية، متطلبات أذونات المستخدم، متطلبات أذونات Microsoft Defender ل Endpoint TVM، إدارة الثغرات الأمنية
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 343a5fd1033a6d954c7cd62e2558a4b401f69b20
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570492"
---
# <a name="prerequisites--permissions---threat-and-vulnerability-management"></a>المتطلبات & الأذونات - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

تأكد من أن أجهزتك:

- تم تعيينهم إلى Microsoft Defender ل Endpoint

- تشغيل [أنظمة التشغيل و الأنظمة الأساسية المعتمدة](tvm-supported-os.md)

- قم بتثبيت التحديثات الإلزامية التالية ونشرها في شبكتك لتعزيز معدلات الكشف عن تقييم الضعف لديك:

  > Release | رقم KB وتحديث الأمان والارتباط
  > :---|:---
  > Windows 10 1709 | [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) [وKB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
  > Windows 10 1803 | [KB4493464](https://support.microsoft.com/help/4493464) [وKB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
  > Windows 10 1809 | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
  > Windows 10 1903 | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)

- تم [التكهين](/mem/intune/fundamentals/what-is-intune) Microsoft Intune [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) للمساعدة في إصلاح التهديدات التي عثر عليها إدارة المخاطر والثغرات الأمنية. إذا كنت تستخدم "إدارة التكوين"، فحدث وحدة التحكم إلى الإصدار الأخير.

  > [!NOTE]
  > إذا تم تمكين اتصال Intune، يمكنك الحصول على خيار لإنشاء مهمة أمان Intune عند إنشاء طلب إصلاح. لا يظهر هذا الخيار إذا لم يتم تعيين الاتصال.

- الحصول على توصية أمان واحدة على الأقل يمكن عرضها في صفحة الجهاز

- وضع علامة عليها أو وضع علامة عليها على أنها مدارة بشكل شاركي

## <a name="relevant-permission-options"></a>خيارات الأذونات ذات الصلة

1. سجل دخولك Microsoft 365 Defender المدخل باستخدام حساب مع تعيين دور مسؤول أمان أو مسؤول عام.
2. في جزء التنقل، حدد الإعدادات > **نقاط النهاية > الأدوار**.

لمزيد من المعلومات، راجع [إنشاء أدوار](user-roles.md) للتحكم بالوصول المستند إلى الدور وإدارتها.

### <a name="view-data"></a>عرض البيانات

- **عمليات الأمان** - عرض كل بيانات عمليات الأمان في المدخل
- **التهديدات إدارة الثغرات الأمنية** - عرض إدارة المخاطر والثغرات الأمنية البيانات في المدخل

### <a name="active-remediation-actions"></a>إجراءات المعالجة النشطة

- **عمليات الأمان** - اتخاذ إجراءات الاستجابة والموافقة على إجراءات المعالجة المعلقة أو استبعادها وإدارة القوائم المسموح بها/المحظورة للأتمتة والمؤشرات
- **التهديدات إدارة الثغرات الأمنية - معالجة الاستثناءات** - إنشاء استثناءات جديدة وإدارة الاستثناءات النشطة
- **التهديدات إدارة الثغرات الأمنية -** معالجة المعالجة - إرسال طلبات إصلاح جديدة وإنشاء تذاكر وإدارة أنشطة الإصلاح الموجودة

لمزيد من المعلومات، راجع خيارات [أذونات RBAC](user-roles.md#permission-options)

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [أنظمة التشغيل و الأنظمة الأساسية المعتمدة](tvm-supported-os.md)
- [تعيين قيمة الجهاز](tvm-assign-device-value.md)
- [لوحة معلومات إدارة الثغرات الأمنية المخاطر](tvm-dashboard-insights.md)

