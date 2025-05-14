# EternalReturn_Overview
- 이터널 리턴 모작입니다.  
- 핵심기술은 이력서와 같이 제출된 기술소개서에 작성되어 있습니다.  

# 작업  개요
[유튜브 링크](https://youtu.be/VZujHWG_ztw)  
> 작업 기간: 2024.07.29 ~ 2024.10.25 (약 3달)  
> 사용 언어: C++, Hlsl, Python3  
> 개인 작업  
> 기술 스텍  
>>- DirectX11  
>>- Hlsl  
>>- GitHub Desktop  
>>- ImGUI  
>>- FMOD  
>>- Assimp  

# 핵심 구현
> 1. 인벤토리, 아이템 제작/사용/장착
> 2. 스킬 캐스팅, 쿨타임, 스텟 등의 UI
> 3. 맵툴/이펙트 툴 (따로 소개하는 글을 작성하겠습니다.)

# 세부 구현사항
### 인벤토리
![image](https://github.com/user-attachments/assets/c63aa028-7f79-47cf-9096-1efde2c3e265)  
- 아이템을 얻으면 인벤토리에 들어갑니다.  
- 아이템을 드래그해서 위치를 바꿀 수 있습니다.
- 아이콘 좌하단에 수량이 표시됩니다.
- 보유 중인 아이템들로 제작 가능한 아이템이 상단에 제시되고, 클릭시 제작됩니다.  
![image](https://github.com/user-attachments/assets/4d3c1aac-d7b0-4f41-b795-d9b5f71842ad)  


- 아이템의 등급에 따라 뒷배경의 색이 달라집니다.
   >- 일반: 투명
   >- 고급: 초록  
   >- 희귀: 파랑  
   >- 영웅: 보라  
   >- 전설: 노랑
- 음식의 경우 사용하면 아이템의 설정된 값만큼 HP/MP를 회복합니다.
- 장비의 경우 사용하면 장착한 뒤 장비 스텟이 반영됩니다.
   >- 공격력  
   >- 방어력  
   >- 체력
   
### 아이템 박스UI
![image](https://github.com/user-attachments/assets/5871febd-c17d-42e9-82c2-ca754a58b111)  
- 적의 시체와 아이템 박스를 클릭하면 아이템 박스 UI가 나옵니다.  
- 동물/박스가 가지고 있던 아이템을 표시하고, 클릭해서 얻으면 인벤토리로 아이템이 들어갑니다.  
- 앞쪽의 아이템을 가져가면 뒤쪽의 아이템들이 앞으로 당겨집니다.  
### 플레이어 UI
![image](https://github.com/user-attachments/assets/d0de5c67-6a94-44a8-a255-17e016991f09)  

- HP와 MP를 표시합니다.
- HP의 경우 100마다 눈금을 넣었습니다.  
![image](https://github.com/user-attachments/assets/aa23b659-e6d2-436d-942d-c4374b4e4dcc)  
- 하단에 HP, MP, 공격력, 방어력이 표시됩니다.
- 플레이어 초상화 좌측에 장착중인 장비 아이템이 표시됩니다. 클릭하면 해제할 수 있습니다.
- 스킬의 남은 쿨타임이 표시됩니다. 남은 쿨타임 비율만큼 반시계 방향으로 아이콘을 어둡게 처리했습니다.
### 행동 UI
![image](https://github.com/user-attachments/assets/e2faa62c-cb7d-4d06-bbf4-15155ed982db)  
- 아이템 제작 시 플레이어는 제작 중인 샹태가 되고 진행도 UI가 생성됩니다.
  아이템 타입에 따라 제작 모션이 다릅니다.
![image](https://github.com/user-attachments/assets/2225063e-23a8-46f1-9333-74f4b69f32dc)
![image](https://github.com/user-attachments/assets/32bed7f6-3c89-4346-b98c-a7d681bc3fd1)
![image](https://github.com/user-attachments/assets/0023a2b5-7371-41bc-a6da-82c89344c3b5)
- 스킬 종류에 따라 알맞은 캐스팅 UI가 제시됩니다.
- 지형을 덮어씌우면서 출력하되, 동시에 플레이어나 몬스터같은 주요 객체를 가리지 않게 했습니다.

### 적
- 야생동물과 위클라인을 구현했습니다. (원작이랑 많이 다릅니다.)  
   >- 위클라인  
   >- 멧돼지: 처음 공격받을 경우 플레이어에게 돌진하여 넉백시킵니다.  
   >- 늑대: 공격받으면 일정 시간마다 하울링해서 주변의 야생동물들이 플레이어를 공격하게 합니다.  
   >- 닭  
   >- 들개  
   >- 박쥐  
   >![image](https://github.com/user-attachments/assets/9df1d9ce-f406-4ba6-89d5-284c9427e6f1)  
- 플레이어를 쫓다가 스폰지점에서 멀리 떨어지면 체력을 전부 회복하고 원래 자리로 돌아갑니다.  
- 위클라인은 네 종류의 공격을 사용합니다.  
   >- 일반 공격  
   >- 플레이어가 멀어지면 돌진해서 추격합니다.  
   >- 반원 범위로 공격합니다.(화무십일홍)  
   >- 플레이어를 바라보고 공격을 충전한 뒤 쏩니다.  
- 야생동물들은 행동 트리를 사용하여 행동을 제어했습니다.  

### 이펙트
![image](https://github.com/user-attachments/assets/d408f13e-d136-4df5-be8d-1ee269d9392c)   
![image](https://github.com/user-attachments/assets/072efd4b-8405-4a9e-9edf-3446d34eb946)  
- 블러와 글로우 효과를 넣어서 이펙트를 흐릿하게 번지고, 더 밝게 만들었습니다.
- 트레일 이펙트를 만들었습니다.
