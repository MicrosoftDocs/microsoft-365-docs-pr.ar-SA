---
title: تمكين أجهزة Windows 10 المنضمة إلى المجال لإدارة Microsoft 365 للأعمال
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: تعرف على كيفية تمكين Microsoft 365 لحماية أجهزة Windows 10 المحلية المنضمة إلى Active-Directory في بضع خطوات فقط.
ms.openlocfilehash: 427010f073eb86a7fe685335189550cf48ea9549
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893178"
---
# <a name="manage-windows-devices-with-microsoft-365-business-premium"></a>إدارة أجهزة Windows باستخدام Microsoft 365 Business Premium

إذا كانت مؤسستك تستخدم Windows Server Active Directory محليا، فيمكنك إعداد Microsoft 365 Business Premium لحماية أجهزة Windows، مع الحفاظ على الوصول إلى الموارد المحلية التي تتطلب مصادقة محلية.

لإعداد ذلك، قم بتنفيذ **الأجهزة المنضمة Azure AD المختلطة**. يتم ربط هذه الأجهزة بكل من Active Directory محلي وAzure Active Directory.

> [!NOTE]
> يتم طرح Microsoft Defender for Business للعملاء Microsoft 365 Business Premium، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../security/defender-business/mdb-overview.md).

## <a name="watch-configure-hybrid-azure-active-directory-join"></a>المراقبة: تكوين الانضمام إلى Hybrid Azure Active Directory

يصف هذا الفيديو الخطوات المتعلقة بكيفية إعداد هذا السيناريو الأكثر شيوعا، وهو مفصل أيضا في الخطوات التالية.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  
## <a name="before-you-begin"></a>قبل البدء

- مزامنة المستخدمين إلى Azure AD مع Azure AD Connect.
- إكمال مزامنة Azure AD Connect Organizational Unit (OU).
- تأكد من أن جميع مستخدمي المجال الذين تقوم مزامنتهم لديهم تراخيص Microsoft 365 Business Premium.

راجع [مزامنة مستخدمي المجال مع Microsoft 365](../admin/setup/manage-domain-users.md) للاطلاع على الخطوات.

## <a name="possible-device-actions-and-statuses"></a>إجراءات الجهاز وحالاته المحتملة
  
![في قائمة إجراءات الجهاز، يمكنك رؤية حالات الأجهزة.](./../media/a621c47e-45d9-4e1a-beb9-c03254d40c1d.png)

يمكن أن تحتوي الأجهزة والإجراءات المقترنة بها على الحالات التالية:
  
|**حاله**|**الوصف**|
|:-----|:-----|
|مدار من قبل Intune  |تتم إدارته بواسطة Microsoft 365 Business Premium.  |
|إيقاف معلق  |Microsoft 365 Business Premium تستعد لإزالة بيانات الشركة من الجهاز.  |
|إيقاف قيد التقدم  |يقوم Microsoft 365 Business Premium حاليا بإزالة بيانات الشركة من الجهاز.  |
|فشل التوقف  | فشل إجراء إزالة بيانات الشركة.  |
|تم إلغاء إيقافه  |تم إلغاء إجراء إيقاف.  |
|المسح معلق  |في انتظار إعادة تعيين المصنع للبدء.  |
|المسح قيد التقدم  |تم إصدار إعادة تعيين المصنع.  |
|فشل المسح  |تعذرت إعادة تعيين المصنع.  |
|تم إلغاء المسح  |تم إلغاء مسح المصنع.  |
|صحيه  |هناك إجراء معلق (أو قيد التقدم)، ولكن الجهاز لم يتم إيداعه لمدة أكثر من 30 يوما.  |
|حذف معلق  |تم تعليق إجراء الحذف.  |
|اكتشف  |لقد كشف Microsoft 365 Business Premium عن الجهاز.  |

## <a name="1-verify-mdm-authority-in-intune"></a>1. التحقق من هيئة إدارة أجهزة الهواتف المحمولة في Intune

