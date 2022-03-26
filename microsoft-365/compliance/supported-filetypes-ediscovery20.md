---
title: أنواع الملفات المعتمدة في Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: قائمة بأنواع الملفات المعتمدة في Microsoft 365 Advanced eDiscovery، بما في ذلك أنواع ملفات الصور المعتمدة بواسطة وظيفة OCR في Advanced eDiscovery.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 96d469d861be3392108b53811478f94d0e59f40b
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63568578"
---
# <a name="supported-file-types-in-advanced-ediscovery"></a>أنواع الملفات المعتمدة في Advanced eDiscovery

Advanced eDiscovery العديد من أنواع الملفات على العديد من المستويات المختلفة. يتم وصف أنواع ملفات الدعم في الجداول التالية في هذه المقالة. لم يتم الانتهاء من هذه القائمة، وسنضيف أنواع ملفات جديدة بينما نستمر في اختبار التحقق من الصحة. تشير هذه الجداول إلى ما إذا كان نوع الملف معتمدا لاستخراج النص (واستخراج نص التعرف البصري على الأحرف أو التعرف البصري على الحروف لملفات الصور)، ويمكن عرضه في العارض الأصلي وكذلك الدعم في عارض التعليقات التوضيحية في Advanced eDiscovery.

## <a name="archive--container"></a>أرشفة / حاوية

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج الحاويات|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|
|تطبيق/x-7z-مضغوط|نعم|نعم|نعم|.7z|
|application/x-rar-مضغوط|نعم|نعم|نعم|.rar|
|application/x-tar|نعم|نعم|نعم|.tar|
|application/zip|نعم|نعم|نعم|.zip|
|

## <a name="audio--video"></a>الصوت / الفيديو

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/mp4|نعم|نعم|لا|نعم|لا|.f4v; .m4a; .m4v; .mp4; .mp4v; .mpeg; .mpeg4|
|الصوت/mpeg|نعم|نعم|لا|نعم|لا|.mpeg|
|video/3gpp|نعم|نعم|لا|نعم|لا|.3gp|
|video/3gpp2|نعم|نعم|لا|نعم|لا|.3g2; .3gp2|
|الفيديو/الوقت السريع|نعم|نعم|لا|نعم|لا|.moov; .mov; .qt|
|video/x-m4v|نعم|نعم|لا|نعم|لا|m4v.|
|

## <a name="database"></a>Database

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-msaccess|نعم|نعم|نعم|لا|لا|mdb.|
|

## <a name="email"></a>البريد الإلكتروني

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-outlook|نعم|نعم|نعم|نعم|نعم|msg.|
|رسالة/rfc822|نعم|نعم|نعم|نعم|نعم|eml.|
|text/vcard-contact|نعم|نعم|نعم|نعم|نعم|vcf.|
|

## <a name="email-container"></a>حاوية البريد الإلكتروني

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج الحاويات|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|
|تطبيق/mbox|نعم|نعم|نعم|mbox.|
|application/vnd.ms-outlook-pst|نعم|نعم|نعم|pst.|
|

## <a name="html"></a>HTML

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/xhtml+xml|نعم|نعم|نعم|نعم|نعم|xhtml.|
|application/xml|نعم|نعم|نعم|نعم|نعم|.xml|
|النص/html|نعم|نعم|نعم|نعم|نعم|.htm؛ .html; .shtml|
|

## <a name="image"></a>صورة

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج نص OCR|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|صورة/bmp|نعم|نعم|نعم|نعم|نعم|.bmp|
|صورة/emf|نعم|نعم|نعم|نعم|نعم|emf.|
|صورة/gif|نعم|نعم|نعم|نعم|نعم|.gif|
|صورة/jpeg|نعم|نعم|نعم|نعم|نعم|jpeg. .jpg|
|صورة/png|نعم|نعم|نعم|نعم|نعم|.png|
|صورة/svg+xml|نعم|نعم|نعم|نعم|لا|.svg|
|صورة/tiff|نعم|نعم|نعم|نعم|نعم|tif.|
|image/vnd.dwg|نعم|نعم|نعم|نعم|نعم|.dwg; .dxf|
|صورة/wmf|نعم|نعم|نعم|نعم|نعم|wmf.|
|

