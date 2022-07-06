---
title: كيفية تحديد المحتوى لتوصيات إدارة البيانات
f1.keywords:
- NOCSH
ms.author: brendonb
author: cabailey
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.custom: admindeeplinkDEFENDER
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: يوفر مدخل Microsoft 365 Defender مدخل التوافق في Microsoft Purview توصيات لإدارة البيانات استنادا إلى الإعداد الحالي لمؤسستك ويسمح لك بإعداد الأشياء ببضع نقرات. تكتشف بعض هذه التوصيات محتوى محددا في مؤسستك ثم توفر خطوات موصى بها لإدارة هذا المحتوى. على سبيل المثال، قد تكتشف التوصية العناصر التي تحتوي على محتوى مهم للأعمال (مثل امتياز الوكيل والعميل أو معلومات NDA)، ثم تسمح لك بتطبيق تسمية استبقاء على تلك العناصر تلقائيا للتأكد من تصنيفها والاحتفاظ بها حسب الحاجة. يسرد هذا الموضوع توصيات إدارة البيانات التي قد تراها ويصف المحتوى الذي تم اكتشافه لتشغيل كل منها.
ms.openlocfilehash: 27fcc5dd07695be355fc15ba2145ffa5540673ca
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637296"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>كيفية تحديد المحتوى لتوصيات إدارة البيانات

يوفر <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a> توصيات لإدارة البيانات استنادا إلى الإعداد الحالي لمؤسستك ويسمح لك بإعداد الأمور ببضع نقرات. تكتشف بعض هذه التوصيات محتوى محددا في مؤسستك ثم توفر خطوات موصى بها لإدارة هذا المحتوى. على سبيل المثال، قد تكتشف التوصية العناصر التي تحتوي على محتوى مهم للأعمال (مثل امتياز الوكيل والعميل أو معلومات NDA)، ثم تسمح لك بتطبيق تسمية استبقاء على تلك العناصر تلقائيا للتأكد من تصنيفها والاحتفاظ بها حسب الحاجة.

يسرد هذا الموضوع توصيات إدارة البيانات التي قد تراها ويصف المحتوى الذي تم اكتشافه لتشغيل كل منها.

## <a name="clean-up-voicemail"></a>تنظيف البريد الصوتي

تظهر هذه التوصية عند الكشف عن رسائل البريد الإلكتروني التي تم تعريفها كنوع الرسالة "البريد الصوتي" في علب بريد المستخدمين. تعرف على المزيد حول [خصائص الرسالة في Exchange](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>تسمية محتوى امتياز الوكيل والعميل

تظهر هذه التوصية عند استيفاء أي من المعايير التالية.

- يتم الكشف عن أي تركيبة من هذه الكلمات الأساسية في النص الأساسي لرسالة بريد إلكتروني:
  - ACP
  - امتياز عميل الوكيل
  - امتياز Attorney-Client
  - Attorney-Client متميز

- يتم الكشف عن أي تركيبة من هذه الكلمات الأساسية في ملفات SharePoint أو OneDrive:
  - ACP
  - امتياز عميل الوكيل*
  - امتياز التيار المتردد

## <a name="retain-audio-files"></a>الاحتفاظ بالملفات الصوتية

تظهر هذه التوصية عند الكشف عن أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- .MP3
- . الاب
- . الرعايا
- . را
- . ذاكره الوصول العشوائي
- .RM
- . منتصف
- . سطين
- . ايف
- . PCM
- . AAC
- . فلك
- . ALAC

## <a name="retain-cad-files"></a>الاحتفاظ بملفات CAD

تظهر هذه التوصية عند الكشف عن أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- .3DXML
- . ACIS
- . قوس
- . ASM
- .CAT*
- . CGR
- . DW*
- . DX*
- . EDRW
- . IAM
- . IGES
- . IGS
- . IPT
- . جي تي
- . MF1
- . نوي
- . قدم المساواه
- . PKG
- . PRC
- . PRT
- . PSM
- . PWD
- . SLD*
- . خطوه
- . STL
- . STP
- . U3D
- . UNV
- . VRML
- . WRL
- . X_*
- . XAS
- . XMT*
- . XPR

## <a name="retain-image-files"></a>الاحتفاظ بملفات الصور

تظهر هذه التوصية عند الكشف عن أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- . JPEG
- .GIF
- . TIF*
- .BMP
- .PNG
- . الخام
- .PSD
- . PSP
- .JPG
- . EXIF
- . المليون
- . PGM
- . PBM
- . PNM
- . WEBP

## <a name="retain-nda-content"></a>الاحتفاظ بمحتوى NDA

تظهر هذه التوصية عند استيفاء أي من المعايير التالية.

- يتم الكشف عن أي تركيبة من هذه الكلمات الأساسية في النص الأساسي لرسالة بريد إلكتروني:
  - التجمع الوطني الديمقراطي
  - "اتفاقية عدم الكشف"
  - "اتفاقية عدم الكشف"

- يتم الكشف عن أي مجموعة من هذه الكلمات الأساسية في ملفات .PDF أو .DOC في SharePoint أو OneDrive:
  - التجمع الوطني الديمقراطي
  - اتفاقية عدم الكشف

## <a name="retain-software-development-files"></a>الاحتفاظ بملفات تطوير البرامج

تظهر هذه التوصية عند الكشف عن أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- .CS
- . المغلق
- . ديسكو
- .HTM*
- . شركه
- . جاد
- . جافا
- .JS*
- . LIB
- . يا
- . PHP
- . اتفاقيه روتردام
- . RESX
- . RPT
- . ار اس اس
- . SCPT
- . SRC
- . VB*
- . WSF
- . XCODEPROJ
- .XML
- . XSD
- . XSL*

## <a name="retain-video-files"></a>الاحتفاظ بملفات الفيديو

تظهر هذه التوصية عند الكشف عن أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- . AVCHD
- .AVI
- . FLV
- . وسائل التحقق
- . MP2V
- .MP4
- . MP4V
- . MPE
- .MPEG
- . MPEG1
- . MPEG2
- . MPEG4
- .MPG
- . MPG2
- . MPG4
- . ومف
- . XMV
