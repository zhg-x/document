# ts-utils 文档

## 介绍

[`@zhg-x/ts-utils`](https://www.npmjs.com/package/@zhg-x/ts-utils)包主要提供一些经常用的 ts 工具方法。

## 安装

通过npm：

```markdown
npm i @zhg-x/ts-utils
```



## 使用

可以直接通过方法名称调用对应方法，也可以通过类名`.`方法名称调用对应的方法。

示例

```
add(); // 1.直接通过方法名称调用
NumberUtils.add(); // 2.通过类名.方法名称调用
```

## Bugs

使用过程中遇到问题可发送邮件至zhangx_study@126.com

---

## ts-utils 方法



### 方法说明

方法调用说明：

1. 直接通过方法名称调用。（所有方法都支持该种方式）
2. 通过类名`.`方法名调用。（非所有方法都支持该种使用方式）

---

### 仅支持通过方法名调用的方法

#### getVarType()

```
getVarType(value: any): string
```

获取变量类型

**实现如下**

```js
Object.prototype.toString.call(value).slice(8, -1).toLowerCase()
```

---

#### isNull()

```
isNull(value: any): boolean
```

检查`value`值是否为`null`

---

#### isUndefined()

```
isUndefined(value: any): boolean
```

检查`value`值是否为`undefined`

---

#### isNumber()

```
isNumber(value: any): boolean
```

检查`value`的类型是否为`number`或者`Number`对象

---

#### isString()

```
isString(value: any): boolean
```

检查`value`的类型是否为`string`或者`String`对象

---

#### isBoolean()

```
isBoolean(value: any): boolean
```

检查`value`的类型是否为`boolean`或者`Boolean`对象

---

#### isSymbol()

```
isSymbol(value: any): boolean
```

检查`value`是否为`symbol`类型

---

#### isArray()

```
isArray(value: any): boolean
```

检查`value`类型是否为`Array`对象

---

#### isDate()

```
isDate(value: any): boolean
```

检查`value`值是否为 `Date` 类型

---

#### isMap()

```
isMap(value: any): boolean
```

检查 `value` 值是否为 `Map` 类型

---


#### isSet()

```
isSet(value: any): boolean
```

检查 `value` 值是否为 `Set` 类型

---

#### isFunction()

```
isFunction(value: any): boolean
```

检查`value`是否为`Function`

---

#### isRegExp()

```
isRegExp(value: any): boolean
```

检查 `value` 值是否为 `RegExp` 类型

---

#### isEmpty()

```
isEmpty(value: ValueType): boolean
```

判断 `value` 是否为空(`null`、`空字符串`、`空对象`、`空数组`、`空map`、`空Set`)

示例如下：

```markdown
isEmpty({})                      // true
isEmpty({id: '1'})               // false
isEmpty([])                      // true
isEmpty([1, 2, 3])               // false
isEmpty(new Set())               // true
isEmpty(new Set([]))             // true
isEmpty(new Set([10, 11, 12]))   // false
```

---

> 以下的方法支持两种方式调用。

### ArrayUtils

数组相关方法

#### arrayCheck()

```
arrayCheck(arr: any): Array<any>
```

校验参数是否为数组，如果是，则原样返回，否则返回空数组。





---

### DateUtils

日期相关方法

#### getDateOfInterval()

```
getDateOfInterval(interval: number, baseDate?: Date): Date
```

获取基础日期的间隔日期

间隔天数，正数则返回基础日期之后的日期，负数则返回基础日期之前的日期

---

#### getDatesFromDateRange()

```
getDatesFromDateRange(startDate: Date, endDate: Date): Date[]
```

获取时间范围内的日期，包含开始日期和结束日期

---

#### dateFormat()

```
dateFormat(date: Date, fmt?: string): string
```

日期格式化，默认格式：`YYYY-MM-dd`

**格式说明**

- y或者Y：年份，一般用yy表示两位年份，yyyy表示四位年份
- M：一般用MM表示月份 (0 ~ 11)
- d：一般用 dd 表示月份中的天数(1 ~ 31)
- H或者h：一般用HH或者hh表示一天中的小时数 (0 ~ 23)
- m：用mm表示分钟数 (0 ~ 59)
- s: 用ss表示秒数 (0 ~ 59)

**示例如下**

```
const date = new Date();
date.setFullYear(2022, 1, 5);
dateFormat(date)                             // 返回 "2022-02-05"
dateFormat(date, 'YYYY-MM-dd hh:mm:ss')      // 返回 "2022-02-05 16:44:11"
```



---

### NumberUtils

数值相关的工具方法

#### numberCheck()

```
numberCheck(arg: any, transFlag?: boolean): number
```

检查参数是否为数字或数字字符串，返回`number`类型的值。`transFlag`默认值为`false`。

1. 如果 `transFlag` 值为 `true` 且参数值转换为`Number`类型后是 `NaN` ，则将参数值转换为数字 `0` ，否则不做转换；
2. 判断上一步处理后的参数值是否为正数、负数、小数，如果是则将参数返回，否则抛出 `TypeError`。

---

#### add()

```
add(arg1: any, arg2: any): number
```

两个数字相加

---

#### calcAdd()

```
calcAdd(args: any[]): number
```

多参数 加法运算

---

#### calcSub()

```
calcSub(arg1: any, arg2: any): number
```

两个数字相减

---

#### calcMul()

```
calcMul(arg1: any, arg2: any): number
```

两数求积

---

#### calcDiv()

```
calcDiv(arg1: any, arg2: any): number
```

两数求商



---

### ObjectUtils

对象相关的工具方法

#### getTag()

```
getTag(value: any): string
```

获取变量类型，返回值为string类型(全部小写字母)

---

#### isObject()

```
isObject(value: any): boolean
```

检查value的类型是否为Object对象(Object、Array、...)

---

#### isObj()

```
isObj(value: any): boolean
```

检查value是否为`object`对象

---

#### cloneDeep()

```
cloneDeep(value: any): any
```

深拷贝对象自身的属性

1. 支持深拷贝的数据类型有number、string、boolean、null、undefined、Number、String、Boolean、Map、Set、Object、Array、RegExp、Date。
2. Int8Array、Uint8Array、Int16Array等对象数据只会进行简单的复制，不会进行深拷贝。

---

### StringUtils

字符串相关的工具方法

#### convertToStr()

```
convertToStr(value: any): string
```

将变量转换成对应的字符串形式

只支持 `number`、`string`、`boolean`、`null`、`undefined`、`Date`、`object`类型的转换。

示例

```
convertToStr(123);						// 返回'123'
convertToStr(new Number(456));			// 返回'456'
convertToStr('');						// 返回''
convertToStr(true);						// 返回'true'
convertToStr(null);						// 返回"null"
convertToStr(undefined);				// 返回'undefined'
convertToStr({name: 'test'});			// 返回'{"name":"test"}'
convertToStr([]);						// 返回[]
```

---

#### strIsEqual()

```
strIsEqual(arg1: any, arg2: any): boolean
```

比较两个参数转换成字符串后是否相等

该方法会将`number`、`null`、`undefined`、`object`类型的参数值转换为字符串类型后再进行比较。

示例

```
strIsEqual(123, '123');				// true
strIsEqual(null, undefined);		// false
```

---

#### strIsEmpty()

```
strIsEmpty(value: string): boolean
```

判断字符串是否为 `null` 或 `空字符串`

---

#### strIsBlank()

```
strIsBlank(value: string): boolean
```

检验字符串是否为 `null`、空串或者空格等



---
