---
title: استيراد مجموعة مصطلحات باستخدام تنسيق مستند إلى SKOS
description: تعرف على كيفية استيراد مجموعة مصطلحات باستخدام تنسيق مستند إلى SKOS
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.service: ''
ms.collection: enabler-strategic
ms.custom: admindeeplinkSPO
search.appverid: ''
ms.localizationpriority: high
ms.openlocfilehash: c7a23b8da32f5ae9132a41661a1141f34df48a6b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575403"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a>استيراد مجموعة مصطلحات باستخدام تنسيق مستند إلى SKOS

يمكنك استيراد مجموعة مصطلحات باستخدام تنسيق مستند إلى SKOS. للحصول على تفاصيل حول التنسيق، راجع مرجع تنسيق [SKOS SharePoint SKOS](skos-format-reference.md). تتطلب هذه [الميزة SharePoint Syntex جديد](index.md).

نوصي بإبقاء ملفات الاستيراد أقل من 20000 مصطلح. يمكن للملفات الأكبر حجما زيادة الوقت الذي تم أخذه للتحقق من الصحة والاستيراد.

1. في مركز SharePoint، قم بتوسيع **خدمات المحتوى**، ثم حدد <a href="https://go.microsoft.com/fwlink/?linkid=2185073" target="_blank">**مخزن المصطلحات**</a>.

2. حدد مجموعة المصطلحات التي تريد استيراد مجموعة المصطلحات فيها.

3. في شريط الأوامر، انقر فوق **استيراد مجموعة المصطلحات**.

4. إذا كنت تريد تنزيل نموذج ملف لاستخدامه كقالب، انقر فوق **sample-metadata.ttl** للحصول على نموذج ملف يستخدم التنسيق المستند إلى SKOS.

5. أنشئ ملف الاستيراد الذي يحتوي على مجموعات المصطلحات & التي تريد استيرادها.

6. ضمن **تنسيق الملف**، حدد **SKOS (*.ttl)**.

7. انقر **فوق** استعراض وانتقل إلى ملف الاستيراد وأضفه.

8. انقر **فوق استيراد**. لا تغلق اللوحة حتى اكتمال عملية الاستيراد.

عند نجاح استيراد الملف، سيتم عرض رسالة نجاح، كما سيتم تحديث مخزن المصطلحات، كما يمكنك الانتقال إلى مجموعات المصطلحات التي تم إنشاؤها حديثا.

## <a name="see-also"></a>راجع أيضًا

[مقدمة حول بيانات التعريف المدارة](/sharepoint/managed-metadata)

[نظرة عامة حول فهم المستند](document-understanding-overview.md)

[استيراد مجموعات المصطلحات (مستوى الموقع)](https://support.microsoft.com/office/168fbc86-7fce-4288-9a1f-b83fc3921c18)
