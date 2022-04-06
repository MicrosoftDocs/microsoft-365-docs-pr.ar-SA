---
title: إعداد بيئة Microsoft 365 Defender التجريبية أو التجريبية
description: الوصول Microsoft 365 Defender ثم إعداد بيئة Microsoft 365 Defender التجريبية
keywords: Microsoft 365 Defender الإعداد التجريبي، Microsoft 365 Defender الإصدار التجريبي، جرب Microsoft 365 Defender، Microsoft 365 Defender معمل التقييم
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 681d9798c6f16f5829bdb4e5272abc3eac719a59
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500970"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>إعداد الإصدار التجريبي Microsoft 365 Defender في بيئة معمل 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender 

يرشدك هذا الموضوع لإعداد بيئة معمل مخصصة. للحصول على معلومات حول إعداد الإصدار التجريبي في الإنتاج، راجع دليل التقييم [Microsoft 365 Defender الجديد.](eval-overview.md) 

## <a name="create-an-office-365-e5-trial-tenant"></a>إنشاء مستأجر Office 365 E5 تجريبي
>[!NOTE]
>إذا كان لديك بالفعل اشتراك Office 365 Azure Active Directory، يمكنك تخطي Office 365 E5 إنشاء مستأجر تجريبي.

1. انتقل إلى مدخل Office 365 E5 [وحدد](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) **الإصدار التجريبي المجاني**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="صفحة Office 365 E5 تجريبية مجانية" lightbox="../../media/mtp-eval-9.png":::
  
2. أكمل التسجيل التجريبي بإدخال عنوان بريدك الإلكتروني (شخصي أو شركة). انقر **فوق إعداد الحساب**.

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="صفحة Office 365 E5 إعداد التسجيل التجريبي" lightbox="../../media/mtp-eval-10.png":::

3. قم بتعبئة اسمك الأول واسم عائلتك ورقم هاتف العمل واسم الشركة وحجم الشركة والبلد أو المنطقة.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="صفحة Office 365 E5 إعداد التسجيل التجريبي التي تطلب الاسم والهاتف وتفاصيل الشركة" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > تحدد البلد أو المنطقة التي قمت بتعيينها هنا منطقة مركز البيانات التي Office 365 استضافتها.
  
4. اختر تفضيل التحقق: من خلال رسالة نصية أو مكالمة. انقر **فوق إرسال رمز التحقق**. 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="صفحة Office 365 E5 إعداد التسجيل التجريبي التي تطلب تفضيلات التحقق" lightbox="../../media/mtp-eval-12.png":::

5. قم بتعيين اسم المجال المخصص للمستأجر، ثم انقر فوق **التالي**.

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="صفحة Office 365 E5 إعداد التسجيل التجريبي حيث يمكنك إعداد اسم المجال المخصص" lightbox="../../media/mtp-eval-13.png":::
 
6. قم بإعداد الهوية الأولى، التي ستكون المسؤول العام للمستأجر. تعبئة الاسم **وكلمة** **المرور**. انقر **فوق تسجيل**.

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="صفحة Office 365 E5 إعداد التسجيل التجريبي حيث يمكنك تعيين هوية العمل" lightbox="../../media/mtp-eval-14.png":::

7. انقر **فوق الانتقال إلى الإعداد** لإكمال Office 365 E5 المستأجر التجريبي.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="صفحة Office 365 E5 إعداد التسجيل التجريبي المطالبة بالنقر فوق الزر الانتقال إلى الإعداد" lightbox="../../media/mtp-eval-15.png":::

8. الاتصال مجال الشركة إلى Office 365 المستأجر. [اختياري] اختر **الاتصال مجال تملكه** بالفعل وا اكتب اسم مجالك. انقر فوق **التالي**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="صفحة Office 365 E5 الإعداد حيث يجب تخصيص تسجيل الدخول والبريد الإلكتروني" lightbox="../../media/mtp-eval-16.png":::
 
9. أضف سجل TXT أو MX للتحقق من ملكية المجال. بعد إضافة سجل TXT أو MX إلى مجالك، حدد **التحقق**.

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="صفحة Office 365 E5 حيث يجب إضافة سجل TXT ل MX للتحقق من مجالك" lightbox="../../media/mtp-eval-17.png":::
 
10. [اختياري] إنشاء المزيد من حسابات المستخدمين للمستأجر. يمكنك تخطي هذه الخطوة بالنقر فوق **التالي**.

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="صفحة Office 365 E5 الإعداد حيث يمكنك إضافة المزيد من المستخدمين" lightbox="../../media/mtp-eval-18.png":::
 
