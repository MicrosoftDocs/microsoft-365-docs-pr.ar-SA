---
title: التشفير في Azure
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: تعرف على التشفير المتوفر في Azure، مثل تشفير قرص Azure
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f3672800b6f90277195a63b640911ea1ed24cac9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566743"
---
# <a name="encryption-in-azure"></a>التشفير في Azure

تساعد الضمانات التقنية في Azure، مثل الاتصالات المشفرة والعمليات التشغيلية، في الحفاظ على أمان البيانات. كما أن لديك المرونة اللازمة لتنفيذ ميزات تشفير إضافية وإدارة مفاتيح التشفير الخاصة بك. بغض النظر عن تكوين العميل، تطبق Microsoft التشفير لحماية بيانات العملاء في Azure. تمكنك Microsoft أيضا من التحكم في بياناتك المستضافة في Azure من خلال مجموعة من التقنيات المتقدمة لتشفير مفاتيح التشفير والتحكم بها وإدارتها والتحكم في الوصول إلى البيانات وتدقيقها. بالإضافة إلى ذلك، توفر Azure Storage مجموعة شاملة من إمكانات الأمان التي تمكن المطورين معا من إنشاء تطبيقات آمنة.

يوفر Azure العديد من الآليات لحماية البيانات عندما تنتقل من موقع إلى آخر. تستخدم Microsoft TLS لحماية البيانات عند التنقل بين الخدمات السحابية والعملاء. تتفاوض مراكز بيانات Microsoft بشأن اتصال TLS بأنظمت العميل التي تتصل ب خدمات Azure. تحمي خدمة "إعادة التشغيل المثالية" (PFS) الاتصالات بين أنظمة العملاء وخدمات Microsoft السحابية من خلال المفاتيح الفريدة. تستخدم Connections أيضا أطوال مفاتيح التشفير 2048 بت المستندة إلى RSA. تجعل هذه المجموعة من الصعب على شخص ما اعتراض البيانات أثناء النقل والوصول إليها.

يمكن تأمين البيانات أثناء نقلها بين تطبيق و Azure باستخدام التشفير من جانب العميل [](/azure/storage/storage-client-side-encryption)أو HTTPS أو SMB 3.0. يمكنك تمكين التشفير لحركة المرور بين الأجهزة الظاهرية الخاصة بك والمستخدمين. باستخدام [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/)، يمكنك استخدام بروتوكول IPsec القياسي في المجال لتشفير حركة المرور بين بوابة VPN الخاصة بالشركة و Azure وكذلك بين أجهزة VMs الموجودة على الشبكة الظاهرية.

