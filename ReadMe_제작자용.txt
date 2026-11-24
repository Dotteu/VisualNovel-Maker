==================================================
비주얼 노벨 커스터마이징 패키지 (제작자 가이드)
제작: 돛트 (Dot-teu) · X : @Dot_teu
버전: v1.5 (2026-11-24)

버그 제보 폼 : https://forms.gle/gXGdtzuFTErmhgGM7
플레이 소감 및 Q&A 폼 : https://forms.gle/FxkLRtxubwCFy6HG7
==================================================

이 문서는 한국어 → English → 日本語 → 简体中文 → 繁體中文 순서로 같은 내용이 적혀 있습니다.
This document contains the same content in Korean → English → Japanese → Simplified Chinese → Traditional Chinese.


##################################################
[한국어]
##################################################

이미지, 사운드, 대사만 바꿔서 코딩 없이 나만의 비주얼 노벨을 만들 수 있는 커스터마이징 키트입니다.

[v1.5 업데이트] 로컬라이징 추가
- 게임과 편집기가 영어·한국어·일본어·중국어(간체)·중국어(번체)를 지원합니다. 처음에는 영어로 열립니다.
- 게임은 설정(Esc)의 ‘Language’, 편집기는 오른쪽 위 ‘Language’에서 바꿀 수 있습니다. 고른 언어는 브라우저에 기억됩니다.
- 언어를 바꾸는 것은 메뉴·안내 같은 화면 글자입니다. 대사와 엔딩 제목은 제작자가 쓴 언어 그대로 나옵니다.

--------------------------------------------------
1. 빠른 시작 (제작 → 테스트 → 배포)
--------------------------------------------------

[제작하기]
① Editor.html을 크롬이나 엣지로 엽니다. (폴더 저장은 크롬·엣지만 지원)
② 오른쪽 위 ‘폴더 연결’을 누르고 index.html이 있는 폴더를 선택합니다.
③ ‘불러오기’를 누른 뒤 캐릭터·배경·사운드·UI·대사를 원하는 대로 고칩니다.
④ ‘저장’을 누르면 폴더에 바로 반영됩니다.
⑤ index.html을 열어 커스텀 폴더를 연결하면 수정된 게임을 확인할 수 있습니다.

[배포하기]
① 완성된 게임 폴더에서 제작용 파일(Editor.html, editor-data.json, 지금 읽고 있는 제작자용 ReadMe)을 삭제합니다. (배포 후에도 업데이트를 하실 생각이 있다면 Editor.html과 editor-data.json은 백업해 주세요. 해당 데이터를 통해 에디터 저장을 불러옵니다.)
② 남은 폴더를 통째로 압축(ZIP)해 배포하거나, GitHub Pages 등에 올립니다.
③ 배포 시 출처 표기 및 비영리 규정은 반드시 아래 ‘라이선스 및 출처 표기 안내’를 지켜 주세요.

--------------------------------------------------
2. 꼭 지켜야 하는 핵심 규칙
--------------------------------------------------

① 파일 이름은 대소문자와 확장자까지 완전히 똑같이 맞춰 주세요. (윈도우에선 보여도 웹에 올리면 대소문자가 다를 시 이미지가 깨집니다.)
② 이미지는 비율(배경·캐릭터 16:9 투명 PNG)을 맞추는 것을 권장합니다. 비율이 달라도 넣을 수 있으나 의도와 다르게 잘리거나 작게 보일 수 있으니 에디터 미리보기에서 꼭 확인해 주세요.
③ 움직이는 배경·캐릭터·엔딩 컷씬은 .png 대신 .webp나 .gif로 넣으면 움직입니다. APNG는 확장자를 .png 그대로 두면 됩니다. (테두리가 깔끔한 WebP나 APNG를 추천합니다.)
④ 게임 공개 후 대사를 수정하면 기존 플레이어의 세이브가 끊길 수 있습니다.

--------------------------------------------------
3. 편집기(Editor.html) 핵심 기능 요약
--------------------------------------------------

