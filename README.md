# Helm Base Chart Repository

이 저장소는 Spring, Flutter 애플리케이션에서 공통적으로 사용되는 Helm library 차트를 정의합니다.

## 구조
- `/packages` 디렉터리: 패키징된 차트 및 `index.yaml`을 포함합니다.

## Helm 리포지토리 추가 및 차트 검색

아래 명령어를 실행하여 Helm 리포지토리를 추가하고 사용 가능한 차트를 검색할 수 있습니다.

```bash
helm repo add isitgone-base https://isitgone.github.io/helm-base-chart/packages
helm repo update
helm search repo isitgone-base --devel
```

- `helm repo add`: Helm 리포지토리를 추가합니다.
- `helm repo update`: 로컬 캐시를 업데이트하여 최신 차트 정보를 가져옵니다.
- `helm search repo isitgone-base --devel`: 개발 버전을 포함하여 리포지토리의 모든 차트를 검색합니다.

## 사용 예시
library 차트는 설치할 수 없습니다. 대신 다른 차트의 Chart.yaml의 dependencies를 설정해 참조할 수 있습니다.

```yaml
apiVersion: v2
name: my-spring-app
version: 0.1.0
dependencies:
  - name: spring-base
    version: "0.0.0"
    repository: "https://isitgone.github.io/helm-base-chart/packages"
```