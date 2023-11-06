<script lang="ts">
	import Navbar from '../layouts/navbar/navbar.svelte';
    import "../styles/global.scss"
</script>

<Navbar
	links={[
		{ displayName: 'About Us', navTo: '#about' },
		{ displayName: 'Services', navTo: '#services' },
		{ displayName: 'Our Approach', navTo: '#approach' },
		{ displayName: 'Careers', navTo: '#careers' }
	]}
/>
