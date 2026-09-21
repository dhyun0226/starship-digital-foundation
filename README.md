# STARSHIP Digital Foundation

STARSHIP Entertainment의 공개 채용공고와 면접에서 들은 내용을 바탕으로 정리한 개인 아키텍처 제안입니다.

> 이 프로젝트는 회사의 실제 내부 시스템이나 확정된 구축안을 나타내지 않습니다. 입사 후 AS-IS, 예산, 보안정책 및 업무 요구사항을 확인한 뒤 변경하는 가설 기반 포트폴리오입니다.

## 구성

- STARSHIP Digital Foundation: 사용자 진입부터 AWS VPC, 보안·관제, 배포환경, 데이터·디자인 기반과 향후 AX까지 한 장에 표현
- CHEESE Design System: 실제 CSS Token과 Button, Form, Alert, Dialog, Toast, Badge, Card, Table 구현

## CHEESE 구조

당근 SEED의 단일 토큰 원천, 스타일 Recipe, Headless 동작, Styled Component 분리 원칙을 참고했습니다. SEED 코드를 복사하지 않고 업무 시스템에 맞는 별도 토큰과 컴포넌트를 구현합니다.

```text
CHEESE Tokens
→ CSS Variables
→ Accessible Primitives
→ Components
→ Business Patterns
→ Digital Products
```

## 로컬 실행

별도 빌드가 필요하지 않습니다. `index.html`을 브라우저에서 열면 됩니다. Mermaid와 웹폰트를 CDN에서 불러오므로 인터넷 연결이 필요합니다.

로컬 HTTP 서버가 필요하면 다음 중 하나를 사용할 수 있습니다.

```bash
npx serve .
```

또는

```bash
python -m http.server 8080
```

## GitHub Pages 배포

1. 이 폴더를 GitHub 저장소에 push합니다.
2. 저장소의 **Settings → Pages**로 이동합니다.
3. Source에서 **GitHub Actions**를 선택합니다.
4. `main` 브랜치에 push하면 포함된 workflow가 정적 사이트를 배포합니다.

배포 주소는 일반적으로 다음과 같습니다.

```text
https://<github-username>.github.io/<repository-name>/
```

## 기술 원칙

- Managed Service 우선
- Modular Monolith 우선
- Private by default
- Build once, deploy many
- 실제 제품에서 검증된 요소만 공통 기반으로 승격
- 개인에게 종속되지 않도록 ADR, Runbook, 운영 문서 유지
