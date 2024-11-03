<pre><code class="language-javascript">function solution(my_string, is_prefix) {
  return +my_string.startsWith(is_prefix);
}</code></pre>
<p>boolean 앞에 <strong>' + '</strong> 해주면 true는 1, false는 0으로 변환!!</p>
<hr />
<pre><code class="language-javascript">const str1 = 'Saturday night plans';

console.log(str1.startsWith('Sat'));
// Expected output: true

console.log(str1.startsWith('Sat', 3));
// Expected output: false
</code></pre>
<pre><code class="language-javascript">startsWith(searchString)
startsWith(searchString, position)
</code></pre>
<p>position Optional
searchString이 발견될 것으로 예상되는 시작 위치(searchString의 첫 번째 문자의 인덱스)입니다. 기본값은 0입니다.</p>