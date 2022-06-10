---
title: إنشاء نهج نوع معلومات حساسة باستخدام تشفير الرسائل Office 365
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
description: تعرف على كيفية إنشاء نهج نوع معلومات حساس لمؤسستك باستخدام Office 365 تشفير الرسائل.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 908ec1cf55d8bee06ce9b3b6ccc8eb699d2ba291
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012263"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>إنشاء نهج نوع معلومات حساسة لمؤسستك باستخدام تشفير الرسائل

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكنك استخدام قواعد تدفق البريد Exchange أو منع فقدان بيانات Microsoft Purview (DLP) لإنشاء نهج نوع معلومات حساسة باستخدام تشفير الرسائل Office 365. لإنشاء قاعدة تدفق بريد Exchange، يمكنك استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange (EAC)</a> أو PowerShell.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>لإنشاء النهج باستخدام قواعد تدفق البريد في EAC

سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> وانتقل إلى **"قواعد** **تدفق** >  البريد". في صفحة "القواعد"، أنشئ قاعدة تطبق Office 365 تشفير الرسائل. يمكنك إنشاء قاعدة استنادا إلى شروط مثل وجود كلمات أساسية معينة أو أنواع معلومات حساسة في الرسالة أو المرفق.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>لإنشاء النهج باستخدام قواعد تدفق البريد في PowerShell

استخدم حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العمومي في مؤسستك، والاتصال Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). استخدم Set-IRMConfiguration و cmdlets New-TransportRule لإنشاء النهج.

## <a name="example-mail-flow-rule-created-with-powershell"></a>مثال على قاعدة تدفق البريد التي تم إنشاؤها باستخدام PowerShell

قم بتشغيل الأوامر التالية في PowerShell لإنشاء قاعدة تدفق بريد Exchange تقوم تلقائيا بتشفير رسائل البريد الإلكتروني المرسلة خارج مؤسستك باستخدام خيار التشفير فقط إذا كانت رسائل البريد الإلكتروني أو مرفقاتها تحتوي على أنواع المعلومات الحساسة التالية:

- رقم توجيه ABA
- رقم بطاقة الائتمان
- رقم وكالة إنفاذ مكافحة الأدوية (DEA)
- الولايات المتحدة / المملكة المتحدة رقم جواز السفر
- رقم الحساب البنكي الأمريكي
- رقم تعريف هوية الأفراد في الولايات المتحدة (ITIN)
- رقم الضمان الاجتماعي (SSN) في الولايات المتحدة

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

لمزيد من المعلومات، راجع [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) و [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>كيفية وصول المستلمين إلى المرفقات

بعد أن تقوم Microsoft بتشفير رسالة، يكون لدى المستلمين وصول غير مقيد إلى المرفقات عند الوصول إلى البريد الإلكتروني المشفر وفتحه.

## <a name="to-prepare-for-this-change"></a>للتحضير لهذا التغيير

قد ترغب في تحديث أي وثائق مستخدم نهائي قابلة للتطبيق ومواد تدريبية لإعداد الأشخاص في مؤسستك لهذا التغيير. شارك موارد تشفير الرسائل Office 365 هذه مع المستخدمين حسب الاقتضاء:

- [إرسال الرسائل المشفرة وعرضها والرد عليها في Outlook للكمبيوتر الشخصي](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [فيديو Microsoft 365 Essentials: تشفير الرسائل](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>عرض هذه التغييرات في سجل التدقيق

Microsoft 365 تدقيق هذا النشاط وإتاحته للمسؤولين. العملية هي "New-TransportRule" ومقتطف من إدخال تدقيق عينة من البحث في سجل التدقيق في Security & Compliance Center أدناه:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"...etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>لتعطيل نهج أنواع المعلومات الحساسة أو تخصيصه

بمجرد إنشاء قاعدة تدفق البريد Exchange، يمكنك [تعطيل القاعدة أو تحريرها](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) عن طريق الانتقال إلى **"قواعد** **تدفق** >  البريد" في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> وتعطيل القاعدة "*تشفير رسائل البريد الإلكتروني الحساسة الصادرة (قاعدة خارج الصندوق)*".
