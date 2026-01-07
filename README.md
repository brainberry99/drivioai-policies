# 드리비오 AI - 개인정보 처리방침 및 이용약관 호스팅 가이드

이 문서는 앱스토어 심사를 위해 개인정보 처리방침과 이용약관을 웹에 호스팅하는 방법을 안내합니다.

## 📋 필요한 파일

- `privacy_policy.html` - 개인정보 처리방침
- `terms_of_service.html` - 서비스 이용약관

## 🌐 웹 호스팅 옵션

### 옵션 1: GitHub Pages (무료, 추천)

1. **GitHub 저장소 생성**
   - GitHub에서 새 Public 저장소 생성 (예: `drivioai-policies`)

2. **파일 업로드**
   ```bash
   cd docs
   git init
   git add privacy_policy.html terms_of_service.html
   git commit -m "Add privacy policy and terms of service"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/drivioai-policies.git
   git push -u origin main
   ```

3. **GitHub Pages 활성화**
   - 저장소 Settings → Pages
   - Source: "Deploy from a branch"
   - Branch: main, /root 선택
   - Save 클릭

4. **URL 확인**
   - 개인정보 처리방침: `https://YOUR_USERNAME.github.io/drivioai-policies/privacy_policy.html`
   - 이용약관: `https://YOUR_USERNAME.github.io/drivioai-policies/terms_of_service.html`

### 옵션 2: Firebase Hosting (무료)

1. **Firebase CLI 설치**
   ```bash
   npm install -g firebase-tools
   ```

2. **Firebase 로그인 및 초기화**
   ```bash
   cd docs
   firebase login
   firebase init hosting
   ```

3. **배포**
   ```bash
   firebase deploy --only hosting
   ```

4. **URL 확인**
   - Firebase 콘솔에서 Hosting URL 확인
   - 개인정보 처리방침: `https://YOUR_PROJECT.web.app/privacy_policy.html`
   - 이용약관: `https://YOUR_PROJECT.web.app/terms_of_service.html`

### 옵션 3: Netlify Drop (무료, 가장 간단)

1. [Netlify Drop](https://app.netlify.com/drop) 접속
2. `docs` 폴더를 드래그 앤 드롭
3. 자동으로 생성된 URL 확인

## 🔧 앱 코드 업데이트

웹 호스팅 후 [setting_screen.dart](../lib/screens/setting_screen.dart) 파일의 URL을 실제 URL로 교체하세요:

```dart
// 개인정보 처리방침 열기
Future<void> _openPrivacyPolicy(BuildContext context) async {
  const url = 'https://YOUR_ACTUAL_URL/privacy_policy.html'; // 실제 URL로 교체
  final uri = Uri.parse(url);
  // ...
}

// 서비스 이용약관 열기
Future<void> _openTermsOfService(BuildContext context) async {
  const url = 'https://YOUR_ACTUAL_URL/terms_of_service.html'; // 실제 URL로 교체
  final uri = Uri.parse(url);
  // ...
}
```

## 📱 App Store Connect 설정

### 1. Privacy Policy URL 설정

1. App Store Connect → 내 앱 선택
2. App Information → Privacy Policy URL
3. 개인정보 처리방침 URL 입력 (예: `https://YOUR_USERNAME.github.io/drivioai-policies/privacy_policy.html`)
4. Save

### 2. EULA (이용약관) 설정

**방법 A: 앱 설명에 링크 추가 (간단)**
- App Store Connect → App Information → Description
- 설명 맨 아래에 이용약관 링크 추가:
  ```
  이용약관: https://YOUR_USERNAME.github.io/drivioai-policies/terms_of_service.html
  ```

**방법 B: Custom EULA 사용 (전문적)**
- App Store Connect → App Information → License Agreement
- "Custom" 선택
- 이용약관 전체 텍스트를 복사하여 붙여넣기
- 또는 "View online at: [URL]" 형태로 링크 제공

### 3. 인앱 구매 (Subscription) 관련 추가 설정

구독 서비스를 제공하는 경우:
1. App Store Connect → Features → In-App Purchases
2. 각 구독 상품 선택
3. "App Store Localization" 섹션에서:
   - Privacy Policy URL 입력
   - Terms of Use (EULA) URL 입력

## ✅ 확인사항

심사 제출 전 다음 사항을 확인하세요:

- [ ] 개인정보 처리방침 URL이 정상적으로 접근 가능
- [ ] 이용약관 URL이 정상적으로 접근 가능
- [ ] 앱 내 설정 화면에서 두 링크가 정상 작동
- [ ] App Store Connect에 Privacy Policy URL 입력 완료
- [ ] 앱 설명 또는 Custom EULA에 이용약관 링크/내용 포함
- [ ] 인앱 구매 상품에도 약관 URL 입력 (해당하는 경우)

## 📧 연락처 업데이트

개인정보 처리방침의 "개인정보 보호책임자" 섹션에서 실제 연락처 이메일을 입력하세요:

```html
<li>연락처: [이메일 주소를 입력하세요]</li>
```

위 내용을 실제 이메일 주소로 변경:

```html
<li>연락처: support@yourdomain.com</li>
```

## ⚠️ 중요 참고사항

1. **HTTPS 사용 필수**: Apple은 HTTPS URL만 허용합니다
2. **접근 가능성**: URL은 누구나 접근 가능해야 합니다 (로그인 불필요)
3. **모바일 최적화**: HTML은 모바일 화면에서도 잘 보여야 합니다 (현재 파일은 반응형으로 제작됨)
4. **업데이트 관리**: 약관 변경 시 웹 페이지도 함께 업데이트해야 합니다

## 🔄 업데이트 프로세스

약관 내용을 변경해야 할 경우:

1. HTML 파일 수정
2. 웹 호스팅 플랫폼에 재배포
3. 앱에서 7일 전 사전 공지 (법적 요구사항)
4. 중요 변경사항의 경우 앱 업데이트 고려

## 문의

심사 관련 문제가 발생하면 Apple App Review 팀에 다음 정보를 제공하세요:

- Privacy Policy URL: [실제 URL]
- Terms of Service URL: [실제 URL]
- 앱 내 접근 경로: 설정 → 약관 및 정책
