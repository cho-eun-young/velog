<h2 id="7-1-클래스와-인스턴스의-개념-이해">7-1 클래스와 인스턴스의 개념 이해</h2>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/27637741-8114-496b-b8c5-e3e6893c179d/image.png" />
자바스크립트는 프로토 타입 기반 언어라서 '상속'개념이 존재하지 않지만, ES6 이후 클래스 문법이 추가되고, 클래스 문법에서도 일정 부분은 프로토타입을 활용하고 있습니다.</p>
<p>class라는 의미는 '계급, 집단, 집합'등의 의미로 번역됩니다. 프로그래밍 언어적으로도 동일한 개념으로 접근하면 됩니다.</p>
<h2 id="7-2-자바스크립트의-클래스">7-2 자바스크립트의 클래스</h2>
<p>프로토타입을 일반적인 의미에서의 클래스 관점에서 접근해보면, 비슷하게 해석할 수 있는 요소가 있다.
 
생성자 함수 Array를 new 연산자와 함께 호출하면 인스턴스가 생성된다.
이때 Array를 일종의 클래스라고 하면, Array의 prototype 객체 내부 요소들이 인스턴스에 '상속'된다고 볼 수 있다.
프로토타입 체이닝에 의한 참조가 결과적으로는 클래스의 상속과 동일하게 동작하기 때문.
한편 Array 내부 프로퍼티들 중 prototype 프로퍼티를 제외한 나머지는 인스턴스에 상속되지 않는다.
 
인스턴스에 상속되는지(인스턴스가 참조하는지) 여부에 따라 스태틱 멤버(static member)와 인스턴스 멤버(instance member)로 나뉜다. 이 분류는 다른 언어의 클래스 구성요소에 대한 정의를 차용한 것으로서 클래스 입장에서 사용 대상에 따라 구분한 것.</p>
<h4 id="스태틱-메서드-프로토타입-메서드">스태틱 메서드, 프로토타입 메서드</h4>
<pre><code class="language-javascript">var Rectangle = function (width, height){ // 생성자
    this.width = width;
    this.height = height;
};
Rectabgle.prototype.getArea = function (){ // (프로토타입) 메서드
    return this.width * this.heigth;
};
Rectabgle.isRectangle = function (instance){ // 스태틱 메서드
    return instance instanceof Rectangle &amp;&amp; 
        instance.width &gt; 0 &amp;&amp; instance.height &gt; 0;
};

var rect1 = new Rectangle(3, 4)
console.log(rect1.getArea()); // 12 (o) (프로토타입 메서드)
console.log(rect1.isRectangle(rect1)); // Error (x)
console.log(Rectangle.isRectangle(rect1)); // true</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/eunyoung224/post/42118cf2-f97c-4219-98fa-7db749d67af5/image.png" /></p>
<p>일반적인 사용 방식, 즉 구체적인 인스턴스가 사용할 메서드를 정의한 '틀' 역할을 담당하는 목적을 가질 때의 클래스는 추상적인 개념이다.
하지만 클래스 자체를 this로 해서 직접 접근해야만 하는 스태틱 메서드를 호출할 때의 클래스는 그 자체가 하나의 개체로서 취급된다.</p>
<h2 id="7-3-클래스-상속">7-3 클래스 상속</h2>
<p>클래스 상속은 객체지향에서 가장 중요한 요소 중 하나이다. 이때문에 ES5까지의 자바스크립트 커뮤니티에서는 클래스 상속을 다른 객체지향 언어에 익숙한 개발자들에게 최대한 친숙한 형태로 흉내내는 것이 주요한 관심사였다.</p>
<h4 id="grade-생성자-함수-및-인스턴스">Grade 생성자 함수 및 인스턴스</h4>
<pre><code class="language-javascript">var Grade = function () {
     var args = Array.prototype.slice.call(arguments);
    for (var i = 0'; i &lt; args.length; t++) {
        this[i] = args[i];
    }
    this.length = args.length;
};
var g = new Grade(100, 80);</code></pre>
<p>ES5까지의 자바스크립트에는 클래스가 없었기 때문에, 이는 결국 프로토타입 체이닝을 잘 연결한 것으로 이해할 수 있다.
다만, 세부적으로 완벽하게 superclass와 subclass의 구현이 이루어진 것은 아니다.
 
length 프로퍼티가 configurable(삭제가능)하다는 점과, Grade.prototype에 빈 배열을 참조시켰다는 점에서 문제가 발생한다.</p>
<h4 id="length-프로퍼티를-삭제한-경우">length 프로퍼티를 삭제한 경우</h4>
<pre><code class="language-javascript">...
g.push(90);
console.log(g) // Grade {0: 100, 1: 80, 2: 90, length: 3};

delete.g.length;
g.push(70);
console.log(g) // Grade {0: 70, 1: 80, 2: 90, length: 1};</code></pre>
<h4 id="요소가-있는-배열을-prototype에-매칭한-경우">요소가 있는 배열을 prototype에 매칭한 경우</h4>
<pre><code class="language-javascript">...
Grade.prototype = ['a', 'b', 'c', 'd'];
var g = new Grade(100, 80);

g.push(90);
console.log(g); // Grade {0: 100, 1: 80,, 2: 90, length: 3};

delete g.length;
g.push(70);
console.log(g); // Grade {0: 100, 1: 80, 2: 90, __4: 70, length: 5}</code></pre>
<h2 id="7-4-es6의-클래스-및-클래스-상속">7-4 ES6의 클래스 및 클래스 상속</h2>
<h4 id="es5와-es6의-클래스-문법-비교">ES5와 ES6의 클래스 문법 비교</h4>
<pre><code class="language-javascript">var ES5 = function (name){
    this.name = name;
};
ES5.staticMethod = function (){
    return this.name + ' method';
};
ES5.prototype.method = function (){
    return this.name + ' method';
};
var es5Instance = new ES5('es5');
console.log(ES5.staticMethod()); // es5 staticMethod
console.log(es5Instance.method()); // es5 method
---------------------------------
var ES6 = class { // 클래스 본문 영역
    constructor (name) { // function 키워드 생략해도 메서드로 인식 / 생성자 함수와 동일한 역할
        this.name = name;
    }
    static staticMethod () { // static 메서드임을 알림 / 생성자 함수 자신만이 호출 가능
        return this.name + ' staticMethod';
    }
    method () { // 자동으로 prototype 객체 내부에 할당되는 메서드
        return this.name + ' method';
    }
};
var es6Instance = new ES6('es6');
console.log(ES6.staticMethod()); // es6 staticMethod
console.log(es6Instance.method()); // es6 method</code></pre>
<h4 id="es6의-클래스-상속">ES6의 클래스 상속</h4>
<pre><code class="language-javascript">var Rectangle = class {
    constructor (width, heigth) {
        this.width = width;
        this.heigth = heigth;
    }
    getArea (){
        return this.width * this.heigth;
    }
};
var Square = class extends Rectangle { // 상속 관계 설정
    constructor (width) {
        super(width, width); // superClass의 constructor를 실행함
    }
    getArea() {
        console.log('size is : ', super.getArea());
    }
}</code></pre>