<h2 id="📌-3-1-상황에-따라-달라지는-this">📌 3-1 상황에 따라 달라지는 this</h2>
<p>this는 기본적으로 실행 컨텍스트가 생성될 때 결정된다 </p>
<blockquote>
<ul>
<li>this는 함수를 호출할 때 결정된다.</li>
</ul>
</blockquote>
<h3 id="📒-3-1-1-전역-공간에서의-this">📒 3-1-1 전역 공간에서의 this</h3>
<p>전역공간에서 this는 전역 객체를 가리킨다.
브라우저 환경 전역객체 : window / Node.js 환경 전역객체 : global</p>
<h4 id="전역변수와-전역객체">전역변수와 전역객체</h4>
<pre><code class="language-javascript">var a = 1;
console.log(a); // 1
console.log(window.a); // 1
console.log(this.a); // 1</code></pre>
<p>자바스크립트의 모든 변수는 실은 특정 객체의 프로퍼티로서 동작한다.
특정 객체 : 실행 컨텍스트의 LexicalEnvironment(L.E)</p>
<h4 id="전역변수와-전역객체-선언">전역변수와 전역객체 선언</h4>
<pre><code class="language-javascript">var a = 1;
window.b = 2;
console.log(a, window.a, this.a); // 1 1 1
console.log(b, window.b, this.b); // 2 2 2

window.a = 3;
console.log(a, window.a, this.a); // 3 3 3
console.log(b, window.b, this.b); // 4 4 4</code></pre>
<h4 id="전역변수와-전역객체-삭제">전역변수와 전역객체 삭제</h4>
<pre><code class="language-javascript">var a = 1;
delete window.a; // false
console.log(a, window.a, this.a); // 1 1 1

var b = 2;
delete b; // false
console.log(b, window.b, this.b); // 2 2 2

window.c = 3;
delete window.c; // ture
console.log(c, window.c, this.c); // Uncauht ReferenceError: c in not defined

window.d = 3;
delete window.d; // ture
console.log(d, window.d, this.d); // Uncauht ReferenceError: c in not defined</code></pre>
<p>전역 객체의 프로퍼티로 할당한 경우 → 삭제 O
전역변수로 선언한 경우 → 삭제 X
configurable(변경 및 삭제 가능성) 속성 false로 정의됨</p>
<p>: var로 선언한 전역변수와 전역객체의 프로퍼티는 호이스틍 여부 및 configurable여부에서 차이를 보인다.</p>
<h3 id="📒-3-1-2-메서드로서-호출할-때-그-메서드-내부에서의-this">📒 3-1-2 메서드로서 호출할 때 그 메서드 내부에서의 this</h3>
<h4 id="함수-vs-메서드">함수 vs 메서드</h4>
<h4 id="함수를-호출하는-방법">함수를 호출하는 방법</h4>
<ul>
<li>함수로서 호출하는 경우</li>
<li>메서드로서 호출하는 경우</li>
</ul>
<blockquote>
<p>✅ 구분하는 유일한 차이는 독립성 !!
함수 : 그 자체로 독립적인 기능을 수행
메서드 : 자신을 호출한 대상 객체에 관한 동작을 수행</p>
</blockquote>
<h4 id="함수로서-호출-메서드로서-호출">함수로서 호출, 메서드로서 호출</h4>
<pre><code class="language-javascript">var func = function (x) {
    console.log(this, x);
};
func(1); // window { ... } 1