- 이름 규칙: ‘한글 이름/EnglishName’ 형식으로 적으면 한글은 게임 내 이름표로, 영문은 실제 폴더·파일 이름으로 자동 저장됩니다.
- 캐릭터 탭: 동그라미(플레이어 지정)를 켜면 선택지 블록에 해당 이름이 뜹니다. ‘내레이터’는 이름표와 이미지가 나오지 않으므로 그림을 넣지 않아도 됩니다.
- 대사 탭 블록 색: 흰색(일반 대사) / 노란색(선택지) / 보라색(분기 조건 ON) / 하늘색(조건을 만족한 분기 시작점) / 초록색(엔딩). 저장 전 오른쪽 ‘검사’의 빨간 오류를 꼭 고치세요.
- 대사 탭 글자 수: 한 블록에 쓸 수 있는 대사 글자 수는 UI 탭의 ‘대사 글자 영역’ 크기와 글자 크기에 따라 정해지며, 블록 아래에 ‘글자 수 / 최대’로 표시됩니다. 캐릭터 이름은 30자까지입니다.
- 사운드 탭: BGM 칸 위 ‘메인 화면 BGM’에서 게임 시작 화면의 음악을 고를 수 있습니다. BGM이 바뀔 때는 자연스럽게 페이드 인·아웃됩니다. 대사 블록의 SFX 옆 ‘반복’을 체크하면 그 대사가 나오는 동안 효과음이 반복 재생됩니다.
- 엔딩 탭: 엔딩을 추가하고 ‘엔딩 제목/ENDINGNAME’으로 이름을 정한 뒤 컷씬 이미지(16:9)를 넣습니다. 대사 탭의 엔딩 블록에서 오른쪽 ‘엔딩’ 칸으로 이 엔딩을 고르면 엔딩 화면에 제목과 컷씬이 나옵니다. 영문 이름은 대문자로 저장됩니다. (예: Endings/HAPPY.png)
- UI 탭: ‘게임 제목’을 바꾸면 메인 화면과 브라우저 탭 이름이 변경됩니다. 오른쪽 ‘화면 요소’에서 대사창·이름표·선택지·버튼·엔딩 화면 등을 눌러 위치·크기(슬라이더)와 이미지를 바꾸고, ‘글꼴’과 ‘글자 크기·색’ 창에서 글자 설정을 바꿀 수 있습니다. 배치와 글자 설정은 UI/Layout.json에 저장됩니다.
- 언어: 오른쪽 위 ‘Language’에서 편집기 화면 언어를 바꿉니다. 언어를 바꿔도 작업 중인 내용과 저장되는 파일(CSV 등)은 그대로입니다.
- 글꼴 참고: 기본 글꼴(PF스타더스트)에는 중국어와 일부 일본어 글자가 없어서, 그 글자는 컴퓨터의 기본 글꼴로 보입니다. 해당 언어로 게임을 만든다면 그 언어를 지원하는 글꼴을 UI 탭 ‘글꼴’에 넣어 주세요.

--------------------------------------------------
4. 자주 겪는 문제 해결
--------------------------------------------------

- ‘파일 없음’ 상자가 뜰 때: 파일 경로·대소문자·확장자를 확인하세요. (F12 → Console 탭에서 누락된 파일 목록을 바로 볼 수 있습니다.)
- 고쳤는데 반영이 안 될 때: 에디터에서 ‘저장’을 눌렀는지(‘저장 전’ 표시 확인) 체크하고, 게임(index.html)에서 폴더를 다시 연결해 주세요.
- 특정 대사부터 테스트할 때: 게임 실행 후 F12 → Console에 VN.jump('대사ID') 입력
- 기타 질문은 X의 배포 글을 확인하신 후에도 해결되지 않는다면 Q&A 폼에 남겨 주세요. (버그 폼에는 버그만 제보 부탁드립니다!)

==================================================
라이선스 및 출처 표기 안내 (License)
엔진 원작: 돛트 (Dot-teu) · X : @Dot_teu
==================================================

[제작 정보]
대사의 자료 구조와 데이터 흐름, 분기 등 시스템은 돛트(Dot-teu)가 설계하고 흐름을 짰으며, UI와 캐릭터 리소스 또한 직접 작업하였습니다.
완성본 HTML(게임과 편집기)과 기본 배경은 Claude AI의 도움을 받아 제작했습니다.
예시 게임의 BGM은 Suno AI로, 효과음(SFX)은 Mirelo AI로 생성했습니다.

--------------------------------------------------
1. 패키지 라이선스 (CC BY-NC 4.0)
--------------------------------------------------

이 패키지(게임 코드, 편집기, 예시 스토리, 기본 더미 이미지와 소리)는 크리에이티브 커먼즈 저작자표시-비영리 4.0 국제 라이선스(CC BY-NC 4.0)를 따릅니다.
https://creativecommons.org/licenses/by-nc/4.0/deed.ko

[할 수 있는 것]
- 자유롭게 플레이, 수정, 커스터마이징
- 수정한 버전을 무료로 다시 배포(공유)

[지켜야 할 것]
- 출처 표기: 게임을 배포할 때는 항상 원작자를 밝혀 주세요.
- 비영리: 판매, 유료 배포, 후원 보상 등 돈을 받는 용도로 쓸 수 없습니다.
- 시작 화면 유지: 게임을 실행하면 가장 먼저 뜨는 화면(제작자 표기가 있는 시작 화면)을 임의로 삭제하거나 가리지 마세요.

--------------------------------------------------
2. 출처 표기 예시 (배포 글·게임 내 크레딧·리드미)
--------------------------------------------------

엔진 원작: 돛트 (Dot-teu) https://x.com/Dot_teu
CC BY-NC 4.0

