# [مشكلات الأداء في Microsoft Defender لنقطة النهاية](index.yml)

## [نظرة عامة]()
### [ما هو Microsoft Defender لنقطة النهاية؟](microsoft-defender-endpoint.md)
### [مقارنة Defender for Endpoint الخطة 1 مع الخطة 2](defender-endpoint-plan-1-2.md)
### [الحد الأدنى للمتطلبات](minimum-requirements.md)
### [ما الجديد في Microsoft Defender لنقطة النهاية؟](whats-new-in-microsoft-defender-endpoint.md)
### [ميزات المعاينة](preview.md)
### [تخزين البيانات والخصوصية](data-storage-privacy.md)
### [نظرة عامة مركز حماية Microsoft Defender](use.md)
### [Defender for Endpoint الخطة 1]()
#### [نظرة عامة](defender-endpoint-plan-1.md)
#### [الإعداد والتكوين](mde-p1-setup-configuration.md)
#### [بدء الاستخدام](mde-plan1-getting-started.md)
#### [الصيانة والعمليات](mde-p1-maintenance-operations.md)
### [Microsoft Defender لنقطة النهاية لعملاء الحكومة الأمريكية](gov.md)
### [Microsoft Defender لنقطة النهاية على الأنظمة الأساسية غير Windows](non-windows.md)


## [تقييم القدرات](evaluation-lab.md)

## [تخطيط النشر](deployment-strategy.md)

## [دليل النشر]()
### [مراحل النشر](deployment-phases.md)
### [المرحلة 1: التحضير](prepare-deployment.md)
### [المرحلة 2: إعداد](production-deployment.md)
### [المرحلة 3: التجهيز للاستخدام]()
#### [نظرة عامة على التجهيز](onboarding.md)
#### [حلقات النشر](deployment-rings.md)
#### [التجهيز باستخدام Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
#### [التجهيز باستخدام إدارة نقاط النهاية في Microsoft](onboarding-endpoint-manager.md)

## [إرشادات الترحيل](migration-guides.md)
### [الانتقال إلى Defender لنقطة النهاية](switch-to-mde-overview.md)
#### [المرحلة 1: التحضير](switch-to-mde-phase-1.md)
#### [المرحلة 2: الإعداد](switch-to-mde-phase-2.md)
#### [المرحلة 3: التجهيز للاستخدام](switch-to-mde-phase-3.md)
#### [استكشاف الأخطاء وإصلاحها](switch-to-mde-troubleshooting.md)
### [إدارة Defender لنقطة النهاية بعد الترحيل](manage-mde-post-migration.md)
#### [استخدام Intune (مستحسن)](manage-mde-post-migration-intune.md)
#### [استخدام Configuration Manager](manage-mde-post-migration-configuration-manager.md)
#### [استخدام نهج المجموعة](manage-mde-post-migration-group-policy-objects.md)
#### [استخدم PowerShell أو WMI أو MPCmdRun.exe](manage-mde-post-migration-other-tools.md)
#### [سيناريوهات ترحيل الخادم](server-migration.md)

## [أجهزة التجهيز والتكوين]()
### [أجهزة التجهيز وتكوين Microsoft Defender لنقطة النهاية](onboard-configure.md)


### [Microsoft Defender لنقطة النهاية على Windows وWindows Server]()
#### [أدوات وطرق الإعداد لنقاط نهاية Windows](configure-endpoints.md)
#### [أجهزة Windows وخوادم Windows الأجهزة]()

##### [الإصدارات السابقة من Windows](onboard-downlevel.md)


##### [أجهزة Windows وخوادم Windows الأجهزة]()
###### [تشغيل Windows Server 2012 R2 و2016 Semi-Annual و2019 و2022](configure-server-endpoints.md)
###### [أجهزة Windows باستخدام برنامج نصي محلي](configure-endpoints-script.md)
###### [أجهزة Windows باستخدام نهج المجموعة](configure-endpoints-gp.md)
###### [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
###### [أجهزة Windows باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول](configure-endpoints-mdm.md)
###### [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)
###### [أجهزة Windows 10 متعددة جلسات العمل في Windows سطح المكتب الظاهري](onboard-windows-multi-session-device.md)




#### [التكامل مع Microsoft Defender for Cloud](azure-server-integration.md)

#### [أجهزة التجهيز بدون اتصال بالإنترنت](onboard-offline-machines.md)
#### [تشغيل اختبار الكشف على جهاز تم تشغيله حديثاً](run-detection-test.md)
#### [تشغيل هجمات محاكاة على الأجهزة](attack-simulations.md)
#### [تكوين إعدادات الوكيل والاتصال بالإنترنت](configure-proxy-internet.md)
#### [إنشاء قاعدة إعلامات التهيئة أو إيقاف التشغيل](onboarding-notification.md)



### [Microsoft Defender لنقطة النهاية على أنظمة تشغيل أخرى]()
#### [الأجهزة غير المجهزة Windows](configure-endpoints-non-windows.md)

#### [Microsoft Defender لنقطة النهاية على macOS]()
##### [نظرة عامة Microsoft Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md)
##### [الجديد](mac-whatsnew.md)

##### [نشر]()
###### [النشر المستند إلى Microsoft Intune](mac-install-with-intune.md)
###### [النشر المستند إلى JAMF Pro]()
####### [نشر Microsoft Defender لنقطة النهاية على macOS باستخدام Jamf Pro](mac-install-with-jamf.md)
####### [تسجيل الدخول إلى Jamf Pro](mac-install-jamfpro-login.md)
####### [إعداد مجموعات الأجهزة](mac-jamfpro-device-groups.md)
####### [إعداد النُهُج](mac-jamfpro-policies.md)
####### [تسجيل الأجهزة](mac-jamfpro-enroll-devices.md)

###### [النشر باستخدام نظام مختلف إدارة الأجهزة المحمولة (MDM)](mac-install-with-other-mdm.md)
###### [النشر اليدوي](mac-install-manually.md)
##### [تحديث](mac-updates.md)

