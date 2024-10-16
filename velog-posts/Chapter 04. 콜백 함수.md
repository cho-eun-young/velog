<h2 id="📌-4-1-콜백-함수란">📌 4-1 콜백 함수란?</h2>
<p>콜백함수(callback function)는 다른 코드의 인자로 넘겨주는 함수. 콜백 함수를 넘겨받은 코드는 콜백 함수를 필요에 따라 적절한 시점에 실행할 것.
다른 코드(함수 또는 메서드)에게 인자로 넘겨줌으로써 그 제어권도 함께 위임한 함수이다.</p>
<h2 id="📌-4-2-제어권">📌 4-2 제어권?</h2>
<h3 id="📒-4-2-1-호출-시점">📒 4-2-1 호출 시점</h3>
<h4 id="콜백-함수-예제-1-1-setinterval">콜백 함수 예제 1-1 setInterval</h4>
<pre><code class="language-javascript">var count = 0;
var timer = setInterval(function () { 
        console.log(count);
        if(++count &gt; 4) clearInterval(timer);
}, 300) </code></pre>
<h4 id="setinterval-구조">setInterval 구조</h4>
<pre><code class="language-javascript">var intervalID = scope.setInterval(func,delay[, param1, param2, ...]);</code></pre>
<h4 id="콜백-함수-예제-1-2-setinterval">콜백 함수 예제 1-2 setInterval</h4>
<pre><code class="language-javascript">var count = 0;
var cbFufnc = function() { // 콜백함수
    console.log(count);
    if (++count &gt; 4) clearInterval(timer);
};
var timer = setInterval(cbFunc, 300);

// -- 실행 결과 --
// 0 (0.3초)
// 1 (0.6초)
// 2 (0.9초)
// 3 (1.2초)
// 4 (1.5초)</code></pre>
<ul>
<li>setInterval에 전달한 첫번째 인자인 cbFunc함수(콜백함수) 0.3초마다 자동으로 실행.</li>
<li>콜백 함수 내부에서 count 값을 출력하고, count를 1초 증가시킨 다음, 그 값이 4보다 크면 반복 실행을 종료</li>
<li>setInterval이라는 ‘다른코드'에 첫번째 인자로 cbFunc 함수를 넘겨주자, 제어권을 넘겨받은 setInterval이 스스로 판단에 따라 적절한 시점(0.3초)마다 이 익명함수를 실행함.</li>
<li>이처럼, 콜백함수의 제어권을 넘겨받은 코드는 콜백 함수 호출 시점에 대한 제어권을 가진다.</li>
</ul>
<h3 id="📒-4-2-2-인자">📒 4-2-2 인자</h3>
<h4 id="콜백-함수-예제-arrayprototypemap">콜백 함수 예제 Array.prototype.map</h4>
<pre><code class="language-javascript">var newArr = [10, 20, 30].map(function (currentValue, index) {
    console.log(currentValue, index);
    return currentValue + 5;
});
console.log(newArr);

// -- 실행 결과 --
// 10 0 
// 20 1
// 30 2
// [15, 25, 35]</code></pre>
<p>map 메서드</p>
<pre><code class="language-javascript">Array.prototype.map(callback[, thisArg])
callback: function(currentValue, index, array)</code></pre>
<p>첫 번째 인자로 callback 함수를 받고, 생략 가능한 두 번째 인자로 콜백 함수 내부에서 this로 인식할 대상을 특정할 수 있다. thisArg를 생략할 경우에는 일반적인 함수와 마찬가지로 전역 객체가 바인딩 된다.</p>
<p>: 대상이 되는 배열의 모든 요소들을 처음부터 끝까지 하나식 꺼내어 콜백 함수를 반복 호출하고, 콜백 함수의 실행 결과들을 모아 새로운 배열을 만든다. </p>
<ul>
<li>map 메서드를 호출해서 원하는 배열을 얻으려면 map 메서드에 정의된 규칙에 따라 함수를 작성해야한다. </li>
<li>콜백 함수를 호출하는 주체가 사용자가 아닌 map 메서드 이므로 map 메서드가 콜백 함수를 호출할 때 인자에 어떤 값들을 어떤 순서로 넘길 것인지가 전적으로 map메서드에게 달림</li>
<li>이처럼, 콜백 함수의 제어권을 넘겨받은 코드는 콜백 함수를 호출할 때 인자에 어떤 값들을 어떤 순서로 넘길 것인지에 대한 제어권을 가짐</li>
</ul>
<h3 id="📒-4-2-3-this">📒 4-2-3 this</h3>
<h4 id="콜백-함수-내부에서의-this">콜백 함수 내부에서의 this</h4>
<pre><code class="language-javascript">setTimeout(function () {
  console.log(this);
}, 300); // (1) Window { ... }

