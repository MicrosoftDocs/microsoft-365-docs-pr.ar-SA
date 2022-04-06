---
title: إعداد أجهزة Windows للمستخدمين Microsoft 365 Business Premium
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: قم بإعداد Windows أجهزة تعمل Windows 10 Pro للمستخدمين Microsoft 365 Business Premium، مما يمكن الإدارة المركزية و عناصر التحكم في الأمان.
ms.openlocfilehash: 0a6fa4178e3aeb2e77d744283bfcf671d0df1f3d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583653"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>إعداد أجهزة Windows للمستخدمين Microsoft 365 Business Premium

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium، تأكد من تشغيل جميع أجهزة Windows، Windows 10 Pro 1703 (تحديث المبدعين). Windows 10 Pro هو أحد المتطلبات الأساسية لنشر Windows 10 Business، وهو مجموعة من الخدمات السحابية وإمكانيات إدارة الأجهزة التي تكمل Windows 10 Pro وتمكن الإدارة المركزية وتحكم الأمان في Microsoft 365 Business Premium.
  
إذا كان لديك Windows أجهزة تعمل Windows 7 Pro أو Windows 8 Pro أو Windows 8.1 Pro، فإن اشتراكك في Microsoft 365 Business Premium يجهزك للحصول على Windows 10 ترقية.
  
للحصول على مزيد من المعلومات حول Windows الأجهزة Windows 10 Pro المبدعين، اتبع الخطوات الواردة في هذا الموضوع: ترقية Windows [إلى Windows Pro المبدعين](../../business-video/upgrade.md).
  
راجع [التحقق من اتصال الجهاز ب Azure AD](#verify-the-device-is-connected-to-azure-ad) للتحقق من أن لديك الترقية، أو للتأكد من عمل الترقية.

## <a name="watch-connect-your-pc-to-microsoft-365-business"></a>شاهد: الاتصال الكمبيوتر الشخصي Microsoft 365 Business

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3yXh3] 

إذا وجدت هذا الفيديو مفيدا، فتحقق من سلسلة التدريب الكاملة للشركات الصغيرة وتلك الجديدة [Microsoft 365.](../../business-video/index.yml)
  
## <a name="join-windows-10-devices-to-your-organizations-azure-ad"></a>الانضمام Windows 10 الأجهزة إلى Azure AD الخاص مؤسستك

عند ترقية Windows الأجهزة في مؤسستك إلى تحديث المبدعين ل Windows 10 Pro أو تشغيل تحديث المبدعين ل Windows 10 Pro بالفعل، يمكنك ضم هذه الأجهزة إلى Azure Active Directory الخاص مؤسستك. بمجرد انضمام الأجهزة، سيتم ترقيتها تلقائيا إلى Windows 10 Business، وهو جزء من اشتراكك Microsoft 365 Business Premium الاشتراك.
  
### <a name="for-a-brand-new-or-newly-upgraded-windows-10-pro-device"></a>لجهاز جديد أو تمت ترقيته Windows 10 Pro جديد

لجهاز جديد تماما يعمل Windows 10 Pro Creators Update، أو لجهاز تمت ترقيته إلى Windows 10 Pro Creators Update ولكنه لم يمر عبر Windows 10، اتبع الخطوات التالية.
  
1. انتقل إلى Windows 10 الجهاز حتى تصل إلى الصفحة **كيف تريد الإعداد؟** 
    
    ![في الصفحة كيف تريد إعداد، اختر إعداد لمنظمه.](../../media/1b0b2dba-00bb-4a99-a729-441479220cb7.png)
  
2. هنا، **اختر إعداد لمنظمه** ثم أدخل اسم المستخدم وكلمة المرور Microsoft 365 Business Premium. 
    
