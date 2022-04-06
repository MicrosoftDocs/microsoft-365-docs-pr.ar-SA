---
title: تشغيل عمليات المسح المجدولة عند الطلب وتخصيصها
description: يمكنك تخصيص عمليات برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية عبر الشبكة وبدءها.
keywords: المسح الضوئي، الجدولة، التخصيص، الاستثناءات، استبعاد الملفات، المعالجة، نتائج الفحص، الفحص، إزالة التهديدات، الفحص السريع، الفحص الكامل، برنامج الحماية من الفيروسات من Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: f3e0cc7ffccf02e24b9746d539a44d3a72810ead
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/08/2021
ms.locfileid: "63583224"
---
# <a name="customize-initiate-and-review-the-results-of-microsoft-defender-antivirus-scans--remediation"></a>تخصيص نتائج عمليات برنامج الحماية من الفيروسات من Microsoft Defender والشروع فيها ومراجعتها & المعالجة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/)

يمكنك استخدام نهج المجموعة و PowerShell Windows إدارة الأدوات (WMI) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي. 

## <a name="in-this-section"></a>في هذا القسم

| مقالة | الوصف |
|:---|:---|
|[تكوين استثناءات الملفات والمجلدات والملفات المفتوحة في عمليات برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها](configure-exclusions-microsoft-defender-antivirus.md) | يمكنك استبعاد الملفات (بما في ذلك الملفات المعدلة بواسطة عمليات محددة) والمجلدات من عمليات الفحص عند الطلب وعمليات الفحص المجدولة ومراقبة الحماية في الوقت الحقيقي وفحصها دائما |
|[تكوين خيارات برنامج الحماية من الفيروسات من Microsoft Defender ضوئية](configure-advanced-scan-types-microsoft-defender-antivirus.md) | يمكنك تكوين برنامج الحماية من الفيروسات من Microsoft Defender لتضمين أنواع معينة من ملفات تخزين البريد الإلكتروني، ونقاط إجراء عمليات حفظ أو إعادة تخزين، وملفات مؤرشفة (مثل ملفات .zip) في عمليات الفحص. يمكنك أيضا تمكين فحص ملفات الشبكة |
|[تكوين المعالجة من أجل عمليات الفحص](configure-remediation-microsoft-defender-antivirus.md) | تكوين ما برنامج الحماية من الفيروسات من Microsoft Defender القيام به عند الكشف عن وجود خطر، ومدى الوقت الذي يجب الاحتفاظ بالملفات المعزولة في مجلد الفحص |
|[تكوين عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) | إعداد عمليات الفحص المتكررة (المجدولة)، بما في ذلك وقت تشغيلها وما إذا كانت تعمل كمسح كامل أو سريع |
|[تكوين عمليات الفحص وتشغيلها](run-scan-microsoft-defender-antivirus.md) | تشغيل عمليات الفحص عند الطلب وتكوينها باستخدام PowerShell أو Windows Management Instrumentation أو بشكل فردي على نقاط النهاية باستخدام أمن Windows التطبيق |
|[مراجعة نتائج الفحص](review-scan-results-microsoft-defender-antivirus.md) | مراجعة نتائج عمليات الفحص باستخدام Microsoft Endpoint Configuration Manager أو Microsoft Intune أو تطبيق أمن Windows |