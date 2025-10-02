**(API) <span dir="rtl">توثيـق واجهـات برمجـة التطبيقــات</span>**

***Reqres.in <span dir="rtl">والمصادقة باستخدام واجهة</span> CRUD
<span dir="rtl">مثال توضيحي لعمليات</span>***

![](./media/image1.jpeg)

**<span dir="rtl">إعداد: أحمد موسي</span>**  
**<span dir="rtl">التاريخ: 2025/09/25</span>**

# <span dir="rtl">المحتويات</span>

1.  [**<span dir="rtl">المقدمة</span>**](#مقدمة)

2.  [**<span dir="rtl">المتطلبات الأساسية</span>**](#متطلبات)

3.  **[<span dir="rtl">نظرة عامة على واجهة</span>
    Reqres.in](#نظرةعامه)  **
    3.1 <span dir="rtl"></span> <span dir="rtl"> [طبيعة الواجهة وحدود
    الاستخدام](#طبيعةوجهة)</span>

> <span dir="rtl">3.2 [أفضل ممارسات الاختبار](#افضلممارسات)</span>

4.  [**<span dir="rtl">المصادقة (</span>Authentication /
    Login<span dir="rtl">)</span>**](#المصادقة)

> ** **4**.**1 <span dir="rtl">[الهدف](#هدفمصادقة)</span>  
>  4.2 [<span dir="rtl">إرسال طلب تسجيل الدخول</span>](#ارسالطلبتس)  
>  4.3 <span dir="rtl">[الاستجابة المتوقعة](#استجابةمتوقع)</span>  
>  4.4 <span dir="rtl"></span>[<span dir="rtl">استخدام الـ</span>
> Token](#استخدامتوكن)  
>  4.5 <span dir="rtl">[ملاحظات مهمة](#ملاحظاتمهمه)</span>

5.  [**<span dir="rtl">العمليات الأساسية (</span>CRUD<span dir="rtl">)
    باستخدام</span> Postman**](#عملياتاساسى)

    1.  [GET <span dir="rtl">– جلب البيانات</span>](#جلببيانات1)
        <span dir="rtl"></span>

    2.  [POST <span dir="rtl">– إنشاء بيانات
        جديدة</span>](#انشاءبيانان2)

    3.  [PUT <span dir="rtl">– تعديل كامل للبيانات</span>](#تعديلبيان3)

    4.  [PATCH <span dir="rtl">– تعديل جزئي
        للبيانات</span>](#تعديلجزئي4)

    5.  [DELETE <span dir="rtl">– حذف البيانات</span>](#حذفبيانات5)

6.  [**<span dir="rtl">العمليات الأساسية</span>
    <span dir="rtl">على</span> Resources**](#عاساسيةعريسورس)

    1.  [– GET <span dir="rtl">جلب الموارد</span>](#جلب61)

    2.  [– GET <span dir="rtl">جلب مورد واحد</span>](#جلب62)

7.  [**<span dir="rtl">أمثلة باستخدام أمر</span> curl**](#امثلة7)

    1.  [<span dir="rtl">المصادقة</span> (Authentication /
        Login)](#مصاد71)

    2.  [<span dir="rtl">جلب مستخدم و مستخدمين
        (</span>GET<span dir="rtl">)</span>](#مصا72)

    3.  [<span dir="rtl">إنشاء مستخدم
        (</span>POST<span dir="rtl">)</span>](#مصا73)

    4.  [<span dir="rtl">تعديل كامل
        (</span>PUT<span dir="rtl">)</span>](#مصا74)

    5.  [<span dir="rtl">تعديل جزئي
        (</span>PATCH<span dir="rtl">)</span>](#مصا75)

    6.  [<span dir="rtl">حذف
        (</span>DELETE<span dir="rtl">)</span>](#مصا76)

8.  [**<span dir="rtl">معالجة الأخطاء</span> (Error
    Handling)**](#معالجه8)

    1.  [<span dir="rtl">مبادئ عامة</span>](#معال81)

    2.  [<span dir="rtl">رموز الحالة الشائعة</span>](#معا82)

    3.  [<span dir="rtl">مسار تشخيص سريع</span>
        (Troubleshooting)](#معا83)

    4.  [<span dir="rtl">أفضل ممارسات التعامل مع الأخطاء في
        العميل</span>](#افض84)

9.  [**<span dir="rtl">التصفح
    (</span>Pagination<span dir="rtl">)</span>**](#تص9)

10. [**<span dir="rtl">الملاحق</span>**](#ملاح10)

    1.  [<span dir="rtl">مصطلحات موحّدة</span>](#مصطلح101)

    2.  [<span dir="rtl">روابط مفيدة</span>](#روابط102)  
          <span dir="rtl">  
        </span>

<!-- -->

1.  <span id="مقدمة"
    class="anchor"></span>**<span dir="rtl">المقدمة</span>**

<span dir="rtl">يُقدّم هذا الدليل شرحًا عمليًا لاستخدام واجهة برمجة
التطبيقات التجريبية</span> Reqres.in<span dir="rtl">.</span>

<span dir="rtl">يٌركّز الدليل على توضيح كيفية تنفيذ العمليات
الأساسية</span> (CRUD) <span dir="rtl">وآلية المصادقة</span>
(Authentication) <span dir="rtl">بالإضافة إلى معالجة الأخطاء</span>
(Error Handling) <span dir="rtl">وتنظيم النتائج عبر التصفّح</span>
(Pagination)<span dir="rtl">.</span>

<span dir="rtl">الهدف من هذا الدليل هو تزويد المطوّر بخطوات واضحة وأمثلة
عملية يمكن الاعتماد عليها لاختبار واجهات برمجة التطبيقات وفهم كيفية
عملها</span>.

**<span dir="rtl">الفئات المستهدفة</span>:**

- <span dir="rtl">المطوّرون المبتدئون الراغبون في تعلّم مبادئ</span> REST
  APIs<span dir="rtl">، وكذلك المطوّرون المتقدمون الذين يحتاجون إلى مرجع
  سريع أو أمثلة عملية.</span>

- <span dir="rtl">فرق العمل التي تحتاج إلى مرجع تدريبي لتجربة وبناء
  طلبات واجهة برمجة التطبيقات</span>.

2.  <span id="متطلبات" class="anchor"></span>**<span dir="rtl">المتطلبات
    الأساسية</span>**

<span dir="rtl">قبل البدء في استخدام واجهة</span>
Reqres.in<span dir="rtl">، ينبغي التأكد من توافر مجموعة من المتطلبات
التي تُمكّن المطوّر من تنفيذ الطلبات</span> (Requests)
<span dir="rtl">ومعالجة الاستجابات</span> (Responses)
<span dir="rtl">بكفاءة</span>:

- <span dir="rtl">اتصال إنترنت مستقر لضمان تنفيذ جميع العمليات دون
  انقطاع</span>.

- <span dir="rtl">أداة لاختبار واجهات برمجة التطبيقات</span> (API
  Testing Tool) <span dir="rtl">مثل</span> Postman <span dir="rtl">أو أي
  بديل مكافئ يتيح إنشاء الطلبات، إضافة الرؤوس</span>
  (Headers)<span dir="rtl">، إرسال البيانات عبر الجسم</span>
  (Body)<span dir="rtl">، واستعراض الاستجابات</span>.

> <span dir="rtl">يمكن تحميل البرنامج من هنا:</span>
> [Postman](https://www.postman.com/downloads/)

- <span dir="rtl">يمكن الاستعانة بـ أداة سطر أوامر</span> (Command Line
  Tool) <span dir="rtl">مثل</span> cURL <span dir="rtl">لاختبار الطلبات
  من خلال الطرفية</span> (Terminal)<span dir="rtl">، بينما يكفي
  للمبتدئين الاعتماد على أداة رسومية مثل</span> Postman
  <span dir="rtl">في المراحل الأولى</span>.

- <span dir="rtl">يُفضل الإلمام بأساسيات</span> REST
  APIs<span dir="rtl">، بما في ذلك طرق</span> HTTP Methods
  <span dir="rtl">، (</span>GET<span dir="rtl">،</span>POST
  <span dir="rtl">،</span>PUT <span dir="rtl">،</span>
  PATCH<span dir="rtl">،</span> DELETE <span dir="rtl">) والبنية العامة
  للطلبات والاستجابات</span>.

- <span dir="rtl">معرفة برموز حالة</span> (HTTP Status Codes) HTTP
  <span dir="rtl">مثل</span>:

  - 200 <span dir="rtl">(تم التنفيذ بنجاح)</span>

  - 201 <span dir="rtl">(تم إنشاء مورد جديد)</span>

  - 400 <span dir="rtl">(طلب غير صالح)</span>

  - 401 <span dir="rtl">(غير مصرح)</span>

  - 404 <span dir="rtl">(المورد غير موجود)</span>

- <span dir="rtl">إلمام بكيفية التعامل مع</span> JSON (JavaScript Object
  Notation)<span dir="rtl">، باعتبارها الصيغة الأساسية لتبادل البيانات
  بين العميل والخادم.</span>

3.  <span id="نظرةعامه" class="anchor"></span> **<span dir="rtl">نظرة
    عامة وطبيعة الواجهة</span> (Reqres.in)**

Reqres.in <span dir="rtl">هي واجهة برمجة تطبيقات تجريبية</span> (Mock
API) <span dir="rtl">تتيح للمطوّرين اختبار مفاهيم</span> REST APIs
<span dir="rtl">في بيئة آمنة ومجانية. صُمِّمت هذه الواجهة لمحاكاة سلوك
أنظمة حقيقية دون الحاجة إلى إعداد خوادم أو قواعد بيانات</span>.

**<span dir="rtl">المزايا الرئيسية:</span>**

- <span dir="rtl">مجانية بالكامل ولا تتطلّب إنشاء حساب</span>.

- <span dir="rtl">تدعم العمليات الأساسية</span> (CRUD)
  <span dir="rtl">عبر طرق</span> HTTP Methods<span dir="rtl">.</span>

- <span dir="rtl">تُوفّر بيانات جاهزة للتعامل مع كيانات مثل</span> Users
  <span dir="rtl">و</span> Resources<span dir="rtl">.</span>

- <span dir="rtl">تدعم التصفّح</span> (Pagination) <span dir="rtl">وإرجاع
  رموز الحالة القياسية</span> (HTTP Status
  Codes)<span dir="rtl">.</span>

- <span dir="rtl">سهلة الاستخدام عبر أدوات رسومية مثل</span> Postman
  <span dir="rtl">أو عبر الطرفية باستخدام</span>
  cURL<span dir="rtl">.</span>

<span dir="rtl">**الموقع الرسمي**:</span> <https://reqres.in>

<span id="طبيعةوجهة" class="anchor"></span>**<span dir="rtl">3.1</span>
<span dir="rtl">طبيعة الواجهة التجريبية</span>**

- Reqres.in <span dir="rtl">ليست قاعدة بيانات فعلية؛ الغرض منها التدريب
  والعرض فقط</span>.

- <span dir="rtl">بعد تنفيذ</span> POST <span dir="rtl">وإنشاء
  معرّف</span> (id)<span dir="rtl">، قد لا تتمكّن من جلب نفس العنصر لاحقًا
  عبر</span> GET <span dir="rtl">قد تعود الاستجابة (404</span> Not
  Found<span dir="rtl">).</span>

- <span dir="rtl">هذا السلوك متعمّد للتجارب وليس خللًا</span>.

**<span dir="rtl">حدود الاستخدام</span> (Rate Limits)**

- <span dir="rtl">قد تُحاكي الواجهة قيودًا على المعدّل (429</span>Too Many
  Requests <span dir="rtl">).</span>

- <span dir="rtl">عند ظهور 429، يُنصح بالانتظار فترة قصيرة ثم إعادة
  المحاولة</span>.

<span id="افضلممارسات"
class="anchor"></span>**<span dir="rtl">3.2</span> <span dir="rtl">أفضل
ممارسات الاختبار</span>**

- <span dir="rtl">استخدم معرّفات ثابتة في أمثلة القراءة مثل:</span> GET
  /api/users/2)<span dir="rtl">).</span>

- <span dir="rtl">افصل بين اختبارات القراءة</span> (GET)
  <span dir="rtl">والكتابة</span> (POST/PUT/PATCH/DELETE)
  <span dir="rtl">لتتبّع النتائج بسهولة</span>.

- <span dir="rtl">احتفظ بقوالب جاهزة للطلبات</span> (Postman Collection)
  <span dir="rtl">لتسريع الاختبارات المتكررة</span>.

4.  <span id="المصادقة" class="anchor"></span>**<span dir="rtl">المصادقة
    (</span>Authentication / Login<span dir="rtl">)</span>**

**4**<span id="هدفمصادقة" class="anchor"></span>**.1
<span dir="rtl">الهدف من المصادقة</span>**  
<span dir="rtl">التحقّق من هوية المستخدم والحصول على رمز أمني</span>
(Token) <span dir="rtl">لاستخدامه في تفويض الطلبات اللاحقة</span>.

<span id="ارسالطلبتس" class="anchor"></span>**4.2 <span dir="rtl">إرسال
طلب تسجيل الدخول</span>**

- <span dir="rtl">الطريقة (</span>Method<span dir="rtl">):</span> POST

- <span dir="rtl">المسار</span> /api/login :(Endpoint)
  <span dir="rtl"></span>

- <span dir="rtl">الرؤوس</span> Content-Type: application/json
  :(Headers)

- <span dir="rtl">الجسم</span>
  <span dir="rtl"></span>(Body)<span dir="rtl">:</span>JSON

{

"email": "eve.holt@reqres.in",

"password": "Ahmed1-Viper@1stPass"

}

![](./media/image2.png)

<span id="استجابةمتوقع" class="anchor"></span>**4.3
<span dir="rtl">الاستجابة المتوقعة</span>**

- **<span dir="rtl">عند النجاح</span> :(OK) <span dir="rtl"></span>200
  <span dir="rtl"></span>**

![](./media/image3.png)

- **<span dir="rtl">في حال الفشل</span>:**

  - <span dir="rtl">(بيانات ناقصة أو غير صحيحة)</span> 400 Bad Request

  - <span dir="rtl">(غير مصرح) 401</span> Unauthorized

<span id="استخدامتوكن" class="anchor"></span>**4.4
<span dir="rtl">استخدام الـ</span> Token <span dir="rtl">في الطلبات
اللاحقة</span>**

- <span dir="rtl">الطريقة العامة (إضافة يدويا فى الـ</span>
  Headers<span dir="rtl">)</span>

  - Authorization: Bearer \<token\>

<img src="./media/image4.png" style="width:4.76852in;height:1.53704in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-24 220352.png" />

- <span dir="rtl">الطريقة البديلة فى</span> Postman
  <span dir="rtl">(اختر طريقة واحدة اى تضع القيمه فى</span> Headers
  <span dir="rtl">أو من</span> Auth Type<span dir="rtl">)</span>

  - <span dir="rtl">عبر تبويب</span> Headers:

> Authorization: Bearer \<token\> <span dir="rtl"></span>

- <span dir="rtl">أو عبر تبويب</span> Auth:

> Type: Bearer Token <span dir="rtl"></span>
>
> <span dir="rtl">ثم إدخال قيمة الـ</span> Token
> <span dir="rtl">المستلمة</span>.

![](./media/image5.png)

<span id="ملاحظاتمهمه" class="anchor"></span>**4.5
<span dir="rtl">ملاحظات مهمة</span>**

- <span dir="rtl">بما أنّ</span> Reqres.in <span dir="rtl">واجهة تجريبية،
  بعض الطلبات قد تعمل دون الحاجة إلى</span>
  Token<span dir="rtl">.</span>

- <span dir="rtl">يبقى الـ</span> Token <span dir="rtl">صالحًا ما لم
  يتغيّر</span>.

- <span dir="rtl">لا حاجة لإرسال</span> Body <span dir="rtl">مع
  طلبات</span> Get<span dir="rtl">.</span>

- **<span dir="rtl">الطلبات تتطلّب إضافة</span> API Key
  <span dir="rtl">في الهيدر</span>:  
  x-api-key: reqres-free-v1**

![](./media/image6.png)

5.  <span id="عملياتاساسى"
    class="anchor"></span>**<span dir="rtl">العمليات الأساسية</span>
    (CRUD)<span dir="rtl">باستخدام برنامج</span> Postman**

<span dir="rtl">يوضّح هذا القسم كيفية تنفيذ العمليات الأساسية على الموارد
(المستخدمين والمصادر) باستخدام واجهة</span> Reqres.in.  
<span dir="rtl">كل عملية مرفقة بخطوات التنفيذ، مقتطف</span> JSON
<span dir="rtl">مبسّط، وصورة</span> Postman <span dir="rtl">توضّح الطلب
والاستجابة</span>.

<span id="جلببيانات1"
class="anchor"></span>**<span dir="rtl">5.1</span>GET
<span dir="rtl"></span>– <span dir="rtl">جلب البيانات</span>**

<span dir="rtl">**الهدف:** استدعاء بيانات من الخادم: إمّا قائمة
المستخدمين أو مستخدم واحد</span>.

**5.1.2 <span dir="rtl">جلب قائمة المستخدمين</span>**

- Method: GET

- Endpoint: /api/users?page=2

- Headers: Content-Type: application/json

- <span dir="rtl">غير مطلوب</span>Body:

**<span dir="rtl">استجابة متوقعة</span> :(OK)
<span dir="rtl">200</span>**

![](./media/image7.png)

**5.1.3 <span dir="rtl">جلب مستخدم واحد</span>**

- Method: GET

- Endpoint: /api/users/2

- Headers: Content-Type: application/json

**<span dir="rtl">استجابة متوقعة</span> :(OK)
<span dir="rtl">200</span>**

![](./media/image8.png)

- <span dir="rtl">في حال لم يُعثر على المستخدم</span> 404 Not
  Found<span dir="rtl">.</span>

<span id="انشاءبيانان2" class="anchor"></span>**5.2
<span dir="rtl"></span>POST <span dir="rtl"></span>–
<span dir="rtl">إنشاء بيانات جديدة</span>**

<span dir="rtl">الهدف: إرسال بيانات جديدة إلى الخادم لإنشاء
مستخدم</span>.

- Method: POST

- Endpoint: /api/users

- Headers: Content-Type: application/json

{

"name": "Ahmed Mousa",

"job": "Tech Writer"

}

**<span dir="rtl">استجابة متوقعة</span> :(Created)
<span dir="rtl">201</span>**

![](./media/image9.png)

<span id="تعديلبيان3" class="anchor"></span>**5.3
<span dir="rtl"></span> – PUT<span dir="rtl">تعديل كامل
للبيانات</span>**

<span dir="rtl">الهدف: تحديث بيانات مستخدم بشكل كامل (استبدال القيم
القديمة بقيم جديدة</span>).

- Method: PUT

- Endpoint: /api/users/2

{

"name": "Ahmed Hamdy",

"job": "Tech Writer Lead"

}

**<span dir="rtl">استجابة متوقعة</span> :(OK)
<span dir="rtl">200</span>**

![](./media/image10.png)

<span id="تعديلجزئي4" class="anchor"></span>**5.4
<span dir="rtl"></span>– PATCH <span dir="rtl">تعديل جزئي
للبيانات</span>**

<span dir="rtl">الهدف: تحديث جزء محدد من بيانات المستخدم</span>.

- Method: PATCH

- Endpoint: /api/users/2

{

"job": "Principal Technical Writer"

}

**<span dir="rtl">استجابة متوقعة</span> :(OK)
<span dir="rtl">200</span>**

![](./media/image11.png)

<span id="حذفبيانات5" class="anchor"></span>**5.5
<span dir="rtl"></span>DELETE <span dir="rtl"></span>–
<span dir="rtl">حذف البيانات</span>**

<span dir="rtl">الهدف: حذف مستخدم بشكل نهائي</span>.

- Method: DELETE

- Endpoint: /api/users/2

- <span dir="rtl">غير مطلوب</span>Headers / Body:

**<span dir="rtl">استجابة متوقعة</span> No Content
<span dir="rtl">204</span>**

<img src="./media/image12.png" style="width:4.79408in;height:2.81345in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 202115.png" />

<span id="عاساسيةعريسورس"
class="anchor"></span>**<span dir="rtl">6.</span>
<span dir="rtl">العمليات الأساسية على</span> (Resources)**

<span id="جلب61" class="anchor"></span>**6.1 <span dir="rtl"></span>
GET<span dir="rtl">جلب قائمة الموارد</span>**

<span dir="rtl">الهدف: جلب قائمة</span> Resources <span dir="rtl">مع دعم
التصفّح</span> (Pagination)<span dir="rtl">.</span>

<span dir="rtl">تفاصيل الطلب</span>

- Method: GET

- Endpoint: /api/unknown?page=1

- <span dir="rtl">غير مطلوبين</span> Headers & Body:

**<span dir="rtl">استجابة متوقعة</span> :(OK)
<span dir="rtl">200</span>**

![](./media/image13.png)

**<span dir="rtl">ملاحظات مهمة</span>**

- <span dir="rtl">مفاتيح التصفّح:</span> page, per_page, total,
  total_pages

- <span dir="rtl">يمكن تغيير الصفحة باستخدام معاملات الاستعلام</span>
  (Query Parameters) <span dir="rtl">مثل</span> ?page=2

<span id="جلب62" class="anchor"></span>**6.2 <span dir="rtl"></span>GET
<span dir="rtl"></span>– <span dir="rtl">جلب مورد واحد</span>**

<span dir="rtl">الهدف: جلب</span> Resource <span dir="rtl">واحد باستخدام
المعرّف</span> (ID).

<span dir="rtl">تفاصيل الطلب</span>

- Method: GET

- Endpoint: /api/unknown/2

- <span dir="rtl">غير مطلوبين</span> Headers & Body:

**<span dir="rtl">استجابة متوقعة</span> :(OK)
<span dir="rtl">200</span>**

![](./media/image14.png)

**<span dir="rtl">في حال عدم العثور</span>**

- **404 Not Found** <span dir="rtl">عند استخدام معرّف غير موجود</span>.

![](./media/image15.png)

<span id="امثلة7" class="anchor"></span>**<span dir="rtl">7.</span>
<span dir="rtl">أمثلة باستخدام أمر</span> curl**

<span dir="rtl">يمكن نسخ الأمر ثم لصقة فى سطر الأوامر</span>
CMD<span dir="rtl">.</span>

<span id="مصاد71" class="anchor"></span>**<span dir="rtl">7.1</span>
<span dir="rtl">المصادقة</span> (Authentication / Login)**

**cURL:**

curl -X POST "https://reqres.in/api/login" -H "Content-Type:
application/json" -H "x-api-key: reqres-free-v1" -d
"{\\email\\:\\eve.holt@reqres.in\\,\\password\\:\\AhmedTheBest\\}"

<img src="./media/image16.png" style="width:6.5in;height:1.05556in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 203950.png" />**<span dir="rtl">استجابة
متوقعة</span> 200 :(OK)**

<span id="مصا72" class="anchor"></span>**<span dir="rtl">7.2</span>GET
<span dir="rtl"></span>– <span dir="rtl">جلب مستخدم</span>**

> **cURL:**
>
> <img src="./media/image17.png" style="width:6.49097in;height:0.96319in"
> alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 210044.png" />curl
> "https://reqres.in/api/users/2" -H "x-api-key: reqres-free-v1"

**<span dir="rtl">جلب المستخدمين</span>**

**cURL:**

curl "https://reqres.in/api/users?page=2" -H "x-api-key: reqres-free-v1"

<img src="./media/image18.png" style="width:6.5in;height:1.76875in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 205809.png" />

<span id="مصا73" class="anchor"></span>**<span dir="rtl">7.3</span>POST
<span dir="rtl"></span>– <span dir="rtl">إنشاء مستخدم</span>**

**cURL:**

curl -X POST "https://reqres.in/api/users" -H "Content-Type:
application/json" -H "x-api-key: reqres-free-v1" -d
"{\\name\\:\\Ahmed\\,\\job\\:\\Developer\\}"

<img src="./media/image19.png" style="width:6.49097in;height:0.83333in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 204807.png" />

<span id="مصا74" class="anchor"></span>**<span dir="rtl">7.4</span>PUT
<span dir="rtl"></span>– <span dir="rtl">تعديل كامل</span>**

**cURL:**

curl -X PUT "https://reqres.in/api/users/2" -H "Content-Type:
application/json" -H "x-api-key: reqres-free-v1" -d
"{\\name\\:\\Ahmed\\,\\job\\:\\Senior Dev\\}"

<img src="./media/image20.png" style="width:6.49097in;height:0.81458in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 205018.png" />

<span id="مصا75" class="anchor"></span>**<span dir="rtl">7.5</span>PATCH
<span dir="rtl"></span>– <span dir="rtl">تعديل جزئي</span>**

**cURL:**

curl -X PATCH "https://reqres.in/api/users/2" -H "Content-Type:
application/json" -H "x-api-key: reqres-free-v1" -d "{\\job\\:\\Tech
Lead\\}"

<img src="./media/image21.png" style="width:6.5in;height:0.79653in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 205337.png" />

<span id="مصا76"
class="anchor"></span>**<span dir="rtl">7.6</span>DELETE
<span dir="rtl"></span>– <span dir="rtl">حذف</span>**

**cURL:**

curl -X DELETE "https://reqres.in/api/users/2" -H "x-api-key:
reqres-free-v1"

**<span dir="rtl">استجابة متوقعة:</span>204 No Content**
<img src="./media/image22.png" style="width:6.49097in;height:0.69444in"
alt="C:\Users\engra\AppData\Local\Microsoft\Windows\INetCache\Content.Word\Screenshot 2025-09-25 205604.png" />

**<span dir="rtl">التفكيك والشرح</span>:**

1.  **curl**

    - <span dir="rtl">هذا البرنامج هو أداة لعمل طلبات</span> HTTP (GET /
      POST / PUT / PATCH / DELETE) <span dir="rtl"></span>

2.  **-X POST**

    - -X <span dir="rtl">معناها: نوع الطريقة اللي هتستخدمه</span> (HTTP
      Method) <span dir="rtl"></span>

    - <span dir="rtl">هنا اخترنا</span> POST

    - <span dir="rtl">يمكن أن يكون</span>:

      - GET <span dir="rtl">جلب بيانات</span>

      - POST <span dir="rtl">إرسال بيانات جديدة</span>

      - PUT <span dir="rtl">تحديث كامل</span>

      - PATCH <span dir="rtl">تحديث جزئي</span>

      - DELETE <span dir="rtl">حذف</span>

3.  **"https://reqres.in/api/login"**

    - <span dir="rtl">ده الـمسار
      (</span>Endpoint<span dir="rtl">)</span> <span dir="rtl">اللي
      هيتبعتله الطلب</span>.

    - <span dir="rtl">في المثال</span> /api/login
      <span dir="rtl"></span>

4.  **-H "Content-Type: application/json"**

    - -H <span dir="rtl">معناها</span> Header <span dir="rtl"></span>

    - <span dir="rtl">الـ</span> Header <span dir="rtl">بيتكتب كـ</span>
      Name: Value

    - <span dir="rtl">هنا معناه إن جسم الطلب</span> (Body)
      <span dir="rtl">مكتوب بصيغة</span> JSON

    - <span dir="rtl">مكان</span> Value <span dir="rtl">ممكن تحط أي قيمة
      لازمة زي</span> application/xml <span dir="rtl">لو</span> XML

5.  **-H "x-api-key: reqres-free-v1"**

    - <span dir="rtl">مثال على هيدر تاني</span>.

    - <span dir="rtl">هنا اسمه</span> x-api-key<span dir="rtl">،
      وقيمته</span> reqres-free-v1

    - <span dir="rtl">أنت تغيّر الجزء ده لو عندك</span> API Key
      <span dir="rtl">مختلف</span>.

6.  **-d
    "{\\email\\:\\your_email@example.com\\,\\password\\:\\your_password\\}"**

    - -d <span dir="rtl">معناها</span>: <span dir="rtl">بيانات الجسم
      اللي هيتبعت في الطلب.</span>

    - <span dir="rtl">لازم يكون مكتوب بصيغة</span> JSON
      <span dir="rtl">لو الـ</span> API <span dir="rtl">بيطلب
      كده.</span>

    - <span dir="rtl">في المثال</span>:

      - email: <span dir="rtl">هنا تكتب إيميلك</span>.

      - password: <span dir="rtl">هنا تكتب الباسورد</span>.

    - <span dir="rtl">لو الطلب ما يحتاجش</span> Body
      <span dir="rtl">مثل</span> GET <span dir="rtl">لا تكتب</span> -d

**<span dir="rtl">الخلاصة العملية</span>:**

- **-X** <span dir="rtl">هو نوع العملية</span> .(GET/POST/PUT/DELETE)
  <span dir="rtl"></span>

- **-H** <span dir="rtl">هو بيانات</span> Header <span dir="rtl">دايما
  اسم:قيمة</span>Name: Value <span dir="rtl">مثل</span> Content-Type
  <span dir="rtl">أو</span> .Authorization <span dir="rtl"></span>

- **-d** <span dir="rtl">هو بيانات</span> Body <span dir="rtl">تبعتها في
  شكل</span> .JSON

<span id="معالجه8" class="anchor"></span>**<span dir="rtl">8. معالجة
الأخطاء</span> (Error Handling)**

<span id="معال81" class="anchor"></span>**<span dir="rtl">8.1 مبادئ
عامة</span>**

- <span dir="rtl">تُرجِع الواجهة رموز حالة</span> (HTTP Status Codes)
  <span dir="rtl">قياسية توضّح نتيجة الطلب</span>.

- <span dir="rtl">تُعرَض تفاصيل الخطأ –عند توفّرها– في الاستجابة</span>
  (Response) <span dir="rtl">بصيغة</span> JSON <span dir="rtl">ليسهل
  قراءتها ومعالجتها برمجيًا</span>.

- <span dir="rtl">يجب دائمًا قراءة الرمز والنص المصاحب له لتحديد الإجراء
  المناسب (تصحيح الطلب، إعادة المحاولة، المصادقة… إلخ).</span>

<span id="معا82" class="anchor"></span>**<span dir="rtl">8.2 رموز الحالة
الشائعة</span>**

- 200 OK <span dir="rtl">: نجاح الطلب</span> (GET / PUT / PATCH)

- 201 Created<span dir="rtl">: تم إنشاء مورد جديد</span> (POST)
  <span dir="rtl"></span>

- 204 No Content<span dir="rtl">: نجاح بدون جسم استجابة</span> (DELETE)

- 400 Bad Request <span dir="rtl">: جسم أو صيغة طلب غير صحيحة</span>.

- 401 Unauthorized <span dir="rtl">: نقص المصادقة أو</span> Token
  <span dir="rtl">غير صالح</span>.

- 404 Not Found <span dir="rtl">: المورد غير موجود مثل</span> (GET
  /api/users/23) <span dir="rtl"></span>

- 429 Too Many Requests <span dir="rtl">: تجاوز حدّ المعدّل</span> (Rate
  Limit) – <span dir="rtl">إن وُجد</span>.

- 500 Internal Server Error<span dir="rtl">: خطأ عام في الخادم</span>.

<span id="معا83" class="anchor"></span>**<span dir="rtl">8.3 مسار تشخيص
سريع</span> (Troubleshooting)**

- <span dir="rtl">تحقّق من</span> Method <span dir="rtl">و</span>Endpoint
  <span dir="rtl">ومن الأخطاء الشائعة: كتابة</span> GET
  <span dir="rtl">في شريط العنوان بدل اختياره من القائمة.</span>

- <span dir="rtl">راجع</span> Headers <span dir="rtl">المطلوبة
  (مثل</span> Content-Type: application/json <span dir="rtl">و</span>
  Authorization: Bearer \<token\> <span dir="rtl">عند الحاجة)</span>

- <span dir="rtl">تأكّد من أن</span> Body <span dir="rtl">مكتوب
  بصيغة</span> JSON <span dir="rtl">صحيحة، و وجود الحقول الإلزامية (مثل
  البريد الإلكتروني/كلمة المرور في تسجيل الدخول</span>(

- <span dir="rtl">جرّب بمعرّفات صحيحة: بعض المعرّفات في</span> Reqres.in
  <span dir="rtl">ثابتة (مثل المستخدم 2)، بينما المعرّفات المُنشأة تجريبيًا
  قد لا تبقى محفوظة</span>.

- <span dir="rtl">راقب أولًا</span> Status Code <span dir="rtl">ثم نصّ
  الخطأ لتحديد الإجراء المناسب (إعادة الإرسال، تعديل المدخلات،
  إضافة</span> (Token

<span id="افض84" class="anchor"></span>**<span dir="rtl">8.4</span>
<span dir="rtl">أفضل ممارسات التعامل مع الأخطاء في العميل</span>
(Client)**

- <span dir="rtl">أظهر رسالة واضحة للمستخدم النهائي مشتقّة من</span>
  Status Code<span dir="rtl">.</span>

- <span dir="rtl">لا تفترض نجاح الطلب؛ افحص الرمز دائمًا قبل استخدام
  البيانات</span>.

- <span dir="rtl">أعد المحاولة تلقائيًا فقط في الحالات المناسبة (مثل
  مشاكل الشبكة، وليس عند</span> 400 Bad Request<span dir="rtl">)</span>

- <span dir="rtl">سجّل تفاصيل الخطأ</span> (Logging)
  <span dir="rtl">لأغراض التشخيص والمتابعة</span>.

<span id="تص9" class="anchor"></span>**<span dir="rtl">9.</span>
<span dir="rtl">التصفّح</span> (Pagination)**

<span dir="rtl">الهدف**:** تنظيم النتائج على صفحات متتالية لتقليل حجم
الاستجابة وتسهيل العرض والتنقّل</span>.

<span dir="rtl">طريقة الاستخدام (قائمة المستخدمين مثالًا)</span>

- (Method): GET

- (Endpoint): /api/users?page=2

- (Query Parameters):

  - page <span dir="rtl">لتحديد الصفحة المطلوبة</span>.

**<span dir="rtl">الاستجابة المتوقّعة</span> 200 :(OK)**

{

"page": 2,

"per_page": 6,

"total": 12,

"total_pages": 2,

"data": \[ /\* <span dir="rtl">عناصر الصفحة</span> \*/ \]

}

**<span dir="rtl">ملاحظات مهمة</span>**

- <span dir="rtl">يمكن الانتقال بين الصفحات بتغيير قيمة</span>page
  <span dir="rtl">مثل</span> ?page=1, ?page=2

- <span dir="rtl">عدد العناصر في الصفحة</span> (per_page)
  <span dir="rtl">ثابت في</span>Reqres.in <span dir="rtl">لأغراض العرض،
  لكنه قد يختلف في واجهات حقيقية</span>.

- <span dir="rtl">في نهاية الصفحات، قد تعود الاستجابة بحقل</span>data
  <span dir="rtl">فارغ دون أن يكون ذلك خطأ</span>.

<span id="ملاح10" class="anchor"></span>**<span dir="rtl">10.
الملاحق</span>**

<span id="مصطلح101" class="anchor"></span>**<span dir="rtl">10.1 مصطلحات
موحّدة</span>**

- :Token <span dir="rtl">رمز أمني يُستخدم لتفويض الطلبات</span>.

- HTTP Methods: GET, POST, PUT, PATCH, DELETE.

- HTTP Status Codes: 200, 201, 204, 400, 401, 404, 429, 500.

- Requests / Responses <span dir="rtl">طلبات / استجابات</span>.

- JSON (JavaScript Object Notation) <span dir="rtl">صيغة لتبادل البيانات
  بين العميل والخادم</span>.

<span id="روابط102" class="anchor"></span>**<span dir="rtl">10.2 روابط
مفيدة</span>**

- **<span dir="rtl">الموقع الرسمي:</span> <https://reqres.in>**

- **<span dir="rtl">تحميل</span>:Postman <span dir="rtl"></span>
  <https://www.postman.com/downloads/>**

- **<span dir="rtl">شرح فلسفة</span> RESTful API
  <span dir="rtl">بالعربية من حسوب:</span> [Hsoub in
  Arabic](https://academy.hsoub.com/programming/general/شرح-فلسفة-restful-تعلم-كيف-تبني-واجهات-rest-البرمجية-r635/)**

- **<span dir="rtl">تعلم اساسيات</span> :RESTful API
  <span dir="rtl"></span>[https://restfulapi.net<span dir="rtl">/</span>](https://restfulapi.net/)**
