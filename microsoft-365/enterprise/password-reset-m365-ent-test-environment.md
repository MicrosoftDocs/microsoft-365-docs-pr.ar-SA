---
title: إعادة تعيين كلمة المرور لبيئة Microsoft 365 الاختبار
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'ملخص: تكوين إعادة تعيين كلمة المرور واختبارها Microsoft 365 الاختبار.'
ms.openlocfilehash: 9aa55f42ca295577bf3b1c81ee54b1160adf3d27
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568522"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>إعادة تعيين كلمة المرور لبيئة Microsoft 365 الاختبار

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

يتيح Azure Active Directory (Azure AD) إعادة تعيين كلمة مرور الخدمة الذاتية (SSPR) للمستخدمين بإعادة تعيين كلمات المرور أو الحسابات أو إلغاء تأمينها.

تصف هذه المقالة كيفية تكوين إعادة تعيين كلمة المرور واختبارها في Microsoft 365 الاختبار.

يتضمن إعداد SSPR ثلاث مراحل:
- [المرحلة 1: تكوين مزامنة كلمة المرور لبيئة Microsoft 365 الاختبار](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [المرحلة الثانية: تمكين إعادة كتابة كلمة المرور](#phase-2-enable-password-writeback)
- [المرحلة 3: تكوين إعادة تعيين كلمة المرور واختبارها](#phase-3-configure-and-test-password-reset)
    
![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة كلمة المرور لبيئة Microsoft 365 الاختبار

أولا، اتبع الإرشادات الواردة في [مزامنة كلمة المرور.](password-hash-sync-m365-ent-test-environment.md) 

يبدو التكوين الناتج كما يلي:
  
![المؤسسة التي تم محاكاتها مع بيئة اختبار مزامنة كلمة المرور.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراك Microsoft 365 E5 تجريبي أو مدفوع.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.
- يتم تشغيل Azure AD الاتصال على APP1 لمزامنة مجال خدمات مجال TESTLAB Active Directory (AD DS) مع مستأجر Azure AD لاشتراكك في Microsoft 365.

## <a name="phase-2-enable-password-writeback"></a>المرحلة الثانية: تمكين إعادة كتابة كلمة المرور

اتبع الإرشادات الواردة [في المرحلة 2 من دليل اختبار الاختبار للكتابة بكلمة مرور](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

يجب تمكين إعادة كتابة كلمة المرور لاستخدام إعادة تعيين كلمة المرور.
  
## <a name="phase-3-configure-and-test-password-reset"></a>المرحلة 3: تكوين إعادة تعيين كلمة المرور واختبارها

في هذه المرحلة، قم بتكوين إعادة تعيين كلمة المرور في مستأجر Azure AD من خلال عضوية المجموعة، ثم تحقق من عملها.

أولا، قم بتمكين إعادة تعيين كلمة المرور للحسابات في مجموعة Azure AD معينة.

1. من مثيل خاص للمستعرض، افتح [https://portal.azure.com](https://portal.azure.com)، ثم سجل الدخول باستخدام بيانات اعتماد حساب المسؤول العام.
2. في مدخل Azure، حدد **مجموعة Azure Active DirectoryGroupsNew** >  > .
3. قم بتعيين **نوع المجموعة** إلى **الأمان** واسم **المجموعة** إلى **PWReset** ونوع **العضوية** إلى **معين**.
4. حدد **الأعضاء**، واعثر على **المستخدم 3 وحدده**، **وحدد تحديد**، ثم حدد **إنشاء**.
5. أغلق **جزء** المجموعات.
6. في جزء Azure Active Directory، حدد **إعادة تعيين كلمة المرور** في جزء التنقل الأيسر.
7. في الجزء **إعادة تعيين-خصائص** كلمة المرور، ضمن الخيار تمكين إعادة تعيين كلمة مرور الخدمة **الذاتية**، اختر **محدد**.
8. حدد **تحديد المجموعة**، وحدد **مجموعة PWReset**، ثم حدد **SelectSave** > .
9. أغلق مثيل المستعرض الخاص.

بعد ذلك، اختبر إعادة تعيين كلمة المرور لحساب المستخدم 3.

1. افتح مثيل مستعرض خاص جديد واستعرض إلى [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. سجل الدخول باستخدام بيانات اعتماد حساب المستخدم 3.
1. في **مزيد من المعلومات المطلوبة**، حدد **التالي**. 
1. في **عدم فقدان الوصول** إلى حسابك، قم بتعيين هاتف المصادقة إلى رقم هاتفك الجوال والبريد الإلكتروني للمصادقة إلى حساب البريد الإلكتروني الخاص بالعمل أو الشخصي.
1. بعد التحقق من كليهما، حدد **يبدو** جيدا، ثم أغلق المثيل الخاص للمستعرض.
1. في مثيل مستعرض خاص جديد، انتقل إلى [https://aka.ms/sspr](https://aka.ms/sspr).
1. أدخل اسم حساب المستخدم 3، وأدخل الأحرف من CAPTCHA، ثم حدد **التالي**.
1. **للتحقق من الخطوة 1**، حدد **إرسال بريد إلكتروني** بديل، ثم حدد **البريد الإلكتروني**. عندما تتلقى البريد الإلكتروني، أدخل رمز التحقق، ثم حدد **التالي**.
1. في **العودة إلى حسابك،** أدخل كلمة مرور جديدة لحساب المستخدم 3، ثم حدد **إنهاء**. لاحظ كلمة المرور التي تم تغييرها لحساب المستخدم 3 وتخزينها في موقع آمن.
1. في علامة تبويب منفصلة [https://admin.microsoft.com](https://admin.microsoft.com)لنفس المستعرض، انتقل إلى ، ثم سجل الدخول باستخدام اسم حساب المستخدم 3 وكلمة المرور الجديدة الخاصة به. من المفترض أن ترى Microsoft Office **الصفحة** الرئيسية.

## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity) وإمكانياتها في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)