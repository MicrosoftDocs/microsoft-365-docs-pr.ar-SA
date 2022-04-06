---
title: اختبار API & SDK
description: اختبار API & SDK
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
ms.openlocfilehash: f7e5edeeac79b417bcb41f8607c46fc8894ea4fc
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "63583719"
---
# <a name="manage-your-resource-with-sdk--apis"></a>إدارة المورد باستخدام SDK & واجهات برمجة التطبيقات
التنفيذ التلقائي هو أحد الجوانب الأساسية لتطوير التطوير التطويري والتطوير التطويري ل DevOps. هل تبحث عن إدارة Test Base Microsoft 365 الموارد والحصول على نتائج الاختبار برمجيا ودمجها مع أدوات CI لدينا؟ يمكن أن تساعدك واجهات برمجة التطبيقات الأساسية للاختبار/SDK على تحقيق كل هذه الأشياء والمزيد! 

تمكن واجهات برمجة التطبيقات/SDK هذه محترفي تكنولوجيا المعلومات ومطوري التطبيقات من القيام ب: 
- إدارة حسابات Test Base، بما في ذلك إنشاء وتحديث و إيقاف التشغيل. 
- إدارة حزم التطبيقات، بما في ذلك إنشاء حزمة وتحديثها وحذفها وتنزيلها. 
- احصل على ملخص الاختبار ونتائج الاختبارات المفصلة ونتائج التحليل. تتضمن نتيجة التحليل تحليل انحدار CPU وتحليل استخدام CPU وتحليل انحدار الذاكرة وتحليل استخدام الذاكرة. 
- قم بتنزيل نتائج الاختبار وتسجيل فيديو تنفيذ الاختبار.  

اطلع على المخطط التفصيلي خطوة بخطوة أدناه لمعرفة كيفية الوصول إلى هذه الإمكانية الجديدة في Test Base Microsoft 365 الخدمة.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>مثال خطوة بخطوة لإنشاء حساب Test Base باستخدام Python SDK

1. المتطلبات الأساسية: 

- تثبيت أدناه المكونات المطلوبة: 

    [حساب Azure مع اشتراك نشط](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) إذا لم يكن لديك اشتراك<br>
    [Python 2.7+ أو 3.6+](https://www.python.org/downloads)<br>
    [واجهة azure Command-Line (CLI)](/cli/azure/install-azure-cli) <br>

- تثبيت حزم المكتبة باستخدام تثبيت النقطة من وحدة التحكم 

```
pip install azure-identity 
pip install azure-mgmt-testbase
```

- المصادقة في بيئة dev 

عند تصحيح الأخطاء وتنفيذ التعليمات البرمجية محليا، من المعتاد أن يستخدم المطورون حساباتهم الخاصة لمصادقة المكالمات إلى خدمات Azure. تدعم حزمة azure-identity المصادقة من خلال Azure CLI لتبسيط عملية التطوير المحلي. تسجيل الدخول إلى Azure CLI، قم بتشغيل ```az login ```. في نظام به مستعرض ويب افتراضي، سيطلق Azure CLI المستعرض لمصادقة المستخدم. 

تحقق [من كيفية مصادقة تطبيقات Python باستخدام خدمات Azure| مستندات Microsoft ولطرق](/azure/developer/python/azure-sdk-authenticate) [https://pypi.org/project/azure-identity/](https://pypi.org/project/azure-identity/) المصادقة المعتمدة الأخرى. 

 - قم بإنشاء مجموعة موارد باستخدام الاسم المطلوب الذي سيتم استخدامه في الخطوات التالية. 

2. تغطي قصاصة التعليمات البرمجية أدناه التدفق لإنشاء حساب Test Base بما في ذلك 

- طلب بيانات الاعتماد عبر Azure CLI للتفاعل مع Azure 
- تهيي عميل Test Base SDK باستخدام بيانات الاعتماد وم ID الاشتراك للعمليات اللاحقة 
- استدعاء begin_create من test_base_accounts لإنشاء حساب Test Base 

انسخ التعليمة البرمجية إلى بيئة تطوير Python، واستبدل "id الاشتراك" بم ID اشتراك Azure و"مورد-مجموعة-اسم" مع مجموعة الموارد التي أنشأتها أعلاه. 

 
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

**اشتراك Azure** 

- [حساب Azure مع اشتراك نشط](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Python SDK** 

- [Test Base Python SDK Documentation](/python/api/overview/azure/mgmt-testbase-readme)
- [نموذج Test Base Python SDK](https://aka.ms/testbase-sample-py)
- [نمط استخدام Azure العام ل Python SDK](/azure/developer/python/azure-sdk-overview#provision-and-manage-azure-resources-with-management-libraries)

**REST API**  

- [وثائق REST API](https://aka.ms/testbase-api)  
