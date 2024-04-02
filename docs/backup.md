# Azure Backup

## Cosmos DB Backup

**우선 Cosmos DB는 자동백업이 이루어 진다 그 자동백업을 지속적으로 할것이냐 주기적으로 할것이냐 지정할 수 있다.**

### 지속적인 백업 모드
- 지속적인 백업을 사용하면 7일 또는 30일 이내에 새 계정 또는 기존 계정으로 언제든지 복원할 수 있습니다.
  - 컨테이너 내에서 실수로 인한 쓰기 또는 삭제 작업으로부터 복구
  - 삭제된 계정, 데이터베이스 또는 컨테이너를 복원
  - 특정 복원 시점의 백업이 존재하던 지역으로 복원

![image](https://github.com/JoEunSae/Internship/assets/83803199/745f1968-ddc3-4c36-a109-883ca813efc5)

**보존기간은 7일(무료)와 30일(유로)가 가능하다**

**30일 및 7일 지속적인 백업 계층 둘다 데이터 복원 요금이 발생**

### 정기적인 백업 모드
- 기존 계정에 하용되는 기본 백업 모드로, 백업이 정기적 간격을 두고 수행되며 지원 팀을 대상으로 요청을 만들면 데이터가 복원됩니다.
- 기본적으로 4시간마다 데이터베이스와 전체 백업을 자동으로 수행하며 기본적으로 항상 2개의 최신 백업만 저장됩니다. (변경 가능)
- 지정된 프로비전된 처리량 컨테이너 또는 공유 처리량 데이터베이스의 기존 스냅샷을 30일 동안 유지

컨테이너 또는 데이터베이스가 삭제되면 Azure Cosmos DB는 지정된 프로비전된 처리량 컨테이너 또는 공유 처리량 데이터베이스의 기존 스냅샷을 30일 동안 유지합니다.
    
실제 데이터는 Cosmos DB내에, 백업은 동일지역 Azure Blob Storage에 GRS로 


ref)
https://azure.microsoft.com/ko-kr/pricing/details/cosmos-db/autoscale-provisioned/ <br>
https://learn.microsoft.com/ko-kr/azure/cosmos-db/continuous-backup-restore-introduction <br>
https://learn.microsoft.com/ko-kr/azure/cosmos-db/periodic-backup-restore-introduction <br>

