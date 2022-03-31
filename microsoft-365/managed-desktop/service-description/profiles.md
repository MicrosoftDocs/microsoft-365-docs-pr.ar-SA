---
title: فهم ملفات تعريف الجهاز
description: ملفات التعريف المختلفة التي يمكن للمسؤولين تعيينها إلى الأجهزة
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d12a197db8dbcb6356882082c212754fef726d4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578183"
---
# <a name="device-profiles"></a>ملفات تعريف الجهاز

يمكنك التفكير في ملفات تعريف الجهاز على أنها جزء من تسلسل هيكلي من خيارات تكوين الجهاز.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="تكوينات الجهاز المعروضة كهرم. يلي الوصف.":::

| خيارات تكوين الجهاز | الوصف
| ----- | ----- |
| تكويناتك | في الأعلى، توجد التكوينات الخاصة بك، مثل تفاصيل الشبكة أو التطبيقات. يمكن أن يكون للجهاز أي عدد من هذه التكوينات، التي لا يتم إدارتها أو حظرها بواسطة Microsoft Managed Desktop. |
| التخصيصات | المستوى الأعلى التالي هو [التخصيصات الإضافية](customizing.md). يمكن أن يحتوي كل جهاز على تخصيص واحد أو أكثر (أو لا). يمكن للتخصيصات إما تعديل طبقة ذات مستوى أدنى (ملفات تعريف الجهاز أو التكوين الأساس)، أو أن تكون طلبا جديدا تماما يتم وضعه في طبقات أعلى التكوين القياسي. |
| ملفات تعريف الجهاز | يجب أن يكون لكل جهاز سطح مكتب مدار من Microsoft ملف تعريف واحد، وملف تعريف واحد فقط. يمكن للمسؤولين تحديد ملف التعريف الذي تم تعيين جهاز له.<br><br>يمكنك تعيين ملفات تعريف مختلفة تم تعيينها مسبقا إلى الأجهزة. تم تحسين كل ملف تعريف لتلبية احتياجات أنواع معينة من المستخدمين. تتوفر ثلاثة ملفات تعريف للجهاز:<ul><li>Standard</li><li>البيانات الحساسة</li><li>مستخدم الطاقة</li> |
| Foundation | بشكل أساسي، يحتوي كل جهاز سطح مكتب مدار من Microsoft على أساس يتضمن:<br><ul><li>أساس الأمان القياسي</li><li>سياسات التوافق</li><li>Windows التحديث</li><li>المجموعات</li></ul><br>للعمل مع Microsoft Managed Desktop، يجب أن يتضمن كل جهاز كل هذه العناصر. لا يمكن تغيير هذه العناصر من قبل المسؤولين. يجب إرسال طلب إلى Microsoft Managed Desktop. |

## <a name="device-profile-details"></a>تفاصيل ملف تعريف الجهاز

يلخص الجدول التالي الإعدادات وقيمها الافتراضية لكل إعداد تم تكوينه بواسطة ملفات تعريف الجهاز. في الكواليس، يتم تكوين هذه الإعدادات باستخدام OMA-URIs باستخدام ملفات تعريف التكوين المخصصة في إدارة نقاط النهاية من Microsoft.

<br>

****

| الميزة | البيانات الحساسة | Power User | Standard |
| ----- | :-----: | :-----: | :-----: |
|**حظر التخزين الخارجي**| نعم | نعم | لا |
|**[مستوى كتلة السحابة](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)**| عال | عال | عال |
|**تعطيل حسابات Microsoft**| نعم | نعم | لا |
|**تعطيل البيانات OneDrive**| نعم | نعم | لا |
|**[التبديل إلى سطح مكتب آمن للرفع](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-useraccountcontrol-switchtothesecuredesktopwhenpromptingforelevation)**| لا | نعم | لا |
|**علامة جهاز Microsoft Defender لنقطة النهاية**| M365Managed-SensitiveData | M365Managed-PowerUser | M365Managed-Standard |
|**المسؤول على الجهاز؟**| لا | نعم | لا |
|**ملف تعريف Autopilot**| MMD Standard | MMD Power User | MMD Standard |
|**AppLocker**| نعم | لا | لا |
|**حظر المتجر العام**| نعم | نعم | لا |
|

يتضمن كل ملف تعريف جهاز أيضا هذه العناصر:

- مجموعة أجهزة Azure Active Directory ديناميكية العضوية.
- مجموعة أجهزة Azure Active Directory ثابتة العضوية.
- ملف إدارة نقاط النهاية من Microsoft تكوين.

> [!IMPORTANT]
> لا تعدل عضوية هذه المجموعات مباشرة. استخدم الواجهة كما هو موضح في [إعادة تعيين ملفات التعريف](../working-with-managed-desktop/change-device-profile.md).

## <a name="limitations"></a>القيود

يمكنك طلب استثناءات لملفات تعريف الجهاز وتفاصيلها كما هو حالك مع أي نهج آخر.

ضع في اعتبارك أنه يمكنك الحصول على ملف تعريف واحد فقط من كل جهاز في مؤسسة Azure Active Directory ("المستأجر"). على سبيل المثال، لا يمكنك طلب أن يقوم ملف تعريف جهاز البيانات الحساس بتعطيل AppLocker لبعض المستخدمين فقط. يجب أن يكون التكوين نفسه لجميع الأجهزة التي بها ملف تعريف جهاز بيانات حساس.

يمكن أن يحتوي كل جهاز على ملف تعريف واحد فقط. إذا استخدم أكثر من مستخدم واحد جهازا معينا، فإن كل المستخدمين على هذا الجهاز سيكون لديهم التكوين نفسه.
