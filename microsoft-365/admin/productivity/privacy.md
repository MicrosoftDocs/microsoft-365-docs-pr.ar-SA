---
title: نقاط الإنتاجية ورؤى الخصوصية في Microsoft
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: كيفية حماية الخصوصية باستخدام نقاط الإنتاجية.
ms.openlocfilehash: 823e2cc087d3f0e9c486d8c0c4eca92ba42aee21
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467921"
---
# <a name="privacy-controls-for-productivity-score"></a>عناصر التحكم في الخصوصية ل "نقاط الإنتاجية"

توفر نقاط الإنتاجية رؤى حول رحلة التحول الرقمي لمؤسستك من خلال استخدامها Microsoft 365 والتجارب التكنولوجية التي تدعمها.  تعكس درجة مؤسستك قياسات تجربة الأشخاص والتكنولوجيا ويمكن مقارنتها بمقاييس المؤسسات المماثلة لمقاييسك. لمزيد من التفاصيل، اطلع على [نظرة عامة على "نقاط الإنتاجية](productivity-score.md)".

خصوصيتك مهمة ل Microsoft. لمعرفة كيفية حماية خصوصيتك، راجع [بيان الخصوصية الخاص ب Microsoft](https://privacy.microsoft.com/privacystatement). تمنحك "نقاط الإنتاجية"، بصفتك مسؤول تكنولوجيا المعلومات في مؤسستك، إمكانية الوصول إلى إعدادات الخصوصية للمساعدة في التأكد من أن أي معلومات "نقاط الإنتاجية" التي تعرضها قابلة للتنفيذ، مع عدم المساس بالثقة التي تضعها مؤسستك في Microsoft.

ضمن مجال تجارب الأشخاص، تتوفر المقاييس على المستوى التنظيمي فقط. تتناول هذه المنطقة كيفية استخدام الأشخاص Microsoft 365 من خلال النظر إلى فئات التعاون في المحتوى والتنقل والاجتماعات والعمل الجماعي والتواصل. نحن نمكنك من خلال مستويات متعددة من عناصر التحكم لمساعدتك على تلبية احتياجات نهج الخصوصية الداخلية.
تمنحك عناصر التحكم ما يلي:

- أدوار المسؤول المرنة للتحكم في من يمكنه رؤية المعلومات في نقاط الإنتاجية.
- القدرة على إلغاء الاشتراك في منطقة تجارب الأشخاص.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>أدوار المسؤول المرنة للتحكم في من يمكنه رؤية المعلومات في نقاط الإنتاجية

لعرض نقاط الإنتاجية بأكملها، يجب أن تكون أحد أدوار المسؤول التالية:

- مسؤول عمومي
- مسؤولو Exchange
- مسؤول SharePoint
- مسؤول Skype for Business
- مسؤول Teams
- القارئ العمومي
- قارئ التقارير
- قارئ تقارير ملخص الاستخدام

تعيين دور قارئ التقارير أو قارئ تقارير ملخص الاستخدام إلى أي شخص مسؤول عن إدارة التغيير والاعتماد، ولكن ليس بالضرورة مسؤول تكنولوجيا المعلومات. يمنحهم هذا الدور إمكانية الوصول إلى تجربة نقاط الإنتاجية الكاملة في مركز إدارة Microsoft 365.

يجب تعيين دور قارئ تقارير ملخص الاستخدام من خلال PowerShell cmdlets حتى يصبح قابلا للتعيين من مركز مسؤولي Microsoft 365 لاحقا في عام 2020.

لتعيين دور قارئ تقارير ملخص الاستخدام باستخدام PowerShell:

- تشغيل PowerShell التالية:

```powershell
Connect-AzureAD
Enable-AzureADDirectoryRole -RoleTemplateId '75934031-6c7e-415a-99d7-48dbd49e875e'
$role=Get-AzureADDirectoryRole -Filter "roleTemplateId eq '75934031-6c7e-415a-99d7-48dbd49e875e'"
Get-AzureADDirectoryRoleMember -ObjectId $role.ObjectId
$u=Get-AzureADUser -ObjectId <user upn>
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId $u.ObjectId
```

</br>


## <a name="capability-to-opt-out-of-people-experiences"></a>القدرة على إلغاء الاشتراك في تجارب الأشخاص

يمكنك أيضا إلغاء الاشتراك في مجال تجارب الأشخاص في "نقاط الإنتاجية". إذا رفضت المشاركة، فلن يتمكن أي شخص من مؤسستك من عرض هذه المقاييس، وستتم إزالة مؤسستك من أي عمليات حسابية تتضمن الاتصال والاجتماعات والعمل الجماعي والتعاون في المحتوى والتنقل. يجب أن تكون مسؤولا عموميا لسحب مؤسستك من تقارير تجارب الأشخاص.

لإلغاء الاشتراك:

1. في مركز الإدارة، انتقل إلى **الإعدادات**  >   **Org الإعدادات** >  **Productivity Score**.
2. قم بإلغاء تحديد المربع الذي يشير **إلى السماح باستخدام بيانات الاستخدام Microsoft 365 للأشخاص المعرفية**. لفهم كيفية تعديل إعدادات مشاركة البيانات لتحليلات نقطة النهاية في إدارة تكوين Intune، حدد **"معرفة المزيد**".
3. حدد  **"حفظ**".

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="صفحة إعدادات المؤسسة حيث يمكنك إلغاء الاشتراك في تجارب الأشخاص.":::
