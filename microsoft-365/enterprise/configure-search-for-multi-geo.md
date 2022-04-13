---
title: تكوين البحث عن Microsoft 365 متعدد الجغرافيا
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
description: تعرف على كيفية تكوين البحث في بيئة متعددة المناطق الجغرافية. يمكن لبعض العملاء فقط، مثل OneDrive، إرجاع النتائج في بيئة متعددة المناطق الجغرافية.
ms.openlocfilehash: a6f152a3f226befa8bc060dadd0eed1c0952523c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824915"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>تكوين البحث عن Microsoft 365 متعدد الجغرافيا

في بيئة متعددة المناطق الجغرافية، يحتوي كل موقع جغرافي على فهرس البحث ومركز البحث الخاصين به. عندما يبحث المستخدم، يتم مزج الاستعلام مع كافة الفهارس، ويتم دمج النتائج التي تم إرجاعها.

على سبيل المثال، يمكن لمستخدم في موقع جغرافي واحد البحث عن محتوى مخزن في موقع جغرافي آخر، أو عن محتوى على موقع SharePoint يقتصر على موقع جغرافي مختلف. إذا كان المستخدم لديه حق الوصول إلى هذا المحتوى، فسيعرض البحث النتيجة.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>ما عملاء البحث الذين يعملون في بيئة متعددة المناطق الجغرافية؟

يمكن لهؤلاء العملاء إرجاع النتائج من جميع المواقع الجغرافية:

- OneDrive
- Delve
- الصفحة الرئيسية SharePoint
- مركز البحث
- تطبيقات البحث المخصصة التي تستخدم واجهة برمجة تطبيقات البحث SharePoint

### <a name="onedrive"></a>OneDrive

بمجرد إعداد البيئة متعددة المناطق الجغرافية، يحصل المستخدمون الذين يبحثون في OneDrive على نتائج من جميع المواقع الجغرافية.

### <a name="delve"></a>Delve

بمجرد إعداد البيئة متعددة المناطق الجغرافية، يحصل المستخدمون الذين يبحثون في Delve على نتائج من جميع المواقع الجغرافية.

يعرض موجز Delve وبطاقة ملف التعريف معاينات الملفات المخزنة في الموقع المركزي فقط. بالنسبة للملفات المخزنة في مواقع الأقمار الصناعية، تظهر أيقونة نوع الملف بدلا من ذلك.

### <a name="the-sharepoint-home-page"></a>الصفحة الرئيسية SharePoint

بمجرد إعداد البيئة متعددة المناطق الجغرافية، سيرى المستخدمون الأخبار والمواقع الأخيرة والمتابعة من مواقع جغرافية متعددة على الصفحة الرئيسية SharePoint الخاصة بهم. إذا كانوا يستخدمون مربع البحث على الصفحة الرئيسية SharePoint، فسيحصلون على نتائج مدمجة من مواقع جغرافية متعددة.

### <a name="the-search-center"></a>مركز البحث

