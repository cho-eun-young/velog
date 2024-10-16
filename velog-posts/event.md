<p>JavaScript의 이벤트 리스너에서 this 키워드의 의미는 이벤트가 발생한 요소를 가리킵니다.</p>
<h2 id="✅-this-키워드의-동작">✅ this 키워드의 동작</h2>
<p>이벤트 리스너 함수 내에서 this는 이벤트가 바인딩된 요소, 즉 이벤트가 발생한 DOM 요소를 참조합니다. 이는 이벤트 객체의 currentTarget 속성과 동일한 값을 가집니다.</p>
<pre><code class="language-javascript">const button = document.querySelector('button'); 
button.addEventListener('click', function() { console.log(this); // 여기서 this는 클릭된 button 요소를 가리킵니다. });</code></pre>
<p>이 예시에서 버튼을 클릭하면, 콘솔에 버튼 요소 자체가 출력됩니다.</p>
<h3 id="주의사항">주의사항</h3>
<p>화살표 함수와의 차이화살표 함수를 이벤트 리스너로 사용할 경우, this의 동작이 다릅니다. 화살표 함수는 자신만의 this 바인딩을 생성하지 않고, 대신 자신을 포함하고 있는 함수의 this 바인딩을 상속받습니다.</p>
<pre><code class="language-javascript">button.addEventListener('click', () =&gt; { console.log(this); // 여기서 this는 전역 객체(window)를 가리킬 수 있습니다. });</code></pre>
<h3 id="활용">활용</h3>
<p>this를 사용하면 이벤트가 발생한 요소의 속성이나 메서드에 쉽게 접근할 수 있습니다.</p>
<pre><code class="language-javascript">button.addEventListener('click', function() { this.style.backgroundColor = 'red'; // 클릭된 버튼의 배경색을 변경 });</code></pre>
<blockquote>
<p>이벤트 리스너에서 this를 사용하면 코드의 재사용성을 높이고, 여러 요소에 동일한 이벤트 리스너를 적용할 때 유용합니다. 각 요소는 자신의 컨텍스트를 유지하면서 동일한 코드를 실행할 수 있기 때문입니다.</p>
</blockquote>
<h2 id="✅-ui-이벤트">✅ UI 이벤트</h2>
<ul>
<li><p>load: 페이지 로딩이 완료되었을 때</p>
</li>
<li><p>unload: 페이지를 떠날 때</p>
</li>
<li><p>error: JavaScript 오류 발생 시</p>
</li>
<li><p>resize: 브라우저 창 크기가 변경될 때</p>
</li>
<li><p>scroll: 사용자가 페이지를 스크롤할 때</p>
</li>
</ul>
<h3 id="마우스-이벤트">마우스 이벤트</h3>
<ul>
<li><p>click: 요소를 클릭했을 때</p>
</li>
<li><p>dblclick: 요소를 더블클릭했을 때</p>
</li>
<li><p>mousedown: 마우스 버튼을 누를 때</p>
</li>
<li><p>mouseup: 마우스 버튼을 놓을 때</p>
</li>
<li><p>mousemove: 마우스를 움직일 때</p>
</li>
<li><p>mouseover: 요소 위로 마우스가 이동할 때</p>
</li>
<li><p>mouseout: 요소에서 마우스가 벗어날 때</p>
</li>
</ul>
<h3 id="키보드-이벤트">키보드 이벤트</h3>
<ul>
<li><p>keydown: 키를 누를 때</p>
</li>
<li><p>keyup: 키를 놓을 때</p>
</li>
<li><p>keypress: 키를 누르고 놓을 때</p>
</li>
</ul>
<h3 id="폼-이벤트">폼 이벤트</h3>
<ul>
<li><p>submit: 폼이 제출될 때</p>
</li>
<li><p>change: 입력 요소의 값이 변경될 때</p>
</li>
<li><p>focus: 요소에 포커스가 갈 때</p>
</li>
<li><p>blur: 요소에서 포커스가 빠져나갈 때</p>
</li>
</ul>
<h3 id="문서-이벤트">문서 이벤트</h3>
<p>DOMContentLoaded: HTML 문서 로딩과 파싱이 완료되었을 때</p>
<h3 id="드래그-이벤트">드래그 이벤트</h3>
<ul>
<li><p>dragstart: 요소를 드래그하기 시작할 때</p>
</li>
<li><p>drag: 요소를 드래그하는 동안</p>
</li>
<li><p>dragend: 드래그가 끝났을 때</p>
</li>
</ul>
<h3 id="터치-이벤트">터치 이벤트</h3>
<ul>
<li><p>touchstart: 터치가 시작될 때</p>
</li>
<li><p>touchmove: 터치한 상태로 움직일 때</p>
</li>
<li><p>touchend: 터치가 끝날 때</p>
</li>
</ul>