<h2 id="async">async</h2>
<h3 id="--어떤-함수를-비동기-함수로-만들어주는-키워드">-&gt; 어떤 함수를 비동기 함수로 만들어주는 키워드</h3>
<h3 id="--함수가-프로미스를-반환하도록-변환해주는-키워드">-&gt; 함수가 프로미스를 반환하도록 변환해주는 키워드</h3>
<pre><code class="language-javascript">async function getData() {
  return{
    name: '이정환',
    id: 'winterlood',
  };
}

console.log(getData()); // Promise 객체 출력
// [[PromiseState]] : 'fulfilled', [[PromiseResult]] : Object(name, id)</code></pre>
<h2 id="await">await</h2>
<h3 id="--async-함수-내부에서만-사용이-가능한-키워드">-&gt; async 함수 내부에서만 사용이 가능한 키워드</h3>
<h3 id="--비동기-함수가-다-처리되기를-기다리는-역할">-&gt; 비동기 함수가 다 처리되기를 기다리는 역할</h3>
<pre><code class="language-javascript">async function getData() {
  return new Promise((resolve, reject) =&gt; {
    setTimeout(() =&gt; {
      resolve({
        name: '이정환',
        id: 'winterlood',
      });
    },1500);
  });
}


async function printData() {
  const data = await getData();
  console.log(data);
}

printData() // Promise 객체 출력
// [[PromiseState]] : 'fulfilled', [[PromiseResult]] : Object(name, id)</code></pre>
<p>직접 써보고 숙달해야 익숙해질 것 같다 ㅠㅠㅠㅠ 아직은 어렵우...🫠</p>