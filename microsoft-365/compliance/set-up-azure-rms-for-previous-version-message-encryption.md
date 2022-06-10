---
title: إعداد Rights Management Azure للإصدار السابق من تشفير الرسائل
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 2cba47b3-f09e-4911-9207-ac056fcb9db7
description: يعتمد الإصدار السابق من تشفير الرسائل Office 365 على Microsoft Azure Rights Management (المعروف سابقا باسم Windows Rights Management Azure Active Directory).
ms.openlocfilehash: 66447d601d86f1863cf060a3ad097686bb58be98
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016229"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>إعداد Rights Management Azure للإصدار السابق من تشفير الرسائل

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يصف هذا الموضوع الخطوات التي تحتاج إلى اتباعها لتنشيط Azure Rights Management (RMS) ثم إعداده، وهو جزء من Azure حماية البيانات، لاستخدامه مع الإصدار السابق من تشفير الرسائل Office 365 (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>تنطبق هذه المقالة فقط على الإصدار السابق من OME

إذا لم تكن قد نقلت مؤسستك بعد إلى Microsoft Purview Message Encryption، ولكنك قمت بالفعل بنشر OME، فإن المعلومات الواردة في هذه المقالة تنطبق على مؤسستك. توصي Microsoft بوضع خطة للانتقال إلى Microsoft Purview Message Encryption بمجرد أن يكون ذلك معقولا لمؤسستك. للحصول على الإرشادات، راجع [إعداد تشفير رسائل "Microsoft Purview](set-up-new-message-encryption-capabilities.md)". إذا كنت تريد معرفة المزيد حول كيفية عمل القدرات الجديدة أولا، فراجع [تشفير الرسائل](ome.md). تشير بقية هذه المقالة إلى سلوك OME قبل إصدار تشفير الرسائل من Microsoft Purview.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>المتطلبات الأساسية لاستخدام الإصدار السابق من تشفير الرسائل Office 365
<a name="warmprereqs"> </a>

يعتمد Office 365 تشفير الرسائل (OME)، بما في ذلك IRM، على Rights Management Azure (Azure RMS). Azure RMS هي تقنية الحماية المستخدمة من قبل Azure حماية البيانات. لاستخدام OME، يجب أن تتضمن مؤسستك اشتراكا Exchange Online أو Exchange Online Protection يتضمن بدوره اشتراك Azure Rights Management.

- إذا لم تكن متأكدا مما يتضمنه اشتراكك، فراجع أوصاف الخدمة Exchange Online [لنهج الرسالة والاسترداد والتوافق](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- إذا كان لديك Azure Rights Management ولكنه لم يتم إعداده Exchange Online أو Exchange Online Protection، تشرح هذه المقالة كيفية تنشيط azure Rights Management ثم تصف أفضل طريقة لإعداد OME للعمل مع Azure Rights Management.

- إذا قمت بالفعل بإعداد OME للعمل مع Azure Rights Management Exchange Online أو Exchange Online Protection، اعتمادا على كيفية إعداده، فقد تكون جاهزا لبدء استخدام OME وإمكانياته الجديدة على الفور. تشرح هذه المقالة كيفية تحديد ما إذا كنت قد قمت بإعداد OME بشكل صحيح، وما يجب فعله إذا كنت بحاجة إلى تغيير الإعداد، وماذا يحدث إذا اخترت عدم تغيير الإعداد. على سبيل المثال، لاستخدام القدرات الجديدة، يجب استخدام Azure RMS مع OME. لا يمكنك استخدام القدرات الجديدة مع Active Directory محلي RMS.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>تنشيط azure Rights Management للإصدار السابق من OME في Office 365

تحتاج إلى تنشيط Azure Rights Management بحيث يمكن للمستخدمين في مؤسستك تطبيق حماية المعلومات على الرسائل التي يرسلونها، وفتح الرسائل والملفات التي تمت حمايتها بواسطة خدمة Rights Management Azure. للحصول على [الإرشادات، راجع تنشيط Azure Rights Management](/azure/information-protection/activate-service). بعد الانتهاء من التنشيط، ارجع إلى هنا وتابع المهام الواردة في هذه المقالة.

## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>إعداد الإصدار السابق من OME لاستخدام Azure RMS عن طريق استيراد مجالات النشر الموثوق بها (TPDs)

TPD هو ملف XML يحتوي على معلومات حول إعدادات إدارة حقوق مؤسستك. على سبيل المثال، يحتوي TPD على معلومات حول شهادة الخادم المجمع (SLC) المستخدمة لتوقيع الشهادات والتراخيص وتشفيرها، وعناوين URL المستخدمة للترخيص والنشر، وما إلى ذلك. يمكنك استيراد TPD إلى مؤسستك باستخدام PowerShell.

> [!IMPORTANT]
> في السابق، يمكنك اختيار استيراد TPDs من خدمة Rights Management Active Directory (AD RMS) إلى مؤسستك. ومع ذلك، فإن القيام بذلك سيمنعك من استخدام تشفير الرسائل من Microsoft Purview ولا يوصى به. إذا تم تكوين مؤسستك حاليا بهذه الطريقة، توصي Microsoft بإنشاء خطة للرحل من Active Directory محلي RMS إلى Azure حماية البيانات المستندة إلى السحابة. لمزيد من المعلومات، راجع [الترحيل من AD RMS إلى Azure حماية البيانات](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). لن تتمكن من استخدام تشفير رسائل Microsoft Purview حتى تنتهي من الترحيل إلى Azure حماية البيانات.

**لاستيراد TPDs من Azure RMS**:

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. اختر عنوان URL لمشاركة المفاتيح الذي يتوافق مع الموقع الجغرافي لمؤسستك:

   |موقع|URL موقع مشاركة المفاتيح|
   |---|---|
   |أمريكا الشمالية|<https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc>|
   |الاتحاد الأوروبي|<https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc>|
   |اسيا|<https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc>|
   |أمريكا الجنوبية|<https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Office 365 للحكومة (سحابة القطاع الحكومي)  <br/> موقع مشاركة مفاتيح RMS هذا محجوز للعملاء الذين اشتروا Office 365 ل SKU الحكومية.|<https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc>|

3. تكوين موقع مشاركة المفتاح عن طريق تشغيل [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet كما يلي:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```

   على سبيل المثال، لتكوين موقع المشاركة الرئيسية إذا كانت مؤسستك موجودة في أمريكا الشمالية:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. قم بتشغيل [أمر cmdlet Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) باستخدام مفتاح التبديل -RMSOnline لاستيراد TPD من Azure Rights Management:

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   حيث  *TPDName*  هو الاسم الذي تريد استخدامه ل TPD. على سبيل المثال، "Contoso North American TPD".

5. للتحقق من أنك قمت بتكوين مؤسستك بنجاح لاستخدام خدمة azure Rights Management، قم بتشغيل [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) cmdlet باستخدام مفتاح التبديل -RMSOnline كما يلي:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   من بين أمور أخرى، يتحقق أمر cmdlet هذا من الاتصال بخدمة Azure Rights Management، وينزل TPD، ويتحقق من صلاحيته.

6. قم بتشغيل [set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet كما يلي لتعطيل قوالب azure Rights Management من أن تكون متوفرة في Outlook على ويب Outlook:

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. قم بتشغيل [set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet كما يلي لتمكين Rights Management Azure لمؤسسة البريد الإلكتروني المستندة إلى السحابة وتكوينه لاستخدام azure Rights Management لتشفير الرسائل Office 365:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. للتحقق من أنك قمت باستيراد TPD بنجاح وتمكين Rights Management Azure، استخدم Test-IRMConfiguration cmdlet لاختبار وظيفة azure Rights Management. للحصول على التفاصيل، راجع "المثال 1" في [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>لقد أعددت الإصدار السابق من OME مع Active Directory Rights Management وليس حماية البيانات Azure، ماذا أفعل؟
<a name="importTPDs"> </a>

يمكنك الاستمرار في استخدام قواعد تدفق بريد تشفير الرسائل Office 365 الموجودة مع Rights Management Active Directory، ولكن لا يمكنك تكوين تشفير رسائل Microsoft Purview أو استخدامه. بدلا من ذلك، تحتاج إلى الترحيل إلى Azure حماية البيانات. للحصول على معلومات حول الترحيل وما يعنيه ذلك لمؤسستك، راجع [الترحيل من AD RMS إلى Azure حماية البيانات](/information-protection/deploy-use/prepare-environment-adrms).

## <a name="next-steps"></a>الخطوات التالية
<a name="importTPDs"> </a>

بمجرد الانتهاء من إعداد Azure Rights Management، إذا كنت تريد تمكين تشفير رسالة "Microsoft Purview"، فراجع [إعداد تشفير رسائل "Microsoft Purview](./set-up-new-message-encryption-capabilities.md)".

بعد إعداد مؤسستك لاستخدام تشفير الرسائل من Microsoft Purview، تصبح جاهزا [لتعريف قواعد تدفق البريد](define-mail-flow-rules-to-encrypt-email.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
<a name="importTPDs"> </a>

[التشفير في Office 365](encryption.md)

[تفاصيل المرجع التقني حول التشفير في Office 365](technical-reference-details-about-encryption.md)

[ما هو Azure Rights Management؟](/information-protection/understand-explore/what-is-azure-rms)