var obj = {
    method: func
};
obj.method(2); // { method: f } 2
obj['method'](2); // { method: f } 2</code></pre>
<p>함수로서 호출 / 메서드로서 호출 구분방법!</p>
<ul>
<li>함수 앞에 점(.)이 있는지 여부로 구분 가능.</li>
</ul>
<h4 id="메서드-내부에서의-this">메서드 내부에서의 this</h4>
<p>this에는 호출한 주체에 대한 정보가 담김 ⇒ 호출 주체 : 함수명(프로퍼티명) 앞의 객체</p>
<h3 id="📒-3-1-3-함수로서-호출할-때-그-함수-내부에서의-this">📒 3-1-3 함수로서 호출할 때 그 함수 내부에서의 this</h3>
<h4 id="함수-내부에서의-this">함수 내부에서의 this</h4>
<p>함수 내부에서의 this. 함수를 함수로서 호출한 경우에는 호출 주체의 정보를 알 수 없기 때문에 this가 지정되지 않았기 때문에 this는 전역 객체를 가리킨다.</p>
<h4 id="메서드의-내부-함수에서의-this">메서드의 내부 함수에서의 this</h4>
<h4 id="내부-함수에서의-this">내부 함수에서의 this</h4>
<pre><code class="language-javascript">var obj = {
    outer: function() {
        console.log(this); // obj1
        var innerFunc = function (){
            console.log(this); // window
        }
        innerFunc(); // 함수로서 호출

        var obj2 = {
            innerMethod: innerFunc // obj2
        };
        obj2.innerMethod(); // 메서드로서 호출
    }
};
obj1.outer(); // 메서드로서 호출</code></pre>
<h4 id="메서드의-내부-함수에서의-this를-우회하는-방법">메서드의 내부 함수에서의 this를 우회하는 방법</h4>
<h4 id="내부-함수에서의-this를-우회하는-방법">내부 함수에서의 this를 우회하는 방법</h4>
<p>ES5까지는 자체적으로 내부함수에 this를 상속할 방법이 없지만 다행히 우회할 방법이 없지는 않다 
: 대표적인 방법은 변수를 활용하는 것</p>
<pre><code class="language-javascript">var obj = {
    outer: function() {
        console.log(this);  // {outer: f}
        var innerFunc1 = function (){
            console.log(this); // window
        }
    };
    innerFunc1();

    var self = this;
    var innerFunc2 = function() {
        console.log(self); // {outer: f}
    };
};
obj.outer();</code></pre>
<h4 id="this를-바인딩-하지-않는-함수">this를 바인딩 하지 않는 함수</h4>
<pre><code class="language-javascript">var obj = {
    outer: function() {
        console.log(this);  // {outer: f}
        var innerFunc = () =&gt; {
            console.log(this); // {outer: f}
        }
    };
    innerFunc();
};
obj.outer();</code></pre>
<p>this를 바인딩 하지 않는 화살표 함수(arrow function) 도입했다.
화살표 함수는 실행 컨텍스트를 생성할 때 this 바인딩 과정 자체가 빠지게 되어, 상위 스코프의 this를 그대로 활용할 수 있다.(ES5 환경에서는 화살표 함수 사용 불가)</p>
<h3 id="📒-3-1-4-콜백-함수-호출-시-그-함수-내부에서의-this">📒 3-1-4 콜백 함수 호출 시 그 함수 내부에서의 this</h3>
<p>콜백 함수 : 함수 A의 제어권을 다른 함수(또는 메서드) B에게 넘겨주는 경우 제어권을 넘겨준 함수 A</p>
<p>함수 A는 함수 B의 내부 로직에 따라 실행</p>
<h4 id="콜백-함수-내부에서의-this">콜백 함수 내부에서의 this</h4>
<pre><code class="language-javascript">setTimeout(function() {console.log(this); }, 300) // 300ms만큼 시간 지연 한뒤 콜백함수 실행. 0.3초뒤 전역객체 출력

[1,2,3,4,5].forEach(function(x) {
    console.log(this, x);
}); // 전역객체와 배열의 각 요소가 총 5회 출력

document.body.innerHTML += '&lt;button id="a"&gt;클릭&lt;/button&gt;';
document.body.querySelector('#a')
    .addEventListener('click', function(e) {
          console.log(this, e);
    }); // click이벤트 발생할 때마다 이벤트 정보를 콜백 함수의 첫 번째 인자로 삼아 함수를 실행. 
        //앞서 지정한 엘리먼트와 클릭 이벤트에 관한 정보가 담긴 객체가 출력</code></pre>
<h3 id="📒-3-1-5-생성자-함수-내부에서의-this">📒 3-1-5 생성자 함수 내부에서의 this</h3>
<p>생성자 함수 : 어떤 공통된 성질을 지니는 객체들을 생성하는 데 사용하는 함수
객체지향 언어에서 → 클래스(생성자), 인스턴스(클래스를 통해 만든 객체) ⇒ 생성자 : 구체적인 인스턴스를 만들기 위한 일종의 틀
사용법 : new 명령어와 함께 함수를 호출 → 생성자의 prototype 프로퍼티를 참조하는 <strong>proto</strong>라는 프로퍼티가 있는 객체 생성 → 미리 준비된 공통 속성 및 개성을 해당 객체(this)에 부여</p>
<h4 id="생성자-함수">생성자 함수</h4>
<pre><code class="language-javascript">var Cat = function (name, age) {
      this.bark: '야옹', 
    this.name = name;
    this.age = age;
};

var choco = new Cat("초코", 7);
var nabi = new Cat("나비", 5);
console.log(choco, nabi); 

