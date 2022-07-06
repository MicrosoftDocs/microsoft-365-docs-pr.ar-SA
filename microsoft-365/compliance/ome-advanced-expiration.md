---
title: تعيين تاريخ انتهاء صلاحية للبريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم من Microsoft Purview
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
description: استخدم Microsoft Purview Advanced Message Encryption لتوسيع أمان البريد الإلكتروني عن طريق تعيين تاريخ انتهاء صلاحية على رسائل البريد الإلكتروني من خلال قالب مخصص له علامة تجارية.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b93aad4f217f956561b686b1415c64456a4360db
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635140"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-microsoft-purview-advanced-message-encryption"></a>تعيين تاريخ انتهاء صلاحية للبريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم من Microsoft Purview

يتم تضمين تشفير الرسائل المتقدم ل Microsoft Purview في [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home)، Office 365 E5، Microsoft 365 E5 (تسعير الموظفين غير الربحي)، Office 365 Enterprise E5 (تسعير الموظفين غير الربحي)، و Office 365 Education A5. التوافق في Microsoft 365 E5 وظيفة SKU الإضافية Microsoft 365 E3 أو Microsoft 365 E3 (تسعير الموظفين غير الربحي) أو الوظيفة الإضافية خدمات الامتثال المتطورة في Office 365 SKU ل Microsoft 365 E3 أو Microsoft 365 E3 (أسعار الموظفين غير الربحية) أو Office 365 وحدات SKU.

إذا كان لدى مؤسستك اشتراك لا يتضمن تشفير الرسائل المتقدمة من Microsoft Purview، يمكنك شراؤه باستخدام الوظيفة الإضافية التوافق في Microsoft 365 E5 SKU Microsoft 365 E3 أو Microsoft 365 E3 (تسعير الموظفين غير الربحي) أو خدمات الامتثال المتطورة في Office 365 وظيفة SKU الإضافية لوحدات Microsoft 365 E3 أو Microsoft 365 E3 (أسعار الموظفين غير الربحية) أو وحدات SKU Office 365.

يمكنك استخدام انتهاء صلاحية الرسالة على رسائل البريد الإلكتروني التي يرسلها المستخدمون إلى مستلمين خارجيين يستخدمون مدخل OME للوصول إلى رسائل البريد الإلكتروني المشفرة. يجبر المستلمين على استخدام مدخل OME لعرض رسائل البريد الإلكتروني المشفرة المرسلة من مؤسستك والرد عليها باستخدام قالب مخصص له علامة تجارية يحدد تاريخ انتهاء الصلاحية في PowerShell.

بصفتك مسؤولا عاما Office 365، عند تطبيق العلامة التجارية للشركة لتخصيص مظهر رسائل البريد الإلكتروني الخاصة بمؤسستك، يمكنك أيضا تحديد انتهاء صلاحية لرسائل البريد الإلكتروني هذه. باستخدام Microsoft Purview Advanced Message Encryption، يمكنك إنشاء قوالب متعددة لرسائل البريد الإلكتروني المشفرة التي تنشأ من مؤسستك. باستخدام قالب، يمكنك التحكم في مدة وصول المستلمين إلى البريد المرسل من قبل المستخدمين.

عندما يتلقى مستخدم نهائي بريدا يحتوي على تاريخ انتهاء صلاحية معين، يرى المستخدم تاريخ انتهاء الصلاحية في البريد الإلكتروني للملف. إذا حاول مستخدم فتح بريد منتهي الصلاحية، يظهر خطأ في مدخل OME.

يمكنك فقط تعيين تواريخ انتهاء الصلاحية لرسائل البريد الإلكتروني إلى مستلمين خارجيين.

باستخدام Microsoft Purview Advanced Message Encryption، في أي وقت تقوم فيه بتطبيق العلامة التجارية المخصصة، يطبق Office 365 برنامج التضمين على البريد الإلكتروني الذي يناسب قاعدة تدفق البريد التي تقوم بتطبيق القالب عليها. بالإضافة إلى ذلك، يمكنك استخدام انتهاء الصلاحية فقط إذا كنت تستخدم العلامة التجارية المخصصة.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>إنشاء قالب علامة تجارية مخصص لفرض انتهاء صلاحية البريد باستخدام PowerShell

1. [اتصل Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام حساب لديه أذونات المسؤول العام في مؤسستك.

2. تشغيل New-OMEConfiguration cmdlet.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

المكان:

- `Identity` هو اسم القالب المخصص.

- `ExternalMailExpiryInDays` يحدد عدد الأيام التي يمكن للمستلمين الاحتفاظ بها قبل انتهاء صلاحيتها. يمكنك استخدام أي قيمة بين يوم و730 يوما.

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>مزيد من المعلومات حول تشفير الرسائل المتقدم ل Microsoft Purview

- [تشفير الرسائل المتقدم](ome-advanced-message-encryption.md)

- [إبطال البريد الإلكتروني المشفر بواسطة تشفير رسائل Microsoft Purview](revoke-ome-encrypted-mail.md)

- [نهج الرسالة ووصف خدمة التوافق](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
