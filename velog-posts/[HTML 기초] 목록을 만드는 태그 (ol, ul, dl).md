<p>목록을 만드는 태그들을 정리해보겠습니다. </p>
<h3 id="1-순서가-있는-리스트-ol">1. 순서가 있는 리스트: ol</h3>
<p><code>&lt;ol&gt;</code>은 ordered list의 약자로 순서를 표시하는 리스트이다.</p>
<pre><code class="language-html">&lt;!--순서가 있는 목록--&gt;
  &lt;ol&gt;
    &lt;li&gt;사과&lt;/li&gt;
    &lt;li&gt;바나나&lt;/li&gt;
    &lt;li&gt;배&lt;/li&gt;
  &lt;/ol&gt;</code></pre>
<p>✨ <strong>출력결과</strong>
 <ol type="">
    <li>사과</li>
    <li>바나나</li>
    <li>배</li>
 </ol></p>
<p>ol은 태그 안에 type이라는 속성을 이용해 다른 순서 목록(영문자, 로마자)을 이용할 수 있다. 기본값은 <code>ol type=&quot;1&quot;</code>로 지정되어 있다.
<img alt="" src="https://images.velog.io/images/jiwon_kim/post/fd5d6604-5e1d-46d0-83d5-278c8cecc762/ol%20%EC%86%8D%EC%84%B1.PNG" /></p>
<hr />

<h3 id="2-순서가-없는-리스트-ul">2. 순서가 없는 리스트: ul</h3>
<p><code>&lt;ul&gt;</code>은 unordered list의 약자로 순서가 없는 리스트이다.</p>
<pre><code class="language-html">&lt;ul&gt;
  &lt;li&gt;사과&lt;/li&gt;
  &lt;li&gt;바나나&lt;/li&gt;
  &lt;li&gt;배&lt;/li&gt;
&lt;/ul&gt;</code></pre>
<p>✨ <strong>출력결과</strong></p>
<ul type="disc">
  <li>사과</li>
  <li>바나나</li>
  <li>배</li>
</ul>

<p>ul은 태그 안에 type이라는 속성을 이용해 다른 bullet (텍스트 앞에 붙는 기호) 스타일을 사용 할 수 있다. 
속성 값으로는 circle, squre, disc이 있으며 기본 값은 <code>ul type=&quot;disc&quot;</code>로 설정되어 있다.</p>
<hr />

<h3 id="3-정의-리스트-dl-dt-dd">3. 정의 리스트: dl, dt, dd</h3>
<p><code>&lt;dl&gt;</code>는  description list ,<code>&lt;dt&gt;</code>는 description term,<code>&lt;dd&gt;</code>는 description details의 약자이다.
<span style="color: #8a8a8a;">(내가 배웠을 때는 다른 약자로 배웠으나 MDN의 표기대로 작성함)</span></p>
<pre><code>&lt;dl&gt;
  &lt;dt&gt;목록이란?&lt;/dt&gt;
  &lt;dd&gt;
     어떤 물품의 이름을 일정한 순서로 적은 것. 카탈로그.
  &lt;/dd&gt;
&lt;/dl&gt;</code></pre><p>✨ <strong>출력결과</strong></p>
<dl>
  <dt>목록이란?</dt>
  <dd>
     어떤 물품의 이름을 일정한 순서로 적은 것. 카탈로그.
  </dd>
</dl>

<br />

<p><code>&lt;dl&gt;``&lt;dt&gt;``&lt;dd&gt;</code>는 1:1로 쌍을 이룰 때 사용하는 것을 권장한다.
스크린 리더는 <code>&lt;dt&gt;``&lt;dd&gt;</code>가 1:1로 쌍을 이룰 때 사용하는 것이 정확한 의미를 읽어내어 스크린 리더 이용자의 이해가 쉬워진다.</p>
<hr />

<h3 id="-리스트를-중첩-할-때">+ 리스트를 중첩 할 때</h3>
<p>리스트를 리스트 안에 중첩해서 사용 할 때는</p>
<pre><code>&lt;ol type=&quot;&quot;&gt;
  &lt;li&gt;사과
    &lt;ul&gt;
      &lt;li&gt;홍옥&lt;/li&gt;
      &lt;li&gt;황옥&lt;/li&gt;
    &lt;/ul&gt;
  &lt;/li&gt;
  &lt;li&gt;바나나&lt;/li&gt;
  &lt;li&gt;배&lt;/li&gt;
&lt;/ol&gt;</code></pre><p>이런 식으로 <code>&lt;li&gt;</code> 안에 자식 요소로 들어갈 수 있도록 해줘야한다.</p>