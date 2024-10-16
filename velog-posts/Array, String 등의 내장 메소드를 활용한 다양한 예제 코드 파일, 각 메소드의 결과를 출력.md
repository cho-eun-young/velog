<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/a49292e3-5414-464e-9c82-a28cdf680353/image.webp" /></p>
<h1 id="📌-array-메소드">📌 Array 메소드</h1>
<h3 id="📒-요소-추가제거-메소드">📒 요소 추가/제거 메소드</h3>
<ul>
<li>push(): 배열 끝에 요소 추가</li>
<li>pop(): 배열 끝에서 요소 제거 및 반환</li>
<li>unshift(): 배열 앞에 요소 추가</li>
<li>shift(): 배열 앞에서 요소 제거 및 반환</li>
<li>splice(): 배열의 특정 위치에 요소를 추가하거나 제거</li>
</ul>
<h3 id="📒-배열-변형-메소드">📒 배열 변형 메소드</h3>
<ul>
<li>concat(): 두 개 이상의 배열을 합침</li>
<li>slice(): 배열의 일부분을 새 배열로 반환</li>
<li>reverse(): 배열의 순서를 뒤집음</li>
<li>sort(): 배열을 정렬</li>
</ul>
<h3 id="📒-반복-메소드">📒 반복 메소드</h3>
<ul>
<li>forEach(): 배열의 각 요소에 대해 함수 실행</li>
<li>map(): 배열의 각 요소를 변환하여 새 배열 생성</li>
<li>filter(): 조건을 만족하는 요소로 새 배열 생성</li>
<li>reduce(): 배열의 요소를 하나의 값으로 줄임</li>
<li>some(): 하나라도 조건을 만족하는 요소가 있는지 확인</li>
<li>every(): 모든 요소가 조건을 만족하는지 확인</li>
</ul>
<h3 id="📒-검색-메소드">📒 검색 메소드</h3>
<ul>
<li>indexOf(): 지정된 요소의 첫 번째 인덱스 반환</li>
<li>lastIndexOf(): 지정된 요소의 마지막 인덱스 반환</li>
<li>find(): 조건을 만족하는 첫 번째 요소 반환</li>
<li>findIndex(): 조건을 만족하는 첫 번째 요소의 인덱스 반환</li>
<li>includes(): 배열에 특정 요소가 포함되어 있는지 확인</li>
</ul>
<h3 id="📒-기타-메소드">📒 기타 메소드</h3>
<ul>
<li><p>join(): 배열의 모든 요소를 문자열로 결합</p>
</li>
<li><p>flat(): 중첩 배열을 평탄화</p>
</li>
<li><p>fill(): 배열의 모든 요소를 특정 값으로 채움</p>
</li>
<li><p>code</p>
<pre><code class="language-jsx">  // 배열 생성
  const fruits = ['apple', 'banana', 'orange', 'grape'];
  console.log("Original array:", fruits);

  // push(): 배열 끝에 요소 추가
  fruits.push('kiwi');
  console.log("After push():", fruits);

  // pop(): 배열 끝에서 요소 제거 및 반환
  const lastFruit = fruits.pop();
  console.log("Popped element:", lastFruit);
  console.log("After pop():", fruits);

  // unshift(): 배열 앞에 요소 추가
  fruits.unshift('mango');
  console.log("After unshift():", fruits);

  // shift(): 배열 앞에서 요소 제거 및 반환
  const firstFruit = fruits.shift();
  console.log("Shifted element:", firstFruit);
  console.log("After shift():", fruits);

  // indexOf(): 요소의 인덱스 찾기
  const bananaIndex = fruits.indexOf('banana');
  console.log("Index of 'banana':", bananaIndex);

  // includes(): 요소 포함 여부 확인
  console.log("Includes 'orange'?", fruits.includes('orange'));

  // slice(): 배열의 일부분 추출
  const slicedFruits = fruits.slice(1, 3);
  console.log("Sliced fruits:", slicedFruits);

  // splice(): 요소 추가/제거
  fruits.splice(1, 1, 'pear', 'melon');
  console.log("After splice():", fruits);

  // forEach(): 각 요소에 대해 함수 실행
  fruits.forEach((fruit, index) =&gt; {
      console.log(`${index}: ${fruit}`);
  });

  // map(): 각 요소를 변환하여 새 배열 생성
  const upperFruits = fruits.map(fruit =&gt; fruit.toUpperCase());
  console.log("Uppercase fruits:", upperFruits);

  // filter(): 조건을 만족하는 요소로 새 배열 생성
  const longFruits = fruits.filter(fruit =&gt; fruit.length &gt; 5);
  console.log("Fruits with more than 5 characters:", longFruits);

  // reduce(): 배열의 요소를 하나의 값으로 줄임
  const totalLength = fruits.reduce((sum, fruit) =&gt; sum + fruit.length, 0);
  console.log("Total length of all fruits:", totalLength);

  // sort(): 배열 정렬
  fruits.sort();
  console.log("Sorted fruits:", fruits);

  // reverse(): 배열 순서 뒤집기
  fruits.reverse();
  console.log("Reversed fruits:", fruits);</code></pre>
  <aside>

