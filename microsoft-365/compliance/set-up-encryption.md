---
title: إعداد التشفير في Office 365 Enterprise
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: مع Office 365، يتم تشغيل بعض قدرات التشفير بشكل افتراضي؛ ويمكن تكوين قدرات أخرى لتلبية متطلبات توافق أو متطلبات قانونية معينة.
ms.openlocfilehash: 86e39603025c29d47a2e1b2b5b946bfe2549245d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622096"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>إعداد التشفير في Office 365 Enterprise

يمكن أن يحمي التشفير المحتوى الخاص بك من القراءة من قبل مستخدمين غير مصرح لهم. نظرا لأنه يمكن إجراء [التشفير في Office 365](encryption.md) باستخدام تقنيات وأساليب مختلفة، لا يوجد مكان واحد تقوم فيه بتشغيل التشفير أو إعداده. توفر هذه المقالة معلومات حول الطرق المختلفة التي يمكنك من خلالها إعداد التشفير أو تكوينه كجزء من استراتيجية حماية المعلومات.

> [!TIP]
> إذا كنت تبحث عن مزيد من التفاصيل التقنية حول التشفير، فراجع [تفاصيل المرجع التقني حول التشفير في Office 365](technical-reference-details-about-encryption.md).

مع Office 365، تتوفر العديد من قدرات التشفير بشكل افتراضي. يمكن تكوين قدرات تشفير إضافية لتلبية متطلبات توافق أو متطلبات قانونية معينة. يصف الجدول التالي عدة طرق تشفير لسيناريوهات مختلفة.

<br>

****

|السيناريو|أساليب التشفير|
|---|---|
|يتم حفظ الملفات على أجهزة كمبيوتر Windows|يمكن إجراء التشفير على مستوى الكمبيوتر باستخدام BitLocker على أجهزة Windows. بصفتك مسؤول مؤسسة أو محترف تكنولوجيا المعلومات، يمكنك إعداد هذا باستخدام مجموعة أدوات نشر Microsoft (MDT). راجع [إعداد MDT ل BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|يتم حفظ الملفات على الأجهزة المحمولة|تقوم بعض أنواع الأجهزة المحمولة بتشفير الملفات التي يتم حفظها في تلك الأجهزة بشكل افتراضي. باستخدام [قدرات Mobile Device Management لـ Office 365 المضمنة](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0)، يمكنك تعيين النهج التي تحدد ما إذا كان يجب السماح للأجهزة المحمولة بالوصول إلى البيانات في Office 365. على سبيل المثال، يمكنك تعيين نهج يسمح فقط للأجهزة التي تقوم بتشفير المحتوى بالوصول إلى البيانات Office 365. راجع [إنشاء نهج أمان الجهاز ونشرها](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> للتحكم الإضافي في كيفية تفاعل الأجهزة المحمولة مع Office 365، يمكنك التفكير في إضافة [Microsoft Intune](/mem/intune/fundamentals/setup-steps).|
|تحتاج إلى التحكم في مفاتيح التشفير المستخدمة لتشفير بياناتك في مراكز بيانات Microsoft|بصفتك مسؤول Office 365، يمكنك التحكم في مفاتيح التشفير الخاصة بمؤسستك ثم تكوين Office 365 لاستخدامها لتشفير بياناتك الثابتة في مراكز بيانات Microsoft. <p> [تشفير الخدمة باستخدام مفتاح عميل Microsoft Purview](customer-key-overview.md)|
|يتصل الأشخاص عبر البريد الإلكتروني (Exchange Online)|بصفتك مسؤول Exchange Online، لديك العديد من الخيارات لتكوين تشفير البريد الإلكتروني. وتشمل هذه الخطوات ما يلي: <ul><li>استخدام [تشفير الرسائل Office 365 (OME)](set-up-new-message-encryption-capabilities.md) مع Azure Rights Management (Azure RMS) لتمكين الأشخاص من إرسال رسائل مشفرة داخل مؤسستك أو خارجها</li><li>استخدام [S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo) لتشفير رسائل البريد الإلكتروني وتوقيعها رقميا</li><li>استخدام TLS [لإعداد الموصلات لتدفق البريد الآمن مع مؤسسة أخرى](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)</li></ul> <p> راجع [تشفير البريد الإلكتروني في Office 365](./email-encryption.md).|
|يتم الوصول إلى الملفات من مواقع الفريق أو مكتبات المستندات (OneDrive for Business أو SharePoint Online)|عندما يعمل الأشخاص على ملفات محفوظة في OneDrive for Business أو SharePoint Online، يتم استخدام اتصالات TLS. يتم تضمين هذا في Office 365 تلقائيا. راجع [تشفير البيانات في OneDrive for Business وSharePoint Online](./data-encryption-in-odb-and-spo.md).|
|تتم مشاركة الملفات في الاجتماعات عبر الإنترنت ومحادثات المراسلة الفورية (Skype for Business Online)|عندما يعمل الأشخاص على الملفات باستخدام Skype for Business Online، يتم استخدام TLS للاتصال. يتم تضمين هذا في Office 365 تلقائيا. راجع [الأمان والأرشفة (Skype for Business Online).](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)|
|تتم مشاركة الملفات في الاجتماعات عبر الإنترنت ومحادثات المراسلة الفورية (Microsoft Teams)|عندما يعمل الأشخاص على الملفات باستخدام Microsoft Teams، يتم استخدام TLS للاتصال. يتم تضمين هذا في Office 365 تلقائيا. لا يدعم Microsoft Teams حاليا العرض المضمن للبريد الإلكتروني المشفر. لمنع وصول البريد الإلكتروني المشفر إلى Microsoft Teams على أنه مشفر، راجع [الأسئلة المتداولة حول تشفير الرسائل](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>معلومات إضافية

لمعرفة المزيد حول حلول حماية الملفات التي تتضمن خيارات التشفير، راجع ["حلول حماية الملفات" في Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
