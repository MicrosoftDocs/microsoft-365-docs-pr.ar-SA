---
title: البحث عن رسائل الدردشة وحذفها في Teams
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: استخدم eDiscovery (Premium) وMicrosoft Graph Explorer للبحث عن رسائل الدردشة وحذفها في Microsoft Teams، والاستجابة لحوادث انسكاب البيانات في Teams.
ms.openlocfilehash: 372293e11ee16498746da69c824a91abd108f2cf
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66857514"
---
# <a name="search-and-purge-chat-messages-in-teams-preview"></a>البحث عن رسائل الدردشة وإصفادها في Teams (معاينة)

يمكنك استخدام eDiscovery (Premium) وMicrosoft Graph Explorer للبحث عن رسائل الدردشة وحذفها في Microsoft Teams. يمكن أن يساعدك ذلك في العثور على المعلومات الحساسة أو المحتوى غير المناسب وإزالتها. سيساعدك سير عمل البحث والإزالة هذا أيضا على الاستجابة لحادث انسكاب البيانات، عند إصدار محتوى يحتوي على معلومات سرية أو ضارة من خلال رسائل الدردشة في Teams.

> [!NOTE]
> تنطبق هذه المقالة على المؤسسات Microsoft 365 Enterprise. سيتوفر قريبا دعم سحابة حكومة الولايات المتحدة (بما في ذلك GCC و GCC High و DoD).

## <a name="before-you-search-and-purge-chat-messages"></a>قبل البحث عن رسائل الدردشة وإصفادها

- لإنشاء حالة eDiscovery (Premium) واستخدام المجموعات للبحث عن رسائل الدردشة، يجب أن تكون عضوا في مجموعة دور **eDiscovery Manager** في مدخل التوافق في Microsoft Purview. لحذف رسائل الدردشة، يجب تعيين دور **البحث والإزالة** . يتم تعيين هذا الدور إلى مجموعات دور "محقق البيانات وإدارة المؤسسة" بشكل افتراضي. لمزيد من المعلومات، راجع [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md).
- يتم دعم البحث والإزالة للمحادثات داخل المستأجر. يتم تمكين دعم محادثات Teams Connect Chat (الوصول الخارجي أو الاتحاد) في الواجهة في بعض الحالات ولكنه لا يعمل على النحو المنشود.
- يمكن إزالة 10 عناصر كحد أقصى لكل علبة بريد في وقت واحد. نظرا لأن القدرة على البحث عن رسائل الدردشة وإزالتها تهدف إلى أن تكون أداة للاستجابة للحوادث، فإن هذا الحد يساعد على ضمان إزالة رسائل الدردشة بسرعة.

## <a name="search-and-purge-workflow"></a>البحث عن سير العمل وإزالةه

إليك عملية البحث عن رسائل دردشة Teams وإزالة هذه الرسائل:

![سير العمل للبحث عن رسائل دردشة Teams وإزالة هذه الرسائل.](../media/TeamsSearchAndPurgeWorkflow.png)

## <a name="step-1-create-a-case-in-ediscovery-premium"></a>الخطوة 1: إنشاء حالة في eDiscovery (Premium)

الخطوة الأولى هي إنشاء حالة في eDiscovery (Premium) لإدارة عملية البحث والإزالة. للحصول على معلومات حول إنشاء حالة، راجع [استخدام تنسيق الحالة الجديد](advanced-ediscovery-new-case-format.md).

## <a name="step-2-create-a-draft-collection"></a>الخطوة 2: إنشاء مجموعة مسودات

بعد إنشاء حالة، الخطوة التالية هي إنشاء مجموعة مسودات للبحث عن رسائل الدردشة في Teams التي تريد إزالتها. عملية الإزالة التي تنفذها هي الخطوة 5 ستؤدي إلى إزالة كافة العناصر الموجودة في مجموعة المسودات.

في eDiscovery (Premium)، *المجموعة* هي بحث eDiscovery لمواقع محتوى Teams التي تحتوي على رسائل الدردشة التي تريد إزالتها. إنشاء مجموعة المسودات في الحالة التي قمت بإنشائها في الخطوة السابقة. لمزيد من المعلومات، راجع [إنشاء مجموعة مسودات](create-draft-collection.md).

### <a name="data-sources-for-chat-messages"></a>مصادر البيانات لرسائل الدردشة

استخدم الجدول التالي لتحديد مصادر البيانات التي تريد البحث فيها استنادا إلى نوع رسالة الدردشة التي تحتاج إلى إزالتها.