## <a name="microsoft-excel"></a>Microsoft Excel

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-excel|نعم|نعم|نعم|نعم|نعم|.dat; .xls|
|application/vnd.ms-excel.sheet.binary.macroenabled.12|نعم|نعم|نعم|نعم|لا|xlsb.|
|application/vnd.ms-excel.sheet.macroenabled.12|نعم|نعم|نعم|نعم|نعم|xlsm.|
|application/vnd.ms-excel.template.macroenabled.12|نعم|نعم|نعم|لا|لا|xltm.|
|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|نعم|نعم|نعم|نعم|نعم|.xlsx|
|application/vnd.openxmlformats-officedocument.spreadsheetml.template|نعم|نعم|نعم|نعم|نعم|xltx.|
|

## <a name="microsoft-onenote"></a>Microsoft OneNote

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|تطبيق/onenote|نعم|نعم|نعم|لا|لا|.one|
|

## <a name="microsoft-powerpoint"></a>Microsoft PowerPoint

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-powerpoint|نعم|نعم|نعم|نعم|نعم|.pot; .pps; .ppt|
|application/vnd.openxmlformats-officedocument.presentationml.presentation|نعم|نعم|نعم|نعم|نعم|.pptx|
|application/vnd.openxmlformats-officedocument.presentationml.slideshow|نعم|نعم|نعم|نعم|نعم|ppsx.|
|application/vnd.openxmlformats-officedocument.presentationml.template|نعم|نعم|نعم|نعم|نعم|potx.|
|

## <a name="microsoft-project"></a>Microsoft Project

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-project|نعم|نعم|نعم|لا|نعم|.mpp|
|

## <a name="microsoft-publisher"></a>Microsoft Publisher

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-mspublisher|نعم|نعم|نعم|نعم|نعم|.pub|
|

## <a name="microsoft-visio"></a>Microsoft Visio

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-visio.drawing|نعم|نعم|نعم|نعم|لا||
|application/vnd.visio|نعم|نعم|نعم|نعم|نعم|vsd.|
|

## <a name="microsoft-word"></a>Microsoft Word

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/msword|نعم|نعم|نعم|نعم|نعم|.dat; .doc|
|application/rtf|نعم|نعم|نعم|نعم|نعم|.doc; .rtf|
|application/vnd.ms-word.document.macroenabled.12|نعم|نعم|نعم|نعم|نعم|docm.|
|application/vnd.ms-word.template.macroenabled.12|نعم|نعم|نعم|نعم|نعم|dotm.|
|application/vnd.openxmlformats-officedocument.wordprocessingml.document|نعم|نعم|نعم|نعم|نعم|.docx|
|application/vnd.openxmlformats-officedocument.wordprocessingml.template|نعم|نعم|نعم|نعم|نعم|dotx.|
|

## <a name="microsoft-works"></a>Microsoft Works

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-works-ss|نعم|نعم|لا|لا|لا|wps.|
|application/vnd.ms-works-wp|نعم|نعم|لا|لا|لا|wps.|
|

## <a name="open-document-format"></a>فتح تنسيق المستند

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.oasis.opendocument.text|نعم|نعم|نعم|نعم|نعم|odt.|
|

## <a name="other"></a>غير ذلك

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/json|نعم|نعم|نعم|نعم|نعم|n/a|
|application/octet-stream|نعم|لا|لا|لا|لا|.fluid|
|application/vnd.ms-graph|نعم|نعم|لا|لا|لا||
|application/winhlp|نعم|نعم|لا|لا|لا|hlp.|
|application/x-tnef|نعم|نعم|لا|لا|لا||
|

## <a name="plain-text"></a>نص عادي

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|text/csv|نعم|نعم|نعم|نعم|نعم|.csv|
|نص/عادي|نعم|نعم|نعم|نعم|نعم|.con; .css; .csv; .dat; .pl; .txt|
|

## <a name="portable-document-format"></a>Portable Document Format

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/pdf|نعم|نعم|نعم|نعم|نعم|.pdf|
|

## <a name="word-perfect"></a>Word Perfect

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.wordperfect; version=5.0|نعم|نعم|نعم|لا|لا|wpd.|
|application/vnd.wordperfect; version=5.1|نعم|نعم|نعم|لا|لا|wpd.|
|application/vnd.wordperfect; version=6.x|نعم|نعم|نعم|لا|لا|wpd.|
|

## <a name="word-pro"></a>Word Pro

<br>

****

|نوع Mime|تعريف الملف|استخراج بيانات التعريف|استخراج النص|العارض الأصلي|عارض التعليقات التوضيحية|الملحقات المحتملة|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.lotus-wordpro|نعم|نعم|لا|لا|لا|lwp.|
|
