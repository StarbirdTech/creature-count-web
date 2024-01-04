<script>
	import MuxVideo from '$lib/components/player.svelte';

	let playbackIds = [
		'Wp7cuhA81CTcxllwohIAHLB6qQcbzNawGOdaJtIXaWw',
		'rJZgeXCnAkwTqyVMlBCHcCyTcYflA3spUmxVvqsMaHI',
		'VFjyInnh1v02zM4VBTmzEOEWwgPM01jcRsCDwRFHV02ovc',
		'W2QWGlagbNH7u8uu96giBX00sISgHWNuqT02YmGeBmiw4'
	];
</script>

<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head>

<player>
	<MuxVideo />
</player>
