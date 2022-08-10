---
title: Date.prototype.toLocaleString()
slug: Web/JavaScript/Reference/Global_Objects/Date/toLocaleString
translation_of: Web/JavaScript/Reference/Global_Objects/Date/toLocaleString
---
{{JSRef("Global_Objects", "Date")}}

**`toLocaleString()`** 方法返回该日期对象的字符串，该字符串格式因不同语言而不同。新增的参数 `locales` 和 `options` 使程序能够指定使用哪种语言格式化规则，允许定制该方法的表现（behavior）。在旧版本浏览器中， `locales` 和 `options` 参数被忽略，使用的语言环境和返回的字符串格式是各自独立实现的。

{{EmbedInteractiveExample("pages/js/date-tolocalestring.html")}}

## 语法

```plain
dateObj.toLocaleString([locales [, options]])
```

### 参数

查看[浏览器兼容性](#Browser_Compatibility)小节，看下哪些浏览器支持 `locales` 和 `options` 参数，还可以参看[例子：检测 `locales` 和 `options` 参数支持情况](#Example:_Checking_for_support_for_locales_and_options_arguments)。

{{page('zh-CN/docs/JavaScript/Reference/Global_Objects/DateTimeFormat','Parameters')}}

每个日期时间组件的默认值都是 undefined，但是如果 `weekday`, `year`, `month`, `day`, `hour`, `minute`, `second` 属性都是 `undefined`, 那么 `year`, `month`, `day`, `hour`, ` minute 和 ``second` 的值都被认为是 "numeric".

### 返回值

根据当地语言规定返回代表着时间的字符串。

## 例子

### 例子：使用 `toLocaleString`

没有指定语言环境（locale）时，返回一个使用默认语言环境和格式设置（options）的格式化字符串。

```js
var date = new Date(Date.UTC(2012, 11, 12, 3, 0, 0));

// toLocaleString 不包含参数的返回值取决于实现，
// 默认的区域 (locale),和默认的时区 (time zone)
date.toLocaleString();
// → 如果是在 en-US 区域和 America/Los_Angeles 时区运行返回值为"12/11/2012, 7:00:00 PM"
```

### 例子：检测 `locales` 和 `options` 参数支持情况

`locales` 和 `options` 参数不是所有的浏览器都支持。为了检测一种实现环境（implementation）是否支持它们，可以使用不合法的语言标签，如果实现环境支持该参数，则会抛出一个 `RangeError` 异常，反之会忽略参数。

```js
function toLocaleStringSupportsLocales() {
    try {
        new Date().toLocaleString("i");
    } catch (e) {
        return e​.name === "RangeError";
    }
    return false;
}
```

### 例子：使用 `locales` 参数

下例展示了本地化日期格式的一些变化。为了在应用的用户界面得到某种语言的日期和时间格式，必须确保使用 `locales` 参数指定了该语言（可能还需要设置某些回退语言）。

```js
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

//假定本地时区是 America/Los_Angeles(美国时区)
//en-US(美利坚英语) 使用 month-day-year 的顺序展示年月日
alert(date.toLocaleString("en-US"));
// → "12/19/2012, 7:00:00 PM"

// en-GB(不列颠英语) 使用 day-month-year 顺序展示年月日
alert(date.toLocaleString("en-GB"));
// → "20/12/2012 03:00:00"

// 韩语使用 year-month-day 顺序展示年月日
alert(date.toLocaleString("ko-KR"));
// → "2012. 12. 20. 오후 12:00:00"

// 大多数阿拉伯语国家的阿拉伯语使用阿拉伯数字
alert(date.toLocaleString("ar-EG"));
// → "٢٠‏/١٢‏/٢٠١٢ ٥:٠٠:٠٠ ص"

//在日本，应用可能想要使用日本日历，
//2012 是平成 24 年（平成是是日本天皇明仁的年号，由 1989 年 1 月 8 日起开始计算直至现在）
alert(date.toLocaleString("ja-JP-u-ca-japanese"));
// → "24/12/20 12:00:00"

//当请求一个语言可能不支持，如巴厘 (ban)，若有备用的语言印尼语 (id)，
//那么将使用印尼语 (id)
alert(date.toLocaleString(["ban", "id"]));
// → "20/12/2012 11.00.00"
```

### 例子：使用 `options` 参数

可以使用 `options `参数来自定义 `toLocaleString` 方法返回的字符串。

```js
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

//请求参数 (options) 中包含参数星期 (weekday)，并且该参数的值为长类型 (long)
var options = {weekday: "long", year: "numeric", month: "long", day: "numeric"};
alert(date.toLocaleString("de-DE", options));
// → "Donnerstag, 20. Dezember 2012"

//一个应用使用 世界标准时间 (UTC),并且 UTC 使用短名字 (short) 展示
options.timeZone = "UTC";
options.timeZoneName = "short";//若不写这一行那么仍然显示的是世界标准时间；但是 GMT 三个字母不会显示
alert(date.toLocaleString("en-US", options));
// → "Thursday, December 20, 2012, GMT"

// 使用 24 小时制
alert(date.toLocaleString("en-US", {hour12: false}));
// → "12/19/2012, 19:00:00"
```

## 性能

当格式化大量日期时，最好创建一个 [`Intl.DateTimeFormat`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/DateTimeFormat) 对象，然后使用该对象 [`format`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/DateTimeFormat/format) 属性提供的方法。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 相关链接

- {{jsxref("Global_Objects/DateTimeFormat", "DateTimeFormat")}}
- {{jsxref("Date.prototype.toLocaleDateString()")}}
- {{jsxref("Date.prototype.toLocaleTimeString()")}}