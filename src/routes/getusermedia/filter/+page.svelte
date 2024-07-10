<script>
	import { onMount } from 'svelte';

	let localVideo;
	let canvas;
	let selectedFilter = 'none';
	let canvasClass = '';

	function handleSuccess(stream) {
		localVideo.srcObject = stream;
	}

	function handleError(error) {
		console.log('navigator.MediaDevices.getUserMedia error: ', error.message, error.name);
	}

	onMount(async () => {
		canvas.width = 480;
		canvas.height = 360;

		const constraints = {
			audio: false,
			video: true
		};

		try {
			const stream = await navigator.mediaDevices.getUserMedia(constraints);
			handleSuccess(stream);
		} catch (e) {
			handleError(e);
		}
	});
</script>

<div id="container">
	<h1>
		<a href="//webrtc.github.io/samples/" title="WebRTC samples homepage">WebRTC samples</a>
		<span>getUserMedia + CSS filters</span>
	</h1>

	<video bind:this={localVideo} class={selectedFilter} playsinline autoplay>
		<track kind="captions" />
	</video>

	<label for="filter">Filter: </label>
	<select id="filter" bind:value={selectedFilter}>
		<option value="none">None</option>
		<option value="blur">Blur</option>
		<option value="grayscale">Grayscale</option>
		<option value="invert">Invert</option>
		<option value="sepia">Sepia</option>
	</select>

	<button
		id="snapshot"
		on:click={() => {
			canvasClass = selectedFilter;
			const ctx = canvas.getContext('2d');
			ctx.filter = selectedFilter;
			ctx.drawImage(localVideo, 0, 0, canvas.width, canvas.height);
		}}>Take snapshot</button
	>

	<canvas bind:this={canvas} class={canvasClass}></canvas>

	<p>
		Draw a frame from the getUserMedia video stream onto the canvas element, then apply CSS filters.
	</p>

	<p>
		The variables <code>canvas</code>, <code>video</code> and <code>stream</code> are in global scope,
		so you can inspect them from the console.
	</p>

	<a
		href="https://github.com/webrtc/samples/tree/gh-pages/src/content/getusermedia/filter"
		title="View source for this page on GitHub"
		id="viewSource">View source on GitHub</a
	>
</div>

<style>
	.none {
		-webkit-filter: none;
		filter: none;
	}

	.blur {
		-webkit-filter: blur(3px);
		filter: blur(3px);
	}

	.grayscale {
		-webkit-filter: grayscale(1);
		filter: grayscale(1);
	}

	.invert {
		-webkit-filter: invert(1);
		filter: invert(1);
	}

	.sepia {
		-webkit-filter: sepia(1);
		filter: sepia(1);
	}

	button#snapshot {
		margin: 0 10px 25px 0;
		width: 110px;
	}

	video {
		object-fit: cover;
	}
</style>
