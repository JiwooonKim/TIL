HTML에서 doctype은 모든 문서의 최상단에서 찾을 수 있는 필수 서문이다.

# 1. DOCTYPE이란?

document type의 약어로, 웹 문서가 어떤 형식으로 작성되었는지 문서 형식을 선언하여 브라우저에게 알려주는 것.

# 2. DOCTYPE의 종류

1. **엄격모드 (strict)**
   문법과 구조가 모두 정확히 맞아야한다.

2. **호환모드 (transitional)**
   어느 정도 구버전의 속성 태그들을 허용한다.

3. **프레임셋 모드 (frameset)**
   프레임셋을 이용해 제작한 웹페이지의 경우에만 사용된다.

# 3. DOCTYPE을 쓰는 이유

DOCTYPE을 선언하면 표준 모드로 렌더링하고,
DOCTYPE을 선언하지 않을 경우 쿼크 모드로 렌더링 해서 각 브라우저마다 다른 형태의 결과물을 보여준다.
이것을 방지하기 위해 문서 형식 선언을 하며 이로 인해 HTML 문서를 표준 모드로 렌더링 할 수 있게된다.

## 쿼크 모드(Quirks mode)?

오래된 웹 브라우저를 위해 표준모드를 대신하여 쓰이는 렌더링 모드.
예전에 만들어진 비표준 웹 페이지들이 최신 버전의 브라우저에서 깨져보이지 않으려는 목적이다.

## 표준 모드(Standard mode)?

W3C등의 표준을 준수하는 렌더링 모드.

> **렌더링** : 서버로부터 HTML파일을 받아 브라우저에 뿌려주는 과정.

<hr>

HTML5의 등장으로 웹표준이 정착해가고 있기 때문에 <!DOCTYPE html> 선언을 주로 하지만
HTML4.01, XHTML의 경우 선언부가 다르다.

### **1. HTML 4.01**

버전: HTML 4.01 Strict (엄격모드)
선언부:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

버전 : HTML 4.01 Transitional (호환모드)
선언부:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN""http://www.w3.org/TR/html4/loose.dtd">
```

버전 : HTML 4.01 Frameset (프레임셋모드)
선언부 :

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
```

### 2. XHTML1.0

버전 : XHTML 1.0 Strict (엄격모드)
선언부 :

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
```

버전 : XHTML 1.0 Transitional (호환모드)
선언부 :

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

버전 : XHTML 1.0 Frameset (프레임셋모드)
선언부 :

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
```
