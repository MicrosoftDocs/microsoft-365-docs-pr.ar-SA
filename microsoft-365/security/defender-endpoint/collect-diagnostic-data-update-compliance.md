---
title: تجميع البيانات التشخيصية لتحديث التوافق برنامج الحماية من الفيروسات من Microsoft Defender
description: استخدم أداة لتجميع البيانات لا استكشاف مشاكل التوافق في تحديث الأخطاء وإصلاحها عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender التقييم الإضافية.
keywords: استكشاف الأخطاء وإصلاحها وإصلاحها وتحديث التوافق وoms وشاشة العرض والتقارير و Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9e368f2cb3cecf9359c4aed5e727aef2ee21c02b
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/25/2021
ms.locfileid: "63578177"
---
# <a name="collect-update-compliance-diagnostic-data-for-microsoft-defender-antivirus-assessment"></a>تجميع بيانات تحديث التوافق التشخيصية برنامج الحماية من الفيروسات من Microsoft Defender التقييم


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

تصف هذه المقالة كيفية تجميع البيانات التشخيصية التي يمكن استخدامها من قبل فرق الدعم والهندسة من Microsoft للمساعدة في استكشاف المشاكل التي قد تواجهها عند استخدام قسم تقييم برنامج الحماية من الفيروسات من Microsoft Defender في الوظائف الإضافية تحديث التوافق.

قبل محاولة هذه العملية، تأكد من قراءة استكشاف الأخطاء [](troubleshoot-reporting.md)وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender التقارير، والمتطلبات الأساسية كلها، واتخذ أي خطوات أخرى لاقتراح استكشاف الأخطاء وإصلاحها.

على جهازين على الأقل لا يجريان تقارير أو يظهران في تحديث التوافق، احصل على .cab التشخيصي باتباع الخطوات التالية:

1. افتح إصدارا على مستوى المسؤول من موجه الأوامر كما يلي:

    أ. افتح قائمة **البدء** .

    ب. اكتب **cmd**. انقر ب زر الماوس الأيمن فوق **موجه الأوامر** ثم حدد **تشغيل كمسؤول**.

    c. حدد بيانات اعتماد المسؤول أو وافق على المطالبة.

2. انتقل إلى Windows Defender. بشكل افتراضي، هذا هو `C:\Program Files\Windows Defender`.

3. اكتب الأمر التالي، ثم اضغط على **Enter**

    ```Dos
    mpcmdrun -getfiles
    ```

4. سيتم .cab ملف يحتوي على سجلات تشخيص متنوعة. سيتم تحديد موقع الملف في الإخراج في موجه الأوامر. بشكل افتراضي، يكون الموقع هو `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

5. انسخ .cab الملفات إلى موقع يمكن الوصول إليه بواسطة دعم Microsoft. على سبيل المثال، قد يكون مجلد OneDrive محمي بكلمة مرور يمكنك مشاركته معنا.

6. أرسل بريدا إلكترونيا باستخدام <a href="mailto:ucsupport@microsoft.com?subject=MDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">قالب البريد</a> الإلكتروني لدعم توافق التحديث، واملأ القالب بالمعلومات التالية:

    ```text
    I am encountering the following issue when using Microsoft Defender Antivirus in Update Compliance:

    I have provided at least 2 support .cab files at the following location: <accessible share, including access details such as password>

    My OMS workspace ID is:

    Please contact me at:
    ```

## <a name="see-also"></a>راجع أيضًا

- [استكشاف الأخطاء برنامج الحماية من الفيروسات من Microsoft Defender التقارير وإصلاحها](troubleshoot-reporting.md)
