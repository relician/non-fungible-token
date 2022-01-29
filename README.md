# non-fungible-token

## Blockchain 개발은 크게 두가지 형태로 구분 됩니다. 
- Blockchain 네트워크 (MainNet, SideChain 등)
- Blockchain 기반 서비스 (DApp 또는 BApp )

NFT 관련 서비스는 위에서 DApp에 해당하는 것으로 보이기 때문에이에 집중해서 설명 또는 자료를 전달 드리고자 합니다.

## NFT 관련 서비스 필수 요소
- Smart Contract : Back-end의 처리 로직과 Data관리를 대체하는 Bytecode
- Client App : Front-end Web 또는 모바일 App
  (이 또한 자체 Wallet 기능을 개발하거나, 3rdParty Wallet 연동이 필요합니다.)
  
※ Wallet이 필요한 이유는 Client가 누구인 지 식별(Address)하고,
  Blockchain의 상태를 천이 시키는 행위[ Coin의 거래나 Smart Contract의 함수 실행, 수수료 차감 등 ]를 요청할 때 Signature를
  포함해야 하는데, 이 Sign을 생성할 때 필요한 Key (WalletKey 또는 PrivateKey)를 관리해 주기 때문입니다.
  
  
--- 여기서부터는 Etherium 또는 그 계열인 Klaytn을 기준으로 작성하겠습니다.
## NFT 관련 서비스를 제공하기 위해 개발되어야 하는 내용
- NFT 표준 Interface 기반 Smart Contract
아래의 표준 interface를 따르는 Smart Contract를 개발하고 Blockchain에 배포함으로써 Token을 민팅 (minting - 발행, 생성)할 수 있습니다.

  - ERC 20 , ERC 721
    ERC 20의 컨셉은 누가, 얼마나 Token을 가지고 있는지?를 관리하는 내용을 담고 있고,
    ERC 721의 컨셉은 누가, 어떤 Token을 가지고 있으며, 각각의 Token이 어떤 Metadata를 가지고 있는지? 를 관리하는내용을 담고 있습니다.
    https://brunch.co.kr/@curg/20
  - ERC 1155 는 ERC20과 ERC721을 한번에 관리하겠다는 내용이라고 하는데 저도 아직 표준 인터페이스를 제대로 보지 않았습니다. (Klaytn은 아직 지원을 못하고 있다고 해서요...) 
  

