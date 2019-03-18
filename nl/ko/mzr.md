---

copyright:
  years: 2017, 2018
lastupdated: "2019-01-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# MZR(Multi-Zone Region) 개요
{: #multi-zone-region-mzr-overview}

로드 밸런서를 작성할 때 해당 로드 밸런서가 작성되어야 하는 데이터 센터를 지정합니다. 이 데이터 센터가 MZR(Multi-Zone Region)의 일부이면 두 개의 서로 다른 데이터 센터에서 로드 밸런서 노드가 인스턴스화됩니다. 예를 들어 `us-south`는 `dal10`, `dal12`, `dal13`을 포함하는 MZR입니다. 고객이 `dal13` 데이터 센터에 로드 밸런서를 작성하는 경우 `dal13`, `dal10` 또는 `dal12`에서 노드가 인스턴스화됩니다. 일반적으로 트래픽이 명확하게 변경되지 않습니다. MZR 지원은 데이터 센터와의 통신이 중단되는 경우 유용합니다. 다른 노드가 다른 데이터 센터에 있으므로 로드 밸런서가 계속 작동합니다.

현재 다음 데이터 센터가 MZR의 일부입니다.

| MZR 이름 | 데이터 센터 |
| ---------|--------------|
| us-south | dal10, dal12, dal13 |
| us-east | wdc04, wdc06, wdc07 |


## MZR 요구사항
MZR(Multi-Zone Regions)의 요구사항은 다음과 같습니다.
* 선택한 데이터 센터는 MZR의 일부여야 합니다. 위의 표에는 지역과 각 지역의 데이터 센터가 나열되어 있습니다.
* 계정에서 VLAN Spanning이 사용으로 설정되어야 합니다.
* 사설 서브넷은 MZR의 데이터 센터에 있는 계정에 있어야 합니다. 데이터 센터에 컴퓨팅 디바이스를 작성하면 사설 서브넷이 인스턴스화됩니다.

선택하는 데이터 센터가 MZR의 일부가 아니거나 계정에서 VLAN Spanning이 사용되지 않은 경우 로드 밸런서를 작성하면 기본적으로 사용자가 지정하는 데이터 센터에서 모든 로드 밸런서 노드를 인스턴스화하는 원래 동작이 수행됩니다.
