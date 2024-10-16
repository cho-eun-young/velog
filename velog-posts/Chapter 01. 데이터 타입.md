<hr />
<h2 id="📌-1-1-데이터-타입과-종류">📌 1-1 데이터 타입과 종류</h2>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/adaf4807-242f-4c61-a3a9-fe0193cad43a/image.png" /></p>
<h3 id="기본형primitive-type">기본형(primitive type)</h3>
<ul>
<li>숫자 (number)</li>
<li>문자열 (string)</li>
<li>불리언 (boolean)</li>
<li>null</li>
<li>undefined</li>
</ul>
<h3 id="참조형reference-type">참조형(reference type)</h3>
<ul>
<li>객체 (object)</li>
<li>배열 (Array)</li>
<li>함수 (function)</li>
<li>날짜 (Date)</li>
<li>정규표현식 (RegExp)</li>
<li>ES6 + (추가된) Map, WeakMap, Set, WeakSet </li>
</ul>
<h3 id="기본형과-참조형을-구분하는-기준--">기본형과 참조형을 구분하는 기준 ? ?</h3>
<ul>
<li>기본형 : 값이 담긴 주솟값을 바로 복제</li>
<li>참조형 : 값이 담긴 주솟값들로 이루어진 묶음을 가리키는 주솟값을 복제</li>
</ul>
<p>** 기본형은 불변성 (immutability)을 띈다.</p>
<hr />
<h2 id="📌-1-2-데이터-타입에-관한-배경지식">📌 1-2 데이터 타입에 관한 배경지식</h2>
<h3 id="1-2-1-메모리와-데이터">1-2-1 메모리와 데이터</h3>
<p>메모리 : 매우 많은 비트(0,1)로 구성되어 있다. </p>
<ul>
<li>각 비트는 고유한 식별자 (unique identifier)를 통해 위치 확인 할 수 있다.</li>
</ul>
<p>하지만 0이나 1만 표현할 수 있는 비트 단위로 위치 확인은 비효율적이다.
적정한 공간을 묶는 바이트(byte)라는 단위가 생겼다.</p>
<blockquote>
<p>1bit = 0 or 1
1byte = 8bit</p>
</blockquote>
<p>비트나 바이트의 식별자로 위치를 파악할 수 있다.</p>
<blockquote>
<p>모든 데이터는 바이트 단위의 식별자, 
즉 메모리 주소값 (memory address)을 통해 서로 구분하고 연결 할 수 있다 !</p>
</blockquote>
<h3 id="1-2-2-식별자와-변수">1-2-2 식별자와 변수</h3>
<ul>
<li>변수 (variable) : 변할 수 있는 데이터</li>
<li>식별자 (identifier) : 어떤 데이터를 식별하는 이름. 변수명</li>
</ul>
<hr />
<h2 id="📌-1-3-변수-선언과-데이터-할당">📌 1-3 변수 선언과 데이터 할당</h2>
<h3 id="1-3-1-변수-선언">1-3-1 변수 선언</h3>
<pre><code class="language-javascript">var a; // 변수 선언</code></pre>
<p>변수 선언 : 변경 가능한 데이터가 담길 수 있는 공간
<img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/aa311501-c7ea-4624-afa6-651091cd6a38/image.png" /></p>
<ul>
<li>비어있는 공간 또는 그릇 확보 -&gt; 임의로 1003번 지정 : 식별자 a라고 지정</li>
</ul>
<h3 id="1-3-2-데이터-할당">1-3-2 데이터 할당</h3>
<pre><code class="language-javascript">var a; // 변수선언
a = 'abc'; // 변수 a에 데이터 할당

