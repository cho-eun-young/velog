<p>한입크기 리액트 강의를 들었는데 이정환님은 export를 사용하였고 나는 구름 딥다이브 강의시간에 자연스럽게 export default를 사용하고 있었다. (rafce JSX 스니펫 단축키를 사용해서 ..) 그래서 export default와 export의 차이가 궁금해졌다.</p>
<hr />
<h2 id="export-default">export default</h2>
<ul>
<li>모듈당 하나의 값만 내보낼 수 있다.</li>
<li>import 시 중괄호 {} 없이 원하는 이름으로 가져올 수 있다.</li>
<li>함수, 클래스, 객체 등을 내보낼 수 있다.</li>
</ul>
<pre><code class="language-javascript">// 내보내기
export default function() { ... }

// 가져오기
import anyName from './module';</code></pre>
<h2 id="export-named-export">export (named export)</h2>
<ul>
<li>여러 값을 동시에 내보낼 수 있다.</li>
<li>import 시 정확한 이름을 중괄호 {} 안에 명시해야 한다.</li>
<li>as 키워드를 사용해 다른 이름으로 가져올 수 있다.</li>
</ul>
<pre><code class="language-javascript">// 내보내기
export const foo = 'foo';
export function bar() { ... }

// 가져오기
import { foo, bar } from './module';</code></pre>
<h2 id="사용-시기">사용 시기</h2>
<ul>
<li>단일 기능을 제공하는 모듈은 export default를 사용한다.</li>
<li>여러 기능을 제공하거나 특정 부분만 필요한 경우 named export를 사용한다.</li>
</ul>
<hr />
<p><code>rafce</code>, <code>rafc</code>, <code>rafcp</code>는 <strong>React Snippets</strong> 확장 프로그램에서 제공하는 단축키로, React 컴포넌트를 빠르게 생성하기 위해 사용되는데 각각의 특징에 대해서도 알아보자. </p>
<hr />
<h3 id="1-rafce"><strong>1. rafce</strong></h3>
<ul>
<li><p><strong>의미</strong>: React Arrow Function Component with Export</p>
</li>
<li><p><strong>생성 코드</strong>: 화살표 함수형 컴포넌트를 생성하며, <code>export default</code>를 포함한다.</p>
</li>
<li><p><strong>예제 코드</strong></p>
<pre><code class="language-javascript">import React from 'react';

const ComponentName = () =&gt; {
  return (
    &lt;div&gt;ComponentName&lt;/div&gt;
  );
};

export default ComponentName;</code></pre>
</li>
<li><p><strong>특징</strong></p>
<ul>
<li>화살표 함수로 구성된 함수형 컴포넌트.</li>
<li><code>export default</code>가 포함되어 있어 바로 사용할 수 있음.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="2-rafc"><strong>2. rafc</strong></h3>
<ul>
<li><p><strong>의미</strong>: React Arrow Function Component</p>
</li>
<li><p><strong>생성 코드</strong>: 화살표 함수형 컴포넌트를 생성하며, 명명된 export를 사용한다.</p>
</li>
<li><p><strong>예제 코드</strong></p>
<pre><code class="language-javascript">import React from 'react';

export const ComponentName = () =&gt; {
  return (
    &lt;div&gt;ComponentName&lt;/div&gt;
  );
};</code></pre>
</li>
<li><p><strong>특징</strong></p>
<ul>
<li>화살표 함수로 구성된 함수형 컴포넌트.</li>
<li><code>export default</code> 대신 명명된 <code>export</code>를 사용.</li>
<li>컴포넌트를 명명된 방식으로 가져와야 함 (<code>import { ComponentName } from './ComponentName'</code>).</li>
</ul>
</li>
</ul>
<hr />
<h3 id="3-rafcp"><strong>3. rafcp</strong></h3>
<ul>
<li><p><strong>의미</strong>: React Arrow Function Component with Props</p>
</li>
<li><p><strong>생성 코드</strong>: 화살표 함수형 컴포넌트를 생성하며, <code>props</code>를 포함한다.</p>
</li>
<li><p><strong>예제 코드</strong></p>
<pre><code class="language-javascript">import React from 'react';

const ComponentName = (props) =&gt; {
  return (
    &lt;div&gt;{props.children}&lt;/div&gt;
  );
};

export default ComponentName;</code></pre>
</li>
<li><p><strong>특징</strong></p>
<ul>
<li><code>props</code>를 기본적으로 포함하여 컴포넌트가 부모로부터 전달받은 데이터를 처리할 준비가 되어 있음.</li>
<li><code>export default</code> 포함.</li>
</ul>
</li>
</ul>
<hr />
<h3 id="차이점-요약">차이점 요약</h3>
<table>
<thead>
<tr>
<th>단축키</th>
<th>화살표 함수</th>
<th>Props 포함</th>
<th>Export 방식</th>
</tr>
</thead>
<tbody><tr>
<td><strong>rafce</strong></td>
<td>O</td>
<td>X</td>
<td>Default Export</td>
</tr>
<tr>
<td><strong>rafc</strong></td>
<td>O</td>
<td>X</td>
<td>Named Export</td>
</tr>
<tr>
<td><strong>rafcp</strong></td>
<td>O</td>
<td>O</td>
<td>Default Export</td>
</tr>
</tbody></table>
<hr />
<h3 id="사용-방법">사용 방법</h3>
<ol>
<li>Visual Studio Code에서 <a href="https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets">ES7+ React/Redux/React-Native snippets</a> 확장 프로그램을 설치합니다.</li>
<li><code>.js</code> 또는 <code>.jsx</code> 파일에서 해당 단축키(예: <code>rafce</code>)를 입력하고 Enter를 누르면 자동으로 컴포넌트 코드가 생성됩니다.</li>
</ol>
<hr />
<h3 id="언제-어떤-단축키를-사용할까">언제 어떤 단축키를 사용할까?</h3>
<ol>
<li><strong><code>rafce</code></strong>: 기본적으로 많이 사용되며, 간단한 화살표 함수형 컴포넌트를 빠르게 생성하고 싶을 때 적합.</li>
<li><strong><code>rafc</code></strong>: 명명된 export가 필요한 경우 (여러 컴포넌트를 한 파일에서 내보낼 때 유용).</li>
<li><strong><code>rafcp</code></strong>: props를 처리해야 하는 경우 기본적으로 props를 포함한 템플릿을 생성.</li>
</ol>