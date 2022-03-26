---
title: إعداد الوصول إلى الموارد المحلية لسطح المكتب المدار من Microsoft
description: خطوات هامة للتأكد من أن Azure AD يمكنه التواصل مع AD في الموقع لتوفير المصادقة
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 3db3d469f7b417035e6ae11507c54c6bad871a89
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63567110"
---
# <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>إعداد الوصول إلى الموارد المحلية لسطح المكتب المدار من Microsoft

في Microsoft Managed Desktop، يتم تلقائيا ضم الأجهزة إلى Azure Active Directory (Azure AD). لهذا السبب، إذا كنت تستخدم Active Directory، فيجب عليك التأكد من أن الأجهزة المنضمة إلى Azure AD يمكنها التواصل مع Active Directory الخاص بك.

> [!NOTE]  
> *مختلط* لا يدعم Microsoft Managed Desktop انضمام Azure AD.

يتيح Azure Active Directory للمستخدمين الاستفادة من ميزة "مفردةSign-On (SSO). يعني تسجيل الدخول المفرد أنه لن يكون عليه عادة توفير بيانات الاعتماد في كل مرة يستخدم فيها الموارد.

للحصول على معلومات حول الانضمام إلى Azure Active Directory، راجع كيفية [: تخطيط تنفيذ الانضمام إلى Azure AD](/azure/active-directory/devices/azureadjoin-plan). للحصول على معلومات حول الخلفية Sign-On Single (SSO) على الأجهزة المنضمة إلى Azure AD، راجع كيفية عمل SSO للموارد المحلية على الأجهزة المنضمة إلى [Azure AD](/azure/active-directory/devices/azuread-join-sso#how-it-works).

تشرح هذه المقالة الأشياء التي يجب عليك التحقق فيها لضمان عمل التطبيقات والموارد الأخرى التي تعتمد على اتصال Active Directory المحلي بسلاسة مع Microsoft Managed Desktop.

## <a name="single-sign-on-for-on-premises-resources"></a>موارد Sign-On مفردة للموارد المحلية

يتم تمكين Sign-On مفردة (SSO) باستخدام UPN وكلمة المرور بشكل افتراضي على أجهزة سطح المكتب المدارة من Microsoft. ولكن يمكن للمستخدمين أيضا استخدام Windows Hello for Business، مما يتطلب بعض خطوات الإعداد الإضافية.

### <a name="single-sign-on-by-using-upn-and-password"></a>استخدام Sign-On باستخدام UPN وكلمة المرور

في معظم المؤسسات، سيكون بإمكان المستخدمين استخدام SSO للمصادقة بواسطة UPN وكلمة المرور على أجهزة سطح المكتب المدارة من Microsoft. للتأكد من أن هذه الدالة ستعمل، يجب التحقق مرة أخرى من الأمور التالية:

- تأكد من إعداد azure AD الاتصال. يجب أن يستخدم خادم Active Directory Windows Server 2008 R2 أو أحدث.
- تأكد من أن Azure AD الاتصال تشغيل إصدار معتمد. يجب تعيينها لمزامنة هذه السمات الثلاث مع Azure AD:
    - اسم مجال DNS ل Active Directory المحلي (حيث يوجد المستخدمون).
    - NetBIOS ل Active Directory المحلي (حيث يوجد المستخدمون).
    - اسم حساب SAM للمستخدم.

### <a name="single-sign-on-by-using-windows-hello-for-business"></a>استخدام Sign-On واحد باستخدام Windows Hello for Business

توفر أجهزة سطح المكتب المدارة من Microsoft للمستخدمين تجربة سريعة وأقل كلمة مرور من خلال Windows Hello for Business. لضمان عمل Windows Hello for Business بدون أن يحتاج المستخدمون إلى توفير UPN وكلمة المرور، تفضل بزيارة تكوين أجهزة [Azure AD](/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) المنضمة إلى Single-Sign عند استخدام Windows Hello for Business للتحقق من المتطلبات، ثم اتبع الخطوات المتوفرة هناك.

## <a name="apps-and-resources-that-use-authentication"></a>التطبيقات والموارد التي تستخدم المصادقة

راجع [فهم اعتبارات](/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) التطبيقات والموارد في مجموعة محتوى Azure للحصول على إرشادات كاملة حول إعداد التطبيقات للعمل مع Azure Active Directory. باختصار:

| التطبيق أو الخدمة | مهمة |
| ------ | ------ |
| التطبيقات المستندة إلى السحابة | إذا كنت تستخدم **تطبيقات** مستندة إلى السحابة، مثل تلك التي تم إضافتها إلى معرض تطبيقات Azure AD، فإن معظمها لا تتطلب أي تحضيرات إضافية للعمل مع Microsoft Managed Desktop. ومع ذلك، قد لا تزال أي تطبيقات Win32 لا تستخدم Web Account Manager (WAM) مطالبة المستخدمين بالمصادقة. |
| التطبيقات المستضافة في الموقع | بالنسبة **للتطبيقات** المستضافة في الموقع، تأكد من إضافة تلك التطبيقات إلى قائمة المواقع الموثوق بها في المستعرضات. ستمكن هذه الخطوة Windows المصادقة بطريقة سلسة، من دون مطالبة المستخدمين باستخدام بيانات الاعتماد. لإضافة تطبيقات، يمكنك الرجوع إلى [المواقع الموثوق بها](../working-with-managed-desktop/config-setting-ref.md#trusted-sites) في [مرجع الإعدادات القابلة للتكوين](../working-with-managed-desktop/config-setting-ref.md). |
| خدمات Active Directory المتحدة | إذا كنت تستخدم خدمات Active Directory الموحدة، فتحقق من تمكين SSO باستخدام الخطوات في التحقق من تسجيل الدخول الفردي وإدارته باستخدام [AD FS](/previous-versions/azure/azure-services/jj151809(v=azure.100)). |
| التطبيقات التي تستخدم بروتوكولات قديمة | بالنسبة للتطبيقات التي تستخدم بروتوكولات قديمة، لا يلزم إعداد إضافي، طالما أن الأجهزة لديها حق الوصول إلى وحدة تحكم مجال في الموقع للمصادقة. ومع ذلك، لتوفير وصول آمن لهذه التطبيقات، يجب نشر وكيل تطبيق Azure AD. لمزيد من المعلومات، راجع الوصول البعيد إلى التطبيقات في الموقع من [خلال وكيل تطبيق Azure Active Directory](/azure/active-directory/manage-apps/application-proxy). |
| التطبيقات التي يتم تشغيلها على مصادقة الجهاز | التطبيقات التي **يتم تشغيلها في الموقع وتعتمد** على مصادقة الجهاز غير معتمدة، لذا يجب أن تفكر في استبدالها بالإصدارات الأحدث. |

### <a name="network-shares-that-use-authentication"></a>أسهم الشبكة التي تستخدم المصادقة

لا يتطلب الأمر إعدادا إضافيا للمستخدمين للوصول إلى أسهم الشبكة، طالما أن الأجهزة لديها حق الوصول إلى وحدة تحكم المجال المحلية باستخدام مسار UNC.

### <a name="printers"></a>الطابعات

لا يمكن لأجهزة سطح المكتب المدار من Microsoft الاتصال بالطابعات التي يتم نشرها إلى Active Directory الخاص بك في الموقع ما لم تكن قد قمت بتكوين ["طباعة السحابة المختلطة](/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy)".

على الرغم من أنه لا يمكن اكتشاف الطابعات تلقائيا في بيئة السحابة فقط، إلا أنه يمكن للمستخدمين استخدام الطابعات المحلية باستخدام مسار الطابعة أو مسار قائمة انتظار الطابعات، طالما أن الأجهزة لديها حق الوصول إلى وحدة تحكم المجال المحلية.

<!--add fuller material on printers when available-->
## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>خطوات الاستعداد لسطح المكتب المدار من Microsoft

1. مراجعة [المتطلبات الأساسية لسطح المكتب المدار من Microsoft](prerequisites.md).
1. تشغيل [أدوات تقييم الجهوزية](readiness-assessment-tool.md).
1. شراء [Company Portal](../get-started/company-portal.md).
1. مراجعة [المتطلبات الأساسية الخاصة وحسابات الضيوف](guest-accounts.md).
1. تحقق [من تكوين الشبكة](network.md).
1. [إعداد الشهادات وملفات تعريف الشبكة](certs-wifi-lan.md).
1. إعداد وصول المستخدم إلى البيانات (هذه المقالة).
1. [تحضير التطبيقات](apps.md).
1. [إعداد محركات أقراص تم تعيينها](mapped-drives.md).
1. [تحضير موارد الطباعة](printing.md).
1. أسماء [أجهزة العنوان](address-device-names.md).
