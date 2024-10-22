<h2 id="6-1-프로토타입의-개념-이해">6-1 프로토타입의 개념 이해</h2>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/f2b92eb4-ab7d-40ab-9ef2-888fe403a01d/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/72b32e35-b17c-412e-b148-b2740944ded1/image.png" /></p>
<h3 id="6-1-1-constructor-prototype-instance">6-1-1 constructor, prototype, instance</h3>
<pre><code class="language-javascript">var instance = new Constructor();</code></pre>
<h4 id="personprototype">Person.prototype</h4>
<pre><code class="language-javascript">var Person = function (name) {
    this._name = name;
};
Person.prototype.getName = function() {
    return this._name;
};
var suzi = new Person('Suzi');
suzi.__proto__.getName(); // undefined (이유: __proto__ 객체에 name 프로퍼티가 없어서) 
// ⇒ **메서드**로서 호출 : 바로 앞의 객체가 this → suzi.__proto__ 

suzi.__proto__.name = 'suzi.__proto__';
suzi.__proto__.getName(); // suzi.__proto__ (__proto__ 객체에 name 프로퍼티에 할당 후)</code></pre>
<h3 id="6-1-2-constructor-프로퍼티">6-1-2 constructor 프로퍼티</h3>
<p>옅은색 : innumerable (열거할 수 없는 프로퍼티)
짙은색 : enumerable (열거 가능한 프로퍼티)</p>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/37ad1b6b-b3b9-4c45-9df8-aff4fdd29357/image.png" /></p>
<h4 id="모두-동일한-대상을-가리키는-코드">모두 동일한 대상을 가리키는 코드</h4>
<pre><code class="language-javascript">[Constructor]
[instance].__proto__.constructor
[instance].constructor
Object.getPrototypeOf([instance]).constructor
[Constructor].prototype.constructor</code></pre>
<h4 id="모두-동일한-객체prototype-접근-가능">모두 동일한 객체(prototype) 접근 가능</h4>
<pre><code class="language-javascript">[Constructor].prototype
[instance].__proto__
[instance]
Object.getPrototypeOf([instance])</code></pre>
<h2 id="6-2-프로토타입-체인">6-2 프로토타입 체인</h2>
<h3 id="6-2-1-메서드-오버라이드">6-2-1 메서드 오버라이드</h3>
<p>인스턴스가 동일한 이름의 프로퍼티 또는 메서드를 가지고 있는 상황에서 발생
원본이 그대로 있는 상태에서 다른 대항을 그 위에 얹는 이미지라고 생각</p>
<pre><code class="language-javascript">var Person = function(name) {
    this.name = name;
};
Person.prototype.getName = function (){
    return this.name;
};

var iu = new Person('지금');
iu.getName = function() {
    return '바로' + this.name;
};
console.log(iu.getName()); // 바로 지금

console.log(iu.__proto__.getName()); // undefined</code></pre>
<p>getName 메서드 찾는 방식 : 가장 가까운 대상인 자신의 프로퍼티 검색 → (없으면) proto 검색</p>
<h3 id="6-2-2-프로토타입-체인">6-2-2 프로토타입 체인</h3>
<p>프로토타입 체인 : 어떤 데이터의 proto 프로퍼티 내부에 다시 proto 프로퍼티가 연쇄적으로 이어진 것
⇒ 프로토타입 체이닝 : 프로토타입 체인을 따라가며 검색하는 것</p>
<p>데이터 자신의 프로퍼티들을 검색해서 원하는 메서드가 있으면 메서드를 실행하고, 없으면 <strong>proto</strong>를 검색해서 있으면 그 메서드를 실행하는 식으로 진행</p>
<h4 id="메서드-오버라이드와-프로토타입-체이닝">메서드 오버라이드와 프로토타입 체이닝</h4>
<pre><code class="language-javascript">var arr = [1,2];
Array.prototype.toString.call(arr); // 1,2
Object.prototype.toString.call(arr); // [Object Array]
arr.toString(); // 1,2

arr.toString = function(){
    return this.join('_');
};
arr.toString(); // 1_2 -&gt; Array.prototype.toString이 아닌 arr.toString이 실행된 것</code></pre>
<h3 id="6-2-3-객체-전용-메서드의-예외사항">6-2-3 객체 전용 메서드의 예외사항</h3>
<p>어떤 생성자 함수이든 prototype은 반드시 객체이기 때문에 Object.prototype이 언제나 프로토타입 체인의 최상단에 존재</p>
<h4 id="objectprototype에-추가한-메서드에의-접근">Object.prototype에 추가한 메서드에의 접근</h4>
<pre><code class="language-javascript">Object.prototype.getEntries = function() {
    var res = [];
    for (var prop in this) {
        if(this.hasOwnProperty(prop)) {
            res.push([prop, this[prop]]);
        }
    }
    return res;
};
var data = [
    ['object', {a: 1, b: 2, c: 3}], // [["a",1], ["b", 2], ["c", 3]]
    ['number', 345], // []
    ['string', 'abc'], // [["0", "a"], ["1", "b"], ["2", "c"]]
    ['boolean', false], // []
    ['func', function(){}], // []
    ['array', [1, 2, 3]] // [["0", 1], ["1", 2], ["2", 3]]
];
data.forEach(function (datum){
    console.log(datum[1].getEntries());
});</code></pre>
<h3 id="6-2-4-다중-프로토타입-체인">6-2-4 다중 프로토타입 체인</h3>
<h4 id="grade-생성자-함수와-인스턴스">Grade 생성자 함수와 인스턴스</h4>
<pre><code class="language-javascript">var Grade = function() {
    var args = Array.prototype.slice.call(arguments);
    for(var i = 0; i &lt; args.length; i++){
        this[i] = args[i];
    }
    this.length = args.length;
};
var g = new Grade(100,100);</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/b8fb4b5d-43e8-4377-99fa-275a1cd2dbcd/image.jpg" /></p>
<p>서로 별개로 분리돼 있던 데이터가 연결되도록 설정</p>
<pre><code class="language-javascript">Grade.prototype = []; </code></pre>
<p><img alt="업로드중.." src="blob:https://velog.io/6cf16219-36fb-423e-8f78-25413d8bcce3" /></p>
<pre><code class="language-javascript">console.log(g); // Grade(2) [100, 80]
g.pop();        
console.log(g); // Grade(1) [100]
g.push(90);
console.log(g); // Grade(2) [100, 90]               </code></pre>