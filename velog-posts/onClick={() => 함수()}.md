<h3 id="🤔-react에서-onclick--함수-형태로-이벤트-핸들러를-작성할-때---문법을-사용하는-이유-">🤔 React에서 <code>onClick={() =&gt; 함수()}</code> 형태로 이벤트 핸들러를 작성할 때 <code>() =&gt;</code> 문법을 사용하는 이유 !!</h3>
<p>영화의 이미지를 클릭하고 모달창이 나올때 쓰였던 부분이 궁금해서 가져온...</p>
<pre><code class="language-javascript">&lt;div id={id} className="row__posters"&gt;
  {movies.map((movie) =&gt; (
    &lt;img
        key={movie.id}
        className="row__poster"
        src={`https://image.tmdb.org/t/p/original/${movie.backdrop_path}`}
        alt={movie.name}
        onClick={() =&gt; handleClick(movie)}
      /&gt;
   ))}
&lt;/div&gt;</code></pre>
<h4 id="1-즉시-실행-방지">1. 즉시 실행 방지</h4>
<ul>
<li><code>onClick={함수()}</code> 형태로 작성하면 컴포넌트가 렌더링될 때 함수가 즉시 실행됩니다.</li>
<li><code>() =&gt;</code> 화살표 함수를 사용하면 클릭 이벤트가 발생할 때까지 함수 실행을 지연시킵니다.</li>
</ul>
<h4 id="2-매개변수-전달">2. 매개변수 전달</h4>
<ul>
<li><code>onClick={() =&gt; 함수(매개변수)}</code> 형태로 함수에 매개변수를 쉽게 전달할 수 있습니다.</li>
</ul>
<h4 id="3-이벤트-객체-접근">3. 이벤트 객체 접근</h4>
<ul>
<li><code>onClick={(e) =&gt; 함수(e)}</code> 형태로 이벤트 객체에 접근할 수 있습니다.</li>
</ul>
<h4 id="4-컨텍스트-유지">4. 컨텍스트 유지</h4>
<ul>
<li>클래스 컴포넌트에서 <code>this</code>의 바인딩 문제를 해결할 수 있습니다.</li>
</ul>
<h4 id="5-인라인-로직">5. 인라인 로직</h4>
<ul>
<li>간단한 로직을 인라인으로 작성할 수 있습니다. 예: <code>onClick={() =&gt; { /* 여러 줄의 코드 */ }}</code></li>
</ul>
<h4 id="6-조건부-실행">6. 조건부 실행</h4>
<ul>
<li><code>onClick={() =&gt; 조건 ? 함수1() : 함수2()}</code> 형태로 조건에 따라 다른 함수를 실행할 수 있습니다.</li>
</ul>
<p>이 방식은 이벤트 핸들링을 유연하게 만들어주며, 특히 동적인 값이나 추가적인 로직이 필요할 때 유용하다. </p>
<p>하지만 성능 최적화 관점에서는 불필요한 함수 생성을 피하기 위해 단순한 경우 <code>onClick={함수}</code>형태를 사용하는 것이 좋다!!</p>