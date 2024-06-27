<script>
	import './main.css';

	let localVideo;
	let remoteVideo;

	let localStream;
	let pc1;
	let pc2;
	const offerOptions = {
		offerToReceiveAudio: 1,
		offerToReceiveVideo: 1
	};

	async function start() {
		console.log('Requesting local stream');
		try {
			const stream = await navigator.mediaDevices.getUserMedia({ audio: true, video: true });
			console.log('Received local stream');
			localVideo.srcObject = stream;
			localStream = stream;
		} catch (e) {
			alert(`getUserMedia() error: ${e.name}`);
		}
	}

	function call() {}

	function hangUp() {}
</script>

<div id="container">
	<h1>
		<a href="/" title="WebRTC samples homepage">WebRTC samples</a>
		<span>Peer connection</span>
	</h1>

	<p>
		This sample shows how to setup a connection between two peers using
		<a href="https://developer.mozilla.org/en-US/docs/Web/API/RTCPeerConnection"
			>RTCPeerConnection</a
		>.
	</p>

	<video bind:this={localVideo} id="localVideo" playsinline autoplay muted>
		<track kind="captions" />
	</video>
	<video bind:this={remoteVideo} id="remoteVideo" playsinline autoplay>
		<track kind="captions" />
	</video>

	<div class="box">
		<button id="startButton" on:click={start}>Start</button>
		<button id="callButton" on:click={call}>Call</button>
		<button id="hangupButton" on:click={hangUp}>Hang Up</button>
	</div>

	<p>
		View the console to see logging. The <code>MediaStream</code> object <code>localStream</code>,
		and the <code>RTCPeerConnection</code>
		objects <code>pc1</code> and <code>pc2</code> are in global scope, so you can inspect them in the
		console as well.
	</p>

	<p>
		For more information about RTCPeerConnection, see <a
			href="http://www.html5rocks.com/en/tutorials/webrtc/basics/"
			title="HTML5 Rocks article about WebRTC by Sam Dutton">Getting Started With WebRTC</a
		>.
	</p>

	<a
		href="https://github.com/webrtc/samples/tree/gh-pages/src/content/peerconnection/pc1"
		title="View source for this page on GitHub"
		id="viewSource">View source on GitHub</a
	>
</div>
