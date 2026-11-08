# 하루 퀘스트

캘린더 + 루틴/투두/식단(칼로리·영양소) 기록, 다 하면 +100P / 못 하면 −50P 퀘스트 앱.

- 앱 주소: https://kimmk114.github.io/daily-quest/
- 홈 화면 추가 안내 이미지: https://kimmk114.github.io/daily-quest/guide.png
- GitHub 저장소: https://github.com/kimmk114/daily-quest
- claude.ai 비공개 버전(계정 저장): https://claude.ai/artifact/XofY1DwXJYisV6gY8gynnD

## 폴더 구성
- `index.html` — 앱 본문 (수정은 여기서)
- `foods.json` — 음식 칼로리·영양소 데이터 (식약처 음식 + 가공식품 표준데이터)
- `icons/`, `manifest.webmanifest` — 앱 아이콘, 홈 화면 설정
- `guide/guide.html` — 홈 화면 추가 안내 이미지 원본
- `tools/build-foods.js` — CSV → foods.json 변환 스크립트
- `build-site.sh` — index.html 을 GitHub 배포용으로 감싸서 `site/` 에 만듦
- `site/` — GitHub 에 올라가는 폴더 (git 저장소)

## 수정 후 배포
```
sh build-site.sh
cd site && git add -A && git commit -m "수정 내용" && git push
```

## 음식 데이터 다시 만들기
CSV(공공데이터포털, cp949)를 UTF-8 로 바꾼 뒤 `food.csv`(음식), `proc.csv`(가공식품) 이름으로 같은 폴더에 두고:
```
node tools/build-foods.js foods.json
```
