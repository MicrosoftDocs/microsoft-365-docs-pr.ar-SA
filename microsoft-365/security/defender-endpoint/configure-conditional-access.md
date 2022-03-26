---
title: تكوين الوصول الشرطي في Microsoft Defender لنقطة النهاية
description: تعرف على الخطوات التي تحتاج إلى تنفيذها في Intune Microsoft 365 Defender و Azure لتطبيق الوصول الشرطي
keywords: الوصول الشرطي، الشرطي، الوصول، مخاطر الجهاز، مستوى المخاطر، التكامل، تكامل intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8706f756b4e8d0ba87a747396e8f7ef71d66460c
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573323"
---
# <a name="configure-conditional-access-in-microsoft-defender-for-endpoint"></a>تكوين الوصول الشرطي في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يرشدك هذا القسم عبر كل الخطوات التي تحتاج إلى اتخاذها لتنفيذ "الوصول الشرطي" بشكل صحيح.

## <a name="before-you-begin"></a>قبل البدء

> [!WARNING]
> من المهم ملاحظة أن أجهزة Azure AD المسجلة غير معتمدة في هذا السيناريو.</br>
> يتم دعم أجهزة Intune التي تم تسجيلها فقط.

يجب أن تتأكد من أن جميع أجهزتك مسجله في Intune. يمكنك استخدام أي من الخيارات التالية لتسجيل الأجهزة في Intune:

