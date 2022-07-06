---
title: تشفير بريد Exchange عبر الإنترنت باستخدام AD RMS
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 2c956776-0016-4be6-b4cd-133a237f4a9e
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية تكوين Exchange Online IRM لاستخدام Active Directory محلي Rights Management Service (AD RMS) لتلبية متطلبات مؤسستك.
ms.openlocfilehash: 926bea0b1f9379d2eaad2bc7c5bd672f98329b8a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628782"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>تشفير بريد Exchange عبر الإنترنت باستخدام AD RMS

للمساعدة في منع تسرب المعلومات، Exchange Online تتضمن وظيفة إدارة حقوق استخدام المعلومات (IRM) التي توفر حماية عبر الإنترنت وغير متصلة لرسائل البريد الإلكتروني والمرفقات. يمكنك تكوين Exchange Online IRM لاستخدام Active Directory محلي Rights Management Service (AD RMS)، إذا لزم الأمر، لتلبية متطلبات مؤسستك. هذا ليس شائعا. إذا لم يكن لديك شرط لاستخدام AD RMS، فاستخدم [تشفير الرسائل في Microsoft Purview](ome.md) بدلا من ذلك.

يمكن تطبيق حماية IRM من قبل المستخدمين في Microsoft Outlook أو Outlook على ويب، ويمكن تطبيقها من قبل المسؤولين باستخدام قواعد حماية النقل أو قواعد حماية Outlook. تساعدك IRM والمستخدمين على التحكم في الأشخاص الذين يمكنهم الوصول إلى البيانات الحساسة أو إعادة توجيهها أو طباعتها أو نسخها داخل رسالة بريد إلكتروني.
  
## <a name="changes-to-how-irm-works-with-message-encryption-and-azure-active-directory"></a>تغييرات على كيفية عمل IRM مع تشفير الرسائل وAzure Active Directory

اعتبارا من سبتمبر 2017، عند إعداد تشفير الرسائل في Microsoft Purview لمؤسستك، قمت أيضا بإعداد IRM للاستخدام مع Azure Rights Management (Azure RMS). لم تعد تقوم بإعداد IRM باستخدام Azure RMS بشكل منفصل. بدلا من ذلك، يعمل تشفير الرسائل وإدارة الحقوق معا بسلاسة. لمزيد من التفاصيل حول تشفير الرسائل في Microsoft Purview، راجع [الأسئلة المتداولة حول تشفير الرسائل](./ome-faq.yml). إذا كنت جاهزا لبدء استخدام تشفير الرسائل في Microsoft Purview داخل مؤسستك، فراجع [إعداد تشفير الرسائل في Microsoft Purview](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>كيفية عمل IRM مع خدمات إدارة حقوق Exchange Online وActive Directory

تستخدم Exchange Online IRM Active Directory محلي خدمات إدارة الحقوق (AD RMS)، وهي تقنية حماية المعلومات في Windows Server 2008 والإي وقت لاحق. يتم تطبيق حماية IRM على البريد الإلكتروني عن طريق تطبيق قالب نهج حقوق AD RMS على رسالة بريد إلكتروني. يتم إرفاق الحقوق بالرسالة نفسها بحيث تحدث الحماية عبر الإنترنت ودون اتصال وداخل وخارج جدار حماية مؤسستك.
  
يمكن للمستخدمين تطبيق قالب على رسالة بريد إلكتروني للتحكم في الأذونات التي يملكها المستلمون في الرسالة. يمكن التحكم في الإجراءات، مثل إعادة التوجيه أو استخراج المعلومات من رسالة أو حفظ رسالة أو طباعة رسالة من خلال تطبيق نهج حقوق AD RMS على الرسالة.
  
يمكنك تكوين IRM لاستخدام خادم AD RMS الذي يعمل بنظام التشغيل Windows Server 2008 أو إصدار أحدث. يمكنك استخدام خادم AD RMS هذا لإدارة قوالب نهج حقوق AD RMS لمؤسستك المستندة إلى السحابة. يعتمد Outlook أيضا على خادم AD RMS لتمكين المستخدمين من تطبيق حماية IRM على الرسائل التي يرسلونها. للحصول على التفاصيل، راجع [تكوين IRM لاستخدام خادم AD RMS محلي](configure-irm-to-use-an-on-premises-ad-rms-server.md).
  
بعد تمكينها، يمكن تطبيق حماية إدارة حقوق المعلومات (IRM) على الرسائل كما يلي:
  
- **يمكن للمستخدمين تطبيق قالب يدويا باستخدام Outlook Outlook على ويب.** يمكن للمستخدمين تطبيق قالب نهج حقوق AD RMS على رسالة بريد إلكتروني عن طريق تحديد القالب من قائمة **تعيين الأذونات** . عندما يرسل المستخدمون رسالة محمية بواسطة IRM، فإن أي ملفات مرفقة تستخدم تنسيقا معتمدا تتلقى أيضا نفس حماية IRM مثل الرسالة. يتم تطبيق حماية IRM على الملفات المقترنة ب Word وExcel وPowerPoint، بالإضافة إلى ملفات .xps ورسائل البريد الإلكتروني المرفقة.

- **يمكن للمسؤولين استخدام قواعد حماية النقل لتطبيق حماية IRM تلقائيا على كل من Outlook و Outlook على ويب.** يمكنك إنشاء قواعد حماية النقل لرسائل حماية IRM. تكوين إجراء قاعدة حماية النقل لتطبيق قالب نهج حقوق AD RMS على الرسائل التي تفي بشرط القاعدة. بعد تمكين IRM، تتوفر قوالب نهج حقوق AD RMS الخاصة بالمؤسسة للاستخدام مع إجراء قاعدة حماية النقل الذي يسمى **تطبيق حماية الحقوق على الرسالة التي تتضمنها**.

- **يمكن للمسؤولين إنشاء قواعد حماية Outlook.** تطبق قواعد حماية Outlook تلقائيا حماية IRM على الرسائل في Outlook 2010 (وليس Outlook على ويب) استنادا إلى شروط الرسالة التي تتضمن قسم المرسل والأشخاص الذين يتم إرسال الرسالة إليهم وما إذا كان المستلمون داخل مؤسستك أو خارجها. للحصول على التفاصيل، راجع [إنشاء قاعدة حماية Outlook](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
