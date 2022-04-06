---
title: تشغيل إعدادات الأمان الافتراضية Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية مساعدة إعدادات الأمان الافتراضية في حماية مؤسستك من الهجمات ذات الصلة بالهوية من خلال توفير إعدادات أمان تم تكوينها مسبقا Microsoft 365 Business Premium.
ms.openlocfilehash: dfd0d3edff541d828b70d383641aaf66c93826b6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705133"
---
# <a name="turn-on-security-defaults-for-microsoft-365-business-premium"></a>تشغيل إعدادات الأمان الافتراضية Microsoft 365 Business Premium

تساعد إعدادات الأمان الافتراضية على حماية مؤسستك من الهجمات ذات الصلة بالهوية من خلال توفير إعدادات أمان تم تكوينها مسبقا تديرها Microsoft بالنيابة عن مؤسستك. تتضمن هذه الإعدادات تمكين المصادقة متعددة العوامل (MFA) لجميع المسؤولين وحسابات المستخدمين. بالنسبة لمعظم المؤسسات، توفر إعدادات الأمان الافتراضية مستوى جيدا من أمان تسجيل الدخول الإضافي.

لمزيد من المعلومات حول إعدادات الأمان الافتراضية والسياسات التي تفرضها، راجع [ما هي إعدادات الأمان الافتراضية؟](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

إذا تم إنشاء اشتراكك في 22 أكتوبر 2019&mdash; أو بعده، فقد تكون إعدادات الأمان الافتراضية قد تم تمكينها تلقائيا لكي تقوم بالتحقق من إعداداتك للتأكد.

لتمكين إعدادات الأمان الافتراضية في Azure Active Directory (Azure AD) أو للتحقق مما إذا كان قد تم تمكينها بالفعل:

1. سجل دخولك <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">إلى مركز مسؤولي Microsoft 365</a> باستخدام مسؤول الأمان أو مسؤول الوصول الشرطي أو بيانات اعتماد المسؤول العام.

2. في الجزء الأيسر، حدد **إظهار الكل،** ثم ضمن **مراكز** الإدارة، حدد **Azure Active Directory**.

3. في الجزء الأيسر من **مركز إدارة Azure Active Directory** ، حدد **Azure Active Directory**.

4. من القائمة اليسرى من لوحة المعلومات، في **المقطع إدارة** ، حدد **خصائص**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="لقطة شاشة لمركز إدارة Azure Active Directory تعرض موقع عنصر القائمة Properties.":::

5. في أسفل صفحة **Properties** ، حدد **إدارة إعدادات الأمان الافتراضية**.

6. في الجزء الأيمن، سترى الإعداد **تمكين إعدادات الأمان** الافتراضية. إذا **تم** تحديد نعم، يتم تمكين إعدادات الأمان الافتراضية بالفعل ولا يلزم اتخاذ أي إجراء آخر. إذا لم يتم تمكين إعدادات الأمان الافتراضية حاليا، فحدد **نعم** لتمكينها، ثم حدد **حفظ**.

> [!NOTE]
> إذا كنت تستخدم سياسات الوصول الشرطي، ستحتاج إلى إيقاف تشغيلها قبل استخدام إعدادات الأمان الافتراضية.
>
> يمكنك استخدام إما إعدادات الأمان الافتراضية أو سياسات الوصول الشرطي، ولكن لا يمكنك استخدام كليهما في الوقت نفسه.

## <a name="consider-using-conditional-access"></a>التفكير في استخدام الوصول الشرطي

إذا كانت مؤسستك لديها متطلبات أمان معقدة أو كنت بحاجة إلى تحكم أكثر تشعبا في سياسات الأمان، يجب عليك التفكير في استخدام "الوصول الشرطي" بدلا من إعدادات الأمان الافتراضية لتحقيق وضع أمان مماثل أو أعلى. 

يتيح لك الوصول الشرطي إنشاء سياسات تتفاعل مع أحداث تسجيل الدخول وتحديدها وطلب إجراءات إضافية قبل منح المستخدم حق الوصول إلى تطبيق أو خدمة. يمكن أن تكون سياسات الوصول الشرطي محددة ومحددة، وتمكين المستخدمين من تحقيق الإنتاجية في أي مكان وأينما، مع حماية مؤسستك أيضا.

تتوفر إعدادات الأمان الافتراضية لجميع العملاء، بينما يتطلب الوصول الشرطي ترخيصا ل إحدى الخطط التالية:

- Azure Active Directory Premium P1 أو P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 أو E5
- Enterprise Mobility & Security E3 أو E5

إذا كنت تريد استخدام "الوصول الشرطي" لتكوين سياسات مكافئة لتلك التي تم تمكينها بواسطة إعدادات الأمان الافتراضية، فاستعرض الدليلين التاليين خطوة بخطوة:

- [طلب MFA للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [يتطلب MFA لإدارة Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [حظر المصادقة القديمة](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [طلب MFA لجميع المستخدمين](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [يتطلب تسجيل Azure AD MFA](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) - يتطلب Azure AD Identity Protection، الذي هو جزء من Azure Active Directory Premium P2

لمعرفة المزيد حول الوصول الشرطي، راجع [ما هو الوصول الشرطي؟](/azure/active-directory/conditional-access/overview) لمزيد من المعلومات حول إنشاء نهج الوصول الشرطي، راجع [إنشاء نهج وصول شرطي](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> إذا كان لديك خطة أو ترخيص يوفر الوصول الشرطي ولكن لم تقم بعد بإنشاء أي من سياسات الوصول الشرطي، يمكنك استخدام إعدادات الأمان الافتراضية. ومع ذلك، ستحتاج إلى إيقاف تشغيل إعدادات الأمان الافتراضية قبل أن تتمكن من استخدام سياسات الوصول الشرطي.
