<blockquote>
<p><a href="https://school.programmers.co.kr/learn/courses/30/lessons/92335">https://school.programmers.co.kr/learn/courses/30/lessons/92335</a></p>
</blockquote>
<h3 id="문제-설명">문제 설명</h3>
<p>양의 정수 n이 주어집니다. 이 숫자를 k진수로 바꿨을 때, 변환된 수 안에 아래 조건에 맞는 소수(Prime number)가 몇 개인지 알아보려 합니다.</p>
<p>0P0처럼 소수 양쪽에 0이 있는 경우
P0처럼 소수 오른쪽에만 0이 있고 왼쪽에는 아무것도 없는 경우
0P처럼 소수 왼쪽에만 0이 있고 오른쪽에는 아무것도 없는 경우
P처럼 소수 양쪽에 아무것도 없는 경우
단, P는 각 자릿수에 0을 포함하지 않는 소수입니다.
예를 들어, 101은 P가 될 수 없습니다.
예를 들어, 437674을 3진수로 바꾸면 211020101011입니다. 여기서 찾을 수 있는 조건에 맞는 소수는 왼쪽부터 순서대로 211, 2, 11이 있으며, 총 3개입니다. (211, 2, 11을 k진법으로 보았을 때가 아닌, 10진법으로 보았을 때 소수여야 한다는 점에 주의합니다.) 211은 P0 형태에서 찾을 수 있으며, 2는 0P0에서, 11은 0P에서 찾을 수 있습니다.</p>
<p>정수 n과 k가 매개변수로 주어집니다. n을 k진수로 바꿨을 때, 변환된 수 안에서 찾을 수 있는 위 조건에 맞는 소수의 개수를 return 하도록 solution 함수를 완성해 주세요.</p>
<h3 id="제한사항">제한사항</h3>
<p>1 ≤ n ≤ 1,000,000
3 ≤ k ≤ 10</p>
<h3 id="입출력-예">입출력 예</h3>
<p>n    /    k     / result
437674    3    3
110011    10    2</p>
<pre><code class="language-javascript">function solution(n, k) {
    let result = '';
  // k진법 변환
    while (n &gt; 0) {
        result = (n % k) + result;
        n = Math.floor(n / k);
    }

  // 문자열 분할
    return result.split('0').filter((num) =&gt; {
        if (num === '' || num === '1'){
          return false;  
        } 

        const n = parseInt(num, 10); // 211 2 11 , 11 11

      // 소수 판별
        for (let i = 2; i &lt;= Math.sqrt(n); i++) {
            if (n % i === 0){
              return false;  
            } 
        }
        return n &gt; 1;
    }).length;
}
</code></pre>
<h3 id="풀이">풀이</h3>
<ul>
<li>변환된 수(result)를 '0'을 기준으로 나눕니다(split('0')).</li>
</ul>
<hr />
<ul>
<li><p>각 부분에 대해 소수인지 판별합니다</p>
<ul>
<li>빈 문자열이거나 '1'인 경우는 제외합니다.</li>
<li>2부터 해당 수의 제곱근까지 나누어 떨어지는지 확인합니다.</li>
<li>나누어 떨어지는 수가 없고, 1보다 큰 경우 소수로 판정합니다.</li>
</ul>
</li>
<li><p>filter 함수를 사용해 소수인 경우만 남깁니다.</p>
</li>
<li><p>최종적으로 소수의 개수(length)를 반환합니다.</p>
</li>
</ul>
<p>** 시간복잡도 **
k진법 변환: O(log_k n)
문자열 분할: O(n)
소수 판별: 최악의 경우 O(n * sqrt(m))</p>
<hr />
<p>소수 찾을때는 Math.sqrt 를 이용하자!!</p>