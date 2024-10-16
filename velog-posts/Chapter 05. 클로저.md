<h2 id="📌-5-1-클로저의-의미-및-원리-이해">📌 5-1 클로저의 의미 및 원리 이해</h2>
<ul>
<li>클로저는 여러 함수형 프로그래밍 언어에서 등장하는 보편적인 특성<h4 id="외부-함수의-변수를-참조하는-내부-함수1">외부 함수의 변수를 참조하는 내부 함수(1)</h4>
<pre><code class="language-javascript">var outer = function () {   // 외부 함수
var a = 1;
var inner = function () { // 내부 함수
  console.log(++a); // 2
};
inner();
};
outer();</code></pre>
</li>
</ul>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/c0d88b11-3da5-4b5f-bc83-691444f22d07/image.png" /></p>
<h4 id="외부-함수의-변수를-참조하는-내부-함수3">외부 함수의 변수를 참조하는 내부 함수(3)</h4>
<pre><code class="language-javascript">var outer = function () {   // 외부 함수
  var a = 1;
  var inner = function () { // 내부 함수
    return ++a;
  };
  return inner();
};
var outer2 = outer();
console.log(outer2()); // 2
console.log(outer2()); // 3</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/8a9e271d-f7f0-4ba0-9f6f-5d457b6794a9/image.png" /></p>
<ul>
<li>클로저란 어떤 함수 A에서 선언한 변수 a를 참조하는 내부함수 B를 외부로 전달할 경우 A의 실행 컨텍스트가 종료된 이후에도 변수 a가 사라지지 않는 현상</li>
</ul>
<h2 id="📌-5-2-클로저와-메모리-관리">📌 5-2 클로저와 메모리 관리</h2>
<p>메모리 누수의 위험을 이유로 클로저 사용을 조심, 지양해야한다고 주장하는 사람들이 있음
하지만, 메모리 소모는 클로저의 본질적인 특성.</p>
<p>메모리 누수 : 개발자의 의도와 달리 어떤 값의 참조 카운트가 0이 되지 않아 가비지 컬렉팅의 수거 대상이 되지 않는 경우</p>
<h4 id="클로저의-메모리-관리">클로저의 메모리 관리</h4>
<pre><code class="language-javascript">// return 에 의한 클로저의 메모리 해제
var outer = (function () {
    var a = 1;
    var inner = function () {
        return ++a;
    }
    return inner;
})();

console.log(outer());
console.log(outer());
outer = null; // outer 식별자의 inner 함수 참조를 끊음</code></pre>
<h2 id="📌-5-3-클로저-활용-사례">📌 5-3 클로저 활용 사례</h2>
<h3 id="📒-5-3-1-콜백-함수-내부에서-외부-데이터를-사용하고자-할-때">📒 5-3-1 콜백 함수 내부에서 외부 데이터를 사용하고자 할 때</h3>
<h4 id="콜백-함수와-클로저1">콜백 함수와 클로저(1)</h4>
<pre><code class="language-javascript">const fruits = ['apple', 'banana', 'peach'];
const $ul = document.createElement('ul');         // (공통 코드)

fruits.forEach(function (fruit) {                 // (A)
    var $li = document.createElement('li');
   $li.innerText = fruit;
   $li.addEventListener('click', function() {     // (B) 
      alert('your choice is ' + fruit); 
   });

   $ul.appendChild($li);
});

