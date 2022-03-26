---
title: كيفية نشر Defender for Endpoint على Linux مع Chef
description: تعرف على كيفية نشر Defender for Endpoint على Linux مع Chef
keywords: microsoft، defender، atp، linux، المسح الضوئي، برنامج الحماية من الفيروسات، microsoft defender لنقطة النهاية (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 799fc4d163b120b4197b6cd044efe4740e4a3cc7
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63575486"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>نشر Defender لنقطة النهاية على Linux باستخدام Chef

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

قبل البدء: قم بتثبيت إلغاء التثبيت إذا لم يكن مثبتا بالفعل.

مكونات Chef مثبتة بالفعل ومستودع Chef موجود (يقوم الشيف بإنشاء repo \<reponame\>) لتخزين دفتر الطهي الذي سيتم استخدامه لنشره في Defender for Endpoint على خوادم Linux المدارة من قبل Chef.

يمكنك إنشاء مصنف طبخ جديد في المستودع الموجود عن طريق تشغيل الأمر التالي من داخل مجلد كتب الطهي الموجود في مستودع الطهاة:

```bash
chef generate cookbook mdatp
```

سينشئ هذا الأمر بنية مجلد جديدة لمكتب الطهي الجديد المسمى mdatp. يمكنك أيضا استخدام مصنف طبخ موجود إذا كان لديك بالفعل واحد تريد استخدامه لإضافة نشر MDE فيه.
بعد إنشاء مصنف الطهي، قم بإنشاء مجلد ملفات داخل مجلد كتاب الطهي الذي تم إنشاؤه للتو:

```bash
mkdir mdatp/files
```

قم بنقل ملف Zip لورد خادم Linux الذي يمكن تنزيله من Microsoft 365 Defender إلى مجلد الملفات الجديد هذا.

على محطة عمل Chef، انتقل إلى مجلد mdatp/recipes. يتم إنشاء هذا المجلد عند إنشاء دفتر الطهي. استخدم محرر النص المفضل لديك (مثل vi أو nano) لإضافة الإرشادات التالية إلى نهاية الملف الافتراضي.rb:

- include_recipe '::onboard_mdatp'
- include_recipe '::install_mdatp'

ثم احفظ الملف الافتراضي.rb وأغلقه.

بعد ذلك، أنشئ ملف وصفة install_mdatp.rb في مجلد الوصفات وأضف هذا النص إلى الملف:

```powershell
#Add Microsoft Defender
Repo
case node['platform_family']
when 'debian'
 apt_repository 'MDAPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'focal'
   repo_name          'microsoft-prod'
   components         ['main']
   trusted            true
   uri                "https://packages.microsoft.com/config/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/config/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end
```

ستحتاج إلى تعديل رقم الإصدار والتوزيع واسم إعادة النشر ليتطابق مع الإصدار الذي تقوم بنشره والقناة التي تريد نشرها.
بعد ذلك، يجب إنشاء ملف onboard_mdatp.rb في مجلد mdatp/recipies. أضف النص التالي إلى هذا الملف:

```powershell
#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
zip_path = "/path/to/chef-repo/cookbooks/mdatp/files/WindowsDefenderATPOnboardingPackage.zip"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Extract WindowsDefenderATPOnbaordingPackage.zip into /etc/opt/microsoft/mdatp

bash 'Extract Onbaording Json MDATP' do
  code <<-EOS
  unzip #{zip_path} -d #{mdatp}
  EOS
  not_if { ::File.exist?('/etc/opt/microsoft/mdatp/mdatp_onboard.json') }
end
```

تأكد من تحديث اسم المسار إلى موقع ملف الboarding.
لاختبار نشره على محطة عمل Chef، ما عليك سوى تشغيل ``sudo chef-client -z -o mdatp``.
بعد النشر، يجب عليك التفكير في إنشاء ملف تكوين ونشره إلى الخوادم استنادا إلى تعيين تفضيلات [ل Microsoft Defender ل Endpoint على Linux](/linux-preferences.md).
بعد إنشاء ملف التكوين واختباره، يمكنك وضعه في مجلد ملفات/mdatp/cookbook حيث قمت أيضا بوضع حزمة التهيئة. بعد ذلك، يمكنك إنشاء ملف settings_mdatp.rb في مجلد mdatp/recipies وإضافة هذا النص:

```powershell
#Copy the configuration file
cookbook_file '/etc/opt/microsoft/mdatp/managed/mdatp_managed.json' do
  source 'mdatp_managed.json'
  owner 'root'
  group 'root'
  mode '0755'
  action :create
end
```

لتضمين هذه الخطوة كجزء من الوصفة، ما عليك سوى إضافة include_recipe ':: settings_mdatp' إلى الملف الافتراضي.rb ضمن مجلد الوصفات.
يمكنك أيضا استخدام crontab لجدولة التحديثات التلقائية جدولة تحديث [ل Microsoft Defender ل Endpoint (Linux)](linux-update-MDE-Linux.md).

إلغاء تثبيت مصنف طباخ MDATP:

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```