[1, 2, 3, 4, 5].forEach(function (x) {
  console.log(this); // (2) Window { ... }
});

document.body.innerHTML += '&lt;button id="a"&gt;클릭&lt;/button&gt;';
document.body.querySelector("#a").addEventListener("click", function (e) {
  console.log(this, e); // (3) &lt;button id="a"&gt;클릭&lt;/button&gt;
});                     //  MouseEvent { isTrusted: true, ... }
</code></pre>
<p>(1) setTimeout은 내부에서 콜백 함수를 호출할 때 call 메서드의 첫 번째 인자에 전역 객체를 넘기기 때문에, 콜백 함수 내부에서의 this가 전역 객체를 가리킴</p>
<p>(2) forEach는 ‘별도의 인자로 this를 받는 경우'에 해당하지만 별도의 인자로 this를 넘져주지 않았기 때문에 전역 객체를 가리킴</p>
<p>(3) addEventListener는 내부에서 콜백 함수를 호출할 때 call 메서드의 첫번째 인자에 addEventListener 메서드의 this를 그래도 넘기도록 정의돼 있기 때문에 콜백 함수 내부에서의 this가 addEventListener를 호출한 주체인 HTML 엘리먼트를 가리킴</p>
<h2 id="📌-4-3-콜백-함수는-함수다">📌 4-3 콜백 함수는 함수다</h2>
<p>콜백 함수는 함수다
콜백 함수로 어떤 객체의 메서드를 전달하더라고 그 메서드는 메서드가 아닌 <strong>함수</strong>로서 호출된다.</p>
<h4 id="메서드를-콜백-함수로-전달한-경우">메서드를 콜백 함수로 전달한 경우</h4>
<pre><code class="language-javascript">var obj = {
  vals: [1, 2, 3],
  logValues: function (v, i) {
    console.log(this, v, i);
  },
};
obj.logValues(1, 2); // (1) {vals: [1, 2, 3], logValues: f} 1 2
[4, 5, 6].forEach(obj.logValues); // (2) Window  {...} 4 0</code></pre>
<ul>
<li><p>obj 객체의 logValues는 메서드로 정의됨. (1) 에서는 이 메서드의 이름앞에 점이 있으니 메서드로서 호출한 것.this는 obj를 가리키고, 인자로 넘어온 1, 2가 출력된다.</p>
</li>
<li><p>(2) 이 메서드를 forEach 함수의 콜백 함수로서 전달함. obj를 this로 하는 메서드를 그대로 전달한게 아니라, obj.logValues가 가리키는 함수만 전달한 것. forEach에 의해 콜백이 함수로서 호출이 되고, 별도로 this를 지정하지 않았으므로 함수 내부에서의 this는 전역객체를 바라본다.</p>
</li>
</ul>
<h2 id="📌-4-4-콜백-함수-내부의-this에-다른-값-바인딩하기">📌 4-4 콜백 함수 내부의 this에 다른 값 바인딩하기</h2>
<p>위에서 “객체의 메서드를 콜백 함수로 전달하면 해당 객체를 this로 바라볼 수 없다.” 라고 했다. 그럼에도 콜백 함수 내부에서 this가 객체를 바라보게하고 싶다면 어떻게 해야하는지?</p>
<p>전통적으로는 this를 다른 변수에 담아 콜백 함수로 활용할 함수에서는 this 대신 그 변수를 사용하게 하고, 이를 클로저로 만드는 방식을 썼다.</p>
<h4 id="콜백-함수-내부의-this에-다른-값을-바인딩하는-방법1---전통적인-방식">콜백 함수 내부의 this에 다른 값을 바인딩하는 방법(1) - 전통적인 방식</h4>
<pre><code class="language-javascript">var obj1 = {
  name: "obj1",
  func: function () {
    var self = this;
    return function () {
      console.log(self.name);
    };
  },
};
var callback = obj1.func(); // (1)
setTimeout(callback, 1000); // (2) obj1</code></pre>
<p>obj1.func 메서드 내부에서 self 변수에 this를 담고, 익명함수를 반환한다.</p>
<p>(1) 에서 obj1.func()를 호출하면 앞서 선언한 내부함수가 반환되어 callback 변수에 담긴다.</p>
<p>(2)에서 이 callback을 setTimeout함수에 인자로 전달하면 1초 뒤 callback이 실행되면서 ‘obj1’을 출력한다.</p>
<p>하지만 이 방식은 실제로 this를 사용하지 않을뿐더러 너무 번거롭고 비효율적이다.</p>
<h4 id="콜백-함수-내부에서-this를-사용하지-않은-경우">콜백 함수 내부에서 this를 사용하지 않은 경우</h4>
<pre><code class="language-javascript">var obj1 = {
  name: "obj1",
  func: function () {
    console.log(obj1.name);
  },
};
setTimeout(obj1.func, 1000);</code></pre>
<h4 id="콜백-함수-내부의-this에-다른-값을-바인딩하는-방법2---bind-메서드-활용">콜백 함수 내부의 this에 다른 값을 바인딩하는 방법(2) - bind 메서드 활용</h4>
<pre><code class="language-javascript">var obj1 = {
  name: 'obj1',
  func: function () {
    console.log(this.name);
  },
};
setTimeout(obj1.func.bind(obj1), 1000);