--------------------------------------------------
3. 외부 리소스 및 창작물 권리
--------------------------------------------------

- 기본 글꼴(Fonts 폴더의 PF스타더스트 3.0 S)은 본 라이선스에 포함되지 않으며, 해당 글꼴 자체의 이용 규칙을 따릅니다.
- 제작자 본인이 새로 그린 그림, 캐릭터, 작성한 대사의 저작권은 각 제작자에게 있습니다.
- 타인의 그림이나 캐릭터, 음원을 사용할 때는 해당 원작자의 이용 규칙을 별도로 확인해 주세요.


##################################################
[English]
##################################################

A customizing kit for making your own visual novel without coding — just replace the images, sounds and dialogue.

[v1.5 update] Localization added
- The game and the editor support English, Korean, Japanese, Simplified Chinese and Traditional Chinese. They open in English by default.
- Change the language with ‘Language’ in the game’s Settings (Esc), or ‘Language’ at the top right of the editor. Your choice is remembered by the browser.
- The language setting changes on-screen text such as menus and guides. Dialogue and ending titles appear in the language the creator wrote them in.

--------------------------------------------------
1. Quick start (Create → Test → Release)
--------------------------------------------------

[Creating]
① Open Editor.html in Chrome or Edge. (Saving to a folder works only in Chrome and Edge.)
② Press ‘Connect Folder’ at the top right and select the folder that contains index.html.
③ Press ‘Load’, then edit characters, backgrounds, sounds, UI and dialogue as you like.
④ Press ‘Save’ to apply the changes to the folder right away.
⑤ Open index.html and connect the custom folder to see your edited game.

[Releasing]
① Delete the creator files (Editor.html, editor-data.json and this creator ReadMe) from the finished game folder. (If you plan to update the game after release, back up Editor.html and editor-data.json. The editor uses this data to reload your work.)
② Compress the remaining folder as a ZIP and share it, or upload it to GitHub Pages or a similar service.
③ When releasing, always follow the attribution and non-commercial rules in ‘License and Attribution’ below.

--------------------------------------------------
2. Key rules you must follow
--------------------------------------------------

① File names must match exactly, including letter case and extension. (They may show on Windows, but online, images break if the case differs.)
② Matching the image ratio (backgrounds and characters: 16:9, characters as transparent PNG) is recommended. Other ratios still work, but images may be cropped or shown smaller than intended, so always check in the editor preview.
③ For animated backgrounds, characters and ending cutscenes, use .webp or .gif instead of .png. For APNG, keep the .png extension. (WebP or APNG is recommended for clean edges.)
④ Editing dialogue after the game is released may break existing players’ saves.

--------------------------------------------------
3. Editor (Editor.html) key features
--------------------------------------------------

- Naming rule: write names as ‘Display name/EnglishName’. The display name appears on the in-game name box, and the English name is used for the actual folder and file names.
- Characters tab: turn on the circle (player) to show that name on choice blocks. The narrator (‘내레이터’) has no name box or image, so it needs no pictures.
- Dialogue tab block colors: white (line) / yellow (choice) / purple (sets a branch flag) / sky blue (branch start when the condition is met) / green (ending). Fix the red errors under ‘Check’ on the right before saving.
- Dialogue length: the number of characters per block depends on the size of the ‘Dialogue text area’ and the text size in the UI tab, and is shown under the block as ‘count / max’. Character names can be up to 30 characters.
- Sound tab: choose the music for the game’s start screen in ‘Main screen BGM’ above the BGM list. BGM changes fade in and out smoothly. Check ‘Loop’ next to SFX on a dialogue block to loop the sound effect while that line is shown.
- Endings tab: add an ending, name it ‘Ending title/ENDINGNAME’, and add a cutscene image (16:9). Pick this ending in the ‘Ending’ field on the right for an ending block in the Dialogue tab, and the title and cutscene appear on the ending screen. English names are saved in uppercase. (e.g. Endings/HAPPY.png)
- UI tab: changing the ‘Game title’ changes the main screen and the browser tab name. In ‘Screen elements’ on the right, click the dialogue box, name box, choices, buttons, ending screen and so on to change their position and size (sliders) and images, and change text settings in the ‘Fonts’ and ‘Text size · color’ windows. Layout and text settings are saved in UI/Layout.json.
- Language: change the editor’s display language with ‘Language’ at the top right. Your work in progress and the saved files (CSV etc.) stay the same when you switch.
- Font note: the default font (PF Stardust) has no Chinese and some Japanese characters, so those are shown in your computer’s default font. If you make a game in those languages, add a font that supports them under ‘Fonts’ in the UI tab.

--------------------------------------------------
4. Troubleshooting
--------------------------------------------------