##### [تكوين]()
###### [تكوين الاستثناءات والتحقق من صحتها](mac-exclusions.md)
###### [تعيين التفضيلات](mac-preferences.md)
###### [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها](mac-pua.md)
###### [عنصر تحكم الجهاز]()
####### [نظرة عامة حول التحكم في الجهاز](mac-device-control-overview.md)
####### [أمثلة JAMF](mac-device-control-jamf.md)
####### [أمثلة Intune](mac-device-control-intune.md)
###### [جدولة عمليات الفحص](mac-schedule-scan.md)

##### [استكشاف الأخطاء وإصلاحها]()
###### [استكشاف مشاكل التثبيت وإصلاحها](mac-support-install.md)
###### [استكشاف مشاكل الأداء وإصلاحها](mac-support-perf.md)
###### [استكشاف الأخطاء في اتصال السحابة وإصلاحها](troubleshoot-cloud-connect-mdemac.md)
###### [استكشاف مشاكل ملحقات kernel وإصلاحها](mac-support-kext.md)
###### [استكشاف مشاكل الترخيص وإصلاحها](mac-support-license.md)

##### [الخصوصية](mac-privacy.md)
##### [الموارد](mac-resources.md)


#### [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux]()
##### [نظرة عامة Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
##### [الجديد](linux-whatsnew.md)
##### [نشر]()
###### [النشر اليدوي](linux-install-manually.md)
###### [النشر المستند إلى Puppet](linux-install-with-puppet.md)
###### [نشر مستند إلى Ansible](linux-install-with-ansible.md)
###### [نشر Defender لنقطة النهاية على Linux باستخدام Chef](linux-deploy-defender-for-endpoint-with-chef.md)

##### [تحديث](linux-updates.md)

##### [تكوين]()
###### [تكوين الاستثناءات والتحقق من صحتها](linux-exclusions.md)
###### [تكوين الوكيل الثابت](linux-static-proxy-configuration.md)
###### [تعيين التفضيلات](linux-preferences.md)
###### [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها](linux-pua.md)
###### [جدولة عمليات الفحص باستخدام Microsoft Defender لنقطة النهاية على Linux](linux-schedule-scan-mde.md)
###### [جدولة تحديث Microsoft Defender لنقطة النهاية (Linux)](linux-update-MDE-Linux.md)


##### [استكشاف الأخطاء وإصلاحها]()
###### [استكشاف مشاكل التثبيت وإصلاحها](linux-support-install.md)
###### [التحقق من مشاكل صحة الوكيل](health-status.md)
###### [استكشاف مشاكل اتصال السحابة وإصلاحها](linux-support-connectivity.md)
###### [استكشاف مشاكل تثبيت RHEL 6 وإصلاحها](linux-support-rhel.md)
###### [استكشاف مشاكل الأداء وإصلاحها](linux-support-perf.md)
###### [استكشاف مشاكل الأحداث المفقودة وإصلاحها](linux-support-events.md)

##### [الخصوصية](linux-privacy.md)
##### [الموارد](linux-resources.md)

#### [الدفاع عن المخاطر على الأجهزة المحمولة]()
##### [نظرة عامة حول الدفاع عن المخاطر على الأجهزة المحمولة](mtd.md)

##### [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Android]()
###### [نظرة عامة على Microsoft Defender لنقطة النهاية على Android](microsoft-defender-endpoint-android.md)
###### [أحدث الميزات](android-whatsnew.md)

###### [نشر]()
####### [نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune](android-intune.md)

###### [تكوين]()
####### [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md)
####### [تكوين Microsoft Defender لنقطة النهاية المخاطر باستخدام نهج حماية التطبيق](android-configure-mam.md)

###### [الخصوصية]()
####### [Microsoft Defender لنقطة النهاية على Android - معلومات الخصوصية](android-privacy.md)

###### [استكشاف الأخطاء وإصلاحها]()
####### [استكشاف مشكلات نقل الملكية وإصلاحها](android-support-signin.md)

##### [مشكلات الأداء في Microsoft Defender لنقطة النهاية على iOS]()
###### [نظرة عامة Microsoft Defender لنقطة النهاية على iOS](microsoft-defender-endpoint-ios.md)
###### [الجديد](ios-whatsnew.md)

###### [نشر]()
####### [نشر Microsoft Defender لنقطة النهاية على iOS عبر Intune](ios-install.md)
####### [نشر Microsoft Defender لنقطة النهاية على iOS للأجهزة غير التي تم نشرها](ios-install-unmanaged.md)

###### [تكوين ميزات iOS](ios-configure-features.md)

###### [الأسئلة والأعلام حول استكشاف الأخطاء وإصلاحها](ios-troubleshoot.md)

###### [الخصوصية](ios-privacy.md)


### [قم بإدارة Microsoft Defender لإعدادات تكوين نقطة النهاية على الأجهزة باستخدام دارة نقاط النهاية في Microsoft](security-config-management.md)

### [استكشاف مشاكل التجهيز وإصلاحها]()
#### [استكشاف الأخطاء وإصلاحها أثناء التجهيز](troubleshoot-onboarding.md)
#### [استكشاف مشاكل الوصول إلى المدخل والاشتراك وإصلاحها](troubleshoot-onboarding-error-messages.md)
#### [استكشاف مشاكل تشغيل تكوين الأمان وإصلاحها](troubleshoot-security-config-mgt.md)





### [تكوين إعدادات المدخل]()
#### [تكوين عام Defender لإعدادات نقطة النهاية](preferences-setup.md)
#### [عام]()
##### [التحقق من موقع تخزين البيانات وتحديث إعدادات استبقاء البيانات](data-retention-settings.md)
##### [تكوين إعلامات التنبيهات](configure-email-notifications.md)
##### [تكوين إعلامات البريد الإلكتروني لنقاط الضعف](configure-vulnerability-email-notifications.md)
##### [تكوين الميزات المتقدمة](advanced-features.md)