بالنسبة للبيانات في وضع الراحة، يوفر Azure العديد من خيارات التشفير، مثل دعم AES-256، مما يوفر لك المرونة لاختيار سيناريو تخزين البيانات الذي يلبي احتياجاتك على أفضل نحو. يمكن تشفير البيانات تلقائيا عند كتابتها في Azure Storage باستخدام تشفير خدمة التخزين[](/azure/storage/storage-service-encryption)، كما يمكن تشفير نظام التشغيل وأقراص البيانات التي تستخدمها أجهزة VMs. لمزيد من المعلومات، راجع [توصيات الأمان Windows الظاهرية في Azure](/azure/security/azure-security-disk-encryption). بالإضافة إلى ذلك، يمكن منح حق الوصول المفوض إلى كائنات البيانات في Azure Storage باستخدام [تواقيع الوصول المشترك](/azure/storage/storage-dotnet-shared-access-signature-part-1). يوفر Azure أيضا تشفير البيانات في وضع الراحة باستخدام تشفير البيانات الشفاف ل [Azure SQL قاعدة البيانات ومستودع البيانات](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

للحصول على مزيد من المعلومات حول التشفير في Azure، راجع نظرة عامة حول تشفير [Azure](/azure/security/security-azure-encryption-overview) و تشفير بيانات [Azure في حالة راحة](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>تشفير قرص Azure

يمكنك تشفير قرص Azure من تشفير Windows الأساسية ل Linux كخدمة (IaaS) قرصي VM. يعمل تشفير قرص Azure على الاستفادة من ميزة BitLocker Windows وميزة DM-Crypt Linux لتوفير تشفير على مستوى الصوت لنظام التشغيل وأقراص البيانات. كما يضمن أيضا تشفير كل البيانات الموجودة على أقراص VM في مخزن Azure. إن تشفير قرص Azure متكامل مع مخزن مفاتيح Azure لمساعدتك على التحكم في مفاتيح التشفير وأسرارها وإدارتها وتدقيقها.

لمزيد من المعلومات، راجع [توصيات الأمان Windows الظاهرية في Azure](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>تشفير خدمة تخزين Azure

باستخدام [تشفير خدمة تخزين Azure](/azure/storage/storage-service-encryption)، تقوم Azure Storage بتشفير البيانات تلقائيا قبل الاستمرار في تخزين البيانات وفك تشفيرها قبل استردادها. تكون عمليات التشفير وفك التشفير والإدارة الأساسية شفافة تماما للمستخدمين. يمكن استخدام تشفير خدمة تخزين Azure ل [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/) [وملفات Azure](https://azure.microsoft.com/services/storage/files/). يمكنك أيضا استخدام مفاتيح التشفير المدارة من Microsoft مع تشفير خدمة تخزين Azure، أو يمكنك استخدام مفاتيح التشفير الخاصة بك. (للحصول على معلومات حول استخدام المفاتيح الخاصة بك، راجع [تشفير خدمة التخزين باستخدام المفاتيح المدارة من قبل العملاء في مخزن مفاتيح Azure](/azure/storage/common/storage-service-encryption-customer-managed-keys). للحصول على معلومات حول استخدام المفاتيح المدارة من Microsoft، راجع [تشفير خدمة التخزين للبيانات في Rest](/azure/storage/storage-service-encryption).) بالإضافة إلى ذلك، يمكنك أتمتة استخدام التشفير. على سبيل المثال، يمكنك تمكين تشفير خدمة التخزين أو تعطيله برمجيا على حساب تخزين باستخدام [AZure Storage Resource Resource API (REST API](/rest/api/storagerp/)) أو مكتبة عميل موفري موارد التخزين ل [.NET](/dotnet/api/overview/azure/storage) أو [Azure PowerShell](/powershell/azureps-cmdlets-docs) أو [Azure CLI](/azure/storage/storage-azure-cli).

تستخدم Microsoft 365 الخدمات Azure لتخزين البيانات. على سبيل المثال، SharePoint عبر الإنترنت OneDrive for Business البيانات في مساحة تخزين Azure Blob، ويخزن Microsoft Teams البيانات لخدمة المحادثة الخاصة به في الجداول والمقابض المؤقتة وفي قوائم الانتظار. بالإضافة إلى ذلك، تخزن ميزة إدارة التوافق في مركز التوافق في Microsoft 365 البيانات التي أدخلها العميل والتي يتم تخزينها في نموذج مشفر في [Azureاعماوس DB](/azure/cosmos-db/database-encryption-at-rest)، وهو نظام أساسي كخدمة (PaaS)، قاعدة بيانات متعددة النماذج موزعة على مستوى العالم. يقوم تشفير خدمة تخزين Azure بتشفير البيانات المخزنة في تخزين Azure Blob وفي الجداول، كما يقوم تشفير قرص Azure بتشفير البيانات في قوائم الانتظار، بالإضافة إلى قرصي Windows و IaaS الظاهريين لتوفير تشفير كمية لنظام التشغيل وقرص البيانات. يضمن الحل تشفير كل البيانات الموجودة على أقراص الجهاز الظاهرية في مخزن Azure. [يتم تنفيذ التشفير في Azureاعما DB](/azure/cosmos-db/database-encryption-at-rest) باستخدام العديد من تقنيات الأمان، بما في ذلك أنظمة التخزين الأساسية الآمنة والشبكات المشفرة و واجهات برمجة تطبيقات التشفير.

## <a name="azure-key-vault"></a>مخزن مفاتيح Azure

لا تكون الإدارة الآمنة للمفتاح أساسية فقط في أفضل ممارسات التشفير؛ بل هي أيضا أساسية بالنسبة إلى ممارسات التشفير. كما أنه ضروري لحماية البيانات في السحابة. [يتيح لك Azure Key Vault](/azure/key-vault/key-vault-whatis) تشفير المفاتيح وأسرار صغيرة مثل كلمات المرور التي تستخدم المفاتيح المخزنة في الوحدات النمطية لأمان الأجهزة (HSMs). إن Azure Key Vault هو الحل الموصى به من Microsoft لإدارة الوصول إلى مفاتيح التشفير المستخدمة بواسطة خدمات السحابة والتحكم فيها. يمكن تعيين أذونات الوصول إلى المفاتيح للخدمات أو للمستخدمين الذين لديهم حسابات Azure Active Directory. يعفي Azure Key Vault المؤسسات من الحاجة إلى تكوين HSMs وبرامج الإدارة الأساسية وتصحيحها والمحافظة عليها. باستخدام Azure Key Vault، لا ترى Microsoft مفاتيحك وتطبيقاتك لا تملك حق الوصول المباشر إليها؛ يمكنك الاحتفاظ بالتحكم. يمكنك أيضا استيراد المفاتيح أو إنشاءها في HSMs. يمكن أن تقوم المؤسسات التي لديها اشتراك يتضمن Azure Information Protection بتكوين مستأجر Azure Information Protection لاستخدام مفتاح مدار بواسطة العملاء [إحضار](/information-protection/plan-design/byok-price-restrictions) المفتاح الخاص بك (BYOK)) وتسجيل [استخدامه](/information-protection/deploy-use/log-analyze-usage).