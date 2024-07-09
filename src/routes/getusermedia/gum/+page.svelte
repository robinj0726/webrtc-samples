<script>
	let localVideo;
	let errorMsg;

	const constraints = {
		video: true,
		audio: false
	};

	function handleSuccess(stream) {
		const videoTracks = stream.getVideoTracks();
		console.log('Got stream with constraints:', constraints);
		console.log(`Using video device: ${videoTracks[0].label}`);
		localVideo.srcObject = stream;
	}

	function handleError(error) {
		if (error.name === 'OverconstrainedError') {
			errorMsg = `OverconstrainedError: The constraints could not be satisfied by the available devices. Constraints: ${JSON.stringify(constraints)}`;
		} else if (error.name === 'NotAllowedError') {
			errorMsg =
				'NotAllowedError: Permissions have not been granted to use your camera and ' +
				'microphone, you need to allow the page access to your devices in ' +
				'order for the demo to work.';
		}
		errorMsg = `getUserMedia error: ${error.name}`;
		if (typeof error !== 'undefined') {
			console.error(error);
		}
	}

	async function init() {
		try {
			const stream = await navigator.mediaDevices.getUserMedia(constraints);
			handleSuccess(stream);
		} catch (e) {
			handleError(e);
		}
	}
</script>

<div id="container">
	<h1>
		<a href="//webrtc.github.io/samples/" title="WebRTC samples homepage">WebRTC samples</a>
		<span>getUserMedia</span>
	</h1>

	<video id="gum-local" bind:this={localVideo} autoplay playsinline>
		<track kind="captions" />
	</video>
	<button id="showVideo" on:click={init}>Open camera</button>

	<div id="errorMsg">{errorMsg}</div>

	<p class="warning">
		<strong>Warning:</strong> if you're not using headphones, pressing play will cause feedback.
	</p>

	<p>Display the video stream from <code>getUserMedia()</code> in a video element.</p>

	<p>
		The <code>MediaStream</code> object <code>stream</code> passed to the
		<code>getUserMedia()</code> callback is in global scope, so you can inspect it from the console.
	</p>

	<a
		href="https://github.com/webrtc/samples/tree/gh-pages/src/content/getusermedia/gum"
		title="View source for this page on GitHub"
		id="viewSource">View source on GitHub</a
	>
</div>

<style>
	button {
		cursor: pointer;
	}
</style>
