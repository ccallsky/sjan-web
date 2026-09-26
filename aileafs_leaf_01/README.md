# aileafs_leaf_01 — GitHub Pages 버전

별도 빌드, 서버, ChatGPT 로그인 없이 동작하는 정적 사이트입니다.
현재 과제 설문은 미연결입니다. config.js에 실제 응답자 주소를 넣어야 접수가 가능합니다.
기존 ChatGPT Sites 주소와 제출 데이터는 이 파일에 포함되지 않습니다.

## 1. 파일 확인과 업로드
1. ZIP 압축을 풉니다. index.html을 열어 화면을 확인할 수 있습니다.
2. GitHub에서 새 Public 저장소 `aileafs_leaf_01`을 만듭니다.
3. Add file → Upload files에서 이 폴더 **안의 파일과 materials 폴더**를 올립니다. 저장소 최상위에 index.html이 있어야 합니다.
4. Settings → Pages → Build and deployment → Source: Deploy from a branch → main / (root) → Save.
5. 이 묶음의 CNAME에는 aileafs.com이 들어 있습니다. 도메인 설정 전 github.io 주소로 먼저 확인하려면 CNAME을 잠시 제외하고 올리세요.

## 2. 로그인 없는 Google 설문 만들기
Google Forms에서 빈 설문을 만들고 제목을 'aileafs_leaf_01 과제 제출'로 지정합니다.
- 이름 또는 수강생 식별명: 단답형 / 필수
- 과제 번호: 드롭다운 1~6 / 필수
- 사용한 프롬프트: 장문형 / 필수
- 과제 내용 및 검증·개선점: 장문형 / 필수
- 결과물 공유 링크: 단답형 / 선택
- 연락받을 이메일: 단답형 / 선택 (필요한 경우에만)

파일 업로드 문항은 넣지 않습니다. 설정에서 '응답 1회로 제한'을 끄고, 검증된 이메일 자동 수집 및 조직 사용자 제한을 사용하지 않습니다. 게시할 때 응답자 접근을 '링크가 있는 모든 사용자'로 설정합니다. 응답 결과 요약 공개는 끄세요. Workspace 정책이 공개 응답을 막으면 개인 계정에서 설문을 만드세요.
설문을 게시한 뒤 **응답자 링크**를 복사합니다. 편집 링크는 사용하지 않습니다.
`config.js`의 `assignmentFormUrl: ""`에 링크를 넣고 저장합니다.
시크릿 창에서 Google에 로그인하지 않은 상태로 설문을 열고 실제 시험 응답을 한 번 제출한 후, 설문 소유자 계정의 응답 탭에서 확인합니다.
Google 설문의 응답은 GitHub가 아닌 해당 설문 소유자 계정에 저장됩니다. 이름 입력은 신원 인증이 아니므로 대리 제출을 막아주지는 않습니다.

## 3. aileafs.com 연결
먼저 GitHub 계정 Settings → Pages에서 도메인 소유권 확인을 진행할 수 있습니다. 표시되는 TXT 레코드는 계정별로 다르므로 화면의 값을 그대로 DNS에 넣습니다.
저장소 Settings → Pages → Custom domain에 `aileafs.com`을 저장한 다음 DNS를 변경합니다.
도메인 DNS가 가비아에서 관리되는 경우 가비아의 DNS 관리에서 다음 레코드를 설정합니다. 네임서버가 다른 업체이면 그 업체에서 설정해야 합니다.

|종류|호스트|값|
|---|---|---|
|A|@|185.199.108.153|
|A|@|185.199.109.153|
|A|@|185.199.110.153|
|A|@|185.199.111.153|
|CNAME|www|본인GitHub아이디.github.io|

마지막 값은 실제 GitHub 아이디로 바꾸며 저장소 이름이나 https://는 넣지 않습니다. 기존 @ 또는 www 웹사이트 레코드가 있으면 현재 사용처를 확인하고 충돌하는 항목만 변경합니다. 이메일용 MX/TXT 등 다른 레코드는 유지합니다.
DNS 검사와 인증서 준비가 끝나면 GitHub Pages의 Enforce HTTPS를 켭니다. DNS 반영과 HTTPS 옵션 활성화에는 최대 24시간 정도 걸릴 수 있습니다.
마지막으로 aileafs.com과 www.aileafs.com, 자료 다운로드, 과제 설문을 확인합니다.

## 4. 내용 수정
- content.js: 강의, 공지, 영상, 추가 자료 링크. 형식을 유지하며 수정하세요.
- config.js: 과제 설문 응답자 링크.
- materials/: 다운로드할 공개 파일. 개인정보·학생 제출물을 올리지 마세요.
- style.css: 디자인.
- 강사 관리 페이지 대신 GitHub에서 파일을 수정하고, 제출 과제는 Google Forms의 응답 탭에서 확인합니다.
- TXT 학습 노트는 별도 파일입니다. 강의 내용 수정 시 해당 노트도 함께 수정하세요.

## 공식 안내 (2026-09-26 확인)
- GitHub 도메인 연결: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- Google 설문 게시·응답 접근: https://support.google.com/docs/answer/2839588
