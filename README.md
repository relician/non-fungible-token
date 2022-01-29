# non-fungible-token

## Blockchain 개발은 크게 두가지 형태로 구분 됩니다. 
- Blockchain 네트워크 (MainNet, SideChain 등)
- Blockchain 기반 서비스 (DApp 또는 BApp )

NFT 관련 서비스는 위에서 DApp에 해당하는 것으로 보이기 때문에, 이에 집중해서 설명 또는 자료를 전달 드리고자 합니다.

## NFT 관련 서비스 필수 요소
- Smart Contract : Back-end의 처리 로직과 Data관리를 대체하는 Bytecode
- Client App : Front-end Web 또는 모바일 App
  (이 또한 자체 Wallet 기능을 개발하거나, 3rdParty Wallet 연동이 필요합니다.)
  
※ Wallet이 필요한 이유는 <br/>
- Client가 누구인 지 식별(Address)하고,
- Blockchain의 상태를 천이 시키는 행위[ Coin의 거래나 Smart Contract의 함수 실행, 수수료 차감 등 ]를 요청할 때 Signature를 포함해야 하는데, 이 Sign을 생성할 때 필요한 Key (WalletKey 또는 PrivateKey)를 관리해 주기 때문입니다.
<br/>
<br/>
--- 여기서부터는 Etherium 또는 그 계열인 Klaytn을 기준으로 작성하겠습니다.<br/>

## DApp 관련 서비스 개발 시 필수 요소
- 개발용 Blockchain 설치 및 네트워크 구축
  - Etherium이나 Klaytn을 추천 드립니다.
  - EOS는 또 개념이 달라요.
- Smart Contract 개발 언어
  - Solidity (Etherium, Klaytn) https://docs.soliditylang.org/en/latest/
  - C++ (EOS - 비추천)
- Smart Contract 관리 계정<br/> Contract 배포에도 수수료가 들어가기 때문에 외부소유계정 (EOA)가 있어야 합니다.
- Wallet<br/> 서비스 이용자의 Address와 Private Key를 관리 해주면서, Smart Contract 연동 시 Signature를 생성하는 기능을 제공하는 프로그램 또는 모듈.
- Application: UI 및 Smart Contract 연동 프로그램. 
  - Web: HTML, Javascript 필수, Wallet 연동 시 Web3.js 모듈 사용 필수, Wallet 사용 하지 않으면 거의 불가하다 보시면 됩니다.
  - App: App은 잘 몰라요.. Wallet 연동 하는 경우도 있는데 자체 개발하는 경우도 많다고 합니다.
- Back-office: 서비스 컨트랙트의 배포, 서비스 상태 모니터링, 토큰의 발행/소각 등의 관리, 거래소 연동 등을 생각하면 필요하지 않을까 생각됩니다.

![image](https://user-images.githubusercontent.com/37832355/151664256-244686d0-bed3-42a3-aa19-d11b090936e6.png)



## NFT 관련 서비스를 제공하기 위해 개발되어야 하는 내용
- NFT 표준 Interface 기반 Smart Contract<br/>
아래의 표준 interface를 따르는 Smart Contract를 개발하고 Blockchain에 배포함으로써 Token을 민팅 (minting - 발행, 생성)할 수 있습니다.<br/>
    - ERC 20 , ERC 721<br/>
ERC 20의 컨셉은 누가, 얼마나 Token을 가지고 있는지?를 관리하는 내용을 담고 있고,<br/>
ERC 721의 컨셉은 누가, 어떤 Token을 가지고 있으며, 각각의 Token이 어떤 Metadata를 가지고 있는지? 를 관리하는내용을 담고 있습니다.<br/>
    - ERC 1155 는 ERC20과 ERC721을 한번에 관리하겠다는 내용이라고 하는데 저도 아직 표준 인터페이스를 제대로 보지 않았습니다. (Klaytn은 아직 지원을 못하고 있다고 해서요...) <br/><br/>
- NFT 서비스 로직 및 데이터 관리 Smart Contract<br/>
서비스 이용자 각각의 개인 컬렉션 관리 기능, 개인 컬렉션의 NFT 등록, 거래, 이용 이력 관리 등의 서비스가 제공해야 하는 기능을 개발해야 합니다.<br/>이는 서비스의 특성에 따라 다른 부분이라...<br/>
예시로 여기 링크를 한번 훑어 봐 주세요. https://brunch.co.kr/@curg/20<br/>
- NFT 서비스와 연결될 UI <br/>
이 UI에는 Wallet 기능 또는 연동 기능이 포함되어 있어야 하며, Wallet의 Address가 보유한 Collection 들에 대한 관리 기능이 구현되어야 합니다.<br/>
- BackOffice
부가적으로 Back-end를 구축하여 Smart Contract가 제공하지 못하는 기능을 제공할 수도 있습니다.
