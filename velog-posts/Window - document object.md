<blockquote>
<p>window 객체는 브라우저의 최상위 객체로, 웹 페이지의 실행 환경을 제공합니다. JavaScript에서 가장 기본적인 객체 중 하나이며, 여러 가지 중요한 기능과 프로퍼티를 포함하고 있습니다.</p>
</blockquote>
<h2 id="1-기본-설명">1. 기본 설명</h2>
<ul>
<li><p>글로벌 객체: 모든 JavaScript 코드에서 전역 범위의 객체로 접근할 수 있습니다. 즉, 변수나 함수를 정의하면 window 객체의 속성으로 자동으로 추가됩니다.</p>
</li>
<li><p>브라우저 환경: window 객체는 브라우저의 창 또는 탭을 나타내며, 사용자가 상호작용할 수 있는 모든 요소를 포함합니다.</p>
</li>
</ul>
<h2 id="2-주요-프로퍼티">2. 주요 프로퍼티</h2>
<ul>
<li><p>document: 현재 웹 페이지의 DOM(Document Object Model)을 나타내는 객체입니다. 이를 통해 HTML 요소에 접근하고 조작할 수 있습니다.</p>
</li>
<li><p>location: 현재 문서의 URL 정보를 담고 있는 객체입니다. 페이지를 리디렉션하거나 새 페이지를 로드할 때 사용됩니다.</p>
</li>
<li><p>history: 사용자가 방문한 페이지의 기록을 관리하는 객체입니다. 이전 페이지로 이동하거나 앞으로 이동하는 기능을 제공합니다.</p>
</li>
<li><p>navigator: 브라우저에 대한 정보를 포함하고 있는 객체로, 브라우저의 종류나 버전, 운영체제 정보 등을 확인할 수 있습니다.</p>
</li>
</ul>
<h2 id="3-주요-메서드">3. 주요 메서드</h2>
<p>alert(): 사용자에게 경고 메시지를 표시하는 팝업 창을 생성합니다.</p>
<pre><code class="language-javascript">window.alert('Hello, World!');</code></pre>
<p>confirm(): 사용자가 확인 또는 취소를 선택할 수 있는 대화 상자를 표시합니다.</p>
<pre><code class="language-javascript">let result = window.confirm('Are you sure?');</code></pre>
<p>prompt(): 사용자에게 입력을 요청하는 대화 상자를 표시합니다.</p>
<pre><code class="language-javascript">name = window.prompt('What is your name?');</code></pre>
<p>setTimeout(): 특정 시간 후에 지정된 함수를 실행합니다.</p>
<pre><code class="language-javascript">window.setTimeout(function() {
    console.log('This will run after 2 seconds');
}, 2000);</code></pre>
<h2 id="4-이벤트-처리">4. 이벤트 처리</h2>
<p>window 객체는 다양한 이벤트를 처리할 수 있습니다. 예를 들어, 페이지가 로드될 때, 크기가 변경될 때 등의 이벤트를 감지할 수 있습니다.</p>
<pre><code class="language-javascript">window.onload = function() {
    console.log('Page is fully loaded');
};</code></pre>
<h2 id="5-전역-변수-및-함수">5. 전역 변수 및 함수</h2>
<p>JavaScript에서 정의한 전역 변수와 함수는 window 객체의 속성으로 접근할 수 있습니다.</p>
<pre><code class="language-javascript">tvar myVar = 'Hello';
console.log(window.myVar); // 'Hello'</code></pre>
<h3 id="요약">요약</h3>
<ul>
<li><p>window 객체는 브라우저 환경을 나타내며, DOM, URL, 브라우저 정보 등 다양한 기능을 제공합니다.</p>
</li>
<li><p>메서드와 프로퍼티를 통해 웹 페이지의 동작을 제어하고 사용자와 상호작용할 수 있는 기능을 제공합니다.</p>
</li>
<li><p>innerHTML: HTML 구조를 포함한 내용을 가져오거나 설정. XSS 공격에 주의.</p>
</li>
<li><p>innerText: 가시적인 텍스트만 포함하며, CSS 스타일에 따라 숨겨진 텍스트는 제외.</p>
</li>
<li><p>textContent: 모든 텍스트를 포함하며, 숨겨진 텍스트까지 가져옴. 성능이 더 좋음.</p>
</li>
</ul>
<h2 id="돔-이란-document-object-model">돔 이란 (Document Object Model)?</h2>
<blockquote>
<p>메모리에 웹 페이지 문서 구조를 트리구조로 표현해서 웹 브라우저가 HTML 페이지를 인식하게 해줍니다.</p>
</blockquote>
<blockquote>
<p>웹페이지를 이루는 요소들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리구조로 만든 객체 모델을 의미합니다.</p>
</blockquote>
<h2 id="1-document-객체의-구조">1. document 객체의 구조</h2>
<ul>
<li><p>최상위 객체: document 객체는 브라우저에서 현재 로드된 HTML 문서에 대한 정보를 담고 있습니다.</p>
</li>
<li><p>속성 및 메서드: 다양한 속성과 메서드를 통해 HTML 요소에 접근하고 조작할 수 있습니다.</p>
</li>
</ul>
<h2 id="2-주요-속성">2. 주요 속성</h2>
<p>document.title: 현재 문서의 제목을 가져오거나 설정합니다.</p>
<p>document.body: 문서의  요소에 접근합니다.</p>
<p>document.head: 문서의  요소에 접근합니다.</p>
<p>document.URL: 현재 문서의 URL을 가져옵니다.</p>
<h2 id="3-주요-메서드-1">3. 주요 메서드</h2>
<p>document.getElementById(id): 주어진 ID를 가진 요소를 반환합니다.</p>
<pre><code class="language-javascript">element = document.getElementById('myId');</code></pre>
<p>document.getElementsByClassName(className): 주어진 클래스 이름을 가진 요소들의 HTMLCollection을 반환합니다.</p>
<pre><code class="language-javascript">elements = document.getElementsByClassName('myClass');</code></pre>
<p>document.getElementsByTagName(tagName): 주어진 태그 이름을 가진 요소들의 HTMLCollection을 반환합니다.</p>
<pre><code class="language-javascript">elements = document.getElementsByTagName('div');</code></pre>
<p>document.querySelector(selector): 주어진 CSS 선택자와 일치하는 첫 번째 요소를 반환합니다.</p>
<pre><code class="language-javascript">element = document.querySelector('.myClass');</code></pre>
<p>document.querySelectorAll(selector): 주어진 CSS 선택자와 일치하는 모든 요소의 NodeList를 반환합니다.</p>
<pre><code class="language-javascript">elements = document.querySelectorAll('div.myClass');</code></pre>
<p>document.createElement(tagName): 새로운 HTML 요소를 생성합니다.</p>
<pre><code class="language-javascript">newDiv = document.createElement('div');</code></pre>
<p>document.appendChild(node): 지정한 노드를 부모 요소에 추가합니다.</p>
<pre><code class="language-javascript">document.body.appendChild(newDiv);</code></pre>
<h2 id="4-이벤트-처리-1">4. 이벤트 처리</h2>
<p>document 객체를 사용하여 이벤트를 처리할 수 있습니다. 이벤트 리스너를 추가하여 특정 사용자 행동에 반응할 수 있습니다.</p>
<pre><code class="language-javascript">tdocument.addEventListener('click', function() {
    console.log('문서가 클릭되었습니다.');
});</code></pre>