document.body.appendChild($ul);</code></pre>
<p>(A): fruits의 개수만큼 실행, 그때마다 새로운 실행 컨텍스트 활성화
(B): (A)의 실행 종료 여부와 무관하게 클릭 이벤트에 의해 실행됨. outerEnvironmentReference가 (A)의 LexicalEnvironment를 참조. 따라서 (B)함수가 참조할 예정인 변수 fruit에 대해서는 (A)가 종료된 후에도 가비지 컬렉터대상에서 제외되고, 계속 참조 가능</p>
<h4 id="콜백-함수와-클로저3">콜백 함수와 클로저(3)</h4>
<pre><code class="language-javascript">...
fruits.forEach(function (fruit){
    var $li = document.createElement('li');
    $li.innerText = fruit;
    $li.addEventListener('click', alertFruit.bind(null, fruit));
    $ul.appendChild($li);
});
...</code></pre>
<p>이벤트 객체가 인자로 넘어오는 순서가 바뀌는 점 및 함수 내부에서의 this가 원래와 달라지게됨.이런 변경사항이 발생하지 않게 하려면 bind 메서드가 아닌 고차함수를 활용해야한다.(함수형 프로그래밍에서 자주 쓰이는 방식)</p>
<h4 id="콜백-함수와-클로저4---콜백함수를-고차함수로-바꿔서-클로저-활용방안">콜백 함수와 클로저(4) - 콜백함수를 고차함수로 바꿔서 클로저 활용방안</h4>
<pre><code class="language-javascript">var alertFruitBuilder = function (fruit) {
    return function () {
        alert('your choice is ' + fruit);
    };
};
fruits.forEach(function (fruit){
    var $li = document.createElement('li');
    $li.innerText = fruit;
    $li.addEventListener('click', alertFruitbuilder(fruit));
    $ul.appendChild($li);
});
...</code></pre>
<p>(1) alertFruitBuilder라는 함수 내부에서는 다시 익명함수를 반환하는데, 이 익명함수가 바로 기존의 alertFruit함수다.
(2) 이벤트 핸들러에서 alertFruitBuilder 함수를 실행하면서 fruit 값을 인자로 전달한다.
이 함수의 실행 결과가 다시 함수가 되며, 이렇게 반환된 함수를 리스너에 콜백 함수로써 전달함.
이후에 클릭 이벤트가 발생하면 이 함수의 실행 컨텍스트가 열리면서 alertFruitBuilder의 인자로 넘어온 fruit를 outerEnvironmentReference에 의해 참조할 수 있게 됨.  즉, alertFruitBuilder의 실행 결과로 반환된 함수에는 클로저가 존재</p>
<h3 id="📒-5-3-2-접근-권한-제어-정보-은닉">📒 5-3-2. 접근 권한 제어 (정보 은닉)</h3>
<pre><code class="language-javascript">const outer = function () {
   let a = 1;
   const inner = function () {
      return ++a;
   };
   return inner; 
};

const outer2 = outer();
console.log(outer2());
console.log(outer2());</code></pre>
<p>정보 은닉(Information hiding) : 어떤 모듈의 내부 로직에 대해 외부로의 노출을 최소화해서 모듈 간의 결합도를 낮추고 유연성을 높이고자 하는 개념</p>
<p>public : 외부에서 접근 가능
private : 내부에서만 사용하며 외부에 노출되지 않는 것</p>
<p>자바스크립트는 기본적으로 변수 자체에 이러한 접근 권한 직접 부여하지 못함
하지만 return 이용해 함수 내부의 변수들 중 선택적으로 일부의 변수에 대한 접근 권한을 부여할 수 있음
외부에 제공하고하는 정보들을 모아서 return하고, 내부에서만 사용할 정보들은 return 하지 않은 것으로 접근 제어 가능</p>
<h3 id="📒-5-3-3-부분-적용-함수">📒 5-3-3 부분 적용 함수</h3>
<ul>
<li><p>부분 적용 함수(partially applied function): n개의 인자를 받는 함수에 미리 m개의 인자만 넘겨 기억시켰다가, 나중에 (n-m)개의 인자를 넘기면 비로소 원래 함수의 실행 결과를 얻을 수 있도록 하는 함수.
this를 바인딩해야 하는 점을 제외하면 bind메서드의 실행 결과가 바로 부분 적용 함수</p>
</li>
<li><p>디바운스(debounce) : scroll, wheel, mousemove, resize에 활용하기 좋다. 
짧은 시간 동안 동일한 이벤트가 많이 발생할 경우 이를 전부 처리하지 않고 처음 또는 마지막에 발생한 이벤트에 대해 한 번만 처리하는 것. 프론트엔드 성능 최적화에 큰 도움을 주는 기능</p>
</li>
</ul>
<h3 id="📒-5-3-4-커링-함수">📒 5-3-4 커링 함수</h3>
<p>커링 함수(currying function) : 여러 개의 인자를 받는 함수를 하나의 인자만 받는 함수로 나눠서 순차적으로 호출될 수 있게 체인 형태로 구성한 것</p>
<h4 id="커링-함수1">커링 함수(1)</h4>
<pre><code class="language-javascript">var curry3 = function (func) {
    return function (a) {
        return function (b) {
            return func(a, b);
        };
    };
};

var getMaxWith10 = curry3(Math.max)(10);
console.log(getMaxWiht10(8)); // 10
console.log(getMaxWiht10(25)); // 25

const getMinWith10 = curry3(Math.min)(10);
onsole.log(getMinWith10(8)); // 8
console.log(getMinWith10(25)); // 10</code></pre>
<p>부분 적용 함수와 달리 커링 함수는 필요한 상황에 직접 만들어 쓰기 용이하다. 필요한 인자 개수만큼 함수를 만들어 계속 리턴해주다가 마지막에 짠! 하고 조합해서 리턴해주면 되기 때문. 다만 인자가 많아질수록 가독성이 떨어진다는 단점.(화살표 함수를 써서 한줄에 표기 가능하다)</p>