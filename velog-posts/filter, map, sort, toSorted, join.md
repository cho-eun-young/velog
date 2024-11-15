<h2 id="1-filter">1. filter</h2>
<h3 id="기존-배열에서-조건을-만족하는-요소들만-필터링하여-새로운-배열로-반환">기존 배열에서 조건을 만족하는 요소들만 필터링하여 새로운 배열로 반환</h3>
<pre><code class="language-javascript">let arr1 =[
  { name: '이정환', hobby: '테니스' },
  { name: '김효빈', hobby: '테니스' },
  { name: '홍길동', hobby: '독서' },
];

const tennisPeople = arr1.filter((item) =&gt; {
     if(item.hobby === '테니스')return true; 
})

const tennisPeople = arr1.filter((item) =&gt; item.hobby === '테니스')

console.log(tennisPeople); 
// { name: '이정환', hobby: '테니스' },{ name: '김효빈', hobby: '테니스' },</code></pre>
<h2 id="2-map">2. map</h2>
<h3 id="배열의-모든-요소를-순회하면서--각각-콜백함수를-실행하고-그-결과값들을-모아서-새로운-배열로-반환">배열의 모든 요소를 순회하면서 , 각각 콜백함수를 실행하고 그 결과값들을 모아서 새로운 배열로 반환</h3>
<pre><code class="language-javascript">let arr2 = [1, 2, 3];

const mapResult1 = arr2.map(function (item, idx, arr) {
      return item * 2;
})
console.log(mapResult1); // [2, 4, 6]</code></pre>
<pre><code class="language-javascript">let arr1 =[
  { name: '이정환', hobby: '테니스' },
  { name: '김효빈', hobby: '테니스' },
  { name: '홍길동', hobby: '독서' },
];

let names = arr1.map((item) =&gt; item.name);

console.log(names) // ['이정환', '김효빈', '홍길동'];</code></pre>
<h2 id="3-sort">3. sort</h2>
<h3 id="배열을-사전순으로-정렬하는-메서드">배열을 사전순으로 정렬하는 메서드</h3>
<pre><code class="language-javascript">let arr3 = ['b', 'a', 'c'];
arr3.sort()

console.log(arr3)  // ['a', 'b', 'c']


// --------------------
let arr3 = [10, 3, 5];
arr3.sort((a,b) =&gt; {
    if(a &gt; b){
      // b가 a 앞에 와라
        return 1; // -&gt; b, a 배치
    }else if(a &lt; b){
      // a가 b 앞에 와라
        return -1; // -&gt; a, b 배치
    }else{
      // 두 값의 자리를 바꾸지 마라
        return 0; // a, b 자리를 그대로 유지
    }
})

console.log(arr3) // [3, 5, 10]</code></pre>
<blockquote>
<p>sort 메서드 관련 아티클
<a href="https://reactjs.winterlood.com/fc0a951e-41cd-4cc5-8f47-7507965bbe41#8f2d70d5e8334377bb56f0a3f9101de2">https://reactjs.winterlood.com/fc0a951e-41cd-4cc5-8f47-7507965bbe41#8f2d70d5e8334377bb56f0a3f9101de2</a></p>
</blockquote>
<h2 id="4-tosorted">4. toSorted</h2>
<h3 id="정렬된-새로운-배열을-반환하는-메서드-가장-최근에-추가된-최신-함수">정렬된 새로운 배열을 반환하는 메서드 (가장 최근에 추가된 최신 함수)</h3>
<pre><code class="language-javascript">let arr4 = ['c', 'a', 'b'];
const sorted = arr5,toSorted();

console.log(arr4)  // ['c', 'a', 'b']
console.log(sorted)  // ['a', 'b', 'c']</code></pre>
<h2 id="5-join">5. join</h2>
<h3 id="배열의-모든-요소를-하나의-문자열로-합쳐서-반환하는-메서드">배열의 모든 요소를 하나의 문자열로 합쳐서 반환하는 메서드</h3>
<pre><code class="language-javascript">let arr5 = ['hi', 'im', 'winterlood'];
const joined = arr5.join(' ')

console.log(joined)  // hi im winterlood</code></pre>