<h2 id="1-foreach">1. forEach</h2>
<h3 id="--모든-요소를-순회하면서--각각의-요소에-특정-동작을-수행시키는-메서드">-&gt; 모든 요소를 순회하면서 , 각각의 요소에 특정 동작을 수행시키는 메서드</h3>
<pre><code class="language-javascript">let arr1 = [1, 2, 3];

arr1.forEach(function (item, idx, arr) {
    console.log(idx, item * 2); // 0 2  1 4  2 6
}


let doubledArr = [];

arr1.forEach((item) =&gt; {
  doubledArr.push(item * 2);
})

console.log(doubledArr); // [2, 4, 6]</code></pre>
<h2 id="2-includes">2. includes</h2>
<h3 id="배열에-특정-요소가-있는지-확인하는-메서드">배열에 특정 요소가 있는지 확인하는 메서드</h3>
<pre><code class="language-javascript">let arr2 = [1, 2, 3];
let isInclude = arr2.includes(3); 

console.log(isInclude) // true</code></pre>
<h2 id="3-indexof">3. indexOf</h2>
<h3 id="특정-요소의-인덱스위치를-찾아서-반환하는-메서드">특정 요소의 인덱스(위치)를 찾아서 반환하는 메서드</h3>
<pre><code class="language-javascript">let arr3 = [1, 2, 3];
let index = arr3.indexOf(2); 

console.log(index) // 1</code></pre>
<h2 id="4-findindex">4. findIndex</h2>
<h3 id="모든-요소를-순회하면서--콜백함수를-만족하는-특정-요소의-인덱스위치를-반환하는-메서드">모든 요소를 순회하면서 , 콜백함수를 만족하는 특정 요소의 인덱스(위치)를 반환하는 메서드</h3>
<pre><code class="language-javascript">let arr4 = [1, 2, 3];
let findedIndex = arr4.findeIndex((item) =&gt; {
    if(item % 2 !== 0) return true;
}); 

// 또는 이렇게 작성
let findedIndex = arr4.findeIndex((item) =&gt; item % 2 !== 0); 

console.log(findedIndex) // 0</code></pre>
<h2 id="indexof는-얕은비교로-객체-인덱스를-찾지-못한다-반면-findeindex는-객체-인덱스를-찾을-수-있다">indexOf는 얕은비교로 객체 인덱스를 찾지 못한다. 반면 findeIndex는 객체 인덱스를 찾을 수 있다.</h2>
<pre><code class="language-javascript">let objectArr = [
    {name: '이정환'},
    {name: '홍길동'},
];

console.log(
    objectArr.indexOf({ name: '이정환'}); // -1
)

console.log(
    objectArr.findeIndex(
        (item) =&gt; item.name === '이정환'
    ); // 0
)</code></pre>
<h2 id="find">find</h2>
<h3 id="모든-요소를-순회하면서-콜백함수를-만족하는-요소를-찾는데-요소를-그대로-반환">모든 요소를 순회하면서 콜백함수를 만족하는 요소를 찾는데, 요소를 그대로 반환</h3>
<pre><code class="language-javascript">let arr5 = [
    {name: '이정환'},
    {name: '홍길동'},
];

const finded = arr5.finc(
    (item) =&gt; item.name === '이정환';
);

console.log(finded); // {name: '이정환'}</code></pre>