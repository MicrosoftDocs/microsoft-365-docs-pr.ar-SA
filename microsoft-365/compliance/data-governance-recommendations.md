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
description: يوفر Microsoft 365 Defender والمدخل مركز التوافق في Microsoft 365 توصيات لإدارة البيانات استنادا إلى الإعداد الحالي للمؤسسة ويسمحان لك بإعداد الأشياء بنقرات قليلة. تكتشف بعض هذه التوصيات محتوى محددا في مؤسستك ثم توفر الخطوات المستحسنة لإدارة هذا المحتوى. على سبيل المثال، قد تكشف التوصية عن العناصر التي تحتوي على محتوى هام للأعمال (مثل امتياز المحامي-العميل أو معلومات NDA)، ثم تسمح لك بتطبيق تسمية استبقاء على تلك العناصر تلقائيا لضمان تصنيفها والاحتفاظ بها حسب الحاجة. يسرد هذا الموضوع توصيات إدارة البيانات التي قد تراها ويصف المحتوى الذي يتم اكتشافه لتحريك كل منها.
ms.openlocfilehash: cddd73fdd0c21605549450968db182883ab7e6ad
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "63567125"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>كيفية تحديد المحتوى لتوصيات إدارة البيانات

يوفر <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender والمدخل</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365</a> توصيات لإدارة البيانات استنادا إلى الإعداد الحالي للمؤسسة ويسمحان لك بإعداد الأشياء بنقرتين. تكتشف بعض هذه التوصيات محتوى محددا في مؤسستك ثم توفر الخطوات المستحسنة لإدارة هذا المحتوى. على سبيل المثال، قد تكشف التوصية عن العناصر التي تحتوي على محتوى هام للأعمال (مثل امتياز المحامي-العميل أو معلومات NDA)، ثم تسمح لك بتطبيق تسمية استبقاء على تلك العناصر تلقائيا لضمان تصنيفها والاحتفاظ بها حسب الحاجة.

يسرد هذا الموضوع توصيات إدارة البيانات التي قد تراها ويصف المحتوى الذي يتم اكتشافه لتحريك كل منها.

## <a name="clean-up-voicemail"></a>تنظيف البريد الصوتي

تظهر هذه التوصية عند اكتشاف رسائل البريد الإلكتروني المحددة كنوع الرسالة "البريد الصوتي" في علب بريد المستخدمين. تعرف على المزيد [حول خصائص الرسالة في Exchange](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>تسمية محتوى امتياز المحامي والعميل

تظهر هذه التوصية عند تنفيذ أي من المعايير التالية.

- يتم اكتشاف أي تركيبة من هذه الكلمات الأساسية في نص رسالة البريد الإلكتروني:
  - ACP
  - امتياز عميل المحامي
  - Attorney-Client امتياز
  - Attorney-Client مميز

- يتم اكتشاف أي تركيبة من هذه الكلمات الأساسية في SharePoint أو OneDrive:
  - ACP
  - امتياز عميل المحامي*
  - امتياز AC

## <a name="retain-audio-files"></a>الاحتفاظ بالملفات الصوتية

تظهر هذه التوصية عند اكتشاف أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- .MP3
- . WMA
- . WAV
- . RA
- . ذاكرة الوصول العشوائي
- RM.
- . MID
- . OGG
- . AIFF
- . PCM
- . AAC
- . FLAC
- . ALAC

## <a name="retain-cad-files"></a>الاحتفاظ بملفات CAD

تظهر هذه التوصية عند اكتشاف أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- .3DXML
- . ACIS
- . ARC
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
- . JT
- . MF1
- . NEU
- . PAR
- . PKG
- . PRC
- . PRT
- . PSM
- . PWD
- . SLD*
- . الخطوة
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

تظهر هذه التوصية عند اكتشاف أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- . JPEG
- .GIF
- . TIF*
- .BMP
- .PNG
- . RAW
- .PSD
- . PSP
- .JPG
- . EXIF
- . PPM
- . PGM
- . PBM
- . PNM
- . WEBP

## <a name="retain-nda-content"></a>الاحتفاظ بمحتوى NDA

تظهر هذه التوصية عند تنفيذ أي من المعايير التالية.

- يتم اكتشاف أي تركيبة من هذه الكلمات الأساسية في نص رسالة البريد الإلكتروني:
  - NDA
  - "اتفاقية عدم الإفصاح عن المعلومات"
  - "اتفاقية عدم الإفصاح عن المعلومات"

- يتم اكتشاف أي تركيبة من هذه الكلمات الأساسية في .PDF أو .DOC في SharePoint أو OneDrive:
  - NDA
  - اتفاقية عدم الإفصاح

## <a name="retain-software-development-files"></a>الاحتفاظ بملفات تطوير البرامج

تظهر هذه التوصية عند اكتشاف أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- CS.
- . CSS
- . DISCO
- .HTM*
- . INC
- . JAD
- . JAVA
- .JS*
- . LIB
- . O
- . PHP
- . RC
- . RESX
- . RPT
- . RSS
- . SCPT
- . SRC
- . VB*
- . WSF
- . XCODEPROJ
- .XML
- . XSD
- . XSL*

## <a name="retain-video-files"></a>الاحتفاظ بملفات الفيديو

تظهر هذه التوصية عند اكتشاف أي من أنواع الملفات التالية في SharePoint أو OneDrive.

- . AVCHD
- .AVI
- . FLV
- . MOV
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
- . WMV
- . XMV
