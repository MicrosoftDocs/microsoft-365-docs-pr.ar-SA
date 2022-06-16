---
title: تضمين ملف
description: تضمين ملف
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 31008df3e43c99f3a97dad3dce037b96e3b0c4b5
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66116188"
---
## <a name="prerequisites"></a>المتطلبات الأساسية

راجع الأقسام التالية للاطلاع على متطلبات إدارة الأمان لسيناريو Microsoft Defender لنقطة النهاية:

### <a name="environment"></a>البيئه

عند إلحاق جهاز Microsoft Defender لنقطة النهاية:


- يتم استطلاع الجهاز للحصول على حالة حضور إدارة نقاط النهاية حالية، وهو تسجيل إدارة أجهزة المحمول (MDM) إلى Intune
- ستمكن الأجهزة التي لا تحتوي على وجود إدارة نقاط النهاية ميزة "إدارة الأمان"
- يتم إنشاء ثقة باستخدام Azure Active Directory إذا لم تكن موجودة بالفعل
- يتم استخدام ثقة Azure Active Directory للتواصل مع إدارة نقاط النهاية (Intune) واسترداد النهج
- يتم فرض استرداد النهج من إدارة نقاط النهاية على الجهاز بواسطة Microsoft Defender لنقطة النهاية

### <a name="active-directory-requirements"></a>متطلبات Active Directory

عندما ينشئ جهاز مرتبط بمجال ثقة مع Azure Active Directory، يشار إلى هذا السيناريو باسم سيناريو *Hybrid Azure Active Directory Join* . تدعم إدارة الأمان Microsoft Defender لنقطة النهاية هذا السيناريو بشكل كامل مع المتطلبات التالية:

- يجب مزامنة الاتصال Azure Active Directory (AAD الاتصال) مع المستأجر المستخدم من Microsoft Defender لنقطة النهاية
- يجب تكوين Hybrid Azure Active Directory Join في بيئتك (إما من خلال Federation أو AAD الاتصال Sync)
- يجب أن تتضمن AAD الاتصال Sync عناصر الجهاز *في نطاق* المزامنة مع Azure Active Directory (عند الحاجة للانضمام)
- يجب تعديل قواعد الاتصال AAD للمزامنة [ل Server 2012 R2](/microsoft-365/security/defender-endpoint/troubleshoot-security-config-mgt?view=o365-worldwide#instructions-for-applying-computer-join-rule-in-aad-connect) (عند الحاجة إلى دعم Server 2012 R2)
- يجب أن تسجل جميع الأجهزة في Azure Active Directory للمستأجر الذي يستضيف Microsoft Defender لنقطة النهاية. لا يتم دعم سيناريوهات عبر المستأجرين. 

### <a name="connectivity-requirements"></a>متطلبات الاتصال

يجب أن يكون للأجهزة حق الوصول إلى نقاط النهاية التالية:

- `enterpriseregistration.windows.net`- لتسجيل Azure AD.
- `login.microsoftonline.com`- لتسجيل Azure AD.
- `*.dm.microsoft.com` - يدعم استخدام حرف بدل نقاط نهاية خدمة السحابة المستخدمة للتسجيل والإيداع وإعداد التقارير، والتي يمكن أن تتغير مع تحجيم الخدمة.

> [!Note]
> إذا كان فحص طبقة مأخذ التوصيل الآمنة (SSL) لمستخدمي مؤسستك، يجب استبعاد نقاط النهاية من الفحص.

### <a name="supported-platforms"></a>الأنظمة الأساسية المدعومة

يتم دعم نهج إدارة أمان Microsoft Defender لنقطة النهاية لأنظمة الأجهزة الأساسية التالية:

- Windows 10 Professional/Enterprise (مع [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows 11 Professional/Enterprise
- Windows Server 2012 R2 مع [Microsoft Defender لأجهزة Down-Level](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 مع [Microsoft Defender لأجهزة Down-Level](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 (مع [KB5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 (مع [KB5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>الترخيص والاشتراكات

لاستخدام إدارة الأمان Microsoft Defender لنقطة النهاية، تحتاج إلى:

- اشتراك يمنح تراخيص Microsoft Defender لنقطة النهاية، مثل Microsoft 365، أو ترخيص مستقل Microsoft Defender لنقطة النهاية فقط. كما يمنح الاشتراك الذي يمنح تراخيص Microsoft Defender لنقطة النهاية المستأجر حق الوصول إلى عقدة أمان نقطة النهاية لمركز إدارة إدارة نقاط النهاية من Microsoft.

  > [!NOTE]  
  > **استثناء**: إذا كان لديك حق الوصول إلى Microsoft Defender لنقطة النهاية كجزء من ترخيص Microsoft Defender for Cloud فقط (المعروف سابقا باسم Azure Security Center)، فلن تتوفر إدارة الأمان لوظائف Microsoft Defender لنقطة النهاية.

عقدة أمان نقطة النهاية هي المكان الذي ستقوم فيه بتكوين النهج ونشرها لإدارة Microsoft Defender لنقطة النهاية لأجهزتك ومراقبة حالة الجهاز.

للحصول على المعلومات الحالية حول الخيارات، راجع [الحد الأدنى من متطلبات Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>التصميم

الرسم التخطيطي التالي هو تمثيل تصوري لحل إدارة تكوين الأمان Microsoft Defender لنقطة النهاية.

:::image type="content" alt-text="تمثيل تصوري لحل إدارة تكوين الأمان Microsoft Defender لنقطة النهاية" source="../security/defender-endpoint/images/mde-architecture.png":::

1. الأجهزة التي يتم إلحاقها Microsoft Defender لنقطة النهاية.

2. يتم تأسيس ثقة بين كل جهاز Azure AD. عندما يكون لدى الجهاز ثقة موجودة، يتم استخدامه. عندما لا تكون الأجهزة مسجلة، يتم إنشاء ثقة جديدة.

3. تستخدم الأجهزة هويتها Azure AD للتواصل مع إدارة نقاط النهاية. تمكن هذه الهوية إدارة نقاط النهاية من Microsoft من توزيع النهج التي تستهدف الأجهزة عند إيداعها.

4. يقوم Defender لنقطة النهاية بالإبلاغ عن حالة النهج مرة أخرى إلى إدارة نقاط النهاية.

## <a name="which-solution-should-i-use"></a>ما الحل الذي يجب أن أستخدمه؟

يتضمن إدارة نقاط النهاية من Microsoft العديد من الأساليب وأنواع النهج لإدارة تكوين Defender لنقطة النهاية على الأجهزة.

عندما تتجاوز احتياجات حماية جهازك إدارة Defender لنقطة النهاية، راجع [نظرة عامة حول حماية الجهاز](/mem/intune/protect/device-protect) للتعرف على القدرات الإضافية التي يوفرها إدارة نقاط النهاية من Microsoft للمساعدة في حماية الأجهزة، بما في ذلك *توافق الأجهزة* *والتطبيقات المدارة* *ونهج حماية التطبيقات* والتكامل مع شركاء *الامتثال لجهات خارجية وشركاء الدفاع عن تهديدات الأجهزة المحمولة*.

يمكن أن يساعدك الجدول التالي على فهم النهج التي يمكنها تكوين إعدادات MDE المدعومة من قبل الأجهزة التي تتم إدارتها بواسطة سيناريوهات مختلفة. عند نشر نهج مدعوم لكل من *تكوين أمان MDE* *إدارة نقاط النهاية من Microsoft*، يمكن معالجة مثيل واحد من هذا النهج بواسطة الأجهزة التي تعمل Microsoft Defender لنقطة النهاية فقط والأجهزة التي تتم إدارتها بواسطة Intune أو Configuration Manager.

| إدارة نقاط النهاية من Microsoft  | عبء العمل |السياسات| تكوين أمان MDE  |  إدارة نقاط النهاية من Microsoft |
|----------------|----------------|-------------------|------------|
| أمان نقطة النهاية    | مكافحه الفيروسات   |     مكافحه الفيروسات           | ![دعم](../media/green-check.png)  | ![دعم](../media/green-check.png)  |
|                      | مكافحه الفيروسات   |   استثناءات برنامج الحماية من الفيروسات   | ![دعم](../media/green-check.png)  | ![دعم](../media/green-check.png)  |
|                      | مكافحه الفيروسات   | تجربة أمن Windows |                        | ![دعم](../media/green-check.png)  |
|                      | تشفير القرص   |     الكل |      | ![دعم](../media/green-check.png)  |
|                      | جدار حمايه   | جدار حمايه              | ![دعم](../media/green-check.png) | ![دعم](../media/green-check.png)  |
|                      | جدار حمايه | قواعد جدار الحماية                | ![دعم](../media/green-check.png) | ![دعم](../media/green-check.png)  |
|                      | الكشف عن نقطة النهاية والاستجابة لها   | الكشف عن نقطة النهاية والاستجابة لها | ![دعم](../media/green-check.png) | ![دعم](../media/green-check.png)  |
|                      | قواعد تقليل الأجزاء المعرضة للهجوم    |   الكل |          | ![دعم](../media/green-check.png)  |
|                      | حماية الحساب       |    الكل |     | ![دعم](../media/green-check.png)  |
|                      | توافق الجهاز     |   الكل |  | ![دعم](../media/green-check.png)  |
|                      | الوصول المشروط    |   الكل |  | ![دعم](../media/green-check.png)  |
|                      | أساسات الأمان      |  الكل |   | ![دعم](../media/green-check.png)  |

نهج **أمان نقطة النهاية** هي مجموعات منفصلة من الإعدادات المخصصة للاستخدام من قبل مسؤولي الأمان الذين يركزون على حماية الأجهزة في مؤسستك.

- تدير نهج **الحماية من الفيروسات** تكوينات الأمان الموجودة في Microsoft Defender لنقطة النهاية. راجع نهج  [الحماية من الفيروسات](/mem/intune/protect/endpoint-security-antivirus-policy) لأمان نقطة النهاية.
- تركز سياسات **تقليل الأجزاء المعرضة للهجوم** على تقليل الأماكن التي تكون فيها مؤسستك عرضة للتهديدات الإلكترونية والهجمات. لمزيد من المعلومات، راجع [نظرة عامة على تقليل الأجزاء المعرضة للهجوم](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) في وثائق الحماية من التهديدات Windows، وسياسة [تقليل الأجزاء المعرضة للهجوم](/mem/intune/protect/endpoint-security-asr-policy) لأمان نقطة النهاية.
- تدير **نهج الكشف عن نقطة النهاية والاستجابة** لها (الكشف التلقائي والاستجابة على النقط النهائية) قدرات Defender لنقطة النهاية التي توفر عمليات الكشف المتقدمة عن الهجمات التي تقترب من الوقت الحقيقي وقابلة للتنفيذ. استنادا إلى تكوينات الكشف التلقائي والاستجابة على النقط النهائية، يمكن لمحللين أمنيين تحديد أولويات التنبيهات بشكل فعال، والحصول على رؤية للنطاق الكامل للخرق، واتخاذ إجراءات الاستجابة لمعالجة التهديدات. راجع [نهج الكشف عن تهديدات نقاط النهاية والرد عليها](/mem/intune/protect/endpoint-security-edr-policy) لأمان نقطة النهاية.
- تركز نهج **جدار الحماية** على جدار حماية Defender على أجهزتك. راجع نهج [جدار الحماية](/mem/intune/protect/endpoint-security-firewall-policy) لأمان نقطة النهاية.
- تعمل **قواعد جدار** الحماية على تكوين قواعد متعددة المستويات لجدار الحماية، بما في ذلك منافذ وبروتوكولات وتطبيقات وشبكات معينة. راجع نهج [جدار الحماية](/mem/intune/protect/endpoint-security-firewall-policy) لأمان نقطة النهاية.
- تتضمن **أساسيات الأمان** إعدادات الأمان المكونة مسبقا التي تحدد وضع الأمان الموصى به من Microsoft لمنتجات مختلفة مثل Defender أو Edge أو Windows. التوصيات الافتراضية من فرق المنتجات ذات الصلة وتمكنك من نشر التكوين الآمن الموصى به بسرعة على الأجهزة. بينما يتم تكوين الإعدادات مسبقا في كل خط أساسي، يمكنك إنشاء مثيلات مخصصة لها لتحديد توقعات الأمان لمؤسستك. راجع [أساسيات الأمان](/mem/intune/protect/security-baselines) ل Intune.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>تكوين المستأجر لدعم Microsoft Defender لنقطة النهاية إدارة تكوين الأمان

لدعم Microsoft Defender لنقطة النهاية إدارة تكوين الأمان من خلال مركز إدارة إدارة نقاط النهاية من Microsoft، يجب تمكين الاتصال بينهما من داخل كل وحدة تحكم.

1. سجل الدخول إلى [مدخل Microsoft 365 Defender](https://security.microsoft.com/) وانتقل إلى نطاق **فرض إدارة** >  تكوين **الإعدادات** >  **Endpoints** >  وتمكين الأنظمة الأساسية لإدارة إعدادات الأمان:

   :::image type="content" source="../media/security-settings-mgt.png" alt-text="تمكين إدارة إعدادات Microsoft Defender لنقطة النهاية في وحدة تحكم Defender.":::
    
1. تكوين الوضع التجريبي وإعدادات المرجع Configuration Manager لتناسب احتياجات مؤسستك:

   :::image type="content" source="../media/pilot-CMAuthority-mde-settings-management-defender.png" alt-text="تكوين الوضع التجريبي لإدارة إعدادات نقطة النهاية في مدخل Microsoft 365 Defender.":::
   
  > [!TIP]
  > استخدم وضع الإصدار التجريبي وعلامات الجهاز المناسبة لاختبار الإطلاق التدريجي والتحقق من صحته على عدد صغير من الأجهزة. دون استخدام وضع الإصدار التجريبي، سيتم تسجيل أي جهاز يقع في النطاق الذي تم تكوينه تلقائيا.

1. تأكد من أن المستخدمين المعنيين لديهم أذونات لإدارة إعدادات أمان نقطة النهاية في إدارة نقاط النهاية من Microsoft أو منح هذه الأذونات عن طريق تكوين دور في مدخل Defender. انتقل إلى **عنصر إضافة الإعدادات** >  **Roles** > :

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="إنشاء دور جديد في مدخل Defender.":::

   > [!TIP]
   > يمكنك تعديل الأدوار الموجودة وإضافة الأذونات الضرورية مقابل إنشاء أدوار إضافية في Microsoft Defender لنقطة النهاية

1. عند تكوين الدور، أضف مستخدمين وتأكد من تحديد **إدارة إعدادات أمان نقطة النهاية في إدارة نقاط النهاية من Microsoft**:

   :::image type="content" source="../media/add-role.png" alt-text="منح المستخدمين أذونات لإدارة الإعدادات.":::

1. سجل الدخول إلى [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

1. حدد **أمان** >  نقطة النهاية **Microsoft Defender لنقطة النهاية**، ثم قم بتعيين **السماح Microsoft Defender لنقطة النهاية لفرض تكوينات أمان نقطة النهاية (معاينة)** إلى **تشغيل**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="تمكين إدارة إعدادات Microsoft Defender لنقطة النهاية في مركز إدارة إدارة نقاط النهاية من Microsoft.":::

   عند تعيين هذا الخيار إلى *"تشغيل"*، ستتأهل جميع الأجهزة الموجودة في نطاق النظام الأساسي في Microsoft Defender لنقطة النهاية التي لا تديرها إدارة نقاط النهاية من Microsoft لإلحاقها Microsoft Defender لنقطة النهاية.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>إلحاق الأجهزة Microsoft Defender لنقطة النهاية

يدعم Microsoft Defender لنقطة النهاية العديد من الخيارات لإلحاق الأجهزة. للحصول على الإرشادات [الحالية، راجع أدوات وأساليب الإلحاق للأجهزة Windows](/microsoft-365/security/defender-endpoint/security-config-management) في وثائق Defender لنقطة النهاية.



## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>التعاون مع Microsoft Endpoint Configuration Manager
في بعض البيئات قد يكون من المطلوب استخدام إدارة الأمان Microsoft Defender لنقطة النهاية مع [إرفاق مستأجر Configuration Manager](/mem/configmgr/tenant-attach/endpoint-security-get-started). إذا كنت تستخدم كليهما، فستحتاج إلى التحكم في النهج من خلال قناة واحدة، لأن استخدام أكثر من قناة واحدة يخلق فرصة للتعارضات والنتائج غير المرغوب فيها.

لدعم ذلك، قم بتكوين *إعدادات إدارة الأمان باستخدام Configuration Manager* التبديل إلى *إيقاف التشغيل*.  سجل الدخول إلى [مدخل Microsoft 365 Defender](https://security.microsoft.com/) وانتقل إلى نطاق **فرض إدارة** >  **تكوين** **الإعدادات** >  **Endpoints** > :

:::image type="content" source="../media/manage-security-settings-cfg-mgr.png" alt-text="إدارة إعدادات الأمان باستخدام إعداد Configuration Manager.":::

>[!NOTE]
>عند استخدام إدارة الأمان Microsoft Defender لنقطة النهاية مع Configuration Manager، يجب عزل نهج أمان نقطة النهاية إلى مستوى تحكم واحد. قد يؤدي التحكم في النهج من خلال القناتين إلى حدوث تعارضات ونتائج غير مرغوب فيها.


## <a name="create-azure-ad-groups"></a>إنشاء مجموعات Azure AD

بعد إلحاق الأجهزة ب Defender لنقطة النهاية، ستحتاج إلى إنشاء مجموعات أجهزة لدعم نشر النهج Microsoft Defender لنقطة النهاية.

لتحديد الأجهزة التي سجلت في Microsoft Defender لنقطة النهاية ولكن لا تتم إدارتها بواسطة Intune أو Configuration Manager:

1. سجل الدخول إلى [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. انتقل إلى **الأجهزة** > **كافة الأجهزة**، ثم حدد العمود **"مدار بواسطة** " لفرز طريقة عرض الأجهزة.

   الأجهزة التي تم إلحاقها Microsoft Defender لنقطة النهاية والتي تم تسجيلها ولكن لا تتم إدارتها بواسطة عرض Intune **Microsoft Defender لنقطة النهاية** في العمود *"مدار بواسطة*". هذه هي الأجهزة التي يمكن أن تتلقى سياسة لإدارة الأمان Microsoft Defender لنقطة النهاية.

   ستجد أيضا تسميتين للأجهزة التي تستخدم إدارة الأمان Microsoft Defender لنقطة النهاية:

   - **MDEJoined** - تمت إضافتها إلى الأجهزة المتصلة بالدليل كجزء من هذا السيناريو.
   - **MDEManaged** - تمت إضافتها إلى الأجهزة التي تستخدم سيناريو إدارة الأمان بشكل نشط. تتم إزالة هذه العلامة من الجهاز إذا توقف Defender for Endpoint عن إدارة تكوين الأمان.

يمكنك إنشاء مجموعات لهذه الأجهزة [في Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) أو [من داخل مركز إدارة إدارة نقاط النهاية من Microsoft](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>نهج النشر

بعد إنشاء مجموعة Azure AD واحدة أو أكثر تحتوي على أجهزة مدارة بواسطة Microsoft Defender لنقطة النهاية، يمكنك إنشاء النهج التالية لإدارة الأمان ونشرها Microsoft Defender لنقطة النهاية إلى تلك المجموعات:

- مكافحه الفيروسات
- جدار حمايه
- قواعد جدار الحماية
- الكشف عن نقطة النهاية والاستجابة لها

> [!TIP]
> تجنب نشر نهج متعددة تدير نفس الإعداد على جهاز.
>
> يدعم إدارة نقاط النهاية من Microsoft نشر مثيلات متعددة لكل نوع نهج أمان نقطة النهاية إلى نفس الجهاز، مع تلقي كل مثيل نهج من قبل الجهاز بشكل منفصل. لذلك، قد يتلقى الجهاز تكوينات منفصلة لنفس الإعداد من نهج مختلفة، ما يؤدي إلى حدوث تعارض. سيتم دمج بعض الإعدادات (مثل استثناءات الحماية من الفيروسات) على العميل وتطبيقها بنجاح.

1. سجل الدخول إلى [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. انتقل إلى **أمان نقطة النهاية** ثم حدد نوع النهج الذي تريد تكوينه، إما برنامج الحماية من الفيروسات أو جدار الحماية، ثم حدد **إنشاء نهج**.

3. أدخل الخصائص التالية أو نوع النهج الذي حددته:

   - لنهج الحماية من الفيروسات، حدد:
     - النظام الأساسي: **خادم Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **برنامج الحماية من الفيروسات من Microsoft Defender (معاينة)**

   - لنهج جدار الحماية، حدد:
     - النظام الأساسي: **خادم Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **جدار الحماية من Microsoft Defender (معاينة)**

   - بالنسبة لنهج قواعد جدار الحماية، حدد:
     - النظام الأساسي: **خادم Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **قواعد جدار الحماية من Microsoft Defender (معاينة)**

   - بالنسبة إلى نهج الكشف عن نقطة النهاية والاستجابة لها، حدد:
     - النظام الأساسي: **خادم Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **الكشف عن نقطة النهاية والاستجابة لها (معاينة)**

   >[!Note]
   > تنطبق ملفات التعريف هذه على كلا الجهازين الذين يتصلان من خلال إدارة الجهاز الأجهزة المحمولة (MDM) مع Microsoft Intune بالإضافة إلى الأجهزة التي تتصل باستخدام عميل Microsoft Defender لنقطة النهاية.
   >
   > تأكد من مراجعة الاستهداف والمجموعات حسب الضرورة.

4. حدد **"إنشاء**".

5. في صفحة **"الأساسيات** "، أدخل اسما ووصفا لملف التعريف، ثم اختر **"التالي**".

6. في صفحة **إعدادات التكوين** ، حدد الإعدادات التي تريد إدارتها باستخدام ملف التعريف هذا. لمعرفة المزيد حول أحد الإعدادات، قم بتوسيع مربع الحوار "معلوماته" وحدد الارتباط *"معرفة المزيد* " لعرض معلومات CSP للإعداد في الوثائق المتصلة.

   عند الانتهاء من تكوين الإعدادات، حدد **"التالي**".

7. في صفحة **"الواجبات**"، حدد مجموعات Azure AD التي ستتلقى ملف التعريف هذا. لمزيد من المعلومات حول تعيين ملفات التعريف، راجع [تعيين ملفات تعريف المستخدمين والجهاز](/mem/intune/configuration/device-profile-assign).

   حدد **"التالي** " للمتابعة.

   > [!TIP]
   >
   > - عوامل تصفية التعيين غير معتمدة لملفات تعريف إدارة تكوين الأمان.
   > - تنطبق *عناصر الجهاز* فقط على إدارة Microsoft Defender لنقطة النهاية. استهداف المستخدمين غير معتمد.
   > - سيتم تطبيق النهج التي تم تكوينها على كل من عملاء Microsoft Intune Microsoft Defender لنقطة النهاية

8. أكمل عملية إنشاء النهج ثم في صفحة **"Review + create** "، حدد **"Create**". يتم عرض ملف التعريف الجديد في القائمة عند تحديد نوع النهج لملف التعريف الذي أنشأته.

9. انتظر حتى يتم تعيين النهج واعرض إشارة نجاح إلى أنه تم تطبيق النهج.

10. يمكنك التحقق من أن الإعدادات قد تم تطبيقها محليا على العميل باستخدام الأداة المساعدة للأمر [Get-MpPreference](/powershell/module/defender/get-mppreference#examples) .