- A ‘File not found’ box appears: check the file path, letter case and extension. (F12 → Console tab shows the list of missing files.)
- Changes don’t show up: check that you pressed ‘Save’ in the editor (look for the ‘Not saved’ mark), then connect the folder again in the game (index.html).
- To test from a specific line: start the game, then type VN.jump('LineID') in F12 → Console.
- For other questions, please check the release post on X first, and if that doesn’t help, leave them in the Q&A form. (Please use the bug form for bugs only!)

==================================================
License and Attribution
Original engine: 돛트 (Dot-teu) · X : @Dot_teu
==================================================

[Credits]
The dialogue data structure, data flow, branching and other systems were designed and laid out by 돛트 (Dot-teu), who also made the UI and character resources.
The finished HTML (game and editor) and the default backgrounds were made with the help of Claude AI.
The sample game’s BGM was generated with Suno AI, and the sound effects (SFX) with Mirelo AI.

--------------------------------------------------
1. Package license (CC BY-NC 4.0)
--------------------------------------------------

This package (game code, editor, sample story, default dummy images and sounds) is licensed under the Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0).
https://creativecommons.org/licenses/by-nc/4.0/deed.en

[You may]
- Play, modify and customize freely
- Share your modified version again for free

[You must]
- Attribution: always credit the original author when you release a game.
- Non-commercial: it may not be used for anything that earns money, such as sales, paid releases or donation rewards.
- Keep the start screen: do not remove or cover the first screen shown when the game runs (the start screen with the creator credit).

--------------------------------------------------
2. Attribution example (release post, in-game credits, ReadMe)
--------------------------------------------------

Original engine: 돛트 (Dot-teu) https://x.com/Dot_teu
CC BY-NC 4.0

--------------------------------------------------
3. External resources and rights to your work
--------------------------------------------------

- The default font (PF Stardust 3.0 S in the Fonts folder) is not covered by this license and follows that font’s own terms of use.
- Copyright of pictures, characters and dialogue you create belongs to you.
- When using other people’s pictures, characters or music, check the original creator’s terms of use separately.


##################################################
[日本語]
##################################################

画像・サウンド・台詞を差し替えるだけで、コーディングなしで自分だけのビジュアルノベルが作れるカスタマイズキットです。

[v1.5 アップデート] ローカライズを追加
- ゲームとエディターが英語・韓国語・日本語・中国語(簡体字)・中国語(繁体字)に対応しました。最初は英語で開きます。
- ゲームは設定(Esc)の「Language」、エディターは右上の「Language」で変えられます。選んだ言語はブラウザに記憶されます。
- 言語設定で変わるのはメニューや案内など画面の文字です。台詞とエンディングのタイトルは制作者が書いた言語のまま表示されます。

--------------------------------------------------
1. クイックスタート(制作 → テスト → 配布)
--------------------------------------------------

[制作する]
① Editor.html を Chrome か Edge で開きます。(フォルダへの保存は Chrome・Edge のみ対応)
② 右上の「フォルダ接続」を押して、index.html があるフォルダを選びます。
③ 「ロード」を押してから、キャラクター・背景・サウンド・UI・台詞を自由に直します。
④ 「保存」を押すとフォルダにすぐ反映されます。
⑤ index.html を開いてカスタムフォルダを接続すると、直したゲームを確認できます。

[配布する]
① 完成したゲームフォルダから制作用ファイル(Editor.html、editor-data.json、今読んでいる制作者用 ReadMe)を削除します。(配布後もアップデートする予定なら、Editor.html と editor-data.json はバックアップしてください。このデータでエディターの作業を読み込みます。)
② 残ったフォルダをまるごと圧縮(ZIP)して配布するか、GitHub Pages などに上げます。
③ 配布するときは、下の「ライセンスとクレジット表記の案内」にある出典表記と非営利の規定を必ず守ってください。

--------------------------------------------------
2. 必ず守る大事なルール
--------------------------------------------------

① ファイル名は大文字・小文字と拡張子まで完全に合わせてください。(Windows では表示されても、ウェブに上げると大文字・小文字が違う場合は画像が壊れます。)
② 画像は比率(背景・キャラクター 16:9、キャラクターは透明 PNG)を合わせることをおすすめします。比率が違っても入れられますが、意図と違って切れたり小さく見えたりすることがあるので、エディターのプレビューで必ず確認してください。
③ 動く背景・キャラクター・エンディングのカットシーンは、.png の代わりに .webp か .gif で入れると動きます。APNG は拡張子を .png のままにしてください。(縁がきれいな WebP か APNG をおすすめします。)
④ ゲーム公開後に台詞を直すと、すでに遊んでいるプレイヤーのセーブがつながらなくなることがあります。

--------------------------------------------------
3. エディター(Editor.html)主な機能
--------------------------------------------------

