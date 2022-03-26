---
title: إحضار Microsoft 365 Defender الأحداث
description: تعرف على كيفية الحصول على Microsoft 365 Defender من مستأجر عميل
keywords: موفر خدمة الأمان المدار، mssp، تكوين، تكامل
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 1ea39bfce5303360165a56d6361908d1014d370f
ms.sourcegitcommit: e110f00dc6949a7a1345187375547beeb64225b2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/06/2021
ms.locfileid: "63574687"
---
# <a name="fetch-microsoft-365-defender-incidents"></a>إحضار Microsoft 365 Defender الأحداث 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> [!NOTE]
> يتم اتخاذ هذا الإجراء بواسطة MSSP.

هناك طريقتان لإحضار التنبيهات:

- استخدام أسلوب SIEM
- استخدام واجهات برمجة التطبيقات

## <a name="fetch-incidents-into-your-siem"></a>إحضار أحداث إلى SIEM

لإحضار الأحداث إلى نظام SIEM، ستحتاج إلى اتخاذ الخطوات التالية:

- الخطوة 1: إنشاء تطبيق جهة خارجية
- الخطوة 2: الحصول على الوصول إلى الرموز المميزة وتحديثها من مستأجر العميل
- الخطوة 3: السماح بتطبيقك على Microsoft 365 Defender

### <a name="step-1-create-an-application-in-azure-active-directory-azure-ad"></a>الخطوة 1: إنشاء تطبيق في Azure Active Directory (Azure AD)

ستحتاج إلى إنشاء تطبيق ومنحه أذونات لإحضار التنبيهات من مستأجر Microsoft 365 Defender العميل.