- مسؤول تكنولوجيا المعلومات: لمزيد من المعلومات حول كيفية تمكين التسجيل التلقائي، راجع Windows [التسجيل](/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- المستخدم النهائي: لمزيد من المعلومات حول كيفية تسجيل جهاز Windows 10 Windows 11 في Intune، راجع تسجيل جهاز Windows 10 في [Intune](/intune/quickstart-enroll-windows-device)
- بديل للمستخدم النهائي: لمزيد من المعلومات حول الانضمام إلى مجال Azure AD، راجع كيفية [: تخطيط تنفيذ الانضمام إلى Azure AD](/azure/active-directory/devices/azureadjoin-plan).

هناك خطوات ستحتاج إلى اتخاذها Microsoft 365 Defender مدخل Intune ومدخل Azure AD.

من المهم ملاحظة الأدوار المطلوبة للوصول إلى هذه المداخل وتطبيق الوصول الشرطي:

- **Microsoft 365 Defender** - ستحتاج إلى تسجيل الدخول إلى المدخل باستخدام دور مسؤول عام ل تشغيل التكامل.
- **Intune** - ستحتاج إلى تسجيل الدخول إلى المدخل باستخدام حقوق مسؤول الأمان باستخدام أذونات الإدارة.
- **مدخل Azure AD** - ستحتاج إلى تسجيل الدخول كمسؤول عام أو مسؤول أمان أو مسؤول وصول شرطي.

> [!NOTE]
> ستحتاج إلى بيئة Microsoft Intune، مع إدارة Intune وأجهزة Azure AD Windows 10 Windows 11 الأجهزة.

اتخاذ الخطوات التالية لتمكين الوصول الشرطي:

- الخطوة 1: تشغيل Microsoft Intune من Microsoft 365 Defender
- الخطوة 2: تشغيل تكامل Defender for Endpoint في Intune
- الخطوة 3: إنشاء نهج التوافق في Intune
- الخطوة 4: تعيين النهج 
- الخطوة 5: إنشاء نهج الوصول الشرطي في Azure AD

### <a name="step-1-turn-on-the-microsoft-intune-connection"></a>الخطوة 1: تشغيل Microsoft Intune الاتصال

1. في جزء التنقل **، حدد الإعدادات** \> **نقاط النهاية** \>  \> الميزات المتقدمة **العامة** \> Microsoft Intune **الاتصال**.
2. تبديل إعداد Microsoft Intune إلى **"على**".
3. انقر **فوق حفظ التفضيلات**.

### <a name="step-2-turn-on-the-defender-for-endpoint-integration-in-intune"></a>الخطوة 2: تشغيل تكامل Defender for Endpoint في Intune

1. سجّل الدخول إلى [مدخل Azure](https://portal.azure.com).
2. حدد **توافق الأجهزة** \> **مع Microsoft Defender ATP**.
3. قم **بتعيين الاتصال Windows 10.0.15063+ إلى Microsoft Defender Advanced Threat Protection** إلى **On**.
4. انقر فوق **حفظ**.

### <a name="step-3-create-the-compliance-policy-in-intune"></a>الخطوة 3: إنشاء نهج التوافق في Intune

1. في مدخل [Azure،](https://portal.azure.com) حدد **كافة الخدمات**، وتصفية **على Intune****، ثم حدد** Microsoft Intune.
2. حدد **نهج توافق** \> **الجهاز** \> **إنشاء نهج**.
3. أدخل **اسما ووصفا**.
4. في **النظام الأساسي**، حدد Windows 10 **واللاحقة**.
5. في إعدادات **"حالة** الجهاز"، قم بتعيين يتطلب أن يكون الجهاز على مستوى تهديدات **الجهاز** أو تحته إلى المستوى المفضل لديك:

   - **مؤمن**: هذا المستوى هو الأكثر أمانا. لا يمكن أن يكون للجهاز أي تهديدات موجودة ولا يزال يمكنه الوصول إلى موارد الشركة. إذا تم العثور على أي تهديدات، يتم تقييم الجهاز على أنه غير متوافق.
   - **منخفض**: الجهاز متوافق في حالة وجود تهديدات منخفضة المستوى فقط. الأجهزة ذات مستويات المخاطر المتوسطة أو العالية غير متوافقة.
   - **متوسط**: يكون الجهاز متوافقا إذا كانت التهديدات التي يتم العثور عليها على الجهاز منخفضة أو متوسطة. إذا تم اكتشاف تهديدات عالية المستوى، يتم تحديد الجهاز على أنه غير متوافق.
   - **عال**: هذا المستوى هو الأقل أمانا، ويسمح بجميع مستويات التهديدات. وبالتالي، فإن الأجهزة ذات مستويات المخاطر العالية أو المتوسطة أو المنخفضة تعتبر متوافقة.

6. حدد **موافق****، وإنشاء** لحفظ التغييرات (وإنشاء النهج).

### <a name="step-4-assign-the-policy"></a>الخطوة 4: تعيين النهج

1. في مدخل [Azure،](https://portal.azure.com) حدد **كافة الخدمات**، وتصفية **على Intune****، ثم حدد** Microsoft Intune.
2. حدد **نهج توافق** \> **الجهاز>** حدد نهج توافق Microsoft Defender لنقطة النهاية.
3. حدد **الواجبات**.
4. قم بتضمين مجموعات Azure AD أو استبعادها لتعيين النهج لها.
5. لنشر النهج إلى المجموعات، حدد **حفظ**. يتم تقييم أجهزة المستخدمين المستهدفة بواسطة النهج للتوافق.

### <a name="step-5-create-an-azure-ad-conditional-access-policy"></a>الخطوة 5: إنشاء نهج الوصول الشرطي في Azure AD

1. في مدخل [Azure،](https://portal.azure.com) افتح **نهج الوصول الشرطي الجديد ل Azure Active Directory** \>  \> **.**
2. أدخل اسم **نهج**، وحدد **المستخدمون والمجموعات**. استخدم الخيارين تضمين أو استبعاد لإضافة مجموعاتك إلى النهج، وحدد **تم**.
3. حدد **تطبيقات السحابة**، واختر التطبيقات التي يجب حمايتها. على سبيل المثال، اختر **تحديد التطبيقات**، وحدد Office 365 SharePoint **عبر الإنترنت** **Office 365 Exchange Online**. حدد **تم** لحفظ التغييرات.

4. حدد **الشروط** \> **تطبيقات العميل** لتطبيق النهج على التطبيقات والمستعرضات. على سبيل المثال، حدد **نعم**، **ثم قم بتمكين** تطبيقات **المستعرض والأجهزة المحمولة والعملاء على سطح المكتب**. حدد **تم** لحفظ التغييرات.

5. حدد **منح** لتطبيق الوصول الشرطي استنادا إلى توافق الجهاز. على سبيل المثال، حدد **منح حق الوصول** \> **يتطلب وضع علامة على الجهاز كمتوافق**. اختر **تحديد** لحفظ التغييرات.

6. حدد **تمكين النهج**، ثم **إنشاء** لحفظ التغييرات.

لمزيد من المعلومات، راجع [فرض التوافق ل Microsoft Defender لنقطة النهاية باستخدام الوصول الشرطي في Intune](/intune/advanced-threat-protection).

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-belowfoldlink)