- 名前のルール:「表示名/EnglishName」の形式で書くと、表示名はゲーム内の名前欄に、英語名は実際のフォルダ・ファイル名として自動で保存されます。
- キャラクタータブ:丸(プレイヤー指定)をオンにすると、選択肢ブロックにその名前が表示されます。ナレーター(「내레이터」)は名前欄と画像が出ないので、絵を入れなくてもかまいません。
- 台詞タブのブロックの色:白(通常の台詞)/黄(選択肢)/紫(分岐フラグをオン)/水色(条件を満たしたときの分岐開始)/緑(エンディング)。保存前に右の「チェック」の赤いエラーを必ず直してください。
- 台詞の文字数:1ブロックに書ける文字数は、UIタブの「台詞の文字エリア」の大きさと文字の大きさで決まり、ブロックの下に「文字数 / 最大」で表示されます。キャラクター名は30文字までです。
- サウンドタブ:BGM欄の上の「メイン画面のBGM」で、ゲーム開始画面の曲を選べます。BGMが変わるときは自然にフェードイン・アウトします。台詞ブロックのSFXの横の「繰り返し」をチェックすると、その台詞が出ている間、効果音が繰り返し再生されます。
- エンディングタブ:エンディングを追加して「エンディングタイトル/ENDINGNAME」で名前を決め、カットシーン画像(16:9)を入れます。台詞タブのエンディングブロックで右の「エンディング」欄からこのエンディングを選ぶと、エンディング画面にタイトルとカットシーンが出ます。英語名は大文字で保存されます。(例:Endings/HAPPY.png)
- UIタブ:「ゲームタイトル」を変えると、メイン画面とブラウザのタブ名が変わります。右の「画面要素」で台詞ウィンドウ・名前欄・選択肢・ボタン・エンディング画面などをクリックして位置・大きさ(スライダー)と画像を変え、「フォント」と「文字の大きさ・色」ウィンドウで文字の設定を変えられます。配置と文字の設定は UI/Layout.json に保存されます。
- 言語:右上の「Language」でエディターの表示言語を変えます。言語を変えても、作業中の内容と保存されるファイル(CSV など)はそのままです。
- フォントについて:基本フォント(PFスターダスト)には中国語と一部の日本語の文字がないため、その文字はパソコンの標準フォントで表示されます。その言語でゲームを作るなら、その言語に対応したフォントをUIタブの「フォント」に入れてください。

--------------------------------------------------
4. よくあるトラブルの解決
--------------------------------------------------

- 「ファイルなし」の枠が出るとき:ファイルのパス・大文字小文字・拡張子を確認してください。(F12 → Console タブで足りないファイルの一覧をすぐ見られます。)
- 直したのに反映されないとき:エディターで「保存」を押したか(「保存前」の表示を確認)チェックし、ゲーム(index.html)でフォルダをもう一度接続してください。
- 特定の台詞からテストしたいとき:ゲームを起動してから F12 → Console に VN.jump('台詞ID') と入力します。
- その他の質問は、X の配布投稿を確認しても解決しない場合、Q&A フォームに書いてください。(バグフォームにはバグだけを報告してください!)

==================================================
ライセンスとクレジット表記の案内(License)
エンジン原作:돛트 (Dot-teu) · X : @Dot_teu
==================================================

[制作情報]
台詞のデータ構造とデータの流れ、分岐などのシステムは 돛트 (Dot-teu) が設計して流れを組み、UI とキャラクターのリソースも自分で制作しました。
完成版の HTML(ゲームとエディター)と基本の背景は Claude AI の助けを借りて制作しました。
サンプルゲームの BGM は Suno AI で、効果音(SFX)は Mirelo AI で生成しました。

--------------------------------------------------
1. パッケージのライセンス(CC BY-NC 4.0)
--------------------------------------------------

このパッケージ(ゲームのコード、エディター、サンプルストーリー、基本のダミー画像と音)は、クリエイティブ・コモンズ 表示-非営利 4.0 国際ライセンス(CC BY-NC 4.0)に従います。
https://creativecommons.org/licenses/by-nc/4.0/deed.ja

[できること]
- 自由にプレイ・改変・カスタマイズ
- 改変したバージョンを無料で再配布(共有)

[守ること]
- 出典表記:ゲームを配布するときは、必ず原作者を明記してください。
- 非営利:販売、有料配布、支援のリターンなど、お金を受け取る用途には使えません。
- スタート画面の維持:ゲームを起動して最初に出る画面(制作者表記のあるスタート画面)を勝手に削除したり隠したりしないでください。

--------------------------------------------------
2. 出典表記の例(配布投稿・ゲーム内クレジット・ReadMe)
--------------------------------------------------

エンジン原作:돛트 (Dot-teu) https://x.com/Dot_teu
CC BY-NC 4.0

--------------------------------------------------
3. 外部リソースと創作物の権利
--------------------------------------------------

