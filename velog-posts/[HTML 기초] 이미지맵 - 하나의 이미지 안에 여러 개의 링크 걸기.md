<p>이미지맵은 하나의 이미지에 여러 개의 링크를 걸어야 할 때, 이미지의 특정한 영역에 링크를 걸어야할 때 사용한다.</p>
<p>이미지맵은 사각형 이미지맵, 원형 이미지맵, 다각형 이미지맵 세가지 유형이 있다.</p>
<p>다각형 이미지맵은 효율이 떨어져서 잘 사용하지 않으니 이미지맵 제너레이터를 사용하자.
<a href="https://www.image-map.net/">https://www.image-map.net/</a> &gt; 이미지맵 제너레이터 주소</p>
<br />
<hr />

<h3 id="1-사각형-이미지맵-링크-만들기">&lt;1&gt; 사각형 이미지맵 링크 만들기</h3>
<pre><code class="language-html">&lt;!--사각형 이미지맵--&gt;
&lt;img src=&quot;이미지 경로&quot; usemap=&quot;#coupon_down&quot;&gt;
&lt;map name=&quot;coupon_down&quot;&gt;
  &lt;area shape=&quot;rect&quot; coords=&quot;111,555,444.600&quot; href=&quot;#&quot; alt=&quot;쿠폰 다운로드&quot;&gt;
&lt;/map&gt;</code></pre>
<ul>
<li><p><code>&lt;img&gt;</code> 태그의 usemap 속성과 <code>&lt;map&gt;</code> 태그의 name 속성을 일치시켜줘야한다. (usemap 속성에는 #을 붙여줄 것.)</p>
</li>
<li><p>사각형 이미지 맵이기 때문에 area shape=&quot;rect&quot;</p>
</li>
<li><p>coords 속성은 좌표. 
<u>coords = &quot;왼쪽 상단 x, y 좌표값, 오른쪽 상단 x, y 좌표값&quot;</u></p>
<br />

</li>
</ul>
<p><strong>&lt;사용 예시&gt;</strong>
<img alt="" src="https://images.velog.io/images/jiwon_kim/post/6ce9e17a-4022-4dd7-8224-506be1eb6567/%EC%82%AC%EA%B0%81%ED%98%95%EC%9D%B4%EB%AF%B8%EC%A7%80%EB%A7%B5%EC%98%88%EC%8B%9C.png" /></p>
<p>마우스 커서가 안보이지만... 쿠폰 다운받기 부분에만 클릭이 된다.</p>
<br />
<hr />

<h3 id="2-원형-이미지맵-링크-만들기">&lt;2&gt; 원형 이미지맵 링크 만들기</h3>
<pre><code class="language-html">&lt;!--원형 이미지맵--&gt;
&lt;img src=&quot;img/browsers.png&quot; usemap=&quot;#browser&quot;&gt;
&lt;map name=&quot;browser&quot;&gt;
  &lt;area shape=&quot;circle&quot; coords=&quot;72,98,54&quot; href=&quot;#&quot; alt=&quot;&quot; title=&quot;브라우저&quot;&gt;
&lt;/map&gt;</code></pre>
<ul>
<li><p>사각형 이미지맵과 마찬가지로 <code>&lt;img&gt;</code> 태그의 usemap 속성과 <code>&lt;map&gt;</code> 태그의 name 속성을 일치시켜줘야한다. (usemap 속성에는 #을 붙여줄 것.)</p>
</li>
<li><p>원형 이미지맵이기 때문에 area shape=&quot;circle&quot;</p>
</li>
<li><p><u>coords = &quot;원의 중앙 x좌표, y좌표, 원의 반지름&quot;</u></p>
<br />


</li>
</ul>
<p><strong>&lt;사용예시&gt;</strong>
<img alt="" src="https://images.velog.io/images/jiwon_kim/post/52864038-5567-49b1-8285-34ae2faea8a4/%EC%9B%90%ED%98%95%EC%9D%B4%EB%AF%B8%EC%A7%80%EB%A7%B5%EC%98%88%EC%8B%9C.png" />
여러개의 이미지를 링크해 줄 때는 map 태그 안의 area 태그를 여러개로 사용하면 된다.
각 브라우저 이미지마다 클릭된다.</p>
<br />
<hr />

<h3 id="📌-좌표값-확인하는-방법">📌 좌표값 확인하는 방법</h3>
<p><img alt="" src="https://images.velog.io/images/jiwon_kim/post/5e372828-1ad2-46e0-87fd-08c5eb0b4153/%EA%B7%B8%EB%A6%BC%ED%8C%90.png" />
그림판으로 좌표값을 확인할 이미지를 불러오면 커서의 위치에 해당하는 좌표값을 밑에 노란색 박스 표시가 되어있는 부분에서 확인해 볼 수 있다. 
해당 이미지의 좌표값은 x축 73px, y축 96px이다.
<br /></p>
<h3 id="📌-원의-반지름-구하기">📌 원의 반지름 구하기</h3>
<p><img alt="" src="https://images.velog.io/images/jiwon_kim/post/7246bb83-f8c1-4f85-bcc1-f653bf2122c0/%EB%B0%98%EC%A7%80%EB%A6%84.png" />
위와 마찬가지로 그림판에서 Select 선택 &gt; 반지름 만큼 드래그 해주면 밑에 노란 박스 표시에서 반지름을 알 수 있다.
해당 이미지에서는 가로 길이가 5px이고 세로 길이가 52px이니  52px이 원의 반지름이다.</p>