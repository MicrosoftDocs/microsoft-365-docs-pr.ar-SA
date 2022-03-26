---
title: كيفية عمل DLP مع مركز & الأمان & Exchange مركز الإدارة
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
description: تعرف على كيفية عمل DLP في مركز & الأمان مع قواعد تدفق البريد (DLP) (قواعد النقل) في Exchange إدارة البريد.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 90706b3dad55ff84d274656673f9a60dbd71e35f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63566525"
---
# <a name="how-dlp-works-between-the-microsoft-365-compliance-center-and-exchange-admin-center"></a>كيفية عمل DLP بين مركز Microsoft 365 ومركز إدارة Exchange

في Microsoft 365، يمكنك إنشاء نهج منع فقدان البيانات (DLP) في مركزين مختلفين للمسؤولين:
  
- في **Microsoft 365 التوافق**، يمكنك إنشاء نهج DLP واحد للمساعدة في حماية المحتوى في SharePoint و OneDrive و Exchange و Teams و الآن أجهزة نقطة النهاية. نوصي بإنشاء نهج DLP هنا. لمزيد من المعلومات، راجع [مرجع منع فقدان البيانات](data-loss-prevention-policies.md).
    
- في مركز <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange،</a> يمكنك إنشاء نهج DLP للمساعدة في حماية المحتوى فقط في Exchange. يمكن أن يستخدم هذا النهج Exchange تدفق البريد الإلكتروني (المعروفة أيضا بقواعد النقل)، بحيث تتوفر فيه خيارات أكثر خاصة لمعالجة البريد الإلكتروني. لمزيد من المعلومات، راجع [DLP في Exchange الإدارة](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
تعمل شرطة DLP التي تم إنشاؤها في مراكز الإدارة هذه جنبا إلى جنب - يشرح هذا الموضوع كيفية ذلك.
  
![صفحات DLP في مركز الأمان والتوافق Exchange مركز الإدارة.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>كيفية عمل DLP في مركز & الأمان مع قواعد تدفق البريد و DLP في مركز إدارة Exchange

بعد إنشاء نهج DLP في مركز & الأمان، يتم نشر النهج إلى كل المواقع المضمنة في النهج. إذا كان النهج Exchange Online، تتم مزامنة النهج هناك، كما يتم فرضه تماما بالطريقة نفسها التي تم بها إنشاء نهج DLP في Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز الإدارة</a>. 
  
إذا قمت بإنشاء سياسات DLP في مركز إدارة Exchange، فإن هذه السياسات ستستمر في العمل جنبا إلى جنب مع أي سياسات للبريد الإلكتروني تقوم & مركز التوافق. ولكن تجدر الإشارة إلى أن القواعد التي تم إنشاؤها في Exchange إدارة المؤسسة لها الأسبقية. تتم Exchange قواعد تدفق البريد أولا، ثم تتم معالجة قواعد DLP من مركز & الأمان.
  
وهذا يعني ما يلي:
  
- لن يتم فحص الرسائل Exchange قواعد تدفق البريد بواسطة قواعد DLP التي تم إنشاؤها في مركز التوافق & الأمان.

- لن يتم فحص الرسائل التي تم فحصها بواسطة Exchange تدفق البريد أو أي عوامل تصفية أخرى قبل تشغيل DLP بواسطة DLP.
    
- إذا كانت قاعدة تدفق بريد Exchange تعدل رسالة بطريقة تؤدي إلى مطابقتها مع نهج DLP في مركز التوافق ل أمان & - مثل إضافة مستخدمين خارجيين - فإن قواعد DLP ستكتشف ذلك وستفرض النهج حسب الحاجة.
    
لاحظ أيضا Exchange قواعد تدفق البريد التي تستخدم الإجراء "إيقاف المعالجة" لا تؤثر على معالجة قواعد DLP في مركز التوافق ل أمان & - وستبقى تتم معالجتها.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>تلميحات النهج في مركز & الأمان مقابل Exchange إدارة

يمكن أن تعمل تلميحات النهج إما مع نهج DLP وقواعد تدفق البريد التي تم <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">إنشاؤها</a> في مركز إدارة Exchange، أو مع نهج DLP التي تم إنشاؤها في مركز التوافق & الأمان، وليس كليهما. وذلك لأن هذه النهج مخزنة في مواقع مختلفة، ولكن يمكن أن ترسم تلميحات النهج من موقع واحد فقط.
  
إذا قمت بتكوين تلميحات النهج في مركز إدارة Exchange، فلن تظهر أي تلميحات نهج تقوم بتكوينها في مركز التوافق ل الأمان & للمستخدمين في Outlook على ويب و Outlook 2013 واللاحقة حتى تقوم إيقاف تشغيل التلميحات في مركز إدارة Exchange. يضمن ذلك استمرار Exchange تدفق البريد الحالية إلى أن تختار التبديل إلى مركز التوافق & الأمان.
  
لاحظ أنه على الرغم من أن تلميحات النهج يمكن أن ترسم من موقع واحد فقط، إلا أنه يتم إرسال إعلامات البريد الإلكتروني دائما، حتى لو كنت تستخدم نهج DLP في كل من مركز التوافق & والأمان ومركز إدارة Exchange.
