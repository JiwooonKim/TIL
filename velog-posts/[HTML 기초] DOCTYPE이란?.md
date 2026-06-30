<p>HTML에서 doctype은 모든 문서의 최상단에서 찾을 수 있는 필수 서문이다.</p>
<h3 id="doctype이란">!DOCTYPE이란?</h3>
<p>document type의 약어로,
웹 문서가 어떤 형식으로 작성되었는지 문서 형식을 선언하는 것이다.</p>
<hr />

<h3 id="doctype을-쓰지않을-경우-어떻게-되는가">!DOCTYPE을 쓰지않을 경우 어떻게 되는가?</h3>
<p>웹 브라우저는 문서 형식 선언이 없으면 쿼크 모드로 렌더링 해서 각 브라우저마다 다른 형태의 결과물을 보여준다.
이것을 방지하기 위해 문서 형식 선언을 하며 이로 인해 HTML 문서를 표준모드로 렌더링 할 수 있게된다.</p>
<p><strong>+ 쿼크 모드(Quirks mode)?</strong>
<small>오래된 웹 브라우저를 위해 디자인된 웹 페이지의 하위 호환성을 유지하기 위해 표준모드를 대신하여 쓰이는 렌더링 모드.오래된 웹 페이지들이 최신 버전의 브라우저에서 깨져보이지 않으려는 목적.</small></p>
<p><strong>+ 표준 모드(Standard mode)?</strong>
<small>W3C등의 표준을 준수하는 렌더링 모드.</small></p>
<p><small><span style="color: gray;">렌더링 : 서버로부터 HTML파일을 받아 브라우저에 뿌려주는 과정.</span></small></p>
<hr />

<br />
HTML5의 등장으로 웹표준이 정착해가고 있기 때문에 
!DOCTYPE HTML 선언을 주로 하지만
HTML4.01, XHTML의 경우 선언부가 다르다.


<p><strong>1. HTML 4.01</strong></p>
<blockquote>
<p>버전: HTML 4.01 Strict
선언부: <code>&lt;!DOCTYPE HTML PUBLIC &quot;-//W3C//DTD HTML 4.01//EN&quot; &quot;http://www.w3.org/TR/html4/strict.dtd&quot;&gt;</code></p>
</blockquote>
<blockquote>
<p>버전 : HTML 4.01 Transitional
선언부: <code>&lt;!DOCTYPE HTML PUBLIC &quot;-//W3C//DTD HTML 4.01 Transitional//EN&quot;&quot;http://www.w3.org/TR/html4/loose.dtd&quot;&gt;</code></p>
</blockquote>
<blockquote>
<p>버전  : HTML 4.01 Frameset
선언부  :  <code>&lt;!DOCTYPE HTML PUBLIC &quot;-//W3C//DTD HTML 4.01 Frameset//EN&quot; &quot;http://www.w3.org/TR/html4/frameset.dtd&quot;&gt;</code></p>
</blockquote>
<p><strong>2. XHTML1.0</strong></p>
<blockquote>
<p>버전  :  XHTML 1.0 Strict
선언부  :  <code>&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Strict//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd&quot;&gt;</code></p>
</blockquote>
<blockquote>
<p>버전  :  XHTML 1.0 Transitional
선언부  :  <code>&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;</code></p>
</blockquote>
<blockquote>
<p>버전  :  XHTML 1.0 Frameset
선언부  :  <code>&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Frameset//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd&quot;&gt;</code></p>
</blockquote>