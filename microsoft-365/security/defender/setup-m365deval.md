---
title: إعداد معمل تجريبي أو بيئة تجريبية Microsoft 365 Defender
description: ثم قم بإعداد بيئة المختبر التجريبي Microsoft 365 Defender في Access Microsoft 365 Defender
keywords: إعداد تجريبي Microsoft 365 Defender، إعداد تجريبي Microsoft 365 Defender، جرب Microsoft 365 Defender، Microsoft 365 Defender إعداد مختبر التقييم
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
ms.openlocfilehash: 5d516a7062d8c6f617cee2a260f27ee896689f2c
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667329"
---
# <a name="set-up-your-microsoft-365-defender-trial-in-a-lab-environment"></a>إعداد الإصدار التجريبي Microsoft 365 Defender في بيئة معملية 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender 

يرشدك هذا الموضوع لإعداد بيئة مختبر مخصصة. للحصول على معلومات حول إعداد إصدار تجريبي في الإنتاج، راجع دليل [التقييم والإصدار التجريبي الجديد Microsoft 365 Defender](eval-overview.md). 

## <a name="create-an-office-365-e5-trial-tenant"></a>إنشاء مستأجر تجريبي Office 365 E5
>[!NOTE]
>إذا كان لديك بالفعل اشتراك Office 365 أو Azure Active Directory موجود، يمكنك تخطي خطوات إنشاء المستأجر التجريبي Office 365 E5.

1. انتقل إلى [مدخل منتج Office 365 E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab) وحدد **الإصدار التجريبي المجاني**.

   :::image type="content" source="../../media/mtp-eval-9.png" alt-text="صفحة الإصدار التجريبي المجاني Office 365 E5" lightbox="../../media/mtp-eval-9.png":::
  
2. أكمل التسجيل التجريبي عن طريق إدخال عنوان بريدك الإلكتروني (شخصي أو شركة). انقر فوق **"إعداد الحساب**".

   :::image type="content" source="../../media/mtp-eval-10.png" alt-text="صفحة إعداد التسجيل التجريبي Office 365 E5" lightbox="../../media/mtp-eval-10.png":::

3. املأ اسمك الأول واسم عائلتك ورقم هاتف العمل واسم الشركة وحجم الشركة والبلد أو المنطقة.  

   :::image type="content" source="../../media/mtp-eval-11.png" alt-text="صفحة إعداد التسجيل التجريبي Office 365 E5 تطلب تفاصيل الاسم والهاتف والشركة" lightbox="../../media/mtp-eval-11.png":::
   
   > [!NOTE]
   > يحدد البلد أو المنطقة التي عينتها هنا منطقة مركز البيانات التي ستتم استضافة Office 365 الخاص بك.
  
4. اختر تفضيل التحقق: من خلال رسالة نصية أو مكالمة. انقر فوق **"إرسال رمز التحقق**". 

   :::image type="content" source="../../media/mtp-eval-12.png" alt-text="صفحة إعداد التسجيل التجريبي Office 365 E5 تطلب تفضيل التحقق" lightbox="../../media/mtp-eval-12.png":::

5. قم بتعيين اسم المجال المخصص للمستأجر، ثم انقر فوق **"التالي**".

   :::image type="content" source="../../media/mtp-eval-13.png" alt-text="صفحة إعداد التسجيل التجريبي Office 365 E5 حيث يمكنك إعداد اسم المجال المخصص" lightbox="../../media/mtp-eval-13.png":::
 
6. قم بإعداد الهوية الأولى، والتي ستكون المسؤول العام للمستأجر. تعبئة **الاسم** **وكلمة المرور**. انقر فوق **"تسجيل".**

   :::image type="content" source="../../media/mtp-eval-14.png" alt-text="صفحة إعداد التسجيل التجريبي Office 365 E5 حيث يمكنك تعيين هوية عملك" lightbox="../../media/mtp-eval-14.png":::

7. انقر فوق **"الانتقال إلى الإعداد**" لإكمال توفير المستأجر التجريبي Office 365 E5.

   :::image type="content" source="../../media/mtp-eval-15.png" alt-text="صفحة إعداد التسجيل التجريبي Office 365 E5 المطالبة بالنقر فوق الزر &quot;الانتقال إلى الإعداد&quot;" lightbox="../../media/mtp-eval-15.png":::

8. الاتصال مجال شركتك إلى مستأجر Office 365. [اختياري] اختر **الاتصال مجال تملكه بالفعل** واكتب اسم مجالك. انقر فوق **التالي**.

   :::image type="content" source="../../media/mtp-eval-16.png" alt-text="صفحة إعداد Office 365 E5 حيث يجب تخصيص تسجيل الدخول والبريد الإلكتروني" lightbox="../../media/mtp-eval-16.png":::
 
9. أضف سجل TXT أو MX للتحقق من صحة ملكية المجال. بمجرد إضافة سجل TXT أو MX إلى مجالك، حدد **"التحقق".**

   :::image type="content" source="../../media/mtp-eval-17.png" alt-text="صفحة إعداد Office 365 E5 حيث يجب إضافة TXT من سجل MX للتحقق من مجالك" lightbox="../../media/mtp-eval-17.png":::
 
10. [اختياري] إنشاء المزيد من حسابات المستخدمين للمستأجر الخاص بك. يمكنك تخطي هذه الخطوة بالنقر فوق **"التالي**".

    :::image type="content" source="../../media/mtp-eval-18.png" alt-text="صفحة إعداد Office 365 E5 حيث يمكنك إضافة المزيد من المستخدمين" lightbox="../../media/mtp-eval-18.png":::
 