| لهذا النوع من الدردشة...|البحث في مصدر البيانات هذا...|
|:---------|:---------|
|دردشات Teams 1:1     |علبة بريد المشاركين في الدردشة.|
|دردشات مجموعة Teams     |علب بريد المشاركين في الدردشة.|
|قنوات Teams (قياسية ومشتركة) |علبة البريد المقترنة بالفريق الأصل.|
|قنوات Teams الخاصة |علبة بريد أعضاء القناة الخاصة.|

> [!NOTE]
> في الخطوة 4، يجب عليك أيضا تحديد وإزالة أي نهج احتجاز واستبقاء تم تعيينها إلى علبة البريد التي تحتوي على نوع رسائل الدردشة التي تريد حذفها.

### <a name="tips-for-searching-for-chat-messages"></a>تلميحات للبحث عن رسائل الدردشة

للمساعدة في ضمان أن المجموعة الأكثر شمولا من محادثات دردشة Teams (بما في ذلك 1:1 ودردشات المجموعة والدردشات من الدردشات القياسية والمشتركة والخاصة) تستخدم شرط **النوع** وحدد خيار **الرسائل الفورية** عند إنشاء استعلام البحث لمجموعة المسودات. نوصي أيضا بتضمين نطاق تاريخ أو عدة كلمات أساسية لتضييق نطاق المجموعة إلى العناصر ذات الصلة بالبحث الخاص بك في تحقيق إزالة.

فيما يلي لقطة شاشة لاستعلام نموذجي باستخدام خيارات **"النوع** " و" **التاريخ** ":

   ![استعلام لتجميع محتوى Teams.](..\media\TeamsConditionsQueryType.png)

لمزيد من المعلومات، راجع [إنشاء استعلامات البحث للمجموعات](building-search-queries.md).

## <a name="step-3-review-and-verify-chat-messages-to-purge"></a>الخطوة 3: مراجعة رسائل الدردشة والتحقق منها لإزالتها

