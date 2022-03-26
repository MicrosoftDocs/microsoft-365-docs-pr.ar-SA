---
title: الكشف المكرر تقريبا - eDiscovery
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
ms.assetid: ''
description: استخدم الكشف المكرر تقريبا لمجموعة مستندات مماثلة نصيا عند تحليل بيانات الحالة في Advanced eDiscovery.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: cbd01bd38f45a397a82a8db3774997349f4eec88
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566744"
---
# <a name="near-duplicate-detection-in-advanced-ediscovery"></a>الكشف المكرر تقريبا في Advanced eDiscovery

فكر في مجموعة من المستندات التي يجب مراجعتها حيث تستند مجموعة فرعية إلى القالب نفسه، وفي معظمها نفس لغة الإعدادات، مع بعض الاختلافات هنا وهناك. إذا كان با الممكن لمراجع تحديد هذه المجموعة الفرعية ومراجعة واحدة منها بدقة ومراجعة الاختلافات للبقية، لما فاته أي معلومات فريدة مع أخذ جزء من الوقت فقط لقراءة كل المستندات التي تغطيها. يجمع الكشف المكرر تقريبا المستندات المتشابهة نصيا معا لمساعدتك على جعل عملية المراجعة أكثر فعالية.

## <a name="how-does-it-work"></a>كيف يعمل؟

عند تشغيل الكشف المكرر القريب، ي تحليل النظام لكل مستند مع النص. بعد ذلك، يقارن كل مستند مع الآخر لتحديد ما إذا كان التشابه أكبر من الحد الذي تم تعيينه. إذا كان الأمر كذلك، يتم تجميع المستندات معا. بمجرد مقارنة كل المستندات تجميعها، يتم وضع علامة "المحور" على مستند من كل مجموعة؛ عند مراجعة المستندات، يمكنك مراجعة محور أولا ومراجعة المستندات الأخرى في المجموعة نفسها المكررة تقريبا، مع التركيز على الفرق بين المحور والمستند قيد المراجعة.
