<script lang="ts">
	import Interactable from '../../components/interactable.svelte';
	import { goto } from '$app/navigation';
	import Text from '../../components/text/text.svelte';
	import Desktoponly from '../../components/conditionalview/desktoponly.svelte';
	import { page } from '$app/stores';
	import Button from '../../components/button/button.svelte';
	import type { NavItem } from '../types.js';
	export let links: NavItem[];

</script>

<Desktoponly>
	<div class="navbar__navlinks">
		{#if links}
			{#each links as link}
				<div class="navlink {$page.url.pathname == link.navTo ? 'current' : ''}">
					<Interactable
						onclick={() => {
							goto(link.navTo);
						}}
					>
						<Text text={link.displayName} style="s-bold" />
					</Interactable>
					<div class="line" />
				</div>
			{/each}
		{/if}
		<Interactable
			onclick={() => {
				goto('#contact');
			}}
		>
			<Button text="Contact" style="s-medium" filled />
		</Interactable>
	</div>
</Desktoponly>
