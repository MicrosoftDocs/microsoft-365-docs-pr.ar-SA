---
title: ميزات الحماية في Azure حماية البيانات للمستأجرين  الموجودين
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 7ad6f58e-65d7-4c82-8e65-0b773666634d
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: تشرح هذه المقالة التغييرات التي يتم طرحها على ميزات الحماية في Azure حماية البيانات
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 80256c3dc4ba8b460b1c5052081aa030a608a7d1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471550"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>ميزات الحماية في Azure حماية البيانات للمستأجرين  الموجودين

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

للمساعدة في الخطوة الأولية في حماية معلوماتك، بدءا من يوليو 2018، سيكون لدى جميع المستأجرين المؤهلين في Azure حماية البيانات ميزات الحماية في Azure حماية البيانات يتم تشغيلها بشكل افتراضي. كانت ميزات الحماية في Azure حماية البيانات معروفة سابقا Office 365 إدارة الحقوق أو Azure RMS. إذا كانت مؤسستك Office خطة خدمة E3 أو خطة خدمة أعلى، ستحصل الآن على معلومات البدء لحماية المعلومات من خلال Azure حماية البيانات عند طرح هذه الميزات.

## <a name="changes-beginning-july-1-2018"></a>التغييرات بدءا من 1 يوليو 2018

اعتبارا من 1 يوليو 2018، ستمكن Microsoft إمكانية الحماية في Azure حماية البيانات لجميع المؤسسات التي لديها إحدى خطط الاشتراك التالية:

- Office 365 تشفير الرسائل كجزء من Office 365 E3 و E5 و Microsoft E3 و E5 و Office 365 A1 و A3 و A5 و Office 365 G3 و G5. لست بحاجة إلى تراخيص إضافية لتلقي قدرات الحماية الجديدة التي يتم دعمها بواسطة Azure حماية البيانات.

- يمكنك أيضا إضافة Azure حماية البيانات الخطة 1 إلى الخطط التالية لتلقي قدرات تشفير الرسائل Office 365 الجديدة: Exchange Online الخطة 1، Exchange Online الخطة 2، Office 365 F1، Microsoft 365 Business Basic أو Microsoft 365 Business Standard أو Office 365 Enterprise E1.

- يجب أن يتم ترخيص كل مستخدم Office 365 تشفير الرسائل لكي يتم تغطيته بواسطة الميزة.

- للحصول على القائمة الكاملة، راجع Exchange Online [الخدمة](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) لتشفير Office 365 الرسائل.

يمكن لمسؤولي المستأجر التحقق من حالة الحماية في مدخل مسؤول Office 365 المستأجر.

:::image type="content" source="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png" alt-text="إدارة الحقوق في Office 365 التي تم تنشيطها" lightbox="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png":::

## <a name="why-are-we-making-this-change"></a>لماذا نقوم بهذا التغيير؟

Office 365 تشفير الرسائل إلى الاستفادة من قدرات الحماية في Azure حماية البيانات. في قلب التحسينات الأخيرة التي تم إدخالها على تشفير الرسائل في Office 365 بالإضافة إلى استثماراتنا الكبيرة في حماية المعلومات في Microsoft 365، أصبح من السهل على المؤسسات تشغيل قدرات الحماية واستخدامها، كما كان من الصعب إعداد تقنيات التشفير في الماضي. من خلال تشغيل ميزات الحماية في Azure حماية البيانات بشكل افتراضي، يمكنك البدء بسرعة في حماية بياناتك الحساسة.

## <a name="does-this-impact-me"></a>هل يؤثر ذلك علي؟

إذا كانت مؤسستك قد اشترت ترخيصا مؤهلا Office 365، سيتأثير المستأجر بهذا التغيير.

> [!IMPORTANT]
> إذا كنت تستخدم خدمات إدارة حقوق Active Directory (AD RMS) في بيئتك المحلية، فيجب إما إلغاء الاشتراك في هذا التغيير على الفور أو الترحيل إلى Azure حماية البيانات قبل طرح هذا التغيير في غضون 30 يوما. للحصول على معلومات حول كيفية إلغاء الاشتراك، راجع "أستخدم AD RMS، كيف يمكنني إلغاء الاشتراك؟" لاحقا في هذه المقالة. إذا كنت تفضل الترحيل، فشاهد الترحيل من [AD RMS إلى Azure حماية البيانات.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms).

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>هل يمكنني استخدام Azure حماية البيانات مع خدمات إدارة حقوق Active Directory (AD RMS)؟

لا. هذا سيناريو نشر غير معتمد. من دون تنفيذ خطوات إلغاء الاشتراك الإضافية، قد تبدأ بعض أجهزة الكمبيوتر تلقائيا باستخدام خدمة Azure Rights Management وتتصل أيضا بكتلة AD RMS. هذا السيناريو غير معتمد ويميز نتائج غير موثوق بها، لذلك من المهم إلغاء الاشتراك في هذا التغيير في غضون 30 يوما قبل أن نظهر هذه الميزات الجديدة. للحصول على معلومات حول كيفية إلغاء الاشتراك، راجع "أستخدم AD RMS، كيف يمكنني إلغاء الاشتراك؟" لاحقا في هذه المقالة. إذا كنت تفضل الترحيل، فشاهد الترحيل من [AD RMS إلى Azure حماية البيانات.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>كيف أعمل إذا كنت أستخدم AD RMS؟

استخدم هذه الإرشادات من إعداد البيئة ل [Azure Rights Management عندما يكون لديك خدمات إدارة حقوق Active Directory (AD RMS)](/azure/information-protection/deploy-use/prepare-environment-adrms) للتحقق مما إذا قمت بنشر AD RMS:

1. تقوم معظم عمليات نشر AD RMS بنشر نقطة اتصال الخدمة (SCP) إلى Active Directory حتى تتمكن أجهزة كمبيوتر المجال من اكتشاف مجموعة AD RMS، على الرغم من أنها اختيارية.

   استخدام ADSI Edit لمعرفة ما إذا كان لديك SCP منشور في Active Directory: CN=Configuration [اسم الخادم]، CN=Services، CN=RightsManagementServices، CN=SCP

2. إذا كنت لا تستخدم SCP، فيجب Windows أجهزة الكمبيوتر التي تتصل بتكتل AD RMS لاكتشاف خدمة من جانب العميل أو إعادة توجيه الترخيص باستخدام سجل Windows: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.

لمزيد من المعلومات حول تكوينات التسجيل هذه، راجع [](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) تمكين اكتشاف الخدمة من جانب العميل باستخدام سجل Windows وإعادة توجيه حركة مرور [خادم الترخيص](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>أستخدم AD RMS، كيف يمكنني إلغاء الاشتراك؟

لإلغاء الاشتراك في التغيير القادم، أكمل الخطوات التالية:

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-IRMConfiguration cmdlet باستخدام بناء الجملة التالي:

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>ما الذي يمكنني توقعه بعد هذا التغيير؟

بمجرد تمكين ذلك، شرط عدم إلغاء الاشتراك، يمكنك البدء باستخدام الإصدار الجديد من تشفير الرسائل في Office 365 الذي تم الإعلان عنه في [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) ويرفع من قدرات التشفير والحماية المتوفرة في Azure حماية البيانات.

:::image type="content" source="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png" alt-text="رسالة محمية من OME في Outlook على ويب" lightbox="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png":::

لمزيد من المعلومات حول التحسينات الجديدة، راجع Office 365 [تشفير الرسائل](../../compliance/ome.md).