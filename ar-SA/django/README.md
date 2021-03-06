# ما هو جانغو؟

جانغو (/ˈdʒæŋɡoʊ/*جانغ-جوه*) إطار تطبيق ويب حر ومفتوح المصدر مكتوب بلغة بايثون. أطار العمل مكون من مجموعه من المكونات التى سوف تساعدك على تطوير المواقع بطريقة اسهل واسرع.

عندما تقوم ببناء موقع على شبكة الإنترنت، تحتاج دائماً مجموعة مماثلة من المكونات: طريقة للتعامل مع مصادقة المستخدم (التسجيل، الدخول، والخروج)، وصفحة إدارية لموقع الويب الخاص بك، والاستمارات، وطريقة لتحميل الملفات، إلخ.

لحسن الحظ لاحظ أشخاص آخرين منذ وقت طويل أن مطوري الويب تواجههم مشاكل مماثلة عند إنشاء موقع جديد، فتعاونوا في إنشاء أطارات عمل (جانغو واحد منهم) التي تعطيك مكونات جاهزة يمكنك استخدامها.

اطارات العمل موجودة لتنقدكم من إعادة اختراع ما تم اختراعه من قبل، وتساعد في تخفيف بعض النفقات العامة عندما تقوم ببناء موقع جديد.

## لماذا تحتاج إلى إطار عمل؟

لفهم ما هو جانغو في الواقع ، علينا أن نلقي نظرة فاحصة على الملقمات. أول شيء أن الملقم يحتاج إلى معرفة أن كنت تريد منه ان يعطيك صفحة انترنت.

تخيل علبة بريد (ميناء) التي يتم ضبطها للرسائل الواردة (الطلبات). وهذا يتم عن طريق خادم ويب. خادم الويب يقوم بقراءة الرسالة وثم يرسل استجابة مع صفحة ويب. ولكن عندما تريد أن ترسل شيئا، فأنت بحاجة إلى بعض المحتوى. وجانغو هو الشيء الذي يساعدك في إنشاء المحتوى.

## ماذا يحدث عندما يطلب شخص ما موقع انترنت من خادمك؟

عندما يصل طلب إلى الخادم ، يتم تمريره لدجانغو ، والذي سيحاول ما الذي تم طلبه. إنه يأخذ عنوان صفحة ويب أولا ويحاول معرفة ما يجب القيام به. يتم هذا الجزء من قبل دجانغو ** urlresolver** (لاحظ أن عنوان موقع ويب يسمى URL - محدد مواقع الموارد - لذلك الاسم * urlresolver * منطقي). أنه ليس ذكية جدا - فإنه يأخذ قائمة من الأنماط ويحاول مطابقة عنوان URL. جانغو يتحقق من الأنماط من أعلى إلى أسفل، وإذا تم مطابقة شيء، يقوم جانغو بتمرير الطلب إلى الدالة المرتبطة بها (والتي تسمى *view*).

تخيل ناقل البريد مع رسالة. تتمشى في الشارع وتفحص جميع ارقام البيوت مع الرقم الموجود في الرسالة. اذا كان مطابقا ، تضع الرسالة هناك. هذه هي الطريقة التي يعمل urlresolver بها!

في الدالة *view*، تتم جميع الأمور المثيرة للاهتمام: يمكننا أن ننظر إلى قاعدة بيانات للبحث عن بعض المعلومات. ربما طلب المستخدم بتغيير شيء ما في البيانات؟ مثلما تقول الرسالة: "يرجى تغيير وصف وظيفتي". يمكن ل * view* التحقق مما إذا كان مسموحا لك القيام بذلك، ثم تحديث الوصف الوظيفي لك وإرسال رسالة مرة أخرى: "تم!" ثم * view* يولد استجابة و جانغو يمكن أن يرسلها إلى متصفح الويب الخاص بالمستخدم.

بالطبع الوصف اعلاه مبسط كثيرا ، لكنك لست في حاجة لمعرفة كل المعلومات التقنية حاليا، الحصول على فكرة عامة كافي.

لذلك بدلا من الغوص كثيرا في التفاصيل، نحن سوف نبدأ ببساطة بصناعة شيء باستخدام جانغو وسنتعلم كل الأجزاء المهمة على طول الطريق!