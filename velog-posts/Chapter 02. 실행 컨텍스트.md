<h2 id="📌-2-1-실행-컨텍스트란">📌 2-1 실행 컨텍스트란?</h2>
<p>실행 컨텍스트(excution context) : <strong>실행할 코드에 제공할 환경 정보들을 모아놓은 객체</strong>
자바스크립트 코드가 실행되는 환경을 의미합니다. 코드의 실행 순서와 스코프를 관리합니다.</p>
<blockquote>
<p>스택(stack) 큐(queue) 란 ? ?
<img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/a0555ba9-f701-4894-a432-6b56842e6d1a/image.png" /></p>
</blockquote>
<p>📒 스택(stack)
"후입선출" (LIFO: Last In, First Out) 원칙을 따르는 자료구조 : 우물 같은 구조
용량보다 많은 데이터를 저장하려고 하면 넘친다 → stack overflow</p>
<p>📒 큐 (queue)
"선입선출" (FIFO: First In, First Out) 원칙을 따르는 자료구조 : 양쪽이 모두 열려 있는 파이프 같은 구조</p>
<pre><code class="language-javascript">// (1)
var a = 1;
function outer() {
    function inner() {
        console.log(a); //undefined
        var a = 3;
    }
    inner(); // (2)
    console.log(a); // 1
}

outer(); // (3)
console.log(a); // 1</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/8daeb112-0ba6-4a1f-b399-398dc2485345/image.png" /></p>
<h3 id="실행-컨텍스트의-구성">실행 컨텍스트의 구성</h3>
<p>📒 VariableEnvironment: 현재 컨텍스트 내의 식별자들에 대한 정보와 외부 환경 정보를 담습니다. 선언 시점의 LexicalEnvironment의 스냅샷으로, 변경사항이 반영되지 않습니다.
📒 LexicalEnvironment: VariableEnvironment와 같지만, 변경사항이 실시간으로 반영됩니다.
📒 ThisBinding: this 식별자가 바라보는 대상 객체를 저장합니다.</p>
<h3 id="lexicalenvironment의-구성">LexicalEnvironment의 구성</h3>
<p>📒 EnvironmentRecord: 현재 컨텍스트와 관련된 식별자 정보를 저장합니다.
📒 OuterEnvironmentReference: 외부 환경에 대한 참조를 저장합니다.</p>
<h2 id="📌-2-2-variableenvironment">📌 2-2 VariableEnvironment</h2>
<p>VariableEnvironment에 담기는 내용은 LexicalEnvironment와 같지만 최초 실행 시의 스냅샷을 유지한다는 점이 다르다. </p>
<p>실행 컨텍스트를 생성할 때 VariableEnvironment에 정보를 담는다 
→ 이를 그대로 복사해서 LexicalEnvironment를 만든다 
→ 이후에 LexicalEnvironment를 주로 활용한다</p>
<h2 id="📌-2-3-lexicalenvironment-사전적인-환경">📌 2-3 LexicalEnvironment ('사전적인 환경')</h2>
<h3 id="✏️-2-3-1-environmentrecord와-호이스팅">✏️ 2-3-1 EnvironmentRecord와 호이스팅</h3>
<p>EnvironmentRecord에는 현재 컨텍스트와 관련된 코드의 식별자 정보들이 저장된다.
컨텍스트 내부 전체를 처음부터 끝까지 쭉 훑어나가며 순서대로 수집한다.</p>
<p>자바스크립트 엔진은 식별자들을 최상단으로 끌어올린 다음 실제 코드를 실행한다.</p>
<blockquote>
<p>🤔 호이스팅 (Hoisting)
변수 선언과 함수 선언을 코드의 최상단으로 끌어올리는 것처럼 동작하는 현상입니다.
실제로는 코드가 옮겨지는 것이 아니라, 자바스크립트 엔진이 코드를 파싱하면서 변수와 함수의 선언부를 먼저 실행하기 때문에 발생합니다. 가상의 개념 !!!</p>
</blockquote>
<h4 id="매개변수와-변수에-대한-호이스팅1---원본코드">매개변수와 변수에 대한 호이스팅(1) - 원본코드</h4>
<pre><code class="language-javascript">function a (x) { // 수집대상 1 (매개변수)
    console.log(x); // (1) 예상 : 1
    var x; // 수집대상 2 (변수 선언)
    console.log(x); // (2) 예상 : undefined
    var x = 2; // 수집대상 3 (변수 선언)
    console.log(x); // (3) 예상 : 2
}</code></pre>
<h4 id="매개변수와-변수에-대한-호이스팅2---매개변수를-변수-선언할당과-같다고-간주해서-변환한-상태">매개변수와 변수에 대한 호이스팅(2) - 매개변수를 변수 선언/할당과 같다고 간주해서 변환한 상태</h4>
<pre><code class="language-javascript">function a () {
    var x = 1; // 수집대상 1 (매개변수 선언)
    console.log(x); // (1)
    var x; // 수집대상 1 (변수 선언)
    console.log(x); // (2)
    var x = 2; // 수집대상 3 (변수 선언)
    console.log(x); // (3)
}</code></pre>
<ul>
<li>호이스팅 할때 : 변수명만 끌어올리고 할당 과정은 원래 자리에 그래도 남겨둡니다)</li>
</ul>
<h4 id="매개변수와-변수에-대한-호이스팅3---호이스팅을-마친-상태">매개변수와 변수에 대한 호이스팅(3) - 호이스팅을 마친 상태</h4>
<pre><code class="language-javascript">function a () {
    var x; // 변수 x 선언 → 메모리에서 저장 공간 확보, 주솟값을 변수 x에 연결
    var x; // 다시 변수 x 선언 
    var x; // 이미 선언된 변수가 있으므로 무시한다.

    x = 1; // x에 1을 할당 → 1을 별도의 메모리에 담고, 주솟값 입력
    console.log(x); // 1 출력
    console.log(x); // 1 출력
    x = 2; // x에 2를 할당 → 2을 별도의 메모리에 담고, 1을 가리키는 주솟값을 2를 가리키는 주소값으로 대치. x는 숫자 2를 가리키게 된다.
    console.log(x); // 2 출력. 함수 내부 모든 코드 실행됐으므로 실행 컨텍스트가 콜 스택에서 제거됨.
}

