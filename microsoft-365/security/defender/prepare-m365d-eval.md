---
title: تحضير بيئة Microsoft 365 Defender التجريبية
description: إعداد تسجيل الخروج من المساهمين والم المخططات الزمنية والاعتبارات الخاصة بالبيئة وأمر الاعتماد عند إعداد Microsoft 365 Defender الإصدار التجريبي أو بيئة الإصدار التجريبي
keywords: Microsoft 365 Defender التجريبية، Microsoft 365 Defender تجريبي، الإعداد لتشغيل مشروع تجريبي Microsoft 365 Defender، تشغيل تجربة Microsoft 365 Defender  المشروع، النشر، التحضير، المساهمين، المخطط الزمني، البيئة، نقطة النهاية، الخادم، الإدارة، الاعتماد
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
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
ms.openlocfilehash: 7ebb7074b0e06eda96d21142044bd8b9997e094b
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2021
ms.locfileid: "63573367"
---
# <a name="prepare-your-microsoft-365-defender-trial-lab-or-pilot-environment"></a>تحضير بيئة Microsoft 365 Defender التجريبية أو التجريبية

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

إن إنشاء Microsoft 365 Defender تجريبية أو معمل تجريبي ونشره عملية من ثلاث مراحل:

|![المرحلة 1: التحضير](../../media/phase-diagrams/prepare.png)<br/>المرحلة 1: التحضير |[![المرحلة الثانية: إعداد](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[المرحلة الثانية: إعداد](setup-m365deval.md) |[![المرحلة 3: Onboard](../../media/phase-diagrams/onboard.png)](config-m365d-eval.md)<br/>[المرحلة 3: Onboard](config-m365d-eval.md) | [![العودة إلى التجربة](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[العودة إلى دليل التشغيل التجريبي](m365d-pilot.md) |
|--|--|--|--|
|*أنت هنا!* | || |

أنت حاليا في مرحلة الإعداد.


الإعداد هو المفتاح لأي نشر ناجح. سيرشدك هذا القسم خلال ما تحتاج إلى وضعه في الاعتبار عند التحضير لإنشاء معمل تجريبي أو بيئة تجريبية Microsoft 365 Defender الإصدار.

## <a name="prerequisites"></a>المتطلبات الأساسية
تعرف على متطلبات الترخيص والأجهزة والبرامج وإعدادات التكوين الأخرى لتوفير Microsoft 365 Defender. راجع الحد الأدنى لمتطلبات Microsoft 365 Defender [](/microsoft-365/security/defender/prerequisites)[و Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements) و [Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) Office 365 [و Microsoft Defender for Identity](/azure-advanced-threat-protection/atp-prerequisites) [و Microsoft Cloud App Security](/azure-advanced-threat-protection/atp-prerequisites).

## <a name="stakeholders-and-sign-off"></a>المساهمين وتوقيع الخروج
تحديد جميع المساهمين المشاركين في المشروع والذين قد يحتاجون إلى تسجيل الخروج أو المراجعة أو البقاء على اطلاع، سواء لتقييم مشروع تجريبي أو تشغيله.

>[!NOTE]
>قد لا يكون لدى كل المؤسسات استحقاق مؤسسة الأمان للحصول على مثل هذه الأدوار. في مثل هذه الحالة، استشر فريق القيادة لديك حول مسؤوليات المراجعة والموافقة.

يمكنك إضافة مساهمين إلى الجدول أدناه بالشكل المناسب لمنظمتك.

-   SO = تسجيل الخروج على هذا المشروع

-   R = مراجعة هذا المشروع وتوفير الإدخال

-   I = مطلع على هذا المشروع

| الاسم                 | الدور                                                                                                                                                                                                          | الإجراء |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|
| إدخال الاسم والبريد الإلكتروني | **كبير موظفي أمن المعلومات (CISO)** ممثل تنفيذي يعمل كراعي داخل المؤسسة لنشر *التقنية الجديدة.*                                                  | SO     |
| إدخال الاسم والبريد الإلكتروني | رئيس مركز عمليات الدفاع عبر الإنترنت **(CDOC)** ممثل عن فريق CDOC المسؤول عن تحديد كيفية محاذاة هذا التغيير مع العمليات في فريق عمليات *أمان العملاء.*       | SO     |
| إدخال الاسم والبريد الإلكتروني | **مهندس الأمان** *ممثل عن فريق الأمان* المسؤول عن تحديد كيفية محاذاة هذا التغيير مع بنية الأمان الأساسية في المؤسسة.                         | R      |
| إدخال الاسم والبريد الإلكتروني | **Workplace Architect** *A representative from the IT team المسؤول عن تحديد كيفية محاذاة هذا التغيير مع بنية مكان العمل الأساسية في المؤسسة.*                             | R      |
| إدخال الاسم والبريد الإلكتروني | **محلل الأمان** ممثل عن فريق CDOC يمكنه تقديم ملاحظات حول قدرات الكشف وتجربة المستخدم وفوائد هذا التغيير بشكل *عام من منظور عمليات الأمان.* | I      |

## <a name="prepare-your-azure-active-directory"></a>تحضير Azure Active Directory
تخطي هذه الخطوة إذا قمت بالفعل بتمكين المزامنة بين Active Directory و Azure Active Directory في الموقع. راجع وثائق أفضل الممارسات الموجودة من Azure Active Directory. تم تحسين الخطوات التالية لتقييم مشروع تجريبي أو تشغيله Microsoft 365 Defender المشروع.

1. انتقل إلى [مدخل Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade) > **Azure AD الاتصال**. 
![صورة صفحة مدخل Azure Active Directory](../../media/mtp-eval-1.png) <br> 

2. انقر **فوق** **تنزيل من Microsoft Azure Active Directory الاتصال** ونقله إلى وحدة التحكم بالمجال.
![صورة صفحة تنزيل Azure Active Directoru الاتصال](../../media/mtp-eval-2.png) <br>

3. على وحدة التحكم بالمجال، اتبع معالج Azure Active Directory الاتصال. اقرأ شروط الترخيص وإشعار الخصوصية وحدد خانة الاختيار إذا وافقت. انقر فوق **متابعة**.
![صورة صفحة الترحيب في Azure AD الاتصال AD](../../media/mtp-eval-3.png) <br>

4. انتقل إلى **Express الإعدادات**.
![صورة صفحة Express الإعدادات](../../media/mtp-eval-4.png) <br>

5. أدخل بيانات اعتماد المسؤول العام. انقر فوق **التالي**.
![صورة الاتصال إلى صفحة Azure AD حيث يجب إدخال بيانات اعتماد المسؤول العام](../../media/mtp-eval-5.png) <br>

6. أدخل بيانات اعتماد مسؤول مؤسسة خدمات مجال Active Directory. انقر فوق **التالي**.
![صورة الاتصال إلى صفحة AD DS حيث يجب إدخال بيانات الاعتماد](../../media/mtp-eval-6.png) <br>

7. انقر **فوق** تثبيت لتأكيد التكوين.
![صورة لصفحة تأكيد التكوين](../../media/mtp-eval-7.png) <br>

8. تهانينا، لقد قمت بتكوين Azure Active Directory بنجاح الاتصال.
![صورة لصفحة Azure Active Directory تم تكوينها الاتصال بنجاح](../../media/mtp-eval-8.png) <br>

يمكنك الآن [إضافة مستخدمين ومجموعات إلى Active Directory](/azure-advanced-threat-protection/atp-playbook-setup-lab#bkmk_hydrate) [وتكوين نهج SAM-R](/azure-advanced-threat-protection/atp-playbook-setup-lab#configure-sam-r-capabilities-from-contosodc).  


## <a name="configuration-order"></a>ترتيب التكوين
يشير الجدول التالي إلى الترتيب الذي توصي به Microsoft لتكوين Microsoft 365 Defender لمختبر الإصدار التجريبي أو نشر بيئة الإصدار التجريبي.

| مكون                               | الوصف                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | ترتيب ترتيب التكوين |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
|Microsoft Defender Office 365|يحمي Microsoft Defender Office 365 مؤسستك من التهديدات الضارة التي تفرضها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون. <br> [التعرف على المزيد.](/microsoft-365/security/office-365-security/defender-for-office-365)                                                                                                                                                                                                                                             | 1                   |
|Microsoft Defender for Identity|يستخدم Microsoft Defender for Identity إشارات Active Directory لتحديد التهديدات المتقدمة والهويات المضرة والإجراءات الضارة ل insider الموجهة إلى مؤسستك والكشف عنها التحقيق فيها. <br> [تعرّف على المزيد](/azure-advanced-threat-protection/).| 2 |
|Microsoft Cloud App Security| Microsoft Cloud App Security هو وسيط أمان الوصول السحابي (CASB) الذي يعمل على عدة سحب. فهو يوفر رؤية غنية، والتحكم في تنقل البيانات، وتحليلات متطورة لتحديد مكافحة الهجمات الإلكترونية عبر جميع خدمات السحابة. <br> [تعرّف على المزيد](/cloud-app-security/).                                                                                                                                                                                                                                                                                                                                                                       |3                   |
|Microsoft Defender لنقطة النهاية | توفر قدرات Microsoft Defender الكشف عن تهديدات نقاط النهاية والرد عليها Endpoint اكتشافات متقدمة للهجمات تكون قريبة من الوقت الحقيقي و قابلة للتنفيذ. يمكن لمحللي الأمان إعطاء الأولوية للتنبيهات بفعالية، واكتساب الرؤية في النطاق الكامل للانتهاك، واتخاذ إجراءات الاستجابة للرد على التهديدات. <br> [التعرف على المزيد.](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)                                     |4                   |                                                                                                                                                                                                                                    

## <a name="next-step"></a>الخطوة التالية
|![المرحلة الثانية: الإعداد](../../media/setup.png) <br>[المرحلة الثانية: الإعداد](setup-m365deval.md) | إعداد بيئة Microsoft 365 Defender التجريبية أو التجريبية
|:-------|:-----|
