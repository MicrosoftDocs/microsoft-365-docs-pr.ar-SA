---
title: Microsoft Productivity Score - الخصوصية
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
description: كيفية حماية الخصوصية باستخدام "نقاط الإنتاجية".
ms.openlocfilehash: 94e0e1fb3190bc45fb0ad580cd823cb121fb60cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572943"
---
# <a name="privacy-controls-for-productivity-score"></a>عناصر تحكم الخصوصية ل "نقاط الإنتاجية"

توفر "نقاط الإنتاجية" تحليلات حول رحلة التحويل الرقمي في مؤسستك من خلال استخدامها Microsoft 365 وتجارب التقنية التي تدعمها.  تعكس نقاط مؤسستك قياسات تجربة الأشخاص والتكنولوجيا ويمكن مقارنتها بمقاييس معايير من مؤسسات مماثلة لمقاييسك. لمزيد من التفاصيل، يمكنك عرض [نظرة عامة حول نقاط الإنتاجية](productivity-score.md).

خصوصيتك مهمة ل Microsoft. لمعرفة كيفية حماية خصوصيتك، راجع [بيان الخصوصية الخاص ب Microsoft](https://privacy.microsoft.com/privacystatement). تمنحك "نقاط الإنتاجية"، كمسؤول تكنولوجيا المعلومات في مؤسستك، إمكانية الوصول إلى إعدادات الخصوصية للتأكد من أن أي معلومات "نقاط الإنتاجية" التي تقوم ب عرضها قابلة للتنفيذ، مع عدم المساس بالثقة التي تضعها مؤسستك في Microsoft.

ضمن منطقة تجارب الأشخاص، تتوفر المقاييس على مستوى المؤسسة فقط. تبحث هذه المنطقة في كيفية استخدام الأشخاص Microsoft 365 من خلال النظر إلى فئات التعاون في المحتوى والتنقل والاجتماعات والعمل الجماعي والتواصل. نحن نمكنك من استخدام مستويات متعددة من عناصر التحكم لمساعدتك على تلبية احتياجات نهج الخصوصية الداخلية.
تمنحك عناصر التحكم:

- أدوار المسؤولين المرنة للتحكم في الأشخاص الذين يمكنهم رؤية المعلومات في "نقاط الإنتاجية".
- القدرة على إلغاء الاشتراك في منطقة تجارب الأشخاص.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>أدوار المسؤولين المرنة للتحكم في الأشخاص الذين يمكنهم رؤية المعلومات في "نقاط الإنتاجية"

لعرض "نقاط الإنتاجية" بالكامل، يجب أن تكون أحد أدوار المسؤولين التالية:

- المسؤول العام
- Exchange المسؤولين
- SharePoint مسؤول
- Skype for Business مسؤول
- Teams مسؤول
- القارئ العام
- قارئ التقارير
- قارئ تقارير ملخص الاستخدام

تعيين دور قارئ التقارير أو قارئ تقارير ملخص الاستخدام إلى أي شخص مسؤول عن إدارة التغيير واعتماده، وليس بالضرورة مسؤول تكنولوجيا المعلومات. يمنحه هذا الدور حق الوصول إلى تجربة "نقاط الإنتاجية" الكاملة في Microsoft 365 الإدارة.

يجب تعيين دور قارئ تقارير ملخص الاستخدام من خلال PowerShell cmdlets حتى يصبح قابلا للتعيين من مركز مسؤولي Microsoft 365 لاحقا في 2020.

لتعيين دور قارئ تقارير ملخص الاستخدام مع PowerShell:

- تشغيل PowerShell التالي:

```powershell
Connect-AzureAD
Enable-AzureADDirectoryRole -RoleTemplateId '75934031-6c7e-415a-99d7-48dbd49e875e'
$role=Get-AzureADDirectoryRole -Filter "roleTemplateId eq '75934031-6c7e-415a-99d7-48dbd49e875e'"
Get-AzureADDirectoryRoleMember -ObjectId $role.ObjectId
$u=Get-AzureADUser -ObjectId <user upn>
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId $u.ObjectId
```

</br>


## <a name="capability-to-opt-out-of-people-experiences"></a>إمكانية إلغاء الاشتراك في تجارب الأشخاص

يمكنك أيضا إلغاء الاشتراك في منطقة تجارب الأشخاص في "نقاط الإنتاجية". إذا قمت بلإلغاء الاشتراك، لن يتمكن أي شخص من مؤسستك من عرض هذه المقاييس، وستزال مؤسستك من أي عمليات حسابية تتضمن الاتصال والاجتماعات والعمل الجماعي والتعاون في المحتوى والتنقل. يجب أن تكون المسؤول العام لإلغاء اشتراك مؤسستك في تقارير تجارب الأشخاص.

لإلغاء الاشتراك:

1. في مركز الإدارة، **انتقل إلى الإعدادات**  >   **أو الإعدادات** >  **Productivity Score**.
2. قم ب إلغاء التحقق من المربع الذي Microsoft 365 استخدام بيانات الاستخدام **للأشخاص الذين يجربون تحليلات.** لفهم كيفية تعديل إعدادات مشاركة البيانات لتحليلات نقطة النهاية في إدارة تكوين Intune، حدد **معرفة المزيد**.
3. حدد  **حفظ**.

:::image type="content" source="../../media/orgsettingspageoptout.png" alt-text="صفحة إعدادات المؤسسة حيث يمكنك إلغاء الاشتراك في تجارب الأشخاص.":::
