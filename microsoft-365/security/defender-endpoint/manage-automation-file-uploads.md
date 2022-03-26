---
title: إدارة عمليات تحميل الملفات التلقائية
description: تمكين تحليل المحتوى وتكوين ملحق الملف وملحقات مرفقات البريد الإلكتروني التي سيتم إرسالها للتحليل
keywords: التنفيذ التلقائي، والملف، والتحميلات، والمحتوى، والتحليل، والملف، والملحق، والبريد الإلكتروني، والمرفق
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 21e7eb17759ff6127f3d91137023c058abe2715e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570537"
---
# <a name="manage-automation-file-uploads"></a>إدارة عمليات تحميل الملفات التلقائية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automationefileuploads-abovefoldlink)

تمكين إمكانية تحليل المحتوى بحيث يمكن تحميل بعض الملفات ومرفقات البريد الإلكتروني تلقائيا إلى السحابة لفحص إضافي في التحقيق التلقائي.

حدد الملفات ومرفقات البريد الإلكتروني من خلال تحديد أسماء ملحقات الملفات وأسماء ملحقات مرفقات البريد الإلكتروني.

على سبيل المثال، إذا أضفت *exe* و *bat* لأسماء ملحقات الملفات أو المرفقات، سيتم إرسال كل الملفات أو المرفقات التي تتضمن هذه الملحقات تلقائيا إلى السحابة لفحص إضافي أثناء إجراء التحقيق التلقائي.

## <a name="add-file-extension-names-and-attachment-extension-names"></a>إضافة أسماء ملحقات الملفات وأسماء ملحقات المرفقات.

1. في جزء التنقل **، حدد الإعدادات** \> **عمليات** \> التحميل التلقائي **لقواعد** \> **نقاط النهاية**.

2. تبديل إعداد تحليل المحتوى بين **تشغيل** أو **إيقاف تشغيل**.

3. تكوين أسماء الملحقات التالية وأسماء الملحقات المنفصلة باستخدام فاصلة:
   - **أسماء ملحقات الملفات** - سيتم إرسال الملفات المريبة باستثناء مرفقات البريد الإلكتروني لفحص إضافي

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة استثناءات مجلدات التنفيذ التلقائي](manage-automation-folder-exclusions.md)
