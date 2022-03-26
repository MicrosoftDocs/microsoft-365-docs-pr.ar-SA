---
title: إنشاء نهج نوع معلومات حساسة باستخدام تشفير الرسائل من Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- Strat_O365_Enterprise
description: تعرف على كيفية إنشاء نهج نوع معلومات حساسة لم المؤسسة باستخدام تشفير الرسائل من Office 365.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 8978b1f9faae2e96fa1940bf7663855ec3bb61da
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63565940"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>إنشاء نهج نوع معلومات حساسة لمنظمتك باستخدام تشفير الرسائل

يمكنك استخدام Exchange تدفق البريد الإلكتروني أو منع فقدان البيانات (DLP) لإنشاء نهج نوع معلومات حساسة باستخدام تشفير الرسائل من Office 365. لإنشاء قاعدة تدفق Exchange البريد الإلكتروني، يمكنك استخدام Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">إدارة (EAC)</a> أو PowerShell.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>لإنشاء النهج باستخدام قواعد تدفق البريد في EAC

سجل الدخول إلى Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">إدارة البريد واذهب</a> إلى **تدفق** **البريدRules** > . في صفحة القواعد، أنشئ قاعدة تنطبق على تشفير الرسائل من Office 365. يمكنك إنشاء قاعدة استنادا إلى شروط مثل وجود كلمات أساسية معينة أو أنواع معلومات حساسة في الرسالة أو المرفق.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>لإنشاء النهج باستخدام قواعد تدفق البريد في PowerShell

استخدم حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، وابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). استخدم Set-IRMConfiguration New-TransportRule cmdlets لإنشاء النهج.

## <a name="example-mail-flow-rule-created-with-powershell"></a>مثال على قاعدة تدفق البريد التي تم إنشاؤها باستخدام PowerShell

قم بتشغيل الأوامر التالية في PowerShell لإنشاء قاعدة تدفق بريد Exchange تقوم تلقائيا بتشفير رسائل البريد الإلكتروني المرسلة خارج مؤسستك باستخدام خيار التشفير فقط إذا كانت رسائل البريد الإلكتروني أو مرفقاتها تحتوي على أنواع المعلومات الحساسة التالية:

- رقم توجيه ABA
- رقم بطاقة الائتمان
- رقم وكالة مكافحة المخدرات (DEA)
- الولايات المتحدة / المملكة المتحدة رقم جواز السفر
- رقم الحساب البنكي الأميركي
- رقم تعريف الممول الفردي (ITIN)
- رقم الضمان الاجتماعي (SSN) الأميركي

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

لمزيد من المعلومات، راجع [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) و [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>كيفية وصول المستلمين إلى المرفقات

بعد أن تقوم Microsoft بتشفير رسالة، يمكن للمستلمين الوصول غير المقيد إلى المرفقات عند الوصول إلى البريد الإلكتروني المشفر وفتحه.

## <a name="to-prepare-for-this-change"></a>للتحضير لهذا التغيير

قد ترغب في تحديث أي وثائق ومواد تدريبية قابلة للتطبيق للمستخدم النهائي لإعداد الأشخاص في مؤسستك لهذا التغيير. شارك هذه تشفير الرسائل من Office 365 الموارد مع المستخدمين لديك حسب الاقتضاء:

- [إرسال رسائل مشفرة وعرضها والرد عليها في Outlook الكمبيوتر الشخصي](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Microsoft 365 الأساسيات: Office تشفير الرسائل](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>عرض هذه التغييرات في سجل التدقيق

Microsoft 365 هذا النشاط ويجعله متوفرا للمسؤولين. العملية هي 'New-TransportRule' و قصاصة من إدخال تدقيق عينة من البحث في سجل التدقيق في الأمان & مركز التوافق أدناه:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"…etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>لتعطيل نهج أنواع المعلومات الحساسة أو تخصيصه

بمجرد إنشاء قاعدة تدفق البريد في Exchange، يمكنك تعطيل القاعدة أو تحريرها عن طريق الذهاب [](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) إلى **تدفق** >  **البريدالقاعدة** في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> وتعطيل القاعدة "تشفير رسائل البريد الإلكتروني الحساسة الصادرة (خارج قاعدة المربع *)*".