---
title: حماية البيانات طرح ميزات الحماية في Azure للمستأجرين الحاليين
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
ms.openlocfilehash: 38dd1accf4641d6dfe3f66574b1072e2500cb914
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647810"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>حماية البيانات طرح ميزات الحماية في Azure للمستأجرين الحاليين

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

للمساعدة في الخطوة الأولية لحماية معلوماتك، بدءا من يوليو 2018، سيكون لدى جميع المستأجرين المؤهلين حماية البيانات Azure ميزات الحماية في Azure حماية البيانات قيد التشغيل بشكل افتراضي. كانت ميزات الحماية في حماية البيانات Azure معروفة سابقا في Office 365 باسم Rights Management أو Azure RMS. إذا كانت مؤسستك لديها خطة خدمة Office E3 أو خطة خدمة أعلى، فستحصل الآن على بداية بادئة لحماية المعلومات من خلال Azure حماية البيانات عندما نطرح هذه الميزات.

## <a name="changes-beginning-july-1-2018"></a>تغييرات تبدأ في 1 يوليو 2018

بدءا من 1 يوليو 2018، ستقوم Microsoft بتمكين إمكانية الحماية في Azure حماية البيانات لجميع المؤسسات التي لديها إحدى خطط الاشتراك التالية:

- يتم تقديم Office 365 تشفير الرسائل كجزء من Office 365 E3 وE5 وMicrosoft E3 وE5 Office 365 A1 وA3 وA5 Office 365 G3 وG5. لا تحتاج إلى تراخيص إضافية لتلقي قدرات الحماية الجديدة التي يتم تشغيلها بواسطة Azure حماية البيانات.

- يمكنك أيضا إضافة Azure حماية البيانات الخطة 1 إلى الخطط التالية لتلقي قدرات تشفير الرسائل Office 365 الجديدة: Exchange Online الخطة 1، Exchange Online الخطة 2، Office 365 F1، Microsoft 365 Business Basic أو Microsoft 365 Business Standard أو Office 365 Enterprise E1.

- يجب أن يكون كل مستخدم يستفيد من Office 365 تشفير الرسائل مرخصا ليغطي بواسطة الميزة.

- للحصول على القائمة الكاملة، راجع [أوصاف الخدمة Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) لتشفير الرسائل Office 365.

يمكن لمسؤولي المستأجرين التحقق من حالة الحماية في مدخل مسؤول Office 365.

:::image type="content" source="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png" alt-text="إدارة الحقوق في Office 365 التي تم تنشيطها" lightbox="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png":::

## <a name="why-are-we-making-this-change"></a>لماذا نقوم بهذا التغيير؟

يعمل تشفير الرسائل Office 365 على الاستفادة من قدرات الحماية في Azure حماية البيانات. في صميم التحسينات الأخيرة لتشفير الرسائل Office 365 استثماراتنا الأوسع لحماية المعلومات في Microsoft 365، نسهل على المؤسسات تشغيل قدرات الحماية واستخدامها، كما كان من الصعب إعداد تقنيات التشفير من الناحية التاريخية. من خلال تشغيل ميزات الحماية في Azure حماية البيانات بشكل افتراضي، يمكنك البدء بسرعة لحماية بياناتك الحساسة.

## <a name="does-this-impact-me"></a>هل يؤثر هذا علي؟

إذا قامت مؤسستك بشراء ترخيص Office 365 مؤهل، فسيتأثر المستأجر بهذا التغيير.

> [!IMPORTANT]
> إذا كنت تستخدم خدمات Rights Management Active Directory (AD RMS) في بيئتك المحلية، فيجب إما إلغاء الاشتراك في هذا التغيير على الفور أو الترحيل إلى Azure حماية البيانات قبل طرح هذا التغيير في غضون 30 يوما. للحصول على معلومات حول كيفية إلغاء الاشتراك، راجع "أستخدم AD RMS، كيف يمكنني إلغاء الاشتراك؟" لاحقا في هذه المقالة. إذا كنت تفضل الترحيل، فراجع [الترحيل من AD RMS إلى Azure حماية البيانات.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>هل يمكنني استخدام Azure حماية البيانات مع خدمات Rights Management Active Directory (AD RMS)؟

لا. هذا ليس سيناريو نشر معتمدا. دون اتخاذ خطوات إلغاء الاشتراك الإضافية، قد تبدأ بعض أجهزة الكمبيوتر تلقائيا باستخدام خدمة Rights Management Azure والاتصال أيضا بمجموعة AD RMS. هذا السيناريو غير مدعوم ولديه نتائج غير موثوق بها، لذلك من المهم إلغاء الاشتراك في هذا التغيير في غضون 30 يوما القادمة قبل طرح هذه الميزات الجديدة. للحصول على معلومات حول كيفية إلغاء الاشتراك، راجع "أستخدم AD RMS، كيف يمكنني إلغاء الاشتراك؟" لاحقا في هذه المقالة. إذا كنت تفضل الترحيل، فراجع [الترحيل من AD RMS إلى Azure حماية البيانات.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>كيف أعمل معرفة ما إذا كنت أستخدم AD RMS؟

استخدم هذه الإرشادات من [إعداد البيئة ل Azure Rights Management عندما يكون لديك أيضا خدمات Rights Management Active Directory (AD RMS)](/azure/information-protection/deploy-use/prepare-environment-adrms) للتحقق مما إذا كنت قد نشرت AD RMS:

1. على الرغم من أنه اختياري، فإن معظم عمليات نشر AD RMS تنشر نقطة اتصال الخدمة (SCP) إلى Active Directory بحيث يمكن لأجهزة كمبيوتر المجال اكتشاف مجموعة AD RMS.

   استخدم ADSI Edit لمعرفة ما إذا كان لديك SCP منشور في Active Directory: CN=Configuration [server name], CN=Services, CN=RightsManagementServices, CN=SCP

2. إذا كنت لا تستخدم SCP، يجب تكوين أجهزة الكمبيوتر Windows التي تتصل بنظام مجموعة AD RMS لاكتشاف الخدمة من جانب العميل أو إعادة توجيه الترخيص باستخدام سجل Windows: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.

لمزيد من المعلومات حول تكوينات التسجيل هذه، راجع [تمكين اكتشاف الخدمة من جانب العميل باستخدام سجل Windows](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) [وإعادة توجيه حركة مرور خادم الترخيص](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>أستخدم AD RMS، كيف يمكنني إلغاء الاشتراك؟

لإلغاء الاشتراك في التغيير القادم، أكمل الخطوات التالية:

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell وقم بالاتصال Exchange Online. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-IRMConfiguration cmdlet باستخدام بناء الجملة التالي:

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>ما الذي يمكنني توقعه بعد إجراء هذا التغيير؟

بمجرد تمكين هذا الخيار، شريطة عدم إلغاء الاشتراك، يمكنك البدء في استخدام الإصدار الجديد من تشفير الرسائل Office 365 الذي تم الإعلان عنه في [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) والاستفادة من قدرات التشفير والحماية ل Azure حماية البيانات.

:::image type="content" source="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png" alt-text="رسالة محمية بواسطة OME في Outlook على ويب" lightbox="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png":::

لمزيد من المعلومات حول التحسينات الجديدة، راجع [Office 365 تشفير الرسائل](../../compliance/ome.md).
