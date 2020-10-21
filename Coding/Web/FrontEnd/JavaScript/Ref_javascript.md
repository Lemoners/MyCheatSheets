# JavaScript �ʼ�

## JavaScript ����

- ͨ�� JavaScript ������Էŵ� `<head> </head>` �У�

    ```javascript
    <html>
        <head>
            <script type="text/javascript">
                alert('Hello World');
            </script>
        </head>
        <body>
            ...
        </body>
    </html>
    ```

    > `type` Ĭ�����Լ�Ϊ��`JavaScript`, ���Կ��Բ�����ʾָ����

- �� JavaScript ����ŵ������� `.js` �ļ��У�

    ```javascript
    <html>
        <head>
            <script src="/static/js/abc.js"></script>
        </head>
        <body>
            ...
        </body>
    </html>
    ```

## JavaScript ����

### �Ƚ������

`==` �� �Զ�ת�����������ڱȽϣ�
`===` �� ����������Ͳ�һ�£����� `false`��

### �ַ���

ʹ�� \`xxxxxxx\` ��ʶ�����ַ�����

```javascript
console.log(`Hello
World
!`);
```

������ `{$variable}` �滻�ַ����еı�����

```javascript
var name = 'Bob';
var age = 20;
console.log(`Hello, ${name}, you are ${age} years old!`);
```

���ַ����Ĳ���������ı��������Ƿ���һ���µ��ַ�����

`str.toUpperCase()` - ת��Ϊ��д
`str.toLowerCase()` - ת��ΪСд
`str.indexOf('string')` - ��ȡָ���ַ������ֵ�λ��
`str.substring(startIndex, length)` - ��ȡ��ȡ���ַ���

### ����

ͨ���������и�ֵ����ֱ���޸���� Array��

```javascript
var arr = ['A', 'B', 'C'];
arr[1] = 100;
arr; //arr now is ['A', 100, 'C'];
```

`indexOf(value)` - ����ָ��ֵ��������
`slice(startIndex, length)` - ������ String �� `substring()`��
`push('value1', 'value2')` - ĩβ���ֵ��
`pop()` - ɾ������һ��ֵ��
`sort()` - ����
`reverse()` - ��ת���飻
`splice(startIndex, deleteNum, replaceValue1, replaceValue2)` - ��ָ����������ʼɾ������ֵ��Ȼ���ٴӸ�λ���������ֵ��
`concat(newArray)` - �������� Array;
`join(connectValue)` - ÿ��ֵ��ָ�����ַ������ӣ�����һ�����Ӻ���ַ���

### ����

JavaScript �����Ƕ�̬���ͣ�������ӻ�ɾ������;

```javascript
var person = {
    name: 'David',
    age: '20',
};

person.gender = 'male'; // ���� gender ����
delete person.age; // ɾ�� age ����
```

ʹ�� `in`/`hasOwnProperty()` ����Ƿ�ӵ��ĳ���ԣ�

`in` - �����̳е�����, ���磺 `toString` �� `object` ��������ԣ����Ҳ�� `true`;
`hasOwnProperty()` - ����������ӵ�е�����

```javascript
'age' in person; //true
'birth' in person; //false
person.hasOwnProperty('age'); //true
person.hasOwnProperty('toString'); //true
```

### ѭ��

- `for(i=index; i<length; i++)`;
- `for (var key in object)`;
- `while(condition)`;
- `do {...} while(condition)`;

### Map & Set

`Map` - ��ֵ�Լ��ϣ�

```javascript
var m = new Map([['David', 100], ['Bob', 10]]);
m.get('David'); //100
m.set('Adam', 99); //����µ� key-value
m.has('Bob'); //true
m.delete('Adam') //ɾ�� key-'Adam'
```

`Set` - Key �ļ��ϣ�Key �����ظ���û��������

```javascript
var s = new Set([1, 2, 3, 3, '3']);
s.add(4); // Set {1, 2, 3, '3', 4}
s.delete(3); // Set {1, 2, '3', 4}
```

### iterable

�µ� `iterable` ���ͣ�`Array`��`Map` �� `Set` ������ `iterable` ���͡�

`for ... of` ѭ�� ��� `for ... in` ѭ������ʷ��������:

```javascript
var a = ['A', 'B', 'C'];
a.name = 'David';
for (var i in a) {
    console.log(i); // '0', '1', '2', 'name'
}
for (var i of a) {
    console.log(i); // 'A', 'B', 'C'
}