1. سجل الدخول إلى مدخل [Azure AD](https://aad.portal.azure.com/).

2. حدد **تسجيلات تطبيق Azure Active Directory** \> **.**

3. انقر **فوق تسجيل جديد**.

4. حدد القيم التالية:

    - الاسم: \<Tenant_name\> SIEM MSSP Connector (استبدال Tenant_name باسم عرض المستأجر)

    - أنواع الحسابات المعتمدة: الحساب في دليل المؤسسة هذا فقط
    - إعادة توجيه URI: حدد ويب وا اكتب `https://<domain_name>/SiemMsspConnector`(استبدل <domain_name> باسم المستأجر)

5. انقر **فوق تسجيل**. يتم عرض التطبيق في قائمة التطبيقات التي تملكها.

6. حدد التطبيق، ثم انقر فوق **نظرة عامة**.

7. انسخ القيمة من **الحقل Application (client) ID إلى** مكان آمن، ستحتاج إلى ذلك في الخطوة التالية.

8. حدد **شهادة & في** لوحة التطبيق الجديدة.

9. انقر **فوق سري عميل جديد**.

    - الوصف: أدخل وصفا للمفتاح.
    - انتهاء الصلاحية: **تحديد في سنة واحدة**

10. انقر **فوق** إضافة، وانسخ قيمة سرية العميل إلى مكان آمن، ستحتاج إلى ذلك في الخطوة التالية.

### <a name="step-2-get-access-and-refresh-tokens-from-your-customers-tenant"></a>الخطوة 2: الحصول على الوصول إلى الرموز المميزة وتحديثها من مستأجر العميل

يرشدك هذا القسم إلى كيفية استخدام برنامج PowerShell النصي للحصول على الرموز المميزة من مستأجر العميل. يستخدم هذا البرنامج النصي التطبيق من الخطوة السابقة للحصول على الرموز المميزة للوصول وتحديثها باستخدام رمز تخويل OAuth Flow.

بعد توفير بيانات الاعتماد الخاصة بك، ستحتاج إلى منح الموافقة على التطبيق بحيث يتم توفير التطبيق في مستأجر العميل.

1. إنشاء مجلد جديد ونسمه: `MsspTokensAcquisition`.

2. قم [بتنزيل الوحدة النمطية LoginBrowser.psm1](https://github.com/shawntabrizi/Microsoft-Authentication-with-PowerShell-and-MSAL/blob/master/Authorization%20Code%20Grant%20Flow/LoginBrowser.psm1) واحفظها في `MsspTokensAcquisition` المجلد.

    > [!NOTE]
    > في السطر 30، استبدل `authorzationUrl` ب `authorizationUrl`.

3. أنشئ ملفا يحتوي على المحتوى التالي واحفظه بالاسم `MsspTokensAcquisition.ps1` في المجلد:

    ```powershell
    param (
        [Parameter(Mandatory=$true)][string]$clientId,
        [Parameter(Mandatory=$true)][string]$secret,
        [Parameter(Mandatory=$true)][string]$tenantId
    )
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

    # Load our Login Browser Function
    Import-Module .\LoginBrowser.psm1

    # Configuration parameters
    $login = "https://login.microsoftonline.com"
    $redirectUri = "https://SiemMsspConnector"
    $resourceId = "https://graph.windows.net"

    Write-Host 'Prompt the user for his credentials, to get an authorization code'
    $authorizationUrl = ("{0}/{1}/oauth2/authorize?prompt=select_account&response_type=code&client_id={2}&redirect_uri={3}&resource={4}" -f
                        $login, $tenantId, $clientId, $redirectUri, $resourceId)
    Write-Host "authorzationUrl: $authorizationUrl"

    # Fake a proper endpoint for the Redirect URI
    $code = LoginBrowser $authorizationUrl $redirectUri

    # Acquire token using the authorization code

    $Body = @{
        grant_type = 'authorization_code'
        client_id = $clientId
        code = $code
        redirect_uri = $redirectUri
        resource = $resourceId
        client_secret = $secret
    }

    $tokenEndpoint = "$login/$tenantId/oauth2/token?"
    $Response = Invoke-RestMethod -Method Post -Uri $tokenEndpoint -Body $Body
    $token = $Response.access_token
    $refreshToken= $Response.refresh_token

    Write-Host " ----------------------------------- TOKEN ---------------------------------- "
    Write-Host $token

    Write-Host " ----------------------------------- REFRESH TOKEN ---------------------------------- "
    Write-Host $refreshToken
    ```
4. افتح موجه أوامر PowerShell مرتفعا في `MsspTokensAcquisition` المجلد.

5. تشغيل الأمر التالي: `Set-ExecutionPolicy -ExecutionPolicy Bypass`

6. أدخل الأوامر التالية: `.\MsspTokensAcquisition.ps1 -clientId <client_id> -secret <app_key> -tenantId <customer_tenant_id>`

    - استبدل \<client_id\> **بميود التطبيق (العميل)** الذي حصلت عليه من الخطوة السابقة.
    - استبدل \<app_key\> **بسر العميل** الذي أنشأته من الخطوة السابقة.
    - استبدل \<customer_tenant_id\> بم **ID المستأجر الخاص للعميل**.

7. سيطلب منك تقديم بيانات الاعتماد الخاصة بك وموافقتك. تجاهل إعادة توجيه الصفحة.

8. في نافذة PowerShell، ستتلقى رمز وصول مميز و رمز تحديث مميز. احفظ رمز التحديث المميز لتكوين موصل SIEM.

### <a name="step-3-allow-your-application-on-microsoft-365-defender"></a>الخطوة 3: السماح بتطبيقك على Microsoft 365 Defender

ستحتاج إلى السماح للتطبيق الذي أنشأته في Microsoft 365 Defender.

ستحتاج إلى إذن **إدارة إعدادات نظام المدخل** للسماح للتطبيق. وبخلاف ذلك، ستحتاج إلى الطلب من العميل السماح للتطبيق لك.

1. انتقل إلى `https://security.microsoft.com?tid=<customer_tenant_id>` (استبدل \<customer_tenant_id\> بم ID المستأجر الخاص للعميل.

2. انقر **الإعدادات** \> **واجهات برمجة التطبيقات** \> **لنقاط النهاية** \> **SIEM**.

3. حدد علامة **التبويب MSSP** .

4. أدخل **"معر ة التطبيق** " من الخطوة الأولى وم **ID المستأجر الخاص بك**.

5. انقر **فوق تخويل التطبيق**.

يمكنك الآن تنزيل ملف التكوين ذي الصلة ل SIEM والاتصال Microsoft 365 Defender API. لمزيد من المعلومات، راجع سحب [التنبيهات إلى أدوات SIEM](../defender-endpoint/configure-siem.md).

- في ملف تكوين ArcSight / ملف خصائص مصادقة Splunk، اكتب مفتاح التطبيق يدويا من خلال تعيين القيمة السرية.
- بدلا من الحصول على رمز تحديث مميز في المدخل، استخدم البرنامج النصي من الخطوة السابقة للحصول على رمز تحديث مميز (أو الحصول عليه باستخدام وسائل أخرى).

## <a name="fetch-alerts-from-mssp-customers-tenant-using-apis"></a>إحضار تنبيهات من مستأجر عميل MSSP باستخدام واجهات برمجة التطبيقات

للحصول على معلومات حول كيفية إحضار التنبيهات باستخدام REST API، راجع [سحب التنبيهات باستخدام REST API](../defender-endpoint/pull-alerts-using-rest-api.md).
