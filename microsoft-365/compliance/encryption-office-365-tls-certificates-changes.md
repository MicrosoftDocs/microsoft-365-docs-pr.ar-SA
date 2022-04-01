---
title: Office شهادة TLS
description: كيفية التحضير للتغييرات القادمة على Office TLS.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: 075fb8f4c27401a4622f4ce639c897f2e98bb3e9
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/12/2022
ms.locfileid: "63580026"
---
# <a name="office-tls-certificate-changes"></a>Office شهادة TLS

Microsoft 365 تحديث خدمات تعمل على تشغيل المراسلة والاجتماعات والهاتف والصوت والفيديو لاستخدام شهادات TLS من مجموعة مختلفة من "المرجع المشهادات الجذر" (CAs). يتم حاليا تغيير هذا بسبب انتهاء صلاحية الم CA الجذر الحالي في مايو 2025.

تتضمن المنتجات المتأثرة ما يلي:
- Microsoft Teams
- Skype
- Skype for Business Online
- Microsoft Dynamics 365
- GroupMe
- Kaizala
- Azure Communication Services

تتضمن نقاط النهاية المتأثرة (ولكن لا تقتصر على):
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

بالإضافة إلى ذلك، Teams نقاط النهاية Skype for Business عبر الإنترنت في مثيلات السحابة الوطنية ل Microsoft 365 الخاصة ب "حكومة الولايات المتحدة" إجراء التغيير نفسه، مما يؤثر على نقاط النهاية مثل:
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

لن يؤثر هذا التغيير على الشهادات أو المجالات أو الخدمات المستخدمة في مثيلات السحابة الوطنية في الصين أو ألمانيا Microsoft 365.

تم توفير كل معلومات الشهادة الواردة في هذه المقالة [في Microsoft 365 التشفير](./encryption-office-365-certificate-chains.md) في موعد لا يزيد عن أكتوبر 2020.

## <a name="when-will-this-change-happen"></a>متى سيحدث هذا التغيير؟

بدأت الخدمات في الانتقال إلى "CAs الجذر" الجديد في يناير 2022 وستستمر حتى أكتوبر 2022.

## <a name="what-is-changing"></a>ما الذي يتغير؟

اليوم، يتم تسلسل معظم شهادات TLS التي تستخدمها Microsoft 365 الخدمات حتى المستعرض الجذر التالي:

| الاسم الشائع ل CA | الطباعة المصغرة (SHA1) |
|--|--|
| [جذر Baltimore CyberTrust](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

مع إحدى وسيطات CAs التالية:

| الاسم الشائع ل CA | الطباعة المصغرة (SHA1) |
|--|--|
| [Microsoft RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [Microsoft RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

ستصل شهادات TLS الجديدة التي تستخدمها Microsoft 365 الخدمات الآن إلى إحدى الشهادات الجذر التالية:

| الاسم الشائع ل CA | الطباعة المصغرة (SHA1) |
|--|--|
| [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [هيئة الشهادات الجذر ل Microsoft RSA 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [مرجع مشهادات الجذر ل Microsoft ECC 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

مع إحدى وسيطات CAs التالية:

| الاسم الشائع ل CA | الطباعة المصغرة (SHA1) |
|--|--|
| [إصدار CA 01 من Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [إصدار CA 02 من Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [إصدار CA 05 ل Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [إصدار CA 06 ل Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

على سبيل المثال، هذه شهادة صالحة مع إحدى سلاسل الشهادات الجديدة:

![Teams شهادة TLS](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>هل سيؤثر هذا التغيير علي؟

إن جذر CA "DigiCert Global Root G2" موثوق به على نطاق واسع بواسطة أنظمة التشغيل بما في ذلك Windows و macOS وAndroid وiOS ومن خلال مستعرضات مثل Microsoft Edge وChrome وSandr safari وFirefox. نتوقع أن **معظم Microsoft 365 العملاء لن يؤثروا**. 

ومع ذلك **، قد يكون التطبيق الخاص بك متأثيا إذا** كان يحدد بشكل صريح قائمة ب CAs المقبولة. تعرف هذه الممارسة باسم "تثبيت الشهادة". سيتلقى العملاء الذين ليس لديهم "CAs الجذر" الجديد في قائمة "CAs" المقبولة أخطاء التحقق من صحة الشهادة، والتي قد تؤثر على توفر التطبيق أو وظيفته.

فيما يلي بعض الطرق للكشف عما إذا كان التطبيق قد تم التأثير عليه:

- ابحث في التعليمات البرمجية المصدر عن الطباعة المصغرة أو الاسم الشائع أو الخصائص الأخرى لأي من "أسماء CAs الوسيطة" الموجودة [هنا](https://www.microsoft.com/pki/mscorp/cps/default.htm). إذا كان هناك تطابق، سيتأثر التطبيق الخاص بك. لحل هذه المشكلة، قم بتحديث التعليمات البرمجية المصدر لإضافة خصائص CAs الجديدة. كأفضل ممارسة، تأكد من أنه يمكن إضافة CAs أو تحريرها في إشعار قصير. تتطلب اللوائح التنظيمية الصناعية استبدال شهادات الماوس في غضون سبعة أيام في بعض الحالات، لذا يجب أن تتفاعل التطبيقات التي تنفذ تثبيت الشهادات مع هذه التغييرات بسرعة.

- يعرض .NET `System.Net.ServicePointManager.ServerCertificateValidationCallback` `System.Net.HttpWebRequest.ServerCertificateValidationCallback` دالتي الاستدعاء و، التي تسمح للمطورين باستخدام المنطق المخصص لتحديد ما إذا كانت الشهادات صالحة بدلا من الاعتماد على مخزن Windows القياسي. يمكن للمطور إضافة منطق يتحقق من وجود اسم شائع معين أو طباعة مصغرة معينة أو يسمح فقط ب CA الجذر المحدد مثل "جذر Baltimore CyberTrust". إذا كان تطبيقك يستخدم دالات رد الاتصال هذه، يجب أن تتأكد من قبوله لكل من CAs الجذر القديم والوسيطة الوسيطة.

- قد تستخدم التطبيقات الأصلية `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`، مما يسمح للتطبيقات الأصلية بتنفيذ منطق التحقق من صحة الشهادة المخصص. استخدام هذا الإعلام نادر ويتطلب كمية كبيرة من التعليمات البرمجية المخصصة لتنفيذها. كما هو الحال أعلاه، تأكد من قبول التطبيق لكل من CAs الجذر القديم والوسيطة المتوسطة. 

- إذا كنت تستخدم تطبيقا يتكامل مع واجهات برمجة تطبيقات Microsoft Teams أو Skype أو Skype for Business Online أو Microsoft Dynamics ولم يكن لديك أي تأكد مما إذا كان يستخدم تثبيت الشهادات، فتحقق من الأمر مع مورد التطبيق.

- قد تتطلب أنظمة التشغيل واللغات المختلفة التي تتواصل مع خدمات Azure خطوات أخرى لإنشاء سلاسل الشهادات الجديدة والتحقق من صحتها بشكل صحيح:
   - **Linux**: تتطلب العديد من التوزيعات إضافة CAs إلى `/etc/ssl/certs`. للحصول على إرشادات معينة، راجع وثائق التوزيع.
   - **Java**: تأكد من أن مخزن مفاتيح Java يحتوي على CAs المذكورة أعلاه.
   - **Windows** في بيئات غير منقطعة الاتصال: ستحتاج الأنظمة التي تعمل في بيئات غير منفصلة إلى إضافة "CAs الجذر" الجديدة إلى متجرها وإضافة "CAs`Trusted Root Certification Authorities`" الوسيطة الجديدة إلى متجرها`Intermediate Certification Authorities`.
   - **Android**: تحقق من الوثائق الخاصة بجهازك والإصدار من Android.
   - **IoT أو** الأجهزة المضمنة: غالبا ما تشحن الأجهزة المضمنة مثل علو مجموعة التلفزيون مجموعة محدودة من شهادات المرجع الجذر ولا تملك أي طريقة سهلة لتحديث مخزن الشهادات. إذا كتبت تعليمات برمجية أو تدير عمليات نشر أجهزة مخصصة مضمنة أو أجهزة IoT، فتأكد من أن الأجهزة تثق بأجهزة CAs الجذر الجديدة. قد تحتاج إلى الاتصال بالشركة المصنعة للجهاز.

- إذا كانت لديك بيئة تسمح فيها قواعد جدار الحماية بالمكالمات الصادرة بنقاط نهاية معينة فقط، فاسمح ب URL لقائمة إلغاء الشهادة التالية (CRL) أو عناوين URL لبروتوكول حالة الشهادة عبر الإنترنت (OCSP):
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- إذا كنت متأثيا بهذا التغيير، فقد ترى رسائل خطأ تعتمد على نوع البيئة التي تقوم بتشغيلها والسيناريوهات التي تم التأثير عليك بها. تحقق Windows سجلات أحداث التطبيق وسجلات أحداث CAPI2 وسجلات التطبيقات المخصصة للرسائل التي تبدو مثل:
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>متى يمكنني إيقاف معلومات CA القديمة؟

لن يتم إبطال شهادات الم CA الجذر و CA الوسيطة و أوراق العمل الحالية. ستكون الأسماء الشائعة ل CA و/أو الصور المصغرة الحالية مطلوبة خلال شهر أكتوبر 2023 على الأقل استنادا إلى مدة عمر الشهادات الموجودة.