var a = 'abc'; // 변수 선언과 할당을 한 문장으로 표현</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/dca3dee1-17e6-49b4-a19d-5fc6b9a66ebb/image.png" /></p>
<h4 id="데이터-할당-흐름">데이터 할당 흐름</h4>
<ol>
<li>변수 영역에 빈공간(@1003)확보</li>
<li>확보한 공간을 식별자 a로 지정 </li>
<li>데이터 영역의 빈공간 (@5004)에 문자열 'abc'저장</li>
<li>변수 영역에 a라는 식별자 검색(@1003)</li>
<li>앞서 저장한 문자열의 주소 (@5004)를 @1003의 공간에 대입</li>
</ol>
<h4 id="변수-영역에-값을-직접-대입하지-않는-이유-">변수 영역에 값을 직접 대입하지 않는 이유? ?</h4>
<ul>
<li>데이터 변환을 자유롭게 할 수 있음</li>
<li>메모리 효율적으로 관리</li>
</ul>
<hr />
<h2 id="📌-1-4-기본형-데이터와-참조형-데이터">📌 1-4 기본형 데이터와 참조형 데이터</h2>
<h3 id="1-4-1-불변값">1-4-1 불변값</h3>
<h4 id="변수variable와-상수constant를-구분하는-성질-">변수(variable)와 상수(constant)를 구분하는 성질 ?</h4>
<ul>
<li>변경 가능성 구분 (대상 : 변수 영역 메모리 - 한번 데이터 할당이 이뤄진 변수 공간에 다른 데이터를 재할당할 수 있는지 여부가 관건)</li>
<li>불변성 여부 구분 (대상 : 데이터 영역 메모리 - 기본형 데이터 숫자, 문자열, boolean, null, undefined, Symbol)</li>
</ul>
<h3 id="1-4-2-가변값">1-4-2 가변값</h3>
<pre><code class="language-javascript">var obj1 = {
  a : 1,
  b : 'bbb',
};</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/c6b28fa4-64f0-442e-bad5-936c2a503402/image.png" /></p>
<h4 id="참조형-데이터를-변수에-할당하는-과정">참조형 데이터를 변수에 할당하는 과정</h4>
<ol>
<li>변수 영역의 빈공간(@5001)확보, 주소 이름 obj1 지정</li>
<li>임의의 데이터 저장공간(@5001)에 데이터 저장하려고 보니 여러 개의 프로퍼티로 이뤄진 데이터 그룹임. 그룹 내부의 프로퍼티들을 저장하기 위해 별도의 변수 영역 마련. 그 영역의 주소 (@7103 ~ ?)를 @5001에 저장</li>
<li>@7103 및 @7104에 각각 a와 b라는 프로퍼티 이름 지정</li>
<li>데이터 영역에서 숫자 1검색. 검색 결과 없으므로 임의로 @5003에 저장. 이 주소를 @7103에 저장. 문자열 'bbb' 임의로 @5004저장. 이 주소를 @7104에 저장</li>
</ol>
<h4 id="참조형-데이터의-프로퍼티-재할당">참조형 데이터의 프로퍼티 재할당</h4>
<pre><code class="language-javascript">var obj1 = {
  a : 1,
  b : 'bbb',
};
obj1.a = 2;</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/0a90bfbf-1d98-4bde-9fc6-389d50c5091e/image.png" /></p>
<ol>
<li>데이터 영역에서 2 검색</li>
<li>검색 결과 없으니 빈공간 @5005저장. 주소를 @7103저장.</li>
<li>obj1이 바라보고 있는 주소는 @5001로 변하지 않았음. '새로운 객체'가 만들어진 것이 아니라, 기존의 객체 내부의 값만 바뀐 것! !</li>
</ol>
<h4 id="중첩-객체-nested-object">중첩 객체 (nested object)</h4>
<pre><code class="language-javascript">var obj = {
  x : 3,
  arr : [3, 4, 5]
}; 
</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/99e2bb08-1f17-486e-8d87-309bdb9ef334/image.png" /></p>
<h4 id="중첩된-참조형-데이터-객체-프로퍼티-할당">중첩된 참조형 데이터 (객체) 프로퍼티 할당</h4>
<ol>
<li>변수 영역의 빈공간 (@1002)확보. 주소 이름 obj로 지정</li>
<li>여러 개의 변수와 값들을 모아놓은 그룹(객체). 각 변수 (프로퍼티)들을 저장하기 위해 별도 변수 영역을 마련(@7103 ~ ?) 주소 @5001 저장.</li>
<li>@7103에 이름 x. @7104에 이름 arr를 지정.</li>
<li>데이터 영역에서 3검색. 없으므로 임의로 @5002에 저장. 이 주소를 @7103에 저장.</li>
<li>@7104 영역에 배열로서 데이터 그룹. 내부 프로퍼티들을 저장하기 위해 별도 변수 영역 (@8104~?)를     @5003에 저장한 다음, @5003 @7104에 저장.</li>
<li>배열 요소 총 3개이므로 3개 변수 공간 확보. 각각 인덱스 부여 (0,1,2)</li>
<li>데이터 영역에 숫자 3을 검색해서 (@5002) 그 주소를 @8104에 저장.</li>
<li>데이터 영역에 숫자 4가 없으므로 @5004에 저장. 이 주소를 @8105에 저장.</li>
<li>데이터 영역 숫자 5가 없으므로 @5005에 저장. 이 주소를 @8106에 저장.</li>
</ol>
<h4 id="objarr1을-검색하고자-하면-메모리에서는-다음과-같은-검색과정을-거친다">obj.arr[1]을 검색하고자 하면 메모리에서는 다음과 같은 검색과정을 거친다.</h4>
<ol>
<li>obj 검색 1: obj라는 식별자를 가진 주소를 찾는다(@1002)</li>
<li>obj 검색 2: 값이 주소이므로 그 주소로 이동(@5001)</li>
<li>obj 검색 3: 값이 주소이므로 그 주소로 이동(@7130 ~ ?)</li>
<li>obj.arr 검색1 : arr이라는 식별자를 가진 주소 찾음(@7104)</li>
<li>obj.arr 검색2 : 값이 주소이므로 그 주소로 이동(@5003)</li>
<li>obj.arr 검색3: 값이 주소이므로 그 주소로 이동(@8104 ~?)</li>
<li>obj.arr[1] 검색 1: 인덱스 1에 해당하는 주소 찾음(@8105)</li>
<li>obj.arr[1] 검색 2: 값이 주소이므로 그 주소로 이동(@5004)</li>
<li>obj.arr[1] 검색 3: 값이 숫자형 데이터이므로 4 반환.</li>
</ol>
<h4 id="이상태에서-재할당-명령을-내리면--">이상태에서 재할당 명령을 내리면 ? ?</h4>
<pre><code class="language-javascript">obj.arr = 'str';</code></pre>
<p>@5006에 문자열 'str'를 저장하고, 그 주소를 @7104에 저장합니다. 그러면 @5003은 더 이상 자신의 주소를 참조하는 변수가 하나도 없게 됩니다. <strong>어떤 데이터에 대해 자신의 주소를 참조하는 변수의 개수를 참조 카운트라고 합니다.</strong> @5003의 참조 카운트는 @7104에 저장돼 있던 시점까지는 1이었다가 <strong>@7104에 @5006이 저장되는 순간 0이 됩니다.</strong> 참조 카운트가 0인 메모리 주소는 가비지 컬렉터(GC)의 수거 대상이 됩니다. 가비지 컬렉터는 런타임 환경에 따라 특정 시점이나 메모리 사용량이 포화 상태에 임박할 때마다 자동으로 수거합니다. 수거된 메모리는 다시 새로운 값을 할당할 수 있는 빈 공간이 됩니다.</p>
<p>즉, @5003은 참조 카운트가 0이 됨에 따라 GC대상이 되고, 이후 언젠가 담겨 있던 데이터인 '@8104 ~? "라는 값이 사라집니다. 이 과정에서 연쇄적으로 <strong>@8104 ~ ? 의 각 데이터들의 참조 카운트가 0이 되고, 이들 역시 GC 대상이 되어 함께 사라 질 것입니다</strong>.
<img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/3bd2bd89-3aae-43b9-94bb-65590e5096c5/image.jpg" /></p>
<h3 id="1-4-3-변수-복사-비교">1-4-3 변수 복사 비교</h3>
<h4 id="기본형-데이터와-참조형-데이터-차이">기본형 데이터와 참조형 데이터 차이</h4>
<pre><code class="language-javascript">var a = 10; // 기본형 데이터
var b = a;

