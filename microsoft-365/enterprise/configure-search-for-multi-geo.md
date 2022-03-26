---
title: تكوين البحث عن Microsoft 365 الجغرافيا المتعددة
ms.reviewer: adwood
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-mar2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: تعرف على كيفية تكوين البحث في بيئة متعددة الجغرافيا. يمكن لبعض العملاء فقط، مثل OneDrive، إرجاع النتائج في بيئة متعددة الجغرافيا.
ms.openlocfilehash: d6d6895c6dc393bb1f28dff60dea996bf80aad5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570033"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>تكوين البحث عن Microsoft 365 الجغرافيا المتعددة

في بيئة متعددة الجغرافيا، يحتوي كل موقع جغرافي على فهرس بحث ومركز بحث خاصين به. عندما يبحث المستخدم، يتم تهيؤ الاستعلام إلى كل فهارس، كما يتم دمج النتائج التي يتم إرجاعها.

على سبيل المثال، يمكن للمستخدم في موقع جغرافي واحد البحث عن محتوى مخزن في موقع جغرافي آخر، أو عن محتوى على موقع SharePoint مقيد بموقع جغرافي آخر. إذا كان لدى المستخدم حق الوصول إلى هذا المحتوى، فإن البحث سيعرض النتيجة.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>ما عملاء البحث الذين يعملون في بيئة متعددة الجغرافيا؟

يمكن للعملاء إرجاع النتائج من كل المواقع الجغرافية:

- OneDrive
- Delve
- الصفحة SharePoint الرئيسية
- مركز البحث
- تطبيقات البحث المخصصة التي تستخدم SharePoint API للبحث

### <a name="onedrive"></a>OneDrive

بمجرد إعداد البيئة متعددة المواقع الجغرافية، يحصل المستخدمون الذين يبحثون OneDrive على نتائج من كل المواقع الجغرافية.

### <a name="delve"></a>Delve

بمجرد إعداد البيئة متعددة المواقع الجغرافية، يحصل المستخدمون الذين يبحثون في Delve على نتائج من كل المواقع الجغرافية.

لا Delve الموجز وبطاقة ملف التعريف إلا معاينات الملفات المخزنة في الموقع المركزي. بالنسبة للملفات المخزنة في مواقع الأقمار الصناعية، يتم عرض أيقونة نوع الملف بدلا من ذلك.

### <a name="the-sharepoint-home-page"></a>الصفحة SharePoint الرئيسية

بمجرد إعداد البيئة متعددة المواقع الجغرافية، سيشاهد المستخدمون الأخبار والمواقع الحديثة والمتابعة من مواقع جغرافية متعددة على SharePoint الرئيسية الخاصة بهم. إذا استخدم مربع البحث على SharePoint الرئيسية، فسوف تحصل على نتائج مدمجة من مواقع جغرافية متعددة.

### <a name="the-search-center"></a>مركز البحث

