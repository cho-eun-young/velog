<p><a href="https://school.programmers.co.kr/learn/courses/30/lessons/12900#qna">https://school.programmers.co.kr/learn/courses/30/lessons/12900#qna</a></p>
<h2 id="문제-설명">문제 설명</h2>
<p>가로 길이가 2이고 세로의 길이가 1인 직사각형모양의 타일이 있습니다. 이 직사각형 타일을 이용하여 세로의 길이가 2이고 가로의 길이가 n인 바닥을 가득 채우려고 합니다. 타일을 채울 때는 다음과 같이 2가지 방법이 있습니다.</p>
<p>타일을 가로로 배치 하는 경우
타일을 세로로 배치 하는 경우
예를들어서 n이 7인 직사각형은 다음과 같이 채울 수 있습니다.</p>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/57eb02c8-ec2d-45a0-9e8b-bb636e914d98/image.png" /></p>
<p>직사각형의 가로의 길이 n이 매개변수로 주어질 때, 이 직사각형을 채우는 방법의 수를 return 하는 solution 함수를 완성해주세요.</p>
<h2 id="제한사항">제한사항</h2>
<p>가로의 길이 n은 60,000이하의 자연수 입니다.
경우의 수가 많아 질 수 있으므로, 경우의 수를 1,000,000,007으로 나눈 나머지를 return해주세요.</p>
<h3 id="입출력-예">입출력 예</h3>
<p>n    / result
4    5</p>
<h2 id="입출력-예-설명">입출력 예 설명</h2>
<h3 id="입출력-예-1">입출력 예 #1</h3>
<p>다음과 같이 5가지 방법이 있다.
<img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/7c5a353b-03aa-4ecd-a773-a9368f667c78/image.png" /></p>
<pre><code class="language-javascript">function solution(n) {
    var answer = 0;
    let a = 2, b = 1;
    for(let i = 2; i &lt; n; i++){
        answer = (a + b) % 1000000007;
        b = a;
        a = answer;
    }
    return answer;
}</code></pre>
<ul>
<li>a = 2: 2x2 크기의 직사각형을 채우는 방법의 수 (2가지)</li>
<li>b = 1: 2x1 크기의 직사각형을 채우는 방법의 수 (1가지)</li>
<li>answer = (a + b) % 1000000007; </li>
<li><blockquote>
<p>현재 크기의 직사각형을 채우는 방법의 수를 계산</p>
</blockquote>
</li>
<li>b = a : 이전 단계의 값을 저장</li>
<li>a = answer : 현재 계산된 값을 다음 단계를 위해 저장</li>
</ul>
<hr />
<pre><code>* 🧩 피보나치 수열 ?
-&gt; n번째 경우의 수는 (n-1) + (n-2)
예시) 1, 1, 2, 3, 5, 8, 13, 21, ...

- 🧩 이 수열의 규칙은 ??
첫 번째 숫자 = 1
두 번째 숫자 = 1
세 번째 숫자부터는 = 앞의 두 숫자의 합

- 🧩 점화식으로 표현하면 ???
F(1) = 1
F(2) = 1
F(n) = F(n-1) + F(n-2) (n ≥ 3)

- 🧩 실제 계산 과정
1, 1 (초기값)
1 + 1 = 2
1 + 2 = 3
2 + 3 = 5
3 + 5 = 8

- 🧩 2 x n 타일링 문제도 비슷한 원리
F(1) = 1
F(2) = 2
F(n) = F(n-1) + F(n-2) (n ≥ 3)
점화식은 &quot;다음 값을 만드는 간단한 공식&quot;이라고 생각!!</code></pre><hr />
<p>DP문제를 공부해야겠다ㅜㅜ 🐢...</p>