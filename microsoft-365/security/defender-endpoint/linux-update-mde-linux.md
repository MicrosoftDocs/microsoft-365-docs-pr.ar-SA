---
title: كيفية جدولة تحديث ل Microsoft Defender ل Endpoint (Linux)
description: تعرف على كيفية جدولة تحديث ل Microsoft Defender ل Endpoint (Linux) لحماية أصول مؤسستك بشكل أفضل.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، عمليات الفحص، الحماية من الفيروسات، microsoft defender لنقطة النهاية (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6fb3141b33948c5c452096c83a2f02657c199575
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/12/2022
ms.locfileid: "63573271"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>جدولة تحديث ل Microsoft Defender ل Endpoint (Linux)

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

لتشغيل تحديث على Microsoft Defender ل Endpoint على Linux، راجع نشر تحديثات [ل Microsoft Defender ل Endpoint على Linux](/microsoft-365/security/defender-endpoint/linux-updates).

لدى Linux (و Unix) أداة تسمى **crontab** (مماثلة لجدول المهام) لكي تتمكن من تشغيل المهام المجدولة.

## <a name="pre-requisite"></a>المتطلبات الأساسية

> [!NOTE]
> للحصول على قائمة بكل المناطق الزمنية، يمكنك تشغيل الأمر التالي: `timedatectl list-timezones`
>
> أمثلة عن المنطقة الزمنية:
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>لتعيين مهمة Cron

استخدم الأوامر التالية:

### <a name="backup-crontab-entries"></a>إدخالات الكرونتاب الاحتياطية

```bash
sudo crontab -l > /var/tmp/cron_backup_201118.dat
```

> [!NOTE]
> حيث 201118 == YYMMDD

> [!TIP]
> قم بذلك قبل التحرير أو الإزالة.

لتحرير الماكرونتاب، وإضافة مهمة جديدة كمستخدم جذر:

```bash
sudo crontab -e
```

> [!NOTE]
> المحرر الافتراضي هو VIM.

قد ترى:

```output
0****/etc/opt/microsoft/mdatp/logrorate.sh
```

و

```output
02**sat /bin/mdatp scan quick>~/mdatp_cron_job.log
```

راجع [جدولة عمليات الفحص باستخدام Microsoft Defender ل Endpoint (Linux)](linux-schedule-scan-mde.md)

اضغط على "إدراج"

أضف الإدخالات التالية:

```bash
CRON_TZ=America/Los_Angeles
```

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>! RHEL والمتغيرات (CentOS و Oracle Linux)
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo yum update mdatp -y >> ~/mdatp_cron_job.log
> ```

> #<a name="sles-and-variants"></a>! SLES والمتغيرات
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo zypper update mdatp >> ~/mdatp_cron_job.log
> ```

> #<a name="ubuntu-and-debian-systems"></a>! أنظمة Ubuntu و Debian
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo apt-get install --only-upgrade mdatp >> ~/mdatp_cron_job.log
> ```

> [!NOTE]
> في الأمثلة أعلاه، نقوم بإعداده على 00 دقيقة، 6 صباحا(الساعة بتنسيق 24 ساعة)، أي يوم من الشهر، أي في أي شهر، في أيام الأحد. [$(date +\%d) -le 15] == لن يتم تشغيله إلا إذا كان مساويا أو أقل من اليوم الخامس عشر (الأسبوع الثالث). مما يعني أنه سيتم تشغيله كل ثلاثة أيام الأحد (7) من الشهر الساعة 6:00 صباحا. Pacific (UTC -8).

اضغط على "Esc"

اكتب "`:wq`" w/o علامات الاقتباس المزدوجة.

> [!NOTE]
> w == write, q == quit

لعرض مهام cron، اكتب `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="تحديث Defender for Endpoint على Linux.":::

لفحص تشغيل مهمة cron:

```bash
sudo grep mdatp /var/log/cron
```

لفحص mdatp_cron_job.log

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>بالنسبة لهؤلاء الذين يستخدمون Ansible أو Chef أو

استخدم الأوامر التالية:

### <a name="to-set-cron-jobs-in-ansible"></a>لتعيين مهام cron في Ansible

```bash
cron - Manage cron.d and crontab entries
```

راجع <https://docs.ansible.com/ansible/latest/modules/cron_module.html> لمزيد من المعلومات.

### <a name="to-set-crontabs-in-chef"></a>لتعيين الكرونتات في Chef

```bash
cron resource
```

راجع <https://docs.chef.io/resources/cron/> لمزيد من المعلومات.

### <a name="to-set-cron-jobs-in-puppet"></a>لتعيين مهام cron في "مهى"

نوع المورد: كرون

راجع <https://puppet.com/docs/puppet/5.5/types/cron.html> لمزيد من المعلومات.

الأتمتة مع "نظام التشغيل": مهام Cron والمهام المجدولة

راجع <https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/> لمزيد من المعلومات.

## <a name="additional-information"></a>معلومات إضافية

### <a name="to-get-help-with-crontab"></a>للحصول على تعليمات حول crontab

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>للحصول على قائمة ملف crontab للمستخدم الحالي

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>للحصول على قائمة ملف crontab لمستخدم آخر

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>لنسخ إدخالات crontab احتياطيا

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> قم بذلك قبل التحرير أو الإزالة.

### <a name="to-restore-crontab-entries"></a>لاستعادة إدخالات الكرونتاب

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>لتحرير الكرونتاب وإضافة مهمة جديدة كمستخدم جذر

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>لتحرير الكرونتاب وإضافة مهمة جديدة

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>لتحرير إدخالات crontab الخاصة ب مستخدم آخر

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>لإزالة كل إدخالات crontab

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>لإزالة إدخالات crontab الخاصة ب مستخدم آخر

```bash
crontab -u username -r
```

### <a name="explanation"></a>شرح

<pre>
+—————- minute (values: 0 - 59) (special characters: , - * /)  <br>
| +————- hour (values: 0 - 23) (special characters: , - * /) <br>
| | +———- day of month (values: 1 - 31) (special characters: , - * / L W C)  <br>
| | | +——- month (values: 1 - 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 - 6) (Sunday=0 or 7) (special characters: , - * / L W C) <br>
| | | | |*****command to be executed
</pre>