- 基本フォント(Fonts フォルダの PFスターダスト 3.0 S)はこのライセンスに含まれず、そのフォント自体の利用規約に従います。
- 制作者本人が新しく描いた絵、キャラクター、書いた台詞の著作権は、それぞれの制作者にあります。
- 他人の絵やキャラクター、音源を使うときは、その原作者の利用規約を別途確認してください。


##################################################
[简体中文]
##################################################

只需替换图像、声音和台词，无需编程就能制作属于自己的视觉小说的自定义工具包。

[v1.5 更新] 新增本地化
- 游戏和编辑器支持英语、韩语、日语、简体中文、繁体中文。默认以英语打开。
- 游戏在设置(Esc)的“Language”中切换，编辑器在右上角的“Language”中切换。所选语言会被浏览器记住。
- 语言设置改变的是菜单、提示等界面文字。台词和结局标题会按制作者书写的语言显示。

--------------------------------------------------
1. 快速开始(制作 → 测试 → 发布)
--------------------------------------------------

[制作]
① 用 Chrome 或 Edge 打开 Editor.html。(保存到文件夹仅支持 Chrome、Edge)
② 点击右上角的“连接文件夹”，选择 index.html 所在的文件夹。
③ 点击“读取”后，随意修改角色、背景、声音、UI 和台词。
④ 点击“保存”即可直接反映到文件夹。
⑤ 打开 index.html 并连接自定义文件夹，即可查看修改后的游戏。

[发布]
① 从完成的游戏文件夹中删除制作用文件(Editor.html、editor-data.json 以及正在阅读的制作者用 ReadMe)。(如果发布后还打算更新，请备份 Editor.html 和 editor-data.json。编辑器会通过这些数据读取之前的工作。)
② 把剩下的文件夹整体压缩(ZIP)后发布，或上传到 GitHub Pages 等。
③ 发布时请务必遵守下方“许可证与署名说明”中的署名和非商业规定。

--------------------------------------------------
2. 必须遵守的核心规则
--------------------------------------------------

① 文件名必须连大小写和扩展名都完全一致。(在 Windows 上可能能显示，但上传到网络后大小写不同会导致图像无法显示。)
② 建议图像保持比例(背景、角色为 16:9，角色为透明 PNG)。比例不同也能放入，但可能会被意外裁切或显示得较小，请务必在编辑器预览中确认。
③ 动态背景、角色和结局过场图，用 .webp 或 .gif 代替 .png 放入即可播放动画。APNG 请保持 .png 扩展名。(推荐边缘干净的 WebP 或 APNG。)
④ 游戏公开后修改台词，可能会导致已有玩家的存档无法继续。

--------------------------------------------------
3. 编辑器(Editor.html)主要功能
--------------------------------------------------

- 命名规则:按“显示名称/EnglishName”格式填写，显示名称会作为游戏内的名字框，英文名会自动作为实际的文件夹和文件名保存。
- 角色标签页:打开圆圈(指定玩家)后，选项块上会显示该名字。旁白(“내레이터”)不显示名字框和图像，因此不需要放图片。
- 台词标签页的块颜色:白色(普通台词)/ 黄色(选项)/ 紫色(开启分支旗标)/ 浅蓝色(满足条件时的分支开始)/ 绿色(结局)。保存前请务必修正右侧“检查”中的红色错误。
- 台词字数:每个块可写的台词字数取决于 UI 标签页中“台词文字区域”的大小和文字大小，并在块下方以“字数 / 最大”显示。角色名称最多 30 字。
- 声音标签页:在 BGM 列表上方的“主界面 BGM”中选择游戏开始画面的音乐。BGM 切换时会自然淡入淡出。勾选台词块 SFX 旁的“循环”后，该台词显示期间音效会循环播放。
- 结局标签页:添加结局，以“结局标题/ENDINGNAME”命名，并放入过场图(16:9)。在台词标签页的结局块中通过右侧“结局”栏选择此结局后，结局画面会显示标题和过场图。英文名会以大写保存。(例:Endings/HAPPY.png)
- UI 标签页:修改“游戏标题”会改变主界面和浏览器标签的名称。在右侧“画面元素”中点击对话框、名字框、选项、按钮、结局画面等，修改位置、大小(滑块)和图像，并可在“字体”和“文字大小·颜色”窗口中修改文字设置。布局和文字设置保存在 UI/Layout.json 中。
- 语言:在右上角的“Language”中切换编辑器的显示语言。切换语言后，正在编辑的内容和保存的文件(CSV 等)保持不变。
- 字体说明:默认字体(PF Stardust)不包含中文和部分日文字符，这些字符会以电脑的默认字体显示。如果要用这些语言制作游戏，请在 UI 标签页的“字体”中放入支持该语言的字体。

--------------------------------------------------
4. 常见问题解决
--------------------------------------------------

