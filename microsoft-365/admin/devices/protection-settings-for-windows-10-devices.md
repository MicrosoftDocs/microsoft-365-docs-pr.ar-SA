---
title: تحرير إعدادات حماية التطبيقات أو تعيينها Windows 10 الأجهزة
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: تعرف على كيفية إنشاء سياسات إدارة التطبيقات أو تحريرها وحماية ملفات العمل على أجهزة المستخدمين Windows 10 الشخصية.
ms.openlocfilehash: 3a565586be4d0dfec308b2dad3b068e01774b161
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579717"
---
# <a name="set-or-edit-application-protection-settings-for-windows-10-devices"></a>تعيين إعدادات حماية التطبيقات أو تحريرها Windows 10 الأجهزة

تنطبق هذه المقالة على Microsoft 365 Business Premium.

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="edit-an-app-management-policy-for-windows-10"></a>تحرير نهج إدارة تطبيق Windows 10

1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     
2. على الجانب الأيسر من التنقل، اختر **"سياسات** \> **الأجهزة".**
1. اختر نهج تطبيق Windows ثم **تحرير**.
1. اختر **تحرير** بجانب إعداد تريد تغييره، ثم **حفظ**.

## <a name="create-an-app-management-policy-for-windows-10"></a>إنشاء نهج إدارة تطبيق Windows 10

إذا كان لدى المستخدمين Windows 10 الشخصية التي ينفذون عليها مهام العمل، يمكنك حماية بياناتك على هذه الأجهزة أيضا.
  
1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
2. على الجانب الأيسر من التنقل، اختر **إضافة** \> **سياسات** \> **الأجهزة**.
3. في الجزء **إضافة نهج** ، أدخل اسما فريدا لهذا النهج. 
4. ضمن **نوع النهج**، اختر **إدارة التطبيقات Windows 10**.
5. ضمن **نوع الجهاز**، اختر **شخصي** أو **شركة مملوكة**.
6. يتم **تشغيل تشفير** ملفات العمل تلقائيا. 
7. تعيين **منع المستخدمين** من نسخ بيانات الشركة إلى الملفات الشخصية وإجبارهم على حفظ ملفات العمل OneDrive for Business إلى **تشغيل** إذا كنت لا تريد أن يقوم المستخدمون بحفظ ملفات العمل على أجهزة الكمبيوتر الخاصة بهم. 
9. توسيع **استرداد البيانات على Windows الأجهزة**. نوصيك بتب **تشغيلها**.
    قبل أن تتمكن من الاستعراض إلى موقع شهادة عامل استرداد البيانات، يجب أولا إنشاء واحدة. للحصول على الإرشادات، راجع إنشاء شهادة عامل استرداد البيانات [(DRA) لنظام تشفير الملفات (EFS) والتحقق منها](/windows/security/information-protection/windows-information-protection/create-and-verify-an-efs-dra-certificate).
    
    بشكل افتراضي، يتم تشفير ملفات العمل باستخدام مفتاح سري مخزن على الجهاز ومقترن بملف تعريف المستخدم. يمكن للمستخدم فقط فتح الملف وفك تشفيره. ومع ذلك، إذا فقد جهاز أو تمت إزالة مستخدم، يمكن أن يكون الملف عالقا في حالة مشفرة. يمكن للمسؤول استخدام شهادة وكيل استرداد البيانات (DRA) لفك تشفير الملف.
    
    ![استعرض بحثا عن شهادة عامل استرداد البيانات.](../../media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. قم **بتوسيع حماية مواقع** الشبكة والسحابة الإضافية إذا كنت تريد إضافة مجالات إضافية أو SharePoint مواقع عبر الإنترنت للتأكد من حماية الملفات الموجودة في جميع التطبيقات المدرجة. إذا كنت بحاجة إلى إدخال أكثر من عنصر واحد لأحد الحقلين، فاستخدم فات من ;) بين العناصر.
    
    ![قم بتوسيع حماية مواقع الشبكة والسحابة الإضافية، وأدخل المجالات أو SharePoint المواقع عبر الإنترنت التي تملكها.](../../media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. هل تقرر **روبوت Who ستحصل على هذه الإعدادات؟** إذا كنت لا تريد استخدام مجموعة أمان جميع المستخدمين  الافتراضية، فاختر تغيير، واختر مجموعات الأمان التي ستحصل على هذه الإعدادات \> **حدد**.
12. وأخيرا، **اختر إضافة** لحفظ النهج وتعيينه إلى الأجهزة.

## <a name="see-also"></a>راجع أيضًا

[أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](../security-and-compliance/secure-your-business-data.md)