a.forEach(function (element, index, array) {
    // element: ָ��ǰԪ�ص�ֵ��
    // index��ָ��ǰ������
    // array��ָ�� Array ������
})
```

## ����

2 �ֶ��巽����

- `function abs(x) { ... }`
- `var abs = function(x) { ... };`

������

- `arguments` - ���ں����ڲ���ָ��������в���
- `...rest` - ָ�����δ��ʾָ���Ĳ��� `function foo(a, b, ...rest){ ... }`

### ������

JavaScript Ĭ����һ��ȫ�ֶ��� `window`���κ�ȫ�ֱ���������Ҳ��Ϊ����������󶨵� `window` �ϡ�

`var` - ����**�ֲ�**���������
`let` - ����**��**�����������

```javascript
function foo() {
    for (let i=0; i<100; i++) {
        //
    }
    i += 100; // SyntaxError;

    for (var i=0; i<100; i++) {
        //
    }
    i += 100; // ��Ȼ�������ñ���i
}
```

`const` - ����

### �⹹��ֵ

����ͬʱ��ֵ�������������Ƕ�׵����飺

`let [x, [y, z]] = ['hello', ['hi', 'welcome']];`

����ֵ��

```javascript
var person = {
    name: 'David',
    age: 20,
    gender: 'male',
    passport: 'G-12345678',
    address: {
        city: 'Beijing',
        zipcode: '100001'
    }
};
var {name, address: {city, zip}} = person;
name; // 'David'
city; // 'Beijing'
zip; // undefined, ��Ϊ��������zipcode������zip
// ע��: address���Ǳ���������Ϊ����city��zip���Ƕ�׵�address���������:
address; // Uncaught ReferenceError: address is not defined
```

## �߽׺���

���Խ�������Ϊ�������룺

```javascript
function add(x, y, abs) {
    return abs(x) + abs(y);
}
```

### map ����

`arr.map(function (x) { return abs(x); } )` - ���ζ������ÿ��Ԫ�ص���ָ���ĺ�����

```javascript
function pow(x) {
    return x * x;
}
var arr = [1, 2, 3, 4, 5];
arr.map(pow); // [2, 4, 9, 16, 25]

arr.map(function (x) { return x * x; }); // [2, 4, 9, 16, 25]

arr.map(x => x * x); // [2, 4, 9, 16, 25]
```

### reduce ����

`arr.reduce(function (x, y) { return add(x, y); })` - �ֱ������Ľ��к������ã����������ۼƣ�

```javascript
var arr = [1, 2, 3, 4, 5];
arr.reduce( function (x, y) { return x + y; }); // 15

arr.reduce( (x,y) => x * y; ) // 15
```

### filter ����

`arr.filter(function (x) { return x>99 })` - ͨ������ֵ�����Ƿ�����Ԫ��

### sort ����

`arr.sort()` - Ĭ�������ַ��� ASCII ���������eg. 10 < 2��

`arr.sort(function(x,y) { if (x < y) return -1; else if (x > y) return 1; else return 0;})` - �޸������������԰������ִ�С��������

`sort` ����ֱ�ӶԵ�ǰ Array �����޸ġ�

### every ����

�ж� Array �е�ÿ��Ԫ���Ƿ���������

`let r = arr.every(funciton (s) { return s.length > 0;});` - �ж� Array ���Ƿ���ڿ�Ԫ��

### find\findIndex ����

���� Array �����������ĵ�һ��Ԫ��\����

`let s = arr.find(function (s) { return s.toLowerCase() === s });` - ���ص�һ��Сд��Ԫ�أ����δ�ҵ����� `undefinded`

### foreach ����

���ڱ��� Array, û�з���ֵ��Ҳ����ı�ԭ Array, �����ڱ���

`arr.forEach(console.log)`

## �հ�

��������Ϊ������ء�ʵ��һ����������ʾ����

```javascript
function counter (initial) {
    var x = initial || 0;
    return function() return x ++;
}

