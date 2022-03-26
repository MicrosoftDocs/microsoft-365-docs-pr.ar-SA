---
title: الوصول إلى الهوية والجهاز لبيئة Microsoft 365 الاختبار
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: أنشئ Microsoft 365 اختبار الهوية والوصول إلى الجهاز.
ms.openlocfilehash: 488bd22b555ab30a27e0d9c8ef662af1b6945da9
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63566081"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>الوصول إلى الهوية والجهاز لبيئة Microsoft 365 الاختبار

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

[تكوينات](../security/office-365-security/microsoft-365-policies-configurations.md) الوصول إلى الأجهزة والهوية هي مجموعة من التكوينات الموصى بها ونهج الوصول الشرطي لحماية الوصول إلى جميع الخدمات المتكاملة مع Azure Active Directory (Azure AD).

لإنشاء بيئة اختبار لها تكوينات الوصول إلى الأجهزة والهوية المشتركة في مكانها:

1. قم بتكوين بيئة الاختبار باستخدام ميزات الأمان وهوية المتطلبات الأساسية استنادا إلى اختيارك لنموذج الهوية وطريقة المصادقة:

  - [السحابة فقط](cloud-only-prereqs-m365-test-environment.md)
  - [مزامنة كلمة المرور (PHS)](phs-prereqs-m365-test-environment.md)
  - [المصادقة المرورية (PTA)](pta-prereqs-m365-test-environment.md)

2. استخدم [سياسات الوصول](../security/office-365-security/identity-access-policies.md) إلى الأجهزة والهوية الشائعة لتكوين النهج التي تقوم على المتطلبات الأساسية التي تم تكوينها لبيئة الاختبار واستكشاف حماية الهويات والأجهزة والتحقق منها.

## <a name="see-also"></a>راجع أيضًا

[دليل اختبار الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity)

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)
