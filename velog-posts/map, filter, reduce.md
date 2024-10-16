<blockquote>
<p>💡고차 함수(Higher-order function)란?
함수를 인자로 받거나 함수를 반환하는 함수</p>
</blockquote>
<ol>
<li>특징:<ul>
<li>함수를 값처럼 다룰 수 있습니다.</li>
<li>추상화 수준을 높여 코드의 재사용성과 모듈화를 증가시킵니다.</li>
</ul>
</li>
<li>예시:<ul>
<li>JavaScript의 map, filter, reduce 등이 대표적인 고차 함수입니다.</li>
</ul>
</li>
<li>장점:<ul>
<li>코드의 추상화 수준을 높여 가독성을 향상시킵니다.</li>
<li>함수의 조합을 통해 복잡한 로직을 간결하게 표현할 수 있습니다.</li>
<li>코드의 재사용성을 높입니다.</li>
</ul>
</li>
<li>사용 사례:<ul>
<li>배열 조작: map, filter, reduce 등</li>
<li>함수 조합: compose, pipe 등</li>
<li>비동기 처리: Promise 체이닝</li>
</ul>
</li>
</ol>
<h2 id="📌-map">📌 map()</h2>
<ul>
<li>배열의 각 요소에 대해 주어진 함수를 호출하고, 그 결과로 새로운 배열을 생성합니다.</li>
</ul>
<pre><code class="language-jsx">구문: array.map(callback(currentValue[, index[, array]])[, thisArg])</code></pre>
<ul>
<li><p>예시:</p>
<pre><code class="language-jsx">  const numbers = [1, 2, 3, 4, 5];
  const doubled = numbers.map(num =&gt; num * 2);
  console.log(doubled); // [2, 4, 6, 8, 10]</code></pre>
</li>
</ul>
<h2 id="📌-filter">📌 filter()</h2>
<ul>
<li>주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환합니다.</li>
</ul>
<pre><code class="language-jsx">구문: array.filter(callback(element[, index[, array]])[, thisArg])</code></pre>
<ul>
<li><p>예시:</p>
<pre><code class="language-jsx">  const numbers = [1, 2, 3, 4, 5];
  const evenNumbers = numbers.filter(num =&gt; num % 2 === 0);
  console.log(evenNumbers); // [2, 4]*</code></pre>