#### [الأذونات]()
##### [استخدام الأذونات الأساسية للوصول إلى المدخل](basic-permissions.md)
##### [إدارة الوصول إلى المدخل باستخدام RBAC](rbac.md)
###### [إنشاء أدوار وإدارتها](user-roles.md)
###### [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md)
###### [إنشاء علامات الجهاز وإدارتها](machine-tags.md)

#### [القواعد]()
##### [إدارة قواعد الحذف](manage-suppression-rules.md)
##### [إنشاء مؤشرات](manage-indicators.md)
###### [إنشاء مؤشرات للملفات](indicator-file.md)
###### [إنشاء مؤشرات لـ IPs أو عناوين URL/المجالات](indicator-ip-domain.md)
###### [إنشاء مؤشرات للشهادات](indicator-certificates.md)
###### [إدارة المؤشرات](indicator-manage.md)
##### [إدارة عمليات تحميل الملفات التلقائية](manage-automation-file-uploads.md)
##### [إدارة استثناءات مجلدات التنفيذ التلقائي](manage-automation-folder-exclusions.md)

#### [إدارة الأجهزة]()
##### [أجهزة التجهيز](onboard-configure.md)
##### [أجهزة إيقاف التجهيز](offboard-machines.md)
##### [التأكد من تكوين أجهزتك بشكل صحيح](configure-machines.md)
##### [مراقبة الجهاز وزيادة إعداده](configure-machines-onboarding.md)

#### [تكوين مركز حماية Microsoft Defender المنطقة الزمنية](time-settings.md)

## [الكشف عن التهديدات وحماية نقاط النهاية]()
### [التهديدات وإدارة الثغرات الأمنية]()
#### [نظرة عامة](next-gen-threat-and-vuln-mgt.md)
#### [بدء الاستخدام]()
##### [الأذونات والمتطلبات الأساسية](tvm-prerequisites.md)
##### [الأنظمة الأساسية وإمكانيات أنظمة التشغيل المعتمدة](tvm-supported-os.md)
##### [تعيين قيمة الجهاز](tvm-assign-device-value.md)
#### [تقييم وضعية الأمان]()
##### [تحليلات لوحة المعلومات](tvm-dashboard-insights.md)
##### [درجة التعرض للضوء](tvm-exposure-score.md)
##### [Microsoft Secure Score للأجهزة](tvm-microsoft-secure-score-devices.md)
#### [تحسين وضعية الأمان وتقليل المخاطر]()
##### [توصيات أمان العنوان](tvm-security-recommendation.md)
##### [إصلاح الثغرات](tvm-remediation.md)
##### [استثناءات توصيات الأمان](tvm-exception.md)
##### [التخطيط لبرامج انتهاء الدعم](tvm-end-of-support-software.md)
##### [ترحيل الثغرات في اليوم الصفري](tvm-zero-day-vulnerabilities.md)
#### [فهم نقاط الضعف بأجهزتك]()
##### [بيانات البرامج](tvm-software-inventory.md)
##### [نقاط الضعف في المؤسسة](tvm-weaknesses.md)
##### [المخطط الزمني للحدث](threat-and-vuln-mgt-event-timeline.md)
##### [تقرير الأجهزة المعرضة](tvm-vulnerable-devices-report.md)
##### [البحث عن الأجهزة المعرضة](tvm-hunt-exposed-devices.md)

### [اكتشاف الجهاز]()
#### [نظرة عامة على اكتشاف الجهاز](device-discovery.md)
#### [تكوين اكتشاف الجهاز](configure-device-discovery.md)
#### [تكامل Microsoft Defender for IoT](enable-microsoft-defender-for-iot-integration.md)
#### [تمكين تكامل بيانات Corelight](corelight-integration.md)
#### [الأسئلة الشائعة حول اكتشاف الجهاز](device-discovery-faq.md)

### [بيانات الجهاز]()
#### [بيانات الجهاز](machines-view-overview.md)
#### [استبعاد الأجهزة](exclude-devices.md)
#### [وضع علامة على أحداث المخطط الزمني للجهاز](device-timeline-event-flag.md)
#### [إدارة مجموعة الأجهزة والعلامات](machine-tags.md)

### [أجهزة الشبكة](network-devices.md)

### [استضافة تقارير جدار الحماية في Microsoft Defender لنقطة النهاية](host-firewall-reporting.md)

### [قواعد تقليل الأجزاء المعرضة للهجوم]()
#### [نظرة عامة حول قواعد تقليل الأجزاء المعرضة للهجوم](overview-attack-surface-reduction.md)
#### [قواعد تقليل الأجزاء المعرضة للهجوم]()
##### [التعرّف على قواعد ASR](attack-surface-reduction.md)
##### [دليل نشر قواعد الحد من سطح الهجوم (ASR)]()
###### [نظرة عامة على دليل نشر قواعد الحد من سطح الهجوم (ASR)](attack-surface-reduction-rules-deployment.md)
###### [تخطيط نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-plan.md)
###### [اختبار قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-test.md)
###### [تمكين قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-implement.md)
###### [تشغيل قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)
##### [مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md)
##### [تمكين أساليب التكوين البديلة لقواعد ASR](enable-attack-surface-reduction.md)
##### [الأسئلة المتداولة حول قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-faq.yml)
#### [الوصول إلى المجلدات الخاضعة للتحكم]()
##### [حماية المجلدات](controlled-folders.md)
##### [تقييم الوصول المتحكم به إلى المجلد](evaluate-controlled-folder-access.md)
##### [تمكين الوصول إلى المجلدات الخاضعة للتحكم](enable-controlled-folders.md)
##### [تخصيص الوصول إلى المجلدات الخاضعة للتحكم](customize-controlled-folders.md)
#### [الحماية من استغلال]()
##### [حماية الأجهزة من استغلالها](exploit-protection.md)
##### [تقييم الحماية من المخاطر](evaluate-exploit-protection.md)
##### [تمكين الحماية من استغلال](enable-exploit-protection.md)
##### [تخصيص الحماية من استغلال](customize-exploit-protection.md)
##### [استيراد تكوينات الحماية من الاستغلال وتصديرها ونشرها](import-export-exploit-protection-emet-xml.md)
##### [مرجع الحماية من استغلال](exploit-protection-reference.md)
#### [حماية الشبكة]()
##### [حماية الشبكة](network-protection.md)
##### [تقييم حماية الشبكة](evaluate-network-protection.md)
##### [تشغيل حماية الشبكة](enable-network-protection.md)

