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
.blog { background-position: -8 0 }
.news { background-position: -180px 0 }
```

1. 산술을 원하는 라인 전 어디에서든 커서 이동
2. 숫자<C-x>(ctrl + x) ex) 180<C-x>: -180 으로 계산 된다
   양수는 모르겠음