var c = conter(100);
c(); //100
c(); //101
```

## ��ͷ����

```javascript
(x, y) => x * y;
```

==> �ȼ��� ==>

```javascript
function (x, y) {
    return x * y;
}
```

## generator ������

��������һ�������ڿ��Է��ض�����

```javascript
function* name(max) {
    var index = 0;
    while(index < max) {
        yield index++;
    }
    return index;
}

for (var x of name()) {
    console.log(x);
}
```

## ��׼����

`number`, `string`, `boolean`, `function`, `underfined`, `object` - (`Array`, `null` ������ `object`��

### Date

`var date = new Date(2019, 6, 12);` - 2019/07/12

JavaScript �� Date �����·�ֵ�� 0 ��ʼ���μ� 0=1 �£�1=2 �£�2=3 �£�������11=12 �¡�

### RegExp

#### ������ʽ����

`\d` - ����
`\w` - ��ĸ������
`\s` - �ո�

`.` - �����ַ�
`*` - ������ַ�(���� 0 ��)
`+` - ����һ���ַ�
`?` - 0 �� 1 ���ַ�
`{n}` - n ���ַ�
`{n, m}` - n~m ���ַ�

`[]` - ��ʾ��Χ
`[0-9a-zA-Z]` - ���ּ���ĸ
`A|B` - A �� B
`^` - ��...��ͷ
`$` - ��...��β

`()` - ������

#### RegExp

`test()` ���������ַ����Ƿ����������ʽ

```javascript
var re = new RegExp('^\d{3}\-\d{3-8}$');
var re = /^\d{3}\-\d{3-8}$/;

re.test('010-12345'); // true
```

`exec()` ������ȡ������ʽ�ж������, ʧ�ܷ��� null

```javascript
var re = /^(\d{3})-(\d{3,8})$/;
re.exec('010-12345'); // ['010-12345', '010', '12345']
re.exec('010 12345'); // null
```

```javascript
var re = /^[0-9a-zA-Z\.]+@.+\.\w+$/; // ƥ������ v-tawe@microsoft.com

var re = /^\<(.+)\>\s+([0-9a-zA-Z\.]+@.+\.\w+)$/; // ƥ������ֵ����� <David Tang> v-tawe@microsoft.com
```

#### JSON

���л� - `JSON.parse('json')`
�����л� - `JSON.stringify(obj)`

## �������

���ִ�������ķ�ʽ��

ͨ���������Ͷ��󴴽���

```javascript
var Student = {
    name: 'Robot';
    height: 1.2;
    run: function() {
        return this.name + 'is running';
    }
}

function createStudent(name) {
    var s = Object.create(Student);
    s.name = name;
    return s;
}

var xiaoming = createStudent('xiaoming');
xiaoming.run(); //xiaoming is runing
```

ͨ�����캯��ʵ�֣�

```javascript
function Student(props) {
    this.name = props.name || 'Robot';
    this.height  = props.height || '1.2';
}

Student.prototype.run = function() {
    return this.name + 'is running';
}

function createStudent(props) {
    return new Student(props || {})
}
```

ͨ�� class ʵ�֣�

```javascript
class Student {
    constructor(name) {
        this.name = name;
    }

    run() {
        return this.name + 'is running';
    }
}
```

### ԭ�ͼ̳�

�����µĹ��캯���������ڲ����ü̳еĹ��캯���� `call()` ������`this`;

![inherits](./inherits.png)

ֻ�к������� `prototype` ����, `_proto_` �����ж����еģ�����������, ������ԭ�� `xxx.constructor`��

ͨ�����캯��ʵ�ּ̳У�

```javascript
function inherits(Child, Father) {
    var F = function(){};
    F.prototype = Father.prototype;
    Child.prototype = new F();
    Child.prototype.constructor = Child;
}

function Student(props) {
    this.name = props.name || 'unnamed';
    this.height = props.height || 1.2;
}

