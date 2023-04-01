---
draft: false
aliases: ["/fa/"]
---

# کامیت های قراردادی 1.0.0

## خلاصه

مشخصه های کامیت های قرار دادی‌ ، قراردادی سبک، اول پیام های کامیت هستند.

 قوانینی آسان برای مشخص کردن واضح تاریخچه کامیت ها تعیین میکند.
که باعث اسان تر شدن نوشتن ابزار های خودکار برای انها میشود و این قرارداد به [SemVer](http://semver.org) به علت شرح دادن قابلیت ها ، اصلاحات و تغییرات عمده در پیام های کامیت ها ، هماهنگ است.

پیام های کامیت ها باید طبق ساختار زیر باشند:


---

```

<نوع>[اختیاری محدوده]: <توضیحات>

[بدنه اختیاری]

[اختیاری پاورقی(ها)]
```
---

<br />
کامیت شامل عناصر ساختاری زیر برای ارتباط استفاده کننده از کتاب خانه شماست:   
 
1. **fix:**

 یک کامیت از *نوع* `اصلاح` که یک باگ را از کد شما برطرف میکند
  
 (با 
 
  [`MINOR`](http://semver.org/#summary)
  
   در نسخه‌بندی معنایی همخوانی دارد ).

2. **feat:** 
یک کامیت از  
*نوع* `قابلیت`  
که یک قابلیت جدید را که به کد شما اضافه شده را نشان میدهد
 (با 
 
  [`PATCH`](http://semver.org/#summary)
  
   در نسخه‌بندی معنایی همخوانی دارد ).

**BREAKING CHANGE:** کامیتی که پاورقی دارد 

 `تغییر عمده:`
 
 , یا  `!` اضافه شده 
 بعد از نوع/محدوده که یک تغییر عمده در ‌API را نشان میدهد
  (با 
 
  [`MAJOR`](http://semver.org/#summary)
  
   در نسخه‌بندی معنایی همخوانی دارد ).
   
   تغییر عمده میتواند بخشی از هر *نوع* کامیتی باشد.
   

نوع ها غیر از

 `fix:` و `feat:`
 
 نیز مجاز هستند برای مثال:
 
 [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional) (based on the [Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines))
 
 recommends build:, chore:, ci:, docs:, style:, refactor:, perf:, test:,
 
 و بقیه .

*پاورقی*
غیر از  
`تغییرات عمده : <توضیحات>`

ممکن است ایجاد شود و از قرار داد شبیه به 

[git trailer format](https://git-scm.com/docs/git-interpret-trailers) 

تبعیت کند


نوع های اضافی برای مشخصه های کامیت های قراردادی اجباری نیستند و هیج تاثیر ضمنی در نسخه‌بندی معنایی ندارند (غیر از انکه شامل تغییرات عمده باشند).
<br /><br />
ممکن است یک نوع کامیت در محدوده برای ارایه اطلاعات متنی بیشتر اورده شود که شامل پرانتز است مثل 

`feat(parser): add ability to parse arrays`




## نمونه ها 

### پیام کامیت با توضیحات و پاورقی تغییرات عمده

```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

### پیام کامیت با علامت `!` برای جلب توجه و نشان دادن تغییرات عمده
```
feat!: send an email to the customer when a product is shipped
```

### پیام کامیت با محدوده و علامت `!` برای جلب توجه و نشان دادن تغییرات عمده 

```
feat(api)!: send an email to the customer when a product is shipped
```

### پیام کامیت همراه `!` و پاورقی تغییرات عمده 

```
chore!: drop support for Node 6

BREAKING CHANGE: use JavaScript features not available in Node 6.
```

### پیام کامیت بدون بنده

```
docs: correct spelling of CHANGELOG
```

### پیام کامیت با محدوده
```
feat(lang): add Polish language
```

### پیام کامیت با چند پاراگراف بنده و چند پاورقی

```
fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Reviewed-by: Z
Refs: #123
```

## مشخصه ها

کلید واژه های

 “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, و “OPTIONAL” 
 
 در این مقاله به شرح در 
 
 [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt)
 
  تفصیر میشوند 


1. Commits MUST be prefixed with a type, which consists of a noun, `feat`, `fix`, etc., followed
  by the OPTIONAL scope, OPTIONAL `!`, and REQUIRED terminal colon and space.
1. The type `feat` MUST be used when a commit adds a new feature to your application or library.
1. The type `fix` MUST be used when a commit represents a bug fix for your application.
1. A scope MAY be provided after a type. A scope MUST consist of a noun describing a
  section of the codebase surrounded by parenthesis, e.g., `fix(parser):`
1. A description MUST immediately follow the colon and space after the type/scope prefix.
The description is a short summary of the code changes, e.g., _fix: array parsing issue when multiple spaces were contained in string_.
1. A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
1. A commit body is free-form and MAY consist of any number of newline separated paragraphs.
1. One or more footers MAY be provided one blank line after the body. Each footer MUST consist of
 a word token, followed by either a `:<space>` or `<space>#` separator, followed by a string value (this is inspired by the
  [git trailer convention](https://git-scm.com/docs/git-interpret-trailers)).
1. A footer's token MUST use `-` in place of whitespace characters, e.g., `Acked-by` (this helps differentiate
  the footer section from a multi-paragraph body). An exception is made for `BREAKING CHANGE`, which MAY also be used as a token.
1. A footer's value MAY contain spaces and newlines, and parsing MUST terminate when the next valid footer
  token/separator pair is observed.
1. Breaking changes MUST be indicated in the type/scope prefix of a commit, or as an entry in the
  footer.
1. If included as a footer, a breaking change MUST consist of the uppercase text BREAKING CHANGE, followed by a colon, space, and description, e.g.,
_BREAKING CHANGE: environment variables now take precedence over config files_.
1. If included in the type/scope prefix, breaking changes MUST be indicated by a
  `!` immediately before the `:`. If `!` is used, `BREAKING CHANGE:` MAY be omitted from the footer section,
  and the commit description SHALL be used to describe the breaking change.
1. Types other than `feat` and `fix` MAY be used in your commit messages, e.g., _docs: update ref docs._
1. The units of information that make up Conventional Commits MUST NOT be treated as case sensitive by implementors, with the exception of BREAKING CHANGE which MUST be uppercase.
1. BREAKING-CHANGE MUST be synonymous with BREAKING CHANGE, when used as a token in a footer.

## Why Use Conventional Commits

* Automatically generating CHANGELOGs.
* Automatically determining a semantic version bump (based on the types of commits landed).
* Communicating the nature of changes to teammates, the public, and other stakeholders.
* Triggering build and publish processes.
* Making it easier for people to contribute to your projects, by allowing them to explore
  a more structured commit history.

## پرسشگان

### چگونه باید با پیام کامیت ها در ابتدای فاز توسعه کنار بیایم؟

ما توصیه میکنیم اگر قبلا محصول را عرضه کرده اید ادامه دهید . به طور نمونه هر کسی حتی اگر او همکار شما در توسعه نرم افزار باشد که از نرم افزار استفاده میکند خواهد دانست که چه چیزی اصلاح شده و چه چیزی خراب شده است و غیره .




### آیا نوع تایتل کامیت باید بزرگ باشد یا کوچک ؟
هر مدلی ممکن است استفاده شود ولی بهتر است که متسمر باشد.


### اگر کامیت شامل بیش از یک نوع کامیت میشد چه کار کنم ؟
تا جای ممکن به عقب برگردید و چند کامیت انجام دهید. بخشی از مزایای کامیت قراردادی امکان هدایت ما به کامیت ها و پول رکوئست های ساختارمند تر است.



### ایا این کار باعث دلسرد شدن از توسعه سریع نمیشود؟
این کار باعث دلسرد شدن از پیشرفت بدون ساختار میشود.
و کمک میکند به شما تا بتوانید به صورت بلند مدت در میان چند پروژه با مشارکت کنندگان زیاد سریع پیشرفت کنید. 


### ایا ممکن است کامیت های قرار دادی توسعه دهندگان را به سمت محدودیت نوع کامیت هدایت کند زیرا آنها دغدغه این را دارند که چه نوعی تغییر ایجاد میکنند؟ 
کامیت های قراردادی مارا بیشتر به نوع کامیت های مشخص تشویق میکند مثل اصلاح . غیر از آن انعطاف پذیری کامیت های قراردادی به تیم ما اجازه میدهد تا با نوع کامیت های خود کار کنند و انها را در طول زمان تغییر دهند.


###  کامیت های قرار دادی با نسخه‌بندی معنایی چگونه ارتباط دارند؟ 


`fix`
 نوعی است که به 
 `PATCH`
  ترجمه میشود 
  . `feat`
   نوعی است که بهتر از به 
   `MINOR` ترجمه شود .
    کامیت هایی با 
     `تغییرات عمده`
     بدون توجه به نوع تغییر به  
      `MAJOR` 
      معادل میشوند.

### چگونه باید ورژن نسخه مشخصه های کامیت های قرار دادی مثل  `@jameswomack/conventional-commit-spec` را انجام دهم
ما توصیه میکنیم از نسخه‌بندی معنایی برای ریلیز نسخه های خود استفاده کنید.



### باید چه کار کنم اگر از نوع اشتباهی از کامیت استفاده کردم؟


#### همگامی که شما از نوعی که مشخص است ولی صحیح نیست مثل 
`fix`
 به جای
  `feat`

قبل از مرج یا ریلیز کردن اشتباه  ُ توصیه میکنیم که از 
`git rebase -i`
برای ادیت تاریخچه کامیت ها استفاده کنید. بعد از ریلیز پاکسازی با توجه به رویکرد شما که چه فرایند یا ابزاری استفاده میکنید متفاوت خواهد بود.

#### زمانی که شما غلط املایی دارید مثل `feet` 
به جای 
`feat`

در بدترین حالت ُ اخر دنیا نمیشود اگر که یک کامیت طبق مشخصه کامیت های قرار دادی نباشد بلکه تنها معنی آن از زیر دست ابزاری که بر اساس مشخصه کامیت های قرار دادی است در میرود 


### ایا همه مشارکت کنندگان من باید از مشخصه کامیت های قراردادی استفاده کنند؟
نه اگر ورک فلو گیت شما بر اساس
 squash
 باشد نگه دارندگان مخزن های گیت میتوانند انها را اصلاح کنند.
 یک ورک فلو معمولی برای این کار هنگامی است که به صورت خودکار کامیت های پول رکوئست 
  squash
میشوند و نگه دارندگان مخزن گیت میتوانند با پیام مناسب آن را با مخزن اصلی ادغام کنند 


### کامیت های قرار دادی چگونه برگشت کامیت ها را مدیریت میکنند

برگشت کد ممکن است پیچیده باشد: ایا چند کامیت را بر میگردانید؟ اگر یک قابلیت را بر میگردانید ریلیز بعدی باید یک اصلاح باشد؟
کامیت های قرار دادی به صورت صریح تلاش نمیکنند که یک رفتار بازگشتی را تبعیین ککند بلکه ان را به ابزار های نویسنده واگزار میکنیم تا با انعطاف _نوع_ و _پاورقی_ منطق بازگشت را مدیریت کنند.

یک توصیه آن است که از نوع `بازگشت` استفاده کنید و پاورقی آن هش کامیت رفرنس باشد: 


```
revert: let us never again speak of the noodle incident

Refs: 676104e, a215868
```