var obj2 = {name: 'obj2' };
setTimeout(obj2.func.bind(obj2), 1000);</code></pre>
<h2 id="📌-4-5-콜백-지옥과-비동기-제어">📌 4-5 콜백 지옥과 비동기 제어</h2>
<ul>
<li><p>콜백 지옥(callback hell): 콜백 함수를 익명 함수로 전달하는 과정이 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상. 자바스크립트에서 흔히 발생하는 문제.</p>
</li>
<li><p>동기적인 코드 : 현재 실행 중인 코드가 완료된 후에야 다음 코드를 실행하는 방식
예) CPU의 계산에 의해 즉시 처리가 가능한 대부분의 코드</p>
</li>
<li><p>비동기적인 코드 : 현재 실행 중인 코드의 완료 여부와 무관하게 즉시 다음 코드로 넘어감
setTimeout, addEventListener, XMLHttpRequest 등
별도의 요청, 실행 대기, 보류 등과 관련된 코드</p>
</li>
</ul>
<h4 id="콜백-지옥-예시">콜백 지옥 예시</h4>
<pre><code class="language-javascript">setTimeout(function (name)){  //  ---- (4)
    var coffeeList = name;
        console.log(coffeeList);

        setTimeout(function (name)){  // ---- (3)
          coffeeList += ',' + name;
            console.log(coffeeList);

            setTimeout(function (name)){  // ---- (2)
              coffeeList += ',' + name;
                console.log(coffeeList);

                setTimeout(function (name)){  // ----(1)
                  coffeeList += ',' + name;
                    console.log(coffeeList);
                },500,'카페라떼');
            },500,'카페모카');
        },500,'아메리카노');
},500,'에스프레소');</code></pre>
<p>0.5초 주기마다 커피 목록을 수집하고 출력하는 코드
가독성 문제, 어색함 해결방법 : 익명의 콜백 함수를 모두 기명함수로 전환</p>
<pre><code class="language-javascript">var coffeeList='';

var addEsspresso = function (name) {
    coffeeList = name;
    console.log(coffeeList);
    setTimeout(addAmericano,500,'아메리카노');
};

var addAmericano = function (name) {
    coffeeList += ',' + name;
    console.log(coffeeList);
    setTimeout(addMocha,500,'카페모카');
};

var addMocha = function (name) {
    coffeeList += ',' + name;
    console.log(coffeeList);
    setTimeout(addLatte,500,'카페라떼');
};

var addLatte = function (name) {
    coffeeList += ',' + name;
    console.log(coffeeList);;
};

setTimeout(addEspresso,500,'에스프레소');</code></pre>
<p>코드의 가독성을 높인다.
하지만 위 코드가 최선이라고 할 수는 없음. 일회성 함수를 전부 변수에 할당하는 것이 비효율적이다.
ES6에서는 Promise, Generator 등이 도입됐고, ES2017에서는 aync/await 가 도입됐다.</p>
<h4 id="비동기-작업의-동기적-표현---promise">비동기 작업의 동기적 표현 - Promise</h4>
<pre><code class="language-javascript">var addCoffee = function (name) {
  return function (prevName) {
    return new Promise(function (resolve) {
      setTimeout(function () {
        var newName = prevName ? prevNAme + ", " + name : name;
        console.log(newName);
        resolve(newName);
      }, 500);
    });
  };
};
addCoffee("아메리카노")()
  .then(addCoffee("카페모카"))
  .then(addCoffee("카페라떼"))
  .then(addCoffee("에스프레소"));</code></pre>