Student.prototype.run = function() {
    return this.name + 'is running';
}

function PrimaryStudent(props) {
    Student.call(this, props);
    this.grade = props.grade || 1;
}

inherits(PrimaryStudent, Student);

PrimaryStudent.prototype.getGrade = function() {
    return this.grade;
}
```

ͨ�� class ʵ�ּ̳У�

```javascript
class PrimaryStudent extends Student {
    constructor(props) {
        super(props);
        this.grade = props.grade || 1;
    }

    getGrade() {
        return this.grade;
    }
}
```

## �����

��Ҫ֧�� ES6

- ��������ڣ� `windows`�� `windows.innerWidth; windows.innerHeight`;
- �������Ϣ�� `navigator`: `navigator.appName; navigator.appVersion`...;
- ��Ļ��Ϣ�� `screen`: `screen.width; screen.height`...;
- ��ǰҳ�� URL ��Ϣ: `location`: `location.protocol; location.host`...;
- DOM ����: `document`: `document.title; document.cookie`...;
    - `document.getElementById();` - ���� ID ��ȡ DOM �ڵ�
    - `document.getElementsByTagName();` - ���� Tag ���ʻ�ȡ DOM �ڵ�
    - `document.cookie` - ��ȡ cookie ��Ϣ����������ʹ�� `httpOnly` ���Խ�ֹ JS ��ȡ Cookie;
- �������ʷ�� `history`: `history.back(); history.forward();` **��ʷ�������������ã���**

### DOM

```javascript

var d = document.getElementById('id');
document.getElementsByTagName('p');
document.getElementsByClassName('class');

document.querySelector('#id');
document.querySelectorAll('div.class > p');

d.children; // ��ȡ id �µ������ӽڵ�
d.firstElementChild; // ��ȡ id �µĵ�һ���ӽڵ�

// ���� DOM
d.innerHTML = 'ABC <span style="color:red">RED</span> XYZ'; // �������� HTML ��ǩ
d.innerText = 'ABC XYZ';

//// ���� CSS
d.style.color = '#ff0000';
d.style.fontSize = '20px';

// ���� DOM
var div1 = document.createElement('p');
div1.id = 'div1';
div1.innerText = 'DIV1';
d.appendChild(div1);

var ref = document.getElementById('ref');
d.insertBefore(div1, ref);

// ɾ�� DOM
var parent = d.parentElement;
// ɾ���ڵ�ʱ children �ڵ�ʵʱ�仯
parent.removeChild(parent.children[0]); // ɾ���ڵ� 0
parent.removeChild(parent.children[0]); // ɾ���ڵ� 1
```

### ��

û�� `name` ���Եı��ؼ������ύ��

���ؼ�

- `<input type='text'></input>`
- `<input type='password'></input>`
- `<input type='radio'></input>`
- `<input type='checkbox'></input>`
- `<input type='hidden'></input>`
- `<select></select></input>`

��ȡֵ

- `text, password, hidden, select` ʹ�� `value` ��ȡֵ
- `select` ʹ�� `checked` ��ȡֵ

### �ļ�

`<input type='file'></input>`

### AJAX

ֻ֧��ͬԴ���Է��ʣ�������Ҫʹ�� CORS ���ԡ�

1. ���� `XMLHttpRequest` ����
1. ���� `onreadystatechange` �ص�������
1. ͨ�� `readyState === 4` �ж������Ƿ���ɣ�
1. ���� `status === 2000` �ж��Ƿ�ɹ���Ӧ��
1. ���� `open()` ����, ����1�� `GET/POST`; ����2�� URL ��ַ�� ����3���Ƿ��첽��Ĭ�� true);
1. ���� `send()` ������������

```javascript
var request = new XMLHttpRequest(); // �½� AJAX ����

// ״̬�����仯ʱ���������ص�
request.onreadystatechange = function() {
    if (request.readyState === 4) { // �ɹ�
        // �ж���Ӧ���
        if (request.status === 200) {
            // �ɹ���responseText - ��Ӧ�ı�
            return success(request.responseText);
        }
        else {
            // ʧ��
            return fail(request.status);
        }
    }
}