11. [اختياري] تنزيل تطبيقات Office. انقر فوق **"التالي** " لتخطي هذه الخطوة. 

    :::image type="content" source="../../media/mtp-eval-19.png" alt-text="صفحة Office 365 E5 حيث يمكنك تثبيت تطبيقات Office" lightbox="../../media/mtp-eval-19.png":::

12. [اختياري] ترحيل رسائل البريد الإلكتروني. مرة أخرى، يمكنك تخطي هذه الخطوة.

    :::image type="content" source="../../media/mtp-eval-20.png" alt-text="Office 365 E5 حيث يمكنك تعيين ما إذا كنت تريد ترحيل رسائل البريد الإلكتروني أم لا" lightbox="../../media/mtp-eval-20.png":::
 
13. اختر خدمات الإنترنت. حدد **Exchange** وانقر فوق **"التالي**". 

    :::image type="content" source="../../media/mtp-eval-21.png" alt-text="Office 365 E5 حيث يمكنك اختيار خدمات الإنترنت" lightbox="../../media/mtp-eval-21.png":::

14. أضف سجلات MX وCNAME وTXT إلى مجالك. عند الانتهاء، حدد **"التحقق".**

    :::image type="content" source="../../media/mtp-eval-22.png" alt-text="Office 365 E5 هنا يمكنك إضافة سجلات DNS" lightbox="../../media/mtp-eval-22.png":::
 
15. تهانينا، لقد أكملت توفير مستأجر Office 365 الخاص بك.

    :::image type="content" source="../../media/mtp-eval-23.png" alt-text="صفحة تأكيد اكتمال إعداد Office 365 E5" lightbox="../../media/mtp-eval-23.png":::
    

## <a name="enable-microsoft-365-trial-subscription"></a>تمكين الاشتراك التجريبي Microsoft 365

>[!NOTE]
>يوفر لك التسجيل للحصول على إصدار تجريبي 25 ترخيص مستخدم لاستخدامها لمدة شهر. راجع [تجربة اشتراك Microsoft 365 أو شراؤه](../../commerce/try-or-buy-microsoft-365.md) للحصول على التفاصيل.

1. من [مسؤول Microsoft 365 Center](https://admin.microsoft.com/)، انقر فوق **الفوترة** ثم انتقل إلى **خدمات الشراء**.

2. حدد **Microsoft 365 E5** وانقر فوق **"بدء الإصدار التجريبي المجاني**". 

   :::image type="content" source="../../media/mtp-eval-24.png" alt-text="Microsoft 365 E5 صفحة الإصدار التجريبي المجاني" lightbox="../../media/mtp-eval-24.png":::

3. اختر تفضيل التحقق: من خلال رسالة نصية أو مكالمة. بعد أن تقرر، أدخل رقم الهاتف، وحدد **"نصي** " أو **"اتصل بي** " وفقا للتحديد الذي حددته.

   :::image type="content" source="../../media/mtp-eval-25.png" alt-text="Microsoft 365 E5 بدء صفحة تجريبية مجانية تطلب تفاصيل جهة الاتصال لإرسال التعليمات البرمجية لإثبات أنك لست روبوتا" lightbox="../../media/mtp-eval-25.png":::
 
4. أدخل رمز التحقق وانقر فوق **"بدء الإصدار التجريبي المجاني**".

   :::image type="content" source="../../media/mtp-eval-26.png" alt-text="صفحة بدء الإصدار التجريبي المجاني Microsoft 365 E5 حيث يمكنك ملء رمز التحقق الذي أرسله النظام لإثبات أنك لست روبوتا" lightbox="../../media/mtp-eval-26.png":::

5. انقر فوق **"جرب الآن**" لتأكيد الإصدار التجريبي Microsoft 365 E5.

   :::image type="content" source="../../media/mtp-eval-27.png" alt-text="Microsoft 365 E5 بدء صفحة الإصدار التجريبي المجاني حيث يجب عليك بدء تشغيل الزر &quot;تجربة الآن&quot;" lightbox="../../media/mtp-eval-27.png":::
 
6. انتقل إلى **مستخدمي مسؤول Microsoft 365** **CenterUsersActive** >  > . حدد حساب المستخدم الخاص بك، وحدد **إدارة تراخيص المنتجات**، ثم قم بتبديل الترخيص من Office 365 E5 إلى **Microsoft 365 E5**. انقر فوق **حفظ**.

   :::image type="content" source="../../media/mtp-eval-28.png" alt-text="صفحة مسؤول Microsoft 365 Center حيث يمكنك تحديد ترخيص Microsoft 365 E5" lightbox="../../media/mtp-eval-28.png":::
 
7. حدد حساب المسؤول العام مرة أخرى ثم انقر فوق **"إدارة اسم المستخدم**".

   :::image type="content" source="../../media/mtp-eval-29.png" alt-text="صفحة &quot;مركز مسؤول Microsoft 365&quot; حيث يمكنك تحديد اسم المستخدم &quot;حساب&quot; و&quot;إدارة&quot;" lightbox="../../media/mtp-eval-29.png":::

8. [اختياري] قم بتغيير المجال من *onmicrosoft.com* إلى مجالك الخاص، استنادا إلى ما اخترته في الخطوات السابقة. انقر فوق **حفظ التغييرات**.

   :::image type="content" source="../../media/mtp-eval-30.png" alt-text="صفحة مسؤول Microsoft 365 Center حيث يمكنك تغيير تفضيلات المجال" lightbox="../../media/mtp-eval-30.png":::

## <a name="next-step"></a>الخطوة التالية
|[المرحلة 3: تكوين & الإلحاق](config-m365d-eval.md) | تكوين كل ركيزة Microsoft 365 Defender لمختبر تجريبي Microsoft 365 Defender أو بيئة تجريبية وإلحاق نقاط النهاية الخاصة بك.
|:-------|:-----|
