# Helm Base Chart Repository

이 저장소는 Spring, Flutter 애플리케이션에서 공통적으로 사용되는 Helm library 차트를 정의합니다.

## 구조
- `/packages` 디렉터리: 패키징된 차트 및 `index.yaml`을 포함합니다.

## Helm 리포지토리 추가

library 차트는 Helm cli를 이용하여 Helm 리포지토리에 추가할 수 있지만, 설치할 수는 없습니다.

```bash
helm repo add isitgone-base https://isitgone.github.io/helm-base-chart/packages
helm repo update
helm search repo isitgone-base --devel
```
- `helm repo add`: Helm 리포지토리를 추가합니다.
- `helm repo update`: 로컬 캐시를 업데이트하여 최신 차트 정보를 가져옵니다.
- `helm search repo isitgone-base --devel`: 개발 버전을 포함하여 리포지토리의 모든 차트를 검색합니다.

## 사용법
다른 차트의 Chart.yaml에 base chart를 dependencies에 추가해 값만 재정의하여 사용할 수 있습니다.

```yaml
apiVersion: v2
name: my-spring-app
version: 0.1.0
dependencies:
  - name: spring-base
    version: "0.0.0"
    repository: "https://isitgone.github.io/helm-base-chart/packages"
```

## 값 재정의
Spring 기본 설정값은 다음과 같습니다.
```yaml
server:
  shutdown: graceful
spring:
  webflux:
    base-path: /api
logging:
  level:
    root: INFO
```

사용자 정의 설정 값은 custom value 파일의 `spring.application.yml`하위에 작성하여 기본값을 재정의할 수 있습니다.
```yaml
spring:
  application:
    yml:
      # 아래 설정 값은 ConfigMap의 application-<profile>.yml 키에 대한 값으로 추가됩니다.
      logging:
        level:
          root: DEBUG # Override
      spring:
        webflux:
          base-path: / # Override
```