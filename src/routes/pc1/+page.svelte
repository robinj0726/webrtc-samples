<script>
	import { onDestroy } from 'svelte';
	import { Client } from '$lib/client';
	import './main.css';

	let client = new Client();
	client.onOpen = onOpen;
	client.onClose = onClose;

	client.onMessage = (message) => {
		console.log('Received message:', message);
	};

	onDestroy(() => {
		cleanUp();
	});

	function onOpen() {
		console.log('Connected to server');
	}

	function onClose() {
		console.log('Disconnected from server');
		cleanUp();
	}

	function start() {
		client.join('ws://localhost:3000/ws');
	}

	function call() {}

	function hangUp() {
		if (client) {
			client.leave();
		}
	}

	function cleanUp() {
		if (client) {
			client.leave();
			client = null;
		}
	}
</script>

<div id="container">
	<h1>
		<a href="//webrtc.github.io/samples/" title="WebRTC samples homepage">WebRTC samples</a>
		<span>Peer connection</span>
	</h1>

	<p>
		This sample shows how to setup a connection between two peers using
		<a href="https://developer.mozilla.org/en-US/docs/Web/API/RTCPeerConnection"
			>RTCPeerConnection</a
		>.
	</p>

	<video id="localVideo" playsinline autoplay muted>
		<track kind="captions" />
	</video>
	<video id="remoteVideo" playsinline autoplay>
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