11. [اختياري] تنزيل Office التطبيقات. انقر **فوق التالي** لتخطي هذه الخطوة. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="صفحة Office 365 E5 حيث يمكنك تثبيت تطبيقاتك Office" lightbox="../../media/mtp-eval-19.png":::

12. [اختياري] ترحيل رسائل البريد الإلكتروني. مرة أخرى، يمكنك تخطي هذه الخطوة.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="يتم Office 365 E5 حيث يمكنك تعيين ما إذا كنت تريد ترحيل رسائل البريد الإلكتروني أم لا" lightbox="../../media/mtp-eval-20.png":::
 
13. اختر خدمات الإنترنت. حدد **Exchange** وانقر فوق **التالي**. 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="يتم Office 365 E5 حيث يمكنك اختيار خدمات الإنترنت" lightbox="../../media/mtp-eval-21.png":::

14. أضف سجلات MX و CNAME و TXT إلى مجالك. عند الانتهاء، حدد **التحقق**.

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="يمكنك Office 365 E5 هنا إضافة سجلات DNS" lightbox="../../media/mtp-eval-22.png":::
 
15. تهانينا، لقد أكملت توفير Office 365 المستأجر.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="صفحة Office 365 E5 تأكيد اكتمال الإعداد" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>تمكين Microsoft 365 التجريبي

>[!NOTE]
>يمنحك التسجيل للحصول على إصدار تجريبي 25 ترخيص مستخدم لاستخدامها لمدة شهر. راجع [تجربة اشتراك Microsoft 365 أو شراؤه](../../commerce/try-or-buy-microsoft-365.md) للحصول على التفاصيل.

1. من [مسؤول Microsoft 365،](https://admin.microsoft.com/) انقر فوق **فوترة** ثم انتقل إلى **شراء خدمات**.

2. حدد **Microsoft 365 E5** ثم انقر فوق **بدء تشغيل تجريبي مجاني**. 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="صفحة Microsoft 365 E5 الإصدار التجريبي المجاني" lightbox="../../media/mtp-eval-24.png":::

3. اختر تفضيل التحقق: من خلال رسالة نصية أو مكالمة. بمجرد أن تقرر ذلك، أدخل رقم الهاتف، وحدد **إرسال رسالة نصية إلي** أو **الاتصال** بي استنادا إلى التحديد الذي قمت به.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="صفحة Microsoft 365 E5 تجريبية مجانية تطلب تفاصيل جهة الاتصال لإرسال التعليمات البرمجية لإثبات أنك لست روبوتا" lightbox="../../media/mtp-eval-25.png":::
 
4. أدخل رمز التحقق وانقر **فوق بدء الإصدار التجريبي المجاني**.

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="صفحة Microsoft 365 E5 البدء التجريبي المجاني حيث يمكنك ملء رمز التحقق الذي أرسله النظام لإثبات أنك لست روبوتا" lightbox="../../media/mtp-eval-26.png":::

5. انقر **فوق تجربة الآن** لتأكيد Microsoft 365 E5 التجريبي.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="صفحة Microsoft 365 E5 بدء الإصدار التجريبي المجاني حيث يجب تسجيل الوقت على الزر &quot;تجربة الآن&quot; للبدء" lightbox="../../media/mtp-eval-27.png":::
 
6. انتقل إلى مسؤول Microsoft 365 **CenterUsersActive** >  > **.** حدد حساب المستخدم، وحدد **إدارة تراخيص المنتجات**، ثم بدل الترخيص من Office 365 E5 إلى **Microsoft 365 E5**. انقر فوق **حفظ**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="صفحة مسؤول Microsoft 365 المركز حيث يمكنك تحديد Microsoft 365 E5" lightbox="../../media/mtp-eval-28.png":::
 
7. حدد حساب المسؤول العام مرة أخرى ثم انقر فوق **إدارة اسم المستخدم**.

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="صفحة مسؤول Microsoft 365 المركز حيث يمكنك تحديد الحساب وإدارة اسم المستخدم" lightbox="../../media/mtp-eval-29.png":::

8. [اختياري] غير *المجال من onmicrosoft.com* إلى مجالك الخاص، استنادا إلى ما اخترته في الخطوات السابقة. انقر فوق **حفظ التغييرات**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="صفحة مسؤول Microsoft 365 الأعلى حيث يمكنك تغيير تفضيل المجال" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>الخطوة التالية
|[المرحلة 3: تكوين & Onboard](config-m365d-eval.md) | قم بتكوين كل Microsoft 365 Defender أساسية لبيئة Microsoft 365 Defender التجريبية أو الاختبارية وتهيئة نقاط النهاية.
|:-------|:-----|
