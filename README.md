# autocorr_kr
리브레오피스(LibreOffice) 자동 교정(Autocorrect)기능에 대한 말모이 저장소

##  프로젝트 소개 

리브레오피스(LibreOffice)의 한국어 자동 교정(Autocorrect)에 대한 데이터를 쌓고 정리하는 저장소입니다.

이 저장소는 리브레오피스(LibreOffice)의 core 저장소(Repository)의 `extras/source/autocorr/lang/ko/DocumentList.xml` 파일의 한국어의 자동교정 대상 낱말 적용 전에 이 저장소에서 `DocumentList.xml`의 추가된 내용을 검토합니다.
검토가 완료되면, 리브레오피스 한국어 담당자가 검토후에 직접 리브레오피스 저장소에 커밋을 하게 됩니다.


## 개발 방법
오타 및 틀린 말에 대한 내용과 교정으로 처리할 말에 대한 내용을 XML형식으로 개발하면 됩니다.

가령, 사람들이 Github나 많은 저장소나 블로그를 보면 `가운데`라는 낱말을  `가운대`라고 자주 틀리는 경우가 있습니다.

리브레오피스에서는 자동교정 xml파일(`DocumentList.xml`)에 `가운대`를 `가운데`로 고치는 것에 대하여 아래와 같이 만듭니다.
```
<block-list:block block-list:abbreviated-name="가운대" block-list:name="가운데"/>
```
즉, `block-list:abbreviated-name` 속성에 수정해야할 낱말을 작성하고, `block-list:name`에 수정된 낱말을 적으면 됩니다.

또 다른 예로, `명예홰손`으로 입력한 낱말을 다음의 `명예훼손`으로 수정하려면 아래와 같이 작성하면 됩니다.
```
<block-list:block block-list:abbreviated-name="명예홰손" block-list:name="명예훼손"/>
```


### 주의사항 
자동 교정 내용을 작성 및 제출 시 `block-list:abbreviated-name` 속성 기준으로 `가나다` 오름차순으로 작성하여 제출하시기 바랍니다. `가나다` 순으로 작성하지 않으면 풀리퀘스트(Pull Request)가 거절 될 수 있습니다. 


### 자동 교정 출처 
이 저장소의 한국어의 자동교정 내용은 아래의 링크를 참조로 만들어집니다.

* [국립국어원](https://korean.go.kr/)
* [국립국어원 - 한글 맞춤법](http://kornorms.korean.go.kr/regltn/regltnView.do#a)
* [국립국어원 - 표준어규정](http://kornorms.korean.go.kr/regltn/regltnView.do?regltn_code=0002#a)
* [한국어 NLP라이브러리 - open-korean-text](https://openkoreantext.org/)의 [타이핑 오타 교정 데이터](https://github.com/open-korean-text/open-korean-text/blob/master/src/main/resources/org/openkoreantext/processor/util/typos/typos.txt)

혹시, 자동교정에 대한 괜찮은 출처가 있으면 출처 추가 부탁드립니다.

(이 프로젝트는 GPLv3을 준수합니다)


### 자동 교정 소스코드 제출 방법
커밋을 할때에 제목 및 수정한 내용을 커밋 메세지에 추가후, 소스코드 커밋을 해주시면 됩니다.
그리고, 풀리퀘스트(Pull Request)를 전달할때에도 동일하게 전달해주시기 바랍니다.
(소스코드가 여러 개라면, 커밋 내용을 요약하여 풀리퀘스트에 전달해주시기 바랍니다)

아래는 커밋 메세지 예제입니다.
```
add korean autocorrect list

Add Korean Auto Correst list
성공율 -> 성공률
외형율 -> 외형률
```

## 여러 오픈소스 행사 참여 관련

### 1. 오픈소스 컨트리뷰톤 2020 행사 
이번 행사로 리브레오피스 [QA의 Easy Hacks](https://wiki.documentfoundation.org/QA/Easy_Hacks) 에 [\[ko\] Extend Autocorrect list for Korean language](https://bugs.documentfoundation.org/show_bug.cgi?id=135727) 항목 추가를 하였습니다.

이후 행사 기간동안 여러 낱말의 자동 교정 대상을 여러 참석하신 분께서 추가를 하였습니다.
추가 내용은 아래와 같습니다. 

* [\[ko\] add new autocorrect words for Korean](https://gerrit.libreoffice.org/c/core/+/100682)
* tdf#135727 add Korean Autocorrect list [https://gerrit.libreoffice.org/c/core/+/100848](https://gerrit.libreoffice.org/c/core/+/100848)
* tdf#135727 add Korean Autocorrect list [https://gerrit.libreoffice.org/c/core/+/100813](https://gerrit.libreoffice.org/c/core/+/100813)
* tdf#135727 add Korean Autocorrect list [https://gerrit.libreoffice.org/c/core/+/100814](https://gerrit.libreoffice.org/c/core/+/100814)
* tdf#135727 add Korean auto correct word [https://gerrit.libreoffice.org/c/core/+/100842](https://gerrit.libreoffice.org/c/core/+/100842)
* tdf#135727 add Korean Autocorrect list [https://gerrit.libreoffice.org/c/core/+/100812](https://gerrit.libreoffice.org/c/core/+/100812)

### 2. 핵토버페스트(Hacktoberfest) 2020
이번 행사에서는 앞서 행사와 다르게, 리브레오피스의 git저장소가 아닌 github 저장소를 만들어 진행합니다.

그 이유는 많은 한국인 개발자들이 리브레오피스(LibreOffice)의 [gerrit 리뷰 시스템](gerrit.libreoffice.org/)에 익숙하지 않고, 빌드방법에 대해서도 익숙하지 않기 대문입니다. 
github에 많이 익숙한 분들에게 gerrit리뷰시스템에 파일 제출하고 리뷰어와 리뷰하는 것에 대해서 생소하게 느끼는 분이 많음을 오픈소스 컨트리뷰톤 2020행사에서 경험을 하였습니다.
그리고, [핵토버페스트(Hacktoberfest)](https://hacktoberfest.digitalocean.com/)에서 Github으로 풀리퀘스트(Pull Request)를 제출해보는 행사를 진행하기 때문에, 행사 취지에 맞게 리브레오피스 우리말 모듬(LibreOffice Korean Team)의 Github저장소에 추가를 하여 커밋을 해보는 것을 진행하도록 했습니다.

핵토버페스트(Hacktoberfest)행사가 마무리되면, 리브레오피스 저장소에 전달받은 자동 교정 데이터를 리브레오피스(LibreOffice)의 core 저장소(Repository)의 `extras/source/autocorr/lang/ko/DocumentList.xml` 파일에 적용할 예정입니다.

