<script>
	let localVideo;
	let stream;

	const messagebox = {};
	const videoblock = {};
	const dimensions = {};

	let currentWidth = 0;
	let currentHeight = 0;

	const qvgaConstraints = {
		video: { width: { exact: 320 }, height: { exact: 240 } }
	};

	const vgaConstraints = {
		video: { width: { exact: 640 }, height: { exact: 480 } }
	};

	const hdConstraints = {
		video: { width: { exact: 1280 }, height: { exact: 720 } }
	};

	const fullHdConstraints = {
		video: { width: { exact: 1920 }, height: { exact: 1080 } }
	};

	const televisionFourKConstraints = {
		video: { width: { exact: 3840 }, height: { exact: 2160 } }
	};

	const cinemaFourKConstraints = {
		video: { width: { exact: 4096 }, height: { exact: 2160 } }
	};

	const eightKConstraints = {
		video: { width: { exact: 7680 }, height: { exact: 4320 } }
	};

	function gotStream(mediaStream) {
		stream = window.stream = mediaStream; // stream available to console
		localVideo.srcObject = mediaStream;
		messagebox.styleDisplay = 'none';
		videoblock.styleDisplay = 'block';
		const track = mediaStream.getVideoTracks()[0];
		const constraints = track.getConstraints();
		console.log('Result constraints: ' + JSON.stringify(constraints));
		// if (constraints && constraints.width && constraints.width.exact) {
		// 	widthInput.value = constraints.width.exact;
		// 	widthOutput.textContent = constraints.width.exact;
		// } else if (constraints && constraints.width && constraints.width.min) {
		// 	widthInput.value = constraints.width.min;
		// 	widthOutput.textContent = constraints.width.min;
		// }
	}

	function errorMessage(who, what) {
		const message = who + ': ' + what;
		messagebox.innerText = message;
		messagebox.styleDisplay = 'block';
		console.log(message);
	}

	function clearErrorMessage() {
		messagebox.styleDisplay = 'none';
	}

	function displayVideoDimensions(whereSeen) {
		console.log(localVideo);
		if (localVideo && localVideo.videoWidth) {
			const dimensionsText =
				'Actual localVideo dimensions: ' +
				localVideo.videoWidth +
				'x' +
				localVideo.videoHeight +
				'px.';
			if (currentWidth !== localVideo.videoWidth || currentHeight !== localVideo.videoHeight) {
				console.log(whereSeen + ': ' + dimensions.innerText);
				currentWidth = localVideo.videoWidth;
				currentHeight = localVideo.videoHeight;
			}
			dimensions.innerText = dimensionsText;
		} else {
			dimensions.innerText = 'Video not ready';
		}
	}
	function getMedia(constraints) {
		if (stream) {
			stream.getTracks().forEach((track) => {
				track.stop();
			});
		}
		dimensions.innerText = '';
		clearErrorMessage();
		videoblock.styleDisplay = 'none';
		navigator.mediaDevices
			.getUserMedia(constraints)
			.then(gotStream)
			.catch((e) => {
				console.log(e);
				errorMessage('getUserMedia', e.message, e.name);
			});
	}
</script>

<div id="container">
	<h1>
		<a href="//webrtc.github.io/samples/" title="WebRTC samples homepage">WebRTC samples</a>
		<span>getUserMedia: select resolution</span>
	</h1>
	<p></p>

	<p>
		This example uses <a
			href="https://w3c.github.io/mediacapture-main/getusermedia.html#media-track-constraints"
			title="W3C getusermedia specification - constraints section">constraints</a
		>.
	</p>

	<p>Click a button to call <code>getUserMedia()</code> with appropriate resolution.</p>

	<div id="buttons">
		<button id="qvga" on:click={() => getMedia(qvgaConstraints)}>QVGA</button>
		<button id="vga" on:click={() => getMedia(vgaConstraints)}>VGA</button>
		<button id="hd" on:click={() => getMedia(hdConstraints)}>HD</button>
		<button id="full-hd" on:click={() => getMedia(fullHdConstraints)}>Full HD</button>
		<button id="televisionFourK" on:click={() => getMedia(televisionFourKConstraints)}
			>Television 4K (3840x2160)</button
		>
		<button id="cinemaFourK" on:click={() => getMedia(cinemaFourKConstraints)}
			>Cinema 4K (4096x2160)</button
		>
		<button id="eightK" on:click={() => getMedia(eightKConstraints)}>8K</button>
	</div>

	<div id="videoblock" style="display: {videoblock.styleDisplay};">
		<p id="dimensions">{dimensions.innerText}</p>

		<video
			id="gum-res-local"
			bind:this={localVideo}
			playsinline
			autoplay
			on:loadedmetadata={() => displayVideoDimensions('loadedmetadata')}
			on:resize={() => displayVideoDimensions('resize')}
		>
			<track kind="captions" />
		</video>
		<div id="width">
			<label for="width-input">Width <span></span>px:</label>
			<input type="range" min="0" max="7680" value="0" />
		</div>
		<input id="sizelock" type="checkbox" />Lock video size<br />
		<input id="aspectlock" type="checkbox" />Lock aspect ratio<br />
	</div>
	<p id="errormessage" style="display: {messagebox.styleDisplay};">{messagebox.innerText}</p>

	<p>
		For more information, see <a
			href="http://www.html5rocks.com/en/tutorials/getusermedia/intro/"
			title="Media capture article by Eric Bidelman on HTML5 Rocks"
			>Capturing Audio &amp; Video in HTML5</a
		> on HTML5 Rocks.
	</p>

	<a
		href="https://github.com/webrtc/samples/tree/gh-pages/src/content/getusermedia/resolution"
		title="View source for this page on GitHub"
		id="viewSource">View source on GitHub</a
	>
</div>

<style>
	:global(html) {
		height: 100%;
	}

	button {
		margin: 0 10px 20px 0;
		min-width: 90px;
	}

	div#buttons {
		margin: 0 0 1em 0;
	}

	div#container {
		max-width: 100%;
	}

	#errormessage {
		display: none;
		font-size: 300%;
	}

	#videoblock {
		display: none;
	}

	p#dimensions {
		height: 1em;
		margin: 0 0 1.5em 0;
	}

	video {
		background: none;
		height: auto;
		width: auto;
	}
</style>
