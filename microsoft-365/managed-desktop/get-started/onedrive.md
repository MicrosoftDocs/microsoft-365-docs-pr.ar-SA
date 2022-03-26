---
title: Microsoft OneDrive
description: كيفية إعداد Microsoft Managed Desktop OneDrive الأجهزة المسجلين
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق، التطبيقات، تطبيقات خط العمل، تطبيقات LOB
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 89d1851b3a2a7358a36d6a1ddd6f7db24dd2e1cf
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63570566"
---
# <a name="microsoft-onedrive"></a>Microsoft OneDrive

يستخدم Microsoft Managed Desktop [OneDrive for Business](/onedrive/plan-onedrive-enterprise) كخدمة تخزين على السحابة لجميع أجهزة سطح المكتب المدارة من Microsoft. وهو يضمن أن الأجهزة بلا حالة قدر الإمكان. وسيتمكن المستخدمون من العثور على ملفاتهم بغض النظر عن الجهاز الذي سجلوا دخولهم. على سبيل المثال، إذا استبدلت جهاز Microsoft Managed Desktop بجهاز جديد، فإن الملفات ستتزامن تلقائيا مع الجهاز الجديد.

نقوم تلقائيا بتكوين هذه الإعدادات بشكل افتراضي على الأجهزة المدارة من Microsoft:

| الميزة | الوصف |
| ------ | ------ |
| تكوين صامت | OneDrive يتم تكوين الحساب تلقائيا باستخدام حساب المستخدم. يقوم تلقائيا تسجيل الدخول، بدون تفاعل المستخدم، إلى حساب المستخدم الذي تم استخدامه تسجيل الدخول إلى Windows. لمزيد من المعلومات، راجع تكوين حسابات المستخدمين [بصمت -](/onedrive/use-silent-account-configuration) OneDrive |
| ملفات عند الطلب | تمكن ميزة الملفات عند الطلب المستخدمين من الوصول إلى الملفات من مساحة التخزين على السحابة في OneDrive دون الحاجة إلى استخدام مساحة القرص بدون داع. لمزيد من المعلومات، راجع حفظ مساحة القرص باستخدام OneDrive [عند الطلب Windows 10](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e). |
| نقل المجلدات المعروفة | يتم تمكين ميزة "نقل المجلدات المعروفة" بصمت لنمح بيانات المستخدمين في السحابة، مما يمنحهم حق الوصول إلى ملفاتهم من أي جهاز. لمزيد من المعلومات، راجع إنشاء نسخة إضافية من مجلدات المستندات والصور وسطح المكتب [باستخدام OneDrive](https://support.microsoft.com/office/back-up-your-documents-pictures-and-desktop-folders-with-onedrive-d61a7930-a6fb-4b95-b28a-6552e77c3057). <p> لا يمكن للمستخدمين تعطيل ميزة نقل المجلدات المعروفة أو تغيير موقع المجلدات المعروفة لضمان تجربة متناسقة عبر أجهزة سطح المكتب المدارة من Microsoft.</p>|

## <a name="user-experience"></a>تجربة المستخدم

عندما يتلقى مستخدمو Microsoft Managed Desktop جهازا جديدا، سيخوضون تجربة التشغيل الأول، عن طريق إدخال بيانات اعتماد Azure الخاصة بهم، أثناء إعداد الجهاز. بعد اكتمال هذه العملية، يمكنهم الوصول إلى سطح المكتب والحصول على OneDrive المستخدم.

1. يخبر النظام المستخدمين بأنه OneDrive تم تكوينهم وأنهم قد تم تسجيل دخولهم تلقائيا إلى OneDrive.

:::image type="content" source="media/onedrive-sync.png" alt-text="قراءة الإعلامات التي تقوم OneDrive الآن، كما يمكنك تحرير الملفات في OneDrive. انقر هنا لعرض ملفاتك.":::

2. يخبر النظام المستخدمين OneDrive تم تكوين "نقل المجلدات المعروفة" لهم.

:::image type="content" source="media/onedrive-folders.png" alt-text="إعلام بقراءة قسم معلومات المعلومات الذي لديك الذي انقسم إلى مجلداتك المهمة. يتم الآن إنشاء OneDrive للمجلدات ومتوفرة من أجهزة أخرى.":::

3. لمنع تكرار الأيقونات على سطح المكتب عند إعادة تعيين الأجهزة أو إعادة تعيينها، يقوم النظام تلقائيا بإزالة Microsoft Edge Microsoft Teams من المزامنة من OneDrive. تظهر هذه المعلومات في مستكشف الملفات.

:::image type="content" source="media/onedrive-teams.png" alt-text="يعرض &quot;مستكشف الملفات&quot; Teams وإدراجات Edge مع خانات الاختيار التي تم مسحها والمرر فوق قراءة النص مستبعد من المزامنة.":::

## <a name="onedrive-sync-restrictions"></a>المزامنة من OneDrive القيود

إذا كنت بحاجة إلى تقييد المزامنة من OneDrive، نوصي بالتحكم في الوصول باستخدام نهج الوصول الشرطي ل Azure Active Directory. لمزيد من المعلومات، راجع [تمكين دعم الوصول الشرطي في المزامنة من OneDrive التطبيق](/onedrive/enable-conditional-access).

إذا لم تتمكن من استخدام نهج الوصول الشرطي ل Azure AD في مؤسستك، يجب على مسؤول المعلومات اتباع الخطوات التالية:

1. إذا لم تكن تعرف ذلك مسبقا، فابحث عن "[معرف](/onedrive/find-your-office-365-tenant-id) المستأجر"، كما هو موضح في البحث عن Microsoft 365 المستأجر.
1. سجل الدخول إلى OneDrive الإدارة.
1. في الجزء الأيسر، حدد **مزامنة**.
1. حدد خانة **الاختيار السماح بالمزامنة** فقط على أجهزة الكمبيوتر الشخصية التي تم ضمها إلى مجالات معينة، ثم أضف "اسم المستأجر" إلى قائمة المجالات. لمزيد من المعلومات، راجع [السماح بالمزامنة فقط على أجهزة الكمبيوتر المنضمة إلى مجالات معينة](/onedrive/allow-syncing-only-on-specific-domains).

> [!NOTE]
> تنطبق هذه الإرشادات فقط على المستأجرين في Microsoft Managed Desktop. هناك إعدادات أخرى في الاستخدام لم يتم مناقشتها في هذه المقالة.