### حماية الجيل التالي
#### [نظرة عامة حول حماية الجيل التالي](next-generation-protection.md)
##### [نظرة عامة برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-windows.md)
##### [معاً بشكل أفضل: برنامج الحماية من الفيروسات من Microsoft Defender Microsoft Defender لنقطة النهاية](why-use-microsoft-defender-antivirus.md)
##### [معاً بشكل أفضل: برنامج الحماية من الفيروسات من Microsoft Defender Office 365](office-365-microsoft-defender-antivirus.md)
#### [تقييم برنامج الحماية من الفيروسات من Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
#### [تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
#### [الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)
##### [لماذا يجب أن تكون الحماية السحابية في](why-cloud-protection-should-be-on-mdav.md)
##### [تشغيل الحماية السحابية](enable-cloud-protection-microsoft-defender-antivirus.md)
##### [تحديد مستوى الحماية السحابية](specify-cloud-protection-level-microsoft-defender-antivirus.md)
##### [الحماية السحابية ونموذج الإرسال](cloud-protection-microsoft-antivirus-sample-submission.md)
#### [تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها](configure-network-connections-microsoft-defender-antivirus.md)
#### [حماية إعدادات الأمان باستخدام الحماية من العبث](prevent-changes-to-security-settings-with-tamper-protection.md)
#### [تشغيل الحظر من النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md)
#### [تكوين الفترة الزمنية لحظر السحابة](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)
#### [تكوين الحماية السلوكية، والحماية التحليلية، والحماية في الوقت الحقيقي](configure-protection-features-microsoft-defender-antivirus.md)
#### [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
#### [تمكين الحماية برنامج الحماية من الفيروسات من Microsoft Defender دائما وتكوينها في نهج المجموعة](configure-real-time-protection-microsoft-defender-antivirus.md)
#### [تكوين المعالجة برنامج الحماية من الفيروسات من Microsoft Defender الكشف](configure-remediation-microsoft-defender-antivirus.md)
#### للحصول على التفاصيل، اطلع على [تكوين الاستثناءات والتحقق من صحتها لعمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender](schedule-antivirus-scans.md).
##### [جدولة عمليات الفحص باستخدام نهج المجموعة](schedule-antivirus-scans-group-policy.md)
##### [جدولة عمليات الفحص باستخدام PowerShell](schedule-antivirus-scans-powershell.md)
##### [جدولة عمليات الفحص باستخدام WMI](schedule-antivirus-scans-wmi.md)
#### [استخدام الفحص الدوري المحدود في برنامج الحماية من الفيروسات من Microsoft Defender](limited-periodic-scanning-microsoft-defender-antivirus.md)
#### [التوافق مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md)
#### [البحث عن أسماء الكشف عن البرامج الضارة Microsoft Defender لنقطة النهاية](find-defender-malware-name.md)

#### [الحصول على تحديثات الحماية من الفيروسات ومكافحة البرامج الضارة](manage-updates-baselines-microsoft-defender-antivirus.md)
##### [إدارة مصادر تحديثات برنامج الحماية من الفيروسات من Microsoft Defender الحماية](manage-protection-updates-microsoft-defender-antivirus.md)
##### [إدارة الجدول الزمني عندما يجب تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)
##### [إدارة عملية التشغيل التدريجي لتحديثات Microsoft Defender](manage-gradual-rollout.md)
##### [تكوين عملية طرح تدريجي لتحديثات Microsoft Defender](configure-updates.md)
##### [إدارة برنامج الحماية من الفيروسات من Microsoft Defender وفحص نقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)
##### [إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)
##### [إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)

#### [إدارة برنامج الحماية من الفيروسات من Microsoft Defender لمنظمتك](configuration-management-reference-microsoft-defender-antivirus.md)
##### [استخدم إدارة نقاط النهاية من Microsoft لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](use-intune-config-manager-microsoft-defender-antivirus.md)
##### [استخدم نهج المجموعة لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
##### [استخدم PowerShell cmdlets لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
##### [استخدم Windows أدوات الإدارة (WMI) لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](use-wmi-microsoft-defender-antivirus.md)
##### [استخدم أداة mpcmdrun.exe لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](command-line-arguments-microsoft-defender-antivirus.md)
##### [تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
##### [تحديد ما إذا كان يمكن للمستخدمين تعديل إعدادات نهج برنامج الحماية من الفيروسات من Microsoft Defender محلياً أم لا](configure-local-policy-overrides-microsoft-defender-antivirus.md)
##### [تحديد ما إذا كان يمكن للمستخدمين رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها](prevent-end-user-interaction-microsoft-defender-antivirus.md)

#### [نشر تقرير حول برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
##### [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-microsoft-defender-antivirus.md)
##### [دليل النشر برنامج الحماية من الفيروسات من Microsoft Defender في بيئة البنية الأساسية لسطح المكتب الظاهري (VDI)](deployment-vdi-microsoft-defender-antivirus.md)
##### [الإبلاغ عن برنامج الحماية من الفيروسات من Microsoft Defender](report-monitor-microsoft-defender-antivirus.md)

#### [عمليات الفحص والمعالجة](review-scan-results-microsoft-defender-antivirus.md)
##### [تكوين عمليات فحص عند برنامج الحماية من الفيروسات من Microsoft Defender عند الطلب](run-scan-microsoft-defender-antivirus.md)
##### [تشغيل نتائج فحص Microsoft Defender في وضع عدم الاتصال ومراجعتها](microsoft-defender-offline.md)
##### [قم بتكوين خيارات فحص Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)
##### [استعادة الملفات المعزولة في برنامج الحماية من الفيروسات من Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md)

