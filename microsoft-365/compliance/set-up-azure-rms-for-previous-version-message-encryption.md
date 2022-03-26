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
description: يعتمد الإصدار السابق من تشفير الرسائل من Office 365 Microsoft Azure Rights Management (المعروف سابقا باسم Windows Azure Active Directory Rights Management).
ms.openlocfilehash: c94497069d929dd3819e3ced915c8e778e983c10
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566324"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>إعداد Azure Rights Management للإصدار السابق من تشفير الرسائل

يصف هذا الموضوع الخطوات التي تحتاج إلى اتباعها لتنشيط Azure Rights Management (RMS) ثم إعداده، وهو جزء من Azure Information Protection، لاستخدامه مع الإصدار السابق من تشفير الرسائل من Office 365 (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>تنطبق هذه المقالة فقط على الإصدار السابق من OME

إذا لم تكن قد نقلت مؤسستك بعد إلى قدرات OME الجديدة، ولكنك نشرت OME بالفعل، فإن المعلومات الواردة في هذه المقالة تنطبق على مؤسستك. توصي Microsoft بأن تقوم بإجراء خطة للانتقال إلى قدرات OME الجديدة بمجرد أن تكون معقولة لمنظمتك. للحصول على الإرشادات، راجع [إعداد قدرات تشفير الرسائل من Office 365 الجديدة](set-up-new-message-encryption-capabilities.md). إذا كنت تريد معرفة المزيد حول كيفية عمل القدرات الجديدة أولا، [فشاهد تشفير الرسائل من Office 365](ome.md). تشير باقي هذه المقالة إلى سلوك OME قبل إصدار قدرات OME الجديدة.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>المتطلبات الأساسية لاستخدام الإصدار السابق من تشفير الرسائل من Office 365
<a name="warmprereqs"> </a>

تشفير الرسائل من Office 365 (OME)، بما في ذلك IRM، على Azure Rights Management (Azure RMS). Azure RMS هي تقنية الحماية المستخدمة بواسطة Azure Information Protection. لاستخدام OME، يجب أن تتضمن مؤسستك اشتراكا Exchange Online أو Exchange Online Protection يتضمن بدوره اشتراك Azure Rights Management.
  
- إذا لم تكن متأكدا مما يتضمنه اشتراكك، فشاهد Exchange Online أوصاف خدمة نهج الرسالة واستردادها [وتوافقها](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- إذا كان لديك Azure Rights Management ولكن لم يتم إعدادها ل Exchange Online أو Exchange Online Protection، تشرح هذه المقالة كيفية تنشيط Azure Rights Management ثم تصف أفضل طريقة لإعداد OME للعمل مع Azure Rights Management.

- إذا قمت بالفعل بإعداد OME للعمل مع Azure Rights Management ل Exchange Online أو Exchange Online Protection، استنادا إلى كيفية إعداده، فقد تكون جاهزا لبدء استخدام OME وإمكاناته الجديدة على الفور. تشرح هذه المقالة كيفية تحديد ما إذا كنت قد قمت بإعداد OME بشكل صحيح، وما يجب فعله إذا كنت بحاجة إلى تغيير الإعداد، وما يحدث إذا اخترت عدم تغيير الإعداد. على سبيل المثال، لاستخدام الإمكانات الجديدة، يجب استخدام Azure RMS مع OME. لا يمكنك استخدام الإمكانات الجديدة مع Active Directory RMS المحلية.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>تنشيط Azure Rights Management للإصدار السابق من OME في Office 365

يجب تنشيط Azure Rights Management بحيث يمكن للمستخدمين في مؤسستك تطبيق حماية المعلومات على الرسائل التي يرسلونها وفتح الرسائل والملفات المحمية بواسطة خدمة Azure Rights Management. للحصول على الإرشادات، راجع [تنشيط Azure Rights Management](/azure/information-protection/activate-service). بعد الانتهاء من التنشيط، ارجع إلى هنا وتابع المهام في هذه المقالة.
  
## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>إعداد الإصدار السابق من OME لاستخدام Azure RMS عن طريق استيراد مجالات النشر الموثوق بها (TPDs)

إن TPD هو ملف XML يحتوي على معلومات حول إعدادات إدارة الحقوق في مؤسستك. على سبيل المثال، تحتوي TPD على معلومات حول شهادة ترخيص الخادم (SLC) المستخدمة لتوقيع الشهادات والتراخيص وتشفيرها، وعنايين URL المستخدمة للترخيص والنشر، وما إلى ذلك. يمكنك استيراد TPD إلى مؤسستك باستخدام Windows PowerShell.
  
> [!IMPORTANT]
> في السابق، يمكنك اختيار استيراد TPDs من خدمة إدارة حقوق Active Directory (AD RMS) إلى مؤسستك. ومع ذلك، فإن القيام بذلك سيمنعك من استخدام قدرات OME الجديدة ولا يوصى به. إذا تم تكوين مؤسستك حاليا بهذه الطريقة، فإن Microsoft توصي بإنشاء خطة للترحيل من Active Directory RMS في الموقع إلى Azure Information Protection المستند إلى السحابة. للحصول على مزيد من المعلومات، راجع عملية "إعادة استلام البيانات" من [AD RMS إلى Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). لن تتمكن من استخدام إمكانات OME الجديدة إلا بعد إكمال عملية الترحيل إلى Azure Information Protection.
  
 **لاستيراد TPDs من Azure RMS**
  
1. [الاتصال Exchange Online استخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell).

2. اختر عنوان URL لمشاركة المفاتيح الذي يتطابق مع الموقع الجغرافي لمنظمتك:

|**الموقع**|**URL موقع المشاركة الرئيسية**|
|:-----|:-----|
|أمريكا الشمالية  <br/> |https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|الاتحاد الأوروبي  <br/> |https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|آسيا  <br/> |https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|أمريكا الجنوبية  <br/> |https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Office 365 ل Government (سحابة القطاع الحكومي)  <br/> موقع مشاركة مفاتيح RMS هذا محجوز للعملاء الذين اشتروا Office 365 SKUs.  <br/> |https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
  
3. قم بتكوين موقع مشاركة المفاتيح عن طريق تشغيل [cmdlet Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) كما يلي: 

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```
  
   على سبيل المثال، لتكوين موقع المشاركة الرئيسي إذا كانت مؤسستك موجودة في أمريكا الشمالية:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. قم بتشغيل [cmdlet Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) باستخدام مفتاح التبديل -RMSOnline لاستيراد TPD من Azure Rights Management: 

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   حيث  *TPDName*  هو الاسم الذي تريد استخدامه ل TPD. على سبيل المثال، "Contoso North American TPD". 

5. للتحقق من أنك قمت بتكوين مؤسستك بنجاح لاستخدام خدمة Azure Rights Management، قم بتشغيل [Cmdlet Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) مع مفتاح التبديل -RMSOnline كما يلي:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   من بين أشياء أخرى، يتحقق cmdlet هذا من الاتصال مع خدمة Azure Rights Management، ويزيل TPD، ويتحقق من صحته.

6. قم بتشغيل [cmdlet Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) كما يلي لتعطيل قوالب Azure Rights Management من أن تكون متوفرة في Outlook على ويب Outlook: 

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. قم [بتشغيل الأمر cmdlet Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) كما يلي لتمكين Azure Rights Management لمنظمه البريد الإلكتروني المستندة إلى السحابة وتكوينه لاستخدام Azure Rights Management تشفير الرسائل من Office 365:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. للتحقق من أنك قمت باستيراد TPD وتمكين Azure Rights Management بنجاح، استخدم الأمر cmdlet Test-IRMConfiguration لاختبار وظيفة Azure Rights Management. للحصول على التفاصيل، راجع "المثال 1" في [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>لقد تم إعداد الإصدار السابق من OME باستخدام إدارة حقوق Active Directory وليس Azure Information Protection، ماذا أفعل؟
<a name="importTPDs"> </a>

يمكنك الاستمرار في استخدام قواعد تدفق البريد تشفير الرسائل من Office 365 مع إدارة حقوق Active Directory، ولكن لا يمكنك تكوين إمكانات OME الجديدة أو استخدامها. بدلا من ذلك، تحتاج إلى الترحيل إلى Azure Information Protection. للحصول على معلومات حول الترحيل وما يعنيه هذا الأمر لمنظمتك، راجع الترحيل من [AD RMS إلى Azure Information Protection](/information-protection/deploy-use/prepare-environment-adrms).
  
## <a name="next-steps"></a>الخطوات التالية
<a name="importTPDs"> </a>

بمجرد الانتهاء من إعداد Azure Rights Management، إذا كنت تريد تمكين قدرات OME الجديدة، فا راجع إعداد قدرات تشفير الرسائل من Office 365 الجديدة المضمنة في أعلى [Azure Information Protection.](./set-up-new-message-encryption-capabilities.md)
  
بعد إعداد مؤسستك لاستخدام قدرات OME الجديدة، تكون جاهزا لتعريف قواعد تدفق البريد لحماية رسائل البريد الإلكتروني بقدرات [OME الجديدة](define-mail-flow-rules-to-encrypt-email.md).
  
## <a name="related-topics"></a>المواضيع ذات الصلة
<a name="importTPDs"> </a>

[التشفير في Office 365](encryption.md)
  
[تفاصيل المراجع التقنية حول التشفير في Office 365](technical-reference-details-about-encryption.md)
  
[ما هي Azure Rights Management؟](/information-protection/understand-explore/what-is-azure-rms)