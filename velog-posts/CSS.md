<h2 id="☘️-container-query">☘️ Container Query</h2>
<ul>
<li><p>media query는 일반적을 viewport의 너비를 기준으로 적용된다.</p>
</li>
<li><p>container query는 viewport 대신 영역을 감싼 container를 기준으로 적용된다.</p>
</li>
</ul>
<h2 id="☘️-dialog-element">☘️ Dialog Element</h2>
<p>모달</p>
<pre><code>&lt;dialog open&gt;
  &lt;span&gt;hi&lt;/span&gt;
&lt;dialog&gt;</code></pre><p>dialog에 open 속성을 추가하지 않으면 기본적으로 dialog 요소가 숨겨진다.</p>
<p>하지만 비모달 대화 상자만 열 수 있으므로 open 속성을 직접 사용하는 것은 권장되지 않는다.</p>
<p>대신 show() 및 showModal() JavaScript 메서드를 사용해야 한다.</p>
<h2 id="☘️-반응형-이미지-최적화-하기">☘️ 반응형 이미지 최적화 하기</h2>
<h4 id="srcset-속성">srcset 속성</h4>
<ul>
<li>반응형 이미지 구현하는 가장 쉬운 방법은 img 태그에 srcset속성을 사용하는 것이다. 이 속성을 사용하면 크기가 다른 여러 이미지를 정의할 수 있으며 브라우저는 사용자의 화면 크기에 가장 잘 맞는 이미지를 자동으로 선택한다.</li>
</ul>
<h4 id="picture-태그">picture 태그</h4>
<ul>
<li>화면 크기에 따라 다른 이미지를 보여주고 싶으면 picture 태그 사용하면 됨.</li>
</ul>
<h4 id="srcset과-picture의-차이점">srcset과 picture의 차이점</h4>
<p>srcset은 한번 큰 사이즈의 이미지를 가져오면 작은 화면에서도 큰 사이즈 이미지를 이용하지만 picture를 이용하면 계속 다른 이미지를 보여주게 됩니다.</p>
<h2 id="☘️-is">☘️ :is()</h2>
<h4 id="is">:is()</h4>
<p>가상 클래스는 셀렉터를 그룹화 할 때 간단하게 처리할 수 있게 해줍니다.</p>
<p>일반적으로 선택기의 일부가 유효하지 않으면 전체 블록이 제거됩니다. 하지만 is는 'forgiving'하기 때문에 유효한 부분은 적용이 됩니다.</p>
<h2 id="☘️-has">☘️ :has()</h2>
<h4 id="has">:has</h4>
<p>선택자를 사용하려면 상위 요소에 적용 될 :has 선택자에 선택자(또는 선택자 목록)를 전달해야 합니다.</p>
<h2 id="☘️-grid-autofill--autofit">☘️ Grid Autofill / Autofit</h2>
<p>auto-fill과 auto-fit은 repeat()함수와 함께 사용됩니다.</p>
<p>컨테이너의 너비가 좁을 경우 auto-fit과 auto-fill의 차이가 없는 것처럼 보이지만 컨테이너 너비가 넓어지면 차이를 볼 수 있습니다.</p>
<p>auto-fit은 컨테이너의 너비가 커질 때 각각의 셀들이 커지면서 공간을 나눠가지게 됩니다.</p>
<p>하지만 auto-fill은 보이지 않는 셀을 만들어서 빈공간을 채우며 셀의 길이는 늘리지 않습니다.</p>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/e2d8b02c-5fd5-484f-a4fa-c2b2d1f73694/image.webp" /></p>