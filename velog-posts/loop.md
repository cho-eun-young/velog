<h2 id="1-for">1. for</h2>
<h3 id="용도">용도:</h3>
<p>일반적인 반복문으로, 인덱스를 통해 배열의 요소에 접근할 수 있습니다.</p>
<h3 id="구문">구문:</h3>
<pre><code class="language-javascript">for (let i = 0; i &lt; array.length; i++) {
    // 코드
}
</code></pre>
<h3 id="특징">특징:</h3>
<p>반복 횟수를 명시적으로 지정할 수 있습니다.</p>
<pre><code class="language-javascript">fruits = ['사과', '바나나', '오렌지'];
for (let i = 0; i &lt; fruits.length; i++) {
    console.log(fruits[i]);
}</code></pre>
<h2 id="2-forin">2. for...in</h2>
<h3 id="용도-1">용도:</h3>
<p>객체의 속성을 반복할 때 사용됩니다.</p>
<h3 id="구문-1">구문:</h3>
<pre><code class="language-javascript">for (let key in object) {
    // 코드
}</code></pre>
<h3 id="특징-1">특징:</h3>
<p>배열의 인덱스도 반복할 수 있지만, 배열에 적합하지 않습니다.</p>
<pre><code class="language-javascript">person = { name: '홍길동', age: 30 };
for (let key in person) {
    console.log(key + ': ' + person[key]);
}</code></pre>
<h2 id="3-while">3. while</h2>
<h3 id="용도-2">용도:</h3>
<p>조건이 참인 동안 반복합니다.</p>
<h3 id="구문-2">구문:</h3>
<pre><code class="language-javascript">while (condition) {
    // 코드
}</code></pre>
<h3 id="특징-2">특징:</h3>
<p>반복 횟수가 불확실할 때 유용합니다.</p>
<pre><code class="language-javascript">i = 0;
while (i &lt; 3) {
    console.log(i);
    i++;
}</code></pre>
<h2 id="4-dowhile">4. do...while</h2>
<h3 id="용도-3">용도:</h3>
<p>최소 한 번은 실행한 후 조건을 검사하여 반복합니다.</p>
<h3 id="구문-3">구문:</h3>
<pre><code class="language-javascript">do {
    // 코드
} while (condition);
</code></pre>
<p>특징: 조건이 false여도 첫 번째 반복은 실행됩니다.</p>
<pre><code class="language-javascript">i = 0;
do {
    console.log(i);
    i++;
} while (i &lt; 3);</code></pre>
<h2 id="5-foreach">5. forEach</h2>
<h3 id="용도-4">용도:</h3>
<p>배열의 각 요소를 반복하는 메서드입니다.</p>
<h3 id="구문-4">구문:</h3>
<pre><code class="language-javascript">forEach(function(element) {
    // 코드
});
</code></pre>
<h3 id="특징-3">특징:</h3>
<p>배열에만 사용되며, 반환값이 없습니다.</p>
<pre><code class="language-javascript">fruits = ['사과', '바나나', '오렌지'];
fruits.forEach(function(fruit) {
    console.log(fruit);
});</code></pre>
<h2 id="6-map">6. map</h2>
<h3 id="용도-5">용도:</h3>
<p>배열의 각 요소를 변환하여 새로운 배열을 생성합니다.</p>
<h3 id="구문-5">구문:</h3>
<pre><code class="language-javascript">newArray = array.map(function(element) {
    // 변환된 요소 반환
});</code></pre>
<pre><code class="language-javascript">numbers = [1, 2, 3];
let doubled = numbers.map(function(num) {
    return num * 2;
});
console.log(doubled); // [2, 4, 6]</code></pre>
<h3 id="요약">요약</h3>
<ul>
<li><p>for: 인덱스를 통해 배열을 반복.</p>
</li>
<li><p>for...in: 객체의 속성을 반복.</p>
</li>
<li><p>while: 조건이 참일 때 반복.</p>
</li>
<li><p>do...while: 최소 한 번 실행 후 조건 검사.</p>
</li>
<li><p>forEach: 배열의 각 요소를 처리.</p>
</li>
<li><p>map: 배열의 각 요소를 변환하여 새 배열 반환.</p>
</li>
</ul>
<h2 id="✅-foreach와-map의-차이점">✅ foreach와 map의 차이점</h2>
<ul>
<li><p>"반환값이 없다"는 말은 forEach 메서드가 실행된 후 결과로 어떤 값을 반환하지 않는다는 의미입니다.</p>
</li>
<li><p>forEach를 사용하여 반복 작업을 수행하더라도 그 결과를 변수에 저장하거나 사용할 수 없다는 것입니다.</p>
</li>
</ul>
<h3 id="foreach-사용-예시">forEach 사용 예시</h3>
<pre><code class="language-javascript">numbers = [1, 2, 3];
let result = numbers.forEach(function(num) {
    console.log(num * 2); // 2, 4, 6을 출력
});

console.log(result); // undefined</code></pre>
<blockquote>
<p>위 코드에서 forEach는 각 숫자를 2배로 곱하여 출력하지만, 그 결과를 변수 result에 저장하려고 하면 undefined가 출력됩니다. 이는 forEach가 어떤 값을 반환하지 않기 때문입니다.</p>
</blockquote>
<h3 id="반면에-map은">반면에 map은</h3>
<pre><code class="language-javascript">numbers = [1, 2, 3];
let doubled = numbers.map(function(num) {
    return num * 2; // [2, 4, 6]을 반환
});

console.log(doubled); // [2, 4, 6]</code></pre>
<blockquote>
<p>map은 각 요소를 변환한 결과로 새로운 배열을 반환하므로, doubled 변수에 변환된 배열을 저장할 수 있습니다.</p>
</blockquote>
<h3 id="요약-1">요약</h3>
<ul>
<li><p>forEach: 실행 결과를 반환하지 않음 (즉, undefined).</p>
</li>
<li><p>map: 변환된 요소로 구성된 새로운 배열을 반환함.</p>
</li>
</ul>