</li>
</ul>
<h2 id="📌-reduce">📌 reduce()</h2>
<ul>
<li>배열의 각 요소에 대해 주어진 리듀서(reducer) 함수를 실행하고, 하나의 결과값을 반환합니다.</li>
</ul>
<pre><code class="language-jsx">구문: array.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])</code></pre>
<ul>
<li>예시:</li>
</ul>
<pre><code class="language-jsx">const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, cur) =&gt; acc + cur, 0);
console.log(sum); // 15</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/1b1bf08b-2276-4688-a120-43e1c9710cf5/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/1641f606-3495-480a-995f-1ea96d52ef54/image.png" /></p>
<h2 id="🤔-map-filter-reduce-차이점--">🤔 map, filter, reduce 차이점 ? ?</h2>
<h3 id="✏️-map">✏️ Map()</h3>
<p>배열의 각 요소를 변환하여 새로운 배열을 생성합니다.</p>
<ul>
<li>특징:<ul>
<li>원본 배열과 동일한 길이의 새 배열을 반환합니다.</li>
<li>각 요소에 대해 주어진 함수를 실행하고 그 결과를 새 배열에 담습니다.</li>
</ul>
</li>
</ul>
<pre><code class="language-jsx">[1, 2, 3].map(x =&gt; x * 2) =&gt; [2, 4, 6]</code></pre>
<h3 id="✏️-filter">✏️ Filter()</h3>
<p>주어진 조건을 만족하는 요소만을 추출하여 새로운 배열을 생성합니다.</p>
<ul>
<li>특징:<ul>
<li>원본 배열의 길이보다 같거나 작은 새 배열을 반환합니다.</li>
<li>각 요소에 대해 주어진 조건 함수를 실행하고, true를 반환하는 요소만 선택합니다.</li>
</ul>
</li>
</ul>
<pre><code class="language-jsx">[1, 2, 3, 4].filter(x =&gt; x % 2 === 0) =&gt; [2, 4]</code></pre>
<h3 id="✏️-reduce">✏️ Reduce</h3>
<p>배열의 모든 요소를 하나의 값으로 줄입니다.</p>
<ul>
<li>특징:<ul>
<li>배열의 요소들을 순회하며 누적된 결과값을 계산합니다.</li>
<li>최종적으로 단일 값을 반환합니다 (숫자, 문자열, 객체 등 어떤 타입이든 가능).</li>
</ul>
</li>
</ul>
<pre><code class="language-jsx">[1, 2, 3, 4].reduce((acc, cur) =&gt; acc + cur, 0) =&gt; 10</code></pre>
<h3 id="✅-주요-차이점">✅ 주요 차이점</h3>
<ul>
<li>Map은 변환, Filter는 선택, Reduce는 집계에 주로 사용됩니다.</li>
<li>Map과 Filter는 항상 새로운 배열을 반환하지만, Reduce는 단일 값을 반환합니다.</li>
<li>Map과 Filter는 원본 배열을 변경하지 않지만, Reduce는 최종 결과로 새로운 값을 생성합니다.</li>
</ul>
<h2 id="🤔-map-filter-reduce-함수의-성능-차이-">🤔 map, filter, reduce 함수의 성능 차이 ?</h2>
<h3 id="일반적인-성능-순서-reduce--map--filter">일반적인 성능 순서 reduce &gt; map &gt; filter</h3>
<h3 id="✏️-reduce-1">✏️ reduce</h3>
<ul>
<li>가장 빠른 성능을 보입니다.</li>
<li>한 번의 순회로 여러 작업을 수행할 수 있어 효율적입니다.</li>
<li>복잡한 로직을 구현할 수 있지만, 가독성이 떨어질 수 있습니다.</li>
</ul>
<h3 id="✏️-map-1">✏️ map</h3>
<ul>
<li>reduce보다는 느리지만 비교적 빠른 성능을 보입니다.</li>
<li>배열의 모든 요소를 변환할 때 효율적입니다.</li>
</ul>
<h3 id="✏️-filter-1">✏️ filter</h3>
<ul>
<li>세 함수 중 가장 느린 성능을 보입니다.</li>
<li>조건에 맞는 요소만 선택하므로, 결과 배열의 크기가 작아질 수 있습니다.</li>
</ul>
<ol>
<li>map과 filter를 함께 사용할 경우<ul>
<li>두 함수를 연속으로 사용하면 배열을 두 번 순회하게 되어 성능이 저하될 수 있습니다.</li>
<li>이 경우 reduce를 사용하여 한 번의 순회로 두 작업을 수행하는 것이 더 효율적일 수 있습니다.</li>
</ul>
</li>
<li>성능 차이의 실제 영향<ul>
<li>작은 배열에서는 성능 차이가 미미합니다.</li>
<li>대규모 데이터를 처리할 때 성능 차이가 두드러집니다.</li>
</ul>
</li>
<li>코드 가독성과 유지보수성<ul>
<li>성능만을 고려하기보다는 코드의 가독성과 유지보수성도 함께 고려해야 합니다.</li>
<li>간단한 작업의 경우 map이나 filter가 더 명확할 수 있습니다.</li>
</ul>
</li>
</ol>
<h3 id="결론">결론</h3>
<p>성능이 중요한 대규모 데이터 처리 상황에서는 reduce를 고려하되  일반적인 상황에서는 코드의 명확성과 가독성을 위해 map과 filter를 적절히 사용하는 것이 좋습니다.</p>
<p> 💻 reference</p>
<p>   <a href="https://joooing.tistory.com/entry/Javascript-%EB%82%B4%EC%9E%A5-%EA%B3%A0%EC%B0%A8-%ED%95%A8%EC%88%98">https://joooing.tistory.com/entry/Javascript-내장-고차-함수</a></p>