3. إنهاء Windows 10 الجهاز.
    
   بعد أن تنجز عملك، سيتصل المستخدم ب Azure AD الخاص بالمستخدم. راجع [التحقق من اتصال الجهاز ب Azure AD](#verify-the-device-is-connected-to-azure-ad) للتأكد من ذلك. 
  
### <a name="for-a-device-already-set-up-and-running-windows-10-pro"></a>لجهاز تم إعداده وتشغيله Windows 10 Pro

 **الاتصال المستخدمين إلى Azure AD:**
  
1. في الكمبيوتر الشخصي الخاص Windows المستخدم، الذي يتم تشغيله في Windows 10 Pro، الإصدار 1703 (تحديث المبدعين) (راجع المتطلبات الأساسية، انقر فوق شعار Windows[](../security-and-compliance/pre-requisites-for-data-protection.md)، ثم أيقونة الإعدادات.
  
   ![في قائمة البدء، انقر Windows الإعدادات الأيقونة.](../../media/74e1ce9a-1554-4761-beb9-330b176e9b9d.png)
  
2. في **الإعدادات**، انتقل إلى **حسابات**.
  
   ![في Windows الإعدادات، انتقل إلى حسابات.](../../media/472fd688-d111-4788-9fbb-56a00fbdc24d.png)
  
3. على **صفحة المعلومات**، انقر فوق **الوصول إلى موقع العمل أو** \> **المدرسة الاتصال**.
  
   ![اختر الاتصال ضمن Access للعمل أو المدرسة.](../../media/af3a4e3f-f9b9-4969-b3e2-4ef99308090c.png)
  
4. في مربع **الحوار إعداد حساب** العمل أو المدرسة، ضمن **إجراءات** بديلة، اختر **الانضمام إلى هذا الجهاز إلى Azure Active Directory**.
  
   ![انقر فوق ضم هذا الجهاز إلى Azure Active Directory.](../../media/fb709a1b-05a9-4750-9cb9-e097f4412cba.png)
  
5. في **الصفحة لنحصل على دخولك**، أدخل حساب العمل أو المدرسة **التالي**\>.
  
   في الصفحة **إدخال كلمة المرور** ، أدخل كلمة المرور \> **تسجيل الدخول**.
  
   ![أدخل البريد الإلكتروني الخاص بالعمل أو المدرسة على الصفحة لنحصل على دخولك.](../../media/f70eb148-b1d2-4ba3-be38-7317eaf0321a.png)
  
6. في صفحة **تأكد من أن هذه هي مؤسستك** ، تحقق من صحة المعلومات، واختر **انضمام**.
  
   في **مجموعة أنت الآن!** ، اختر **تم**.
  
   ![على الشاشة تأكد من أن هذه هي شاشة مؤسستك، اختر انضمام.](../../media/c749c0a2-5191-4347-a451-c062682aa1fb.png)
  
إذا قمت بتحميل الملفات إلى OneDrive for Business، فزامنتها مرة أخرى. إذا استخدمت أداة جهة خارجية لترحيل ملفات التعريف والملفات، فزامنها أيضا إلى ملف التعريف الجديد.
  
## <a name="verify-the-device-is-connected-to-azure-ad"></a>التحقق من اتصال الجهاز ب Azure AD

للتحقق من حالة المزامنة، في صفحة **Access** للعمل أو المدرسة في الإعدادات، حدد المنطقة متصل **ب _** \<organization name\> _ للكشف عن الأزرار **معلومات وقطع** **الاتصال**. اختر **معلومات** للحصول على حالة المزامنة. 
  
في صفحة **حالة المزامنة** ، اختر **مزامنة** للحصول على أحدث سياسات إدارة أجهزة المحمول على الكمبيوتر الشخصي.
  
لبدء استخدام حساب Microsoft 365 Business Premium، انتقل إلى الزر Windows البدء، وانقر بزر الماوس  الأيمن فوق صورة الحساب الحالي، ثم **قم بتبديل الحساب**. سجل الدخول باستخدام البريد الإلكتروني وكلمة المرور في مؤسستك.
  
![انقر فوق الزر معلومات لعرض حالة المزامنة.](../../media/818f7043-adbf-402a-844a-59d50034911d.png)
  
## <a name="verify-the-pc-is-upgraded-to-windows-10-business"></a>تحقق من ترقية الكمبيوتر الشخصي إلى Windows 10 Business

تحقق من ترقية الأجهزة Windows 10 Azure AD إلى Windows 10 Business كجزء من Microsoft 365 Business Premium اشتراكك.
  
1. انتقل **إلى الإعدادات** \> **حول** \> **النظام**.
    
2. تأكد من أن **الإصدار** **يعرض Windows 10 Business**.
    
    ![تحقق من Windows إصدار Windows 10 Business.](../../media/ff660fc8-d3ba-431b-89a5-f5abded96c4d.png)
  
## <a name="next-steps"></a>الخطوات التالية

لإعداد أجهزتك المحمولة، راجع إعداد الأجهزة [المحمولة للمستخدمين Microsoft 365 Business Premium،](set-up-mobile-devices.md) 

لزيادة الحماية، راجع أفضل [10 طرق لتأمين Microsoft 365 لخطط الأعمال](../security-and-compliance/secure-your-business-data.md).
  
