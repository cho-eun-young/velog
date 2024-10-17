<h2 id="✅-react에서-컴포넌트란-">✅ React에서 컴포넌트란 ?</h2>
<p>React에서 컴포넌트는 UI를 구성하는 독립적이고 재사용 가능한 코드 조각입니다. </p>
<ol>
<li><p>UI 구성 단위: 
컴포넌트는 애플리케이션 UI를 구성하는 기본 단위입니다. 버튼, 폼, 대화 상자, 화면 등 모든 것이 컴포넌트가 될 수 있습니다.</p>
</li>
<li><p>재사용성: 
컴포넌트는 재사용 가능하도록 설계됩니다. 동일한 컴포넌트를 여러 곳에서 사용할 수 있습니다.</p>
</li>
<li><p>독립성: 
각 컴포넌트는 독립적으로 동작하며, 자체적인 상태와 로직을 가질 수 있습니다.</p>
</li>
<li><p>계층 구조: 
컴포넌트는 다른 컴포넌트를 포함할 수 있어, 복잡한 UI를 계층적으로 구성할 수 있습니다.</p>
</li>
<li><p>Props: 
컴포넌트는 props를 통해 부모 컴포넌트로부터 데이터를 받을 수 있습니다.</p>
</li>
<li><p>State: 
컴포넌트는 자체적인 상태(state)를 가질 수 있으며, 이를 통해 동적인 데이터를 관리합니다.</p>
</li>
<li><p>생명주기: 
클래스 컴포넌트의 경우, 마운트, 업데이트, 언마운트 등의 생명주기를 가집니다.</p>
</li>
<li><p>함수형 및 클래스형: 
컴포넌트는 함수형 또는 클래스형으로 작성할 수 있습니다. 최근에는 함수형 컴포넌트와 훅(Hooks)의 사용이 권장됩니다.</p>
</li>
</ol>
<p>컴포넌트는 React 애플리케이션의 핵심 개념으로, UI를 모듈화하고 관리하기 쉽게 만들어줍니다. 이를 통해 개발자는 복잡한 UI를 더 쉽게 구축하고 유지보수할 수 있습니다.</p>
<hr />
<h2 id="✅-react-컴포넌트를-작성할-때-주의해야-할-주요-사항들">✅ React 컴포넌트를 작성할 때 주의해야 할 주요 사항들</h2>
<ol>
<li><p>컴포넌트는 언제든 다시 렌더링될 수 있도록 준비되어야 합니다. 특정 시점에만 동작한다고 가정하지 말아야 합니다.</p>
</li>
<li><p>props와 state의 변화에 탄력적으로 대응할 수 있어야 합니다. 데이터 흐름을 방해하지 않도록 주의해야 합니다.</p>
</li>
<li><p>컴포넌트 이름은 대문자로 시작하고, 의미있는 이름을 사용해야 합니다. 이는 디버깅에 도움이 됩니다.</p>
</li>
<li><p>props의 타입을 명시하는 것이 좋습니다. PropTypes를 사용하거나 TypeScript를 활용할 수 있습니다. 이는 문서화 역할도 합니다.</p>
</li>
<li><p>컴포넌트 내부에서 큰 객체를 생성하는 코드는 가능한 외부로 분리하는 것이 좋습니다.</p>
</li>
<li><p>로컬 state는 독립적으로 유지하고, 필요 이상으로 상위 컴포넌트로 끌어올리지 않도록 합니다.</p>
</li>
<li><p>렌더링 함수(render 또는 함수형 컴포넌트 자체)는 순수 함수여야 합니다. 부수 효과를 발생시키지 않아야 합니다.</p>
</li>
<li><p>생명주기 메서드나 훅을 올바르게 사용해야 합니다. 특히 부수 효과는 useEffect 등 적절한 곳에서 처리해야 합니다.</p>
</li>
<li><p>가독성을 위해 컴포넌트 파일 구조를 일관성 있게 유지하는 것이 좋습니다. 예를 들어 import문, 컴포넌트 정의, propTypes 순으로 배치할 수 있습니다.</p>
</li>
<li><p>컴포넌트를 작고 재사용 가능하게 유지하는 것이 좋습니다. 한 컴포넌트가 너무 많은 책임을 갖지 않도록 합니다.</p>
</li>
</ol>
<hr />
<ol>
<li>Header.js<pre><code class="language-jsx">import React from 'react';
</code></pre>
</li>
</ol>
<p>function Header() {
  return (
    &lt;header style={{ backgroundColor: '#333', color: 'white', padding: '1rem' }}&gt;
      <h1>My React App</h1>
    </header>
  );
}</p>
<p>export default Header;</p>
<pre><code>
2. Main.js
```jsx
import React from 'react';

function Main() {
  return (
    &lt;main style={{ padding: '2rem' }}&gt;
      &lt;h2&gt;Welcome to our site!&lt;/h2&gt;
      &lt;p&gt;This is the main content area of our React application.&lt;/p&gt;
    &lt;/main&gt;
  );
}

export default Main;</code></pre><ol start="3">
<li>Footer.js<pre><code class="language-jsx">import React from 'react';
</code></pre>
</li>
</ol>
<p>function Footer() {
  return (
    &lt;footer style={{ backgroundColor: '#333', color: 'white', padding: '1rem', textAlign: 'center' }}&gt;
      <p>&copy; 2024 My React App. All rights reserved.</p>
    </footer>
  );
}</p>
<p>export default Footer;</p>
<pre><code>
4. App.js (메인 컴포넌트)
```jsx
import React from 'react';
import Header from './Header';
import Main from './Main';
import Footer from './Footer';

function App() {
  return (
    &lt;div className="App"&gt;
      &lt;Header /&gt;
      &lt;Main /&gt;
      &lt;Footer /&gt;
    &lt;/div&gt;
  );
}

export default App;</code></pre><ol start="5">
<li>index.js (앱 진입점)<pre><code class="language-jsx">import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
</code></pre>
</li>
</ol>
<p>const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  &lt;React.StrictMode&gt;
    
  &lt;/React.StrictMode&gt;
);</p>
<pre><code>
이 코드를 실행하면 다음과 같은 구조의 웹페이지가 렌더링됩니다
</code></pre><p>+----------------------------------+
|            Header                |
|  My React App                    |
+----------------------------------+
|            Main                  |
|  Welcome to our site!            |
|                                  |
|  This is the main content area   |
|  of our React application.       |
|                                  |
+----------------------------------+
|            Footer                |
|  © 2024 My React App.            |
|  All rights reserved.            |
+----------------------------------+</p>
<pre><code></code></pre>