---
title: Office 365 السريع لشبكة تسليم المحتوى (CDN)
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/13/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Office 365 السريع لشبكة تسليم المحتوى (CDN)
ms.openlocfilehash: b0684fdfd8583ae6780cb23d47dc697582ae133b
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/31/2022
ms.locfileid: "63568808"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a>Office 365 السريع لشبكة تسليم المحتوى (CDN)

يمكنك استخدام شبكة تسليم Office 365 **(CDN)** المضمنة لاستضافة الأصول الثابتة (الصور و JavaScript و أوراق الأنماط وملفات WOFF) لتوفير أداء أفضل لصفحات SharePoint Online. تحسن Office 365 CDN الأداء عن طريق التخزين المؤقت للأصول الثابتة بالقرب من المستعرضات التي تطلبها، مما يساعد على تسريع التنزيلات وتقليل زمن زمن الوصول. كما تستخدم Office 365 CDN بروتوكول HTTP/2 لتحسين الضغط وHTTP. يتم Office 365 خدمة CDN كجزء من اشتراكك في SharePoint Online.

للحصول على إرشادات معلومات أكثر تفصيلا، راجع استخدام [Office 365 تسليم المحتوى (CDN) مع SharePoint Online](use-microsoft-365-cdn-with-spo.md).

>[!NOTE]
>تتوفر Office 365 CDN فقط للمستأجرين في سحابة الإنتاج (على مستوى العالم). لا يدعم المستأجرون في سحابة الحكومة الأمريكية والصين وألمانيا حاليا Office 365 CDN.

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a>استخدام أداة تشخيص الصفحة SharePoint لتحديد العناصر غير الموجودة في CDN

يمكنك استخدام ملحق مستعرض أدوات SharePoint "تشخيص الصفحات" لقائمة الأصول بسهولة في SharePoint عبر الإنترنت التي يمكن إضافتها إلى أصل CDN.

أداة **تشخيص الصفحة SharePoint** هي ملحق مستعرض لمستعرضات Microsoft Edge (<https://www.microsoft.com/edge>) وChrome الجديدة التي تحلل كل من SharePoint Online الحديث وصفحات موقع النشر الكلاسيكي. توفر الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة من معايير الأداء. لتثبيت أداة تشخيص الصفحة SharePoint للتعرف عليها، تفضل بزيارة استخدام أداة تشخيص الصفحة [SharePoint Online](./page-diagnostics-for-spo.md).

عند تشغيل أداة تشخيص الصفحة ل SharePoint على صفحة SharePoint عبر الإنترنت، يمكنك النقر فوق علامة التبويب اختبارات تشخيص لرؤية قائمة بالأصول التي لا  تستضيفها شبكة CDN. سيتم إدراج هذه الأصول ضمن العنوان التحقق من شبكة تسليم المحتوى **(CDN)** كما هو موضح في لقطة الشاشة أدناه.

![تشخيص الصفحة.](../media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
>تعمل الأداة "تشخيص الصفحة" فقط SharePoint Online، ولا يمكن استخدامها على صفحة SharePoint ويب.

## <a name="cdn-overview"></a>نظرة عامة على CDN

تم Office 365 CDN لتحسين الأداء للمستخدمين من خلال توزيع العناصر التي يتم الوصول إليها بشكل متكرر مثل الصور وملفات javascript عبر شبكة عالمية عالية السرعة، وتقليل وقت تحميل الصفحة وتوفير الوصول إلى العناصر المستضافة في أقرب وقت ممكن للمستخدم. تقوم CDN بإحضار الأصول من موقع _يسمى الأصل._ يمكن أن يكون الأصل SharePoint موقع ويب أو مكتبة مستندات أو مجلد يمكن الوصول إليه بواسطة عنوان URL.

يتم Office 365 CDN إلى نوعين أساسيين:

- تم **تصميم CDN** عام ليستخدم للصور JS (JavaScript) و CSS (StyleSheets) و Web Font File (WOFF و WOFF2) والصور غير الخاصة مثل شعارات الشركة.
- **تم تصميم CDN** خاص ليستخدم للصور (PNG و JPG و JPEG وغيرها).

يمكنك اختيار الحصول على أصول عامة أو خاصة لمنظمتك. ستختار معظم المؤسسات تنفيذ تركيبة من الاثنين. يوفر كل من الخيارين العام والخاص نفس المكاسب في الأداء، ولكن لكل منهما سمات ومزايا فريدة. لمزيد من المعلومات حول أصول CDN العامة والخاصة، راجع اختيار ما إذا كان يجب أن يكون كل أصل [عام أو خاص](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a>كيفية تمكين CDN العامة والخاصة باستخدام التكوين الافتراضي
قبل إجراء تغييرات على إعدادات CDN للمستأجر، يجب التحقق من أنها تفي بالامتثال ونهج الأمان والخصوصية في مؤسستك.

للحصول على إعدادات تكوين أكثر تفصيلا، أو إذا قمت بتمكين CDN بالفعل وتريد إضافة مواقع إضافية (أصول)، فالرجاء الاطلاع على المقطع إعداد شبكة CDN Office 365 وتكوينها [باستخدام SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)

الاتصال إلى المستأجر باستخدام SharePoint Online Management Shell:

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

لتمكين مؤسستك من استخدام الأصلين العام والخاص مع التكوين الافتراضي، اكتب الأمر التالي:

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

يجب أن يبدو إخراج هذه cmdlets كما يلي:

![إخراج Set-SPOTenantCdnEnabled.](../media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a>راجع أيضًا

[استخدام أداة تشخيص الصفحة SharePoint Online](./page-diagnostics-for-spo.md)

[استخدام Office 365 تسليم المحتوى (CDN) مع SharePoint Online](use-microsoft-365-cdn-with-spo.md)

[شبكات تسليم المحتوى](./content-delivery-networks.md)

[تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md)

[SharePoint سلسلة أداء - Office 365 فيديو CDN](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