a(1);</code></pre>
<h3 id="✅-함수-선언문과-함수-표현식">✅ 함수 선언문과 함수 표현식</h3>
<ul>
<li>함수 선언문(function declaration) : function 정의부만 존재하고 별도의 할당 명령이 없는 것을 의미, 반드시 함수명 정의 !!</li>
<li>함수 표현식(function expression) : 정의한 function을 별도의 변수에 할당하는 것을 의미, 함수명 없어도 됨. <blockquote>
<p>함수명 정의한것('기명 함수식'), 함수명 정의하지 않은것('익명 함수 표현식')
일반적으로 함수 표현식은 익명 함수 표현식을 말한다.</p>
</blockquote>
</li>
</ul>
<h4 id="함수를-정의하는-세-가지-방식">함수를 정의하는 세 가지 방식</h4>
<pre><code class="language-javascript">function a () {} // 함수 선언문, 함수명 a가 곧 변수명.
a(); // 실행 o

var b = function () {} // (익명) 함수 표현식. 함수명 b가 곧 변수명.
b(); // // 실행 ok

var c = function d () {} // 기명 함수 표현식. 변수명은 c, 함수명은 d.
c(); // 실행 ok
d(); // error (함수명은 오직 내부에서만 접근 가능)</code></pre>
<h3 id="🤔-함수-선언문과-함수-표현식을-사용할-때-주의해야-할-점">🤔 함수 선언문과 함수 표현식을 사용할 때 주의해야 할 점</h3>
<ul>
<li>호이스팅 차이
함수 선언문 :  호이스팅되어 코드의 최상단으로 끌어올려집니다. 따라서 선언 전에도 호출이 가능합니다.
함수 표현식 : 호이스팅되지 않으므로, 반드시 선언 후에 호출해야 합니다.</li>
<li>스코프 관리
함수 선언문 : 전역 스코프에서 사용될 경우, 같은 이름을 가진 함수나 변수와 충돌할 수 있습니다. 지역 스코프나 모듈화된 구조에서 사용하는 것이 좋습니다.</li>
<li>재할당 가능성
함수 표현식 : 변수에 할당되므로 재할당이 가능합니다. 이는 유연성을 제공하지만, 의도치 않은 오버라이딩에 주의해야 합니다.</li>
<li>성능 고려
함수 선언문 : 런타임 이전에 메모리에 할당되어 더 빠르게 호출될 수 있습니다.
함수 표현식 : 런타임에 할당되므로 미세한 성능 차이가 있을 수 있습니다. 하지만 대부분의 경우 이 차이는 무시할 만합니다.</li>
<li>코드 구조화
함수 표현식 : 클로저나 콜백 함수로 사용될 때 유용합니다.
함수 선언문 : 코드의 주요 기능을 정의할 때 더 적합할 수 있습니다.</li>
<li>즉시 실행 함수
함수 표현식 : 즉시 실행 함수(IIFE)로 사용될 수 있어, 독립적인 스코프를 생성하는 데 유용합니다.</li>
</ul>
<h3 id="✏️--2-3-2-스코프-스코프-체인-outerenvironmentreference">✏️  2-3-2 스코프, 스코프 체인, outerEnvironmentReference</h3>
<ul>
<li>스코프(scope) ? 식별자에 대한 유효범위.</li>
<li>스코프 체인(scope chain) ? 식별자의유효범위를 안에서부터 바깥으로 차례로 검색해나가는 것.</li>
</ul>
<p>이를 가능케 하는것 : LexicalEnvironment의 두 번째 수집 자료인<strong>outerEnvironmentReference</strong>이다.</p>
<h3 id="📒-스코프체인">📒 스코프체인</h3>
<ul>
<li>식별자의 유효범위를 안에서부터 바깥으로 차례로 검색해나가는 것을 의미합니다.</li>
<li>LexicalEnvironment의 OuterEnvironmentReference를 통해 구현됩니다.</li>
</ul>
<p>outerEnvironmentReference : 현재 호출된 함수가 선언될 당시의 LexicalEnvironment를 참조한다. 과거 시점인 '선언될 당시'에 주목 / 연결 리스트 형태
→ 선언하는 행위 : 콜 스택 상에서 어떤 실행 컨텍스트가 활성화된 상태일 때뿐</p>
<p>여러 스코프에서 동일한 식별자를 선언한 경우에는 <strong>무조건 스코프 체인 상에서 가장 먼저 발견된 식별자에만 접근 가능</strong></p>
<h4 id="✏️-le는-lexicalenvironment--e는-environmentrecord--o는-outerenvironmentreference--숫자는-코드-줄번호">✏️ L.E는 LexicalEnvironment / e는 environmentRecord / o는 outerEnvironmentReference / [숫자]는 코드 줄번호</h4>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/fb2f0a26-e895-4ef2-935c-62de3aaff293/image.png" /></p>
<p>전역 컨텍스트 → outer 컨텍스트 → inner 컨텍스트
점차 규모가 작아지는 반면 스코프 체인을 타고 접근 가능한 변수의 수는 늘어난다.</p>
<blockquote>
<p>변수의 은닉화 : 클래스 내부의 데이터를 외부에서 직접 접근하지 못하도록 숨기는 것을 의미.
inner 함수 내부에서 a 변수를 선언했기 때문에 전역 공간에서 선언한 동일한 이름의 a 변수에는 접근할 수 없음</p>
</blockquote>
<h3 id="✏️-전역-변수global-scope와-지역변수local-scope">✏️ 전역 변수(global scope)와 지역변수(local scope)</h3>
<p>전역 변수 : 전역 스코프에서 선언한 a와 outer.
지역 변수 : outer 함수 내부에서 선언한 inner와 inner 함수 내부에서 선언한 a.</p>
<h2 id="📌-2-4-this">📌 2-4 this</h2>
<ul>
<li>실행 컨텍스트가 생성될 때 함께 결정된다.</li>
<li>함수를 호출하는 방식에 따라 this가 가리키는 대상이 달라진다.</li>
</ul>