var obj1 = {c: 10, d: 'ddd'}; // 참조형 데이터
var obj2 = obj1;</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/29db10a2-8747-4864-b61d-877b584c020f/image.png" /></p>
<ul>
<li><p>변수 복사 시 복사하려는 변수의 식별자를 검색해 해당 변수의 값을 찾아 대입</p>
</li>
<li><p>복사 과정은 기본형/참조형 데이터 모두 같은 주소를 바라보게 된다는 점에서 동일함</p>
</li>
<li><p>복사 과정은 동일하지만 데이터 할당 과정에서 이미 차이가 있기 때문에 변수 복사 이후의 동작에도 큰 차이 발생함</p>
</li>
</ul>
<pre><code class="language-javascript">var a = 10; // 기본형 데이터
var b = a;

var obj1 = {c: 10, d: 'ddd'}; // 참조형 데이터
var obj2 = obj1;

b = 15;
obj2.c = 20; </code></pre>
<h4 id="변수-복사-이후-값을-변경했을-때-차이점">변수 복사 이후 값을 변경했을 때 차이점</h4>
<p>기본형 데이터를 복사한 변수의 값을 변경하게 되면 해당 변수의 값이 달라짐. 즉 데이터 영역의 다른 주소를 가리키게 됨.</p>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/1b7568fe-1228-4ee9-8535-eb0518ef0dd5/image.png" /></p>
<p>a랑 b는 이제 다른 값을 바라보게 됨. (a !== b)</p>
<p>하지만 ! ! 참조형 데이터를 복사한 변수의 프로퍼티 값 변경 시에는 해당 변수의 값이 그대로임. 여전히 같은 값을 가지고 있음. (obj1 === obj2)</p>
<pre><code class="language-javascript">var a = 10; // 기본형 데이터
var b = a;

