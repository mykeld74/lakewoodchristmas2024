<script>
	import { scss } from 'svelte-preprocess';
</script>

<div class="wrapper">
	<div class="snow layer1 a" />
	<div class="snow layer1" />
	<div class="snow layer2 a" />
	<div class="snow layer2" />
	<div class="snow layer3 a" />
	<div class="snow layer3" />
</div>

<style lang="scss">
	.wrapper {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		background: radial-gradient(farthest-corner at 30vw 20vh, #383838 1%, #101010 100%);
		z-index: -1;
	}
	$s1: '';
	$s2: '';
	$s3: '';
	@for $i from 1 through 50 {
		$s1: $s1 +
			random(1000) *
			0.1vw +
			' ' +
			random(1000) *
			0.1vh +
			' ' +
			0 +
			' ' +
			random(50) *
			-0.01rem +
			#fff;
		$s2: $s2 +
			random(1000) *
			0.1vw +
			' ' +
			random(1000) *
			0.1vh +
			' ' +
			0 +
			' ' +
			random(50) *
			-0.01rem +
			#fff;
		$s3: $s3 +
			random(1000) *
			0.1vw +
			' ' +
			random(1000) *
			0.1vh +
			' ' +
			0 +
			' ' +
			random(50) *
			-0.01rem +
			#fff;
		@if $i < 50 {
			$s1: $s1 + ',';
			$s2: $s2 + ',';
			$s3: $s3 + ',';
		}
	}
	.snow {
		border-radius: 50%;
		opacity: 0.8;
		position: absolute;
		top: -100vh;
		animation-name: fall;
		animation-timing-function: linear;
		animation-iteration-count: infinite;
	}
	.layer1 {
		width: 1rem;
		height: 1rem;
		filter: blur(1px);
		box-shadow: #{$s1};
		animation-duration: 10s;
	}
	.layer1.a {
		animation-delay: -5s;
	}
	.layer2 {
		width: 0.6rem;
		height: 0.6rem;
		filter: blur(2px);
		box-shadow: #{$s2};
		animation-duration: 16s;
	}
	.layer2.a {
		animation-delay: -8s;
	}
	.layer3 {
		width: 0.8rem;
		height: 0.8rem;
		filter: blur(6px);
		box-shadow: #{$s3};
		animation-duration: 12s;
	}
	.layer3.a {
		animation-delay: -3s;
	}
	@keyframes fall {
		100% {
			transform: translateY(200vh);
		}
	}
</style>
