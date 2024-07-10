<div id="container">
	<h1>WebRTC samples</h1>

	<section>
		<p>
			This is a collection of small samples demonstrating various parts of the <a
				href="https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API">WebRTC APIs</a
			>. The code for all samples are available in the
			<a href="https://github.com/webrtc/samples">GitHub repository</a>.
		</p>

		<p>
			Most of the samples use <a href="https://github.com/webrtc/adapter">adapter.js</a>, a shim to
			insulate apps from spec changes and prefix differences.
		</p>

		<p>
			<a
				href="https://webrtc.org/getting-started/testing"
				title="Command-line flags for WebRTC testing">https://webrtc.org/getting-started/testing</a
			>
			lists command line flags useful for development and testing with Chrome.
		</p>

		<p>
			Patches and issues welcome! See <a
				href="https://github.com/webrtc/samples/blob/gh-pages/CONTRIBUTING.md">CONTRIBUTING.md</a
			>
			for instructions.
		</p>

		<p class="warning">
			<strong>Warning:</strong> It is highly recommended to use headphones when testing these samples,
			as it will otherwise risk loud audio feedback on your system.
		</p>
	</section>

	<section>
		<h2 id="getusermedia">
			<a href="https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia"
				>getUserMedia():</a
			>
		</h2>
		<p class="description">Access media devices</p>
		<ul>
			<li><a href="/getusermedia/gum/">Basic getUserMedia demo</a></li>

			<li><a href="/getusermedia/canvas/">Use getUserMedia with canvas</a></li>

			<li>
				<a href="/getusermedia/filter/">Use getUserMedia with canvas and CSS filters</a>
			</li>

			<li><a href="/getusermedia/resolution/">Choose camera resolution</a></li>

			<li>
				<a href="/getusermedia/audio/">Audio-only getUserMedia() output to local audio element</a>
			</li>

			<li>
				<a href="/getusermedia/volume/">Audio-only getUserMedia() displaying volume</a>
			</li>

			<li><a href="/getusermedia/record/">Record stream</a></li>

			<li>
				<a href="/getusermedia/getdisplaymedia/">Screensharing with getDisplayMedia</a>
			</li>

			<li>
				<a href="/getusermedia/pan-tilt-zoom/">Control camera pan, tilt, and zoom</a>
			</li>

			<li><a href="/getusermedia/exposure/">Control exposure</a></li>
		</ul>
		<h2 id="devices">Devices:</h2>
		<p class="description">Query media devices</p>
		<ul>
			<li><a href="src/content/devices/input-output/">Choose camera, microphone and speaker</a></li>

			<li><a href="src/content/devices/multi/">Choose media source and audio output</a></li>
		</ul>

		<h2 id="capture">Stream capture:</h2>
		<p class="description">Stream from canvas or video elements</p>
		<ul>
			<li>
				<a href="src/content/capture/video-video/">Stream from a video element to a video element</a
				>
			</li>

			<li>
				<a href="src/content/capture/video-pc/">Stream from a video element to a peer connection</a>
			</li>

			<li>
				<a href="src/content/capture/canvas-video/"
					>Stream from a canvas element to a video element</a
				>
			</li>

			<li>
				<a href="src/content/capture/canvas-pc/"
					>Stream from a canvas element to a peer connection</a
				>
			</li>

			<li>
				<a href="src/content/capture/canvas-record/">Record a stream from a canvas element</a>
			</li>

			<li>
				<a href="src/content/capture/video-contenthint/"
					>Guiding video encoding with content hints</a
				>
			</li>
		</ul>

		<h2 id="peerconnection">
			<a href="https://developer.mozilla.org/en-US/docs/Web/API/RTCPeerConnection"
				>RTCPeerConnection:</a
			>
		</h2>
		<p class="description">Controlling peer connectivity</p>
		<ul>
			<li>
				<a href="/peerconnection/pc1/">Basic peer connection demo in a single tab</a>
			</li>

			<li>
				<a href="/peerconnection/channel/">Basic peer connection demo between two tabs</a>
			</li>

			<li>
				<a href="/peerconnection/perfect-negotiation/">Peer connection using Perfect Negotiation</a>
			</li>

			<li><a href="/peerconnection/audio/">Audio-only peer connection demo</a></li>

			<li><a href="/peerconnection/bandwidth/">Change bandwidth on the fly</a></li>

			<li><a href="/peerconnection/change-codecs/">Change codecs before the call</a></li>

			<li><a href="/peerconnection/upgrade/">Upgrade a call and turn video on</a></li>

			<li><a href="/peerconnection/multiple/">Multiple peer connections at once</a></li>

			<li>
				<a href="/peerconnection/multiple-relay/">Forward the output of one PC into another</a>
			</li>

			<li><a href="/peerconnection/munge-sdp/">Munge SDP parameters</a></li>

			<li>
				<a href="/peerconnection/pr-answer/">Use pranswer when setting up a peer connection</a>
			</li>

			<li><a href="/peerconnection/constraints/">Constraints and stats</a></li>

			<li>
				<a href="/peerconnection/per-frame-callback/"
					>RTCPeerConnection and requestVideoFrameCallback()</a
				>
			</li>

			<li>
				<a href="/peerconnection/create-offer/">Display createOffer output for various scenarios</a>
			</li>

			<li><a href="/peerconnection/dtmf/">Use RTCDTMFSender</a></li>

			<li><a href="/peerconnection/states/">Display peer connection states</a></li>

			<li>
				<a href="/peerconnection/trickle-ice/">ICE candidate gathering from STUN/TURN servers</a>
			</li>

			<li><a href="/peerconnection/restart-ice/">Do an ICE restart</a></li>

			<li>
				<a href="/peerconnection/webaudio-input/">Web Audio output as input to peer connection</a>
			</li>

			<li>
				<a href="/peerconnection/webaudio-output/">Peer connection as input to Web Audio</a>
			</li>
			<li>
				<a href="/peerconnection/negotiate-timing/">Measure how long renegotiation takes</a>
			</li>
			<li>
				<a href="/extensions/svc/"
					>Choose scalablilityMode before call - Scalable Video Coding (SVC) Extension
				</a>
			</li>
		</ul>
		<h2 id="datachannel">
			<a href="https://developer.mozilla.org/en-US/docs/Web/API/RTCDataChannel">RTCDataChannel:</a>
		</h2>
		<p class="description">Send arbitrary data over peer connections</p>
		<ul>
			<li><a href="src/content/datachannel/basic/">Transmit text</a></li>

			<li><a href="src/content/datachannel/filetransfer/">Transfer a file</a></li>

			<li><a href="src/content/datachannel/datatransfer/">Transfer data</a></li>

			<li>
				<a href="src/content/datachannel/channel/">Basic datachannel demo between two tabs</a>
			</li>

			<li><a href="src/content/datachannel/messaging/">Messaging</a></li>
		</ul>

		<h2 id="videoChat">Video chat:</h2>
		<p class="description">Full featured WebRTC application</p>
		<ul>
			<li>
				<a href="https://github.com/webrtc/apprtc/">AppRTC video chat client</a> that you can run out
				of a Docker image
			</li>
		</ul>

		<h2 id="capture">Insertable Streams:</h2>
		<p class="description">API for processing media</p>
		<ul>
			<li>
				<a href="src/content/insertable-streams/endtoend-encryption"
					>End to end encryption using WebRTC Insertable Streams</a
				>
			</li>
			(Experimental)
			<li>
				<a href="src/content/insertable-streams/video-analyzer"
					>Video analyzer using WebRTC Insertable Streams</a
				>
			</li>
			(Experimental)
			<li>
				<a href="src/content/insertable-streams/video-processing"
					>Video processing using MediaStream Insertable Streams</a
				>
			</li>
			(Experimental)
			<li>
				<a href="src/content/insertable-streams/audio-processing"
					>Audio processing using MediaStream Insertable Streams</a
				>
			</li>
			(Experimental)
			<li>
				<a href="src/content/insertable-streams/video-crop"
					>Video cropping using MediaStream Insertable Streams in a Worker</a
				>
			</li>
			(Experimental)
			<li>
				<a href="src/content/insertable-streams/webgpu"
					>Integrations with WebGPU for custom video rendering:</a
				>
			</li>
			(Experimental)
		</ul>
	</section>
</div>