var obj1 = {c: 10, d: 'ddd'}; // 참조형 데이터
var obj2 = obj1;

b = 15;
obj2 = {c: 20, d: 'ddd'; </code></pre>
<p>참조형 데이터를 복사한 변수의 프로퍼티 값이 아니라 객체 자체를 변경했을 때는 메모리의 데이터 영역에 새로운 공간에 새로운 객체가 저장되고 그 주소를 해당 변수의 변수 영역 위치에 저장. 즉 기존의 복사 대상과 값이 달라짐.</p>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/de074a41-b973-4260-8613-f48611fd71c3/image.png" /></p>
<p>참조형 데이터가 '가변값'이라고 설명할 때의 '가변'은 참조형 데이터 자체를 변경할 경우가 아니라 그 내부의 프로퍼티를 변경할 때만 성립.</p>
<hr />
<h2 id="📌-1-5-불변-객체">📌 1-5 불변 객체</h2>
<h3 id="1-5-1-불변-객체를-만드는-간단한-방법">1-5-1 불변 객체를 만드는 간단한 방법</h3>
<h4 id="불변-객체를-만드는-간단한-방법">불변 객체를 만드는 간단한 방법</h4>
<p>내부 프로퍼티가 아니라 데이터 자체를 변경하고자 하면 기본형 데이터와 마찬가지로 기존 데이터가 변하지 않는다. 따라서 내부 프로퍼티를 변경할 때마다 매번 새로운 객체를 만들어 재할당하기로 규칙을 정하거나 새로운 객체를 만드는 도구를 활용한다면 객체도 불변성을 확보할 수 있다.</p>
<h4 id="불변-객체가-필요한-상황--">불변 객체가 필요한 상황 ? ?</h4>
<p>값으로 전달받은 객체에 변경을 가하더라도 원본 객체는 변하지 않아야 하는 경우에 필요 !</p>
<pre><code class="language-javascript">var user = {
        name :  'Jaenam'
        gender : 'male'
 }

 var changeName = function(user, newName){
    var newUser = user;
    newUser.name = newName;
   return newUser;
}

var user2 = changeName(user, 'Jung');

if(user !== user2){
    console.log('유저 정보가 변경되었습니다.');
}

console.log(user.name, user2.name); // Jung Jung
console.log(user === user2) ; //true</code></pre>
<p>기존 정보를 복사해서 새로운 객체를 반환하는 함수(얕은 복사) </p>
<pre><code class="language-javascript">var copyObject = function(target) {
  var result = {};
  for (var prop in target) {
    result[prop] = target[prop];
  }
  return result;
}</code></pre>
<p>copyObject를 이용한 객체 복사</p>
<pre><code class="language-javascript">var user = {
  name: 'Jaenam',
  gender: 'male'
};

var user2 = copyObject(user);
user2.name = 'Jung';

if (user1= user2) {
  console.log('유저 정보가 변경돠었습니다.'); // 결과 : 유저 정보가 변경돠었습니다.
}

console.log(user.name, user2.name); // Jaenam Jung
console.log(user == user2); // false</code></pre>
<p>user 객체 내부의 변경이 필요할 때 무조건 copyObject 함수를 사용하기로 합의하고 그 규칙을 지킨다는 전제하에서 user 객체가 불변 객체라고 볼 수 있다.</p>
<h3 id="1-5-2-얕은-복사와-깊은-복사">1-5-2 얕은 복사와 깊은 복사</h3>
<ul>
<li>얕은 복사 : 바로 아래 단계의 값만 복사하는 방법 - 주소값만 복사한다는 의미</li>
<li>깊은 복사 : 내부의 모든 값들을 하나하나 찾아서 전부 복사하는 방법</li>
</ul>
<h4 id="중첩된-객체에-대한-얕은-복사">중첩된 객체에 대한 얕은 복사</h4>
<pre><code class="language-javascript">var user = {
  name: 'Jaenam',
  urls: {
    portfolio: 'http://github.com/abc',
    blog: 'http://blog.com/abc',
    facebook: 'http://facebook.com/abc'
  }
};
var user2 = copyObject(user);

user2.name = 'Jung';
console.log(user.name === user2.name); // false

user.urls.portfolio = 'http://portfolio.com';
console.log(user.urls.portfolio === user2.urls.portfolio); // true

user.urls.blog = '';
console.log(user.urls.blog === user2.urls.blog); // true</code></pre>
<blockquote>
<p>user 객체에 직접 속한 프로퍼티에 대해서는 복사해서 완전히 새로운 데이터가 만들어진 반면, 한 단계 더 들어간 urls의 내부 프로퍼티들은 기존 데이터를 그대로 참조</p>
</blockquote>
<h4 id="중첩된-객체에-대한-깊은-복사">중첩된 객체에 대한 깊은 복사</h4>
<pre><code class="language-javascript">var user2 = copyObject(user);
user2.urls = copyObject(user.urls);

user.urls.portfolio = 'http://portfolio.com';
console.log(user.urls.portfolio === user2.urls.portfolio); // false

user.urls.blog = '';
console.log(user.urls.blog === user2.urls.blog); // false</code></pre>
<blockquote>
<p>객체를 복사할 때 객 내부의 모든 값을 복사해서 완전히 새로운 데이터를 만들고자 할 때, 기본형 데이터일 경우에는 그대로 복사하면 되지만 참조형 데이터는 다시 그 내부의 프로퍼티들을 복사해야 함</p>
</blockquote>
<h4 id="json을-활용한-간단한-깊은-복사">JSON을 활용한 간단한 깊은 복사</h4>
<p>(메서드(함수)나 숨겨진 프로퍼티인 <strong>proto</strong>나 getter/setter 등과 같이 JSON으로 변경할 수 없는 프로퍼티들은 모두 무시)</p>
<pre><code class="language-javascript">var copyObjectViaJSON = function (target) {
  return JSON.parse(JSON.stringify(target));
};
var obj = {
  a: 1,
  b: {
    c: null,
    d: [1, 2],
    func1: function () {console.log(3);}
  },
  func2: function () {console.log(4);}
};
var obj2 = copyObjectViaJSON(obj);

obj.a = 3;
obj.b.c = 4;
obj.b.d[1] = 3;

console.log(obj); // {a: 1, b: {c: null, d: [1,3], func1: f() }, func2: f() }
console.log(obj2); // {a: 3, b: {c: 4, d: [1,2]}</code></pre>
<hr />
<h2 id="📌-1-6-undefined와-null">📌 1-6 undefined와 null</h2>
<h3 id="undefined">undefined</h3>
<ul>
<li><p>사용자가 명시적으로 지정할 수도 있지만 값이 존재하지 않을 때 자바스크립트 엔진이 자동으로 부여하는 경우도 있음</p>
</li>
<li><p>자바스크립트 엔진이 사용자가 응당 어떤 값을 지정할 것이라고 예상되는 상황임에도 실제로는 그렇게 하지 않았을 때 undefined 반환</p>
</li>
<li><p>자바스크립트 엔진이 사용자가 응당 어떤 값을 지정할 것이라고 예상되는 상황</p>
<p> 1) 값을 대입하지 않은 변수, 즉 데이터 영역의 메모리 주소를 지정하지 않은 식별자에 접근할 때(변수 선언시 자동으로 undefined 할당하는 것이 아니라 이후 해당 변수에 접근하고자 할 때 비로소 undefined를 반환하는 것)</p>
<p> 2) 객체 내부의 존재하지 않는 프로퍼티에 접근하려고 할 때</p>
<p> 3) return 문이 없거나 호출되지 않는 함수의 실행 결과</p>
</li>
<li><p>'비어있는 요소'와 'undefined를 할당한 요소'는 출력 결과부터 다름. '비어있는 요소'는 순회와 관련된 많은 배열 메서드들의 순회대상에서 제외됨. undefined는 비록 비어있음을 의미하긴 하지만 하나의 값으로 동작하기 때문에 이때의 프로퍼티나 배열의 요소는 고유의 키값(프로퍼티 이름)이 실존하게 되고, 따라서 순회의 대상이 될 수 있음. </p>
</li>
<li><p>값으로써 어딘가에 할당된 undefined는 실존하는 데이터인 반면, 자바스크립트 엔진이 반환해주는 undefined는 문자 그대로 값이 없음을 의미.</p>
</li>
</ul>
<h3 id="null">null</h3>
<p>'비어있음'을 명시적으로 나타내고 싶을 때는 undefined가 아닌 null을 써라. </p>
<p>위 규칙을 따르는 한 undefined가 "값을 대입하지 않은 변수에 접근하고자 할때 자바스크립트 엔진이 반환해주는 값"으로서만 존재 가능.</p>
<h4 id="undefined와-null의-비교">undefined와 null의 비교</h4>
<pre><code class="language-javascript">var n = null;
console.log(typeof n); // object

