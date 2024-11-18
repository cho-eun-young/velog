<h3 id="1-비동기-작업-실행하는-함수-promise">1. 비동기 작업 실행하는 함수 Promise()</h3>
<pre><code class="language-javascript">const promise = new Promise(() =&gt;{
  // 비동기 작업 실행하는 함수
  // executor

   setTimeout(() =&gt; {
    console.log('안녕')
   }, 2000); // 2초뒤 안녕 출력
 });

console.log(promise) 
// Promise{} 객체 출력 
// -&gt; [[Prototype]]: Promise, [[PromiseState]]: 'pending', [[PromiseResult]]: undefined</code></pre>
<h3 id="2-excutor-성공적으로-완료">2. excutor 성공적으로 완료</h3>
<pre><code class="language-javascript">
const promise = new Promise((resolve, reject) =&gt;{

   setTimeout(() =&gt; {
    console.log('안녕'); // 2초뒤 안녕 출력
    resolve()
   }, 2000); 
 });

setTimeout(() =&gt; {
    console.log(promise);
  // 3초뒤 promise 객체 출력, 
  // -&gt; [[PromiseState]]: 'fulfilled' ,[[PromiseResult]]: undefined
   }, 3000); 
 });</code></pre>
<h3 id="3-excutor-성공적으로-완료-promiseresult-전달">3. excutor 성공적으로 완료 (PromiseResult 전달)</h3>
<pre><code class="language-javascript">const promise = new Promise((resolve, reject) =&gt;{

   setTimeout(() =&gt; {
    console.log('안녕'); // 2초뒤 안녕 출력
    resolve('안녕') // PromiseResult 전달
   }, 2000); 
 });

setTimeout(() =&gt; {
    console.log(promise);
  // 3초뒤 promise 객체 출력, 
  // -&gt; [[PromiseState]]: 'fulfilled' ,[[PromiseResult]]: '안녕'
   }, 3000); 
 });</code></pre>
<h3 id="4-실패상태로">4. 실패상태로</h3>
<pre><code class="language-javascript">const promise = new Promise((resolve, reject) =&gt;{

   setTimeout(() =&gt; {
    console.log('안녕'); // 2초뒤 안녕 출력
    reject('왜 실패했는지 이유...')
   }, 2000); 
 });

setTimeout(() =&gt; {
    console.log(promise);
  // 3초뒤 promise 객체 출력, 
  // -&gt; [[PromiseState]]: 'rejected' ,[[PromiseResult]]: '왜 실패했는지 이유...'
   }, 3000); 
 });</code></pre>
<h3 id="5-then">5. then</h3>
<h3 id="--그-후에">-&gt; 그 후에</h3>
<pre><code class="language-javascript">const promise = new Promise((resolve, reject) =&gt;{

   setTimeout(() =&gt; {
     const num = 10;

     if(typeof num === 'number'){
       resolve(num + 10);
     }else {
       reject('num이 숫자가 아닙니다.');
     }
   }, 2000); 
 });

setTimeout(() =&gt; {
    console.log(promise);
  // 3초뒤 promise 객체 출력, 
  // -&gt; [[PromiseState]]: 'fulfiled' ,[[PromiseResult]]: '20'
   }, 3000); 
 });

promise.then((value) =&gt; {
    console.log(value); // 20
})</code></pre>
<p>then 메서드는 promise비동기작업 상태가 성공(fulfiled)일 때만 호출된다.</p>
<h3 id="5-catch">5. catch</h3>
<pre><code class="language-javascript">const promise = new Promise((resolve, reject) =&gt;{

   setTimeout(() =&gt; {
     const num = null;

     if(typeof num === 'number'){
       resolve(num + 10);
     }else {
       reject('num이 숫자가 아닙니다.');
     }
   }, 2000); 
 });

setTimeout(() =&gt; {
    console.log(promise);
  // 3초뒤 promise 객체 출력, 
  // -&gt; [[PromiseState]]: 'fulfiled' ,[[PromiseResult]]: '20'
   }, 3000); 
 });

promise.catch((error) =&gt; { //num이 숫자가 아닙니다.
    console.log(error); 
})</code></pre>
<p>catch 실패버전의 then 메서드 같은 것이다!!</p>
<h3 id="6-promise-체이닝">6. promise 체이닝</h3>
<pre><code class="language-javascript">promise
  .then((value) =&gt; {
    console.log(value); // 20
  })
  .catch((error) =&gt; {
    console.log(error); // num이 숫자가 아닙니다.
  })</code></pre>
<h3 id="7-콜백지옥을-방지">7. 콜백지옥을 방지</h3>
<pre><code class="language-javascript">function add10(num){
  const promise = new Promise((resolve, reject) =&gt;{

   setTimeout(() =&gt; {

     if(typeof num === 'number'){
       resolve(num + 10);
     }else {
       reject('num이 숫자가 아닙니다.');
     }
   }, 2000); 
 });
 return promise;
}  

// 콜백 지옥
const p = add10(0);
p.then((result) =&gt; {
    console.log(result); // 10

    const newP =  add10(result);
      newP.then((result) =&gt; {
        console.log(result); // 20
    });
      return newP; // 콜백지옥을 방지
})</code></pre>
<pre><code class="language-javascript">const p = add10(0);
p.then((result) =&gt; {
    console.log(result); // 10

      const newP = add10(result);

      return newP; // 콜백지옥을 방지
}).then(result) =&gt; {
      console.log(result); // 20
});</code></pre>
<p>위의 코드를 간결하게 변경</p>
<pre><code class="language-javascript">add10(0)
  .then((result) =&gt; {
    console.log(result); // 10
      return add10(result);
})
  .then(result) =&gt; {
      console.log(result); // 20
    return add10(result);
})
  .then(result) =&gt; {
      console.log(result); // 20
})
  .catch((error) =&gt; {
    console.log(error);
})</code></pre>
<p>promise는 자바스크립트에서 중요한 개념!! API 호출, 다른서버와 통신 등 개념을 짚고 가져가야겠다 🫠..!</p>