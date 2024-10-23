<h3 id="기본-구문">기본 구문</h3>
<ul>
<li>array.splice(start, deleteCount, item1, item2, ...)</li>
</ul>
<h3 id="매개변수">매개변수</h3>
<ul>
<li>start: 배열을 변경할 시작 인덱스</li>
<li>deleteCount: 제거할 요소의 수 (선택적)</li>
<li>item1, item2, ...: 배열에 추가할 새 요소들 (선택적)</li>
</ul>
<h3 id="원본-배열-수정">원본 배열 수정</h3>
<ul>
<li>splice()는 원본 배열을 직접 수정합니다.</li>
</ul>
<h2 id="splice-메서드의-다양한-사용-예시">splice() 메서드의 다양한 사용 예시</h2>
<h3 id="1-요소-제거">1. 요소 제거</h3>
<pre><code class="language-javascript">let fruits = ['apple', 'banana', 'cherry', 'date'];
let removed = fruits.splice(1, 2);
console.log(fruits);  // ['apple', 'date']
console.log(removed);  // ['banana', 'cherry']</code></pre>
<h3 id="2-요소-추가">2. 요소 추가</h3>
<pre><code class="language-javascript">let numbers = [1, 2, 5];
numbers.splice(2, 0, 3, 4);
console.log(numbers);  // [1, 2, 3, 4, 5]</code></pre>
<h3 id="3-요소-교체">3. 요소 교체</h3>
<pre><code class="language-javascript">let colors = ['red', 'green', 'blue'];
colors.splice(1, 1, 'yellow', 'orange');
console.log(colors);  // ['red', 'yellow', 'orange', 'blue']</code></pre>
<h3 id="4-마지막-요소-제거">4. 마지막 요소 제거</h3>
<pre><code class="language-javascript">let animals = ['cat', 'dog', 'bird', 'fish'];
animals.splice(-1);
console.log(animals);  // ['cat', 'dog', 'bird']</code></pre>
<h3 id="5-특정-위치부터-끝까지-제거">5. 특정 위치부터 끝까지 제거</h3>
<pre><code class="language-javascript">let letters = ['a', 'b', 'c', 'd', 'e'];
letters.splice(2);
console.log(letters);  // ['a', 'b']</code></pre>
<h3 id="6-음수-인덱스-사용">6. 음수 인덱스 사용</h3>
<pre><code class="language-javascript">let days = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri'];
days.splice(-2, 1, 'Sat');
console.log(days);  // ['Mon', 'Tue', 'Wed', 'Sat', 'Fri']</code></pre>
<h3 id="7-요소-삽입-제거-없이">7. 요소 삽입 (제거 없이)</h3>
<pre><code class="language-javascript">let months = ['Jan', 'Mar', 'Apr'];
months.splice(1, 0, 'Feb');
console.log(months);  // ['Jan', 'Feb', 'Mar', 'Apr']</code></pre>