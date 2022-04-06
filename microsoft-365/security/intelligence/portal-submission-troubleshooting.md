---
title: استكشاف أخطاء مدخل MSI التي تسببها كتلة المسؤول وإصلاحها
description: استكشاف أخطاء مدخل MSI وإصلاحها
ms.reviewer: ''
keywords: الأمان، عينة تعليمات الإرسال، ملف البرامج الضارة، ملف الفيروسات، ملف أحصنة طروادة، إرسال، إرسال إلى Microsoft، إرسال عينة، فيروس، أحصنة طروادة، فيروسات، فيروسات غير مكتشفة، لا تكتشف، البريد الإلكتروني microsoft، البرامج الضارة، أعتقد أن هذا برنامج ضار، أعتقد أنه فيروس، أين يمكنني إرسال فيروس، هل هذا فيروس، MSE، لا يكشف، لا توقيع، لا اكتشاف، ملف مشبوه،  MMPC، مركز الحماية من البرامج الضارة لـ Microsoft، والباحثين، والمحلل، وWDSI، والذكاء الأمني
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
ms.openlocfilehash: 544e96bd0a3985856f47bc8df424a2c2932f3c7e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665657"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>استكشاف أخطاء إرسال البرامج الضارة التي تسببها كتلة المسؤول وإصلاحها

في بعض الحالات، قد تتسبب كتلة المسؤول في حدوث مشاكل في الإرسال عند محاولة إرسال ملف يحتمل أن يكون مصابا إلى [موقع المعلومات الذكية لأمان Microsoft](https://www.microsoft.com/wdsi) لتحليله. توضح العملية التالية كيفية حل هذه المشكلة.

## <a name="review-your-settings"></a>مراجعة الإعدادات

افتح [إعدادات تطبيق](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/) Azure Enterprise. ضمن **Enterprise ApplicationsUsers** >   **يمكنهم الموافقة على التطبيقات التي تصل إلى بيانات الشركة نيابة عنهم**، والتحقق مما إذا كان قد تم تحديد "نعم" أو "لا".

- إذا لم يتم تحديد **"لا** "، فسيحتاج مسؤول Azure AD لمستأجر العميل إلى تقديم الموافقة للمؤسسة. اعتمادا على التكوين باستخدام Azure AD، قد يتمكن المستخدمون من إرسال طلب مباشرة من مربع الحوار نفسه. إذا لم يكن هناك خيار لطلب موافقة المسؤول، يحتاج المستخدمون إلى طلب إضافة هذه الأذونات إلى مسؤول Azure AD. انتقل إلى القسم التالي للحصول على مزيد من المعلومات.

- إذا تم تحديد **"نعم**"، فتأكد من تمكين إعداد تطبيق Windows Defender Security Intelligence **للمستخدمين لتسجيل الدخول؟** تم تعيينه إلى **"نعم**" [في Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). إذا لم يتم تحديد **"لا** "، فستحتاج إلى طلب تمكين مسؤول Azure AD له.

## <a name="implement-required-enterprise-application-permissions"></a>تنفيذ أذونات تطبيق المؤسسة المطلوبة

تتطلب هذه العملية مسؤول عمومي أو مسؤول تطبيق في المستأجر.

1. فتح [إعدادات تطبيق المؤسسة](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).
2. حدد **منح موافقة المسؤول للمؤسسة**.
3. إذا كنت قادرا على القيام بذلك، فراجع أذونات واجهة برمجة التطبيقات المطلوبة لهذا التطبيق، كما تظهر الصورة التالية. تقديم الموافقة للمستأجر.

    ![منح صورة الموافقة.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

4. إذا تلقى المسؤول خطأ أثناء محاولة تقديم الموافقة يدويا، فجرب إما [الخيار 1](#option-1-approve-enterprise-application-permissions-by-user-request) أو [الخيار 2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) كحلين بديلين محتملين.

## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>الخيار 1 الموافقة على أذونات تطبيق المؤسسة حسب طلب المستخدم

> [!NOTE]
> هذه ميزة معاينة حاليا.

سيحتاج مسؤولو Azure Active Directory إلى السماح للمستخدمين بطلب موافقة المسؤول على التطبيقات. تحقق من تكوين الإعداد إلى **"نعم**[" في تطبيقات المؤسسة](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![إعدادات مستخدم تطبيقات المؤسسة.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

تتوفر المزيد من المعلومات في [تكوين سير عمل موافقة المسؤول](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

بمجرد التحقق من هذا الإعداد، يمكن للمستخدمين الانتقال من خلال تسجيل الدخول إلى عميل المؤسسة في [معلومات الأمان من Microsoft](https://www.microsoft.com/wdsi/filesubmission)، وإرسال طلب للحصول على موافقة المسؤول، بما في ذلك التبرير.

![تدفق تسجيل الدخول إلى Contoso.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

سيتمكن المسؤول من مراجعة [طلبات موافقة مسؤول Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/) والموافقة عليها.

بعد تقديم الموافقة، سيتمكن جميع المستخدمين في المستأجر من استخدام التطبيق.

## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>الخيار 2 توفير موافقة المسؤول من خلال مصادقة التطبيق كمسؤول

تتطلب هذه العملية أن يمر المسؤولون العموميون بتدفق تسجيل دخول عملاء Enterprise في [معلومات الأمان في Microsoft](https://www.microsoft.com/wdsi/filesubmission).

![تدفق تسجيل الدخول إلى الموافقة.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

بعد ذلك، يراجع المسؤولون الأذونات ويتأكدون من تحديد " **الموافقة" نيابة عن مؤسستك**، ثم حدد **"قبول**".

سيتمكن جميع المستخدمين في المستأجر الآن من استخدام هذا التطبيق.

## <a name="option-3-delete-and-readd-app-permissions"></a>الخيار 3: حذف أذونات التطبيق وقراءتها

إذا لم يحل أي من هذين الخيارين المشكلة، فجرب الخطوات التالية (كمسؤول):

1. إزالة التكوينات السابقة للتطبيق. انتقل إلى [تطبيقات المؤسسة](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) وحدد **حذف**.

   ![حذف أذونات التطبيق.](../../media/security-intelligence-images/msi-properties.png)

2. التقاط معرف المستأجر من [الخصائص](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. استبدل {tenant-id} بالمستأجر المحدد الذي يحتاج إلى منح الموافقة على هذا التطبيق في عنوان URL أدناه. انسخ عنوان URL هذا إلى المستعرض. اكتملت بقية المعلمات بالفعل.
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![الأذونات المطلوبة.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. راجع الأذونات المطلوبة من قبل التطبيق، ثم حدد **"قبول**".

5. تأكد من تطبيق الأذونات في مدخل [Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![راجع تطبيق الأذونات.](../../media/security-intelligence-images/msi-permissions.jpg)

6. سجل الدخول إلى [معلومات الأمان في Microsoft](https://www.microsoft.com/wdsi/filesubmission) كمستخدم مؤسسة باستخدام حساب غير مسؤول لمعرفة ما إذا كان لديك حق الوصول.

 إذا لم يتم حل التحذير بعد اتباع خطوات استكشاف الأخطاء وإصلاحها هذه، فاتصل بدعم Microsoft.