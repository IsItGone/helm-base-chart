# Helm Base Chart Repository

이 저장소는 Spring, Flutter 애플리케이션에서 공통적으로 사용되는 Helm 차트를 정의합니다.

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
특정 차트를 설치하려면 다음 명령을 실행합니다.

```bash
helm install my-release isitgone-base/<chart-name> --values values.yaml
```

- `<chart-name>`을 원하는 차트 이름으로 변경하세요.
- `--values values.yaml`을 사용하여 사용자 정의 값을 적용할 수 있습니다.

