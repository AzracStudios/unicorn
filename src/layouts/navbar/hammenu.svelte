<script lang="ts">
	import { goto } from '$app/navigation';
	import Button from '../../components/button/button.svelte';
	import Mobileonly from '../../components/conditionalview/mobileonly.svelte';
	import Interactable from '../../components/interactable.svelte';
	import Text from '../../components/text/text.svelte';
	import type { NavItem } from '../types.js';
	
	let open = false;
	$: open;

	export let links: NavItem[];

	const handleClick = async () => {
		open = !open;
		document.body.style.overflow = open ? 'hidden' : 'visible';
	};
</script>

<Mobileonly>
	<div class="navbar__hammenu" role="navigation">
		<Interactable onclick={handleClick}>
			<div class="hammenu__ham {open ? 'hammenu__ham--open' : ''}">
				<div class="ham__l1" />
				<div class="ham__l2" />
				<div class="ham__l3" />
			</div>
		</Interactable>

		<div class="hammenu__navlinks {open ? 'hammenu__navlinks--open' : ''}">
			{#if links}
				{#each links as link}
					<Interactable
						onclick={() => {
							handleClick();
							goto(link.navTo);
						}}
					>
						<Text text={link.displayName} style="m-bold" noselect />
					</Interactable>
				{/each}
			{/if}
			<Interactable
				onclick={() => {
					handleClick();

					goto('#contact');
				}}
			>
				<Button text="Contact" style="s-medium" filled />
			</Interactable>
		</div>
	</div>
</Mobileonly>
