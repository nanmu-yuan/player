<template>
	<div>
		<div class="bg">
			<div class="keys">
				<div data-key="A" class="key">
					<kbd>A</kbd>
					<span class="sound">clap</span>
				</div>
				<div data-key="S" class="key">
					<kbd>S</kbd>
					<span class="sound">hi-hats</span>
				</div>
				<div data-key="D" class="key">
					<kbd>D</kbd>
					<span class="sound">kick</span>
				</div>
				<div data-key="F" class="key">
					<kbd>F</kbd>
					<span class="sound">open-hats</span>
				</div>
				<div data-key="G" class="key">
					<kbd>G</kbd>
					<span class="sound">boom</span>
				</div>
				<div data-key="H" class="key">
					<kbd>H</kbd>
					<span class="sound">ride</span>
				</div>
				<div data-key="J" class="key">
					<kbd>J</kbd>
					<span class="sound">snare</span>
				</div>
				<div data-key="K" class="key">
					<kbd>K</kbd>
					<span class="sound">tom</span>
				</div>
				<div data-key="L" class="key">
					<kbd>L</kbd>
					<span class="sound">tink</span>
				</div>
			</div>
		</div>
		<audio data-key="A" src="sounds/clap.wav"></audio>
		<audio data-key="S" src="sounds/hihat.wav"></audio>
		<audio data-key="D" src="sounds/kick.wav"></audio>
		<audio data-key="F" src="sounds/openhat.wav"></audio>
		<audio data-key="G" src="sounds/boom.wav"></audio>
		<audio data-key="H" src="sounds/ride.wav"></audio>
		<audio data-key="J" src="sounds/snare.wav"></audio>
		<audio data-key="K" src="sounds/tom.wav"></audio>
		<audio data-key="L" src="sounds/tink.wav"></audio>
	</div>
</template>
<script>
export default {
	name: 'demo',
	data() {
		return {
			theme: '',
		};
	},
	methods: {
		change(e) {
			function playSound(e) {
				const ele = e.target.innerText;
				console.log(e.target.innerText)
				const audio = document.querySelector(
					`audio[data-key="${ele}"]`
				);
				const key = document.querySelector(
					`.key[data-key="${e.ele}"]`
				);
				if (!audio) return false;

				audio.currentTime = 0;
				audio.play();

			//	key.classList.add('playing');
			}

			const keys = document.querySelectorAll('.key');

			keys.forEach((key) => {
				return key.addEventListener('transitionend', removeTransition);
			});

			function removeTransition(e) {
				if (e.propertyName !== 'transform') return false;

				this.classList.remove('playing');
			}

			window.addEventListener('click', playSound);
		},
	},
	mounted() {
		this.change();
	},
};
</script>
</script>