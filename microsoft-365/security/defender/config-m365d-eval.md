---
title: تكوين Microsoft 365 Defender أساسية للمختبر التجريبي أو بيئة الإصدار التجريبي
description: قم Microsoft 365 Defender الأساسية، مثل Microsoft Defender ل Office 365 و Microsoft Defender ل Identity و Microsoft Cloud App Security و Microsoft Defender ل Endpoint، لمختبر الإصدار التجريبي أو بيئة الإصدار التجريبي.
keywords: تكوين Microsoft 365 Defender تجريبي، Microsoft 365 Defender تجريبي، Microsoft 365 Defender مشروع تجريبي، Microsoft 365 Defender أعمدة، Microsoft 365 Defender الأساسية
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e50210f02d14be33c357517515d456318aac4bb6
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2021
ms.locfileid: "63572304"
---
# <a name="configure-microsoft-365-defender-pillars-for-your-trial-lab-or-pilot-environment"></a>تكوين Microsoft 365 Defender أساسية لمختبرك التجريبي أو بيئة الإصدار التجريبي

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender


إن إنشاء Microsoft 365 Defender تجريبية أو معمل تجريبي ونشره عملية من ثلاث مراحل:

|[![المرحلة 1: التحضير](../../media/phase-diagrams/prepare.png)](prepare-m365d-eval.md)<br/>[المرحلة 1: التحضير](prepare-m365d-eval.md) |[![المرحلة الثانية: إعداد](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[المرحلة الثانية: إعداد](setup-m365deval.md) |![المرحلة 3: Onboard](../../media/phase-diagrams/onboard.png)<br/>المرحلة 3: Onboard | [![العودة إلى التجربة](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[العودة إلى دليل التشغيل التجريبي](m365d-pilot.md) |
|--|--|--|--|
|| |*أنت هنا!* | |

أنت حاليا في مرحلة التكوين.

الإعداد هو المفتاح لأي نشر ناجح. في هذه المقالة، سيتم إرشادك إلى النقاط التي ستحتاج إلى وضعها في الاعتبار عند التحضير لنشر Microsoft Defender لنقطة النهاية.

## <a name="microsoft-365-defender-pillars"></a>Microsoft 365 Defender الأساسية
Microsoft 365 Defender مكونة من أربعة أعمدة. على الرغم من أن أحد الأعمدة يمكن أن يوفر قيمة لأمن مؤسسة الشبكة، إلا أن تمكين Microsoft 365 Defender الأساسية الأربعة سيمنح مؤسستك أكبر قيمة.

![صورة of_Microsoft 365 Defender للمستخدمين، Microsoft Defender for Identity، لنقاط النهاية Microsoft Defender ل Endpoint، لتطبيقات السحابة، Microsoft Cloud App Security، والبيانات، Microsoft Defender Office 365](../../media/mtp/m365pillars.png)

سيرشدك هذا القسم لتكوين:

- Microsoft Defender Office 365
- Microsoft Defender for Identity
- Microsoft Cloud App Security
- Microsoft Defender لنقطة النهاية

## <a name="configure-microsoft-defender-for-office-365"></a>تكوين Microsoft Defender Office 365

> [!NOTE]
> تخطي هذه الخطوة إذا قمت بالفعل بتمكين Defender Office 365.

هناك وحدة نمطية في PowerShell تسمى Office 365 التكوين المستحسن للحماية المتقدمة من المخاطر *(ORCA)* التي تساعد على تحديد بعض هذه الإعدادات. عند التشغيل كمسؤول في المستأجر، سيساعد get-ORCAReport في إنشاء تقييم لإعدادات مكافحة البريد العشوائي و مكافحة التصيد الاحتيالي والرسائل الأخرى. يمكنك تنزيل هذه الوحدة النمطية من https://www.powershellgallery.com/packages/ORCA/.

1. انتقل إلى Office 365 [الأمان & مركز](https://protection.office.com/homepage) >  التوافق **إدارةPolicy** > .

   ![صفحة of_Office 365 Security & Compliance Center Threat](../../media/mtp-eval-32.png)

2. انقر **فوق مكافحة التصيد الاحتيالي**، وحدد **إنشاء** وملء اسم النهج ووصفه. انقر فوق **التالي**.

   ![صفحة نهج of_Office 365 Security & Compliance Center لمكافحة التصيد الاحتيالي حيث يمكنك تسمية نهجك](../../media/mtp-eval-33.png)

   > [!NOTE]
   > قم بتحرير نهج مكافحة التصيد الاحتيالي المتقدم في Microsoft Defender Office 365. تغيير **عتبة التصيد الاحتيالي المتقدمة** إلى **2 - مخادع**.

3. انقر فوق **القائمة المنسدلة إضافة** شرط وحدد مجالك (مجالاتك) كمجال مستلم. انقر فوق **التالي**.

   ![صورة of_Office 365 Security & مركز التوافق في صفحة نهج مكافحة التصيد الاحتيالي حيث يمكنك إضافة شرط لتطبيقه](../../media/mtp-eval-34.png)

4. راجع الإعدادات. انقر **فوق إنشاء هذا النهج** لتأكيده.

   ![صورة of_Office 365 Security & مركز التوافق لصفحة نهج مكافحة التصيد الاحتيالي حيث يمكنك مراجعة الإعدادات والنقر فوق الزر إنشاء هذا النهج](../../media/mtp-eval-35.png)

5. حدد **خزينة المرفقات** وحدد الخيار تشغيل **ATP** SharePoint OneDrive Microsoft Teams.

   ![صورة of_Office 365 Security & مركز التوافق حيث يمكنك تشغيل ATP ل SharePoint OneDrive و Microsoft Teams](../../media/mtp-eval-36.png)

6. انقر فوق الأيقونة + لإنشاء نهج مرفق آمن جديد، وطبقه كمجال مستلم على مجالاتك. انقر فوق **حفظ**.

   ![صورة of_Office 365 Security & Compliance Center حيث يمكنك إنشاء نهج مرفق آمن جديد](../../media/mtp-eval-37.png)

7. بعد ذلك، **حدد خزينة الارتباطات**، ثم انقر فوق أيقونة القلم لتحرير النهج الافتراضي.

8. تأكد من عدم تحديد  الخيار عدم تعقب عندما ينقر المستخدمون فوق ارتباطات آمنة، بينما يتم تحديد الخيارات المتبقية. راجع [خزينة الارتباطات للحصول](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365) على التفاصيل. انقر فوق **حفظ**.

   ![صورة of_Office 365 Security & مركز التوافق الذي يظهر أن الخيار عدم التعقب عندما ينقر المستخدمون فوق آمن غير محدد](../../media/mtp-eval-38.png)

9. بعد ذلك، حدد **نهج مكافحة البرامج الضارة** ، وحدد الإعداد الافتراضي، واختر أيقونة القلم الرصاص.

10. انقر **الإعدادات** وحدد **نعم، ثم استخدم** نص الإعلام الافتراضي لتمكين استجابة **الكشف عن البرامج الضارة**. تشغيل عامل **تصفية أنواع المرفقات** الشائعة. انقر فوق **حفظ**.

    ![صورة of_Office 365 Security & Compliance Center التي تظهر أن استجابة الكشف عن البرامج الضارة يتم تشغيلها مع إعلام افتراضي وتصفية أنواع المرفقات الشائعة](../../media/mtp-eval-39.png)

11. انتقل إلى Office 365 [الأمان & Compliance](https://protection.office.com/homepage) **CenterSearchAudit** >  >  **البحث** في السجل ثم قم تشغيل التدقيق.

    ![صفحة of_Office 365 Security & Compliance Center حيث يمكنك تشغيل البحث في سجل التدقيق](../../media/mtp-eval-40.png)

12. ادمج Microsoft Defender Office 365 مع Microsoft Defender لنقطة النهاية. انتقل إلى [Office 365 الأمان & مركز](https://protection.office.com/homepage) >  **التوافقييحدد** >  **إدارة Microsoft Defender ل Endpoint الإعدادات** في الزاوية العلوية اليسرى من الشاشة. في مربع الحوار اتصال Defender for Endpoint، قم **الاتصال إلى Microsoft Defender ل Endpoint**.

    ![صورة of_Office 365 Security & مركز التوافق حيث يمكنك تشغيل اتصال Microsoft Defender لنقطة النهاية](../../media/mtp-eval-41.png)

## <a name="configure-microsoft-defender-for-identity"></a>تكوين Microsoft Defender for Identity

> [!NOTE]
> تخطي هذه الخطوة إذا قمت بتمكين Microsoft Defender for Identity بالفعل

1. انتقل إلى Microsoft 365 [مركز >](https://security.microsoft.com/info) حدد **المزيد ResourcesMicrosoft** >  **Defender for Identity**.

   ![صورة of_Microsoft مركز الأمان 365 حيث يوجد خيار لفتح Microsoft Defender for Identity](../../media/mtp-eval-42.png)

2. انقر **فوق** إنشاء لبدء تشغيل معالج Microsoft Defender for Identity.

   ![صورة of_Microsoft معالج Defender for Identity حيث يجب النقر فوق الزر إنشاء](../../media/mtp-eval-43.png)

3. اختر **توفير اسم مستخدم وكلمة مرور للاتصال ب غابة Active Directory**.

   ![صورة of_Microsoft الترحيب في Defender for Identity](../../media/mtp-eval-44.png)

4. أدخل بيانات اعتماد Active Directory في الموقع. يمكن أن يكون هذا أي حساب مستخدم لديه حق الوصول للقراءة إلى Active Directory.

   ![صورة of_Microsoft خدمات دليل الهوية ل Defender for Identity حيث يجب وضع بيانات الاعتماد الخاصة بك](../../media/mtp-eval-45.png)

5. بعد ذلك، اختر **تنزيل إعداد المستشعر** ونقل الملف إلى وحدة التحكم بالمجال.

   ![صورة of_Microsoft Defender for Identity حيث يمكنك تحديد تنزيل إعداد المستشعر](../../media/mtp-eval-46.png)

6. نفذ إعداد مستشعر الهوية ل Microsoft Defender وابدأ باتباع المعالج.

   ![صورة of_Microsoft Defender for Identity حيث يجب النقر فوق التالي لمتابعة معالج مستشعر Microsoft Defender for Identity](../../media/mtp-eval-47.png)

7. انقر **فوق التالي** في نوع نشر المستشعر.

   ![صورة of_Microsoft Defender for Identity حيث يجب النقر فوق بجانب الانتقال إلى الصفحة التالية](../../media/mtp-eval-48.png)

8. انسخ مفتاح الوصول لأنك تحتاج إلى إدخاله التالي في المعالج.

   ![صفحة of_the أدوات استشعار الصور حيث يجب نسخ مفتاح الوصول الذي تحتاج إلى إدخاله في صفحة معالج إعداد مستشعر Microsoft Defender for Identity التالية](../../media/mtp-eval-49.png)

9. انسخ مفتاح الوصول إلى المعالج وانقر فوق **تثبيت**.

   ![صورة of_Microsoft معالج استشعار Defender for Identity حيث يجب توفير مفتاح الوصول ثم النقر فوق زر التثبيت](../../media/mtp-eval-50.png)

10. تهانينا، لقد قمت بتكوين Microsoft Defender for Identity بنجاح على وحدة تحكم المجال.

    ![صورة of_Microsoft تثبيت معالج استشعار Defender for Identity حيث يجب النقر فوق زر الانتهاء](../../media/mtp-eval-51.png)

11. ضمن المقطع [إعدادات Microsoft Defender for Identity](https://go.microsoft.com/fwlink/?linkid=2040449) ، حدد **Microsoft Defender ل Endpoint **، ثم قم تشغيل تبديل. انقر فوق **حفظ**.

    ![صورة of_the Microsoft Defender for Identity settings (إعدادات Microsoft Defender for Endpoint) حيث يجب تشغيل تشغيل Microsoft Defender لنقطة النهاية](../../media/mtp-eval-52.png)

## <a name="configure-microsoft-cloud-app-security"></a>تكوين Microsoft Cloud App Security

> [!NOTE]
> تخطي هذه الخطوة إذا قمت بتمكين Microsoft Cloud App Security.

1. انتقل إلى Microsoft 365 [مركز الأمان](https://security.microsoft.com/info) >  **موارد إضافية Microsoft Cloud App Security** > .

   ![صورة of_Microsoft 365 مركز الأمان حيث يمكنك رؤية بطاقة Microsoft Cloud App ويجب النقر فوق الزر فتح](../../media/mtp-eval-53.png)

2. في موجه المعلومات لدمج Microsoft Defender for Identity، حدد **تمكين تكامل بيانات Microsoft Defender for Identity**.

   ![مطالبة of_the لدمج Microsoft Defender for Identity حيث يجب تحديد الارتباط تمكين تكامل بيانات Microsoft Defender for Identity](../../media/mtp-eval-54.png)

   > [!NOTE]
   > إذا لم تشاهد هذه المطالبة، فقد يعني ذلك أن تكامل بيانات Microsoft Defender for Identity قد تم تمكينه بالفعل. ومع ذلك، إذا لم تكن متأكدا، فاتصل بمسؤول تكنولوجيا المعلومات لتأكيد ذلك.

3. انتقل إلى **الإعدادات**، قم تشغيل **تبديل تكامل Microsoft Defender for Identity**، ثم انقر فوق **حفظ**.

   ![صفحة of_the إعدادات الصورة حيث يجب تشغيل زر تبديل تكامل Microsoft Defender for Identity ثم انقر فوق حفظ](../../media/mtp-eval-55.png)

   > [!NOTE]
   > بالنسبة لمثيلات Microsoft Defender for Identity الجديدة، يتم تشغيل تبديل التكامل هذا تلقائيا. تأكد من تمكين تكامل Microsoft Defender for Identity قبل المتابعة إلى الخطوة التالية.

4. ضمن إعدادات اكتشاف السحابة، حدد **Microsoft Defender لتكامل نقطة النهاية**، ثم قم بتمكين التكامل. انقر فوق **حفظ**.

   ![صورة of_the Microsoft Defender لنقطة النهاية حيث يتم تحديد خانة الاختيار حظر التطبيقات غير الموقوفة ضمن تكامل Microsoft Defender لنقطة النهاية. انقر فوق حفظ.](../../media/mtp-eval-56.png)

5. ضمن إعدادات اكتشاف السحابة، حدد **إثراء المستخدم**، ثم قم بتمكين التكامل مع Azure Active Directory.

   ![صورة لمقسم إثراء المستخدم حيث يتم تحديد خانة الاختيار تحسين معرفات المستخدمين المكتشفة باستخدام أسماء مستخدم Azure Active Directory](../../media/mtp-eval-57.png)

## <a name="configure-microsoft-defender-for-endpoint"></a>تكوين Microsoft Defender لنقطة النهاية

> [!NOTE]
> تخطي هذه الخطوة إذا قمت بتمكين Microsoft Defender لنقطة النهاية بالفعل.

1. انتقل إلى Microsoft 365 [مركز الأمان](https://security.microsoft.com/info) >  **موارد إضافية مركز حماية Microsoft Defender** > . انقر **فوق فتح**.

   ![خيار of_Microsoft مركز أمان Defender في Microsoft 365 مركز الأمان](../../media/mtp-eval-58.png)

2. اتبع معالج Microsoft Defender لنقطة النهاية. انقر فوق **التالي**.

   ![صفحة معالج of_the مركز حماية Microsoft Defender الصور](../../media/mtp-eval-59.png)

3. اختر استنادا إلى موقع تخزين البيانات المفضل لديك ون نهج استبقاء البيانات وحجم المؤسسة وميزات الاشتراك في المعاينة.

   ![صورة of_the لتحديد بلد تخزين البيانات ون نهج الاستبقاء وحجم المؤسسة. انقر فوق التالي عند انتهاء عملية تحديد.](../../media/mtp-eval-60.png)

   > [!NOTE]
   > لا يمكنك تغيير بعض الإعدادات، مثل موقع تخزين البيانات، بعد ذلك.

   انقر فوق **التالي**.

4. انقر **فوق** متابعة وسوف توفر لك Microsoft Defender لمستأجر نقطة النهاية.

   ![صورة of_the يطالبك بالنقر فوق الزر متابعة لإنشاء مثيل السحابة](../../media/mtp-eval-61.png)

5. ادفع نقاط النهاية من خلال "إدارة نقاط النهاية من Microsoft المجموعة" أو عن طريق تشغيل برنامج نصي محلي إلى Microsoft Defender لنقطة النهاية. للتبسيط، يستخدم هذا الدليل البرنامج النصي المحلي.

6. انقر **فوق تنزيل الحزمة** ونسخ البرنامج النصي للتكوين إلى نقطة النهاية (نقاط النهاية).

   ![صورة of_page النقر فوق الزر تنزيل الحزمة لنسخ البرنامج النصي للتكرار إلى نقطة النهاية أو نقاط النهاية](../../media/mtp-eval-62.png)

7. في نقطة النهاية، قم بتشغيل البرنامج النصي للتكوين كمسؤول واختر Y.

   ![صورة of_the سطر الأوامر حيث تقوم بتشغيل البرنامج النصي للدفق واختر Y للمتابعة](../../media/mtp-eval-63.png)

8. تهانينا، لقد قمت بتكوين نقطة النهاية الأولى.

   ![تظهر of_the سطر الأوامر حيث تحصل على التأكيد على أنك قمت بتكوين نقطة النهاية الأولى. اضغط على أي مفتاح للمتابعة](../../media/mtp-eval-64.png)

9. انسخ اختبار الكشف من معالج Microsoft Defender for Endpoint.

   ![صورة of_the خطوة اختبار الكشف حيث يجب النقر فوق نسخ لنسخ البرنامج النصي لاختبار الكشف الذي يجب لصقه في موجه الأوامر](../../media/mtp-eval-65.png)

10. انسخ البرنامج النصي PowerShell إلى موجه أوامر مرتفع ثم اديره.

    ![صورة of_command حيث يجب نسخ البرنامج النصي PowerShell إلى موجه أوامر مرتفع وتشغيله](../../media/mtp-eval-66.png)

11. حدد **بدء استخدام Microsoft Defender لنقطة النهاية** من المعالج.

    ![مطالبة of_the الصورة من المعالج حيث يجب النقر فوق بدء استخدام Microsoft Defender لنقطة النهاية](../../media/mtp-eval-67.png)

12. تفضل بزيارة [مركز حماية Microsoft Defender](https://securitycenter.windows.com/). انتقل إلى **الإعدادات** ثم حدد **الميزات المتقدمة**.

    ![قائمة of_Microsoft "مركز أمان الإعدادات Defender" حيث يجب تحديد الميزات المتقدمة](../../media/mtp-eval-68.png)

13. قم تشغيل التكامل مع **Microsoft Defender for Identity**.

    ![صورة of_Microsoft مركز حماية Defender المتقدمة، تبديل خيار Microsoft Defender للهوية الذي تحتاج إلى تشغيله](../../media/mtp-eval-69.png)

14. قم تشغيل التكامل مع Office 365 **المخاطر.**

    ![ميزات of_Microsoft مركز أمان Defender المتقدمة، Office 365 خيار "معلومات المخاطر" التي تحتاج إلى تشغيلها](../../media/mtp-eval-70.png)

15. تشغيل **التكامل مع Microsoft Cloud App Security**.

    ![صورة of_Microsoft مركز أمان Defender المتقدمة، Microsoft Cloud App Security تبديل الخيار الذي تحتاج إلى تشغيله](../../media/mtp-eval-71.png)

16. قم بالتمرير لأسفل وانقر فوق **حفظ التفضيلات** لتأكيد عمليات التكامل الجديدة.

    ![زر of_Save تفضيلات الصورة التي تحتاج إلى النقر فوقها](../../media/mtp-eval-72.png)

## <a name="start-the-microsoft-365-defender-service"></a>بدء Microsoft 365 Defender الخدمة

> [!NOTE]
> بدءا من 1 يونيو 2020، تقوم Microsoft تلقائيا بتمكين Microsoft 365 Defender لجميع المستأجرين المؤهلين. راجع [مقالة مجتمع Microsoft التقني هذه حول أهلية الترخيص](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/microsoft-threat-protection-will-automatically-turn-on-for/ba-p/1345426) للحصول على التفاصيل.

انتقل إلى [Microsoft 365 الأمان](https://security.microsoft.com/homepage). انتقل إلى **الإعدادات** **ثم حدد Microsoft 365 Defender**.

![لقطة of_Microsoft خيار 365 Defender من Microsoft 365 "مركز الإعدادات"](../../media/mtp-eval-72b.png)

للحصول على إرشادات أكثر شمولية، راجع [تشغيل Microsoft 365 Defender](m365d-enable.md).

تهانينا! لقد أنشأت للتو بيئة تجريبية أو Microsoft 365 Defender تجريبية! يمكنك الآن التعرف على واجهة مستخدم Microsoft 365 Defender! تعرف على ما يمكنك تعلمه من Microsoft 365 Defender التفاعلي ومعرفة كيفية استخدام كل لوحة معلومات لمهام عملية الأمان اليومية.

[الاطلاع على الدليل التفاعلي](https://aka.ms/MTP-Interactive-Guide)

بعد ذلك، يمكنك محاكاة هجوم وترى كيف تكتشف قدرات المنتجات المتقاطعة، وتنشئ تنبيهات، وتستجيب تلقائيا إلى هجوم بدون ملف على نقطة نهاية.

## <a name="next-step"></a>الخطوة التالية

- [إنشاء تنبيه اختباري](generate-test-alert.md) - تشغيل محاكاة هجوم في Microsoft 365 Defender تجريبي.
