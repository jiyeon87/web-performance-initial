# 웹사이트 성능 개선 보고서

본 보고서는 [https://pagespeed.web.dev를](https://pagespeed.web.xn--dev-hw8m/) 통해 진단받은 내용을 기반으로 수행한 성능 개선 작업과 그 결과를 정리한 것입니다.

## 성능 개선 사항

| 개선 사항                                             | 개선된 지표                                                                                                                                 | 개선 방법                                                                                                                                       |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 이미지 최적화 작업                                    | 대용량 이미지들을 압축하고 WebP 형식으로 변환하여 로딩 시간을 단축. [LCP](https://web.dev/articles/lcp?hl=ko)가 평균 9.1초에서 4.8초로 개선 | 기존에 있는 이미지들을 터미널 명령어를 통해서 JPG 이미지를 WebP 로 변환 [(변환 방법)](https://web.dev/articles/codelab-serve-images-webp?hl=ko) |
| img태그 width/height 속성 & 반응형 이미지 제공        | LCP 가 평균 4.8초에서 2.0초로 개선 및 모바일 사용자의 데이터 사용량이 내려감                                                                | img/source 태그에 width/height 속성을 부여 및 <picture> 요소와 <source> 태그를 사용하여 반응형 이미지 구현                                      |
| 렌더링 차단 리소스 제거                               | 렌더링 차단 리소스를 제거하여 페이지 로딩 속도를 개선                                                                                       | 중요하지 않은 cookie 관련 script를 비동기 처리                                                                                                  |
| 외부 font 서버로부터 font를 받아서 초기 렌더링이 느림 | [FCP](https://web.dev/articles/fcp?hl=ko) 가 평균 2.4초에서 0.8초와 [LCP](https://web.dev/articles/lcp?hl=ko) 2.6초에서 1.9초로 개선        | font를 프로젝트 내부에서 호스팅                                                                                                                 |
| 자바스크립트 실행 시간 단축                           | [TBT](https://web.dev/articles/tbt?hl=ko) 가 평균 710 밀리초에서 10밀리초로 개선                                                            | Intersection Observer API를 사용하여 뷰포트에 진입한 상품만 로드                                                                                |

## 결론

위의 개선 작업을 통해 전반적인 웹사이트 성능이 크게 향상되었습니다. PageSpeed Insights 점수가 모바일에서 40점에서 100점으로, 데스크톱에서 63점에서 100점으로 상승했습니다.

### **BEFORE**

<img width="850" alt="스크린샷 2024-08-15 오후 9 19 38" src="https://github.com/user-attachments/assets/06503f0a-2952-446f-bdad-99cd48b001c7">
<img width="851" alt="스크린샷 2024-08-15 오후 10 25 32" src="https://github.com/user-attachments/assets/5c7e8fdc-3710-435c-bb94-07cab05a1e28">

### AFTER

<img width="861" alt="스크린샷 2024-08-16 오전 5 29 37" src="https://github.com/user-attachments/assets/0a59566a-9cba-4ea1-9f45-936246c49222">
<img width="860" alt="스크린샷 2024-08-16 오전 5 15 09" src="https://github.com/user-attachments/assets/bcb53b79-4b35-4044-ba79-39eeceb2f182">
