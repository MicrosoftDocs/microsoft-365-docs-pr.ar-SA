---
title: إهمال تطبيق عارض OME
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6336cabb-b06e-402f-9e85-8bb9eb4ce68f
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: تمت إزالة تطبيق عارض Office 365 Message Encryption (OME) من متاجر Android وApple في عام 2018.
ms.openlocfilehash: 2e1e0ead7d34761a3159b4b51368ea4460acb596
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630070"
---
# <a name="deprecating-message-encryption-viewer-app"></a>إهمال تطبيق عارض تشفير الرسائل

في 15 أغسطس 2018، قمنا بإزالة تطبيق Office 365 Message Encryption (OME) Viewer للأجهزة المحمولة من متاجر Android وApple. طلب Office 365 تطبيق الأجهزة المحمولة لعارض تشفير الرسائل لقراءة رسائل البريد الإلكتروني والمرفقات التي تم تشفيرها باستخدام الإصدار السابق من OME على هواتف Apple وAndroid. بصرف النظر عن إزالة تطبيق OME Viewer، لا نقوم بإجراء أي تغييرات أخرى على الإصدار السابق من OME.
  
## <a name="changes-from-august-2018"></a>تغييرات من أغسطس 2018

كما تم الإعلان عنه في سبتمبر 2017، أصدرنا إصدارا جديدا من [Office 365 تشفير الرسائل](https://aka.ms/ome2017) بحيث يمكن للمستخدمين إرسال رسائل مشفرة ومحمية إلى أي شخص داخل المؤسسة أو خارجها دون متطلبات تطبيق الأجهزة المحمولة. منذ ذلك الحين، أضفنا قدرات إضافية:
  
- [قالب مشفر فقط](https://aka.ms/encryptonly)

- [التحكم في فك تشفير المرفقات](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

مع هذا التغيير، لن يتمكن المستخدمون من تنزيل تطبيق الأجهزة المحمولة Office 365 Message Encryption Viewer بدءا من 1 أغسطس. ونتيجة لذلك، قد لا يتمكن مستلمو البريد من قراءة الرسائل المشفرة باستخدام الإصدار السابق من OME على بعض أجهزة Android وApple المحمولة. ومع ذلك، سيظل بإمكانهم قراءة هذه الرسائل على أجهزة الكمبيوتر الشخصية (عبر مستعرضات سطح المكتب). سيظل المستخدمون الذين قاموا بتنزيل التطبيق قادرين على استخدامه.
  
## <a name="why-this-change-was-made"></a>سبب إجراء هذا التغيير

لم يعد الإصدار الجديد من OME يتطلب تطبيق الأجهزة المحمولة لقراءة رسائل البريد الإلكتروني والمرفقات المحمية. يمكن للعملاء الذين يستخدمون تشفير الرسائل في Microsoft Purview عرض الرسالة المحمية في Outlook للأجهزة المحمولة ويمكن لغير العملاء عرض الرسائل المحمية في مستعرض.
  
تعد مطالبة المستخدمين بتنزيل تطبيق الأجهزة المحمولة عقبة أخرى أمام العملاء لعرض الرسائل المحمية. يوفر تشفير الرسائل في Microsoft Purview تجربة أفضل للأجهزة المحمولة.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>هل يمكنني الاستمرار في استخدام الإصدار السابق من تشفير الرسائل Office 365

لن يتم إهمال الإصدار السابق من Office 365 تشفير الرسائل في الوقت الحالي، ومع ذلك، قمنا بإجراء تحسينات كبيرة على تشفير الرسائل في Microsoft Purview، مما يسهل تشفير البيانات الحساسة وحمايتها لأي شخص وعلى أي جهاز - بما في ذلك قدرة المستخدمين على قراءة الرسائل المحمية مباشرة في Outlook (سطح المكتب والجوال و  الويب).
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>ما الذي أحتاج إلى فعله للتحضير لهذا التغيير

إذا كانت مؤسستك ترسل حاليا مرفقات مشفرة إلى المستلمين الذين يحتاجون إلى تطبيق عارض OME، فيجب عليك تحديث الوثائق وموارد التدريب.
  
نوصي بتحديث قواعد تدفق بريد Exchange الحالية لاستخدام تشفير الرسائل في Microsoft Purview حتى تتمكن مؤسستك من الاستفادة من الإمكانات الجديدة والمحسنة. بعد إعداد تشفير الرسائل في Microsoft Purview، لن يحتاج المستلمون إلى تطبيق OME Viewer لقراءة الرسائل المشفرة على الأجهزة المحمولة.
  
توصي Microsoft بوضع خطة للانتقال إلى تشفير الرسائل في Microsoft Purview بمجرد أن يكون ذلك معقولا لمؤسستك. للحصول على الإرشادات، راجع [إعداد تشفير الرسائل في Microsoft Purview](set-up-new-message-encryption-capabilities.md). إذا كنت تريد معرفة المزيد حول كيفية عمل تشفير الرسائل أولا، فراجع [تشفير الرسائل](ome.md).