<p>  // 출력 결과</p>
<p>  4Original array: [ 'apple', 'banana', 'orange', 'grape', 'mango' ]
  After push(): [ 'apple', 'banana', 'orange', 'grape', 'mango', 'kiwi' ]
  Popped fruit: kiwi
  After pop(): [ 'apple', 'banana', 'orange', 'grape', 'mango' ]
  After unshift(): [ 'pear', 'apple', 'banana', 'orange', 'grape', 'mango' ]
  Shifted fruit: pear
  After shift(): [ 'apple', 'banana', 'orange', 'grape', 'mango' ]
  Sliced fruits: [ 'banana', 'orange' ]
  After splice(): [ 'apple', 'banana', 'cherry', 'peach', 'grape', 'mango' ]
  forEach():
  0: apple
  1: banana
  2: cherry
  3: peach
  4: grape
  5: mango
  Uppercase fruits (map()): [ 'APPLE', 'BANANA', 'CHERRY', 'PEACH', 'GRAPE', 'MANGO' ]
  Long fruits (filter()): [ 'banana', 'cherry' ]
  First fruit starting with "p" (find()): peach
  Total length of all fruits (reduce()): 28
  Has fruit with length &lt; 5 (some()): true
  All fruits have length &gt; 3 (every()): true
  Index of "banana" (indexOf()): 1
  Array includes "mango" (includes()): true</p>
  </aside>


