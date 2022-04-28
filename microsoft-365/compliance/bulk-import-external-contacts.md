---
title: استيراد جهات اتصال خارجية بشكل مجمع إلى Exchange Online
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 6/29/2018
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
ms.custom: admindeeplinkEXCHANGE
description: تعرف على كيفية استخدام المسؤولين Exchange Online PowerShell وملف CSV لاستيراد جهات الاتصال الخارجية بشكل مجمع إلى قائمة العناوين العمومية.
ms.openlocfilehash: 5e80453326159010aaae81a8b810396f5a7294cf
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093537"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>استيراد جهات اتصال خارجية بشكل مجمع إلى Exchange Online

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**هذه المقالة مخصصة للمسؤولين. هل تحاول استيراد جهات الاتصال إلى علبة بريدك؟ راجع [استيراد جهات الاتصال إلى Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
هل لدى شركتك الكثير من جهات الاتصال المهنية الموجودة التي تريد تضمينها في دفتر العناوين المشترك (تسمى أيضا قائمة العناوين العمومية) في Exchange Online؟ هل تريد إضافة جهات اتصال خارجية كأعضاء في مجموعات التوزيع، تماما كما تفعل مع المستخدمين داخل شركتك؟ إذا كان الأمر كذلك، يمكنك استخدام Exchange Online PowerShell وملف CSV (قيمة مفصولة بفواصل) لاستيراد جهات الاتصال الخارجية بشكل مجمع إلى Exchange Online. إنها عملية مكونة من ثلاث خطوات:
  
[الخطوة 1: إنشاء ملف CSV يحتوي على معلومات حول جهات الاتصال الخارجية](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[الخطوة 2: إنشاء جهات الاتصال الخارجية باستخدام PowerShell](#step-2-create-the-external-contacts-with-powershell) 

[الخطوة 3: إضافة معلومات إلى خصائص جهات الاتصال الخارجية](#step-3-add-information-to-the-properties-of-the-external-contacts)

بعد إكمال هذه الخطوات لاستيراد جهات الاتصال، يمكنك تنفيذ هذه المهام الإضافية:
  
- [إضافة المزيد من جهات الاتصال الخارجية](#add-more-external-contacts)
  
- [إخفاء جهات الاتصال الخارجية من دفتر العناوين المشترك](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>الخطوة 1: إنشاء ملف CSV يحتوي على معلومات حول جهات الاتصال الخارجية

الخطوة الأولى هي إنشاء ملف CSV يحتوي على معلومات حول كل جهة اتصال خارجية تريد استيرادها إلى Exchange Online. 
  
1. انسخ النص التالي إلى ملف نصي في NotePad، واحفظه على سطح المكتب كملف CSV باستخدام لاحقة اسم الملف .csv; على سبيل المثال، ExternalContacts.csv.
    
    > [!TIP]
    > إذا كانت لغتك تحتوي على أحرف خاصة (مثل **å** **وä** **وö** باللغة السويدية) فاحفظ ملف CSV مع ترميز UTF-8 أو ترميز Unicode آخر عند حفظ الملف في NotePad. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    يسرد الصف الأول أو صف الرأس لملف CSV خصائص جهات الاتصال التي يمكن استخدامها عند استيرادها إلى Exchange Online. يتم فصل كل اسم خاصية بفواصل. يمثل كل صف أسفل صف الرأس قيم الخصائص لاستيراد جهة اتصال خارجية واحدة. 
    
    > [!NOTE]
    > يتضمن هذا النص بيانات نموذجية، والتي يمكنك حذفها. ولكن لا تحذف الصف الأول (الرأس) أو تغيره. يحتوي على كافة خصائص جهات الاتصال الخارجية. 
  
2. افتح ملف CSV في Microsoft Excel لتحرير ملف CSV لأنه من الأسهل استخدام Excel لتحرير ملف CSV.
    
3. أنشئ صفا لكل جهة اتصال تريد استيرادها إلى Exchange Online. ملء أكبر عدد ممكن من الخلايا. سيتم عرض هذه المعلومات في دفتر العناوين المشترك لكل جهة اتصال. 
    
    > [!IMPORTANT]
    >  الخصائص التالية (وهي العناصر الأربعة الأولى في صف الرأس) مطلوبة لإنشاء جهة اتصال خارجية ويجب ملؤها في ملف CSV: **ExternalEmailAddress**، **والاسم**، **والاسم الأول**، واسم **العائلة**. سيستخدم أمر PowerShell الذي تقوم بتشغيله في الخطوة 2 قيم هذه الخصائص لإنشاء جهات الاتصال. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>الخطوة 2: إنشاء جهات الاتصال الخارجية باستخدام PowerShell

الخطوة التالية هي استخدام ملف CSV الذي قمت بإنشائه في الخطوة 1 وPowerShell لاستيراد جهات الاتصال الخارجية المدرجة في ملف CSV بشكل مجمع إلى Exchange Online. 
  
1.  الاتصال PowerShell إلى مؤسستك Exchange Online. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). تأكد من استخدام اسم المستخدم وكلمة المرور لحساب المسؤول العام عند الاتصال Exchange Online PowerShell. 
    
2. بعد توصيل PowerShell Exchange Online، انتقل إلى مجلد سطح المكتب حيث قمت بحفظ ملف CSV في الخطوة 1؛ على سبيل المثال`C:\Users\Administrator\desktop`.
    
3. قم بتشغيل الأمر التالي لإنشاء جهات الاتصال الخارجية:

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    قد يستغرق إنشاء جهات الاتصال الجديدة بعض الوقت، استنادا إلى عدد جهات الاتصال التي تقوم باستيرادها. عند الانتهاء من تشغيل الأمر، يعرض PowerShell قائمة بجهات الاتصال الجديدة التي تم إنشاؤها. 
    
4. لعرض جهات الاتصال الخارجية الجديدة، انتقل إلى مركز إدارة Exchange (EAC)، ثم انقر فوق <a href="https://go.microsoft.com/fwlink/?linkid=2182970" target="_blank">**"جهات اتصال المستلمين**</a>\>". 
    
    > [!TIP]
    > للحصول على إرشادات الاتصال ب EAC، راجع [مركز إدارة Exchange في Exchange Online](/exchange/exchange-admin-center). 
  
5. إذا لزم الأمر، انقر فوق **"تحديث** " لتحديث القائمة والاطلاع على جهات الاتصال الخارجية التي تم استيرادها. 
    
    ستظهر جهات الاتصال المستوردة في دفتر العناوين المشترك في Outlook Outlook على ويب.
    
    > [!NOTE]
    > يمكنك أيضا عرض جهات الاتصال في مركز مسؤولي Microsoft 365 بالانتقال إلى **"جهات اتصال** **المستخدمين**\>". 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>الخطوة 3: إضافة معلومات إلى خصائص جهات الاتصال الخارجية

بعد تشغيل الأمر في الخطوة 2، يتم إنشاء جهات الاتصال الخارجية، ولكنها لا تحتوي على أي من معلومات جهة الاتصال أو المؤسسة، وهي المعلومات الواردة من معظم الخلايا في ملف CSV. وذلك لأنه عند إنشاء جهات اتصال خارجية جديدة، يتم ملء الخصائص المطلوبة فقط. لا تقلق إذا لم يكن لديك كافة المعلومات التي تم ملؤها في ملف CSV. إذا لم يكن موجودا، فلن تتم إضافته.
  
1.  الاتصال PowerShell إلى مؤسستك Exchange Online. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. انتقل إلى مجلد سطح المكتب حيث حفظت ملف CSV في الخطوة 1؛ على سبيل المثال، `C:\Users\Administrator\desktop`.
    
3. قم بتشغيل الأمرين التاليين لإضافة الخصائص الأخرى من ملف CSV إلى جهات الاتصال الخارجية التي قمت بإنشائها في الخطوة 2.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > قد تكون معلمة  _Manager_ مشكلة. إذا كانت الخلية فارغة في ملف CSV، فستحصل على خطأ ولن تتم إضافة أي من معلومات الخاصية إلى جهة الاتصال. إذا لم تكن بحاجة إلى تحديد مدير، فما عليك سوى الحذف  ` -Manager $_.Manager ` من أمر PowerShell السابق. 
  
    مرة أخرى، قد يستغرق تحديث جهات الاتصال بعض الوقت، استنادا إلى عدد جهات الاتصال التي قمت باستيرادها في الخطوة 1. 
    
4. للتحقق من إضافة الخصائص إلى جهات الاتصال: 
    
1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>، انتقل إلى **جهات اتصال المستلمين**\>.
    
2. انقر فوق جهة اتصال ثم انقر فوق **أيقونة تحرير**![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) لعرض خصائص جهة الاتصال. 
    
هذا هو! يمكن للمستخدمين رؤية جهات الاتصال والمعلومات الإضافية في Outlook دفتر العناوين Outlook على ويب.
  
## <a name="add-more-external-contacts"></a>إضافة المزيد من جهات الاتصال الخارجية

يمكنك تكرار الخطوات من 1 إلى الخطوة 3 لإضافة جهات اتصال خارجية جديدة في Exchange Online. يمكنك أنت أو المستخدمون في شركتك إضافة صف جديد فقط في ملف CSV لجهة الاتصال الجديدة. ثم يمكنك تشغيل أوامر PowerShell من الخطوة 2 والخطوة 3 لإنشاء معلومات وإضافتها إلى جهات الاتصال الجديدة.
  
> [!NOTE]
> عند تشغيل الأمر لإنشاء جهات اتصال جديدة، قد تظهر رسالة خطأ تفيد بأن جهات الاتصال التي تم إنشاؤها مسبقا موجودة بالفعل. ولكن يتم إنشاء أي جهة اتصال جديدة تمت إضافتها إلى ملف CSV. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>إخفاء جهات الاتصال الخارجية من دفتر العناوين المشترك>

قد تستخدم بعض الشركات جهات الاتصال الخارجية فقط بحيث يمكن إضافتها كأعضاء في مجموعات التوزيع. في هذا السيناريو، قد يرغبون في إخفاء جهات الاتصال الخارجية من دفتر العناوين المشترك. إليك كيفية تنفيذ ذلك:
  
1.  الاتصال PowerShell إلى مؤسستك Exchange Online. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. لإخفاء جهة اتصال خارجية واحدة، قم بتشغيل الأمر التالي.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    على سبيل المثال، لإخفاء Pilar Pinilla من دفتر العناوين المشترك، قم بتشغيل هذا الأمر:

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. لإخفاء كافة جهات الاتصال الخارجية من دفتر العناوين المشترك، قم بتشغيل هذا الأمر:

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

بعد إخفائها، لا يتم عرض جهات الاتصال الخارجية في دفتر العناوين المشترك، ولكن لا يزال بإمكانك إضافتها كأعضاء في مجموعة توزيع.