#### [استثناءات برنامج مكافحة الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
##### [الاستثناءات استناداً إلى ملحق الملف وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
##### [الاستثناءات للملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
##### [استثناءات Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
##### [الأخطاء الشائعة التي يجب تجنبها](common-exclusion-mistakes-microsoft-defender-antivirus.md)

#### التشخيص والأداء برنامج الحماية من الفيروسات من Microsoft Defender
##### [تقارير حول صحة الجهاز وتوافقه](machine-reports.md)
##### [استكشاف مشاكل الأداء المتعلقة بالحماية في الوقت الحقيقي وإصلاحها](troubleshoot-performance-issues.md) 
##### [استكشاف الأخطاء وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender التقارير في تحديث التوافق](troubleshoot-reporting.md)
##### [ضبط أداء برنامج الحماية من الفيروسات من Microsoft Defender](tune-performance-defender-antivirus.md)

#### استكشاف الأخطاء وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender
##### [مراجعة سجلات الأحداث ورموز الأخطاء لا استكشاف المشاكل المتعلقة بالأحداث وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender](troubleshoot-microsoft-defender-antivirus.md)
##### [استكشاف الأخطاء برنامج الحماية من الفيروسات من Microsoft Defender أثناء عملية إعادة التهجر من حل جهة خارجية](troubleshoot-microsoft-defender-antivirus-when-migrating.md)

#### [حماية ويب]()
##### [نظرة عامة حول حماية الويب](web-protection-overview.md)
##### [الحماية من المخاطر على الويب]()
###### [نظرة عامة حول الحماية من المخاطر على الويب](web-threat-protection.md)
###### [مراقبة أمان الويب](web-protection-monitoring.md)
###### [الاستجابة إلى تهديدات الويب](web-protection-response.md)
##### [تصفية محتوى ويب](web-content-filtering.md)

#### [التحكم في الجهاز]()
##### [حماية التخزين القابلة للإزالة](device-control-removable-storage-protection.md)
##### [التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)
##### [تثبيت الجهاز](mde-device-control-device-installation.md)
##### [حماية الطابعة للتحكم في الجهاز](printer-protection.md)
##### [تقارير التحكم في الجهاز](device-control-report.md)

#### [الحظر السلوكي والاحتواء]()
##### [الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)
##### [الحظر السلوكي للعميل](client-behavioral-blocking.md)
##### [حظر حلقة الملاحظات](feedback-loop-blocking.md)


### [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)


### [إدارة تكوين الجهاز]()

#### [زيادة التوافق مع خط الأمان الأساسي](configure-machines-security-baseline.md)
#### [تحسين نشر قاعدة الحد من الهجمات والكشف عنها](configure-machines-asr.md)

## [التحقق من التهديدات والاستجابة لها]()
### [الكشف عن نقطة النهاية والاستجابة لها]()
#### [نظرة عامة حول الكشف عن نقطة النهاية والاستجابة](overview-endpoint-detection-response.md)
#### [لوحة معلومات عمليات الأمان](security-operations-dashboard.md)
#### [إرسال ملفات](admin-submissions-mde.md)
#### [قائمة انتظار الأحداث]()
##### [عرض قائمة انتظار الأحداث وتنظيمها](view-incidents-queue.md)
##### [إدارة الأحداث](manage-incidents.md)
##### [التحقيق في الأحداث](investigate-incidents.md)

#### [قائمة انتظار التنبيهات]()
##### [قائمة انتظار التنبيهات في Microsoft 365 Defender](alerts-queue-endpoint-detection-response.md)
##### [عرض قائمة انتظار التنبيهات وتنظيمها](alerts-queue.md)
##### [مراجعة التنبيهات](review-alerts.md)
##### [إدارة التنبيهات](manage-alerts.md)
##### [التحقق من التنبيهات](investigate-alerts.md)
##### [التحقق من الملفات](investigate-files.md)
##### [التحقق من الأجهزة](investigate-machines.md)
##### [التحقق من عنوان IP](investigate-ip.md)
##### [التحقق من مجال](investigate-domain.md)
###### [التحقق من أحداث الاتصال التي تحدث خلف نيات إعادة توجيه](investigate-behind-proxy.md)
##### [التحقق من حساب مستخدم](investigate-user.md)

#### [اتخاذ إجراءات الاستجابة]()
##### [اتخاذ إجراءات الاستجابة على جهاز]()
###### [إجراءات الاستجابة على الأجهزة](respond-machine-alerts.md)
###### [إدارة العلامات](respond-machine-alerts.md#manage-tags)
###### [بدء تحقيق تلقائي](respond-machine-alerts.md#initiate-automated-investigation)
###### [بدء جلسة استجابة مباشرة](respond-machine-alerts.md#initiate-live-response-session)
###### [تجميع حزمة التحقيق](respond-machine-alerts.md#collect-investigation-package-from-devices)
###### [تشغيل مسح الحماية من الفيروسات](respond-machine-alerts.md#run-microsoft-defender-antivirus-scan-on-devices)
###### [تقييد تنفيذ التطبيق](respond-machine-alerts.md#restrict-app-execution)
###### [عزل الأجهزة من الشبكة](respond-machine-alerts.md#isolate-devices-from-the-network)
###### [استشارة خبير في التهديدات](respond-machine-alerts.md#consult-a-threat-expert)
###### [التحقق من تفاصيل النشاط في مركز الإجراءات](respond-machine-alerts.md#check-activity-details-in-action-center)

##### [اتخاذ إجراءات الاستجابة على ملف]()
###### [إجراءات الاستجابة على الملفات](respond-file-alerts.md)
###### [إيقاف الملفات وفحصها في الشبكة](respond-file-alerts.md#stop-and-quarantine-files-in-your-network)
###### [استعادة ملف من الفحص](respond-file-alerts.md#restore-file-from-quarantine)
###### [إضافة مؤشرات لحظر ملف أو السماح به](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
###### [استشارة خبير في التهديدات](respond-file-alerts.md#consult-a-threat-expert)
###### [التحقق من تفاصيل النشاط في مركز الإجراءات](respond-file-alerts.md#check-activity-details-in-action-center)
###### [تنزيل ملف أو تجميعه](respond-file-alerts.md#download-or-collect-file)
###### [تحليل عميق](respond-file-alerts.md#deep-analysis)

