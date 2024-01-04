<script>
	import { MuxPlayer } from '@mux/mux-player';
	import { Player, Video } from '@vime/svelte';

	// You can pass the Mux video URL and other properties as props to this component
	export let muxVideoUrl =
		'https://stream.mux.com/WyT15sK027OmcMuCFI00W3NSuVYOO015Sl1n7OlriMtaIM.m3u8';
</script>

<Player>
	<MuxPlayer
		data={{
			playbackId: muxVideoUrl
		}}
	/>
</Player>

<style>
	/* Add any styling here */
</style>