- 出现“没有文件”框时:请检查文件路径、大小写和扩展名。(在 F12 → Console 标签页中可以直接看到缺少的文件列表。)
- 修改后没有反映时:请检查是否在编辑器中点击了“保存”(确认“未保存”标记)，并在游戏(index.html)中重新连接文件夹。
- 想从特定台词开始测试时:运行游戏后，在 F12 → Console 中输入 VN.jump('台词ID')。
- 其他问题请先查看 X 上的发布帖，如果仍未解决，请在 Q&A 表单中留言。(错误报告表单请只用于报告错误!)

==================================================
许可证与署名说明(License)
引擎原作:돛트 (Dot-teu) · X : @Dot_teu
==================================================

[制作信息]
台词的数据结构、数据流程和分支等系统由 돛트 (Dot-teu) 设计并规划流程，UI 和角色资源也由本人制作。
完成版 HTML(游戏和编辑器)以及默认背景是在 Claude AI 的帮助下制作的。
示例游戏的 BGM 使用 Suno AI 生成，音效(SFX)使用 Mirelo AI 生成。

--------------------------------------------------
1. 工具包许可证(CC BY-NC 4.0)
--------------------------------------------------

本工具包(游戏代码、编辑器、示例故事、默认占位图像和声音)采用知识共享 署名-非商业性使用 4.0 国际许可协议(CC BY-NC 4.0)。
https://creativecommons.org/licenses/by-nc/4.0/deed.zh-hans

[可以做的事]
- 自由游玩、修改、自定义
- 免费再次发布(分享)修改后的版本

[必须遵守的事]
- 署名:发布游戏时请务必注明原作者。
- 非商业:不得用于销售、付费发布、赞助回报等收取金钱的用途。
- 保留开始画面:请勿擅自删除或遮挡游戏运行后最先显示的画面(带有制作者署名的开始画面)。

--------------------------------------------------
2. 署名示例(发布帖、游戏内鸣谢、ReadMe)
--------------------------------------------------

引擎原作:돛트 (Dot-teu) https://x.com/Dot_teu
CC BY-NC 4.0

--------------------------------------------------
3. 外部资源与创作物权利
--------------------------------------------------

- 默认字体(Fonts 文件夹中的 PF Stardust 3.0 S)不在本许可证范围内，遵循该字体自身的使用条款。
- 制作者本人新绘制的图画、角色和撰写的台词，其著作权归各制作者所有。
- 使用他人的图画、角色或音乐时，请另行确认原作者的使用条款。


##################################################
[繁體中文]
##################################################

只需替換圖片、聲音和台詞，不必寫程式就能製作屬於自己的視覺小說的自訂工具包。

[v1.5 更新] 新增在地化
- 遊戲和編輯器支援英文、韓文、日文、簡體中文、繁體中文。預設以英文開啟。
- 遊戲在設定(Esc)的「Language」中切換，編輯器在右上角的「Language」中切換。所選語言會被瀏覽器記住。
- 語言設定改變的是選單、提示等畫面文字。台詞和結局標題會按製作者書寫的語言顯示。

--------------------------------------------------
1. 快速開始(製作 → 測試 → 發布)
--------------------------------------------------

[製作]
① 用 Chrome 或 Edge 開啟 Editor.html。(儲存到資料夾僅支援 Chrome、Edge)
② 點擊右上角的「連接資料夾」，選擇 index.html 所在的資料夾。
③ 點擊「讀取」後，隨意修改角色、背景、聲音、UI 和台詞。
④ 點擊「儲存」即可直接反映到資料夾。
⑤ 開啟 index.html 並連接自訂資料夾，即可查看修改後的遊戲。

[發布]
① 從完成的遊戲資料夾中刪除製作用檔案(Editor.html、editor-data.json 以及正在閱讀的製作者用 ReadMe)。(如果發布後還打算更新，請備份 Editor.html 和 editor-data.json。編輯器會透過這些資料讀取之前的工作。)
② 把剩下的資料夾整體壓縮(ZIP)後發布，或上傳到 GitHub Pages 等。
③ 發布時請務必遵守下方「授權與署名說明」中的署名和非商業規定。

--------------------------------------------------
2. 必須遵守的核心規則
--------------------------------------------------

① 檔名必須連大小寫和副檔名都完全一致。(在 Windows 上可能能顯示，但上傳到網路後大小寫不同會導致圖片無法顯示。)
② 建議圖片保持比例(背景、角色為 16:9，角色為透明 PNG)。比例不同也能放入，但可能會被意外裁切或顯示得較小，請務必在編輯器預覽中確認。
③ 動態背景、角色和結局過場圖，用 .webp 或 .gif 代替 .png 放入即可播放動畫。APNG 請保持 .png 副檔名。(推薦邊緣乾淨的 WebP 或 APNG。)
④ 遊戲公開後修改台詞，可能會導致既有玩家的存檔無法繼續。

--------------------------------------------------
3. 編輯器(Editor.html)主要功能
--------------------------------------------------

