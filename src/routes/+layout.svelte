<script lang="ts">
	import '../app.pcss';
	import Header from './Header.svelte';
	import './styles.css';
	import { ModeWatcher } from 'mode-watcher';
</script>

<ModeWatcher />

<div class="app">
	<Header></Header>

	<main>
		<slot />
	</main>

	<footer class="py-6 md:px-8 md:py-0">
		<div class="container flex flex-col items-center justify-between gap-4 md:h-24 md:flex-row">
			<div class="flex flex-col items-center gap-4 px-8 md:flex-row md:gap-2 md:px-0">
				<p class="text-center text-sm leading-loose text-muted-foreground md:text-left">
					creature-count github link and some other stuff
				</p>
			</div>
		</div>
	</footer>
</div>
