<h2 id="set">set()</h2>
<p>JavaScript Set은 <code>고유한 값의 컬렉션</code>입니다.</p>
<blockquote>
<p>💡 <strong>각 값은 Set에서 한 번만 나타날 수 있습니다. → 중복된 값을 없앨 수 있다.</strong></p>
</blockquote>
<p>값은 기본 값이거나 객체 등 모든 유형이 될 수 있다.</p>
<ul>
<li>set을 사용하는 방법<ul>
<li>배열을 전달하기<code>new Set()</code></li>
<li>빈 세트를 생성하고 <code>add()</code> 값을 추가하는 데 사용.</li>
</ul>
</li>
</ul>
<pre><code class="language-jsx">const mySet1 = new Set();</code></pre>
<pre><code class="language-jsx">// Use to remove duplicate elements from an array
const numbers = [2, 13, 4, 4, 2, 13, 13, 4, 4, 5, 5, 6, 6, 7, 5, 32, 13, 4, 5];

console.log([...new Set(numbers)]); // [2, 13, 4, 5, 6, 7, 32]</code></pre>
<h3 id="✅-주요-메서드">✅ 주요 메서드</h3>
<ul>
<li>add(value): 새로운 요소 추가</li>
<li>delete(value): 요소 삭제</li>
<li>has(value): 요소 존재 여부 확인</li>
<li>clear(): 모든 요소 제거</li>
<li>size: Set의 크기 반환</li>
</ul>
<pre><code class="language-javascript">let mySet = new Set();
mySet.add(1);
mySet.add("some text");
mySet.add({a: 1, b: 2});

console.log(mySet.has(1)); // true
console.log(mySet.size); // 3</code></pre>
<h3 id="✅-장점">✅ 장점</h3>
<ul>
<li>중복 제거가 자동으로 이루어집니다.</li>
<li>값의 존재 여부를 빠르게 확인할 수 있습니다.</li>
</ul>
<p>💻 reference</p>
<p><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set">https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set</a></p>