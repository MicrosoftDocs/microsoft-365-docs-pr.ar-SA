---
title: واجهة برمجة تطبيقات قاعدة الاختبار & SDK
description: واجهة برمجة تطبيقات قاعدة الاختبار & SDK
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 6ae0fdf9cc49faaaff84eb3f96e076d1efba8a4c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077439"
---
# <a name="manage-your-resource-with-sdk--apis"></a>إدارة المورد باستخدام SDK & واجهات برمجة التطبيقات

الأتمتة هي جانب رئيسي من DevOps وتطوير التطوير السريع. هل تبحث عن إدارة قاعدة الاختبار لموارد Microsoft 365، والحصول على نتائج الاختبار برمجيا، ودمجها مع أدوات التكامل المستمر لدينا؟ يمكن أن تساعدك واجهات برمجة تطبيقات قاعدة الاختبار/SDK على تحقيق كل هذه وأكثر!

تمكن واجهات برمجة التطبيقات/SDK هذه محترفي تكنولوجيا المعلومات ومطوري التطبيقات من:

- إدارة حسابات قاعدة الاختبار، بما في ذلك الإنشاء والتحديث والإلحاق.
- إدارة حزم التطبيقات، بما في ذلك إنشاء حزمة وتحديثها وحذفها وتنزيلها.
- احصل على ملخص الاختبار ونتائج الاختبار التفصيلية ونتائج التحليل. تتضمن نتيجة التحليل تحليل انحدار وحدة المعالجة المركزية وتحليل استخدام وحدة المعالجة المركزية وتحليل انحدار الذاكرة وتحليل استخدام الذاكرة.
- تنزيل نتائج الاختبار وتسجيل فيديو تنفيذ الاختبار.

راجع المخطط التفصيلي المفصل خطوة بخطوة أدناه لمعرفة كيفية الوصول إلى هذه الإمكانية الجديدة في قاعدة الاختبار لخدمة Microsoft 365.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>مثال خطوة بخطوة على إنشاء حساب قاعدة الاختبار باستخدام Python SDK

1. المتطلبات الأساسية:

   - التثبيت أدناه المكونات المطلوبة:

     - [حساب Azure مع اشتراك نشط](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) إذا لم يكن لديك اشتراك
     - [Python 2.7+ أو 3.6+](https://www.python.org/downloads)
     - [واجهة Command-Line Azure (CLI)](/cli/azure/install-azure-cli)

   - تثبيت حزم المكتبة باستخدام تثبيت pip من وحدة التحكم

     ```console
     pip install azure-identity
     pip install azure-mgmt-testbase
     ```

   - المصادقة في بيئة التطوير

     عند تصحيح أخطاء التعليمات البرمجية وتنفيذها محليا، من المعتاد للمطورين استخدام حساباتهم الخاصة لمصادقة المكالمات إلى خدمات Azure. تدعم حزمة azure-identity المصادقة من خلال Azure CLI لتبسيط التطوير المحلي. لتسجيل الدخول إلى Azure CLI، قم بتشغيل `az login`. على نظام مع مستعرض ويب افتراضي، سيقوم Azure CLI بتشغيل المستعرض لمصادقة مستخدم.

     تحقق من [كيفية مصادقة تطبيقات Python مع خدمات Azure| Microsoft Docs](/azure/developer/python/azure-sdk-authenticate) وأساليب <https://pypi.org/project/azure-identity/> المصادقة المعتمدة الأخرى.

   - إنشاء مجموعة موارد بالاسم المطلوب الذي سيتم استخدامه في الخطوات التالية.

2. تغطي القصاصة البرمجية أدناه التدفق لإنشاء حساب قاعدة الاختبار بما في ذلك

   - طلب بيانات الاعتماد عبر Azure CLI للتفاعل مع Azure
   - تهيئة عميل Test Base SDK باستخدام بيانات الاعتماد ومعرف الاشتراك للعمليات اللاحقة
   - استدعاء begin_create من نموذج test_base_accounts لإنشاء حساب قاعدة الاختبار

   انسخ التعليمات البرمجية إلى بيئة تطوير Python، واستبدل "subscription-id" بمعرف اشتراك Azure و"resource-group-name" بمجموعة الموارد التي أنشأتها أعلاه.

   ```python
   from azure.identity import AzureCliCredential
   from azure.mgmt.testbase import TestBase
   from azure.mgmt.testbase.models import TestBaseAccountResource
   from azure.mgmt.testbase.models import TestBaseAccountSKU

   # requesting token from Azure CLI for request
   # For other authentication approaches, please see: https://pypi.org/project/azure-identity/
   credential = AzureCliCredential()
   subscription_id = "<subscription-id>"
   resource_group = "<resource-group-name>"
   testBaseAccount_name = "contoso-testbaseAccount"
   testBaseAccount_location = "global"
   sku_name = "S0"
   sku_tier = "Standard"
   sku_locations = {"global"}
  
   # Create client
   testBase_client = TestBase(credential, subscription_id)
  
   # Create sku for test base account
   sku = TestBaseAccountSKU(name=sku_name, tier=sku_tier, locations=sku_locations)
  
   # Create test base account
   parameters = TestBaseAccountResource(location=testBaseAccount_location, sku=sku)
   testBaseAccount = testBase_client.test_base_accounts.begin_create(resource_group, testBaseAccount_name, parameters).result()
   print("Create test base account:\n{}".format(testBaseAccount))
   ```

## <a name="learn-more"></a>التعرف على المزيد

تحقق من الارتباطات أدناه لمعرفة المزيد من التفاصيل حول SDK & API.

**اشتراك Azure**:

- [حساب Azure مع اشتراك نشط](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Python SDK**:

- [اختبار وثائق Python SDK الأساسية](/python/api/overview/azure/mgmt-testbase-readme)
- [نموذج اختبار Python SDK الأساسي](https://aka.ms/testbase-sample-py)
- [نمط الاستخدام العام ل Azure ل Python SDK](/azure/developer/python/sdk/azure-sdk-library-usage-patterns)

**واجهة برمجة تطبيقات REST**:

- [وثائق واجهة برمجة تطبيقات REST](https://aka.ms/testbase-api)
