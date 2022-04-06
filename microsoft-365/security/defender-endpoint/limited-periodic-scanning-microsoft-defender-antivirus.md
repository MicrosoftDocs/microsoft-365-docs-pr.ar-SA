---
title: تمكين ميزة المسح برنامج الحماية من الفيروسات من Microsoft Defender الدورية المحدودة
description: يسمح لك الفحص الدوري المحدود باستخدام برنامج الحماية من الفيروسات من Microsoft Defender بالإضافة إلى موفري AV المثبتة الآخرين
keywords: lps، محدود، دوري، مسح ضوئي، مسح ضوئي، توافق، طرف ثالث، آخر av، تعطيل
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 1ba846402bb2ee447ee5f38ff035c119bdc28fc1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467676"
---
# <a name="use-limited-periodic-scanning-in-microsoft-defender-antivirus"></a>استخدام الفحص الدوري المحدود في برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

الفحص الدوري المحدود هو نوع خاص من الكشف عن المخاطر والوساطة التي يمكن تمكينها عند تثبيت منتج آخر من برامج الحماية من الفيروسات على جهاز Windows 10 أو Windows 11 آخر.

يمكن تمكينه فقط في بعض الحالات. لمزيد من المعلومات حول الفحص الدوري المحدود وكيفية عمل برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الحماية من الفيروسات الأخرى، راجع برنامج الحماية من الفيروسات من Microsoft Defender [التوافق](microsoft-defender-antivirus-compatibility.md).

**لا توصي Microsoft باستخدام هذه الميزة في بيئات المؤسسات. هذه ميزة مخصصة بشكل أساسي للمستهلكين.** تستخدم هذه الميزة مجموعة فرعية محدودة من قدرات برنامج الحماية من الفيروسات من Microsoft Defender للكشف عن البرامج الضارة، ولن تتمكن من الكشف عن معظم البرامج الضارة والبرامج التي يحتمل أن تكون غير مرغوب فيها. كما ستكون قدرات الإدارة وإعداد التقارير محدودة. توصي Microsoft المؤسسات باختيار حل الحماية من الفيروسات الأساسي واستخدامه حصريا.

## <a name="how-to-enable-limited-periodic-scanning"></a>كيفية تمكين الفحص الدوري المحدود

بشكل افتراضي، برنامج الحماية من الفيروسات من Microsoft Defender البرنامج نفسه على جهاز Windows 10 أو جهاز Windows 11 إذا لم يكن هناك منتج آخر من برنامج الحماية من الفيروسات مثبتا، أو إذا كان المنتج الآخر غير منتهي الصلاحية أو منتهيا الصلاحية أو لا يعمل بشكل صحيح.

إذا برنامج الحماية من الفيروسات من Microsoft Defender، ستظهر الخيارات العادية لتكوينه على هذا الجهاز:

:::image type="content" source="images/vtp-wdav.png" alt-text="يعرض أمن Windows خيارات Microsoft Defender AV، بما في ذلك خيارات الفحص والإعدادات وخيارات التحديث" lightbox="images/vtp-wdav.png":::

إذا تم تثبيت منتج آخر من برامج الحماية من الفيروسات ويعمل بشكل صحيح، برنامج الحماية من الفيروسات من Microsoft Defender تعطيل نفسه. سيغير أمن Windows التطبيق قسم الحماية من المخاطر &  الفيروسات لإظهار حالة المنتج AV وتوفير ارتباط لخيارات تكوين المنتج.

أسفل أي من منتجات AV الخاصة بأي جهة خارجية، سيظهر ارتباط جديد ك **برنامج الحماية من الفيروسات من Microsoft Defender إضافية**. سيتم توسيع النقر فوق هذا الارتباط لإظهار زر تبديل الذي يمكن الفحص الدوري المحدود. لاحظ أن الخيار الدوري المحدود هو تبديل لتمكين الفحص الدوري أو تعطيله. 

يؤدي تمرير المفتاح إلى **تشغيل** إلى إظهار خيارات MICROSOFT Defender AV القياسية أسفل منتج AV الخاص ب جهة خارجية. سيظهر خيار الفحص الدوري المحدود في أسفل الصفحة.

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين الحماية السلوكية، والحماية التحليلية، والحماية في الوقت الحقيقي](configure-protection-features-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)