#### [عرض إجراءات الإصلاح والموافقة عليها](manage-auto-investigation.md)
##### [عرض تفاصيل ونتائج الاختبارات التلقائية](auto-investigation-action-center.md)

#### [التحقق من الكيانات باستخدام الاستجابة المباشرة]()
##### [التحقق من الكيانات على الأجهزة](live-response.md)
##### [أمثلة أوامر الاستجابة المباشرة](live-response-command-examples.md)

#### [استخدام تسميات الحساسية لتحديد أولوية الاستجابة للحوادث](information-protection-investigation.md)

#### [إعداد التقارير]()
##### [Power BI - كيفية استخدام واجهة برمجة التطبيقات - نماذج](api-power-bi.md)
##### [تقارير الحماية من المخاطر](threat-protection-reports.md)

### [الصيد المتقدم]()
#### [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
#### [فهم المخطط](advanced-hunting-schema-reference.md)
#### [DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)

### [نظرة عامة حول تحليل المخاطر](threat-analytics.md)
#### [قراءة تقرير المحلل](threat-analytics-analyst-reports.md)

### [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)

### [التحقيق التلقائي والاستجابة (AIR)]()
#### [نظرة عامة على AIR](automated-investigations.md)
#### [مستويات التنفيذ التلقائي في AIR](automation-levels.md)
#### [تكوين قدرات AIR](configure-automated-investigations-remediation.md)

### [خبراء المخاطر في Microsoft]()
#### [خبراء المخاطر في Microsoft عامة](microsoft-threat-experts.md)
#### [تكوين قدرات خبراء المخاطر في Microsoft وإدارتها](configure-microsoft-threat-experts.md)



## المرجع
### [فهم مفاهيم المعلومات الاستخبارية للتهديدات](threat-indicator-concepts.md)
### [تكوين التكامل مع حلول Microsoft الأخرى]()
#### [تكوين الوصول الشرطي](configure-conditional-access.md)
#### [تكوين Microsoft Defender for Cloud Apps التكامل](microsoft-cloud-app-security-config.md)
### [واجهات برمجة التطبيقات والإدارة]()
#### [نظرة عامة على الإدارة و واجهات برمجة التطبيقات](management-apis.md)
#### [ملاحظات حول إصدار واجهة برمجة التطبيقات](api-release-notes.md)
#### [واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية]()
##### [بدء الاستخدام]()
###### [Microsoft Defender لنقطة النهاية ولشروط وترخيص واجهة برمجة التطبيقات](api-terms-of-use.md)
###### [الوصول إلى Microsoft Defender لنقطة النهاية برمجة التطبيقات](apis-intro.md)
###### [مرحباً بالعالم](api-hello-world.md)
###### [الوصول باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md)
###### [الوصول باستخدام سياق المستخدم](exposed-apis-create-app-nativeapp.md)



##### [Microsoft Defender لنقطة النهاية واجهات برمجة التطبيقات]()
###### [واجهات Microsoft Defender لنقطة النهاية برمجة التطبيقات المعتمدة](exposed-apis-list.md)
###### [رموز أخطاء واجهات برمجة تطبيقات REST الشائعة](common-errors.md)
###### [الصيد المتقدم](run-advanced-query-api.md)

###### [تنبيه]()
####### [أساليب التنبيه وخصائصه](alerts.md)
####### [تنبيهات القائمة](get-alerts.md)
####### [إنشاء تنبيه](create-alert-by-reference.md)
####### [تنبيهات التحديثات الدفعية](batch-update-alerts.md)
####### [تحديث التنبيه](update-alert.md)
####### [الحصول على معلومات التنبيه حسب المعرّف](get-alert-info-by-id.md)
####### [الحصول على معلومات المجالات ذات الصلة بالتنبيه](get-alert-related-domain-info.md)
####### [الحصول على معلومات الملف ذات الصلة بالتنبيه](get-alert-related-files-info.md)
####### [الحصول على معلومات تنبيهات ذات صلة ب IPs](get-alert-related-ip-info.md)
####### [الحصول على معلومات الجهاز ذات الصلة بالتنبيه](get-alert-related-machine-info.md)
####### [الحصول على معلومات المستخدم ذات الصلة بالتنبيه](get-alert-related-user-info.md)


###### [تقييمات نقاط الضعف والتكوينات الآمنة]()
####### [تصدير أساليب التقييم وخصائصه](get-assessment-methods-properties.md)
####### [تصدير تقييم تكوين آمن](get-assessment-secure-config.md)
####### [تقييم بيانات البرامج](get-assessment-software-inventory.md)
####### [تقييم نقاط الضعف في البرامج](get-assessment-software-vulnerabilities.md)

###### [التحقيق التلقائي]()
####### [أساليب التحقيق وخصائصه](investigation.md)
####### [التحقيق في القائمة](get-investigation-collection.md)
####### [الحصول على التحقيق](get-investigation-object.md)
####### [بدء التحقيق](initiate-autoir-investigation.md)

###### [المجال]()
####### [الحصول على تنبيهات ذات صلة بالمجال](get-domain-related-alerts.md)
####### [الحصول على الأجهزة ذات الصلة بالمجال](get-domain-related-machines.md)
####### [الحصول على إحصائيات المجال](get-domain-statistics.md)

###### [ملف]()
####### [أساليب الملفات وخصائصها](files.md)
####### [الحصول على معلومات الملف](get-file-information.md)
####### [الحصول على تنبيهات ذات صلة بالملفات](get-file-related-alerts.md)
####### [الحصول على الأجهزة ذات الصلة بالملفات](get-file-related-machines.md)
####### [الحصول على إحصائيات الملفات](get-file-statistics.md)

