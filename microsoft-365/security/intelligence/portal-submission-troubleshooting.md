---
title: استكشاف أخطاء مدخل MSI التي تسببها كتلة المسؤول وإصلاحها
description: استكشاف أخطاء مدخل MSI وإصلاحها
ms.reviewer: ''
keywords: الأمان، عينة تعليمات الإرسال، ملف البرامج الضارة، ملف الفيروسات، ملف طروادة، إرسال، إرسال إلى Microsoft، إرسال عينة، فيروس، طروادة، فيروس، فيروس متنقل، غير مكتشف، لا يكشف، بريد microsoft الإلكتروني، البرامج الضارة بالبريد الإلكتروني، أعتقد أنه برنامج ضار، أعتقد أنه فيروس، أين يمكنني إرسال فيروس، هل هذا فيروس، MSE، لا يكشف، لا توقيع، لا يوجد أي كشف، ملف مشتبه به،  MMPC، مركز الحماية من البرامج الضارة لـ Microsoft، باحثون، محللون، WDSI، معلومات أمان
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: e70eb5192a1fd6171b8e515509ad336aa99a2c63
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705773"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>استكشاف أخطاء إرسال البرامج الضارة التي تسببها كتلة المسؤول وإصلاحها
في بعض الحالات، قد يتسبب حظر المسؤول في حدوث مشاكل في الإرسال عند محاولة إرسال ملف يحتمل أن يكون ملوثا إلى [موقع معلومات أمان Microsoft على الويب](https://www.microsoft.com/wdsi) لتحليله. توضح العملية التالية كيفية حل هذه المشكلة.

## <a name="review-your-settings"></a>مراجعة الإعدادات
افتح إعدادات تطبيق Azure [Enterprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/). ضمن **تطبيقات المؤسسةيوافق** >   المستخدمون **على التطبيقات التي يمكنها الوصول** إلى بيانات الشركة بالنيابة عنهم، تحقق مما إذا تم تحديد نعم أو لا.

- إذا **تم** تحديد لا، سيحتاج مسؤول Azure AD لمستأجر العميل إلى تقديم موافقة المؤسسة. استنادا إلى التكوين باستخدام Azure AD، قد يتمكن المستخدمون من إرسال طلب مباشرة من مربع الحوار نفسه. إذا لم يكن هناك خيار لطلب موافقة المسؤول، يجب على المستخدمين طلب إضافة هذه الأذونات إلى مسؤول Azure AD. انتقل إلى القسم التالي للحصول على مزيد من المعلومات.

- إذا **تم** تحديد نعم، فتأكد Windows إعداد تطبيق "معلومات الأمان ل Defender" الذي تم تمكينه للمستخدمين من تسجيل الدخول **؟** تم تعيينه إلى **نعم** [في Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).إذا **تم** تحديد لا، ستحتاج إلى طلب تمكين مسؤول Azure AD له. 
  
## <a name="implement-required-enterprise-application-permissions"></a>تنفيذ أذونات تطبيق المؤسسة المطلوبة 
تتطلب هذه العملية وجود مسؤول عام أو مسؤول تطبيق في المستأجر.
 1. افتح [إعدادات تطبيق المؤسسة](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). 
 2. حدد **منح موافقة المسؤول لمنظمتك**.
 3. إذا كنت قادرا على القيام بذلك، فراجع أذونات API المطلوبة لهذا التطبيق، كما تظهر الصورة التالية. تقديم الموافقة للمستأجر.

    ![منح صورة الموافقة.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

  4. إذا تلقى المسؤول خطأ أثناء محاولة تقديم الموافقة يدويا، فجرب الخيار [1](#option-1-approve-enterprise-application-permissions-by-user-request) أو الخيار [2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) كحل بديل محتمل.
  
## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>الخيار 1 الموافقة على أذونات تطبيق المؤسسة حسب طلب المستخدم
> [!Note]
> هذه حاليا ميزة معاينة.

سيحتاج مسؤولو Azure Active Directory إلى السماح للمستخدمين بطلب موافقة المسؤول على التطبيقات. تحقق من تكوين الإعداد إلى **نعم** في [تطبيقات المؤسسة](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![إعدادات مستخدم تطبيقات المؤسسة.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

تتوفر المزيد من المعلومات في [تكوين سير عمل موافقة المسؤول](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

بمجرد التحقق من هذا الإعداد، يمكن للمستخدمين الانتقال عبر تسجيل الدخول إلى عميل المؤسسة في معلومات [أمان Microsoft](https://www.microsoft.com/wdsi/filesubmission)، وإرسال طلب للحصول على موافقة المسؤول، بما في ذلك التبرير.

![تدفق تسجيل الدخول إلى Contoso.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

سيكون المسؤول قادرا على مراجعة طلبات موافقة مسؤول [Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/) والموافقة عليها.

بعد تقديم الموافقة، سيكون جميع المستخدمين في المستأجر قادرين على استخدام التطبيق.
  
## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>الخيار 2 تقديم موافقة المسؤول من خلال مصادقة التطبيق كمسؤول 
تتطلب هذه العملية أن يخوض المسؤولون العامون تدفق تسجيل الدخول إلى عميل Enterprise في [المعلومات الأمنية من Microsoft](https://www.microsoft.com/wdsi/filesubmission).

![تدفق تسجيل الدخول بالموافقة.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

بعد ذلك، يراجع المسؤولون الأذونات وتأكد من تحديد الموافقة بالنيابة عن **مؤسستك**، ثم حدد **قبول**.

وسيتمكن الآن جميع المستخدمين في المستأجر من استخدام هذا التطبيق.

## <a name="option-3-delete-and-readd-app-permissions"></a>الخيار 3: حذف أذونات التطبيق وقراءتها
إذا لم يحل أي من هذين الخيارين المشكلة، فجرب الخطوات التالية (كمسؤول):

1. إزالة التكوينات السابقة للتطبيق. انتقل إلى [تطبيقات Enterprise](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) وحدد **حذف**.

   ![حذف أذونات التطبيق.](../../media/security-intelligence-images/msi-properties.png)

2. التقاط "مستأجر" من [Properties](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. استبدل {tenant-id} بالمستأجر المحدد الذي يحتاج إلى منح الموافقة لهذا التطبيق في عنوان URL أدناه. انسخ عنوان URL هذا إلى المستعرض. تم إكمال باقي المعلمات بالفعل. 
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![الأذونات المطلوبة.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. راجع الأذونات المطلوبة بواسطة التطبيق، ثم حدد **قبول**. 

5. تأكد من تطبيق الأذونات في مدخل [Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![راجع تطبيق الأذونات.](../../media/security-intelligence-images/msi-permissions.jpg)
   
6. سجل دخولك إلى [معلومات أمان Microsoft](https://www.microsoft.com/wdsi/filesubmission) كمستخدم مؤسسة باستخدام حساب غير مسؤول لمعرفة ما إذا كان لديك حق الوصول.

 إذا لم يتم حل التحذير بعد اتباع خطوات استكشاف الأخطاء وإصلاحها هذه، فاتصل بدعم Microsoft.