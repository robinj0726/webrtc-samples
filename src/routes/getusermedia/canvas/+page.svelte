<script>
	import { onMount } from 'svelte';

	let localVideo;
	let canvas;

	const constraints = {
		audio: false,
		video: true
	};

	onMount(async () => {
		const stream = await navigator.mediaDevices.getUserMedia(constraints);
		localVideo.srcObject = stream;

		canvas.width = 480;
		canvas.height = 360;
	});
</script>

<div id="container">
	<h1>
		<a href="//webrtc.github.io/samples/" title="WebRTC samples homepage">WebRTC samples</a>
		<span>getUserMedia ⇒ canvas</span>
	</h1>

	<video bind:this={localVideo} playsinline autoplay>
		<track kind="captions" />
	</video>
	<button
		on:click={() => {
			canvas.width = localVideo.videoWidth;
			canvas.height = localVideo.videoHeight;
			canvas.getContext('2d').drawImage(localVideo, 0, 0, canvas.width, canvas.height);
		}}>Take snapshot</button
	>
	<canvas bind:this={canvas}></canvas>

	<p>
		Draw a frame from the video onto the canvas element using the <code>drawImage()</code> method.
	</p>

	<p>
		The variables <code>canvas</code>, <code>video</code> and <code>stream</code> are in global scope,
		so you can inspect them from the console.
	</p>

	<a
		href="https://github.com/webrtc/samples/tree/gh-pages/src/content/getusermedia/canvas"
		title="View source for this page on GitHub"
		id="viewSource">View source on GitHub</a
	>
</div>
