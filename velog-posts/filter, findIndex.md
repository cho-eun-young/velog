<p>JS기초 정리하기</p>
<p><a href="https://school.programmers.co.kr/learn/courses/30/lessons/12919">https://school.programmers.co.kr/learn/courses/30/lessons/12919</a></p>
<p>-&gt; 서울에서 김서방 찾기</p>
<h3 id="for문">for문</h3>
<h3 id="filtername-index">filter(name, index)</h3>
<h3 id="findindex">findIndex</h3>
<blockquote>
<p>순으로 간결하게 코드를 작성했다.
처음엔 간단하게 for문만으로도 작성할 수 있었지만 계속해서 다른 메서드를 이용하지 않는다면 나의 것으로 얻어갈 수 없다고 생각하였다.
그래서 filter를 사용해 보았다.</p>
</blockquote>
<h2 id="filter-구문">filter 구문</h2>
<blockquote>
<p>filter(callbackFn)
filter(callbackFn, thisArg)</p>
</blockquote>
<h3 id="매개변수">매개변수</h3>
<h3 id="callbackfn">callbackFn</h3>
<p>배열의 각 요소에 대해 실행할 함수입니다. 결과 배열에 요소를 유지하려면 참 값을 반환하고 그렇지 않으면 거짓 값을 반환해야 합니다. 이 함수는 다음 인수를 사용하여 호출됩니다.</p>
<h3 id="element">element</h3>
<p>배열에서 처리 중인 현재 요소.</p>
<h3 id="index">index</h3>
<p>배열에서 처리 중인 현재 요소의 인덱스.</p>
<h3 id="array">array</h3>
<p>filter()가 호출된 배열.</p>
<h2 id="findindex-와-indexof">findIndex 와 indexOf</h2>
<p>findIndex()와 indexOf()는 모두 JavaScript에서 배열의 요소를 찾는 메서드입니다. 하지만 사용 방식과 기능이 다릅니다.</p>
<h3 id="1-indexof">1. indexOf()</h3>
<h4 id="정의">정의:</h4>
<p>배열에서 특정 요소의 첫 번째 인덱스를 반환합니다.</p>
<h4 id="사용법">사용법:</h4>
<pre><code class="language-javascript">
const arr = [1, 2, 3, 4];
const index = arr.indexOf(3); // 2</code></pre>
<h4 id="특징">특징:</h4>
<p>기본적으로 원시 값(primitive value)만을 찾습니다.</p>
<p>찾는 값이 없으면 -1을 반환합니다.</p>
<p>대소문자를 구분합니다.</p>
<h3 id="2-findindex">2. findIndex()</h3>
<h4 id="정의-1">정의:</h4>
<p>주어진 테스트 함수를 만족하는 배열의 첫 번째 요소의 인덱스를 반환합니다.</p>
<h4 id="사용법-1">사용법:</h4>
<pre><code class="language-javascript">const arr = [1, 2, 3, 4];
const index = arr.findIndex(element =&gt; element &gt; 2); // 2</code></pre>
<h4 id="특징-1">특징:</h4>
<p>콜백 함수를 사용하여 조건에 맞는 요소를 찾습니다.</p>
<p>찾는 요소가 없으면 -1을 반환합니다.</p>
<p>배열의 각 요소에 대해 조건을 평가할 수 있습니다.</p>
<p>요약</p>
<p>특정 값을 찾고 싶다면: indexOf()</p>
<p>조건에 맞는 요소를 찾고 싶다면: findIndex()</p>