// Cat{ bark: '야옹', name:'초코', age:7 }
// Cat{ bark: '야옹', name:'나비', age:5 }</code></pre>
<h2 id="📌-3-2-명시적으로-this를-바인딩-하는-방법">📌 3-2 명시적으로 this를 바인딩 하는 방법</h2>
<h3 id="📒-3-2-1-call-메서드">📒 3-2-1 call 메서드</h3>
<pre><code class="language-javascript">Function.prototype.call(thisArg[, arg1[, arg2[,...]]])</code></pre>
<p>call 메서드 : 메서드의 호출 주체인 함수를 즉시 실행하도록 하는 명령.</p>
<p>call 메서드의 첫 번째 인자를 this로 바인딩, 이후의 인자들을 호출할 함수의 매개변수로 함
함수를 그냥 실행하면 thissms 전역객체를 참조하지만, call 메서드를 이용하면 임의의 객체를 this로 지정할 수 있다.</p>
<h4 id="call-메서드">call 메서드</h4>
<pre><code class="language-javascript">var func = function (a, b, c) {
    console.log(this, a, b, c);
};
func(1, 2, 3); // window{ ... } 1 2 3
func.call({x: 1}, 4, 5, 6); // { x: 1 } 4 5 6

var obj = {
    a: 1,
    method: function (x, y) {
        console.log(this.a, x, y);
    }
};
obj.method(2, 3); // 1 2 3
obj.method.call({ a: 4 }, 5, 6); // 4 5 6</code></pre>
<h3 id="📒-3-2-2-apply-메서드">📒 3-2-2 apply 메서드</h3>
<pre><code class="language-javascript">Function.prototype.apply(thisArg[, argsArray])</code></pre>
<p>apply 메서드 : call 메서드와 기능적으로 동일</p>
<p>call 메서드는 첫 번째 인자를 제외한 나머지 모든 인자들을 호출할 함수의 매개변수로 지정하는 반면, apply 메서드는 두 번째 인자를 배열로 받아 그 배열의 요소들을 호출할 함수의 매개변수로 지정한다는 점에서만 차이가 있음.</p>
<h4 id="apply-메서드">apply 메서드</h4>
<pre><code class="language-javascript">var func = function (a, b, c) {
    console.log(this, a, b, c);
};
func.apply({x: 1}, [4, 5, 6]); // { x: 1 } 4 5 6

var obj = {
    a: 1,
    method: function (x, y) {
        console.log(this.a, x, y);
    }
};
obj.method.apply({ a: 4 }, [5, 6]); // 4 5 6</code></pre>
<h3 id="📒-3-2-3-call--apply-메서드의-활용">📒 3-2-3 call / apply 메서드의 활용</h3>
<h4 id="유사-배열-객체에-배열-메서드를-적용">유사 배열 객체에 배열 메서드를 적용</h4>
<p>유사 배열 객체 : 키가 0 또는 양의 정수인 프로퍼티가 존재하고 length 프로퍼티의 값이 0 또는 양의 정수인 객체. 즉 배열의 구조와 유사한 객체의 경우</p>
<pre><code class="language-javascript">var obj = {
    0: 'a',
    1: 'b',
    2: 'c',
    length: 3
};

Array.prototype.push.call(obj, 'd');
console.log(obj); // {0: 'a', 1: 'b', 2: 'c', 3: 'd', length: 4}

var arr = Array.prototype.slice.call(obj);
console.log(arr); // ['a', 'b', 'c', 'd']</code></pre>
<h4 id="call--apply-메서드의-활용---es6의-arrayfrom-메서드">call / apply 메서드의 활용 - ES6의 Array.from 메서드</h4>
<pre><code class="language-javascript">var obj = {
    0: 'a',
    1: 'b',
    2: 'c',
    length: 3
};
var arr = Array.from(obj);
console.log(arr); // ['a', 'b', 'c']</code></pre>
<h4 id="생성자-내부에서-다른-생성자를-호출">생성자 내부에서 다른 생성자를 호출</h4>
<h4 id="call--apply-메서드의-활용---생성자-내부에서-다른-생성자를-호출">call / apply 메서드의 활용 - 생성자 내부에서 다른 생성자를 호출</h4>
<pre><code class="language-javascript">function Person(name, gender) {
    this.name = name;
    this.gender = gender;
}

function Student(name, gender, school) {
    Person.call(this, name, gender);
    this.school = school;
}
function Employee(name, gender, company) {
    Person.apply(this, [name, gender]);
    this.company = company;
}
var by = new Student('보영', 'fmale', '단국대');
var jn = new Employee('재난', 'male', '구골');</code></pre>
<p>생성자 내부에 다른 생성자와 공통된 내용이 있을 경우 call 또는 apply를 이용해 다른 생성자 호출하면 간단하게 반복을 줄일 수 있다.
Student, Employee 생성자 함수 내부에서 Person 생성자 함수를 호출해서 인스턴스 속성을 정의 → 반복 줄어든다.</p>
<h4 id="여러-인수를-묶어-하나의-배열로-전달하고-싶을-때---apply-활용">여러 인수를 묶어 하나의 배열로 전달하고 싶을 때 - apply 활용</h4>
<h4 id="call--apply-메서드의-활용---mathmaxmin-es6-펼치기-연산자spread-operator--">call / apply 메서드의 활용 - Math.max/min, ES6 펼치기 연산자(spread operator) : …</h4>
<pre><code class="language-javascript">var numbers = [10,20,3,16,45];
// var max = Math.max.apply(null, numbers);
// var min = Math.min.apply(null, numbers);