بعد إعداد البيئة متعددة الجغرافيا، يستمر كل مركز بحث في عرض النتائج من موقعه الجغرافي الخاص فقط. يجب على [المسؤولين تغيير إعدادات كل مركز بحث](#_Set_up_a_1) للحصول على نتائج من كل المواقع الجغرافية. بعد ذلك، يحصل المستخدمون الذين يبحثون في مركز البحث على نتائج من كل المواقع الجغرافية.

### <a name="custom-search-applications"></a>تطبيقات البحث المخصصة

وكالعادة، تتفاعل تطبيقات البحث المخصصة مع فهارس البحث باستخدام SharePoint واجهات برمجة تطبيقات REST للبحث. للحصول على نتائج من كل المواقع الجغرافية أو من بعض المواقع الجغرافية، يجب أن يتصل التطبيق ب API وأن يتضمن معلمات الاستعلام [متعدد الجغرافيا الجديدة](#_Get_custom_search) في الطلب. يؤدي ذلك إلى تشغيل مروحة من الاستعلام إلى كل المواقع الجغرافية.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>ما الذي يختلف عن البحث في بيئة متعددة الجغرافيا؟

تعمل بعض ميزات البحث التي قد تكون على دراية بها بشكل مختلف في بيئة متعددة الجغرافيا.

<table>
<thead>
<tr class="header">
<th align="left">الميزة</th>
<th align="left">كيفية عمل ذلك</th>
<th align="left">الحل البديل</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">النتائج التي تم الترويج لها</td>
<td align="left">يمكنك إنشاء قواعد استعلام ذات نتائج ترقية على مستويات مختلفة: للمستأجر بكامله أو مجموعة مواقع ويب أو لموقع. في بيئة متعددة الجغرافيا، حدد النتائج التي تم الترويج لها على مستوى المستأجر للترويج للنتائج في مراكز البحث في كل المواقع الجغرافية. إذا كنت تريد فقط ترقية النتائج في "مركز البحث" في الموقع الجغرافي الخاص بمجموعه المواقع أو الموقع، فحدد النتائج التي تم ترقيتها على مستوى مجموعة المواقع أو المواقع. لا يتم ترقية هذه النتائج في مواقع جغرافية أخرى.</td>
<td align="left">إذا لم تكن بحاجة إلى نتائج مختلفة تم ترقياتها لكل موقع جغرافي، على سبيل المثال قواعد مختلفة للسفر، فإننا نوصي بتعريف النتائج التي تم الترويج لها على مستوى المستأجر.</td>
</tr>
<tr class="even">
<td align="left">مصافي البحث</td>
<td align="left">ترجع عملية البحث مصاف من كل المواقع الجغرافية لمستأجر ثم تقوم بتجميعها. يعد التجميع أفضل جهد، مما يعني أن عدد المصاف قد لا يكون دقيقا بنسبة 100٪. بالنسبة لمعظم السيناريوهات التي تعتمد على البحث، تكون هذه الدقة كافية. 
</td>
<td align="left">بالنسبة للتطبيقات التي تعتمد على البحث التي تعتمد على اكتمال المكيف، استعلام كل موقع جغرافي بشكل مستقل.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">لا يدعم البحث الجغرافي المتعدد مستودعات ديناميكية لمصافي الأرقام.</td>
<td align="left">استخدم <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">المعلمة "منفصلة"</a> للمصافي الرقمية.</td>
</tr>
<tr class="even">
<td align="left">"مستندات الملهمة"</td>
<td align="left">إذا كنت تطور تطبيقا مستندا إلى البحث يعتمد على "مستندات المفردات"، فلاحظ أن "لمستندات" في بيئة متعددة الجغرافيا ليست فريدة عبر المواقع الجغرافية، فهي فريدة لكل موقع جغرافي.</td>
<td align="left">لقد أضفنا عمودا يعرف الموقع الجغرافي. استخدم هذا العمود لتحقيق التفرد. يسمى هذا العمود "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">عدد النتائج</td>
<td align="left">تعرض صفحة نتائج البحث النتائج المجمعة من المواقع الجغرافية، ولكن لا يمكن عرض أكثر من 500 نتيجة.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">البحث المختلط</td>
<td align="left">في بيئة مختلطة SharePoint البحث المختلط في السحابة<a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint"></a>، يضاف المحتوى المحلي إلى Microsoft 365 الموقع المركزي.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>ما هي غير المعتمدة للبحث في بيئة متعددة الجغرافيا؟

لا يتم دعم بعض ميزات البحث التي قد تكون على دراية بها في بيئة متعددة الجغرافيا.

<table>
<thead>
<tr class="header">
<th align="left">ميزة البحث</th>
<th align="left">ملاحظة</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">مصادقة التطبيق فقط</td>
<td align="left">لا يتم دعم مصادقة التطبيقات فقط (الوصول المتميز من الخدمات) في بحث في مواقع جغرافية متعددة.</td>
</tr>
<tr class="even">
<td align="left">الضيوف</td>
<td align="left">يحصل الضيوف على النتائج فقط من الموقع الجغرافي الذي يبحثون منه.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>كيف يعمل البحث في بيئة متعددة الجغرافيا؟

يستخدم كل عملاء البحث واجهات برمجة SharePoint للبحث في REST للتفاعل مع فهارس البحث.

![رسم تخطيطي SharePoint تفاعل واجهات برمجة التطبيقات "REST" مع فهارس البحث.](../media/configure-search-for-multi-geo-image1-1.png)

1. يستدعي عميل البحث نقطة نهاية Search REST مع خاصية الاستعلام EnableMultiGeoSearch= true.
2. يتم إرسال الاستعلام إلى كل المواقع الجغرافية في المستأجر.
3. يتم دمج نتائج البحث من كل موقع جغرافي ومرتبة.
4. يحصل العميل على نتائج بحث موحدة.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>لاحظ أننا لا نقوم بدمج نتائج البحث حتى نتلقى نتائج من كل المواقع الجغرافية. وهذا يعني أن عمليات البحث الجغرافي المتعددة لها زمن زمن إضافي مقارنة بعمليات البحث في بيئة ذات موقع جغرافي واحد فقط.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>الحصول على مركز بحث لعرض النتائج من كل المواقع الجغرافية

يحتوي كل مركز بحث على عدة رأسيات، كما يجب إعداد كل عمود على حدة.

1. تأكد من تنفيذ هذه الخطوات باستخدام حساب لديه الإذن لتحرير صفحة نتائج البحث وجزء ويب لنتيجة البحث.

2. الانتقال إلى صفحة نتائج البحث ( [راجع قائمة](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) صفحات نتائج البحث)

3. حدد العمودي الذي تريد إعداده **، الإعدادات** أيقونة الترس في الزاوية العلوية اليسرى، ثم انقر فوق **تحرير الصفحة**. يتم فتح صفحة نتائج البحث في وضع التحرير.

   ![تحرير تحديد الصفحة في الإعدادات.](../media/configure-search-for-multi-geo-image2.png)

4. في جزء ويب نتائج البحث، حرك الماوس إلى الزاوية العلوية اليسرى من جزء ويب، وانقر فوق السهم، ثم انقر فوق تحرير **جزء** ويب من القائمة. يتم فتح جزء أدوات جزء ويب الخاص بنتائج البحث أسفل الشريط في الجزء العلوي الأيمن من الصفحة.

   ![تحرير تحديد جزء ويب.](../media/configure-search-for-multi-geo-image3.png)

5. في جزء أدوات جزء ويب، في المقطع **الإعدادات**، ضمن إعدادات التحكم في النتائج، حدد إظهار نتائج **متعددة** الجغرافيا للحصول على جزء ويب نتائج البحث لعرض النتائج من كل المواقع الجغرافية.

6. انقر **فوق** موافق لحفظ التغيير وأغلق جزء أدوات جزء ويب.

7. تحقق من تغييراتك في جزء ويب نتائج البحث **بالنقر فوق تسجيل** الدخول على علامة التبويب صفحة من القائمة الرئيسية.

8. انشر التغييرات باستخدام الارتباط الموفر في الملاحظة في أعلى الصفحة.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>الحصول على تطبيقات بحث مخصصة لعرض النتائج من كل المواقع الجغرافية أو بعضها

تحصل تطبيقات البحث المخصصة على نتائج من كل المواقع الجغرافية أو بعضها من خلال تحديد معلمات الاستعلام مع الطلب إلى SharePoint بحث في REST API. استنادا إلى معلمات الاستعلام، يتم تهيييه الاستعلام إلى كل المواقع الجغرافية أو إلى بعض المواقع الجغرافية. على سبيل المثال، إذا كنت تحتاج فقط إلى الاستعلام عن مجموعة فرعية من المواقع الجغرافية للعثور على المعلومات ذات الصلة، يمكنك التحكم في المروحة في هذه المواقع فقط. إذا نجح الطلب، فترجع SharePoint Search REST API بيانات الاستجابة.

### <a name="requirement"></a>المتطلب

لكل موقع جغرافي، يجب أن تضمن منح جميع المستخدمين في المؤسسة مستوى الأذونات "قراءة"  لموقع ويب الجذر (على سبيل المثال contosoAPAC.sharepoint.com/ و contosoEU.sharepoint.com/). [تعرف على الأذونات](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>معلمات الاستعلام

EnableMultiGeoSearch - هذه قيمة منطقية تحدد ما إذا كان سيتم تكبير الاستعلام إلى فهارس المواقع الجغرافية الأخرى للمستأجر متعدد الجغرافيا. قم **بتعيينه إلى true** لتخيل الاستعلام؛ **خطأ** عدم مروحة الاستعلام. إذا لم تقوم بتضمين هذه المعلمة، تكون القيمة الافتراضية خاطئة، إلا عند إجراء استدعاء REST API مقابل موقع يستخدم قالب "مركز البحث الخاص بالمؤسسة"، في هذه الحالة تكون القيمة الافتراضية **صحيحة**. إذا كنت تستخدم المعلمة في بيئة غير متعددة الجغرافيا، يتم تجاهل المعلمة.

ClientType - هذه سلسلة. أدخل اسم عميل فريدا لكل تطبيق بحث. إذا لم تقوم بتضمين هذه المعلمة، فلا يتم تغيير الاستعلام إلى مواقع جغرافية أخرى.

MultiGeoSearchConfiguration - هذه قائمة اختيارية للمواقع الجغرافية في المستأجر الجغرافي المتعدد لتشويه الاستعلام عندما **يكون EnableMultiGeoSearch** **صحيحا**. إذا لم تتضمن هذه المعلمة، أو تركتها فارغة، يتم تهي الاستعلام إلى كل المواقع الجغرافية. لكل موقع جغرافي، أدخل العناصر التالية، بتنسيق JSON:

<table>
<thead>
<tr class="header">
<th align="left">عنصر</th>
<th align="left">الوصف</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">الموقع الجغرافي، على سبيل المثال NAM.</td>
</tr>
<tr class="even">
<td align="left">EndPoint</td>
<td align="left">نقطة النهاية التي يجب الاتصال بها، على سبيل المثال https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">الم GUID لمصدر النتائج، على سبيل المثال B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

إذا حذفت DataLocation أو EndPoint، أو إذا تم تكرار DataLocation، يفشل الطلب. [يمكنك الحصول على معلومات حول نقطة نهاية](/sharepoint/dev/solution-guidance/multigeo-discovery) المواقع الجغرافية للمستأجر باستخدام Microsoft Graph.

### <a name="response-data"></a>بيانات الاستجابة

MultiGeoSearchStatus – هذه خاصية ترجعها SharePoint API للبحث استجابة لطلب. قيمة الخاصية هي سلسلة وتعطي المعلومات التالية حول النتائج التي ترجعها SharePoint API للبحث:

<table>
<thead>
<tr class="header">
<th align="left">القيمة</th>
<th align="left">الوصف</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">كامل</td>
<td align="left">النتائج الكاملة من <strong>كل</strong> المواقع الجغرافية.</td>
</tr>
<tr class="even">
<td align="left">جزئي</td>
<td align="left">نتائج جزئية من موقع جغرافي واحد أو أكثر. النتائج غير مكتملة بسبب خطأ وقتي.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>استعلام باستخدام خدمة REST

باستخدام طلب GET، يمكنك تحديد معلمات الاستعلام في عنوان URL. باستخدام طلب POST، يمكنك تمرير معلمات الاستعلام في الشكل الأساسي بتنسيق JavaScript Object Notation (JSON).

#### <a name="request-headers"></a>طلب رؤوس

<table>
<thead>
<tr class="header">
<th align="left">الاسم</th>
<th align="left">القيمة</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">نوع المحتوى</td>
<td align="left">application/json;odata=verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>نموذج لطلب GET الذي تم تزينه في **كل المواقع** الجغرافية

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>طلب الحصول النموذجي لهواة **بعض المواقع** الجغرافية

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> تسبق الفاصلات والرموش النقطية في قائمة المواقع الجغرافية ل خاصية MultiGeoSearchConfiguration الحرف **المزدوج** . وذلك لأن طلبات GET تستخدم الفاصلتين لفصل الخصائص ونقطتي الفاصلة لفصل وسيطات الخصائص. إذا لم يتم وضع خط مبلج على أنه حرف هروب، يتم تفسير الخاصية MultiGeoSearchConfiguration بشكل غير صحيح.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>نموذج لطلب النشر الذي تم نشره إلى **كل المواقع** الجغرافية

```http
    {
    "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }
```

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>نموذج لطلب النشر الذي تم نشره في **بعض المواقع** الجغرافية

```http
    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }
```

### <a name="query-using-csom"></a>استعلام باستخدام CSOM

فيما يلي استعلام CSOM النموذجي الذي تم تهيئيته **إلى كل المواقع** الجغرافية:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
