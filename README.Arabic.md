# ChatGPT Line Bot

* [الإنجليزية](README.md)
* [النسخة باللغة الصينية التقليدية README.md](README.zh-TW.md)
* [الصينية البسيطة](README.zh-CN.md)
* [الفرنسية](README.French.md)
* [عربى](README.Arabic.md)


## مقدمة

في Line ، يمكنك إضافة ChatGPT Bot ببساطة عن طريق كتابة النصوص مباشرة في مربع الإدخال لبدء التفاعل مع ChatGPT.

<img src="img/2023-10-25-10-03-47.png" width="30%" />

## الأدوات والميزات

* `Python FastAPI`: إنشاء API استجابة ChatGPT
* `gpt4free`: **استخدام مجاني لخدمة OpenAI API**
* `Line messaging API channel`: تكامل مع API ChatGPT
* `Github`: تخزين الشيفرة
* `replit`: **نشر مجاني لتطبيق FastAPI الخاص بك**
* `CronJob`: إرسال طلبات دورية مجانية لتجنب انقطاع الخدمة


## خطوات التثبيت

### الحصول على الرموز

1. الحصول على رمز Line:
    1. قم بتسجيل الدخول إلى [Line Developer](https://developers.line.biz/zh-hant/)
    2. إنشاء الروبوت:
        1. إنشاء `مزود` -> انقر فوق `Create`
        2. إنشاء `قناة` -> حدد `Create a Messaging API channel`
        3. قم بإدخال المعلومات الأساسية الضرورية
        4. بمجرد الانتهاء من الإدخال ، في الجزء السفلي من `Basic Settings` ، هناك `Channel Secret` -> انقر على `Issue` ، بعد ذلك سيتم توليد `LINE_CHANNEL_SECRET` (سيتم استخدامه قريبًا)
        5. في `Messaging API` في الجزء السفلي ، هناك `Channel access token` -> انقر على `Issue` ، بعد ذلك سيتم توليد `LINE_CHANNEL_ACCESS_TOKEN` (سيتم استخدامه قريبًا)

### إعداد المشروع
1. إنشاء Fork لمشروع Github:
    1. سجل الدخول / سجل الدخول إلى [GitHub](https://github.com/)
    2. انتقل إلى [ChatGPT-Line-Bot](https://github.com/Lin-jun-xiang/ChatGPT-Line-Bot)
    3. انقر على `Star` لدعم المطور
    4. انقر على `Fork` لنسخ جميع الشيفرة إلى مستودعك
2. النشر (في مساحة مجانية):
    1. انتقل إلى [replit](https://replit.com/)
    2. انقر فوق `Sign Up` وقم بتسجيل الدخول باستخدام حساب `Github` الخاص بك ومن ثم قم بالتفويض -> انقر فوق `Skip` لتجاوز الإعداد الأولي
    3. بمجرد الوصول ، انقر على `Create` في الوسط -> انقر على `Import from Github` في الزر الأيمن العلوي
    4. إذا لم تكن قد قمت بإضافة مستودع Github بعد ، انقر على الارتباط `Connect GitHub to import your private repos.` -> حدد `Only select repositories` -> اختر `ChatGPT-Line-Bot`
    5. عد إلى الخطوة الرابعة ، في هذا الوقت يمكنك اختيار `ChatGPT-Line-Bot` في المشروع URL أعلاه -> انقر فوق `Import from Github`.

### تشغيل المشروع
1. تكوين المتغيرات البيئية
    1. بعد الانتهاء من الخطوة السابقة ، انتقل إلى `Secrets` في أسفل الشاشة في صفحة إدارة المشروع الرئيسية في `Replit`.
    2. بعد النقر فوق `Got it` على اليمين ، يمكنك إضافة متغيرات البيئة ، والتي يجب أن تتضمن:
        1. Line Channel Secret:
            - key: `LINE_CHANNEL_SECRET`
            - value: `[الذي تم الحصول عليه في الخطوة الأولى]`
        2. Line Channel Access Token:
            - key: `LINE_CHANNEL_ACCESS_TOKEN`
            - value: `[الذي تم الحصول عليه في الخطوة الأولى]`

        <img src="img/2023-10-25-10-00-59.png" width="60%" />

2. بدء التشغيل
    1. انقر فوق `Run` في الأعلى
    2. بمجرد النجاح ، ستظهر `Hello World` في الزاوية العليا اليمنى للشاشة ، ويمكنك نسخ العنوان في الأعلى للتو
    3. عد إلى Line Developer ، وفي `Messaging API` في الجزء السفلي ، يمكنك لصق العنوان الذي نسخته مع إضافة `/callback` مثل: `https://ChatGPT-Line-Bot.jimmylin.repl.co/callback`
    4. قم بتمكين `Use webhook` من الأسفل
    5. قم بإيقاف تشغيل `Auto-reply messages`
    - ملاحظة: إذا لم يتم استلام أي طلب في ساعة واحدة ، سيؤدي ذلك إلى إيقاف تشغيل البرنامج ، لذا يجب إتباع الخطوات التالية

        <img src="img/2023-10-25-10-01-21.png" width="60%" />

3. CronJob إرسال طلبات دورية
    1. سجل الدخول / سجل الدخول إلى [cron-job.org](https://cron-job.org/en/)
    2. بعد الدخول ، انتقل إلى الجهة العليا اليمنى واختر `CREATE CRONJOB`
    3. قم بإدخال `Title` ChatGPT-Line-Bot` ، وأدخل العنوان الذي نسخته في الخطوة السابقة ، مثل: `https://ChatGPT-Line-Bot.jimmylin.repl.co/`
    4. في الأسفل ، اضغط على كل `5 دقائق` مرة واحدة
    5. انقر فوق `CREATE`

### ربط الخدمة بـ Line Bot

ارجع إلى [Line Developer](https://manager.line.biz/account) الصفحة الرئيسية وانقر على `دليل إضافة الأصدقاء` ، ثم قم بمسح رمز الاستجابة السريعة للانضمام إلى LINE Bot:

الصفحة الرئيسية -> انقر على bot الخاص بك -> انقر على أدوات زيادة الأصدقاء -> إنشاء رمز استجابة سريعة للأصدقاء (https://manager.line.biz/account/<yourBotId>/gainfriends)

تهانينا! لقد أكملت أول LINE Bot خاص بك! جرب التحدث معه وشاهد كيف يرد عليك!

### تقدم - تخصيص الروبوت

بالإضافة إلى ذلك ، يمكننا استخدام الطريقة `prompt` للسماح لـ Line Bot بالرد بطريقة شخصية ، في `./chatgpt_linebot/prompts/template.py` يمكننا تعريف `template` ، مثل:

<img src="img/2023-10-27-10-09-17.png" width="60%" />

**سؤال**: ماذا تأكل في الفطور اليوم؟

**رد الروبوت**: حبيبي ، هل استيقظت صباح اليوم؟ لقد كنت في السرير في انتظارك ، أشعر بالجوع عند التفكير في جسمك الجميل. ماذا يجب أن أتناول في الفطور اليوم؟ هل يجب أن أحضر لك بيض مقلي حار ، مثل لياقتك الجسدية المثيرة؟ 😏🍳

---

## المراجع

[Line_Bot_Tutorial](https://github.com/FawenYo/LINE_Bot_Tutorial)

[ChatGPT-Line-Bot](https://github.com/TheExplainthis/ChatGPT-Line-Bot)
