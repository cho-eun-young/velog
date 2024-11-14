<h2 id="1-spread-연산자">1. Spread 연산자</h2>
<h3 id="--spread--흩뿌리다-펼치다-라는-뜻">-&gt; Spread : 흩뿌리다, 펼치다 라는 뜻</h3>
<h3 id="--객체나-배열에-저장된-여러개의-값을-개별로-흩뿌려주는-역할">-&gt; 객체나 배열에 저장된 여러개의 값을 개별로 흩뿌려주는 역할</h3>
<pre><code class="language-javascript">let arr1 = [1, 2, 3];
let arr2 = [4, ...arr1, 5, 6] // [4, 1, 2, 3, 5, 6]</code></pre>
<pre><code class="language-javascript">let obj1 = {
  a : 1,
  b : 2,
};

let obj2 = {
  ...obj1,
  c : 3,
  d : 4,
}; // { a: 1, b: 2, c: 3, d: 4}

function funcA(p1, p2, p3){
  console.log(p1, p2, p3)
}

funcA(...arr1) // 1 2 3</code></pre>
<h2 id="2-rest-매개변수">2. Rest 매개변수</h2>
<h3 id="--rest는-나머지-나머지-매개변수">-&gt; Rest는 나머지, 나머지 매개변수</h3>
<pre><code class="language-javascript">function funcB(one, ...rest){
  console.log(rest)
}

funcB(...arr1) // [2, 3]</code></pre>
<p>rest 매개변수는 뒤에 추가적으로 나오는 매개변수를 선언할 수 없다. 
마지막으로 선언해야함! rest로 할 필요는 없음. ex) ...abc</p>