console.log(n == undefined); // ture
console.log(n == null); // ture


console.log(n === undefined); // false
console.log(n === null); // ture</code></pre>
<h4 id="주의점-typeof-null이-object임-자바스크립트-자체-버그">주의점: typeof null이 object임. (자바스크립트 자체 버그)</h4>
<pre><code class="language-javascript">var n = null;
console.log(typeof n); // object

console.log(n == undefined); // true
console.log(n == null); // true

console.log(n === undefined); // false
console.log(n === null); // true</code></pre>
<p>=== 일치 연산자(identity operator)를 써야만 정확히 판별 가능하다.</p>
<hr />
<h2 id="📌-1-7-정리">📌 1-7 정리</h2>
<p>자바스크립트 데이터 타입 크게 <strong>기본형</strong>, <strong>참조형</strong>이 있다.
기본형 : 불변값
참조형 : 가변값</p>
<p><strong>변수</strong> : 변경 가능한 데이터가 담길 수 있는 공간.
<strong>식별자</strong> : 그 변수의 이름</p>
<p>변수 선언하면 메모리의 빈 공간에 식별자 지정. 그 공간에 자동으로 undefined 할당함. 이후 기본형 데이터 할당하려고 하면 별도의 공간에 데이터 저장, 그 공간에 주소를 변수의 값 영역에 할당.</p>
<p>참조형 데이터 할당하려고 하면 확보된 주소를 변수에 연결. 확보한 변수 영역에 각 프로퍼티의 식별자 저장. 각 데이터 별도의 공간에 저장해서 주소와 식별자들과 매칭. </p>
<p>차이가 생긴이유는 참조형 데이터가 여러개의 프로퍼티(변수)를 모은 '그룹' 이기 때문.
이 차이로 참조형 데이터를 '가변값'으로 여겨야만 하는 상황이 발생.</p>
<p>참조형 데이터를 불변값으로 사용하는 방법 : 내부 프로퍼티들을 일일이 복사하면된다.(깊은 복사)
또는 라이브러리 사용. </p>
<p>자바스크립트에서 "없음"을 나타내는 두 가지 값.</p>
<ul>
<li>'<strong>undefined</strong>'는 어떤 변수에 값이 존재하지 않음을 의미</li>
<li>'<strong>null</strong>'은 사용자가 명시적으로 '없음'을 표현하기 위해 대입한 값.</li>
</ul>
<p>본래의 의미에 따라 사용자가 없음을 표현하기 위해 명시적으로 undefined 대입하는 것은 지양해야함.</p>
<hr />