بعد إعداد البيئة متعددة المناطق الجغرافية، يستمر كل مركز بحث في إظهار النتائج من موقعه الجغرافي فقط. يجب على المسؤولين [تغيير إعدادات كل مركز بحث](#_Set_up_a_1) للحصول على نتائج من جميع المواقع الجغرافية. بعد ذلك، يحصل المستخدمون الذين يبحثون في مركز البحث على نتائج من جميع المواقع الجغرافية.

### <a name="custom-search-applications"></a>تطبيقات البحث المخصصة

وكالعادة، تتفاعل تطبيقات البحث المخصصة مع فهارس البحث باستخدام واجهات برمجة تطبيقات REST SharePoint البحث الموجودة. للحصول على نتائج من جميع المواقع الجغرافية، أو بعض المواقع الجغرافية، يجب على التطبيق [استدعاء واجهة برمجة التطبيقات وتضمين معلمات الاستعلام متعددة المناطق الجغرافية الجديدة](#_Get_custom_search) في الطلب. يؤدي هذا إلى تشغيل مروحة من الاستعلام إلى جميع المواقع الجغرافية.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>ما المختلف في البحث في بيئة متعددة الجغرافيا؟

بعض ميزات البحث التي قد تكون على دراية بها، تعمل بشكل مختلف في بيئة متعددة المناطق الجغرافية.

<table>
<thead>
<tr class="header">
<th align="left">ميزه</th>
<th align="left">كيفية عملها</th>
<th align="left">الحل البديل</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">النتائج التي تمت ترقيتها</td>
<td align="left">يمكنك إنشاء قواعد الاستعلام مع نتائج تمت ترقيتها على مستويات مختلفة: للمستأجر بأكمله أو لمجموعة مواقع مشتركة أو لموقع. في بيئة متعددة المناطق الجغرافية، حدد النتائج التي تمت ترقيتها على مستوى المستأجر لترقية النتائج إلى مراكز البحث في جميع المواقع الجغرافية. إذا كنت تريد فقط ترقية النتائج في مركز البحث الموجود في الموقع الجغرافي لمجموعة المواقع المشتركة أو الموقع، فحدد النتائج التي تمت ترقيتها على مستوى مجموعة المواقع المشتركة أو على مستوى الموقع. لا يتم ترقية هذه النتائج في مواقع جغرافية أخرى.</td>
<td align="left">إذا لم تكن بحاجة إلى نتائج مختلفة تمت ترقيتها لكل موقع جغرافي، على سبيل المثال قواعد مختلفة للتنقل، نوصي بتعريف النتائج التي تمت ترقيتها على مستوى المستأجر.</td>
</tr>
<tr class="even">
<td align="left">مدققات البحث</td>
<td align="left">يقوم البحث بإرجاع المدققات من جميع المواقع الجغرافية للمستأجر ثم تجميعها. التجميع هو أفضل جهد، ما يعني أن عدد المدققات قد لا يكون دقيقا بنسبة 100٪. بالنسبة لمعظم السيناريوهات المستندة إلى البحث، تكون هذه الدقة كافية.
</td>
<td align="left">بالنسبة للتطبيقات المستندة إلى البحث التي تعتمد على اكتمال المدقق، استعلم عن كل موقع جغرافي بشكل مستقل.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">لا يدعم البحث متعدد المناطق الجغرافية التجميع الديناميكي للمدققات الرقمية.</td>
<td align="left">استخدم <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">المعلمة "منفصلة"</a> للمدققات الرقمية.</td>
</tr>
<tr class="even">
<td align="left">معرفات المستندات</td>
<td align="left">إذا كنت تقوم بتطوير تطبيق يستند إلى البحث يعتمد على معرفات المستندات، فلاحظ أن معرفات المستندات في بيئة متعددة المناطق الجغرافية ليست فريدة عبر المواقع الجغرافية، فهي فريدة لكل موقع جغرافي.</td>
<td align="left">لقد أضفنا عمودا يحدد الموقع الجغرافي. استخدم هذا العمود لتحقيق التفرد. يسمى هذا العمود "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">عدد النتائج</td>
<td align="left">تعرض صفحة نتائج البحث النتائج المجمعة من المواقع الجغرافية، ولكن لا يمكن صفحة أكثر من 500 نتيجة.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">البحث المختلط</td>
<td align="left">في بيئة SharePoint المختلطة مع <a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">البحث المختلط على السحابة</a>، تتم إضافة المحتوى المحلي إلى فهرس Microsoft 365 للموقع المركزي.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>ما الذي لا يتم دعمه للبحث في بيئة متعددة الجغرافيا؟

بعض ميزات البحث التي قد تكون على دراية بها غير مدعومة في بيئة متعددة المناطق الجغرافية.

<table>
<thead>
<tr class="header">
<th align="left">ميزة البحث</th>
<th align="left">ملاحظه</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">مصادقة التطبيق فقط</td>
<td align="left">المصادقة الخاصة بالتطبيق فقط (الوصول المتميز من الخدمات) غير معتمدة في بحث في مواقع جغرافية متعددة.</td>
</tr>
<tr class="even">
<td align="left">الضيوف</td>
<td align="left">يحصل الضيوف فقط على النتائج من الموقع الجغرافي الذي يبحثون منه.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>كيف يعمل البحث في بيئة متعددة المناطق الجغرافية؟

يستخدم جميع عملاء البحث واجهات برمجة التطبيقات الموجودة SharePoint Search REST للتفاعل مع فهارس البحث.

![رسم تخطيطي يوضح كيفية تفاعل واجهات برمجة تطبيقات REST للبحث SharePoint مع فهارس البحث.](../media/configure-search-for-multi-geo-image1-1.png)

1. يستدعي عميل البحث نقطة نهاية Search REST مع خاصية الاستعلام EnableMultiGeoSearch= true.
2. يتم إرسال الاستعلام إلى جميع المواقع الجغرافية في المستأجر.
3. يتم دمج نتائج البحث من كل موقع جغرافي وترتيبها.
4. يحصل العميل على نتائج بحث موحدة.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>لاحظ أننا لا ندمج نتائج البحث حتى نتلقى نتائج من جميع المواقع الجغرافية. وهذا يعني أن عمليات البحث متعددة المناطق الجغرافية لها زمن انتقال إضافي مقارنة بعمليات البحث في بيئة ذات موقع جغرافي واحد فقط.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>الحصول على مركز بحث لإظهار النتائج من جميع المواقع الجغرافية

يحتوي كل مركز بحث على عدة أعمدة، كما يتعين عليك إعداد كل عمودي بشكل فردي.

1. تأكد من تنفيذ هذه الخطوات باستخدام حساب لديه الإذن لتحرير صفحة نتائج البحث وجزء ويب نتائج البحث.

2. الانتقال إلى صفحة نتائج البحث (راجع [قائمة](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) صفحات نتائج البحث)

3. حدد الرأسي الذي تريد إعداده، وانقر فوق **أيقونة الترس الإعدادات** في الزاوية العلوية اليسرى، ثم انقر فوق **"تحرير الصفحة**". يتم فتح صفحة نتائج البحث في وضع التحرير.

   ![تحرير تحديد الصفحة في الإعدادات.](../media/configure-search-for-multi-geo-image2.png)

4. في جزء ويب "نتائج البحث"، انقل المؤشر إلى الزاوية العلوية اليسرى من جزء ويب، وانقر فوق السهم، ثم انقر فوق **"تحرير جزء ويب** " في القائمة. يتم فتح جزء أداة جزء ويب لنتائج البحث أسفل الشريط في الجزء العلوي الأيسر من الصفحة.

   ![تحرير تحديد جزء ويب.](../media/configure-search-for-multi-geo-image3.png)

5. في جزء أدوات جزء ويب، في قسم **الإعدادات**، ضمن **إعدادات التحكم بالنتائج**، حدد **"إظهار النتائج متعددة المناطق الجغرافية**" للحصول على جزء ويب "نتائج البحث" لعرض النتائج من كافة المواقع الجغرافية.

6. انقر فوق **"موافق** " لحفظ التغيير وإغلاق جزء أداة جزء ويب.

7. تحقق من التغييرات التي أجريتها على جزء ويب "نتائج البحث" بالنقر فوق **"إيداع"** ضمن علامة التبويب "صفحة" في القائمة الرئيسية.

8. انشر التغييرات باستخدام الارتباط المتوفر في الملاحظة في أعلى الصفحة.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>الحصول على تطبيقات بحث مخصصة لإظهار النتائج من كافة المواقع الجغرافية أو بعض المواقع الجغرافية

تحصل تطبيقات البحث المخصصة على نتائج من جميع المواقع الجغرافية أو بعضها عن طريق تحديد معلمات الاستعلام مع الطلب إلى واجهة برمجة تطبيقات REST للبحث SharePoint. اعتمادا على معلمات الاستعلام، يتم توجيه الاستعلام إلى جميع المواقع الجغرافية، أو إلى بعض المواقع الجغرافية. على سبيل المثال، إذا كنت بحاجة فقط إلى الاستعلام عن مجموعة فرعية من المواقع الجغرافية للعثور على المعلومات ذات الصلة، يمكنك التحكم في المروحة لهذه المواقع فقط. إذا نجح الطلب، فإن واجهة برمجة تطبيقات REST للبحث SharePoint ترجع بيانات الاستجابة.

### <a name="requirement"></a>شرط

لكل موقع جغرافي، يجب التأكد من منح جميع المستخدمين في المؤسسة مستوى إذن **القراءة** لموقع الويب الجذر (على سبيل المثال contosoAPAC.sharepoint.com/ وcontosoEU.sharepoint.com/). [تعرف على الأذونات](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>معلمات الاستعلام

EnableMultiGeoSearch - هذه قيمة منطقية تحدد ما إذا كان سيتم تحريك الاستعلام إلى فهارس المواقع الجغرافية الأخرى للمستأجر متعدد المناطق الجغرافية. قم بتعيينه إلى **"صواب** " لسحب الاستعلام؛ **خطأ** عدم تصغير الاستعلام. إذا لم تقم بتضمين هذه المعلمة، تكون القيمة الافتراضية **خاطئة**، إلا عند إجراء استدعاء REST API مقابل موقع يستخدم قالب مركز البحث للمؤسسات، في هذه الحالة تكون القيمة الافتراضية **صحيحة**. إذا كنت تستخدم المعلمة في بيئة غير متعددة المناطق الجغرافية، يتم تجاهل المعلمة.

ClientType - هذه سلسلة. أدخل اسم عميل فريدا لكل تطبيق بحث. إذا لم تقم بتضمين هذه المعلمة، فلن يتم تمرير الاستعلام إلى مواقع جغرافية أخرى.

MultiGeoSearchConfiguration - هذه قائمة اختيارية للمواقع الجغرافية في المستأجر متعدد المناطق الجغرافية لتفعيل الاستعلام عندما يكون **EnableMultiGeoSearch** **صحيحا**. إذا لم تقم بتضمين هذه المعلمة، أو اتركها فارغة، يتم تمرير الاستعلام إلى كافة المواقع الجغرافية. لكل موقع جغرافي، أدخل العناصر التالية، بتنسيق JSON:

<table>
<thead>
<tr class="header">
<th align="left">البند</th>
<th align="left">الوصف</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">تحديد البيانات</td>
<td align="left">الموقع الجغرافي، على سبيل المثال NAM.</td>
</tr>
<tr class="even">
<td align="left">نقطه النهايه</td>
<td align="left">نقطة النهاية التي يجب الاتصال بها، على سبيل المثال https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">معرف المصدر</td>
<td align="left">المعرف الفريد العمومي لمصدر النتائج، على سبيل المثال B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

إذا حذفت DataLocation أو EndPoint، أو إذا تم تكرار DataLocation، فسيفشل الطلب. [يمكنك الحصول على معلومات حول نقطة نهاية المواقع الجغرافية للمستأجر باستخدام Microsoft Graph](/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>بيانات الاستجابة

MultiGeoSearchStatus – هذه خاصية ترجعها واجهة برمجة تطبيقات البحث SharePoint استجابة لطلب. قيمة الخاصية هي سلسلة وتعطي المعلومات التالية حول النتائج التي ترجعها واجهة برمجة تطبيقات البحث SharePoint:

<table>
<thead>
<tr class="header">
<th align="left">قيمه</th>
<th align="left">الوصف</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">الكامل</td>
<td align="left">النتائج الكاملة من <strong>جميع</strong> المواقع الجغرافية.</td>
</tr>
<tr class="even">
<td align="left">الجزئي</td>
<td align="left">نتائج جزئية من موقع جغرافي واحد أو أكثر. النتائج غير مكتملة بسبب خطأ عابر.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>الاستعلام باستخدام خدمة REST

مع طلب GET، يمكنك تحديد معلمات الاستعلام في عنوان URL. مع طلب POST، يمكنك تمرير معلمات الاستعلام في النص الأساسي بتنسيق JavaScript Object Notation (JSON).

#### <a name="request-headers"></a>عناوين الطلبات

<table>
<thead>
<tr class="header">
<th align="left">الاسم</th>
<th align="left">قيمه</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">نوع المحتوى</td>
<td align="left">تطبيق/json;odata=verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>نموذج طلب GET الذي تم توزيعه على **جميع** المواقع الجغرافية

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>نموذج طلب GET لسحب **بعض** المواقع الجغرافية

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> تسبق الفاصلات والنقطتان في قائمة المواقع الجغرافية لخاصية MultiGeoSearchConfiguration حرف **خط مائل عكسي** . وذلك لأن طلبات GET تستخدم نقطتين لفصل الخصائص والفاصلات لفصل وسيطات الخصائص. بدون خط مائل عكسي كحرف إلغاء، يتم تفسير الخاصية MultiGeoSearchConfiguration بشكل خاطئ.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>نموذج طلب POST الذي تم توزيعه على **جميع** المواقع الجغرافية

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

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>نموذج طلب POST الذي تم نشره في **بعض** المواقع الجغرافية

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

فيما يلي نموذج استعلام CSOM الذي تم توزيعه على **جميع** المواقع الجغرافية:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