###### [المؤشرات]()
####### [أساليب المؤشرات وخصائصها](ti-indicator.md)
####### [مؤشرات القائمة](get-ti-indicators-collection.md)
####### [مؤشر إرسال](post-ti-indicator.md)
####### [مؤشر الاستيراد](import-ti-indicators.md)
####### [مؤشر الحذف](delete-ti-indicator-by-id.md)

###### [IP]()
####### [الحصول على تنبيهات ذات صلة ب IP](get-ip-related-alerts.md)
####### [الحصول على إحصائيات IP](get-ip-statistics.md)

###### [مكتبة استجابة مباشرة]()
####### [أساليب وخصائص مكتبة الاستجابة المباشرة](live-response-library-methods.md)
####### [ملفات مكتبة القائمة](list-library-files.md)
####### [تحميل إلى مكتبة الاستجابة المباشرة](upload-library.md)
####### [حذف من المكتبة](delete-library.md)


###### [الجهاز]()
####### [أساليب الجهاز وخصائصه](machine.md)
####### [أجهزة القائمة](get-machines.md)
####### [الحصول على جهاز بواسطة المعرّف](get-machine-by-id.md)
####### [الحصول على سجل الجهاز للمستخدمين](get-machine-log-on-users.md)
####### [الحصول على تنبيهات متعلقة بالآلة](get-machine-related-alerts.md)
####### [الحصول على البرامج المثبتة](get-installed-software.md)
####### [الحصول على نقاط الضعف المكتشفة](get-discovered-vulnerabilities.md)
####### [الحصول على توصيات الأمان](get-security-recommendations.md)
####### [إضافة علامات الجهاز أو إزالتها](add-or-remove-machine-tags.md)
####### [البحث عن الأجهزة حسب IP](find-machines-by-ip.md)
####### [البحث عن الأجهزة حسب العلامة](find-machines-by-tag.md)
####### [فقدان KBs](get-missing-kbs-machine.md)
####### [تعيين قيمة الجهاز](set-device-value.md)
####### [تحديث الجهاز](update-machine-method.md)



###### [إجراء الجهاز]()
####### [أساليب إجراءات الجهاز وخصائصه](machineaction.md)
####### [إجراءات جهاز القائمة](get-machineactions-collection.md)
####### [إجراء الحصول على جهاز](get-machineaction-object.md)
####### [تجميع حزمة التحقيق](collect-investigation-package.md)
####### [الحصول على حزمة التحقيق SAS URI](get-package-sas-uri.md)
####### [الحصول على نتيجة استجابة مباشرة](get-live-response-result.md)
####### [جهاز عزل](isolate-machine.md)
####### [تحرير الجهاز من العزل](unisolate-machine.md)
####### [تقييد تنفيذ التطبيق](restrict-code-execution.md)
####### [إزالة تقييد التطبيق](unrestrict-code-execution.md)
####### [تشغيل مسح الحماية من الفيروسات](run-av-scan.md)
####### [تشغيل الاستجابة المباشرة](run-live-response.md)
####### [جهاز إيقاف التجهيز](offboard-machine-api.md)
####### [ملف إيقاف وفحص](stop-and-quarantine-file.md)
####### [إجراء إلغاء الجهاز](cancel-machine-action.md)

###### [توصية]()
####### [أساليب التوصيات وخصائصها](recommendation.md)
####### [سرد كل التوصيات](get-all-recommendations.md)
####### [الحصول على توصية بواسطة المعرّف](get-recommendation-by-id.md)
####### [الحصول على توصية حسب البرنامج](list-recommendation-software.md)
####### [قائمة الأجهزة حسب التوصية](get-recommendation-machines.md)
####### [نقاط الضعف في القائمة حسب التوصية](get-recommendation-vulnerabilities.md)

###### [نشاط المعالجة]()
####### [أساليب وخصائص نشاط الإصلاح](get-remediation-methods-properties.md)
####### [الحصول على نشاط معالجة واحد بواسطة المعرّف](get-remediation-one-activity.md)
####### [سرد كل أنشطة المعالجة](get-remediation-all-activities.md)
####### [سرد الأجهزة التي تم عرضها لنشاط معالجة واحد](get-remediation-exposed-devices-activities.md)

###### [النتيجة]()
####### [أساليب النقاط وخصائصها](score.md)
####### [درجة التعرض للقائمة حسب مجموعة الجهاز](get-machine-group-exposure-score.md)
####### [الحصول على نقاط التعرض للضوء](get-exposure-score.md)
####### [الحصول على نقاط آمنة للجهاز](get-device-secure-score.md)

###### [البرامج]()
####### [أساليب البرنامج وخصائصه](software.md)
####### [قائمة البرامج](get-software.md)
####### [الحصول على البرامج حسب المعرّف](get-software-by-id.md)
####### [توزيع إصدار برنامج القائمة](get-software-ver-distribution.md)
####### [سرد الأجهزة حسب البرنامج](get-machines-by-software.md)
####### [الثغرات في القائمة حسب البرنامج](get-vuln-by-software.md)
####### [فقدان KBs](get-missing-kbs-software.md)

###### [User]()
####### [أساليب المستخدم](user.md)
####### [الحصول على تنبيهات ذات صلة بالمستخدم](get-user-related-alerts.md)
####### [الحصول على الأجهزة ذات الصلة بالمستخدمين](get-user-related-machines.md)

###### [ثغرة أمنية]()
####### [أساليب الثغرات وخصائصها](vulnerability.md)
####### [نقاط الضعف في القائمة](get-all-vulnerabilities.md)
####### [الثغرات في القائمة حسب الجهاز والبرامج](get-all-vulnerabilities-by-machines.md)
####### [الحصول على ثغرة أمنية بواسطة المعرّف](get-vulnerability-by-id.md)
####### [أجهزة القائمة حسب الثغرة الأمنية](get-machines-by-vulnerability.md)

