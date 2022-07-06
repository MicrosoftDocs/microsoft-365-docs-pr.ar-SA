---
title: إعداد Azure Rights Management للإصدار السابق من تشفير الرسائل
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
description: يعتمد الإصدار السابق من Office 365 Message Encryption على Microsoft Azure Rights Management (المعروف سابقا باسم Windows Azure Active Directory Rights Management).
ms.openlocfilehash: 386056c282ea5f4ad996cc7ae7c50926436fe720
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641351"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>إعداد Azure Rights Management للإصدار السابق من تشفير الرسائل

يصف هذا الموضوع الخطوات التي تحتاج إلى اتباعها لتنشيط إدارة حقوق Azure (RMS) ثم إعدادها، وهي جزء من azure حماية البيانات، لاستخدامها مع الإصدار السابق من تشفير الرسائل Office 365 (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>تنطبق هذه المقالة فقط على الإصدار السابق من OME

إذا لم تقم بعد بنقل مؤسستك إلى تشفير الرسائل في Microsoft Purview، ولكنك قمت بالفعل بنشر OME، فإن المعلومات الواردة في هذه المقالة تنطبق على مؤسستك. توصي Microsoft بوضع خطة للانتقال إلى تشفير الرسائل في Microsoft Purview بمجرد أن يكون ذلك معقولا لمؤسستك. للحصول على الإرشادات، راجع [إعداد تشفير الرسائل في Microsoft Purview](set-up-new-message-encryption-capabilities.md). إذا كنت تريد معرفة المزيد حول كيفية عمل القدرات الجديدة أولا، فراجع [تشفير الرسائل](ome.md). يشير باقي هذه المقالة إلى سلوك OME قبل إصدار تشفير الرسائل في Microsoft Purview.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>المتطلبات الأساسية لاستخدام الإصدار السابق من تشفير الرسائل Office 365
<a name="warmprereqs"> </a>

يعتمد Office 365 تشفير الرسائل (OME)، بما في ذلك IRM، على Azure Rights Management (Azure RMS). Azure RMS هي تقنية الحماية المستخدمة من قبل Azure حماية البيانات. لاستخدام OME، يجب أن تتضمن مؤسستك اشتراكا Exchange Online أو Exchange Online Protection يتضمن بدوره اشتراك Azure Rights Management.

- إذا لم تكن متأكدا مما يتضمنه اشتراكك، فراجع أوصاف الخدمة Exchange Online [لنهج الرسالة والاسترداد والتوافق](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- إذا كان لديك Azure Rights Management ولكنها لم يتم إعدادها Exchange Online أو Exchange Online Protection، تشرح هذه المقالة كيفية تنشيط Azure Rights Management ثم تصف أفضل طريقة لإعداد OME للعمل مع Azure Rights Management.

- إذا قمت بالفعل بإعداد OME للعمل مع Azure Rights Management Exchange Online أو Exchange Online Protection، اعتمادا على كيفية إعداده، فقد تكون جاهزا لبدء استخدام OME وإمكانياته الجديدة على الفور. تشرح هذه المقالة كيفية تحديد ما إذا كنت قد قمت بإعداد OME بشكل صحيح، وما يجب فعله إذا كنت بحاجة إلى تغيير الإعداد، وماذا يحدث إذا اخترت عدم تغيير الإعداد. على سبيل المثال، لاستخدام القدرات الجديدة، يجب استخدام Azure RMS مع OME. لا يمكنك استخدام القدرات الجديدة مع Active Directory محلي RMS.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>تنشيط Azure Rights Management للإصدار السابق من OME في Office 365

تحتاج إلى تنشيط Azure Rights Management بحيث يمكن للمستخدمين في مؤسستك تطبيق حماية المعلومات على الرسائل التي يرسلونها، وفتح الرسائل والملفات المحمية بواسطة خدمة Azure Rights Management. للحصول على [الإرشادات، راجع تنشيط Azure Rights Management](/azure/information-protection/activate-service). بعد الانتهاء من التنشيط، ارجع إلى هنا وتابع المهام الواردة في هذه المقالة.

## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>إعداد الإصدار السابق من OME لاستخدام Azure RMS عن طريق استيراد مجالات النشر الموثوق بها (TPDs)

TPD هو ملف XML يحتوي على معلومات حول إعدادات إدارة حقوق مؤسستك. على سبيل المثال، يحتوي TPD على معلومات حول شهادة الخادم المجمع (SLC) المستخدمة لتوقيع الشهادات والتراخيص وتشفيرها، وعناوين URL المستخدمة للترخيص والنشر، وما إلى ذلك. يمكنك استيراد TPD إلى مؤسستك باستخدام PowerShell.

> [!IMPORTANT]
> في السابق، يمكنك اختيار استيراد TPDs من خدمة Active Directory Rights Management (AD RMS) إلى مؤسستك. ومع ذلك، فإن القيام بذلك سيمنعك من استخدام تشفير الرسائل في Microsoft Purview ولا يوصى به. إذا تم تكوين مؤسستك حاليا بهذه الطريقة، توصي Microsoft بإنشاء خطة للرحل من Active Directory محلي RMS إلى Azure حماية البيانات المستندة إلى السحابة. لمزيد من المعلومات، راجع [الترحيل من AD RMS إلى Azure حماية البيانات](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). لن تتمكن من استخدام تشفير الرسائل في Microsoft Purview حتى تنتهي من الترحيل إلى Azure حماية البيانات.

**لاستيراد TPDs من Azure RMS**:

1. [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. اختر عنوان URL لمشاركة المفاتيح الذي يتوافق مع الموقع الجغرافي لمؤسستك:

   |موقع|URL موقع مشاركة المفاتيح|
   |---|---|
   |أمريكا الشمالية|<https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc>|
   |الاتحاد الأوروبي|<https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc>|
   |اسيا|<https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc>|
   |أمريكا الجنوبية|<https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Office 365 للحكومة (سحابة مجتمع الحكومة)  <br/> موقع مشاركة مفاتيح RMS هذا محجوز للعملاء الذين اشتروا Office 365 ل SKU الحكومية.|<https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc>|

3. تكوين موقع مشاركة المفتاح عن طريق تشغيل [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet كما يلي:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```

   على سبيل المثال، لتكوين موقع المشاركة الرئيسية إذا كانت مؤسستك موجودة في أمريكا الشمالية:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. قم بتشغيل [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) cmdlet باستخدام مفتاح التبديل -RMSOnline لاستيراد TPD من Azure Rights Management:

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   حيث  *TPDName*  هو الاسم الذي تريد استخدامه ل TPD. على سبيل المثال، "Contoso North American TPD".

5. للتحقق من تكوين مؤسستك بنجاح لاستخدام خدمة Azure Rights Management، قم بتشغيل [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) cmdlet باستخدام مفتاح التبديل -RMSOnline كما يلي:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   من بين أمور أخرى، يتحقق أمر cmdlet هذا من الاتصال بخدمة Azure Rights Management، وينزل TPD، ويتحقق من صلاحيته.

6. قم بتشغيل [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet كما يلي لتعطيل قوالب Azure Rights Management من أن تكون متوفرة في Outlook على ويب وOutlook:

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. قم بتشغيل [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) cmdlet كما يلي لتمكين إدارة حقوق Azure لمؤسسة البريد الإلكتروني المستندة إلى السحابة وتكوينها لاستخدام Azure Rights Management لتشفير الرسائل Office 365:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. للتحقق من أنك قمت باستيراد TPD بنجاح وتمكين إدارة حقوق Azure، استخدم Test-IRMConfiguration cmdlet لاختبار وظيفة Azure Rights Management. للحصول على التفاصيل، راجع "المثال 1" في [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>لقد أعددت الإصدار السابق من OME مع Active Directory Rights Management وليس Azure حماية البيانات، ماذا أفعل؟
<a name="importTPDs"> </a>

يمكنك الاستمرار في استخدام قواعد تدفق بريد تشفير الرسائل Office 365 الموجودة باستخدام Active Directory Rights Management، ولكن لا يمكنك تكوين تشفير الرسائل في Microsoft Purview أو استخدامها. بدلا من ذلك، تحتاج إلى الترحيل إلى Azure حماية البيانات. للحصول على معلومات حول الترحيل وما يعنيه ذلك لمؤسستك، راجع [الترحيل من AD RMS إلى Azure حماية البيانات](/information-protection/deploy-use/prepare-environment-adrms).

## <a name="next-steps"></a>الخطوات التالية
<a name="importTPDs"> </a>

بمجرد الانتهاء من إعداد Azure Rights Management، إذا كنت تريد تمكين تشفير الرسائل في Microsoft Purview، فراجع [إعداد تشفير الرسائل في Microsoft Purview](./set-up-new-message-encryption-capabilities.md).

بعد إعداد مؤسستك لاستخدام تشفير الرسائل في Microsoft Purview، تصبح جاهزا [لتعريف قواعد تدفق البريد](define-mail-flow-rules-to-encrypt-email.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
<a name="importTPDs"> </a>

[التشفير في Office 365](encryption.md)

[تفاصيل المرجع التقني حول التشفير في Office 365](technical-reference-details-about-encryption.md)

[ما هي إدارة حقوق Azure؟](/information-protection/understand-explore/what-is-azure-rms)
