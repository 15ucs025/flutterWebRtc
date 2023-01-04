# flutter_nativewebrtc

Project for implementing Audio/Video communication using flutter_webRTC plugin

## Getting Started

Add Flutter_webrtc plugin using: "flutter pub add flutter_webrtc"

Add Local Renderer to stream local/Remote video feed in the app: (instance of RTCVideoRenderer)
It needs to be initialized and disposed

Add getUserMedia method to get users mic or camera permission: navigator.mediaDevices.getUserMedia(mediaConstraints)
This will return a MediaStream which should be passed to _localVideoRenderer.srcObject

Flutter_webrtc plugin provides a RTCVideoView widget which takes renderer as argument to display the data "RTCVideoView(_localVideoRenderer)"

Now, create ui for displaying different feed for the remote and local ui

Create Method "_createPeerConnecion":
In order to create peer to peer connection, bypass firewall/NAT if required and exchange data server is required. WebRTC offer IEC framework to overcome these challenges (Requires server, stun is set as default).
We will use google free STUN server
Pass it SDP constraints and local media renderer

Use RTCPeerConnection object to add methods for createOffer, createAnswer, addCandidate and setRemoteDescription

 ======================== Step 1 ============================================
   RTCPeerConnection object is received from the create peer connection method
   Now, We use it to call the createOffer method
   This offer is send by Caller to the Remote user

 ======================== Step 2 ============================================
   Remote user takes offer from the caller
   it sets it as its RTCSessionDescritpion
   Only after this Remote user can answer the call

 ======================== Step 3 ============================================
   The sdp description which is created after the Remote user clicks the answer
   This description must be set as remoteDescription by the Caller

 ======================== Step 4 ============================================
   Candidate info generated after createaAnswer method of the Remote user should
   be Added as Candidate by the Caller to start the Connection

## Reference
- [Blog Tutorial] (https: www.100ms.live/blog/flutter-webrtc)
- [Video Reference] (https: youtu.be/IFPFNiFozdw)