- 命名規則:按「顯示名稱/EnglishName」格式填寫，顯示名稱會作為遊戲內的名字框，英文名會自動作為實際的資料夾和檔名儲存。
- 角色分頁:開啟圓圈(指定玩家)後，選項區塊上會顯示該名字。旁白(「내레이터」)不顯示名字框和圖片，因此不需要放圖片。
- 台詞分頁的區塊顏色:白色(一般台詞)/ 黃色(選項)/ 紫色(開啟分支旗標)/ 淺藍色(滿足條件時的分支開始)/ 綠色(結局)。儲存前請務必修正右側「檢查」中的紅色錯誤。
- 台詞字數:每個區塊可寫的台詞字數取決於 UI 分頁中「台詞文字區域」的大小和文字大小，並在區塊下方以「字數 / 最大」顯示。角色名稱最多 30 字。
- 聲音分頁:在 BGM 列表上方的「主畫面 BGM」中選擇遊戲開始畫面的音樂。BGM 切換時會自然淡入淡出。勾選台詞區塊 SFX 旁的「循環」後，該台詞顯示期間音效會循環播放。
- 結局分頁:新增結局，以「結局標題/ENDINGNAME」命名，並放入過場圖(16:9)。在台詞分頁的結局區塊中透過右側「結局」欄選擇此結局後，結局畫面會顯示標題和過場圖。英文名會以大寫儲存。(例:Endings/HAPPY.png)
- UI 分頁:修改「遊戲標題」會改變主畫面和瀏覽器分頁的名稱。在右側「畫面元素」中點擊對話框、名字框、選項、按鈕、結局畫面等，修改位置、大小(滑桿)和圖片，並可在「字型」和「文字大小·顏色」視窗中修改文字設定。版面和文字設定儲存在 UI/Layout.json 中。
- 語言:在右上角的「Language」中切換編輯器的顯示語言。切換語言後，正在編輯的內容和儲存的檔案(CSV 等)保持不變。
- 字型說明:預設字型(PF Stardust)不包含中文和部分日文字元，這些字元會以電腦的預設字型顯示。如果要用這些語言製作遊戲，請在 UI 分頁的「字型」中放入支援該語言的字型。

--------------------------------------------------
4. 常見問題解決
--------------------------------------------------

- 出現「沒有檔案」框時:請檢查檔案路徑、大小寫和副檔名。(在 F12 → Console 分頁中可以直接看到缺少的檔案清單。)
- 修改後沒有反映時:請檢查是否在編輯器中點擊了「儲存」(確認「未儲存」標記)，並在遊戲(index.html)中重新連接資料夾。
- 想從特定台詞開始測試時:執行遊戲後，在 F12 → Console 中輸入 VN.jump('台詞ID')。
- 其他問題請先查看 X 上的發布貼文，如果仍未解決，請在 Q&A 表單中留言。(錯誤回報表單請只用於回報錯誤!)

==================================================
授權與署名說明(License)
引擎原作:돛트 (Dot-teu) · X : @Dot_teu
==================================================

[製作資訊]
台詞的資料結構、資料流程和分支等系統由 돛트 (Dot-teu) 設計並規劃流程，UI 和角色資源也由本人製作。
完成版 HTML(遊戲和編輯器)以及預設背景是在 Claude AI 的協助下製作的。
範例遊戲的 BGM 使用 Suno AI 生成，音效(SFX)使用 Mirelo AI 生成。

--------------------------------------------------
1. 工具包授權(CC BY-NC 4.0)
--------------------------------------------------

本工具包(遊戲程式碼、編輯器、範例故事、預設佔位圖片和聲音)採用創用 CC 姓名標示-非商業性 4.0 國際授權條款(CC BY-NC 4.0)。
https://creativecommons.org/licenses/by-nc/4.0/deed.zh-hant

[可以做的事]
- 自由遊玩、修改、自訂
- 免費再次發布(分享)修改後的版本

[必須遵守的事]
- 署名:發布遊戲時請務必註明原作者。
- 非商業:不得用於販售、付費發布、贊助回饋等收取金錢的用途。
- 保留開始畫面:請勿擅自刪除或遮擋遊戲執行後最先顯示的畫面(帶有製作者署名的開始畫面)。

--------------------------------------------------
2. 署名範例(發布貼文、遊戲內致謝、ReadMe)
--------------------------------------------------

引擎原作:돛트 (Dot-teu) https://x.com/Dot_teu
CC BY-NC 4.0

--------------------------------------------------
3. 外部資源與創作物權利
--------------------------------------------------

- 預設字型(Fonts 資料夾中的 PF Stardust 3.0 S)不在本授權範圍內，遵循該字型自身的使用條款。
- 製作者本人新繪製的圖畫、角色和撰寫的台詞，其著作權歸各製作者所有。
- 使用他人的圖畫、角色或音樂時，請另行確認原作者的使用條款。

==================================================
