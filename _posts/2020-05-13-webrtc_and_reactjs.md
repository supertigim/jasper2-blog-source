---  
layout: post  
current: post
cover: assets/images/webrtc_reactjs_demo.png
navigation: True
title: WebRTC와 ReactJS   
tags: technology
class: post-template
subclass: 'post tag-technology'  
author: tigim
---  

WebRTC와 ReactJS를 활용한 모바일 로봇 조이스틱 웹앱 프로젝트 정리  

Background  
==========    

전부터 불만이었던 유저 인터페이스를 개선해보고자 최대한 간단한 형태의 모바일 로봇용 조이스틱 프로그램을 개발 하기로 했다. 목표는 최대한 간단하며, 심플하고 매우 직관적이어야 한다는 것이다. 그래서 생각한 것이 FPV 형태의 모바일 게임 인터페이스 였다.

**디자인 상세**   

1. 백그라운드는 로봇이 이동하는 방향의 카메라 영상  
2. 조이스틱은 360도 모든 방향을 지원하며, 속도 표현도 가능  
3. 다른 기능은 Switch Button을 이용   
4. 로봇에 네트워크 스위치가 있기 때문에 보안을 위한 추가 기능(eg. 로그인 프로세스)은 배제  
5. 사용자의 모바일 기기에서 추가적인 설치 없이 사용 가능  
6. 개발 기간은 1달 이내  

위의 요구 사항을 기반으로 진행을 했으며, 가능한 심플하게 구현해 보았다. 자세한 소스코드는와 설치는 깃허브  [github.com/supertigim/video_streaming_on_web](https://github.com/supertigim/video_streaming_on_web)에 올려 두었다.  


Architecture  
============  

![](https://github.com/supertigim/video_streaming_on_web/raw/master/data/video_streaming_system_architecture.png)

전체 구조는 간단하다. 일반적인 웹앱의 형태로 구성했고, 백엔드 WebRTC 시그널링을 위해 좀 더 친숙한 Python을 사용했다. 정확히 표현하자면, 자바스크립트로는 뭐를 못하겠다.  


Tech Stack  
==========   

- ReactJS 
- ReactRTC (정확히는 수정하여 사용)
- AioHttp
- AioRTC
  

Details  
=======  

자세한 내용은 코드를 보면 대부분 이해가 될 것 이고, 어렵지 않게 구현을 하였다. 물론 기본적인 WebRTC의 개념과 ReactJS의 동작 원리를 알고 있으면 좀더 쉬울 것이다.  

**WebRCT Signalling**  

이부분이 진행하기 제일 어려웠다. 무엇보다 프로토콜을 분석할 만한 시간적인 여유가 없었기 때문에 동작 원리를 정확히 이해하지 못하고 시작한게 어려움의 가장 큰 이유가 아니었나 생각한다. 결국 하다보니 어찌어찌 완성은 했는데, 고생한 건 분명하다. ㅎㅎㅎ 이해 하는데 가장 도움이 되었던 것은 ReactRTC의 소스 코드 였고, 이에 맞춰서 시그널링 서버를 구축했다. 그리고, AioRTC의 예제도 많이 참고 하였는데, 이부분도 테스트를 위해 살려두었다. 결국 시스템은 AioRTC의 예제와 ReactRTC를 모두 지원하게 되었다. 

웹 시그널링을 위한 통신 방법은 여러가지 있는데, AioRTC 예제는 REST API, ReactRTC에서는 WebSocket을 이용했다. 리액트에서도 REST API로 처리하려 했으나, 아시다시피 포트가 틀리면 처리해 줘야 하는 다른 어려움이 있어 WebSocket을 사용하기로 했는데 이또한 Security 이슈가 있어 결국 HTTPS로 설정하여 해결했으며, 과정이 꽤 험난했다. 

**Front-end with ReactJS**  

개인 취미로 몇가지 테스트 해본게 전부인, ReactJS를 건드린 것도 처음엔 일이었다. 하지만, 진행 하면서 느낀건 약간 레고 블럭 쌓는 느낌이라고 해야 할까? 크게 프로그래밍적인 어려움은 없고 그냥 좀 갑갑한 기분이 든 정도? ㅎㅎㅎ 동시에 프론트-엔트 개발자들이 이런 언어로 어떻게 개발을 진행할 수 있는지 약간 의문이 들었다. 어째든, Render() 함수에 모든걸 때려(?)넣고, 필요한 모듈은 임포트 했고, 중요한 ReactRTC 모듈은 수정이 불가피해서 임포트하지 않고 직접 수정을 했다. 아마 경험이 많으면 이부분도 방법이 있겠지만, 현재는 관심 없고, 앞으로도 없을듯 해서 패스! 

중요한 모듈은 Joystick GUI를 위한 [react-nipple](https://github.com/loopmode/react-nipple)가 다이고, 배경으로 스트리밍 이미지를 넣는건 미디엄의 한 [블로그](https://medium.com/@Rayyan995/how-to-make-a-background-video-component-in-react-8725e32da272)에서 도움 받았다. 관련된 간단한 예제는 [github.com/Rayyan995/background-video/tree/master/src/components/BackgroundVideo](https://github.com/Rayyan995/background-video/tree/master/src/components/BackgroundVideo)에 있다.  

**Difficulties**  

1. stun server: 두 peer통신을 위한 중계 역할을 하는 서버인데, 이걸 인터넷과 연결되지 않은 독립 네트워크에 어떻게 구현해야 하나 고민이 많았다. 결론은 쓸 필요가 없다. Negotiation 프로세스에서 ICE Candidate를 전달해 주니 자연스럽게 해결. ㅋ 
2. Security & HTTPS: Web 표준을 제정하는 사람들의 고민이 느껴지는 부분이다. 덕분에 나만 고생했지만! 어째든 WebRTC와 WebSocket을 정상적으로 사용하려면 무조건 HTTPS로 연결 되어야 한다. 이거 안해주면, 그냥 이상하게 안됨 ㅎㅎㅎㅎㅎ
3. Browswer: 이미 만들어진 브라우저를 욕해봐야 무얼하리오! ㅎㅎㅎ 아시다시피 MS에서 나온 브라우져들은 웹 표준을 제대로 따르지 않기 때문에 WebRTC가 정상 동작하지 않는다. 다른 브라우저들은 괜찮다. 한가지 알아 둘것은 iOS에서는 오직 **사파리**만 WebRTC를 지원한다. OS레벨에서 디바이스 장치에 연결하는 API를 제공하지 않아 설치한 다른 브라우저에서는 쓸 수 없다.  

Result  
======  

<iframe width="560" height="315" src="https://www.youtube.com/embed/Lm0EJ54ANJs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

이렇게 잘 동작하는게 결론이다. 더 프로젝트를 진행 했으면 좋으련만 Covid-19으로 모든 것이 물거품이 되었고, 나는 다른 세계로 옮겨져 버렸다. ㅎㅎㅎㅎㅎ
