---
title: تحرير إعدادات حماية التطبيقات أو تعيينها لأجهزة Windows
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
f1.keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection: ''
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية إنشاء نهج إدارة التطبيقات أو تحريرها وحماية ملفات العمل على أجهزة Windows الشخصية للمستخدمين.
ms.openlocfilehash: d02b406f98aadcaaf21005686212b4da9e4fac2c
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893912"
---
# <a name="set-or-edit-application-protection-settings-for-windows-devices"></a>تعيين إعدادات حماية التطبيقات أو تحريرها لأجهزة Windows

تحتاج الآن إلى إعداد نهج حماية التطبيقات لأجهزة Windows الخاصة بمؤسستك لضمان حماية جميع المستخدمين عند استخدام التطبيقات لعملهم.

## <a name="edit-an-app-management-policy-for-windows-devices"></a>تحرير نهج إدارة التطبيقات لأجهزة Windows

1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     

2. في جزء التنقل الأيمن، اختر **"نهج الأجهزة**\>".

3. اختر نهج تطبيق Windows الموجود ثم **قم بالتحرير**.

4. اختر **"تحرير"** إلى جانب إعداد تريد تغييره ثم **"حفظ**".

## <a name="create-an-app-management-policy-for-windows-devices"></a>إنشاء نهج إدارة التطبيقات لأجهزة Windows

إذا كان لدى المستخدمين أجهزة Windows شخصية يقومون بتنفيذ مهام العمل عليها، يمكنك حماية بياناتك على تلك الأجهزة.
  
1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 

2. في جزء التنقل الأيمن، اختر **"إضافة** **نهج** \> **الأجهزة**\>".

3. في جزء **"إضافة نهج** "، أدخل اسما فريدا لهذا النهج. 

4. ضمن **نوع النهج**، اختر **إدارة التطبيقات Windows 10**.

5. ضمن **نوع الجهاز**، اختر " **شخصي** " أو **"مملوك للشركة**".

6. يتم تشغيل **ملفات عمل التشفير** تلقائيا. 

7. قم بتعيين **منع المستخدمين من نسخ بيانات الشركة إلى الملفات الشخصية وإجبارهم على حفظ ملفات العمل إلى OneDrive for Business** إلى **"تشغيل**" إذا كنت لا تريد أن يقوم المستخدمون بحفظ ملفات العمل على أجهزة الكمبيوتر الخاصة بهم. 

8. توسيع **استرداد البيانات على أجهزة Windows**. نوصي **بتشغيله.**
    قبل أن تتمكن من الاستعراض وصولا إلى موقع شهادة عامل استرداد البيانات، يجب عليك أولا إنشاء واحد. للحصول على الإرشادات، راجع [إنشاء شهادة عامل استرداد البيانات (DRA) لنظام الملفات المشفر (EFS) والتحقق منها](/windows/security/information-protection/windows-information-protection/create-and-verify-an-efs-dra-certificate).

    بشكل افتراضي، يتم تشفير ملفات العمل باستخدام مفتاح سري يتم تخزينه على الجهاز ومقترن بملف تعريف المستخدم. يمكن للمستخدم فقط فتح الملف وفك تشفيره. ومع ذلك، إذا فقدت جهازا أو تمت إزالة مستخدم، يمكن أن يكون الملف عالقا في حالة مشفرة. يمكن للمسؤول استخدام شهادة عامل استرداد البيانات (DRA) لفك تشفير الملف.

    ![استعرض للوصول إلى شهادة عامل استرداد البيانات.](./../media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
9. قم بتوسيع **"حماية" مواقع إضافية للشبكات والسحابة** إذا كنت تريد إضافة مجالات إضافية أو مواقع SharePoint Online للتأكد من حماية الملفات الموجودة في جميع التطبيقات المدرجة. إذا كنت بحاجة إلى إدخال أكثر من عنصر واحد لأي من الحقلين، فاستخدم فاصلة منقوطة (;) بين العناصر.

    ![قم بتوسيع حماية مواقع إضافية للشبكة والسحابة، وأدخل المجالات أو مواقع SharePoint Online التي تملكها.](./../media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
10. بعد ذلك، حدد **من سيحصل على هذه الإعدادات؟** إذا كنت لا تريد استخدام مجموعة أمان **كافة المستخدمين** الافتراضية، فاختر **"تغيير**"، واختر مجموعات الأمان التي ستحصل على هذه الإعدادات \> **"تحديد**".
11. وأخيرا، اختر **"إضافة** " لحفظ النهج وتعيينه إلى الأجهزة.

## <a name="see-also"></a>راجع أيضًا

[أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>الهدف التالي

[التحقق من صحة إعدادات Windows](m365bp-validate-settings-on-windows-10-pcs.md).