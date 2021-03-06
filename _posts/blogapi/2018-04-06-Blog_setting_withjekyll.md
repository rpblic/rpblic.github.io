---
layout: post
title: Jekyll을 활용한 블로그 세팅
category: Blogapi
tags: ['Jekyll', 'Blog']
---

### Tistory 블로그는 더 이상은 Naver...

저는 이전에는 티스토리의 블로그를 활용하고 있었습니다.  그렇지만 티스토리 블로그로는 제가 활용할 수 있는 한계가 너무 뚜렷했고, 포트폴리오를 만들기 위해 티스토리 블로그가 가진 한계를 활용할 수 없다고 생각했습니다.


티스토리 블로그로 할 수 없는 것은 이런 것들이었습니다:

* *Jupyter notebook* 파일을 활용할 수 없었습니다. 티스토리 블로그는 *highlight.js*를 활용하여 코드를 올리는 데만 해도 너무 많은 에러가 나타났고, *Jupyter notebook*의 결과로 나타나는 표나 사진을 올리기에는 너무 큰 시간 비용이 들었습니다.

* 보다 해커적인 플랫폼이 필요했습니다. 저는 원체 블로그 테마를 자주 바꾸고 싶어하는 성격이기도 하고, 블로그에 필요한 기능은 언제든 자유롭게 추가시키고 싶었습니다. 티스토리 블로그는 테마에 따라 포스트의 형태가 고정되는 경향이 강했고, 기능을 추가시키기에는 너무 정형적인 플랫폼이었습니다.<br>
저에게 필요한 기능은 *Evernote*와의 연계(저는 관심 있는 포스팅들을 *Evernote*로 정리하고 있었기 때문에 *Evernote*의 포스트를 가져와서 포스팅하고 싶었습니다), 코드 노출, *Jupyter notebook* 파일 노출 등이었습니다. 이 모든 일들은 티스토리 블로그로는 불가능한 일이었습니다.


### Jekyll 블로그 세팅

이런 저에게 눈에 들어온 두 가지 옵션은 *Wordpress*와 *Jekyll*이었습니다. 저는 그 중 *Jekyll*을 선택했습니다. 그 이유는 다음의 두 가지입니다.

* 우선, 너무나도 해커적입니다.
이후 얘기드리겠지만 저는 이후 *ever2simple*을 활용하여 *Evernote* 포스트를 연동할 예정입니다. 마치 라이브러리를 활용하는 것처럼요!<br>
또 저는 *Lanyon* 테마를 다운받고 이 테마에 Search.js, Category.js를 추가했습니다. *Liquid* 언어를 통해 포스팅을 모두 포함하는 json 파일을 만들고, 이 json 파일에서 포스팅을 찾아내는 Search.js 기능, 카테고리를 제가 포스팅한 모든 포스트에서 자동으로 찾아서 출력해 주는 Category.js(심지어 Vue.js로 동작합니다!)를 웹에서 찾아서 추가시킬 수 있었습니다. 이 모든 과정이 코드 추가를 통해 이루어집니다.

* 데이터 분석 관련 내용을 포스팅하기에 가장 적합합니다.<br>
위의 내용과도 연관되는 것 같습니다. 코드 기반의 플랫폼이기 때문에 *Jupyter notebook*을 활용하는 일도 매우 쉽고(*Jupyter notebook*의 테마도 *html* 파일을 통해 가져올 수 있었습니다!) 추후 다양한 시각화 결과를 보여 주기에도 적합해 보였습니다.

이런 판단에 따라 저는 *Jekyll*과 *Github page*를 통해 블로그를 세팅했습니다. 세팅한 내용은 다음과 같습니다.

#### github fork를 통해 블로그 제작
*Jekyll*의 좋은 점 중 하나는 블로그가 포크 한 번만으로 만들어진다는 사실입니다. 저는 [*Lanyon*][1] 테마를 포크해서 rpblic.github.io라는 이름으로 가져왔습니다.

#### 테마 커스터마이징
*Lanyon* 테마는 카테고리를 만들 때마다 해당 카테고리에 대한 인덱스 파일을 만들어 줘야 하는 문제가 있었습니다. 이러한 문제는 저에게는 매우 귀찮은 일이었습니다. <br>
저는 포스트를 적을 때마다 카테고리와 태그를 지정하고, 홈페이지를 열 때마다 모든 포스트에서 카테고리를 가져와 사이드바에 추가하도록 하는 코드를 추가했습니다. [제가 활용한 코드는 다음과 같습니다.][2]

또한 저는 제 블로그를 포스팅과 제 자신의 분석 효율성을 높이기 위한 수단으로 쓰고 싶었기 때문에, 제가 활용하고 싶은 포스트를 빠르게 찾는 일이 중요했습니다.<br>
이를 위해서는 블로그 내에서 제 포스트를 제가 찾을 수 있는 방법이 필요했습니다. 이를 위해 저는 블로그 상단에 검색창을 추가시켰습니다. [제가 활용한 코드는 다음과 같습니다.][3] 해당 포스트에서는 별도의 페이지로 검색창을 운영했지만 저는 제 블로그의 상단에 검색창을 위치시켜 놓았습니다.

