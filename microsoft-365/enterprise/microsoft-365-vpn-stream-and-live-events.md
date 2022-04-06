---
title: اعتبارات خاصة للبث والأحداث المباشرة في بيئات VPN
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: اعتبارات خاصة للبث والأحداث المباشرة في بيئات VPN
ms.openlocfilehash: eb2e57b844f06bc3b1e005aa1095794b176bba94
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705253"
---
# <a name="special-considerations-for-stream-and-live-events-in-vpn-environments"></a>اعتبارات خاصة للبث والأحداث المباشرة في بيئات VPN

>[!NOTE]
>هذه المقالة هي جزء من مجموعة من المقالات التي تعالج Microsoft 365 للمستخدمين البعيدين.

>- للحصول على نظرة عامة حول استخدام تقسيم VPN لتحسين Microsoft 365 للمستخدمين البعيدين، راجع نظرة عامة[: تقسيم VPN](microsoft-365-vpn-split-tunnel.md) للتحكم Microsoft 365.
>- للحصول على إرشادات مفصلة حول تنفيذ تقسيم VPN، راجع تنفيذ تقسيم [VPN Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- للحصول على قائمة تفصيلية بسيناريوهات تقسيم VPN التي تم تقسيمها، راجع سيناريوهات تقسيم VPN الشائعة [لسيناريوهات](microsoft-365-vpn-common-scenarios.md) تقسيم VPN Microsoft 365.
>- للحصول على إرشادات حول تأمين Teams الوسائط في بيئات تقسيم VPN التي تم تقسيمها، راجع تأمين Teams الوسائط لتقسيم [VPN](microsoft-365-vpn-securing-teams.md).
>- للحصول على معلومات حول تحسين Microsoft 365 المستأجر على مستوى العالم للمستخدمين في الصين، راجع Microsoft 365 تحسين أداء [المستخدمين في الصين](microsoft-365-networking-china.md).

Microsoft 365 حركة مرور الأحداث المباشرة (يشمل ذلك الحضور إلى الأحداث المباشرة التي تم إنتاج Teams منها وتلك التي يتم إنتاجها باستخدام ترميز خارجي عبر Teams أو Stream أو Yammer) كما يتم حاليا تصنيف حركة مرور Stream عند الطلب على أنها افتراضية مقابل تحسين في قائمة [URL/IP](urls-and-ip-address-ranges.md) للخدمة.  يتم تصنيف نقاط النهاية هذه **كافتراضية** لأنها مستضافة على CDNs التي قد تستخدمها خدمات أخرى أيضا. يفضل العملاء بشكل عام إنشاء وكيل لهذا النوع من البيانات وتطبيق أي عناصر أمان يتم القيام بها عادة على نقاط النهاية مثل هذه.

طلب العديد من العملاء بيانات URL/IP اللازمة لتوصيل المستخدمين ب Stream/Live Events مباشرة من اتصال الإنترنت المحلي، بدلا من توجيه حركة المرور عالية الحجم وحساسة زمن المرور عبر البنية الأساسية ل VPN. عادة، لا يكون ذلك ممكنا بدون كل من مساحات الاسم المخصصة ومعلومات IP الدقيقة لنقاط النهاية، والتي لا يتم توفيرها لنقاط نهاية Microsoft 365 المصنفة **كافتراضية**.

استخدم الخطوات التالية لتمكين الاتصال المباشر لخدمة Stream/Live Events من العملاء باستخدام VPN إجباري. الهدف من هذا الحل هو تزويد العملاء بخيار لتجنب توجيه حركة مرور Live Events عبر VPN أثناء وجود نسبة مرور عالية على الشبكة بسبب سيناريوهات العمل من المنزل. وينصح بالوصول إلى الخدمة من خلال وكيل فحص، إذا أمكن ذلك.

>[!NOTE]
>باستخدام هذا الحل، قد تكون هناك عناصر خدمة لا تحل عناوين IP المتوفرة وبالتالي تجتاز VPN، ولكن يجب أن يتم نقل البيانات بشكل كبير مثل دفق البيانات. قد تكون هناك عناصر أخرى خارج نطاق Live Events/Stream يتم مسكها نتيجة هذا التحميل، ولكن يجب أن تكون محدودة حيث يجب أن تلبي كل من FQDN ومطابقة IP قبل  المباشر.

>[!IMPORTANT]
>يتم توجيه العملاء إلى تقييم مخاطر إرسال المزيد من حركة المرور التي تتجاوز VPN عبر اكتساب الأداء للأحداث المباشرة.

لتنفيذ استثناء إجباري للانبثاث Teams Live Events وS stream، يجب تطبيق الخطوات التالية:

## <a name="1-configure-external-dns-resolution"></a>1. تكوين دقة DNS خارجية

يحتاج العملاء إلى دقة DNS خارجية ومت تكرارية حتى يمكن حل أسماء المضيفين التالية إلى عناوين IP.

- \*.azureedge.net
- \*.media.azure.net
- \*.bmc.cdn.office.net

**\*.azureedge.net** يستخدم هذا الإعداد في أحداث Stream (تكوين ترميزات للتدفق المباشر في [Microsoft Stream - Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*يتم** **media.azure.net.bmc.cdn.office.net\* و .bmc.cdn.office.net** Teams Live Events (أحداث البدء السريع، أحداث RTMP-In المعتمدة [المخطط الم ID 84960]) المجدولة من عميل Teams.

 تمت مشاركة بعض نقاط النهاية هذه مع عناصر أخرى خارج Stream/Live Events، لا ننصحك باستخدام FQDNs هذه لتكوين تحميل VPN حتى لو كان ذلك ممكنا من الناحية التقنية في حل VPN (على سبيل المثال، إذا كان يعمل على FQDN بدلا من IP).

إن FQDNs غير مطلوبة في تكوين VPN، بل تستخدم فقط في ملفات PAC مع IPs لإرسال حركة المرور ذات الصلة مباشرة.

## <a name="2-implement-pac-file-changes-where-required"></a>2. تنفيذ تغييرات ملف PAC (عند الحاجة)

بالنسبة إلى المؤسسات التي تستخدم ملف PAC من أجل توجيه حركة المرور عبر وكيل أثناء العمل على VPN، يتم عادة تحقيق ذلك باستخدام FQDNs. ومع ذلك، باستخدام Stream/Live Events **\***، تحتوي أسماء المضيفين المتوفرة على أحرف بدل مثل .azureedge.net، والتي تشمل أيضا العناصر الأخرى التي لا يمكن توفير قوائم IP كاملة لها. وبالتالي، إذا تم إرسال الطلب مباشرة استنادا إلى تطابق أحرف البدل DNS فقط، سيتم حظر حركة المرور إلى نقاط النهاية هذه حيث لا يوجد مسار عبر المسار المباشر له في الخطوة [3](#3-configure-routing-on-the-vpn-to-enable-direct-egress) لاحقا في هذه المقالة.

لحل هذه المشكلة، يمكننا توفير IPs التالية واستخدامها مع أسماء المضيفين في مثال ملف PAC كما هو موضح في [الخطوة 1](#1-configure-external-dns-resolution). يفحص ملف PAC ما إذا كان عنوان URL يتطابق مع تلك المستخدمة في أحداث Stream/Live، ثم إذا كان كذلك، فإنه يتحقق أيضا لمعرفة ما إذا كان عنوان IP الذي تم إرجاعه من عملية البحث DNS يتطابق مع تلك المتوفرة للخدمة. إذا _تطابق كل_ منهما، يتم توجيه حركة المرور مباشرة. إذا لم يكن أي من العنصرين (FQDN/IP) متطابقا، يتم إرسال حركة المرور إلى الوكيل. ونتيجة لذلك، يضمن التكوين أن أي شيء يتم حله إلى IP خارج نطاق كل من IP ومجالات الاسم المعرفة سيجتاز الوكيل عبر VPN كالمعتاد.

### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>تجميع القوائم الحالية لنقاط نهاية CDN

تستخدم Live Events عدة موفري CDN للتدفق إلى العملاء، لتوفير أفضل تغطية وجودة و مرونة. يتم حاليا استخدام Azure CDN من Microsoft ومن Verizon. ومع مرور الوقت، قد يتغير ذلك بسبب حالات مثل التوفر الإقليمي. هذه المقالة هي مصدر لتمكينك من المحافظة على آخر المدى على نطاقات IP.

بالنسبة إلى Azure CDN من Microsoft، يمكنك تنزيل القائمة من تنزيل نطاقات [IP من Azure](https://www.microsoft.com/download/details.aspx?id=56519) والعلامات الخاصة بالخدمة – السحابة العامة من مركز التنزيل الرسمي ل Microsoft - ستحتاج إلى البحث بشكل خاص عن علامة الخدمة *AzureFrontdoor.Frontend* في JSON؛ *addressPrefixes* will show the IPv4/IPv6 subnets. بمرور الوقت، يمكن أن تتغير IPs، ولكن يتم دائما تحديث قائمة علامات الخدمة قبل استخدامها.

بالنسبة إلى Azure CDN من Verizon (Edgecast) [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) يمكنك العثور على قائمة شاملة باستخدام (انقر فوق **تجربة ) -** **\_** ستحتاج إلى البحث عن المقطع Premium Verizon تحديدا. تجدر الإشارة إلى أن API تعرض كل برامج IPs ل Edgecast (الأصل و Anycast). لا توجد حاليا آلية ل API للتمييز بين الأصل و Anycast.

لتنفيذ ذلك في ملف PAC، يمكنك استخدام المثال التالي الذي يرسل إلى Microsoft 365 تحسين حركة المرور المباشر (وهو أفضل الممارسات المستحسنة) عبر FQDN، و نقل بيانات أحداث Stream/Live الهامة مباشرة عبر مجموعة من FQDN وعنوان IP الذي تم إرجاعه. يجب تحرير اسم العنصر النائب _Contoso_ إلى اسم المستأجر المحدد حيث _contoso_ من contoso.onmicrosoft.com

#### <a name="example-pac-file"></a>مثال لملف PAC

فيما يلي مثال حول كيفية إنشاء ملفات PAC:

1. احفظ البرنامج النصي أدناه على القرص الثابت _المحليGet-TLEPacFile.ps1._
1. انتقل إلى [عنوان URL Verizon وتنزيل](/rest/api/cdn/edge-nodes/list#code-try-0) JSON الناتج (انسخ لصقه في ملف مثل cdnedgenodes.json)
1. ضع الملف في المجلد نفسه الذي يحتوي على البرنامج النصي.
1. في نافذة PowerShell، تشغيل الأمر التالي. يمكنك تغيير اسم المستأجر لشيء آخر إذا كنت تريد عناوين URL ل SPO. هذا هو النوع 2، لذلك **تحسين** **والسماح** (النوع 1 هو تحسين فقط).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. سيحتوي ملف TLE.pac على كل مساحات الاسم و IPs (IPv4/IPv6).

##### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

سيتم تحليل البرنامج النصي تلقائيا لقائمة Azure استنادا إلى عنوان [URL](https://www.microsoft.com/download/details.aspx?id=56519) للتنزيل والمفاتيح من **AzureFrontDoor.Frontend**، لذا لا حاجة إلى الحصول عليها يدويا.

مرة أخرى، لا ينصح بإجراء عملية تفريغ VPN باستخدام FQDNs فقط؛ يساعد **استخدام كل** من FQDN وعناوين IP في الدالة على تحديد نطاق استخدام هذا التحميل إلى مجموعة محدودة من نقاط النهاية بما في ذلك Live Events/Stream. ستنتج عن الطريقة التي يتم بها بناء الدالة إجراء عملية البحث عن DNS ل FQDN التي تطابق تلك المدرجة بواسطة العميل مباشرة، أي أن دقة DNS لم مساحات الاسم المتبقية لا تتغير.

إذا كنت ترغب في الحد من مخاطر إزالة تحميل نقاط النهاية غير المرتبطة ب Live Events **\*** وS stream، يمكنك إزالة مجال .azureedge.net من التكوين حيث يقع معظم هذا الخطر حيث إنه مجال مشترك يستخدم لجميع عملاء Azure CDN. الجانب السلبي لذلك هو أنه لن يتم تحسين أي حدث يستخدم ترميز خارجي ولكن الأحداث التي يتم إنتاجها/تنظيمها ضمن Teams ستكون كذلك.

## <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. تكوين التوجيه على VPN لتمكين الخروج المباشر

الخطوة الأخيرة هي إضافة مسار مباشر ل IPS الأحداث المباشرة الموضحة في جمع القوائم الحالية لنقاط نهاية **CDN** في تكوين VPN لضمان عدم إرسال حركة المرور عبر النقل المضطر إلى VPN. معلومات تفصيلية حول كيفية إجراء ذلك Microsoft 365 يمكن العثور على تحسين نقاط النهاية في المقطع تنفيذ [تقسيم VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) من تنفيذ تقسيم [VPN](microsoft-365-vpn-implement-split-tunnel.md) الذي يتم تقسيمه إلى Microsoft 365. العملية هي نفسها تماما ل IPs أحداث Stream/Live المدرجة في هذا المستند.

تجدر الإشارة إلى أنه يجب استخدام IPs (وليس FQDNs) فقط من تجميع القوائم الحالية [لنقاط نهاية CDN](#gathering-the-current-lists-of-cdn-endpoints) لتكوين VPN.

## <a name="faq"></a>الأسئلة المتداولة

### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>هل سيرسل هذا كل حركة المرور إلى الخدمة مباشرة؟

لا، سيرسل ذلك حركة النقل المتدفقة الحساسة لزمن المرور ل Live Event أو Stream video direct، ستستمر أي حركة مرور أخرى في استخدام خدمة VPN إذا لم تحل على ملفات IPs المنشورة.

### <a name="do-i-need-to-use-the-ipv6-addresses"></a>هل أحتاج إلى استخدام عناوين IPv6؟

لا، يمكن أن يكون الاتصال IPv4 فقط إذا لزم الأمر.

### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>لماذا لا يتم نشر عناوين IP هذه في Microsoft 365 URL/IP؟

تتحكم Microsoft بشكل صارم في تنسيق المعلومات المضمنة في الخدمة ونوعها لضمان أن العملاء يمكنهم استخدام المعلومات بشكل موثوق لتنفيذ التوجيه الآمن والأمثل استنادا إلى فئة نقطة النهاية.

لا **توفر** فئة نقطة النهاية الافتراضية معلومات IP لأسباب عديدة (قد تكون نقاط النهاية الافتراضية خارج نطاق تحكم Microsoft، أو قد تتغير بشكل متكرر جدا، أو قد تكون في كتل مشتركة مع عناصر أخرى). لهذا السبب، تم تصميم نقاط النهاية الافتراضية بحيث يتم إرسالها عبر FQDN إلى وكيل فحص، مثل حركة مرور الويب العادية.

في هذه الحالة، تكون نقاط النهاية أعلاه هي CDNs التي يمكن استخدامها من قبل عناصر غير خاضعة لمراقبة Microsoft غير Live Events أو Stream، وبالتالي فإن إرسال توجيه حركة المرور يعني أيضا أن أي شيء آخر يتم حله ل IPs هذه سيتم أيضا إرساله مباشرة من العميل. نظرا للطبيعة الفريدة للازمة العالمية الحالية وللوفاء باحتياجات عملائنا القصيرة المدى، وفرت Microsoft المعلومات الواردة أعلاه للعملاء لاستخدامها كما يرونها مناسبة.

تعمل Microsoft على إعادة تكوين نقاط نهاية الأحداث المباشرة للسماح بتضمينها في فئات السماح/تحسين نقطة النهاية في المستقبل.

### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>هل أحتاج فقط إلى السماح بالوصول إلى هذه IPs؟

لا، يعد الوصول إلى كل نقاط  النهاية المطلوبة التي تم وضع علامة عليها في [خدمة URL/IP](urls-and-ip-address-ranges.md) أمرا أساسيا لكي تعمل الخدمة. بالإضافة إلى ذلك، يجب وضع علامة على أي نقطة نهاية اختيارية ل Stream (الم ID 41-45).

### <a name="what-scenarios-will-this-advice-cover"></a>ما هي السيناريوهات التي ستغطيها هذه النصائح؟

1. الأحداث المباشرة التي يتم إنتاجها ضمن Teams App
2. عرض المحتوى المستضاف في Stream
3. أحداث أنتجها جهاز خارجي (ترميز)

### <a name="does-this-advice-cover-presenter-traffic"></a>هل تغطي هذه النصيحة حركة مرور مقدم عرض؟

لا يحدث ذلك، فالنصائح الواردة أعلاه هي فقط لمن يستهلكون الخدمة. سيشاهد العرض التقديمي من داخل Teams حركة مرور مقدم العرض تتدفق إلى نقاط نهاية تحسين UDP التي تم وضع علامة عليها مدرجة في صف خدمة URL/IP 11 مع نصيحة تفصيلية حول تفريغ VPN موضحة في القسم تنفيذ تقسيم [VPN](microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) من تنفيذ تقسيم VPN الذي يتم تقسيمه إلى [Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).

### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>هل يخاطر هذا التكوين بخطر النقل غير Live Events &amp; Stream الذي يتم إرساله مباشرة؟

نعم، نظرا للعناصر FQDN المشتركة المستخدمة لبعض عناصر الخدمة، لا يمكن تجنب ذلك. يتم إرسال حركة المرور هذه عادة عبر وكيل الشركة الذي يمكنه تطبيق الفحص. في سيناريو تقسيم VPN للانقسام، فإن استخدام كل من FQDN و IPs سيحد من هذا الخطر إلى الحد الأدنى، ولكنه سيبقى موجودا. يمكن للعملاء إزالة مجال azureedge.net. من تكوين التحميل الخارجي وتقليل هذا الخطر إلى الحد الأدنى، ولكن هذا سيزيل التحميل من أحداث Live Live المعتمدة من Stream (أحداث ترميز خارجية مجدولة في Teams، أحداث ترميز خارجية، أحداث Yammer تم إنتاجها في Teams و Yammer أحداث ترميز خارجية مجدولة في Stream، والأحداث المجدولة في Stream أو عرض عند الطلب من Stream).**\*** الأحداث المجدولة والمنتجة في Teams غير متأثرة.

## <a name="related-articles"></a>المقالات ذات الصلة

[نظرة عامة: تقسيم VPN إلى تقسيم Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[تنفيذ تقسيم VPN لتنفيذ Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[سيناريوهات تقسيم VPN الشائعة للانقسام Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[تأمين Teams الوسائط من أجل تقسيم VPN](microsoft-365-vpn-securing-teams.md)

[Microsoft 365 تحسين أداء المستخدمين في الصين](microsoft-365-networking-china.md)

[Microsoft 365 "مبادئ اتصال الشبكة"](microsoft-365-network-connectivity-principles.md)

[تقييم Microsoft 365 الشبكة](assessing-network-connectivity.md)

[Microsoft 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

[طرق بديلة لمحترفي الأمان تكنولوجيا المعلومات لتحقيق عناصر التحكم الحديثة في الأمان في سيناريوهات العمل عن بعد الفريدة اليوم (مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[تحسين أداء VPN في Microsoft: Windows 10 ملفات تعريف VPN للسماح باتصالات التشغيل التلقائي](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[تشغيل VPN: كيف تحافظ Microsoft على اتصال القوى العاملة البعيدة](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[شبكة Microsoft العامة](/azure/networking/microsoft-global-network)
