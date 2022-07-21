---
title: إدارة البيانات ل Microsoft Whiteboard
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: تعرف على استبقاء البيانات ل Microsoft Whiteboard في Azure OneDrive for Business.
ms.openlocfilehash: 88ebe6de6983823e6f782f006ac2aa58cfe9af93
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66943035"
---
# <a name="manage-data-for-microsoft-whiteboard"></a>إدارة البيانات ل Microsoft Whiteboard

يتم تخزين محتوى لوح المعلومات في كل من Azure و OneDrive for Business. سيتم تخزين ألواح المعلومات الجديدة في OneDrive for Business؛ الاستثناء الوحيد هو ألواح المعلومات التي بدأت من Surface Hub وسيتم تخزينها في Azure (والتي سيتم نقلها إلى OneDrive for Business في المستقبل). لمزيد من المعلومات، راجع [إدارة المشاركة في Whiteboard](manage-sharing-organizations.md).

## <a name="azure-storage-overview"></a>نظرة عامة على تخزين Azure

يقوم Whiteboard حاليا بتخزين المحتوى بشكل آمن في Azure. قد يتم تخزين البيانات في مواقع مختلفة، اعتمادا على البلد ووقت تبديل Whiteboard إلى تخزين محتوى جديد في تلك المواقع. للتحقق من مكان إنشاء بيانات جديدة، راجع [مكان تخزين بيانات عميل Microsoft 365](/microsoft-365/enterprise/o365-data-locations). 

لا يدعم المحتوى في Azure منع فقدان البيانات (DLP) وeDiscovery ونهج الاستبقاء والميزات المشابهة. يمكن إدارة المحتوى باستخدام [Whiteboard PowerShell cmdlets](/powershell/module/whiteboard/) وبمرور الوقت، يجب ترحيل هذا المحتوى إلى OneDrive for Business أو حذفه.

### <a name="if-a-user-account-is-deleted-in-azure"></a>إذا تم حذف حساب مستخدم في Azure

نحن نغير كيفية تخزين ألواح المعلومات عند حذف حساب المستخدم في Azure. قبل التغيير، عند حذف حساب المستخدم، تم أيضا حذف ألواح المعلومات التي يملكها المستخدم، ولكن لم يتم حذف ألواح المعلومات التي تمت مشاركتها مع الآخرين.

>[!NOTE]
> ستتم معالجة ألواح المعلومات المخزنة في OneDrive for Business مثل أي محتوى آخر في OneDrive for Business. لمزيد من المعلومات، راجع [تعيين استبقاء OneDrive للمستخدمين المحذوفين](/onedrive/set-retention).

اعتبارا من **1 يونيو 2022**، تغير سلوك ألواح المعلومات على Azure. سيتم حذف أي ألواح معلومات تمت مشاركتها مع مستخدمين آخرين.

إذا كنت تريد الاحتفاظ بألواح المعلومات الخاصة بالمستخدم المحذوفة، *قبل* حذف الحساب، يمكنك نقل الملكية. يمكنك نقل لوح معلومات واحد أو كلها إلى مستخدم آخر. 

- اتبع هذه الإرشادات [لنقل جميع ألواح المعلومات](/powershell/module/whiteboard/invoke-transferallwhiteboards).

- لمزيد من المعلومات حول كيفية حذف حسابات المستخدمين، راجع [حذف مستخدم من مؤسستك](/microsoft-365/admin/add-users/delete-a-user).

تأكد من أن أي عملية حذف أو برنامج نصي يعالج هذا التغيير. إذا كنت على ما يرام مع الألواح البيضاء التي يتم حذفها، فلا يلزم اتخاذ أي إجراء. 

## <a name="onedrive-for-business-storage-overview"></a>نظرة عامة على التخزين OneDrive for Business

سيتم إنشاء ألواح المعلومات في مجلد OneDrive for Business للشخص الذي يبدأ تشغيل لوح المعلومات (SharePoint غير معتمد بعد). تنطبق هذه العملية على جميع ألواح المعلومات التي تم إنشاؤها في تطبيقات Whiteboard المستقلة، وفي اجتماعات Microsoft Teams والدردشات والقنوات. الاستثناء الوحيد هو ألواح المعلومات التي بدأت من Surface Hub سيتم تخزينها في Azure (والتي سيتم نقلها إلى OneDrive for Business في المستقبل).

لن يتمكن أي مستخدمين لم يتم توفير OneDrive for Business لهم من إنشاء ألواح معلومات جديدة عند تنفيذ هذا التغيير. ومع ذلك، لا يزال بإمكانهم تحرير لوحاتهم التي تم إنشاؤها مسبقا. كما يمكنهم التعاون في العمل على أي ألواح معلومات تتم مشاركتها معهم من قبل الآخرين الذين لديهم OneDrive for Business.

قد يتراوح متوسط حجم لوح المعلومات من 50 كيلوبايت إلى 1 ميغابايت في أي مكان يتواجد فيه محتوى OneDrive for Business. للتحقق من مكان تخزين بيانات المستأجر، راجع [مكان تخزين بيانات عميل Microsoft 365](/microsoft-365/enterprise/o365-data-locations). ثم انظر إلى موقع OneDrive for Business.

### <a name="controls-for-onedrive-for-business-storage"></a>عناصر التحكم لتخزين OneDrive for Business 

يمكنك إدارة بيانات Whiteboard باستخدام عناصر تحكم OneDrive for Business الموجودة. لمزيد من المعلومات، راجع [دليل OneDrive للمؤسسات](/onedrive/plan-onedrive-enterprise).

يمكنك استخدام أدوات OneDrive for Business الموجودة لتلبية طلبات موضوع البيانات (DSRs) للائحة العامة لحماية البيانات (GDPR). إذا كنت تريد التأكد من إزالة كافة التغييرات السابقة من الملف، فيجب حذف الملف بأكمله.

يمكن نقل ملفات لوح المعلومات بنفس طريقة نقل المحتوى الآخر في OneDrive for Business. ومع ذلك، قد لا يتم نقل مشاركة الارتباطات والأذونات.

عناصر التحكم في البيانات المدعومة اليوم:

- نهج الاستبقاء
- الحصه النسبيه
- احتجاز قانوني
- دلب
- eDiscovery الأساسي – يتم تخزين ملفات .whiteboard كملفات في OneDrive for Business المنشئ. تتم فهرستها للبحث عن الكلمة الأساسية ونوع الملف، ولكنها غير متوفرة للمعاينة أو المراجعة. عند التصدير، يحتاج المسؤول إلى تحميل الملف مرة أخرى إلى OneDrive for Business لعرض المحتوى. ويخطط للحصول على دعم إضافي في المستقبل.

عناصر تحكم البيانات المخطط لها للإصدارات المستقبلية:

- تسميات الحساسية
- تحليلات
- دعم eDiscovery إضافي

## <a name="see-also"></a>راجع أيضًا

[إدارة الوصول إلى Whiteboard](manage-whiteboard-access-organizations.md)

[إدارة المشاركة ل Whiteboard](manage-sharing-organizations.md)

[توزيع لوح المعلومات على Windows](deploy-on-windows-organizations.md)


