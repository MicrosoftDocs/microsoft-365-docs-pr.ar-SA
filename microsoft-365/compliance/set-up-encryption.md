---
title: إعداد التشفير في Office 365 Enterprise
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: باستخدام Office 365، يتم تشغيل بعض قدرات التشفير بشكل افتراضي؛ ويمكن تكوين قدرات أخرى لتلبية بعض متطلبات التوافق أو المتطلبات القانونية.
ms.openlocfilehash: 00035af0049abedff8a794710649f162576dc46c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566942"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>إعداد التشفير في Office 365 Enterprise

يمكن أن يحمي التشفير المحتوى الخاص بك من القراءة من قبل مستخدمين غير مصرح لهم. نظرا [لأنه يمكن Office 365](encryption.md) التشفير باستخدام أساليب وتقنيات مختلفة، فلا يوجد مكان واحد تقوم فيه تشغيل التشفير أو إعداده. توفر هذه المقالة معلومات حول الطرق المختلفة التي يمكنك من خلالها إعداد التشفير أو تكوينه كجزء من استراتيجية حماية المعلومات.

> [!TIP]
> إذا كنت تبحث عن مزيد من التفاصيل التقنية حول التشفير، فراجع تفاصيل المراجع التقنية [حول التشفير في](technical-reference-details-about-encryption.md) Office 365.

باستخدام Office 365، تتوفر قدرات تشفير متعددة بشكل افتراضي. يمكن تكوين قدرات تشفير إضافية لتلبية بعض متطلبات التوافق أو المتطلبات القانونية. يصف الجدول التالي العديد من أساليب التشفير لسيناريوهات مختلفة.

<br>

****

|السيناريو|أساليب التشفير|
|---|---|
|يتم حفظ الملفات على أجهزة الكمبيوتر Windows الكمبيوتر|يمكن القيام بالتشفير على مستوى الكمبيوتر باستخدام BitLocker Windows الأجهزة. كمسؤول مؤسسة أو مسؤول تكنولوجيا Pro، يمكنك إعداد هذا باستخدام مجموعة أدوات النشر من Microsoft (MDT). راجع [إعداد MDT ل BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|يتم حفظ الملفات على الأجهزة المحمولة|تعمل بعض أنواع الأجهزة المحمولة على تشفير الملفات التي يتم حفظها على هذه الأجهزة بشكل افتراضي. باستخدام [إمكانيات البيانات المضمنة](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0) Mobile Device Management لـ Office 365، يمكنك تعيين سياسات تحدد ما إذا كنت تريد السماح للأجهزة المحمولة بالوصول إلى البيانات في Office 365. على سبيل المثال، يمكنك تعيين نهج يسمح فقط للأجهزة التي تقوم بتشفير المحتوى بالوصول إلى Office 365 البيانات. راجع [إنشاء سياسات أمان الأجهزة ونشرها](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> لمزيد من التحكم في كيفية تفاعل الأجهزة المحمولة مع Office 365، يمكنك [التفكير في إضافة](/mem/intune/fundamentals/setup-steps) Microsoft Intune.|
|أنت بحاجة إلى التحكم في مفاتيح التشفير المستخدمة لتشفير البيانات في مراكز بيانات Microsoft|كمسؤول Office 365، يمكنك التحكم في مفاتيح تشفير مؤسستك ثم تكوين Office 365 لاستخدامها لتشفير البيانات في مراكز بيانات Microsoft. <p> [تشفير الخدمة باستخدام "مفتاح العميل" في Office 365](customer-key-overview.md)|
|الأشخاص يتواصلون عبر البريد الإلكتروني (Exchange Online)|كمسؤول Exchange Online، لديك العديد من الخيارات لتكوين تشفير البريد الإلكتروني. وتتضمن هذه الخيارات: <ul><li>استخدام [Office 365 تشفير الرسائل (OME) مع](set-up-new-message-encryption-capabilities.md) Azure Rights Management (Azure RMS) لتمكين الأشخاص من إرسال رسائل مشفرة داخل مؤسستك أو خارجها</li><li>استخدام [S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo) لتشفير رسائل البريد الإلكتروني وتوقيعها رقميا</li><li>استخدام TLS [لإعداد الموصلات لتدفق البريد الآمن مع مؤسسة أخرى](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)</li></ul> <p> راجع [تشفير البريد الإلكتروني في Office 365](./email-encryption.md).|
|يتم الوصول إلى الملفات من مواقع الفريق أو مكتبات المستندات (OneDrive for Business أو SharePoint عبر الإنترنت)|عندما يعمل الأشخاص على ملفات محفوظة على OneDrive for Business أو SharePoint عبر الإنترنت، يتم استخدام اتصالات TLS. هذا مضمن في Office 365 تلقائيا. راجع [تشفير البيانات في OneDrive for Business SharePoint عبر الإنترنت](./data-encryption-in-odb-and-spo.md).|
|يتم مشاركة الملفات في الاجتماعات عبر الإنترنت ومحادثات المراسلة الفورية (Skype for Business Online)|عندما يعمل الأشخاص على ملفات Skype for Business عبر الإنترنت، يتم استخدام TLS للاتصال. هذا مضمن في Office 365 تلقائيا. راجع [الأمان والأرشفة (Skype for Business Online)](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).|
|يتم مشاركة الملفات في الاجتماعات عبر الإنترنت ومحادثات المراسلة الفورية (Microsoft Teams)|عندما يعمل الأشخاص على الملفات باستخدام Microsoft Teams، يتم استخدام TLS للاتصال. هذا مضمن في Office 365 تلقائيا. Microsoft Teams حاليا العرض الم خطيا للبريد الإلكتروني المشفر. لمنع البريد الإلكتروني المشفر من الوصول إلى Microsoft Teams مشفرة، راجع [الأسئلة الشائعة حول تشفير الرسائل](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>معلومات إضافية

لمعرفة المزيد حول حلول حماية الملفات التي تتضمن خيارات التشفير، راجع حلول حماية الملفات [في Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