##### [كيفية استخدام واجهات برمجة التطبيقات - نماذج]()
###### [Power Automate](api-microsoft-flow.md)
###### [Power BI](api-power-bi.md)
###### ["الصيد المتقدم" باستخدام Python](run-advanced-query-sample-python.md)
###### [الصيد المتقدم باستخدام PowerShell](run-advanced-query-sample-powershell.md)
###### [استخدام استعلامات OData](exposed-apis-odata-samples.md)


#### [واجهة برمجة التطبيقات لبث البيانات الخام]()
##### [بث البيانات الخام](raw-data-export.md)
##### [بث أحداث الصيد المتقدمة إلى مركز أحداث Azure](raw-data-export-event-hub.md)
##### [بث أحداث الصيد المتقدمة إلى حساب التخزين](raw-data-export-storage.md)

#### [تكامل إدارة معلومات الأمان والأحداث]()
##### [دمج أدوات إدارة معلومات الأمان والأحداث مع Microsoft Defender لنقطة النهاية](configure-siem.md)
##### [استكشاف مشاكل تكامل أداة إدارة معلومات الأمان والأحداث وإصلاحها](troubleshoot-siem.md)

#### [الشركاء واجهات برمجة التطبيقات]()
##### [تطبيقات الشركاء](partner-applications.md)
##### [التطبيقات المتصلة](connected-applications.md)
##### [مستكشف واجهة برمجة التطبيقات](api-explorer.md)

#### [عنصر تحكم الوصول المستند إلى الدور]()
##### [إدارة الوصول إلى المدخل باستخدام RBAC](rbac.md)
##### [إنشاء أدوار وإدارتها](user-roles.md)
##### [إنشاء مجموعات الأجهزة وإدارتها]()
###### [استخدام مجموعات الأجهزة](machine-groups.md)
###### [إنشاء علامات الجهاز وإدارتها](machine-tags.md)







### [تكامل موفر خدمة الأمان المدار (MSSP)]()
#### [تكوين تكامل موفر خدمة الأمان المدار](configure-mssp-support.md)
#### [موفرو خدمات الأمان المدارة المعتمدون](mssp-list.md)
#### [منح MSSP حق الوصول إلى المدخل](grant-mssp-access.md)
#### [الوصول إلى مدخل عميل MSSP](access-mssp-portal.md)
#### [تكوين إعلامات التنبيهات](configure-mssp-notifications.md)
#### [الحصول على وصول إلى تطبيق الشريك](exposed-apis-create-app-partners.md)
#### [إحضار التنبيهات من مستأجر العملاء](fetch-alerts-mssp.md)
#### [فرصة موفر خدمة أمان مدارة](mssp-support.md)
### [سيناريوهات تكامل الشريك]()
#### [فرص الشريك التقني](partner-integration.md)
#### [كن شريكاً Microsoft Defender لنقطة النهاية](get-started-partner-integration.md)
### [عمليات التكامل]()
#### [Microsoft Defender لنقطة النهاية التكامل](threat-protection-integration.md)
#### [حماية المستخدمين والبيانات والأجهزة باستخدام الوصول الشرطي](conditional-access.md)
#### [نظرة عامة حول تكامل Microsoft Defender for Cloud Apps](microsoft-cloud-app-security-integration.md)

### [نظرة عامة حول حماية المعلومات في Windows]()
#### [التكامل في Windows](information-protection-in-windows-overview.md)

### [الوصول إلى Microsoft Defender لنقطة النهاية المجتمع](community.md)

### [موارد مفيدة](helpful-resources.md)

## [استكشاف الأخطاء وإصلاحها]()
### [استكشاف حالة المستشعر وإصلاحها]()
#### [التحقق من حالة المستشعر](check-sensor-status.md)
#### [إصلاح أدوات الاستشعار غير الصحية](fix-unhealthy-sensors.md)
#### [الأجهزة غير النشطة](fix-unhealthy-sensors.md#inactive-devices)
#### [الأجهزة التي تم تكوينها بشكل خاطئ](fix-unhealthy-sensors.md#misconfigured-devices)
#### [مراجعة أحداث المستشعر والأخطاء على الأجهزة التي تعمل عارض الأحداث](event-error-codes.md)

### [استكشاف مشاكل صحة المستشعر وإصلاحها باستخدام "محلل العملاء"]()
#### [نظرة عامة حول محلل العميل](overview-client-analyzer.md)
#### [تنزيل محلل العميل وتشغيله](download-client-analyzer.md)
#### [تشغيل محلل العميل على Windows](run-analyzer-windows.md)
#### [تشغيل محلل العميل على macOS أو Linux](run-analyzer-macos-linux.md)
#### [تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows](data-collection-analyzer.md)
#### [فهم تقرير HTML الخاص ب المحلل](analyzer-report.md)
#### [تقديم ملاحظات حول أداة محلل العميل](analyzer-feedback.md)

 

### [استكشاف مشاكل Microsoft Defender لنقطة النهاية الخدمة وإصلاحها]()
#### [استكشاف مشاكل الخدمة وإصلاحها](troubleshoot-mdatp.md)
#### [الاتصال Microsoft Defender لنقطة النهاية الدعم](contact-support.md)

### [استكشاف مشاكل الاستجابة المباشرة وإصلاحها](troubleshoot-live-response.md)

### [تجميع سجلات الدعم باستخدام LiveAnalyzer](troubleshoot-collect-support-log.md)

### [استكشاف مشاكل الحد من سطح الهجوم وإصلاحها]()
#### [حماية الشبكة](troubleshoot-np.md)
#### [قواعد تقليل الأجزاء المعرضة للهجوم](troubleshoot-asr.md)
#### [الترحيل إلى قواعد الحد من سطح الهجوم](migrating-asr-rules.md)

# [المستندات في Microsoft 365 Defender]()
## [Microsoft 365 Defender](../defender/index.yml)
## [دليل إعداد Microsoft Defender لـ Office 365](../office-365-security/index.yml)
## [Defender for Identity](/defender-for-identity/)
## [Defender for Cloud Apps](/cloud-app-security/)
## [Defender for Business](../defender-business/index.yml)

