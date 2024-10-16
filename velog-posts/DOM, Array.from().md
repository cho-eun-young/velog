<h2 id="✅-createelement">✅ createElement</h2>
<ul>
<li><p>요소 생성: 원하는 HTML 요소를 생성할 수 있습니다.</p>
</li>
<li><p>속성 설정: 생성한 요소에 속성을 추가하거나 수정할 수 있습니다.</p>
</li>
</ul>
<pre><code class="language-javascript">newDiv.setAttribute('class', 'my-class');</code></pre>
<p>이벤트 리스너 추가: 생성한 요소에 이벤트 리스너를 추가할 수 있습니다.</p>
<pre><code class="language-javascript">newDiv.addEventListener('click', () =&gt; {
    alert('클릭되었습니다!');
});</code></pre>
<p>자식 요소 추가: 다른 요소를 자식으로 추가할 수 있습니다.</p>
<pre><code class="language-javascript">const newSpan = document.createElement('span');
newSpan.textContent = '이것은 자식 요소입니다.';
newDiv.appendChild(newSpan);</code></pre>
<h2 id="✅-1-removechild">✅ 1. removeChild</h2>
<p>removeChild 메서드는 특정 부모 요소에서 자식 요소를 제거합니다.</p>
<pre><code class="language-javascript">parentElement.removeChild(childElement);</code></pre>
<ul>
<li><p>parentElement: 자식 요소를 제거할 부모 요소.</p>
</li>
<li><p>childElement: 제거할 자식 요소.</p>
</li>
</ul>
<pre><code class="language-javascript">// div 요소 생성 및 추가
const parentDiv = document.createElement('div');
const childDiv = document.createElement('div');
childDiv.textContent = '이 자식 요소를 제거합니다.';
parentDiv.appendChild(childDiv);
document.body.appendChild(parentDiv);</code></pre>
<pre><code class="language-javascript">// 자식 요소 제거
parentDiv.removeChild(childDiv);</code></pre>
<h2 id="✅-2-replacechild">✅ 2. replaceChild</h2>
<p>replaceChild 메서드는 특정 부모 요소에서 기존 자식 요소를 새로운 요소로 교체합니다.</p>
<pre><code class="language-javascript">parentElement.replaceChild(newChild, oldChild);</code></pre>
<ul>
<li><p>parentElement: 자식 요소를 교체할 부모 요소.</p>
</li>
<li><p>newChild: 새로 추가할 요소.</p>
</li>
<li><p>oldChild: 교체할 기존 자식 요소.</p>
</li>
</ul>
<pre><code class="language-javascript">// div 요소 생성 및 추가
const parentDiv = document.createElement('div');
const oldChildDiv = document.createElement('div');
oldChildDiv.textContent = '이 자식 요소를 교체합니다.';
parentDiv.appendChild(oldChildDiv);
document.body.appendChild(parentDiv);</code></pre>
<pre><code class="language-javascript">// 새 자식 요소 생성
const newChildDiv = document.createElement('div');
newChildDiv.textContent = '새로운 자식 요소로 교체되었습니다.';</code></pre>
<pre><code class="language-javascript">// 자식 요소 교체
parentDiv.replaceChild(newChildDiv, oldChildDiv);</code></pre>
<ul>
<li><p>removeChild: 특정 부모 요소에서 자식 요소를 제거합니다.</p>
</li>
<li><p>replaceChild: 특정 부모 요소에서 기존 자식 요소를 새로운 요소로 교체합니다.</p>
</li>
</ul>
<h2 id="✅-arrayfrom">✅ Array.from()</h2>
<blockquote>
<p>Array.from()은 JavaScript에서 배열(Array)을 생성하는 메서드로, 유사 배열 객체(array-like objects)나 반복 가능한 객체(iterable objects)로부터 새로운 배열을 생성합니다. 이 메서드는 배열을 쉽게 생성하고 변환할 수 있도록 도와줍니다.</p>
</blockquote>
<pre><code class="language-javascript">Array.from(arrayLike, mapFunction, thisArg);</code></pre>
<ul>
<li><p>arrayLike: 배열로 변환할 유사 배열 객체나 반복 가능한 객체.</p>
</li>
<li><p>mapFunction (선택적): 생성된 배열의 각 요소에 적용할 함수.</p>
</li>
<li><p>thisArg (선택적): mapFunction에서 this로 사용할 값.</p>
</li>
</ul>
<h3 id="유사-배열-객체-변환">유사 배열 객체 변환</h3>
<pre><code class="language-javascript">const str = 'hello';
const arr = Array.from(str);
console.log(arr); // 출력: ['h', 'e', 'l', 'l', 'o']</code></pre>
<h3 id="반복-가능한-객체-변환">반복 가능한 객체 변환</h3>
<pre><code class="language-javascript">const set = new Set([1, 2, 3]);
const arr = Array.from(set);
console.log(arr); // 출력: [1, 2, 3]</code></pre>
<h3 id="맵-함수-사용">맵 함수 사용</h3>
<pre><code class="language-javascript">const numbers = [1, 2, 3, 4];
const doubled = Array.from(numbers, x =&gt; x * 2);
console.log(doubled); // 출력: [2, 4, 6, 8]</code></pre>
<h3 id="thisarg-사용">thisArg 사용</h3>
<pre><code class="language-javascript">const obj = {
    multiplier: 2
};</code></pre>
<pre><code class="language-javascript">const numbers = [1, 2, 3, 4];
const doubled = Array.from(numbers, function(x) {
    return x * this.multiplier;
}, obj);

console.log(doubled); // 출력: [2, 4, 6, 8]</code></pre>