const max = Math.max(...numbers);
const min = Math.min(...numbers);
console.log(max, min);  // 45 3</code></pre>
<h3 id="📒-3-2-4-bind-메서드">📒 3-2-4 bind 메서드</h3>
<pre><code class="language-javascript">Fnuction.prototype.bind(thisArg[, arg1, [arg2[, ...]])</code></pre>
<p>bind 메서드 : ES5에서 추가된 기능, call과 비슷하지만 즉시 호출하지는 않고 넘겨받은 this 및 인수들을 바탕으로 새로운 함수를 반환하기만 하는 메서드
→ 함수에 this를 미리 적용하는 것과 부분 적용 함수를 구현하는 두 가지 목적</p>
<h4 id="bind-메서드---this-지정과-부분-적용-함수-구현">bind 메서드 - this 지정과 부분 적용 함수 구현</h4>
<pre><code class="language-javascript">var func = function (a, b, c, d){
    console.log(this, a, b, c, d);
};
func(1, 2, 3, 4);  // window{ ... } 1 2 3 4

var bindFunc1 = func.bind({x: 1});
bindFunc1(5, 6, 7, 8);  // { x: 1 } 5 6 7 8

var bindFunc2 = func.bind({ x: 1 }, 4, 5);
bindFunc2(6, 7);  // { x: 1 } 4 5 6 7
bindFunc2(8, 9);  // { x: 1 } 4 5 8 9</code></pre>
<h4 id="name-프로퍼티">name 프로퍼티</h4>
<h4 id="bind-메서드---name-프로퍼티">bind 메서드 - name 프로퍼티</h4>
<pre><code class="language-javascript">var func = function (a, b, c, d){
    console.log(this, a, b, c, d);
};
var bindFunc = func.bind({ x: 1 }, 4, 5);
console.log(func.name);  // func
console.log(bindFunc.name);  // bound func</code></pre>
<p>name 프로퍼티에 동사 bind의 수동태인 ‘bound’ 라는 접두어가 붙는다.</p>
<h4 id="상위-컨텍스트의-this를-내부-함수나-콜백-함수에-전달하기">상위 컨텍스트의 this를 내부 함수나 콜백 함수에 전달하기</h4>
<p>메서드의 내부 함수에서 메서드의 this를 그대로 바라보게 하기 위한 방법으로 self등의 변수를 활용한 우회회법을 사용하는 것보다 call, apply, bind 메서드를 이용해 더 깔끔하게 처리 가능하다.</p>
<h3 id="📒-3-2-5-화살표-함수의-예외사항">📒 3-2-5 화살표 함수의 예외사항</h3>
<p>ES6에 새롭게 도입된 화살표 함수는 실행 컨텍스트 생성 시 this를 바인딩 하는 과정이 제외 → 함수 내부에는 this가 아예 없으며 접근하고자 하면 스코프체인상 가장 가까운 this에 접근하게 된다.</p>
<pre><code class="language-javascript">var obj = {
  outer: function() {
    console.log(this);
    var innerFunc = () =&gt; {
      console.log(this);
    };
    inneerFunc();
  }
};
obj.outer();</code></pre>
<h3 id="📒-3-2-6-별도의-인자로-this를-받는-경우콜백-함수-내에서의-this">📒 3-2-6 별도의 인자로 this를 받는 경우(콜백 함수 내에서의 this)</h3>
<p>콜백 함수를 인자로 받는 메서드 중 일부는 추가로 this로 지정할 객체(thisArg)를 인자로 지정할 수 있는 경우가 있다. 이러한 메서드의 thisArg 값을 지정하면 콜백 함수 내부에서 this 값을 원하는 대로 변경할 수 있다. 이런 형태는 여러 내부 요소에 대해 같은 동작을 반복 수행해야 하는 배열 메서드에 많이 포진돼 있으며, 새로 등장한 Set, Map 등의 메서드에도 일부 존재한다.</p>
<pre><code class="language-javascript">Array.prototype.forEach(callback[, thisArg])
Array.prototype.map(callback[, thisArg])
Array.prototype.filter(callback[, thisArg])
Array.prototype.some(callback[, thisArg])
Array.prototype.every(callback[, thisArg])
Array.prototype.find(callback[, thisArg])
Array.prototype.findIndex(callback[, thisArg])
Array.prototype.flatMap(callback[, thisArg])
Array.prototype.from(arrayLike[, callback[, thisArg]])
Set.prototype.forEach(callback[, thisArg])
Map.prototype.forEach(callback[, thisArg])</code></pre>