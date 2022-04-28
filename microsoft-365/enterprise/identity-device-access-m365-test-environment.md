---
title: الوصول إلى الهوية والجهاز لبيئة اختبار Microsoft 365
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: إنشاء بيئة Microsoft 365 لاختبار الهوية والوصول إلى الجهاز.
ms.openlocfilehash: 09c7bf9ecb6aaadc89cedfd881e66a5fd19f28d7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091204"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>الوصول إلى الهوية والجهاز لبيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

[تكوينات الوصول إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) هي مجموعة من التكوينات الموصى بها ونهج الوصول المشروط لحماية الوصول إلى جميع الخدمات المدمجة مع Azure Active Directory (Azure AD).

لإنشاء بيئة اختبار تحتوي على تكوينات الوصول إلى الأجهزة والهوية الشائعة في مكانها:

1. تكوين بيئة الاختبار الخاصة بك مع هوية المتطلبات الأساسية وميزات الأمان استنادا إلى اختيارك لنموذج الهوية وأسلوب المصادقة:

  - [السحابة فقط](cloud-only-prereqs-m365-test-environment.md)
  - [مزامنة تجزئة كلمة المرور (PHS)](phs-prereqs-m365-test-environment.md)
  - [المصادقة التمريرية (PTA)](pta-prereqs-m365-test-environment.md)

2. استخدم [نهج الوصول إلى الأجهزة والهوية الشائعة](../security/office-365-security/identity-access-policies.md) لتكوين النهج التي تعتمد على المتطلبات الأساسية التي تم تكوينها لبيئة الاختبار الخاصة بك واستكشاف الحماية للهويات والأجهزة والتحقق منها.

## <a name="see-also"></a>راجع أيضًا

[دلائل مختبر اختبار الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity)

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)
