<pre><code class="language-javascript">function knapsack(W, wt, val, n) {
    // DP 테이블 초기화
    let K = Array(n + 1).fill().map(() =&gt; Array(W + 1).fill(0));

    // DP 테이블 채우기
    for (let i = 0; i &lt;= n; i++) {
        for (let w = 0; w &lt;= W; w++) {
            if (i === 0 || w === 0) {
                K[i][w] = 0;
            } else if (wt[i - 1] &lt;= w) {
                K[i][w] = Math.max(val[i - 1] + K[i - 1][w - wt[i - 1]], K[i - 1][w]);
            } else {
                K[i][w] = K[i - 1][w];
            }
        }
    }

    return K[n][W];
}

// 테스트
let val = [60, 100, 120];
let wt = [10, 20, 30];
let W = 50;
let n = val.length;

console.log(knapsack(W, wt, val, n));</code></pre>
<h3 id="코드분석">코드분석</h3>
<ol>
<li><p>2차원 DP 테이블 <code>K</code>를 생성합니다. <code>K[i][w]</code>는 처음 i개의 아이템과 무게 제한 w를 고려했을 때의 최대 가치를 저장합니다.</p>
</li>
<li><p><code>Array(n + 1).fill().map(() =&gt; Array(W + 1).fill(0))</code>를 사용하여 2차원 배열을 초기화합니다.</p>
</li>
<li><p>테이블을 bottom-up 방식으로 채웁니다. 각 단계에서 현재 아이템을 포함할지 말지 결정합니다.</p>
</li>
<li><p><code>Math.max()</code>를 사용하여 두 값 중 큰 값을 선택합니다.</p>
</li>
<li><p>최종적으로 <code>K[n][W]</code>가 문제의 해답이 됩니다.</p>
</li>
</ol>
<hr />
<h2 id="🤔-01-knapsack-problem-">🤔 0/1 Knapsack Problem ??</h2>
<blockquote>
<p>0/1 Knapsack Problem(0/1 배낭 문제)은 조합 최적화 문제의 한 유형.</p>
</blockquote>
<h3 id="주요특징">주요특징</h3>
<ol>
<li><p>목적: 주어진 무게 제한 내에서 가치의 합이 최대가 되도록 물건을 선택하는 것입니다.</p>
</li>
<li><p>제약 조건:</p>
<ul>
<li>각 물건은 고유한 무게와 가치를 가집니다.</li>
<li>배낭의 무게 제한이 있습니다.</li>
<li>각 물건은 선택하거나(1) 선택하지 않거나(0) 둘 중 하나만 가능합니다. 즉, 물건을 부분적으로 선택할 수 없습니다.</li>
</ul>
</li>
<li><p>문제 해결 방법: 주로 동적 계획법(Dynamic Programming)을 사용하여 해결합니다.</p>
</li>
<li><p>응용 분야: </p>
<ul>
<li>자원 할당 문제</li>
<li>예산 계획</li>
<li>투자 결정</li>
<li>물류 최적화</li>
</ul>
</li>
<li><p>특징:</p>
<ul>
<li>NP-hard 문제로, 입력 크기가 커지면 계산 복잡도가 급격히 증가합니다.</li>
<li>그리디 알고리즘으로는 최적해를 보장할 수 없습니다.</li>
</ul>
</li>
<li><p>변형: Fractional Knapsack Problem(분할 가능한 배낭 문제)과는 달리, 0/1 Knapsack Problem에서는 물건을 부분적으로 선택할 수 없습니다.</p>
</li>
</ol>
<hr />
<p>💻 reference 
<a href="https://jeonyeohun.tistory.com/86">https://jeonyeohun.tistory.com/86</a>
<a href="https://gsmesie692.tistory.com/113">https://gsmesie692.tistory.com/113</a></p>