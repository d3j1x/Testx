<script lang="ts">
	import '../app.css';
	let { children } = $props();

	import testxLogo from '$lib/images/TestxLogo.webp';
	function checkScreenSize() {
		return window.innerWidth <= 768; // Adjust the value as needed
	}

	import {
		Navbar,
		NavBrand,
		NavHamburger,
		NavUl,
		NavLi,
		Dropdown,
		DropdownItem
	} from 'flowbite-svelte';
	import { ChevronDownOutline } from 'flowbite-svelte-icons';
	let menu = [{ name: 'ISTQB', href: '/ISTQB' }];
</script>

<Navbar let:hidden let:toggle>
	<NavBrand href="/">
		<img src={testxLogo} class="me-3 h-14 rounded-md sm:h-16" alt="Test X Logo" />
		<dl>
			<dt
				class="self-center text-xl font-extrabold whitespace-nowrap text-black md:text-2xl dark:text-white"
			>
				T E S T X
			</dt>
			<dd class="ml-8 font-mono text-sm text-green-600">Empowering Future Testers</dd>
		</dl>
	</NavBrand>
	<NavHamburger on:click={toggle} />
	<NavUl {hidden}>
		<NavLi
			class="mt-1 font-bold"
			on:click={() => {
				if (checkScreenSize()) toggle();
			}}
			href="/">Home</NavLi
		>

		<NavLi class="mt-1 cursor-pointer font-semibold">
			Certifications<ChevronDownOutline
				class="text-primary-800 inline  font-bold dark:text-white"
			/>
		</NavLi>
		<Dropdown class="z-20 w-44">
			<DropdownItem
				class=" font-extrabold"
				on:click={() => {
					if (checkScreenSize()) toggle();
				}}
				href="/certifications/ISTQB">ISTQB (CTFL)</DropdownItem
			>
		</Dropdown>

		<NavLi
			class="mt-1"
			on:click={() => {
				if (checkScreenSize()) toggle();
			}}
			href="/download"><span class="font-semibold">Download</span></NavLi
		>
		<NavLi
			on:click={() => {
				if (checkScreenSize()) toggle();
			}}
			href="https://github.com/SmrtMrktX/Testx"
			target="_blank"><i class="fa-brands fa-square-github text-2xl"></i></NavLi
		>
	</NavUl>
</Navbar>

{@render children()}

<footer class="">
	<h1 class="m-auto text-center text-slate-950">
		© 2025 <a class="font-semibold" href="https://www.smx.tn/" target="_blank">SMX™</a> All Rights
		Reserved.
	</h1>
</footer>
