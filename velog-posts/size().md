<h3 id="1-정의">1. 정의</h3>
<ul>
<li><code>size</code>는 Set 객체에 포함된 값의 개수를 반환합니다</li>
</ul>
<h3 id="2-사용법">2. 사용법</h3>
<pre><code class="language-javascript">   const mySet = new Set([1, 2, 3]);
   console.log(mySet.size); // 3</code></pre>
<h3 id="3-특징">3. 특징</h3>
<ul>
<li>읽기 전용 속성입니다. 즉, 직접 값을 할당할 수 없습니다</li>
<li>중복된 요소는 하나로 계산됩니다</li>
</ul>
<h3 id="4-반환-값">4. 반환 값</h3>
<ul>
<li>Set에 포함된 고유한 요소의 수를 나타내는 정수를 반환합니다</li>
</ul>
<h3 id="5-성능">5. 성능</h3>
<ul>
<li><code>size</code> 속성에 접근하는 것은 O(1)의 시간 복잡도를 가집니다. 즉, Set의 크기와 관계없이 빠르게 접근할 수 있습니다</li>
</ul>
<h3 id="6-용도">6. 용도</h3>
<ul>
<li>Set의 크기를 확인할 때 사용합니다.</li>
<li>빈 Set인지 확인할 때 유용합니다 (size가 0이면 빈 Set).</li>
<li>특정 작업 전후로 Set의 크기 변화를 확인할 때 사용할 수 있습니다.</li>
</ul>
<h3 id="7-주의사항">7. 주의사항</h3>
<ul>
<li>Array의 <code>length</code> 속성과 유사하지만, Set은 <strong>중복을 허용하지 않으므로</strong> 실제 추가된 요소의 수와 다를 수 있습니다</li>
</ul>