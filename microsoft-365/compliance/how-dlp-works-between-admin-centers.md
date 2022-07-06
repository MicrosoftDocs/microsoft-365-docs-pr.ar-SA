---
title: كيفية عمل DLP مع مركز توافق & الأمان & مركز إدارة Exchange
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a7e4342a-a0a1-4b43-b166-3d7eecf5d2fd
description: تعرف على كيفية عمل DLP في مركز التوافق & الأمان مع قواعد تدفق البريد وDLP (قواعد النقل) في مركز إدارة Exchange.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: fa77bf84ff8ef2b4f194f45b9a29b49f6b662a70
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641395"
---
# <a name="how-dlp-works-between-the-compliance-center-and-exchange-admin-center"></a>كيفية عمل DLP بين مركز التوافق ومركز إدارة Exchange

في Microsoft Purview، يمكنك إنشاء نهج منع فقدان البيانات (DLP) في مركزي إدارة مختلفين:
  
- في **مدخل التوافق في Microsoft Purview**، يمكنك إنشاء نهج DLP واحد للمساعدة في حماية المحتوى في SharePoint وOneDrive وExchange وTeams والآن أجهزة نقطة النهاية. نوصي بإنشاء نهج DLP هنا. لمزيد من المعلومات، راجع [مرجع منع فقدان البيانات](data-loss-prevention-policies.md).
    
- في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>، يمكنك إنشاء نهج DLP للمساعدة في حماية المحتوى فقط في Exchange. يمكن أن يستخدم هذا النهج قواعد تدفق بريد Exchange (المعروفة أيضا بقواعد النقل)، بحيث يحتوي على المزيد من الخيارات الخاصة بمعالجة البريد الإلكتروني. لمزيد من المعلومات، راجع [DLP في مركز إدارة Exchange](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
تعمل نهج DLP التي تم إنشاؤها في مراكز الإدارة هذه جنبا إلى جنب - تشرح هذه المقالة كيفية القيام بذلك.
 
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>كيفية عمل DLP في مركز التوافق & الأمان مع قواعد تدفق البريد وDLP في مركز إدارة Exchange

بعد إنشاء نهج DLP في مركز توافق & الأمان، يتم نشر النهج إلى جميع المواقع المضمنة في النهج. إذا كان النهج يتضمن Exchange Online، تتم مزامنة النهج هناك وفرضه بنفس الطريقة تماما مثل نهج DLP الذي تم إنشاؤه في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>. 
  
إذا قمت بإنشاء نهج DLP في مركز إدارة Exchange، فستستمر هذه النهج في العمل جنبا إلى جنب مع أي نهج للبريد الإلكتروني تقوم بإنشائها في مركز التوافق & الأمان. ولكن لاحظ أن القواعد التي تم إنشاؤها في مركز إدارة Exchange لها الأسبقية. تتم معالجة كافة قواعد تدفق بريد Exchange أولا، ثم تتم معالجة قواعد DLP من مركز التوافق & الأمان.
  
وهذا يعني:
  
- لن يتم مسح الرسائل المحظورة بواسطة قواعد تدفق بريد Exchange ضوئيا بواسطة قواعد DLP التي تم إنشاؤها في مركز توافق & الأمان.
- يتم تشغيل الرسائل التي تم عزلها بواسطة قواعد تدفق بريد Exchange أو أي عوامل تصفية أخرى قبل DLP بواسطة DLP. 
- إذا كانت قاعدة تدفق بريد Exchange تعدل رسالة بطريقة تؤدي إلى مطابقتها لنهج DLP في مركز التوافق & الأمان، مثل إضافة مستخدمين خارجيين، فإن قواعد DLP ستكتشفها وتفرض النهج كما تقتضي الحاجة.
    
لاحظ أيضا أن قواعد تدفق بريد Exchange التي تستخدم الإجراء "إيقاف المعالجة" لا تؤثر على معالجة قواعد DLP في مركز توافق & الأمان - ستظل قيد المعالجة.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>تلميحات النهج في مركز التوافق & الأمان مقابل مركز إدارة Exchange

يمكن أن تعمل تلميحات النهج إما مع نهج DLP وقواعد تدفق البريد التي تم إنشاؤها في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>، أو مع نهج DLP التي تم إنشاؤها في مركز توافق & الأمان، ولكن ليس كليهما. وذلك لأن هذه النهج مخزنة في مواقع مختلفة، ولكن يمكن أن ترسم تلميحات النهج من موقع واحد فقط.
  
إذا قمت بتكوين تلميحات النهج في مركز إدارة Exchange، فلن تظهر أي تلميحات نهج تقوم بتكوينها في مركز توافق & الأمان للمستخدمين في Outlook على ويب وOutlook 2013 والإي وقت لاحق حتى تقوم بإيقاف تشغيل التلميحات في مركز إدارة Exchange. يضمن ذلك استمرار عمل قواعد تدفق بريد Exchange الحالية حتى تختار التبديل إلى مركز توافق & الأمان.
  
>[!Note]
>بينما يمكن أن ترسم تلميحات النهج من موقع واحد فقط، يتم إرسال إعلامات البريد الإلكتروني دائما، حتى لو كنت تستخدم نهج DLP في كل من مركز توافق & الأمان ومركز إدارة Exchange.
