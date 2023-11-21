<script lang="ts">
	import { onMount } from 'svelte';
	import './navbar.scss';
	import Image from '../../components/image/image.svelte';
	import Interactable from '../../components/interactable.svelte';
	import { goto } from '$app/navigation';
	import Navlinks from './navlinks.svelte';
	import Hammenu from './hammenu.svelte';
	import type { NavItem } from '../types.js';
	import Text from '../../components/text/text.svelte';

	export let links: NavItem[];
	$: links;
</script>

<nav class="component__navbar">
	<div class="vspace vspace--small" />
	<div class="navbar__wrapper">
		<div class="navbar__logo">
			<Interactable
				onclick={() => {
					goto('/');
				}}
			>
				<Image src="" alt="logo" />
			</Interactable>
		</div>

		<Navlinks {links} />
		<Hammenu {links} />
	</div>
	<div class="vspace vspace--small" />
</nav>
