---
title: إدارة Microsoft Defender لنقطة النهاية الخطة 1
description: صيانة وتحديث Defender لنقطة النهاية الخطة 1. إدارة الإعدادات والحصول على التحديثات ومعالجة الإيجابيات/السلبيات الخاطئة.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 417dd33eed846e45453464e63ff403374ce224dc
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667395"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>إدارة Microsoft Defender لنقطة النهاية الخطة 1

**ينطبق على**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

أثناء استخدام Defender لنقطة النهاية الخطة 1 في مؤسستك، يمكن لفريق الأمان اتخاذ خطوات معينة للحفاظ على حل الأمان الخاص بك. بينما يجمع فريق الأمان خطة الصيانة والعمليات، تأكد من تضمين الأنشطة التالية على الأقل:

- [إدارة معلومات الأمان وتحديثات المنتجات](#manage-security-intelligence-and-product-updates)
- [ضبط وضبط Defender لنقطة النهاية](#fine-tune-and-adjust-defender-for-endpoint)
- [معالجة الإيجابيات/السلبيات الخاطئة](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>إدارة معلومات الأمان وتحديثات المنتجات

يعد تحديث برنامج الحماية من الفيروسات من Microsoft Defender أمرا بالغ الأهمية للحماية من البرامج الضارة الجديدة وتقنيات الهجوم. تصدر Microsoft تحديثات منتظمة للذكاء الأمني ومكافحة الفيروسات والحماية من البرامج الضارة. يتم تنظيم التحديثات في فئتين: 

- تحديثات معلومات الأمان
- تحديثات المنتج 

لإدارة معلومات الأمان وتحديثات المنتجات، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>ضبط وضبط Defender لنقطة النهاية

يوفر لك Defender لنقطة النهاية الكثير من المرونة وخيارات التكوين. يمكنك ضبط إعداداتك وضبطها لتلائم احتياجات مؤسستك. على سبيل المثال، يمكنك استخدام إدارة نقاط النهاية من Microsoft نهج المجموعة وأساليب أخرى لإدارة إعدادات أمان نقطة النهاية. 

لمعرفة المزيد، راجع [إدارة Defender لنقطة النهاية](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>معالجة الإيجابيات/السلبيات الخاطئة

الإيجابية الخاطئة هي أداة، مثل ملف أو عملية، تم الكشف عنها على أنها ضارة، على الرغم من أنها ليست في الواقع تهديدا. السالب الخاطئ هو كيان لم يتم اكتشافه كتهديد، على الرغم من أنه في الواقع. يمكن أن تحدث الإيجابيات/السلبيات الخاطئة مع أي حل حماية نقطة النهاية، بما في ذلك Defender لنقطة النهاية. ومع ذلك، هناك خطوات يمكنك اتخاذها لمعالجة هذه الأنواع من المشكلات وضبط الحل الخاص بك، كما هو مبين في الصورة التالية:

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="نظرة عامة على عملية الإيجابيات والسلبيات الخاطئة" lightbox="../../media/defender-endpoint/false-positives-overview.png":::

إذا كنت ترى إيجابيات/سلبيات خاطئة في Defender لنقطة النهاية، فراجع [النتائج الإيجابية/السلبيات الخاطئة للعنوان في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md).

## <a name="next-steps"></a>الخطوات التالية

- [اطلع على أحدث الميزات في Microsoft Defender لنقطة النهاية](whats-new-in-microsoft-defender-endpoint.md)