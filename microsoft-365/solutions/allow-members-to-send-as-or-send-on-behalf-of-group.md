---
title: السماح للأعضاء بإرسال ك أو إرسال نيابة عن مجموعة
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
recommendations: false
description: تعرف على كيفية السماح لأعضاء المجموعة بإرسال بريد إلكتروني كمجموعة Microsoft 365 أو إرسال بريد إلكتروني نيابة عن مجموعة Microsoft 365 أخرى.
ms.openlocfilehash: 588008669359629f5b59498bb7dbf776112d5408
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63576881"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>السماح للأعضاء بإرسال ك أو إرسال نيابة عن مجموعة

يمكن أن يرسل عضو مجموعة Microsoft 365 تم منحه أذونات إرسال باسم أو  إرسال نيابة عنه  بريدا إلكترونيا كمجموعة، أو بالنيابة عن المجموعة. (لا يمكن منح الضيوف في المجموعة هذه الأذونات.)

تشرح هذه المقالة كيف يمكن للمسؤول العام أو المسؤول Exchange تعيين هذه الأذونات.
  
على سبيل المثال، إذا كانت ميغان بوين جزءا من مجموعة **التدريب Microsoft 365،** وكان لديها أذونات إرسال ك  في المجموعة، إذا أرسلت بريدا إلكترونيا كمجموعة، سيبدو الأمر مثل المجموعة التدريبية التي أرسلت البريد الإلكتروني. 
  
يتيح **الإذن "إرسال** نيابة عن" للمستخدم إرسال بريد إلكتروني نيابة عن مجموعة Microsoft 365 أخرى. على سبيل المثال، إذا كان Alex Wilber جزءا من مجموعة **التسويق Microsoft 365،** وكان لديه أذونات "إرسال نيابة  عن" وأرسل بريدا إلكترونيا كمجموعة، يبدو أن البريد الإلكتروني تم إرساله بواسطة **Alex Wilber** نيابة عن التسويق.

> [!IMPORTANT]
> يمكنك تكوين إرسال **باسم** أو **إرسال** نيابة عن مستخدم معين، وليس كليهما. إذا قمت بتكوين كليهما، سيتم تعيين الخيار "إرسال باسم" **بشكل افتراضي**.

> [!NOTE]
> **لا يتم** دعم **"** إرسال باسم" و"إرسال نيابة عن" Outlook for Mac في تكوينات Exchange المختلطة.
    
## <a name="allow-members-to-send-email-as-a-group"></a>السماح للأعضاء بإرسال البريد الإلكتروني كمجموعة

يشرح هذا القسم كيفية السماح للمستخدمين بإرسال البريد الإلكتروني كمجموعة في مركز إدارة Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">(EAC)</a> في Exchange Online.
  
1. في مركز Exchange، انتقل إلى **مجموعات المستلمين**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. حدد المجموعة التي تريد السماح للمستخدمين بإرسالها باسم. 
    
3. حدد **الإعدادات** >  **إدارة المفوضين**.
    
4. في المقطع **إضافة مفوض** ، أدخل عنوان البريد الإلكتروني للمستخدم الذي ترغب في الحصول على **إرسال كالوصول** إليه.
  
5. حدد **نوع الإذن** ك **إرسال باسم** من المنسدل.

6.  حدد **حفظ التغييرات**.
    
    
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>السماح للأعضاء بإرسال البريد الإلكتروني نيابة عن مجموعة

يشرح هذا القسم كيفية السماح للمستخدمين بإرسال بريد إلكتروني نيابة عن مجموعة في مركز إدارة Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">(EAC)</a> في Exchange Online.
  
1. في مركز Exchange، انتقل إلى **مجموعات المستلمين**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. حدد المجموعة التي تريد السماح للمستخدمين بإرسالها بالنيابة عنها. 
    
3. حدد **الإعدادات** >  **إدارة المفوضين**.
    
4. في المقطع **إضافة مفوض** ، أدخل عنوان البريد الإلكتروني للمستخدم الذي ترغب في الحصول على **إرسال كالوصول** إليه.
  
5. حدد **نوع الإذن** ك **إرسال نيابة** عن منسدل.

6.  حدد **حفظ التغييرات**.

## <a name="related-articles"></a>المقالات ذات الصلة

[إرسال بريد إلكتروني من مجموعة Microsoft 365 أو بالنيابة عنها](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[معرفة المزيد حول Microsoft 365 المجموعات](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)
