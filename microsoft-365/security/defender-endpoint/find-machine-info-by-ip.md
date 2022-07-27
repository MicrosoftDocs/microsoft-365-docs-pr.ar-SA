---
title: البحث عن معلومات الجهاز بواسطة واجهة برمجة تطبيقات IP الداخلية
description: استخدم واجهة برمجة التطبيقات هذه لإنشاء مكالمات تتعلق بالبحث عن إدخال جهاز حول طابع زمني معين بواسطة IP الداخلي.
keywords: ip، وواجهة برمجة التطبيقات، وواجهة برمجة تطبيقات الرسم البياني، وواجهة برمجة التطبيقات المدعومة، والعثور على الجهاز، ومعلومات الجهاز
search.product: eADQiWindows 10XVcnh
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
ms.custom: api
ms.openlocfilehash: a641784e632574d8b5ba50c59bbc5b987d9375de
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051855"
---
# <a name="find-device-information-by-internal-ip-api"></a>البحث عن معلومات الجهاز بواسطة واجهة برمجة تطبيقات IP الداخلية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

ابحث عن جهاز بواسطة IP الداخلي.

> [!NOTE]
> يجب أن يكون الطابع الزمني في غضون آخر 30 يوما.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
:---|:---|:---
Application|Machine.Read.All|"قراءة كافة ملفات تعريف الجهاز"
Application|Machine.ReadWrite.All|'قراءة كافة معلومات الجهاز وكتابتها'

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/find(timestamp={time},key={IP})
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا كان ناجحا وكان الجهاز موجودا - 200 موافق.
إذا لم يتم العثور على أي جهاز - لم يتم العثور على 404.

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

فيما يلي مثال على الطلب.

```http
GET https://graph.microsoft.com/testwdatppreview/machines/find(timestamp=2018-06-19T10:00:00Z,key='10.166.93.61')
Content-type: application/json
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

سترجع الاستجابة قائمة بجميع الأجهزة التي تم الإبلاغ عن عنوان IP هذا في غضون 16 دقيقة قبل الطابع الزمني وبعده.

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://graph.microsoft.com/testwdatppreview/$metadata#Machines",
    "value": [
        {
            "id": "04c99d46599f078f1c3da3783cf5b95f01ac61bb",
            "computerDnsName": "",
            "firstSeen": "2017-07-06T01:25:04.9480498Z",
            "osPlatform": "Windows10",
...
}
```