<p>new 연산자와 함께 호출한 Promise의 인자로 넘겨주는 콜백 함수는 호출할 때 바로 실행되지만 그 내부에 resolve 또는 reject 함수를 호출하는 구문이 있을 경우 둘 중 하나가 실행 되지 전까지는 다음(then) 또는 오류 구문(catch)로 넘어가지 않는다.</p>
<p>따라서 비동기 작업이 완료될 때 resolve 또는 reject를 호출하는 방법으로 비동기 작업의 동기적 표현이 가능하다.</p>
<h4 id="비동기-작업의-동기적-표현---promise-반복적인-내용을-함수화해서-짧게-표현한-것">비동기 작업의 동기적 표현 - Promise (반복적인 내용을 함수화해서 짧게 표현한 것)</h4>
<pre><code class="language-javascript">var addCoffee = function(name){
    return function(prevName){
        return new Promise(function (resolve){
            setTimeout(function(){
                var newName = prevName ? (prevName + ' ,'+name) : name;
                console.log(newName);
                resolve(newName);
            },500);
        });
    };
};
addCoffee('에스프레소')()
    .then(addCoffee('아메리카노'))
    .then(addCoffee('카페모카'))
    .then(addCoffee('카페라떼'))</code></pre>
<h4 id="비동기-작업의-동기적-표현---generator">비동기 작업의 동기적 표현 - Generator</h4>
<pre><code class="language-javascript">var addCoffee = function(prevName, name) {
    setTimeout(function() {
        coffeeMaker.next(prevName ? prevName + ', ' + name : name);
    }, 500);
};
var coffeeGenerator = function* () { // '*'이 붙은 함수 -&gt; Generator 함수
    var espresso = yield addCoffee('', '에스프레소');
    console.log(espresso);
    var americano = yield addCoffee(espresso, '아메리카노');
    console.log(americano);
    var mocha = yield addCoffee(americano, '카페모카');
    console.log(mocha);
    var latte = yield addCoffee(mocha, '카페라떼');
    console.log(latte);
};
var coffeeMaker = coffeeGenerator();
coffeeMaker.next();</code></pre>
<p>Generator 함수를 실행하면 Iterator가 반환되는데, Iterator가 가지고 있는 next 메서드를 호출하면 Generator 함수 내부에서 가장 먼저 등장하는 yield에서 함수의 실행을 멈춤</p>
<p>이후 다시 next 메서드를 호출하면 앞서 멈췄던 부분부터 시작해서 다음 yield에서 함수의 실행을 멈춤 (반복)</p>
<p>비동기 작업이 완료되는 시점마다 next 메서드를 호출해준다면 Generator 함수 내부의 소수가 위에서부터 아래로 순차적으로 진행됨</p>
<h4 id="비동기-작업의-동기적-표현---promise--asyncawait">비동기 작업의 동기적 표현 - Promise + Async/await</h4>
<pre><code class="language-javascript">var addCoffee = function (name) {
  return new Promise(function (resolve) {
    setTimeout(function () {
      resolve(name);
    }, 500);
  });
};
var coffeeMaker = async function () {
  var coffeeList = "";
  var _addCoffee = async function (name) {
    coffeeList += (coffeeList ? "," : "") + (await addCoffee(name));
  };

  await _addCoffee("아메리카노");
  console.log(coffeeList);
  await _addCoffee("카페모카");
  console.log(coffeeList);
  await _addCoffee("카페라떼");
  console.log(coffeeList);
  await _addCoffee("에스프레소");
  console.log(coffeeList);
};

coffeeMaker();</code></pre>
<p>ES2017에서 가독성도 뛰어나고 작성법도 간단한 async/await 기능이 추가됨.</p>
<p>비동기 작업을 수행하고자 하는 함수 앞에 async를 표기하고, 함수 내부에서 실질적인 비동기 작업이 필요한 위치마다 await를 표기하면 뒤의 내용을 Promise로 자동 전환하고, 해당 내용이 resolve 된 이후에야 다음으로 진행함.</p>
<p>즉 Promise의 then과 흡사한 효과 얻을 수 있다.</p>