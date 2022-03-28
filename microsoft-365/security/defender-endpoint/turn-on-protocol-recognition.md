---
title: تشغيل التعرف على البروتوكولات برنامج الحماية من الفيروسات من Microsoft Defender
description: تشغيل التعرف على البروتوكول برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، defender، التعرف على البروتوكول
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 02/21/2022
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: 221eff4af6bf8e77f29db84694bf3a683107fc8c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63573930"
---
# <a name="turn-on-protocol-recognition"></a>تشغيل التعرف على البروتوكول

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يسمح لك إعداد النهج هذا بتكوين التعرف على البروتوكول لحماية الشبكة من استغلال نقاط الضعف المعروفة. إذا قمت بتمكين هذا الإعداد أو لم تقوم بتكوينه، سيتم تمكين التعرف على البروتوكول. إذا قمت بتعطيل هذا الإعداد، سيتم تعطيل التعرف على البروتوكول.

[!IMPORTANT]
تم الآن إهمال هذا الإعداد. 

## <a name="use-group-policy-to-configure-protocol-recognition"></a>استخدام "نهج المجموعة" لتكوين التعرف على البروتوكول

1. في نقطة نهاية إدارة نهج المجموعة، افتح وحدة [التحكم في إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انتقل إلى **قوالب تكوين** \> الكمبيوتر  **الإدارية** **Windows** \> مكونات برنامج الحماية من الفيروسات من Microsoft Defender \> \> فحص الشبكة.

3. حدد **التعرف على البروتوكول**. بشكل افتراضي، يتم تمكين هذا النهج. إذا تم **تعيين لم يتم تكوينه**، يتم تمكين تقاعد التعريف.

4. لتحرير النهج، حدد **ارتباط إعداد نهج** التحرير.

5. حدد **تمكين**، ثم حدد **موافق**.

6. نشر كائن نهج المجموعة المحدث. راجع [وحدة تحكم إدارة نهج المجموعة](/windows/win32/srvnodes/group-policy).

> [!TIP]
> هل تستخدم "كائنات نهج المجموعة" في الموقع؟ تعرف على كيفية ترجمتها في السحابة. [قم بتحليل كائنات نهج المجموعة](/mem/intune/configuration/group-policy-analytics) في الموقع باستخدام تحليلات نهج المجموعة في إدارة نقاط النهاية من Microsoft - معاينة.

## <a name="related-articles"></a>المقالات ذات الصلة

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [تمكين الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)
- [كيفية إنشاء سياسات الحماية من البرامج الضارة ونشرها: خدمة الحماية من السحابة](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)
