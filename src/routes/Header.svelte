<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import * as DropdownMenu from '$lib/components/ui/dropdown-menu';
	import { Sun, Moon } from 'lucide-svelte';

	import { setMode, resetMode } from 'mode-watcher';
</script>

<header
	class="supports-[backdrop-filter]:bg-background/60 sticky top-0 z-50 w-full border-b bg-background/95 shadow-sm backdrop-blur"
>
	<div class="container flex h-14 items-center">
		<div class="mr-4 hidden md:flex">
			<a href="." class="mr-6 flex items-center space-x-2"
				><span class="hidden font-bold sm:inline-block text-[15px] lg:text-base"
					>creature-count</span
				>
			</a>
			<nav class="flex items-center space-x-6 text-sm font-medium">
				<a href="." class="transition-colors hover:text-foreground/80 text-foreground/60"
					>placeholder</a
				>
			</nav>
		</div>
		<div class="flex flex-1 items-center justify-between space-x-2 sm:space-x-4 md:justify-end">
			<DropdownMenu.Root>
				<DropdownMenu.Trigger asChild let:builder>
					<Button builders={[builder]} variant="outline" size="icon">
						<Sun
							class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
						/>
						<Moon
							class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
						/>
						<span class="sr-only">Toggle theme</span>
					</Button>
				</DropdownMenu.Trigger>
				<DropdownMenu.Content align="end">
					<DropdownMenu.Item on:click={() => setMode('light')}>Light</DropdownMenu.Item>
					<DropdownMenu.Item on:click={() => setMode('dark')}>Dark</DropdownMenu.Item>
					<DropdownMenu.Item on:click={() => resetMode()}>System</DropdownMenu.Item>
				</DropdownMenu.Content>
			</DropdownMenu.Root>
		</div>
	</div>
</header>