</li>
</ul>
<h1 id="📌-string-내장-메소드">📌 String 내장 메소드</h1>
<h3 id="📒-문자열-조작-메소드">📒 문자열 조작 메소드</h3>
<ul>
<li>concat(): 두 개 이상의 문자열을 결합</li>
<li>slice(): 문자열의 일부분을 추출</li>
<li>substring(): 두 인덱스 사이의 문자열을 추출</li>
<li>substr(): 특정 위치에서 시작하여 지정된 문자 수만큼 추출</li>
<li>replace(): 문자열 내의 특정 부분을 다른 문자열로 교체</li>
<li>replaceAll(): 문자열 내의 모든 일치하는 부분을 교체</li>
<li>trim(): 문자열 양 끝의 공백을 제거</li>
<li>trimStart(), trimLeft(): 문자열 시작 부분의 공백 제거</li>
<li>trimEnd(), trimRight(): 문자열 끝 부분의 공백 제거</li>
<li>padStart(): 문자열의 시작을 다른 문자열로 채움</li>
<li>padEnd(): 문자열의 끝을 다른 문자열로 채움</li>
</ul>
<h3 id="📒-문자열-검색-메소드">📒 문자열 검색 메소드</h3>
<ul>
<li>indexOf(): 지정된 값의 첫 번째 발생 인덱스를 반환</li>
<li>lastIndexOf(): 지정된 값의 마지막 발생 인덱스를 반환</li>
<li>search(): 정규 표현식과 매치되는 문자열을 검색</li>
<li>match(): 정규 표현식과 매치되는 문자열을 찾아 배열로 반환</li>
<li>includes(): 문자열에 특정 문자열이 포함되어 있는지 확인</li>
</ul>
<h3 id="📒-문자열-변환-메소드">📒 문자열 변환 메소드</h3>
<ul>
<li>toLowerCase(): 문자열을 소문자로 변환</li>
<li>toUpperCase(): 문자열을 대문자로 변환</li>
<li>toString(): 문자열 객체를 문자열 원시값으로 변환</li>
</ul>
<h3 id="📒-문자-접근-메소드">📒 문자 접근 메소드</h3>
<ul>
<li>charAt(): 지정된 인덱스의 문자를 반환</li>
<li>charCodeAt(): 지정된 인덱스의 문자의 Unicode 값을 반환</li>
</ul>
<h3 id="📒-문자열-분할-메소드">📒 문자열 분할 메소드</h3>
<ul>
<li>split(): 문자열을 지정된 구분자를 기준으로 분할하여 배열로 반환</li>
</ul>
<h3 id="📒-기타-메소드-1">📒 기타 메소드</h3>
<ul>
<li><p>repeat(): 문자열을 지정된 횟수만큼 반복</p>
</li>
<li><p>startsWith(): 문자열이 지정된 문자열로 시작하는지 확인</p>
</li>
<li><p>endsWith(): 문자열이 지정된 문자열로 끝나는지 확인</p>
</li>
<li><p>code</p>
<pre><code class="language-jsx">  // 샘플 문자열
  let str = "  Hello, World!  ";
  console.log("Original string:", str);

  // length: 문자열 길이
  console.log("Length:", str.length);

  // trim(): 양쪽 공백 제거
  console.log("Trimmed:", str.trim());

  // toLowerCase(): 소문자로 변환
  console.log("Lowercase:", str.toLowerCase());

  // toUpperCase(): 대문자로 변환
  console.log("Uppercase:", str.toUpperCase());

  // charAt(): 특정 위치의 문자 반환
  console.log("Character at index 7:", str.charAt(7));

  // indexOf(): 부분 문자열의 위치 찾기
  console.log("Index of 'World':", str.indexOf("World"));

  // slice(): 부분 문자열 추출
  console.log("Slice (7, 12):", str.slice(7, 12));

  // substring(): 부분 문자열 추출 (다른 방식)
  console.log("Substring (7, 12):", str.substring(7, 12));

  // replace(): 부분 문자열 교체
  console.log("Replace 'World' with 'JavaScript':", str.replace("World", "JavaScript"));

  // split(): 문자열을 배열로 분할
  console.log("Split by comma:", str.split(","));

  // startsWith(): 특정 문자열로 시작하는지 확인
  console.log("Starts with 'Hello':", str.trim().startsWith("Hello"));

  // endsWith(): 특정 문자열로 끝나는지 확인
  console.log("Ends with '!':", str.trim().endsWith("!"));

  // includes(): 부분 문자열 포함 여부 확인
  console.log("Includes 'World':", str.includes("World"));

  // repeat(): 문자열 반복
  console.log("Repeat 'Hi' 3 times:", "Hi ".repeat(3));

  // padStart(): 문자열 앞에 패딩 추가
  console.log("Pad start:", "5".padStart(3, "0"));

  // padEnd(): 문자열 뒤에 패딩 추가
  console.log("Pad end:", "5".padEnd(3, "0"));

  // concat(): 문자열 연결
  console.log("Concat:", "Hello".concat(" ", "World"));

  // 템플릿 리터럴 사용 (ES6+)
  let name = "Alice";
  console.log(`Hello, ${name}!`);</code></pre>
  <aside>

<p>  // 출력 결과</p>
<p>  Original string:   Hello, World!</p>
<p>  Length: 17
  Trimmed: Hello, World!
  Lowercase:   hello, world!</p>
<p>  Uppercase:   HELLO, WORLD!</p>
<p>  Character at index 8: W
  Index of "World": 8
  Slice (7, 12): World
  Replace "World" with "JavaScript":   Hello, JavaScript!</p>
<p>  Split by comma: ['  Hello', ' World!  ']
  Starts with "  Hello": true
  Ends with "!  ": true
  Includes "World": true
  Repeat 2 times: Hello, World!Hello, World!
  Substring (7, 12): World
  Concat: Hello, World! Welcome to JavaScript!</p>
  </aside></li>
</ul>