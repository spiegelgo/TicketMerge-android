# TicketMerge_android
 
## ⚡기획의도⚡
만들어진 **API**를 사용하여<br/>
안드로이드앱을 개발하자<br/>

## ✌데이터셋 정보✌
해당 데이터는<br/>
[멜론](https://ticket.melon.com/concert/index.htm?genreType=GENRE_CON, '멜론 티켓'),
[인터파크 티켓](https://tickets.interpark.com/contents/genre/concert, '인터파크 티켓'),
[티켓링크](https://www.ticketlink.co.kr/performance/14, '티켓링크'),
[Yes24](http://ticket.yes24.com/New/Genre/GenreMain.aspx?genre=15456, 'yes24 티켓')<br/>
에서 스크래핑하여 데이터를 가공하였습니다<br/><br/>

## 👍안드로이드 개발 과정👍
+ 먼저 팀원간 **코드 충돌을 막기 위한** 대책으로<br/>
+ 버전관리 및 소스코드 관리를 위해 기초가 되는 프래그먼트, 탭바 등 구현 후 **master 브랜치**에 저장후<br/>
+ 팀원간 **각자의 브랜치 생성하여 pull** 받아 파트 분배하여 각자 작업<br/>
+ 이후 각자 **기능을 하나 구현할 때마다 commit과 push** 후 변경사항을 **master 브랜치에 merge** 하여 소스코드 관리 하였음 <br/><br/>

1. 홈 화면에서는 **가로 리사이클러뷰**를 사용, 최근 업로드된 콘서트의 정보를 보여주고<br/>
장르별/지역별로 선택가능하고 추천순, 조회순, 공연임박순으로 정렬이 가능한 **세로 리사이클러뷰**를 사용하여 <br/>
콘서트 목록들을 보여주게 되는데, 이 때 회원/비회원 모두 가능하게 하기 위해<br/>
**addinterceptor**를 사용하여 **request 요청을 가로채** 인증토큰이 있는지 없는지 체크하여<br/>
있다면 **헤더에 토큰을 자동으로 추가**해주는 작업이 추가로 들어간다<br/>

1-1. 콘서트 목록에서 콘서트를 클릭하면 **상세페이지**가 나오게되며<br/>
콘서트에 대한 짧은 정보들과 함께 예매페이지의 링크가 있어서<br/>
더 자세히 보고 싶다거나, 예매를 하고 싶다면 링크를 클릭하여 넘어가면 된다 <br/><br/>

2. 검색 화면에서는 기본적으로 콘서트와 아티스트들을 검색하며<br/>
검색된 **아티스트의 정보와 공연목록**을 보여주게 되는데<br/>
아티스트의 정보는 있지만 해당 아티스트의 **공연정보가 없을 경우**,<br/>
**해당 아티스트를 좋아요**를 한 **유저**들이 **좋아요를 한 콘서트** 목록을 보여주게 된다<br/>

2-1. 이미지 검색에서는 아티스트의 이미지를 검색하면 정상적으로 검색이 되고<br/>
아무 이미지를 검색하게 되면 정보가 없다고 나오게 된다<br/><br/>

3. **게시판 페이지**에서는 자유로운 소통을 위한 게시판과, 콘서트에 동행인을 구하는 게시판,<br/>
  그리고 콘서트의 후기를 공유하는 게시판들이 있어 **유저들간의 소통**에 용이하다<br/><br/>

4. **좋아요 목록**을 확인하는 페이지는 **로그인**이 필요하며<br/>
로그인을 할 시에 지금까지 좋아요를 한 목록들을 확인이 가능하며,<br/>
좋아하는 장르를 체크, 전체 아티스트, 전체 콘서트 목록을 확인/검색 할 수 있으며<br/>
좋아하는 아티스트, 콘서트 목록 또한 확인/검색 할 수 있으며, <br/>
이는 **leftjoin**으로 둘을 구분 지었다<br/><br/>

## 😒개발 이슈😒
+ 이미지 검색 부분에서 **AWS Rekognition API**로 **인지도가 낮은** 아티스트들은 **검색이 잘 되지않는 문제**가 있으나<br/>
다른 API도 찾아본 결과 **Naver의 Clova face recognition API**는 **신뢰도가 낮다** 판단되어 현재에 만족하기로 결정<br/><br/>

+ 홈 화면에서 스크롤을 아래로 내릴때 **세로 리사이클러뷰의 공간만** 스크롤이 내려가는 이슈가 있었지만<br/>
레이아웃에서 **nested scroll view**로 감싸주어 해결<br/><br/>
## 🎈결과🎈

[프로젝트 기술서 링크](https://docs.google.com/presentation/d/10SK2fhhHQwgktnOjM6e3k2yymyNaWv71hm8S_mkchUI/edit?usp=sharing, '프로젝트 기술서 링크')<br/>
[시연 동영상 링크](https://youtu.be/feCfx006Jew, '시연동영상 링크')<br/>
