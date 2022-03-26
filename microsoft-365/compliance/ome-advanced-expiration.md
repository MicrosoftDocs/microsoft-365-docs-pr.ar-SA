---
title: تعيين تاريخ انتهاء صلاحية للبريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم من Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/8/2019
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: استخدم تشفير الرسائل المتقدم من Office 365 لتوسيع أمان البريد الإلكتروني من خلال تعيين تاريخ انتهاء صلاحية على رسائل البريد الإلكتروني من خلال قالب مخصص له علامة تجارية.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1213ecf48ee9bd2e04accdd13aaf3ecd74d3faba
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566557"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-office-365-advanced-message-encryption"></a>تعيين تاريخ انتهاء صلاحية للبريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم من Office 365

تشفير الرسائل المتقدم من Office 365 في [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home)، Office 365 E5، Microsoft 365 E5 (أسعار الموظفين غير الربحية)، Office 365 Enterprise  E5 (أسعار الموظفين غير الربحية)، Office 365 Education A5. إذا كانت مؤسستك لديها اشتراك لا يتضمن تشفير الرسائل المتقدم من Office 365، يمكنك شراؤه باستخدام التوافق في Microsoft 365 E5 SKU الإضافية ل Microsoft 365 E3، Microsoft 365 E3 ( أسعار الموظفين غير الربحية) أو خدمات الامتثال المتطورة في Office 365 SKU الإضافية Microsoft 365 E3 أو Microsoft 365 E3 (أسعار الموظفين غير الربحية) أو Office 365 SKU.

يمكنك استخدام انتهاء صلاحية الرسائل في رسائل البريد الإلكتروني التي يرسلها المستخدمون إلى مستلمين خارجيين يستخدمون مدخل OME للوصول إلى رسائل البريد الإلكتروني المشفرة. يجبر المستلمين على استخدام مدخل OME لعرض رسائل البريد الإلكتروني المشفرة المرسلة بواسطة مؤسستك والرد عليها باستخدام قالب مخصص له علامة تجارية يحدد تاريخ انتهاء الصلاحية في Windows PowerShell.

كمسؤول Office 365 عام، عند تطبيق العلامة التجارية للشركة لتخصيص مظهر رسائل البريد الإلكتروني الخاصة بالشركة، يمكنك أيضا تحديد انتهاء صلاحية لرسائل البريد الإلكتروني هذه. باستخدام تشفير الرسائل المتقدم من Office 365، يمكنك إنشاء قوالب متعددة لر رسائل البريد الإلكتروني المشفرة التي تنشأ من مؤسستك. باستخدام قالب، يمكنك التحكم في مدة وصول المستلمين إلى البريد المرسل من قبل المستخدمين.

عندما يتلقى مستخدم بريدا له مجموعة تاريخ انتهاء صلاحية، يرى المستخدم تاريخ انتهاء الصلاحية في البريد الإلكتروني الملتف. إذا حاول مستخدم فتح بريد منتهية الصلاحية، يظهر خطأ في مدخل OME.

يمكنك فقط تعيين تواريخ انتهاء صلاحية رسائل البريد الإلكتروني إلى مستلمين خارجيين.

باستخدام تشفير الرسائل المتقدم من Office 365، في أي وقت تقوم فيه بتطبيق العلامة التجارية المخصصة، Office 365 تطبيق الملتف على البريد الإلكتروني الذي يتلاءم مع قاعدة تدفق البريد التي تقوم بتطبيق القالب عليها. بالإضافة إلى ذلك، يمكنك استخدام انتهاء الصلاحية فقط إذا كنت تستخدم علامة تجارية مخصصة.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>إنشاء قالب علامة تجارية مخصص فرض انتهاء صلاحية البريد باستخدام PowerShell

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام حساب لديه أذونات المسؤول العام في مؤسستك.

2. تشغيل New-OMEConfiguration cmdlet.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

المكان:

- `Identity` هو اسم القالب المخصص.

- `ExternalMailExpiryInDays` يحدد عدد الأيام التي يمكن للمستلمين الاحتفاظ بالبريد قبل انتهاء صلاحيتها. يمكنك استخدام أي قيمة تتراوح بين يوم و730 يوما.

## <a name="more-information-about-office-365-advanced-message-encryption"></a>مزيد من المعلومات حول تشفير الرسائل المتقدم من Office 365

- [تشفير الرسائل المتقدم من Office 365](ome-advanced-message-encryption.md)

- [إبطال البريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم من Office 365](revoke-ome-encrypted-mail.md)

- [وصف خدمة التوافق ون نهج الرسالة](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)