// ��������
request.open('GET', '/api/categories');
request.send();
```

## Promise

```javascript
function ajax(method, url, data) {
    var request = new XMLHttpRequest();
    return new Promise(function (resolve, reject) {
        request.onreadystatechange = function() {
            if (request.readyState === 4) {
                if (request.status === 200) {
                    resolve(request.responseText);
                }
                else {
                    reject(request.status);
                }
            }
        };
    request.open(method, url);
    request.send(data);
    });
}

var p = ajax('GET', '/api/categories');
p.then(function(text) {
    log.innerText = text;
}).catch(function(status) {
    log.innerText ='ERROR' + status;
})
```

����ִ�У� `Promise.all()`
�ݴ�ִ�У� `Promise.race()`

```javascript
var p1 = new Promise(function(resolve, reject) {
    ...
})

var p2 = new Promise(function(resolve, reject) {
    ...
})

// p1, p2 ��ִ�гɹ���ִ�� then
Promise.all([p1, p2]).then(function(results) {
    console.log(results);
})

// p1, p2 ͬʱִ�У���ִ�гɹ��ķ��ؽ���� then����ִ�гɹ��Ľ����ʧ
Promise.race([p1, p2]).then(function(result) {
    console.log(result);
})
```

## JQuery

- �� ID ���ң� `$('#id')`
- �� class ���ң� `$('.class')`
- �� Tag ���ң� `$('tag')`
- �����Բ��ң� `$('[name=email]')`; `$('[type=password]')`
    - `$('[name^=icon])`: ���� name ������ icon ��ͷ�� DOM;
    - `$('[name$=with]')`: ���� name ������ with ��β�� DOM;
- ��ϲ��ң� `$('input[name=email]')`; `$('tr.red')`
- ����ѡ������ `$('p, div')`; `$('p.red, p.green')`; `$('input[name=email],[name=password]')`

### ѡ����

- �㼶ѡ���� �� �ո� ������ `$('ul li.class')`
- ��ѡ���� �� > ������ `$('ul > li.class')`

    �㼶ѡ���� �� ��ѡ�����������ڣ� ��ѡ��������ʱ���ӹ�ϵ�����ɿ�㼶ѡ��

- ������ �� : ������ `$('ul li:first-child')`;  `$('ul li:last-child')`; `$('ul li:nth-child(2)')`; `$('ul li:nth-child(even)')`

### �����

- `:input` - `<input>`, `<textarea>`, `<select>`, `<button>`
- `:file` - `input[type=file]`
- `:checkbox` - `input[type=checkbox]`
- `:radio` - `input[type=radio]`
- `:focus` - ��ȡ��굱ǰ�Ľ���ؼ� `input:focus`
- `:checked` - ��ѡ��ĵ�ѡ��ѡ��ؼ� `input[type=radio]:checked`
- `:enabled` - ������������Ŀؼ�
- `:disabled` - �ѱ����õĿؼ�
- `:visible` - �ɼ��Ŀؼ�
- `:hidden` - ���صĿؼ�
- ... ...

### ���� & ����

- `find()` - �������ӽڵ��н��в���
- `parent()` - �ӵ�ǰ�ڵ����ϲ���
- `next()` & `prev()` - ͬһ�㼶�ڵ�ǰ����в���

- `filter()` - ���˵������������Ľڵ�
- `map()` - ��һ�� jQuery ������������� DOM �ڵ�ת��Ϊ��������
- `first()` & `last()` & `slice(2, 4)` - ��ȡ jQuery ����

### ����

- `text()` & `html()` - ��ȡ���޸� text �� html
- `val()` - ��ȡ���޸� value ����
- `css()` - ��ȡ���޸� css
- `hide()` & `show()` - ���ػ���ʾԪ��; ���Ӳ�������ʵ�ֵ��뵭��Ч���� `hide('slow')` / `show('slow')`
- `attr()` & `removeAttr()` - �޸� DOM ����
- `prop()` - �� attr() ����

- `append()` & `prepend()` - ��� DOM �ڵ�
- `before()` & `after()` - �ڵ�ǰԪ��ǰ/����� DOM �ڵ�
- `remove()` - ɾ���ڵ�

### �¼�

���¼���

- `$('#id').on('click', function() { alert('Hello, World'); });`
- `$('#id').click(function() { alert('Hello, World'); });`

�¼����ͣ�

- `click` - ����
- `dblclick` - ˫��
- `mouseenter` - �������
- `mouseleave` - ����Ƴ�
- `mousemove` - ����� DOM ���ƶ�
- `hover` - `mouseenter` + `mouseleave`

- `keydown` - ���̰���
- `keyup` - �����ɿ�
- `keypress` - ��һ�μ�����

- `focus` - DOM ��ý���
- `blur` - DOM ʧȥ����
- `change` - DOM ���ݱ��
- `submit` - form �ύ
- `ready` - ҳ�����벢�� DOM ����ʼ���� �������� document ����

    `$(document).ready(function() {...});` 
    �򻯺�
    `$(function() {...});`

- `off('click', <functionName>)` ȡ���¼���

### ����Ч��

- `show('slow') / hide('slow') / toogle('slow')` - ���Ͻǻ�������
- `slideUp('slow') / SlideDown('slow') / slideToogle('slow')` - ��ֱ��������
- `fadeIn('slow') / fadeOut('slow') / fadeToggle('slow')` - ���뵭��
- `animate()` - �Զ���Ч��

    ```javascript
    $('#id').animate({
        opacity: 0.25,
        width: 0px;
        height: 0px;
    }, 1000, function() { console.log('Complete'); }).delay(1000).animate(...);
    ```

    ����ʹ�� `delay()` ʵ�ֶ�������ͣ��

### AJAX

- `$.ajax(async, method, contentType, data, headers, dataType)`
- `$.ajax(async, method, contentType, data, headers, dataType, jsonp:'callback', jsonpCallback:'callbackFunction', success: function(data){...})`

- `$.get(url)`
- `$.post(url, data)`

- `$.getJSON(url)`

### ��չ

1. ʹ�� `$.fn` �󶨺���
1. ʹ�� `return this` ʵ����ʽ����
1. �����Ĭ��ֵ������ `$.fn.<pluginName>.defaults` ��
1. �û��ڵ���ʱ�ɴ�������Ը���Ĭ��ֵ

```javascript
$.fn.<pluginName> = function(options) {
    var bgcolor = options && options.bgcolor || '#FFFFFF';
    this.css('background', bgcolor)
    return this;
}
```

`extend(target, obj1, obj2, ...)` �Ὣ��������ֵ�ϲ�����һ�� target ��, Խ������Ķ������ȼ�Խ�ߣ�

`extend({}, $.fn.<pluginName>.defaults, options)`

## �쳣����

ʹ�� `try {...} catch {...} finally {...}` ����

> ע�⣺�첽����ʱ���쳣�޷��ڵ��ô�����ͬ�������ڿؼ����¼������ڰ��¼��Ĵ��봦�޷������¼����������쳣��

## unerscore

�� jQuery ���ƣ��ṩһ�����Ƶ� API, �󶨵� `_` �����ϡ�

### Collections

#### map/filter

������ Array �� `map/filter` ����

- `_.map(object, function(value, key) {...});`
- `_.mapObject(object, function(value, key) {...});`
- `_.filter(object, function(value, key) {...});`

#### every/some

������Ԫ�ض����������`_.every()` ���� `true`, �����в���Ԫ����������� `_.some()` ���� `true`

- `_.every([1, 4, 7, -3, -9], (x) => x > 0); // false`
- `_.some([1, 4, 7, -3, -9], (x) => x > 0); // true`

#### max/min

����ʱ Object������Ե� key��ֻ�Ƚ� value

`_.max({ a: 1, b: 2, c: 3 }); // 3`

#### groupBy

`_.groupBy([1, 2, 3, 4, 5], (x) => { if(x<3) return 'small'; else return 'big' });`

���� [underscrore ����](https://underscorejs.org/)��