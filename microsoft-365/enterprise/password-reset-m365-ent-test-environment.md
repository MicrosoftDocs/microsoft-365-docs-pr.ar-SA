---
title: إعادة تعيين كلمة المرور لبيئة اختبار Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'ملخص: تكوين واختبار إعادة تعيين كلمة المرور لبيئة اختبار Microsoft 365.'
ms.openlocfilehash: 4e68372aee44887641d626c3e3667adbdedd5a1e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095609"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>إعادة تعيين كلمة المرور لبيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

تسمح إعادة تعيين كلمة مرور الخدمة الذاتية (SSPR) في Azure Active Directory (Azure AD) للمستخدمين بإعادة تعيين كلمات المرور أو الحسابات أو إلغاء تأمينها.

تصف هذه المقالة كيفية تكوين عمليات إعادة تعيين كلمة المرور واختبارها في بيئة اختبار Microsoft 365.

يتضمن إعداد إعادة تعيين كلمة مرور الخدمة الذاتية ثلاث مراحل:
- [المرحلة 1: تكوين مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [المرحلة الثانية: تمكين إعادة كتابة كلمة المرور](#phase-2-enable-password-writeback)
- [المرحلة 3: تكوين إعادة تعيين كلمة المرور واختبارها](#phase-3-configure-and-test-password-reset)
    
![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365

أولا، اتبع الإرشادات في [مزامنة تجزئة كلمة المرور](password-hash-sync-m365-ent-test-environment.md). 

يبدو التكوين الناتج كما يلي:
  
![المؤسسة المحاكاة مع بيئة اختبار مزامنة تجزئة كلمة المرور.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراك تجريبي أو مدفوع Microsoft 365 E5.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.
- يتم تشغيل الاتصال Azure AD على APP1 لمزامنة مجال خدمات مجال ACTIVE DIRECTORY TESTLAB (AD DS) مع مستأجر Azure AD لاشتراكك في Microsoft 365.

## <a name="phase-2-enable-password-writeback"></a>المرحلة الثانية: تمكين إعادة كتابة كلمة المرور

اتبع الإرشادات في [المرحلة 2 من دليل اختبار اختبار إعادة كتابة كلمة المرور](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

يجب تمكين إعادة كتابة كلمة المرور لاستخدام إعادة تعيين كلمة المرور.
  
## <a name="phase-3-configure-and-test-password-reset"></a>المرحلة 3: تكوين إعادة تعيين كلمة المرور واختبارها

في هذه المرحلة، قم بتكوين إعادة تعيين كلمة المرور في مستأجر Azure AD من خلال عضوية المجموعة، ثم تحقق من أنها تعمل.

أولا، تمكين إعادة تعيين كلمة المرور للحسابات في مجموعة Azure AD معينة.

1. من مثيل خاص للمستعرض، افتح [https://portal.azure.com](https://portal.azure.com)، ثم سجل الدخول باستخدام بيانات اعتماد حساب المسؤول العام.
2. في مدخل Microsoft Azure، حدد **مجموعة** **Azure Active DirectoryGroupsNew** >  > .
3. تعيين **نوع المجموعة** إلى **الأمان** **واسم المجموعة** إلى **PWReset** **ونوع العضوية** إلى **معين**.
4. حدد **"الأعضاء**"، وابحث عن **المستخدم 3** وحدده، وحدد **"تحديد**"، ثم حدد **"إنشاء**".
5. أغلق جزء **المجموعات** .
6. في جزء Azure Active Directory، حدد **إعادة تعيين كلمة المرور** في جزء التنقل الأيمن.
7. في جزء **"Password reset-Properties** "، ضمن الخيار **"تمكين إعادة تعيين كلمة مرور الخدمة الذاتية**"، اختر **"Selected**".
8. حدد **مجموعة التحديد**، وحدد مجموعة **PWReset**، ثم حدد **SelectSave** > .
9. أغلق مثيل المستعرض الخاص.

بعد ذلك، اختبر إعادة تعيين كلمة المرور لحساب المستخدم 3.

1. افتح مثيل مستعرض خاص جديد واستعرض وصولا إلى [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. سجل الدخول باستخدام بيانات اعتماد حساب المستخدم 3.
1. **في مزيد من المعلومات المطلوبة**، حدد **"التالي**". 
1. في **"عدم فقدان إمكانية الوصول إلى حسابك**"، قم بتعيين هاتف المصادقة إلى رقم هاتفك الجوال والبريد الإلكتروني للمصادقة إلى حساب العمل أو البريد الإلكتروني الشخصي.
1. بعد التحقق من كليهما، حدد **"يبدو جيدا**"، ثم أغلق المثيل الخاص للمستعرض.
1. في مثيل مستعرض خاص جديد، انتقل إلى [https://aka.ms/sspr](https://aka.ms/sspr).
1. أدخل اسم حساب المستخدم 3، وأدخل الأحرف من CAPTCHA، ثم حدد **"التالي**".
1. **للتحقق من الخطوة 1**، حدد **البريد الإلكتروني البديل**، ثم حدد **"البريد الإلكتروني**". عند تلقي البريد الإلكتروني، أدخل رمز التحقق، ثم حدد **"التالي**".
1. في **"العودة إلى حسابك**"، أدخل كلمة مرور جديدة لحساب المستخدم 3، ثم حدد **"إنهاء**". لاحظ كلمة المرور التي تم تغييرها لحساب المستخدم 3 وقم بتخزينها في موقع آمن.
1. في علامة تبويب منفصلة من المستعرض نفسه، انتقل إلى [https://admin.microsoft.com](https://admin.microsoft.com)، ثم سجل الدخول باستخدام اسم حساب المستخدم 3 وكلمة المرور الجديدة الخاصة به. يجب أن تشاهد الصفحة **الرئيسية Microsoft Office**.

## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وإمكانات الهوية](m365-enterprise-test-lab-guides.md#identity) الإضافية في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)