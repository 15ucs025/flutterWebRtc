# flutter_nativewebrtc

Project for implementing Audio/Video communication using flutter_webRTC plugin

## Getting Started

Add Flutter_webrtc plugin using: "flutter pub add flutter_webrtc"

Add Local Renderer to stream local/Remote video feed in the app: (instance of RTCVideoRenderer)
It needs to be initialized and disposed

Add getUserMedia method to get users mic or camera permission: navigator.mediaDevices.getUserMedia(mediaConstraints)
This will return a MediaStream which should be passed to _localVideoRenderer.srcObject

Flutter_webrtc plugin provides a RTCVideoView widget which takes renderer as argument to display the data "RTCVideoView(_localVideoRenderer)"

## Reference
- [Blog Tutorial] (https://www.100ms.live/blog/flutter-webrtc)