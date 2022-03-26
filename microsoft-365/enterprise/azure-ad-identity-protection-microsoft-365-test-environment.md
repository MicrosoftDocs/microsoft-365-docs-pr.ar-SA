---
title: حماية هوية Azure AD Microsoft 365 بيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: تكوين حماية هوية Azure AD وتحليل الحسابات الحالية في Microsoft 365 بيئة اختبار المؤسسة.
ms.openlocfilehash: 210736e0a950d74e0cd761463e9cc27f1dc3c721
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63566886"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>حماية هوية Azure AD Microsoft 365 بيئة اختبار المؤسسة

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

يمكنك استخدام حماية هوية Azure Active Directory (Azure AD) للكشف عن نقاط الضعف المحتملة التي تؤثر على هويات مؤسستك وتكوين الاستجابات التلقائية وتحري الأحداث. تصف هذه المقالة كيفية استخدام Azure AD Identity Protection لعرض تحليل حسابات بيئة الاختبار.

يتضمن إعداد حماية هوية Azure AD في Microsoft 365 اختبار المؤسسة مرحلتين:

- [المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة الثانية: استخدام حماية هوية Azure AD](#phase-2-use-azure-ad-identity-protection)

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة

إذا كنت تريد اختبار Azure AD Identity Protection فقط بطريقة خفيفة مع الحد الأدنى من المتطلبات، فاتبع الإرشادات الموجودة في [تكوين الأساس الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت تريد اختبار حماية هوية Azure AD في مؤسسة محاكاة، فاتبع الإرشادات الواردة في [المصادقة المرورية](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار حماية هوية Azure AD بيئة اختبار المؤسسة المحاكاة، التي تتضمن إنترانت محاكاة متصلة بالإنترنت ومزامنة الدليل الغابات خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار حماية هوية Azure AD واختباره في بيئة تمثل مؤسسة نموذجية.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>المرحلة الثانية: استخدام حماية هوية Azure AD

1. افتح مثيلا خاصا للمستعرض الخاص بك، ثم سجل الدخول إلى مدخل Azure [https://portal.azure.com](https://portal.azure.com) باستخدام حساب المسؤول العام في Microsoft 365 اختبار المؤسسة.
2. في مدخل Azure، اكتب **حماية** الهوية في مربع البحث، ثم حدد **حماية هوية Azure AD**.
3. في **ريشة حماية الهوية - نظرة** عامة، حدد كل تقرير لمعرفة ما يتم إعداد التقارير عنه.
4. ضمن **إعلام**، حدد **المستخدمون المعرضون لخطر التنبيهات التي تم الكشف عنها**.
5. في جزء **التنبيهات** التي كشف عنها المستخدمون المعرضون للمخاطر، حدد **متوسط**.
6. بالنسبة **إلى رسائل البريد الإلكتروني التي يتم إرسالها إلى المستخدمين** التاليين، حدد **مضمن** وتحقق من وجود حساب المسؤول العام في قائمة الأعضاء المحددين.
7. حدد **حفظ**.

ضمن **حماية**، حدد العديد من الشرطة لمعرفة كيفية تكوينها. إذا قمت بإنشاء نهج وتنشيطه، فتأكد من أنه لا يمنع وصول جميع المستخدمين، أو قد لا تتمكن من تسجيل الدخول. لمنع حدوث ذلك، استثني حسابات مستخدمين معينة، مثل المسؤولين العامين.

لمزيد من الاختبارات والاختبارات، راجع [محاكاة أحداث المخاطر](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity) وإمكانياتها في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)