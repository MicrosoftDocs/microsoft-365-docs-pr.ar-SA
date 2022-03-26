---
title: تعيين مهام الاختبار
description: تعيين مهام الاختبار
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 8255cadfa77dec222527c79caf4d8737abfe2b8c
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/06/2022
ms.locfileid: "63571729"
---
# <a name="step-4-the-tasks-tab"></a>الخطوة 4: علامة تبويب المهام

على علامة تبويب المهام، من المتوقع أن توفر المسارات إلى البرامج النصية الاختبارية في المجلد البريدي الذي قمت بتحميله ضمن علامة التبويب الثنائيات.

  - **البرامج النصية لاختبار "خارج المربع":** اكتب المسارات النسبية لتثبيت البرامج النصية، و تشغيلها، و إغلاقها، و إلغاء تثبيتها. لديك أيضا خيار تحديد إعدادات إضافية لتثبيت البرنامج النصي.
  - **برامج نصية لاختبار الوظائف:** اكتب المسار النسبي لكل برنامج نصي اختباري وظيفي تم تحميله. يمكن إضافة برامج نصية إضافية لاختبار الوظائف باستخدام ```Add Script``` الزر. تحتاج إلى برنامج نصي واحد (1) كحد أدنى، كما يمكنك إضافة ما يصل إلى ثمانية (8) برامج نصية لاختبار الوظائف. 
  
    يتم تشغيل البرامج النصية بالتسلسل الذي يتم سردها فيه. يؤدي الفشل في برنامج نصي معين إلى إيقاف البرامج النصية التالية من التنفيذ.
    لديك أيضا خيار تحديد إعدادات إضافية لكل برنامج نصي تم توفيره.

## <a name="set-script-path"></a>تعيين مسار البرنامج النصي

![صورة لمهمة اختبار.](Media/testtask.png)

فيما يلي نموذج حول كيفية توفير المسار النسبي على بنية مجلد:

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** . _ScriptX.ps1_ كمسار نسبي.
  - **Script.ps1** _مجلد1/script.ps1_ كمسار نسبي.


## <a name="next-steps"></a>الخطوات التالية

عرض تفاصيل علامة التبويب "خيارات الاختبار" في المقالة التالية 
> [!div class="nextstepaction"]
> [الخطوة التالية](testoptions.md)
