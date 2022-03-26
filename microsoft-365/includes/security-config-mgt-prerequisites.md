---
title: تضمين ملف
description: تضمين ملف
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 2d48c4066cc1cde102fc395d7c532d26ea2a4db0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572050"
---
## <a name="prerequisites"></a>المتطلبات الأساسية

راجع الأقسام التالية للحصول على متطلبات سيناريو إدارة الأمان ل Microsoft Defender لنقطة النهاية:

### <a name="environment"></a>البيئة

عند ألواح الأجهزة إلى Microsoft Defender لنقطة النهاية:


- يتم استطلاع حالة حضور الجهاز إدارة نقاط النهاية، وهو تسجيل إدارة أجهزة المحمول (MDM) في Intune
- ستمكن الأجهزة إدارة نقاط النهاية حالة الحضور ميزة إدارة الأمان
- يتم إنشاء الثقة باستخدام Azure Active Directory إذا لم يكن أحدها موجودا بالفعل
- يتم استخدام الثقة في Azure Active Directory للتواصل مع إدارة نقاط النهاية (Intune) واسترداد النهج
- يتم فرض استرداد النهج إدارة نقاط النهاية على الجهاز بواسطة Microsoft Defender لنقطة النهاية

### <a name="active-directory-requirements"></a>متطلبات Active Directory

عندما ينشئ الجهاز المنضم إلى المجال الثقة مع Azure Active Directory، يشار إلى هذا السيناريو على أنه سيناريو انضمام *Azure Active Directory* المختلط. تدعم إدارة الأمان ل Microsoft Defender لنقطة النهاية هذا السيناريو بشكل كامل مع المتطلبات التالية:

- يجب مزامنة azure Active Directory الاتصال (AAD (دليل Azure النشط) الاتصال) مع المستأجر المستخدم من Microsoft Defender لنقطة النهاية
- يجب تكوين Azure Active Directory Join المختلط في بيئتك (إما من خلال الاتحاد أو AAD (دليل Azure النشط) الاتصال المزامنة)
- AAD (دليل Azure النشط) الاتصال يجب أن تتضمن المزامنة كائنات *الجهاز* في نطاق المزامنة مع Azure Active Directory (عند الحاجة للانضمام)
- AAD (دليل Azure النشط) الاتصال تعديل قواعد المزامنة ل Server 2012 R2 (عندما يكون دعم Server 2012 R2 مطلوبا)
- يجب أن يتم تسجيل جميع الأجهزة في Azure Active Directory للمستأجر الذي يستضيف Microsoft Defender ل Endpoint. سيناريوهات المستأجرين غير معتمدة. 

### <a name="connectivity-requirements"></a>متطلبات الاتصال

يجب أن يكون للأجهزة حق الوصول إلى نقاط النهاية التالية:

- `enterpriseregistration.windows.net` - لتسجيل Azure AD.
- `login.microsoftonline.com` - لتسجيل Azure AD.
- `*.dm.microsoft.com` - يدعم استخدام أحرف البدل نقاط نهاية الخدمة السحابية المستخدمة للتسجيل والتحقق من الوصول وإعداد التقارير، والتي يمكن أن تتغير مع تغيير مقياس الخدمة.

### <a name="supported-platforms"></a>الأنظمة الأساسية المعتمدة

يتم دعم سياسات Microsoft Defender لإدارة أمان نقطة النهاية ل الأنظمة الأساسية للجهاز التالية:

- Windows 10 Pro/Enterprise ([مع KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows 11 Pro/Enterprise
- Windows Server 2012 R2 مع [Microsoft Defender Down-Level الأجهزة](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 مع [Microsoft Defender Down-Level الأجهزة](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 ([مع KB5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 ([مع KB5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>الترخيص والاشتراكات

لاستخدام إدارة الأمان ل Microsoft Defender لنقطة النهاية، ستحتاج إلى:

- اشتراك يمنح تراخيص ل Microsoft Defender لنقطة النهاية، مثل Microsoft 365 أو ترخيص مستقل ل Microsoft Defender لنقطة النهاية فقط. كما يمنح الاشتراك الذي يمنح Microsoft Defender لتراخيص نقطة النهاية للمستأجر الخاص بك حق الوصول إلى عقدة أمان نقطة النهاية الخاصة إدارة نقاط النهاية من Microsoft مركز الإدارة.

  > [!NOTE]  
  > استثناء **: إذا** كان لديك حق الوصول إلى Microsoft Defender ل Endpoint كجزء من ترخيص Microsoft Defender for Cloud فقط (مركز أمان Azure سابقا)، فإن وظيفة إدارة الأمان ل Microsoft Defender ل Endpoint غير متوفرة.

عقدة أمان نقطة النهاية هي المكان الذي ستقوم فيه بتكوين سياسات ونشرها لإدارة Microsoft Defender ل Endpoint للأجهزة ومراقبة حالة الجهاز.

للحصول على معلومات حالية حول الخيارات، راجع [الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>التصميم

الرسم التخطيطي التالي هو تمثيل تصوري لحل إدارة تكوين أمان نقطة النهاية من Microsoft Defender.

:::image type="content" alt-text="تمثيل تصوري لحل إدارة تكوين أمان نقطة النهاية ل Microsoft Defender" source="../security/defender-endpoint/images/mde-architecture.png":::

1. الأجهزة المجهزة ل Microsoft Defender لنقطة النهاية.

2. يتم إنشاء الثقة بين كل جهاز و Azure AD. عندما يكون هناك جهاز لديه ثقة موجودة، يتم استخدامه. عندما لا تكون الأجهزة مسجلة، يتم إنشاء ثقة جديدة.

3. تستخدم الأجهزة هوية Azure AD الخاصة بها للتواصل مع إدارة نقاط النهاية. تمكن هذه الهوية إدارة نقاط النهاية من Microsoft توزيع النهج التي يتم استهدافها للأجهزة عند تسجيل الدخول.

4. سيرجع Defender for Endpoint حالة النهج إلى إدارة نقاط النهاية.

## <a name="which-solution-should-i-use"></a>ما الحل الذي يجب استخدامه؟

إدارة نقاط النهاية من Microsoft على العديد من الأساليب وأنواع النهج لإدارة تكوين Defender لنقطة النهاية على الأجهزة.

عندما تحتاج حماية جهازك إلى تجاوز إدارة Defender for Endpoint، راجع نظرة عامة حول حماية الجهاز للتعرف على الإمكانات الإضافية التي يوفرها إدارة نقاط النهاية من Microsoft للمساعدة في حماية الأجهزة، بما في ذلك توافق الأجهزة والتطبيقات المدارة ونهج حماية التطبيقات والتكامل مع شركاء الدفاع ضد التهديدات المتنقلة والتوافق مع جهة خارجية.[](/mem/intune/protect/device-protect) 

يمكن أن يساعدك الجدول التالي على فهم السياسات التي يمكنها تكوين إعدادات MDE المعتمدة بواسطة الأجهزة التي تديرها السيناريوهات المختلفة. عند نشر نهج معتمد لكل من تكوين أمان *MDE* و إدارة نقاط النهاية من Microsoft، يمكن معالجة مثيل واحد من هذا النهج بواسطة الأجهزة التي تقوم بتشغيل MDE فقط والأجهزة التي تتم إدارتها بواسطة Intune أو Configuration Manager.

| إدارة نقاط النهاية من Microsoft  | حمل العمل | تكوين أمان MDE  |  إدارة نقاط النهاية من Microsoft |
|----------------|----------------|-------------------|------------|
| أمان نقطة النهاية    | برنامج الحماية من الفيروسات                   | ![معتمد](../media/green-check.png)  | ![معتمد](../media/green-check.png)  |
|                      | تشفير القرص   |           | ![معتمد](../media/green-check.png)  |
|                      | جدار الحماية (ملف التعريف والقواعد)                | ![معتمد](../media/green-check.png) | ![معتمد](../media/green-check.png)  |
|                      | الكشف عن نقطة النهاية والاستجابة لها        | ![معتمد](../media/green-check.png) | ![معتمد](../media/green-check.png)  |
|                      | الحد من سطح الهجوم    |           | ![معتمد](../media/green-check.png)  |
|                      | حماية الحساب       |       | ![معتمد](../media/green-check.png)  |
|                      | توافق الجهاز     |   | ![معتمد](../media/green-check.png)  |
|                      | الوصول الشرطي    |   | ![معتمد](../media/green-check.png)  |
|                      | خطوط الأمان الأساسية      |   | ![معتمد](../media/green-check.png)  |

**إن سياسات أمان نقطة** النهاية هي مجموعات منفصلة من الإعدادات المخصصة للاستخدام من قبل المسؤولين عن الأمان الذين يركزون على حماية الأجهزة في مؤسستك.

- **تقوم** سياسات الحماية من الفيروسات بإدارة تكوينات الأمان الموجودة في Microsoft Defender لنقطة النهاية. راجع  [نهج الحماية](/mem/intune/protect/endpoint-security-antivirus-policy) من الفيروسات لأمن نقطة النهاية.
- **تركز سياسات الحد** من الهجمات على تقليل الأماكن التي تكون فيها مؤسستك عرضة للهجمات ولهجمات الإنترنت. لمزيد من المعلومات، راجع [](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) نظرة عامة حول الحد من سطح الهجوم في وثائق الحماية من المخاطر Windows، ونهج [](/mem/intune/protect/endpoint-security-asr-policy) الحد من سطح الهجوم لأمن نقطة النهاية.
- **تدير سياسات** الكشف عن نقاط النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) قدرات Defender لنقطة النهاية التي توفر عمليات الكشف المتقدمة عن الهجمات التي تكون قريبة من الوقت الحقيقي و قابلة للتنفيذ. استنادا إلى الكشف التلقائي والاستجابة على النقط النهائية، يمكن لمحللي الأمان تحديد أولويات التنبيهات بفعالية، واكتساب الرؤية في النطاق الكامل للمخالفة، واتخاذ إجراءات الاستجابة للرد على التهديدات. راجع [الكشف عن تهديدات نقاط النهاية والرد عليها](/mem/intune/protect/endpoint-security-edr-policy) نهج أمان نقطة النهاية.
- **تركز** سياسات جدار الحماية على جدار الحماية Defender على أجهزتك. راجع [نهج جدار](/mem/intune/protect/endpoint-security-firewall-policy) الحماية لأمن نقطة النهاية.
- **تقوم قواعد جدار** الحماية بتكوين القواعد الخاصة بجدار الحماية، بما في ذلك المنافذ والبروتوكولات والتطبيقات والشبكات المحددة. راجع [نهج جدار](/mem/intune/protect/endpoint-security-firewall-policy) الحماية لأمن نقطة النهاية.
- **تتضمن خطوط الأمان الأساسية** إعدادات أمان تم تكوينها مسبقا تحدد وضع الأمان الموصى به من قبل Microsoft لمنتجات مختلفة مثل Defender أو Edge أو Windows. تكون التوصيات الافتراضية من فرق المنتجات ذات الصلة وتمكنك من نشر التكوين الآمن الموصى به على الأجهزة بسرعة. على الرغم من أن الإعدادات تكون مسبقة الإعدادات في كل خط أساسي، يمكنك إنشاء مثيلات مخصصة لها لإنشاء توقعات الأمان لمؤسستك. راجع [خطوط الأمان الأساسية](/mem/intune/protect/security-baselines) ل Intune.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>تكوين المستأجر لدعم Microsoft Defender لإدارة تكوين أمان نقطة النهاية

لدعم إدارة تكوين أمان Microsoft Defender لنقطة النهاية إدارة نقاط النهاية من Microsoft مركز الإدارة، يجب تمكين التواصل بينها من داخل كل وحدة تحكم.

1. سجل الدخول [إلى Microsoft 365 Defender واذهب](https://security.microsoft.com/)  >  إلى الإعدادات **EndpointsConfiguration** >  **ManagementEnforcement** **Scope** >  وتمكين الأنظمة الأساسية لإدارة إعدادات الأمان:

   :::image type="content" source="../media/enable-mde-settings-management-defender.png" alt-text="تمكين إدارة إعدادات Microsoft Defender لنقطة النهاية في وحدة تحكم Defender.":::

2. تأكد من أن المستخدمين ذوي الصلة لديهم أذونات لإدارة إعدادات أمان نقاط النهاية في إدارة نقاط النهاية من Microsoft أو منح هذه الأذونات من خلال تكوين دور في مدخل Defender. انتقل إلى **الإعدادات** >  **RolesAdd** >  **العنصر**:

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="إنشاء دور جديد في مدخل Defender.":::

   > [!TIP]
   > يمكنك تعديل الأدوار الموجودة وإضافة الأذونات الضرورية مقابل إنشاء أدوار إضافية في Microsoft Defender لنقطة النهاية

3. عند تكوين الدور، أضف مستخدمين وتأكد من تحديد إدارة إعدادات أمان نقطة النهاية **في** إدارة نقاط النهاية من Microsoft:

   :::image type="content" source="../media/add-role.png" alt-text="منح المستخدمين أذونات لإدارة الإعدادات.":::

4. سجل الدخول إلى إدارة نقاط النهاية من Microsoft [الإدارة](https://go.microsoft.com/fwlink/?linkid=2109431).

5. حدد **نقطة النهاية securityMicrosoft** >  **Defender ل Endpoint**، ثم قم بتعيين **السماح ل Microsoft Defender لنقطة النهاية بفرض تكوينات أمان** نقطة النهاية (معاينة) على التشغيل.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="تمكين إدارة إعدادات Microsoft Defender لنقطة النهاية إدارة نقاط النهاية من Microsoft مركز الإدارة.":::

   عندما تقوم بتعيين هذا الخيار إلى *"* التشغيل"، فإن كل الأجهزة في نطاق النظام الأساسي في Microsoft Defender لنقطة النهاية التي لا يديرها إدارة نقاط النهاية من Microsoft ستكون مؤهلة للانصدار إلى Microsoft Defender ل Endpoint.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>الأجهزة المجهزة ل Microsoft Defender لنقطة النهاية

يدعم Microsoft Defender ل Endpoint العديد من الخيارات للأجهزة المجهزة. للحصول على الإرشادات الحالية، راجع [أدوات](/microsoft-365/security/defender-endpoint/security-config-management) وأساليب Windows الأجهزة في وثائق Defender for Endpoint.


> [!IMPORTANT]
> بعد ألواح الأجهزة مع Microsoft Defender لنقطة النهاية، يجب وضع علامة عليها باستخدام **MDE-Management** قبل أن تتمكن من التسجيل في إدارة الأمان ل Microsoft Defender ل Endpoint. لمزيد من المعلومات حول وضع علامات على الجهاز في MDE، راجع [*إنشاء علامات الجهاز وإدارتها*](/microsoft-365/security/defender-endpoint/machine-tags).


## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>التعاون مع Microsoft Endpoint Configuration Manager
عند استخدام "إدارة التكوين"، فإن أفضل مسار لإدارة نهج الأمان هو استخدام إرفاق مستأجر ["إدارة التكوين](/mem/configmgr/tenant-attach/endpoint-security-get-started)". في بعض البيئات، قد ترغب في استخدام إدارة الأمان ل Microsoft Defender. عند استخدام إدارة الأمان ل Microsoft Defender مع إدارة التكوين، يجب عزل نهج أمان نقطة النهاية إلى مستوى تحكم واحد. يؤدي التحكم في النهج عبر كلتا القناةين إلى إنشاء فرصة التعارضات والنتائج غير المرجوة.


## <a name="create-azure-ad-groups"></a>إنشاء مجموعات Azure AD

بعد الأجهزة التي يتم تشغيلها على Defender for Endpoint، ستحتاج إلى إنشاء مجموعات أجهزة لدعم نشر النهج ل Microsoft Defender لنقطة النهاية.

لتحديد الأجهزة التي تم تسجيلها في Microsoft Defender لنقطة النهاية ولكن لا يديرها Intune أو إدارة التكوين:

1. سجل الدخول إدارة نقاط النهاية من Microsoft [مركز الإدارة](https://go.microsoft.com/fwlink/?linkid=2109431).

2. انتقل إلى **الأجهزة** >  **كل الأجهزة**، ثم حدد العمود **مدار حسب** لفرز طريقة عرض الأجهزة.

   تعرض الأجهزة التي يتم تشغيلها على Microsoft Defender لنقطة النهاية والمسجلة ولكن لا يديرها Intune **Microsoft Defender لنقطة** النهاية في العمود *المدار بواسطة* . هذه هي الأجهزة التي يمكنها تلقي نهج لإدارة الأمان ل Microsoft Defender ل Endpoint.

   ستجد أيضا تسميتين للأجهزة التي تستخدم إدارة الأمان ل Microsoft Defender لنقطة النهاية:

   - **MDEJoined** - يضاف إلى الأجهزة التي تم ضمها إلى الدليل كجزء من هذا السيناريو.
   - **MDEManaged** - مضافة إلى الأجهزة التي تستخدم سيناريو إدارة الأمان بشكل نشط. تتم إزالة هذه العلامة من الجهاز إذا توقف Defender for Endpoint عن إدارة تكوين الأمان.

يمكنك إنشاء مجموعات لهذه الأجهزة [في Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) أو من [إدارة نقاط النهاية من Microsoft مركز الإدارة](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>نهج النشر

بعد إنشاء مجموعة Azure AD واحدة أو أكثر تحتوي على أجهزة مدارة بواسطة Microsoft Defender لنقطة النهاية، يمكنك إنشاء ونشر السياسات التالية لإدارة الأمان ل Microsoft Defender لنقطة النهاية لتلك المجموعات:

- برنامج الحماية من الفيروسات
- جدار الحماية
- قواعد جدار الحماية
- الكشف عن نقطة النهاية والاستجابة لها

> [!TIP]
> تجنب نشر عدة سياسات تدير الإعداد نفسه على جهاز.
>
> إدارة نقاط النهاية من Microsoft نشر مثيلات متعددة من كل نوع نهج أمان نقطة نهاية إلى الجهاز نفسه، مع تلقي كل مثيل نهج من قبل الجهاز بشكل منفصل. وبالتالي، قد يتلقى الجهاز تكوينات منفصلة لنفس الإعداد عن مختلف السياسات، مما يؤدي إلى تعارض. سيتم دمج بعض الإعدادات (مثل استثناءات برنامج الحماية من الفيروسات) على العميل وتطبيقها بنجاح.

1. سجل الدخول إلى إدارة نقاط النهاية من Microsoft [الإدارة](https://go.microsoft.com/fwlink/?linkid=2109431).

2. انتقل إلى **أمان نقطة النهاية** ثم حدد نوع النهج الذي تريد تكوينه، إما برنامج الحماية من الفيروسات أو جدار الحماية، ثم حدد **إنشاء نهج**.

3. أدخل الخصائص التالية أو نوع النهج الذي حددته:

   - بالنسبة إلى نهج الحماية من الفيروسات، حدد:
     - النظام الأساسي: **Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **برنامج الحماية من الفيروسات من Microsoft Defender (معاينة)**

   - بالنسبة إلى نهج جدار الحماية، حدد:
     - النظام الأساسي: **Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **جدار الحماية ل Microsoft Defender (معاينة)**

   - بالنسبة إلى نهج قواعد جدار الحماية، حدد:
     - النظام الأساسي: **Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **قواعد جدار حماية Microsoft Defender (معاينة)**

   - بالنسبة إلى نهج الكشف عن نقاط النهاية والاستجابة لها، حدد:
     - النظام الأساسي: **Windows 10 Windows 11 وخادم Windows (معاينة)**
     - ملف التعريف: **الكشف عن نقطة النهاية والاستجابة لها (معاينة)**

   >[!Note]
   > تنطبق ملفات التعريف هذه على كلا الجهازين الذين يتواصلون عبر إدارة أجهزة المحمول (MDM) مع Microsoft Intune بالإضافة إلى الأجهزة التي تتواصل باستخدام عميل Microsoft Defender for Endpoint.
   >
   > تأكد من مراجعة الاستهداف والمجموعات حسب الحاجة.

4. حدد **إنشاء**.

5. في صفحة **الأساسيات** ، أدخل اسما ووصفا لملف التعريف، ثم اختر **التالي**.

6. في **الصفحة إعدادات التكوين** ، حدد الإعدادات التي تريد إدارتها باستخدام ملف التعريف هذا. لمعرفة المزيد حول أحد الإعدادات، قم بتوسيع مربع حوار المعلومات الخاص به وحدد الارتباط معرفة المزيد لعرض معلومات CSP الخاصة بهذا الإعداد في الوثائق على الخط.

   عند انتهائك من تكوين الإعدادات، حدد **التالي**.

7. في صفحة **الواجبات** ، حدد مجموعات Azure AD التي ستتلقى ملف التعريف هذا. لمزيد من المعلومات حول تعيين ملفات التعريف، راجع [تعيين ملفات تعريف المستخدمين والجهاز](/mem/intune/configuration/device-profile-assign).

   حدد **التالي** للمتابعة.

   > [!TIP]
   >
   > - عوامل تصفية التعيين غير معتمدة لملفات تعريف إدارة تكوين الأمان.
   > - تنطبق *كائنات الجهاز* فقط على Microsoft Defender لإدارة نقاط النهاية. استهداف المستخدمين غير معتمد.
   > - سيتم تطبيق السياسات التي تم تكوينها على كل من Microsoft Intune و Microsoft Defender لعملاء Endpoint

8. أكمل عملية إنشاء النهج، ثم في الصفحة **مراجعة + إنشاء** ، حدد **إنشاء**. يتم عرض ملف التعريف الجديد في القائمة عند تحديد نوع النهج لملف التعريف الذي أنشأته.

9. انتظر حتى يتم تعيين النهج وانظر إشارة نجاح إلى أنه تم تطبيق النهج.

10. يمكنك التحقق من صحة تطبيق الإعدادات محليا على العميل باستخدام الأداة المساعدة لأوامر [Get-MpPreference](/powershell/module/defender/get-mppreference#examples) .