#### *Jupyter notebook* 의 활용
블로그 포스트를 통해 최대한 *Jupyter notebook*을 원형에 맞게 올릴 수 있도록 하고자 했습니다. <br>
*Jupyter notebook*은 자체로 *Markdown*, *HTML* 형태로의 저장을 지원하고 있습니다. 따라서 *Jupyter notebook*의 지원은 문제가 되지 않았고, *Jupyter notebook* 고유의 프레임을 가져오는 것을 중점으로 했습니다. [제가 활용한 코드는 다음과 같습니다.][4]

#### *Slideshare* 의 활용
분석과 함께 제가 만든 ppt를 포스팅하기 위해 활용하고자 했던 방법 중 하나는 [*Photoswipe*][5]입니다. 우선 너무 ppt가 예쁘게 나왔습니다. 사실 *Slideshare*를 활용하고 싶지 않았던 이유 중 하나가 별로 예쁘지 않다는 것이었고, *Photoswipe*를 활용하면 꽤 블로그가 깔끔해질 것 같았습니다.<br>
그러나 *Photoswipe*를 사용하기에 가장 큰 문제점은 *Photoswipe*가 이미지 포스팅을 중심으로 하는 서비스였다는 것입니다. *Photoswipe*는 ppt를 지원하지 않아서 이를 활용하기 위해서는 모든 ppt 페이지를 이미지로 변환해서 포스팅해야 했습니다.<br>
이 과정을 반복하느니 차라리 *Slideshare*를 활용하고 말지라는 생각이 제일 커서 [*Slideshare*][6]의 iframe share를 활용해 ppt 파일을 포스팅했습니다. 그러나 *Slideshare*의 기능들이 지원되면서 보다 깔끔한 포스팅이 가능한 서비스가 있으면 바로 갈아탈 생각입니다.

#### *Marxico* 활용
*Markdown*을 활용하기 위해 저는 웹 앱인 [*Marxico*][7]를 활용하기로 했습니다. 그 선택의 가장 큰 이유는 *Evernoe*와의 연동 때문입니다. 저는 모든 스크랩을 *Evernote*로 하고 있습니다. 그래서 *Evernote*와의 연동은 저에게 가장 중요한 일이었고, *Evernote*가 지원하지 않는 *Markdown* 파일을 *Evernote*와 연동하고 싶었습니다.<br>
이 연동의 한 쪽 방향을 담당할 수 있는 서비스가 이 *Marxico*였습니다. 이 서비스는 *Markdown* 문법에 대한 설명과 활용을 도와 주었고, 제가 쓰는 *Markdown* 문서를 *Evernote*에 연동해 주었습니다.<br>
연동의 반대 방향을 위해 저는 [*ever2simple*][8]을 활용할 예정입니다. 이 api는 *Python*으로 개발되었고, *Evernote* 포스트를 txt 파일로 변환해 주는 api입니다. 이 api와 *Marxico*를 통해 저는 *Evernote*에 저장되어 있는 포스트를 제 블로그에 올리는 일, 블로그에 올릴 포스트를 *Evernote*에 저장하는 일을 모두 할 수 있게 됩니다.<br>


### 블로그 환경

이런 기능들을 통해 저는 블로그 포스팅 환경을 갖출 수 있었습니다. 제가 세팅한 블로그 포스팅 환경은 다음과 같습니다.

![Blog Setting](https://g.gravizo.com/svg?
@startuml;
Mobile->Desktop: Pushbullet: 포스팅에 필요한 정보 데스크탑으로 전달;
Mobile->Evernote: 외부 포스트 Evernote 포스트 형태로 저장;
Desktop-->Blog: 블로그 기능 추가;
Desktop->Blog: 포스팅, Jupyter notebook, Slideshare 활용;
Evernote->Blog: ever2simple: 외부 포스트 공유;
Blog->Evernote: Marxico: 블로그 포스트 동기화;
@enduml;
)

앞으로는 이런 환경 하에서 다양한 포스트를 올려 볼 생각입니다. 재미있는 사례나 생각들을 함께할 수 있었으면 좋겠습니다. :) 늦게나마 인사드리게 되어 반갑습니다! 잘 부탁드립니다.

[1]: https://github.com/poole/lanyon
[2]: https://cookieshake.github.io/posts/Jekyll-%EB%B8%94%EB%A1%9C%EA%B7%B8%EC%97%90-Category-%ED%8E%98%EC%9D%B4%EC%A7%80-%EB%A7%8C%EB%93%A4%EA%B8%B0
[3]: https://imyeonn.github.io/blog/blog/30/
[4]: https://nipunbatra.github.io/blog/2017/Jupyter-powered-blog.html
[5]: http://photoswipe.com/
[6]: https://www.slideshare.net/GyuminSim2
[7]: https://marxi.co/
[8]: https://github.com/claytron/ever2simple/tree/master/ever2simple

