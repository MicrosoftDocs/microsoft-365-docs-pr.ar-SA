---
title: قواعد التطبيق/الاختبار
description: القواعد التي يجب اتباعها عند تحميل تطبيق/اختبار
search.appverid: MET150
author: andreicsibi-msft
ms.author: ancsibi
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: cebf888d7a17d6d589888d529cea1731b666f562
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/06/2022
ms.locfileid: "63579214"
---
# <a name="applicationtest-rules"></a>قواعد التطبيق/الاختبار

يجب أن تتوافق جميع التطبيقات أو الاختبارات في Test Base مع القواعد التالية:

## <a name="test-base-folders"></a>اختبار المجلدات الأساسية 

يتم استخدام المجلدات التالية بواسطة البنية الأساسية Test Base:
* ٪SYSTEMDRIVE٪\USL
* ٪SYSTEMDRIVE٪\EtlExport
* ٪SYSTEMDRIVE٪\Ffmpeg
* ٪SYSTEMDRIVE٪\Monitoring
* ٪SYSTEMDRIVE٪\powershell-yaml
* ٪SYSTEMDRIVE٪\ProcMon
* ٪SYSTEMDRIVE٪\PSTools
* ٪SYSTEMDRIVE٪\TokenProviderTool
* ٪SYSTEMDRIVE٪\USLPowershellModules
* ٪SYSTEMDRIVE٪\UtcUtil
* ٪SYSTEMDRIVE٪\WPT
* ٪SYSTEMDRIVE٪\WULogs

> [!IMPORTANT]
> **تجنب ما يلي**:
> * حظر تنفيذ أي عملية من هذه المجلدات. إذا كان تطبيقك برنامج مكافحة البرامج الضارة، ف قم بتكوين تثبيت التطبيق للسماح بتنفيذ كل العمليات من هذه المجلدات بدون اطباق.
> * العبث بأي من هذه المجلدات.

## <a name="test-base-registry-keys"></a>اختبار مفاتيح التسجيل الأساسية

يجب ألا تحذف التطبيقات/الاختبارات أي مفاتيح تسجيل ذات صلة ب:
* Windows بيانات التهية
* إزالة TLS 1.2
