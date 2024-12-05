<h2 id="jsx를-사용할-때-주의사항">JSX를 사용할 때 주의사항</h2>
<h3 id="1-중괄호-내부에는-자바스크립트-표현식만-넣을-수-있다">1. 중괄호 내부에는 자바스크립트 표현식만 넣을 수 있다.</h3>
<p>표현식 = 값이있는 식
ex) 삼항연산자, {10}, {number} </p>
<p>{if(){}}, {for(){}} 등 조건문, 반복문을 사용하면 오류발생 -&gt; 한줄로써 값으로 평가받을 수 없기때문</p>
<pre><code class="language-jsx">import React from &quot;react&quot;;

const Main = () =&gt; {
  const number = 10;

  return (
    &lt;main&gt;
      &lt;h1&gt;Main&lt;/h1&gt;
      &lt;h2&gt;number : {number % 2 === 0 ? &quot;even&quot; : &quot;odd&quot;}&lt;/h2&gt;
    &lt;/main&gt;
  );
};

export default Main;</code></pre>
<h3 id="2-숫자-문자열-배열-값만-렌더링-된다">2. 숫자, 문자열, 배열 값만 렌더링 된다.</h3>
<pre><code class="language-jsx">{true}
{undefined}
{null}</code></pre>
<p>위의 값들은 화면에 랜더링 되지않는다. 그리고 객체 전체를 렌더링 할 수 없다. 문자값이나 숫자값으로 가져와야한다. obj.a 처럼!</p>
<h3 id="3-모든-태그는-닫혀있어야-한다">3. 모든 태그는 닫혀있어야 한다.</h3>
<pre><code class="language-jsx">&lt;img&gt;&lt;/img&gt;
&lt;img /&gt;</code></pre>
<h3 id="4-최상위-태그는-반드시-하나여야만-한다">4. 최상위 태그는 반드시 하나여야만 한다.</h3>
<pre><code class="language-jsx">&lt;main&gt; 
&lt;/main&gt;

&lt;&gt;
&lt;/&gt;</code></pre>