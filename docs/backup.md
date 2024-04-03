# Azure Backup

## Cosmos DB Backup

**우선 Cosmos DB는 자동백업이 이루어 진다 그 자동백업을 지속적으로 할것이냐 정기적으로 할것이냐 지정할 수 있다.**

### 지속적인 백업 모드
- 지속적인 백업은 Cosmos DB에서 자동으로 수행하는 백업 메커니즘입니다.
- 데이터베이스에 대한 변경 사항이 발생할 때마다 즉시 백업이 생성됩니다.
- 백업 데이터는 Cosmos DB 서비스 내부에서 안전하게 보관됩니다.
- 지속적인 백업을 사용하면 7일 또는 30일 이내에 새 계정 또는 기존 계정으로 언제든지 복원할 수 있습니다.

![image](https://github.com/JoEunSae/Internship/assets/83803199/745f1968-ddc3-4c36-a109-883ca813efc5)

**보존기간은 7일(무료)와 30일(유로)가 가능하다**

**30일 및 7일 지속적인 백업 계층 둘다 데이터 복원 요금이 발생**

### 정기적인 백업 모드
- 정기적 백업은 사용자가 직접 설정하고 관리하는 백업으로, 일정 주기로 실행됩니다.
- 기존 계정에 하용되는 기본 백업 모드로, 백업이 정기적 간격을 두고 수행되며 지원 팀을 대상으로 요청을 만들면 데이터가 복원됩니다.
- 기본적으로 4시간마다 데이터베이스와 전체 백업을 자동으로 수행하며 기본적으로 항상 2개의 최신 백업만 저장됩니다. (변경 가능)
- 지정된 프로비전된 처리량 컨테이너 또는 공유 처리량 데이터베이스의 기존 스냅샷을 30일 동안 유지
- 실제 데이터는 Cosmos DB내에, 백업은 동일지역 Azure Blob Storage에 GRS로 

![image](https://github.com/JoEunSae/Internship/assets/83803199/b0f06a2c-035b-4e9a-a1d1-78c79de397f6)

ref) <br>
https://azure.microsoft.com/ko-kr/pricing/details/cosmos-db/autoscale-provisioned/ <br>
https://learn.microsoft.com/ko-kr/azure/cosmos-db/continuous-backup-restore-introduction <br>
https://learn.microsoft.com/ko-kr/azure/cosmos-db/periodic-backup-restore-introduction <br>


## Appservice Backup

### 자동 백업
- App Service에서 자동 백업을 설정하여 시스템이 일정한 주기로 백업을 생성합니다.
- 사용자는 별도의 구성이나 작업을 수행할 필요가 없습니다.
- 백업 주기와 보관 기간을 설정할 수 있으며, 백업 데이터는 Azure Sotrage에 저장됩니다.


### 사용자 지정 백업
- 사용자 지정 백업은 사용자가 직접 설정하고 관리하는 백업입니다.
- 사용자는 필요할 때마다 백업을 생성하고, 백업을 수동으로 관리하며, 백업 데이터를 자체 관리합니다.
- 유연성이 높으며 특정 요구 사항에 맞게 조정할 수 있습니다.

![image](https://github.com/JoEunSae/Internship/assets/83803199/eeb65f23-b6f9-4e7a-80e9-0824459d919f)

ref) <br>
https://learn.microsoft.com/ko-kr/azure/app-service/manage-backup?tabs=portal#back-up--restore-vs-disaster-recovery <br>
https://learn.microsoft.com/ko-kr/troubleshoot/azure/app-service/backing-up-restoring-and-cloning-microsoft-azure-app-services
