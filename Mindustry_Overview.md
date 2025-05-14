# Mindustry(Maptool)_Overview
# 🗺️ 작업 개요
[유튜브 링크](https://youtu.be/6f3Dh_f-bUI?si=luaAIkSgYBgvT8lV) / 
[작업 계획 및 스케쥴](https://docs.google.com/spreadsheets/d/1bZk6VRwaPgibCmlTrZYsdJl5gqvpjnND-Cx6VtI6I94/edit?usp=sharing)
>🏁 작업 기간 : 4/22 ~ 4/30 (9일)  
>📚 사용 언어: C++  
>🧑‍🤝‍🧑 2인 작업 (심현우, 최승준)  
>💻 기술 스텍  
>>- MFC  
>>- TCP소켓 프로그래밍  
>>- 깃허브 데스크탑

# 🚩핵심 구현
### 1. 맵툴
> 원하는 이미지 파일들을 불러와서 타일로 사용합니다.  
> 타일로 된 맵을 꾸미고, 자원을 배치합니다.  
> 맵을 저장하거나 불러옵니다.  

### 2. 채팅/저장 서버
> 서버와 연결해서 맵을 업로하고, 채팅을 할 수 있습니다.  

# 👷 역할 분담
### 1. 심현우 (팀장)
> - 채팅  
> - 클라이언트 파싱  
> - 유닛툴  
> - 미니맵  
> - 레이어 전환, 구분 UI  

### 2. 최승준
> - 로컬 서버에 맵 저장/불러오기  
> - 타일맵 배치/삭제  
> - 자원/드릴 배치 및 통계  
> - 마우스 피킹  
> - 피킹 박스  


# 세부 구현사항
- 메인화면 좌측의 버튼들을 기준으로 카테고리를 나누어서 설명하고 있습니다.

### 메인 화면
- 기본 화면입니다.
   - 타일을 좌클릭하면 해당 타일을 현재 선택중인 타일로 바꿉니다.
   - 타일을 우클릭하면 선택중인 오브젝트가 설치/제거됩니다.  
   - 좌상단의 미니맵으로 전체 맵을 보여줍니다.  
![image](https://github.com/user-attachments/assets/8a6923de-9312-43dc-8de0-ad8819a071c2)  

- 마우스가 있는 타일 위치에 피킹 박스가 따라다닙니다.  
![image](https://github.com/user-attachments/assets/5d972731-e7d0-4ae7-a2f2-a9663778c2f9)

- R 버튼을 누르면 전체 맵을 다른 타일로 바꿉니다.  
![image](https://github.com/user-attachments/assets/c3ab5c33-df9a-4d0a-ab83-517939123e4d)

- 자원과 드릴을 배치해보고, 드릴이 채굴중인 자원량을 표시합니다.  
![image](https://github.com/user-attachments/assets/5e44c669-44b5-4872-a268-313f9f1c5aee)

### 유닛 탭
- 플레이어의 스텟을 설정하고, 인게임에서 플레이어 시작 위치를 설정할 수 있습니다.
- 추가 버튼을 누를 때마다 플레이어의 정보가 갱신됩니다.  
![image](https://github.com/user-attachments/assets/508dfc95-ce1c-4224-afa3-b0cd379b8b9b)  

### 맵툴 탭
- 타일 불러오기, 맵 저장, 불러오기 등의 기능을 구현했습니다.
- (촬영을 위한 환경이라 서버IP를 127.0.0.1로 설정했습니다.)
![image](https://github.com/user-attachments/assets/f65c903b-0514-4a84-a6ec-5dbd220dfc29)  

- ```TileSetSave```, ```TileSetLoad```  
타일 이미지의 경로들을 기록한 txt 파일을 선택해서 이미지들을 불러옵니다.  

- ```클라우드 업로드```, ```클라우드 다운로드```(사실 네트워크 클라우드 시스템은 아닙니다.)  
열려있는 로컬 서버로 현재 맵 데이터를 전송하거나 받아옵니다.
- 파일을 선택해서 타일을 확인하거나 맵에 설치할 수 있습니다.

### 오브젝트 탭
- 오브젝트들을 확인하고, 배치할 수 있습니다.  
   - 광물  
   - 타일  
   - 드릴  
- 설치해둔 오브젝트들을 저장하고, 불러올 수 있습니다.  
![image](https://github.com/user-attachments/assets/4ecf94b4-9595-4ef7-acf3-dd34d99f0d40)

### 경로 탭
- 현재 로드되어 있는 타일들의 경로를 확인하고, 저장할 수 있습니다.
- 저장된 타일 이미지 세트들을 전부 불러올 수 있습니다.
(타일 세트들을 불러오는 프리셋을 의도했습니다.)
![image](https://github.com/user-attachments/assets/07aabc06-028a-404c-b886-7062b5aa28d5)


### 채팅
- 작업 중 편리하게 소통할 수 있도록 간단한 채팅 시스템을 구현했습니다.
- 닉네임을 적고 Connect를 누르면 설정된 IP를 통해 채팅 서버에 연결됩니다.
- 하단 메시지박스에 글을 적고 Submit버튼을 누르면 채팅이 송신됩니다.
![image](https://github.com/user-attachments/assets/cb2b30c0-94e0-406f-ac05-b0d03e2bbf38)

