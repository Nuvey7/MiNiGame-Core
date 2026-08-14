# MiNiGame
이 마인크래프트 플러그인은 1.21.8(JAVA25) 기반으로 제작 되었습니다.

이 플러그인은 나중에 따로 제작할 Bedwars, Skywars, TnT Tag, TNT Run 등 미니게임 요소를 넣어서 실행 할 수 있는 Core 플러그인 입니다

지금 현재는 Development Build라서 매우 불안정 합니다.

현재 추가 되어있는 기능/명령어는

<유저 명령어>
/game list - 등록 되어 있는 게임 목록 표시
/game join <게임ID> - 해당 게임 Queue 참가
/lobby - Queue 또는 게임에서 나와 로비로 이동
/hub - /lobby와 같음
/leave - /lobby와 같음
/stats - 승리, 패배, 킬, 데스, 플레이 횟수 확인
/coins - 현재 Coins 확인
/party invite <플레이어> - 파티 초대
/party accept <파티장> - 파티 초대 수락
/party leave - 파티 탈퇴
/party kick <플레이어> - 파티원 추방
/party disband - 파티 해산
/party list - 파티장과 파티원 확인
/p - /party와 같음
파티장이 게임 Queue에 참가하면 온라인 상태인 파티원도 함께 들어갑니다. 파티원은 직접 파티 Queue를 시작할 수 없습니다.

<관리자 명령어> (luckperms 권한 : minigame.admin)
/arena create <게임ID> <Arena명> - 현재 월드에 아레나 생성
/arena delete <Arena명> - 사용중이 아닌 아레나 삭제
/arena setlobby <Arena명> - 현재 위치를 대기장소로 설정
/arena setspawn <Arena명> - 현재 위치를 게임 스폰장소로 설정
/arena setspectator <Arena명> - 현재 위치를 관전자 스폰장소로 설정
/arena enable <Arena명> - 아레나 활성화
/arena disable <Arena명> - 아레나 비활성화
/arena info <Arena명> - 게임, 월드, 상태, 인원, 설정 완료 여부 확인
/arena list - 모든 아레나 목록 표시
세 Spawn이 모두 설정되어야 Arena를 활성화할 수 있습니다. Arena 정보는 arenas.yml에 저장됩니다.

<게임 관리>
/game end <Arena명> - 진행중인 게임 강제종료
/minigame - 플러그인 버전과 게임/Arena 개수 표시

<Coins 관리>
/coins give <플레이어> <금액> - Coins 지급
/coins remove <플레이어> <금액> - Coins 차감
/coins set <플레이어> <금액> - Coins 잔액 설정

<로비 기능>
플레이어 접속 또는 게임 종료 시 상태를 초기화하고 로비로 이동시킵니다.
1번 슬롯: 게임 선택기
5번 슬롯: 프로필
9번 슬롯: 로비 설정
게임 선택 GUI에는 등록된 게임과 Queue 인원이 표시됩니다.
프로필 GUI에서는 다음 정보를 확인할 수 있습니다.
닉네임
Coins
전체 승리
전체 킬
플레이 횟수
게임별 승리 기록
로비 설정 GUI에는 서버 선택 메뉴가 있습니다. config.yml에서 proxy.enabled: true로 설정하면 BungeeCord 호환 플러그인 메시지를 통해 다른 서버로 이동합니다.

<게임 진행 기능>
게임 선택
→ Queue 참가
→ 사용 가능한 Arena 자동 배정
→ 최소 인원 충족
→ Countdown
→ 게임 시작
→ 사망 시 관전자
→ 승자 판정
→ Stats와 Coins 기록
→ 로비 복귀
Countdown에는 다음 표시가 사용됩니다.
BossBar
ActionBar
마지막 5초 Title
인원이 최소 인원 아래로 감소하면 Countdown이 자동 취소됩니다.

<관전자 기능>
게임 중 사망하면 관전자가 됩니다.
블록 설치 및 파괴 방지
아이템 드롭 및 습득 방지
공격 및 피해 방지
배고픔 방지
비행 가능
살아 있는 플레이어 텔레포터 GUI
게임 나가기 아이템
외부 게임용 일반 관전자 입장 API

<데이터와 화면 표시 기능>
SQLite 기본 지원
MySQL 교체 지원
DB 작업은 전용 비동기 스레드에서 처리
Wins, Losses, Kills, Deaths, Games Played, Play Time 저장
게임별 통계 분리 저장
Lobby 및 게임 Scoreboard
TabList Header/Footer
변경된 경우에만 Scoreboard 다시 표시
PlaceholderAPI 선택 연동
(
지원 Placeholder :
%minigame_coins%
%minigame_wins%
%minigame_kills%
%minigame_game%
%minigame_arena%
)

<확장 API 기능>
다른 플러그인에서 다음 기능을 가져다 쓸 수 있습니다.
새로운 Minigame 등록
Arena 조회 및 관리
Queue 참가 처리
Party 조회
Coins 처리
게임 Lifecycle 제어
일반 관전자 참가
게임별 Listener, 아이템, 팀, Scoreboard 등록
제공 이벤트:
PlayerJoinGameEvent
PlayerLeaveGameEvent
GameStartEvent
GameEndEvent
PlayerJoinQueueEvent
PlayerLeaveQueueEvent
PlayerCoinsChangeEvent
명령어 선언은 [plugin.yml](/home/vireinne/바탕화면/Coding/MINIGAME/src/main/resources/plugin.yml), 실제 처리 코드는 [command 디렉터리](/home/vireinne/바탕화면/Coding/MINIGAME/src/main/java/dev/minigame/core/command)에 있습니다.
