---
title: تغييرات شهادة Office TLS
description: كيفية التحضير للتغييرات القادمة على شهادات Office TLS.
author: pshelton-skype
ms.author: pshelton
manager: toddbeckett
ms.topic: article
audience: Developer
ms.date: 3/7/2022
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.openlocfilehash: 65b0ffd5d605302dd62369471b65c1ac10aacd40
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641757"
---
# <a name="office-tls-certificate-changes"></a>تغييرات شهادة Office TLS

يقوم Microsoft 365 بتحديث خدمات تشغيل المراسلة والاجتماعات والهتفية والصوت والفيديو لاستخدام شهادات TLS من مجموعة مختلفة من المراجع المصدقة الجذرية (CAs). يتم إجراء هذا التغيير لأن المرجع المصدق الجذري الحالي ستنتهي صلاحيته في مايو 2025.

وتشمل المنتجات المتأثرة ما يلي:
- Microsoft Teams
- سكايب
- Skype for Business Online
- Microsoft Dynamics 365
- GroupMe
- Kaizala
- Azure Communication Services

تتضمن نقاط النهاية المتأثرة (على سبيل المثال لا الحصر):
- *.teams.microsoft.com
- *.skype.com
- *.skypeforbusiness.com
- *.groupme.com
- *.communication.azure.com
- *.operatorconnect.microsoft.com

بالإضافة إلى ذلك، ستقوم Teams ونقاط النهاية Skype for Business Online في مثيلات السحابة الوطنية لحكومة الولايات المتحدة من Microsoft 365 بإجراء نفس التغيير، مما يؤثر على نقاط النهاية مثل:
- *.gcc.teams.microsoft.com
- *.dod.teams.microsoft.us
- *.gov.teams.microsoft.us
- *.online.dod.skypeforbusiness.us
- *.online.gov.skypeforbusiness.us
- *.um-dod.office365.us
- *.um.office365.us

لن يؤثر هذا التغيير على الشهادات أو المجالات أو الخدمات المستخدمة في مثيلات السحابة الوطنية في الصين أو ألمانيا من Microsoft 365.

تم توفير كافة معلومات الشهادة في هذه المقالة مسبقا في [سلاسل تشفير Microsoft 365](./encryption-office-365-certificate-chains.md) في موعد لا يتجاوز أكتوبر 2020.

## <a name="when-will-this-change-happen"></a>متى سيحدث هذا التغيير؟

بدأت الخدمات في الانتقال إلى المراجع المصدقة الجذرية الجديدة في يناير 2022 وستستمر حتى أكتوبر 2022.

## <a name="what-is-changing"></a>ما الذي يتغير؟

اليوم، معظم شهادات TLS المستخدمة من قبل سلسلة خدمات Microsoft 365 تصل إلى المرجع المصدق الجذري التالي:

| الاسم الشائع للمرجع المصدق | بصمة الإبهام (SHA1) |
|--|--|
| [جذر CyberTrust في Baltimore](https://cacerts.digicert.com/BaltimoreCyberTrustRoot.crt) | d4de20d05e66fc53fe1a50882c78db2852cae474 |

مع أحد المراجع الم CAs المتوسطة التالية:

| الاسم الشائع للمرجع المصدق | بصمة الإبهام (SHA1) |
|--|--|
| [MICROSOFT RSA TLS CA 01](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2001.crt) | 703d7a8f0ebf55aaa59f98eaf4a206004eb2516a |
| [MICROSOFT RSA TLS CA 02](https://www.microsoft.com/pki/mscorp/Microsoft%20RSA%20TLS%20CA%2002.crt) | b0c2d2d13cdd56cdaa6ab6e2c04440be4a429c75 |

سيتم الآن ربط شهادات TLS الجديدة التي تستخدمها خدمات Microsoft 365 بأحد المراجع المصدقة الجذرية التالية:

| الاسم الشائع للمرجع المصدق | بصمة الإبهام (SHA1) |
|--|--|
| [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) | df3c24f9bfd666761b268073fe06d1cc8d4f82a4 |
| [المرجع المصدق الجذري ل Microsoft RSA 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20RSA%20Root%20Certificate%20Authority%202017.crt) | 73a5e64a3bff8316ff0edccc618a906e4eae4d74 | 
| [المرجع المصدق الجذري ل Microsoft ECC 2017](https://www.microsoft.com/pkiops/certs/Microsoft%20ECC%20Root%20Certificate%20Authority%202017.crt) | 999a64c37ff47d9fab95f14769891460eec4c3c5 |

مع أحد المراجع الم CAs المتوسطة التالية:

| الاسم الشائع للمرجع المصدق | بصمة الإبهام (SHA1) |
|--|--|
| [إصدار CA 01 من Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2001%20-%20xsign.crt) | 2f2877c5d778c31e0f29c7e371df5471bd673173 |
| [إصدار CA 02 من Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2002%20-%20xsign.crt) | e7eea674ca718e3befd90858e09f8372ad0ae2aa |
| [إصدار CA 05 من Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2005%20-%20xsign.crt) | 6c3af02e7f269aa73afd0eff2a88a4a1f04ed1e5 |
| [إصدار CA 06 من Microsoft Azure TLS](https://www.microsoft.com/pkiops/certs/Microsoft%20Azure%20TLS%20Issuing%20CA%2006%20-%20xsign.crt) | 30e01761ab97e59a06b41ef20af6f2de7ef4f7b0 |

على سبيل المثال، هذه شهادة صالحة مع إحدى سلاسل الشهادات الجديدة:

![سلسلة شهادات TLS ل Teams](../media/teams-tls-certificate-chain.png)

## <a name="will-this-change-affect-me"></a>هل سيؤثر هذا التغيير علي؟

المرجع المصدق الجذري "DigiCert Global Root G2" موثوق به على نطاق واسع من قبل أنظمة التشغيل بما في ذلك Windows وmacOS وAndroid وiOS ومن خلال مستعرضات مثل Microsoft Edge وChrome وSafari وFirefox. نتوقع أن **معظم عملاء Microsoft 365 لن يتأثروا**. 

ومع ذلك، **قد يتأثر التطبيق الخاص بك إذا كان يحدد بشكل صريح قائمة المراجع المعتمدة المقبولة**. تعرف هذه الممارسة باسم "تثبيت الشهادة". سيتلقى العملاء الذين ليس لديهم المراجع المصدقة الجذرية الجديدة في قائمة المراجع المصدقة المقبولة أخطاء التحقق من صحة الشهادة، والتي قد تؤثر على توفر التطبيق أو دالته.

فيما يلي بعض الطرق للكشف عن ما إذا كان التطبيق الخاص بك قد يتأثر:

- ابحث في التعليمات البرمجية المصدر عن بصمة الإبهام أو الاسم الشائع أو الخصائص الأخرى لأي من المراجع المرجعة المرجعة الوسيطة الموجودة [هنا](https://www.microsoft.com/pki/mscorp/cps/default.htm). إذا كان هناك تطابق، فسيتأثر تطبيقك. لحل هذه المشكلة، قم بتحديث التعليمات البرمجية المصدر لإضافة خصائص المراجع المرجعة الجديدة. وكأفضل ممارسة، تأكد من إمكانية إضافة المراجع المحسنة أو تحريرها في غضون إشعار قصير. تتطلب اللوائح الصناعية استبدال شهادات المرجع المصدق في غضون سبعة أيام في بعض الظروف، لذلك يجب أن تتفاعل التطبيقات التي تنفذ تثبيت الشهادات مع هذه التغييرات بسرعة.

- يكشف .NET دالات `System.Net.ServicePointManager.ServerCertificateValidationCallback` رد الاتصال والاستدعاء `System.Net.HttpWebRequest.ServerCertificateValidationCallback` ، والتي تسمح للمطورين باستخدام منطق مخصص لتحديد ما إذا كانت الشهادات صالحة بدلا من الاعتماد على مخزن شهادات Windows القياسي. يمكن للمطور إضافة منطق يتحقق من وجود اسم شائع أو بصمة إبهام معينة أو يسمح فقط بالمرجع المصدق الجذري المحدد مثل "Baltimore CyberTrust Root". إذا كان التطبيق الخاص بك يستخدم دالات رد الاتصال هذه، يجب التأكد من أنه يقبل كلا من المراجع المصدقة الجذرية والمتوسطة القديمة والجديدة.

- قد تستخدم `WINHTTP_CALLBACK_STATUS_SENDING_REQUEST`التطبيقات الأصلية ، ما يسمح للتطبيقات الأصلية بتنفيذ منطق التحقق من صحة الشهادة المخصص. استخدام هذا الإعلام نادر ويتطلب قدرا كبيرا من التعليمات البرمجية المخصصة لتنفيذها. على غرار ما سبق، تأكد من أن التطبيق الخاص بك يقبل كلا من المراجع المصدقة الجذرية والجديدة والمتوسطة. 

- إذا كنت تستخدم تطبيقا يتكامل مع Microsoft Teams أو Skype أو Skype for Business Online أو Microsoft Dynamics APIs وكنت غير متأكد مما إذا كان يستخدم تثبيت الشهادة، فتحقق من مورد التطبيق.

- قد تتطلب أنظمة التشغيل المختلفة ووقت تشغيل اللغة التي تتصل بخدمات Azure خطوات أخرى لإنشاء سلاسل الشهادات الجديدة والتحقق من صحتها بشكل صحيح:
   - **Linux**: تتطلب منك العديد من التوزيعات إضافة CAs إلى `/etc/ssl/certs`. للحصول على تعليمات محددة، راجع وثائق التوزيع.
   - **Java**: تأكد من أن مخزن مفاتيح Java يحتوي على المراجع المضمنة أعلاه.
   - **Windows الذي يعمل في بيئات غير متصلة**: ستحتاج الأنظمة التي تعمل في بيئات غير متصلة إلى إضافة المراجع المصدقة الجذرية الجديدة إلى متجرها `Trusted Root Certification Authorities` وإضافة المراجع المصدقة الوسيطة الجديدة إلى متجرها `Intermediate Certification Authorities` .
   - **Android**: تحقق من وثائق جهازك وإصدار Android.
   - **IoT أو الأجهزة المضمنة**: غالبا ما تشحن الأجهزة المضمنة مثل المربعات العلوية لمجموعة التلفزيون بمجموعة محدودة من شهادات المرجع الجذر وليس لديها طريقة سهلة لتحديث مخزن الشهادات. إذا كتبت تعليمة برمجية للأجهزة المخصصة المضمنة أو IoT أو تديرها، فتأكد من أن الأجهزة تثق في المراجع المصدقة الجذرية الجديدة. قد تحتاج إلى الاتصال بالشركة المصنعة للجهاز.

- إذا كانت لديك بيئة تسمح فيها قواعد جدار الحماية بالمكالمات الصادرة إلى نقاط نهاية معينة فقط، فاسمح بعناوين URL التالية لقائمة إبطال الشهادات (CRL) أو بروتوكول حالة الشهادة عبر الإنترنت (OCSP):
   - `http://crl3.digicert.com`
   - `http://crl4.digicert.com`
   - `http://ocsp.digicert.com`
   - `http://crl.microsoft.com`
   - `http://oneocsp.microsoft.com`
   - `http://ocsp.msocsp.com`
   - `http://www.microsoft.com/pkiops`

- إذا تأثرت بهذا التغيير، فقد ترى رسائل خطأ تعتمد على نوع البيئة التي تعمل فيها والسيناريو الذي تتأثر به. تحقق من سجلات أحداث تطبيق Windows وسجلات أحداث CAPI2 وسجلات التطبيقات المخصصة للرسائل التي تبدو مثل:
   ```output
   An operation failed because the following certificate has validation errors:
   
   Subject Name: CN=teams.microsoft.com
   Issuer Name: CN=Microsoft Azure TLS Issuing CA 01, O=Microsoft Corporation, C=US
   
   Errors:
   
   The root of the certificate chain is not a trusted root authority.
   ```

## <a name="when-can-i-retire-the-old-ca-information"></a>متى يمكنني إيقاف معلومات CA القديمة؟

لن يتم إبطال شهادات المرجع المصدق الجذري الحالية والمرجع المصدق المتوسط وشهادات الكائن الطرفي. ستكون أسماء المرجع المصدق المشتركة و/أو بصمات الإبهام الموجودة مطلوبة حتى أكتوبر 2023 على الأقل استنادا إلى مدة بقاء الشهادات الموجودة.

## <a name="known-issues"></a>المشاكل المعروفة

في ظل ظروف نادرة جدا، قد يرى مستخدمو المؤسسة أخطاء التحقق من صحة الشهادة حيث يظهر المرجع المصدق الجذري "DigiCert Global Root G2" كما تم إبطاله. يعود سبب ذلك إلى وجود خطأ Windows معروف ضمن كلا الشرطين التاليين:

- المرجع المصدق الجذري موجود في [مخزن شهادات CurrentUser\Root](/windows/win32/seccrypto/system-store-locations#cert_system_store_current_user) ويفقد `NotBeforeFileTime` `NotBeforeEKU` الخصائص
- المرجع المصدق الجذري موجود أيضا في [مخزن شهادات LocalMachine\AuthRoot](/windows/win32/seccrypto/system-store-locations#cert_system_store_local_machine) ولكنه يحتوي على كل من `NotBeforeFileTime` الخصائص والخصائص `NotBeforeEKU`

تظهر كافة شهادات الكائن الطرفي التي تم إصدارها من المرجع المصدق الجذري هذا بعد إبطالها `NotBeforeFileTime` . 

يمكن للمسؤولين تحديد المشكلة واستكشافها وإصلاحها عن طريق فحص سجل CAPI2 لمعرفة هذا الخطأ:

```text
Log Name:      Microsoft-Windows-CAPI2/Operational
Source:        Microsoft-Windows-CAPI2
Date:          6/23/2022 8:36:39 AM
Event ID:      11
Task Category: Build Chain
Level:         Error
[...]
        <ChainElement>
          <Certificate fileRef="DF3C24F9BFD666761B268073FE06D1CC8D4F82A4.cer" subjectName="DigiCert Global Root G2" />
          [...]
          <TrustStatus>
            <ErrorStatus value="4000024" CERT_TRUST_IS_REVOKED="true" CERT_TRUST_IS_UNTRUSTED_ROOT="true" CERT_TRUST_IS_EXPLICIT_DISTRUST="true" />
            <InfoStatus value="10C" CERT_TRUST_HAS_NAME_MATCH_ISSUER="true" CERT_TRUST_IS_SELF_SIGNED="true" CERT_TRUST_HAS_PREFERRED_ISSUER="true" />
          </TrustStatus>
          [...]
          <RevocationInfo freshnessTime="PT0S">
            <RevocationResult value="80092010">The certificate is revoked.</RevocationResult>
          </RevocationInfo>
        </ChainElement>
      </CertificateChain>
      <EventAuxInfo ProcessName="Teams.exe" />
      <Result value="80092010">The certificate is revoked.</Result>
```
لاحظ وجود `CERT_TRUST_IS_EXPLICIT_DISTRUST="true"` العنصر. 

يمكنك التأكد من وجود نسختين من المرجع المصدق الجذري بخصائص مختلفة `NotBeforeFileTime` عن طريق تشغيل الأوامر التالية `certutil` ومقارنة الإخراج:

```
certutil -store -v authroot DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
certutil -user -store -v root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```

يمكن للمستخدم حل المشكلة عن طريق حذف نسخة المرجع المصدق الجذري في مخزن الشهادات `CurrentUser\Root` :
```
certutil -user -delstore root DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
```