انتقل إلى مركز إدارة Microsoft إدارة نقاط النهاية ([https://endpoint.microsoft.com](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview)) وحدد **تسجيل الجهاز**، ثم في صفحة **النظرة العامة**، تأكد من أن **مرجع MDM** هو **Intune**.

- إذا كانت **سلطة MDM** **بلا**، فانقر فوق **سلطة MDM** لتعيينها إلى **Intune**.
- إذا **كانت** **سلطة MDM** Microsoft Office 365، فانتقل إلى **أجهزة تسجيل** **الأجهزة** >  واستخدم مربع الحوار **"إضافة مرجع MDM**" على اليمين لإضافة سلطة إدارة أجهزة الهواتف المحمولة **Intune** (يتوفر مربع الحوار **"إضافة هيئة إدارة** أجهزة الهواتف المحمولة" فقط إذا تم تعيين **هيئة إدارة أجهزة الهواتف المحمولة** إلى Microsoft Office 365).

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. التحقق من تمكين Azure AD للانضمام إلى أجهزة الكمبيوتر

1. انتقل إلى مركز مسؤولي Microsoft 365 في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> **Azure Active Directory** وحدده (حدد إظهار الكل إذا لم يكن Azure Active Directory مرئيا) في قائمة **مراكز مسؤول**. 

2. في **مركز إدارة Azure Active Directory**، انتقل إلى **Azure Active Directory** ، واختر **الأجهزة** ثم **إعدادات الجهاز**.

3. التحقق من أن **المستخدمين قد ينضمون إلى الأجهزة إلى Azure AD** ممكن 

    1. لتمكين كافة المستخدمين، قم بتعيين إلى **الكل**.

    2. لتمكين مستخدمين محددين، قم بتعيينهم إلى **"محدد** " لتمكين مجموعة معينة من المستخدمين.

        - أضف مستخدمي المجال المطلوبين الذين تمت مزامنتهم في Azure AD إلى [مجموعة أمان](../admin/create-groups/create-groups.md).

        - اختر **"تحديد المجموعات** " لتمكين نطاق مستخدم MDM لمجموعة الأمان هذه.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. التحقق من تمكين Azure AD ل MDM

1. انتقل إلى مركز مسؤولي Microsoft 365 وحدد <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> **إدارة نقطة النهاية** (حدد **"إظهار الكل**" إذا **لم تكن إدارة نقاط النهاية** مرئية)

2. في **مركز إدارة Microsoft إدارة نقاط النهاية**، انتقل إلى "**التسجيل التلقائي لتسجيل** >  **أجهزة** > **Windows Windows** > ".

3. تحقق من تمكين نطاق مستخدم MDM.

    1. لتسجيل كافة أجهزة الكمبيوتر، قم **بتعيين الكل لتسجيل** كافة أجهزة الكمبيوتر الخاصة بالمستخدمين المتصلين بأجهزة الكمبيوتر Azure AD والجديدة تلقائيا عندما يضيف المستخدمون حساب عمل إلى Windows.
  
    2. تعيين إلى **"البعض** " لتسجيل أجهزة الكمبيوتر الخاصة بمجموعة معينة من المستخدمين.
  
        -  أضف مستخدمي المجال المطلوبين الذين تمت مزامنتهم في Azure AD إلى [مجموعة أمان](/admin/create-groups/create-groups.md).
  
       -  اختر **"تحديد المجموعات** " لتمكين نطاق مستخدم MDM لمجموعة الأمان هذه.

## <a name="4-create-the-required-resources"></a>4. إنشاء الموارد المطلوبة 

تم تبسيط تنفيذ المهام المطلوبة [لتكوين صلة Azure AD المختلطة](/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) من خلال استخدام [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) cmdlet الموجودة في الوحدة النمطية [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell. عند استدعاء أمر cmdlet هذا، سيقوم بإنشاء وتكوين نقطة اتصال الخدمة المطلوبة ونهج المجموعة.

يمكنك تثبيت هذه الوحدة النمطية عن طريق استدعاء ما يلي من مثيل PowerShell:

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> قم بتثبيت هذه الوحدة النمطية على Windows Server الذي يعمل Azure AD Connect.

لإنشاء نقطة اتصال الخدمة المطلوبة ونهج المجموعة، سوف تقوم باستدعاء  [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) cmdlet. ستحتاج إلى بيانات اعتماد المسؤول العمومي Microsoft 365 Business Premium عند تنفيذ هذه المهمة. عندما تكون جاهزا لإنشاء الموارد، قم باستدعاء ما يلي:

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

سيقوم الأمر الأول بإنشاء اتصال مع سحابة Microsoft، وعند مطالبتك، حدد بيانات اعتماد المسؤول العام Microsoft 365 Business Premium.

## <a name="5-link-the-group-policy"></a>5. ربط نهج المجموعة

1. في نهج المجموعة Management Console (GPMC)، انقر بزر الماوس الأيمن فوق الموقع حيث تريد ربط النهج وحدد *Link an existing GPO...* من قائمة السياق.

2. حدد النهج الذي تم إنشاؤه في الخطوة أعلاه، ثم انقر فوق **"موافق**".

## <a name="get-the-latest-administrative-templates"></a>الحصول على أحدث القوالب الإدارية

إذا لم يظهر النهج **تمكين تسجيل MDM التلقائي باستخدام بيانات اعتماد Azure AD الافتراضية**، فقد يرجع ذلك إلى عدم تثبيت ADMX Windows 10 أو الإصدار 1803 أو الإصدارات الأحدث. لإصلاح المشكلة، اتبع الخطوات التالية (ملاحظة: آخر MDM.admx متوافق مع الإصدارات السابقة):

1. Download: [Administrative Templates (.admx) for Windows 10 October 2020 Update (20H2)](https://www.microsoft.com/download/102157).

2. تثبيت الحزمة على وحدة التحكم بالمجال.

3. انتقل، استنادا إلى إصدار القوالب الإدارية إلى المجلد: **C:\Program Files (x86)\Microsoft نهج المجموعة\Windows 10 تحديث أكتوبر 2020 (20H2)**.

4. إعادة تسمية مجلد **تعريفات النهج** في المسار أعلاه إلى **PolicyDefinitions**.

5. انسخ مجلد **PolicyDefinitions** إلى مشاركة SYSVOL، الموجودة بشكل افتراضي في `C:\Windows\SYSVOL\domain\Policies`.

   إذا كنت تخطط لاستخدام مخزن نهج مركزي لمجالك بأكمله، أضف محتويات PolicyDefinitions هناك.

6. في حالة وجود العديد من وحدات التحكم بالمجال، انتظر حتى يقوم SYSVOL بالنسخ المتماثل حتى تتوفر النهج. سيعمل هذا الإجراء مع أي إصدار مستقبلي من القوالب الإدارية أيضا.

في هذه المرحلة، يجب أن تكون قادرا على رؤية النهج **تمكين تسجيل MDM التلقائي باستخدام بيانات اعتماد Azure AD الافتراضية** المتوفرة.

## <a name="related-content"></a>المحتويات ذات الصلة

- [مزامنة مستخدمي المجال Microsoft 365](../admin/setup/manage-domain-users.md)

- [إنشاء مجموعة في مركز الإدارة](../admin/create-groups/create-groups.md)

- [البرنامج التعليمي: تكوين الانضمام إلى Azure Active Directory المختلط للمجالات المدارة](/azure/active-directory/devices/hybrid-azuread-join-managed-domains)

- [إعداد كلمات مرور الخدمة الذاتية](../admin/add-users/let-users-reset-passwords.md)

- [إعداد إدارة مجموعة الخدمة الذاتية](/azure/active-directory/enterprise-users/groups-self-service-management)

- [أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>الهدف التالي

[الاستعداد لنشر عميل Office](m365bp-prepare-for-office-client-deployment.md)