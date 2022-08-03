# vim 명령어

## 한 걸음 물러나고 세 걸음 나아가기

```
var foo = "method("+argument+","+argument1+")";
```

- 사이에 공백 넣기

1. f+
2. s + <esc>
3. ;(다음 대상으로 이동): f로 찾은 +
4. .(마지막 변경을 반복)
5. (3, 4 반복)

```
var foo = "method(" + argument + "," + argument1 + ")";
```

## 직접 찾고 치환

... We're waiting for content before the site can go live...
...If you are content with this, let's go ahead with it...
...We'll launch as soon as we have the content...

content를 찾아 copy로 바꾸기

1. content로 커서 이동
2. \*명령어로 해당 단어 검색
3. cw(현재 커서가 위치한 곳의 단어를 삭제 후 끼워넣기 모드) copy 입력 후 ctrl + [
4. n (일치하는 다음 단어 찾기)
5. . (마지막 변경 반복)

## 단어 삭제하기

- dw, daw: 단어 삭제
- db: 커서 이전에 있는 단어 삭제

## 간단한 산술 실행 횟수 사용하기

```
.blog,.news { background-image: url(/sprite.png) }
.blog { background-position: 0 0 }
.news { background-position: -180px 0 }
```

1. 산술을 원하는 라인 전 어디에서든 커서 이동
2. 숫자<C-x>(ctrl + x) ex) 180<C-x>: -180 으로 계산 된다
   양수는 모르겠음

Practical Vim, by Drew Neil
Read Drew Neil' Practical Vim

## visual mode

### 선택 영역의 끝 전환하기

Select from here to here.

: 마지막 here의 h에 커서가 있을 떄 from 다음의 here부터 . 전까지 선택하기

1. vbb 또는 v2b로 from 다음의 here까지 선택
2. o를 입력해 영역을 다시 to 다음의 h로 선택
3. e를 입력해 커서가 위치한 단어의 마지막을 선택

### tag 안의 내용 선택 후 대문자로 변경

```
<a href="#">one</a>
<a href="#">two</a>
<a href="#">three</a>
```

1. 태그 시작 < 커서 위치
2. vit
3. U 또는 <C-~>

visual mode 대신 일반 오퍼레이터 명령 사용하기
(점 명령을 사용했을때 예상과 다른 방식으로 동작하는 경우가 있다.)
(visual방식으로 위의 태그안 내용을 대문자 변경시 three는 THRee로 위의 단어가 3글자여서 앞의 세 알파벳만 대문자로 변경이 됨)
(하지만 vscode에서는 전체 변경이 됨)

1. < 위치로 커서
2. gUit (it는 모션)
3. 다음 아래 단어 이동j 마지막 변경 반복 .

visual모드에서 점 명령어를 사용하려면 고려할 사항이 많아진다.

Chapter Page
Normal 15
Intert 31
Visual 44

아래처럼 바꾸기

## Chapter | Page

Normal | 15
Intert | 31
Visual | 44

1. chapter와 page 사이의 빈영역으로 이동
2. <C-v>비쥬얼 블록 모드로 진입
3. 3j로 열을 기준으로 여러 행 선택
4. x...를 눌러 영역 삭제 후 .로 마지막 변경 반복
5. gv로 마지막으로 선택했던 범위 재 선택
6. r|로 파이프 문자 삽입
7. 제일 상단으로 이동 후 yy(행단위 복사) p(붙여넣기)로 최상위 행 복사후
8. Vr- 행선택 replace - 로 한 행을 -로 변경

```
li.one    a{ background-image: url('/images/sprite.jpg'); }
li.two    a{ background-image: url('/images/sprite.jpg'); }
li.three  a{ background-image: url('/images/sprite.jpg'); }

# images -> component로 변경하기


li.one    a{ background-image: url('/component/sprite.jpg'); }
li.two    a{ background-image: url('/component/sprite.jpg'); }
li.three  a{ background-image: url('/component/sprite.jpg'); }
```

1. f/ /를 찾아 다음의 i위치로 이동
2. <C-v>로 비쥬얼 블록모드 진입
3. 2je로 남은 두줄도 선택 후 s까지 images단어 선택
4. c 로 끼워넣기 모드 진입
5. component 끼워넣기 모드
6. <C-[>로 일반 모드

```
var foo = 1
var bar = 'a'
var foobar = foo + bar

# 마지막에 ;찍기

var foo = 1
var bar = 'a'
var foobar = foo + bar

```

1. 가장 상위의 1의 위치로 이동
2. <C-v> 비쥬얼 블록모드 진입
3. jj$ 하위 두줄도 선택 후 라인 마지막으로 커서 이동
4. A; 커서 뒤로 입력모드 변경 후 ; 추가

var tpl = [
'<a href="{url}">{title}</a>'
]

url만 선택

1. r위치에서 vi}

"{url}"까지 선택

1. r위치에서 va"

a href="{url}"까지

1. r위치에서 vi>

['<a href="{url}">{title}</a>]선택

1. r위치 에서 va]

i: inside
a: around

{url}을 #으로 치환

1. ci"#

ci": "안의 내용을 치환 한다.