كما ذكر سابقا، ستحذف عملية الإزالة في الخطوة 5 العناصر التي تم إرجاعها بواسطة المجموعة. لذلك من المهم مراجعة نتائج مجموعة المسودات للتأكد من أن المجموعة ترجع العناصر التي تريد إزالتها فقط. لمراجعة عينة من العناصر في مجموعة مسودات، راجع المقطع "الخطوات التالية بعد اكتمال مجموعة مسودات" في [إنشاء مجموعة مسودات](create-draft-collection.md#next-steps-after-a-draft-collection-is-complete).

بالإضافة إلى ذلك، يمكنك استخدام إحصائيات المجموعة (خاصة إحصائيات المواقع العليا) لإنشاء قائمة بمصادر البيانات التي تحتوي على عناصر تم إرجاعها بواسطة المجموعة. استخدم هذه القائمة في الخطوة التالية لإزالة نهج الاحتجاز والاستبقاء من مصادر البيانات التي تحتوي على نتائج البحث. لمزيد من المعلومات، راجع [إحصائيات المجموعة والتقارير](collection-statistics-reports.md).

## <a name="step-4-remove-holds-and-retention-policies-from-data-sources"></a>الخطوة 4: إزالة نهج الاحتجاز والاستبقاء من مصادر البيانات

قبل أن تتمكن من إزالة رسائل الدردشة من علبة بريد، يجب إزالة أي نهج احتجاز أو استبقاء تم تعيينه إلى علبة بريد هدف. إذا لم يكن الأمر كما يلي، فسيتم الاحتفاظ بالدردشة التي تحاول حذفها.

استخدم قائمة علب البريد التي تحتوي على رسائل الدردشة التي تريد حذفها وحدد ما إذا كان هناك نهج احتجاز أو استبقاء معين لعلب البريد هذه، ثم قم بإزالة نهج الاحتجاز أو الاستبقاء. تأكد من تحديد نهج الاحتجاز أو الاستبقاء الذي تقوم بإزالته بحيث يمكنك إعادة التعيين إلى علب البريد في الخطوة 7.

للحصول على إرشادات حول كيفية تحديد نهج الاحتجاز والاستبقاء وإزالتها، راجع "الخطوة 3: إزالة كافة عمليات الاحتجاز من علبة البريد" في [مجلد "حذف العناصر القابلة للاسترداد" في علب البريد المستندة إلى السحابة في قائمة الاحتجاز](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox).

## <a name="step-5-purge-chat-messages-from-teams"></a>الخطوة 5: إزالة رسائل الدردشة من Teams

أنت الآن جاهز لإزالة رسائل الدردشة من Teams. ستستخدم Microsoft Graph Explorer لتنفيذ المهام الثلاث التالية:

1. احصل على معرف حالة eDiscovery (Premium) التي قمت بإنشائها في الخطوة 1. هذه هي الحالة التي تحتوي على المجموعة التي تم إنشاؤها في الخطوة 2.

2. احصل على معرف المجموعة التي أنشأتها في الخطوة 2 وتحققت من نتائج البحث في الخطوة 3. يقوم استعلام البحث في هذه المجموعة بإرجاع رسائل الدردشة التي سيتم إزالتها.

3. قم بإزالة رسائل الدردشة التي تم إرجاعها بواسطة المجموعة.

للحصول على معلومات حول استخدام مستكشف الرسم البياني، راجع [استخدام مستكشف الرسم البياني لتجربة واجهات برمجة تطبيقات Microsoft Graph](/graph/graph-explorer/graph-explorer-overview).

> [!IMPORTANT]
> واجهات برمجة التطبيقات ضمن إصدار /beta في Microsoft Graph عرضة للتغيير. استخدام واجهات برمجة التطبيقات هذه في تطبيقات الإنتاج غير معتمد. لتحديد ما إذا كانت واجهة برمجة التطبيقات متوفرة في الإصدار 1.0، استخدم محدد الإصدار.

> [!IMPORTANT]
> لتنفيذ هذه المهام الثلاث في Graph Explorer، قد تحتاج إلى الموافقة على أذونات eDiscovery.Read.All وeDiscovery.ReadWrite.All. لمزيد من المعلومات، راجع قسم "الموافقة على الأذونات" في ["العمل باستخدام مستكشف الرسم البياني](/graph/graph-explorer/graph-explorer-features#consent-to-permissions)".

### <a name="get-the-case-id"></a>الحصول على معرف الحالة

1. انتقل إلى <https://developer.microsoft.com/graph/graph-explorer> Graph Explorer وسجل الدخول باستخدام حساب تم تعيينه لدور **البحث والإزالة** في مدخل التوافق في Microsoft Purview.

2. قم بتشغيل طلب GET التالي لاسترداد المعرف لحالة eDiscovery (Premium). استخدم القيمة `https://graph.microsoft.com/beta/compliance/ediscovery/cases` الموجودة في شريط العناوين لاستعلام الطلب. تأكد من تحديد **الإصدار 1.0** في القائمة المنسدلة لإصدار واجهة برمجة التطبيقات.

   ![طلب GET لمعرف الحالة.](..\media\GraphGetRequestForCaseId.png)

   يقوم هذا الطلب بإرجاع معلومات حول كافة الحالات في مؤسستك ضمن علامة التبويب **"معاينة الاستجابة** ".

3. قم بالتمرير عبر الاستجابة لتحديد موقع حالة eDiscovery (Premium). استخدم **الخاصية displayName** لتعريف الحالة.

   ![الاستجابة بمعرف الحالة.](..\media\GraphResponseForCaseId.png)

4. انسخ المعرف المقابل (أو انسخه والصقه إلى ملف نصي). ستستخدم هذا المعرف في المهمة التالية للحصول على معرف المجموعة.

> [!TIP]
> بدلا من استخدام الإجراء السابق للحصول على معرف الحالة، يمكنك فتح الحالة في مدخل التوافق في Microsoft Purview ونسخ معرف الحالة من عنوان URL.

### <a name="get-the-collection-id"></a>الحصول على معرف المجموعة

1. في مستكشف الرسم البياني، قم بتشغيل طلب GET التالي لاسترداد معرف المجموعة التي أنشأتها في الخطوة 2، ويحتوي على العناصر التي تريد إزالتها. استخدم القيمة `https://graph.microsoft.com/beta/compliance/ediscovery/cases('caseId')/sourceCollections` الموجودة في شريط العناوين لاستعلام الطلب، حيث يكون CaseId هو المعرف الذي حصلت عليه في الإجراء السابق. تأكد من إحاطة معرف الحالة بأقواس وعلامات اقتباس مفردة.

   ![طلب GET لمعرف المجموعة.](..\media\GraphGetRequestForCollectionId.png)

   يقوم هذا الطلب بإرجاع معلومات حول كافة المجموعات في الحالة على علامة التبويب **"معاينة الاستجابة** ".

2. قم بالتمرير عبر الاستجابة لتحديد موقع المجموعة التي تحتوي على العناصر التي تريد إزالتها. استخدم **الخاصية displayName** لتعريف المجموعة التي أنشأتها في الخطوة 3.

   ![الاستجابة بمعرف المجموعة.](..\media\GraphResponseForCollectionId.png)

   في الاستجابة، يتم عرض استعلام البحث من المجموعة في الخاصية **contentQuery** . سيتم إزالة العناصر التي تم إرجاعها بواسطة هذا الاستعلام في المهمة التالية.

3. انسخ المعرف المقابل (أو انسخه والصقه إلى ملف نصي). ستستخدم هذا المعرف في المهمة التالية لإزالة رسائل الدردشة.

### <a name="purge-the-chat-messages"></a>إزالة رسائل الدردشة

1. في Graph Explorer، قم بتشغيل طلب POST التالي لإزالة العناصر التي تم إرجاعها بواسطة المجموعة التي قمت بإنشائها في الخطوة 2. استخدم القيمة `https://graph.microsoft.com/beta/compliance/ediscovery/cases('caseId')/sourceCollections('collectionId')/purgeData` الموجودة في شريط العناوين لاستعلام الطلب، حيث إن معرف الحالة ومعرف المجموعة هما المعرفان التانتان التانكتانيتان. تأكد من إحاطة قيم المعرف بأقواس وعلامات اقتباس مفردة.

      ![طلب POST لحذف العناصر التي تم إرجاعها بواسطة المجموعة.](..\media\GraphPOSTRequestToPurgeItems.png)

   إذا نجح طلب POST، يتم عرض رمز استجابة HTTP في شعار أخضر يفيد بأنه تم قبول الطلب.

   ![الاستجابة لطلب الإزالة.](..\media\GraphResponseForPurge.png)

  لمزيد من المعلومات حول purgeData، راجع [sourceCollection: purgeData](/graph/api/ediscovery-sourcecollection-purgedata).

## <a name="step-6-verify-chat-messages-are-purged"></a>الخطوة 6: التحقق من إزالة رسائل الدردشة

بعد تشغيل طلب POST لإزالة رسائل الدردشة، تتم إزالة هذه الرسائل من عميل Teams واستبدالها بملف تم إنشاؤه تلقائيا يفيد بأن المسؤول قام بإزالة الرسالة. للحصول على مثال على هذه الرسالة، راجع قسم [تجربة المستخدم النهائي](#end-user-experience) في هذه المقالة.

يتم نقل رسائل الدردشة التي تمت إزالتها إلى مجلد SubstrateHolds، وهو مجلد علبة بريد مخفي. يتم تخزين رسائل الدردشة التي تمت إزالتها هناك لمدة يوم واحد على الأقل، ثم يتم حذفها نهائيا في المرة التالية التي يتم فيها تشغيل مهمة المؤقت (عادة ما بين يوم واحد و7 أيام). لمزيد من المعلومات، راجع ["تعرف على استبقاء Microsoft Teams](retention-policies-teams.md)".

## <a name="step-7-reapply-holds-and-retention-policies-to-data-sources"></a>الخطوة 7: إعادة تطبيق نهج الاحتجاز والاستبقاء على مصادر البيانات

بعد التحقق من إزالة رسائل الدردشة وإزالتها من عميل Teams، يمكنك إعادة تطبيق نهج الاحتجاز والاستبقاء التي قمت بإزالتها في الخطوة 4.

<!--
## Deleting chat messages in federated environments

Admins can use the procedures in this article to search and delete Teams chat messages in federated environments. However, you must adhere to the following guidelines. These guidelines are based on the organizational ownership of the conversation thread that contains the messages you want to delete. An organization is the owner of a conversation thread that is started by a user in that organization. In other words, when a user starts a chat, the user's organization becomes the owner of the conversation thread.

- Admins can delete the compliance copy in conversation threads owned by their organization. That means compliance copies are purged when the admin who purges the chat messages in Step 5 is in the same organization as the user who initiated the conversation thread that contains the purged messages. If a conversation thread has users in two organizations, compliance copies for the other organization will be retained.

- If a conversation thread has users in two organizations, purged chat messages are removed from the Teams client in both organizations.

- The only way to purge chat messages from user mailboxes in your organization for chat messages in conversation threads owned by another organization is to use retention policies for Teams. For more information, see [Learn about retention for Microsoft Teams](retention-policies-teams.md).
-->

## <a name="end-user-experience"></a>تجربة المستخدم النهائي

بالنسبة لرسائل الدردشة المحذوفة، سيرى المستخدمون رسالة تم إنشاؤها تلقائيا تفيد "تم حذف هذه الرسالة من قبل مسؤول".

![عرض رسالة الدردشة التي تمت إزالتها في عميل Teams.](..\media\TeamsPurgeTombstone.png)

تحل الرسالة في لقطة الشاشة السابقة محل رسالة الدردشة التي تم حذفها.

> [!NOTE]
> إذا كنت مستخدما نهائيا وتم حذف رسالة دردشة، فاتصل بالمسؤول للحصول على مزيد من المعلومات.
