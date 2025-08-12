<!-- <h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p> -->

<script lang="ts">
	import { twMerge } from 'tailwind-merge';
	import Button from '$lib/components/button.svelte';
	import Tooltip from '$lib/components/tooltip.svelte';

	let sidebarOpen = $state(true);

	const toggleSidebar = () => (sidebarOpen = !sidebarOpen);
</script>

<div class="roboto-flex flex h-full w-full overflow-hidden text-neutral-400">
	<header class="fixed z-1 my-4 flex h-12 w-full items-center px-2">
		<section class="relative flex size-10 items-center">
			<Tooltip description={sidebarOpen ? 'Cerrar' : 'Abrir'} position="right">
				<Button
					type="button"
					id="sidebarToggle"
					onclick={toggleSidebar}
					class={twMerge('size-10', `${sidebarOpen && '!w-full'}`)}
					icon={{
						name: sidebarOpen ? 'keyboard_tab_rtl' : 'keyboard_tab',
						weight: 400,
						size: 40
					}}
				>
					<span class="sr-only">{sidebarOpen ? 'Cerrar' : 'Abrir'}</span>
				</Button>
			</Tooltip>
		</section>
	</header>
	<aside
		id="sidebar"
		class={twMerge(
			'invisible grid h-dvh transform grid-rows-[auto_1fr_min-content] bg-black px-2 pt-20 transition-[width] duration-300 ease-in-out md:visible md:relative md:min-w-14',
			sidebarOpen ? 'w-80' : 'w-14'
		)}
	>
		<!-- Contenido del Sidebar -->
		<section class="mx-auto my-4 w-full">
			<Tooltip description="Nuevo" position="right">
				<Button
					id="newChatButton"
					icon={{ name: 'add', weight: 400, size: 40 }}
					class={twMerge('size-10', `${sidebarOpen && '!w-full'}`)}
				>
					<span
						id="support"
						class={twMerge(
							'relative left-10 w-full text-start text-sm text-nowrap',
							sidebarOpen
								? 'opacity-100 delay-100 duration-200'
								: 'invisible opacity-0 delay-50 duration-100'
						)}
					>
						Nuevo chat
					</span>
				</Button>
			</Tooltip>
		</section>
		<section
			class="mx-auto my-4 grid w-full grid-cols-[minmax(0,1fr)] grid-rows-[auto,1fr] overflow-y-auto"
		>
			{#each Array.from({ length: 26 }, (_, i) => i) as n (n)}
				<Button id={`${n}`} class={twMerge('size-12 !ps-4 !pe-10', `${sidebarOpen && '!w-full'}`)}>
					<span
						id="support"
						class={twMerge(
							'w-full overflow-hidden text-start text-sm text-ellipsis whitespace-nowrap',
							sidebarOpen
								? 'opacity-100 delay-100 duration-200'
								: 'invisible opacity-0 delay-50 duration-100'
						)}
					>
						Chat equis con mensaje largo pero muy largo
					</span>
				</Button>
			{/each}
			<!-- <div class="my-3 h-full w-full overflow-x-hidden overflow-y-auto">
				<ul class="flex flex-col items-center justify-start">
					{#each chats as { id, title }}
						<li
							class={`w-full relative flex items-center rounded-full my-2 hover:bg-gray-300 dark:hover:bg-gray-800 ${!sidebarOpen ? 'opacity-0 invisible delay-100 duration-300' : 'opacity-100 delay-100 duration-500 ps-3 mx-3'}`}
						>
							<button
								type="button"
								id={`chat-${id}`}
								class="w-full py-2 pe-8 ms-8 text-start text-ellipsis overflow-hidden whitespace-nowrap"
								{title}
							>
								<i
									class="fa-solid fa-message absolute left-4 bottom-[20%] -translate-y-1/4"
								></i>
								{title}
							</button>
							<button
								type="button"
								class="flex justify-center items-center p-3 absolute right-0 z-20 hover:bg-slate-500 hover:rounded-full dark:hover:bg-gray-700"
								title="Más"
							>
								<i class="fa-solid fa-ellipsis-vertical"></i>
							</button>
						</li>
					{/each}
				</ul>
			</div> -->
		</section>
		<section class="mx-auto my-4 w-full">
			<Tooltip description="Configuraciones" position="right">
				<Button
					id="configurationsButton"
					icon={{ name: 'settings', weight: 400, size: 40 }}
					class={twMerge('size-10', `${sidebarOpen && '!w-full'}`)}
				>
					<span
						id="support"
						class={twMerge(
							'relative left-10 w-full text-start text-sm text-nowrap',
							sidebarOpen
								? 'opacity-100 delay-100 duration-200'
								: 'invisible opacity-0 delay-50 duration-100'
						)}
					>
						Configuraciones
					</span>
				</Button>
			</Tooltip>
		</section>
	</aside>
	<!-- xddd -->
	<!-- Contenedor principal -->
	<main class="relative flex h-dvh w-full flex-col justify-between bg-neutral-800">
		<header class="flex h-32 w-full items-center bg-gray-700 px-2 pb-4">header</header>
		<section
			class="flex size-auto flex-col items-center space-y-6 overflow-x-hidden overflow-y-auto py-6"
		>
			<article class="w-2/3 rounded-xl bg-neutral-700 p-6">
				Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam
				at minus cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem
				impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor sit amet consectetur,
				adipisicing elit. Doloribus consectetur debitis nam at minus cupiditate hic illum eligendi
				obcaecati culpa libero, quas, repellat blanditiis rem impedit reiciendis. Cupiditate,
				mollitia dolorum! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus
				consectetur debitis nam at minus cupiditate hic illum eligendi obcaecati culpa libero, quas,
				repellat blanditiis rem impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor
				sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam at minus
				cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem impedit
				reiciendis. Cupiditate, mollitia dolorum!
			</article>
			<article class="w-2/3 rounded-xl bg-neutral-700 p-6">
				Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam
				at minus cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem
				impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor sit amet consectetur,
				adipisicing elit. Doloribus consectetur debitis nam at minus cupiditate hic illum eligendi
				obcaecati culpa libero, quas, repellat blanditiis rem impedit reiciendis. Cupiditate,
				mollitia dolorum! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus
				consectetur debitis nam at minus cupiditate hic illum eligendi obcaecati culpa libero, quas,
				repellat blanditiis rem impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor
				sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam at minus
				cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem impedit
				reiciendis. Cupiditate, mollitia dolorum!
			</article>
			<article class="w-2/3 rounded-xl bg-neutral-700 p-6">
				Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam
				at minus cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem
				impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor sit amet consectetur,
				adipisicing elit. Doloribus consectetur debitis nam at minus cupiditate hic illum eligendi
				obcaecati culpa libero, quas, repellat blanditiis rem impedit reiciendis. Cupiditate,
				mollitia dolorum! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus
				consectetur debitis nam at minus cupiditate hic illum eligendi obcaecati culpa libero, quas,
				repellat blanditiis rem impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor
				sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam at minus
				cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem impedit
				reiciendis. Cupiditate, mollitia dolorum!
			</article>
			<article class="w-2/3 rounded-xl bg-neutral-700 p-6">
				Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam
				at minus cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem
				impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor sit amet consectetur,
				adipisicing elit. Doloribus consectetur debitis nam at minus cupiditate hic illum eligendi
				obcaecati culpa libero, quas, repellat blanditiis rem impedit reiciendis. Cupiditate,
				mollitia dolorum! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus
				consectetur debitis nam at minus cupiditate hic illum eligendi obcaecati culpa libero, quas,
				repellat blanditiis rem impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor
				sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam at minus
				cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem impedit
				reiciendis. Cupiditate, mollitia dolorum!
			</article>
			<article class="w-2/3 rounded-xl bg-neutral-700 p-6">
				Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam
				at minus cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem
				impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor sit amet consectetur,
				adipisicing elit. Doloribus consectetur debitis nam at minus cupiditate hic illum eligendi
				obcaecati culpa libero, quas, repellat blanditiis rem impedit reiciendis. Cupiditate,
				mollitia dolorum! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus
				consectetur debitis nam at minus cupiditate hic illum eligendi obcaecati culpa libero, quas,
				repellat blanditiis rem impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor
				sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam at minus
				cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem impedit
				reiciendis. Cupiditate, mollitia dolorum!
			</article>
			<article class="w-2/3 rounded-xl bg-neutral-700 p-6">
				Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam
				at minus cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem
				impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor sit amet consectetur,
				adipisicing elit. Doloribus consectetur debitis nam at minus cupiditate hic illum eligendi
				obcaecati culpa libero, quas, repellat blanditiis rem impedit reiciendis. Cupiditate,
				mollitia dolorum! Lorem ipsum dolor sit amet consectetur, adipisicing elit. Doloribus
				consectetur debitis nam at minus cupiditate hic illum eligendi obcaecati culpa libero, quas,
				repellat blanditiis rem impedit reiciendis. Cupiditate, mollitia dolorum! Lorem ipsum dolor
				sit amet consectetur, adipisicing elit. Doloribus consectetur debitis nam at minus
				cupiditate hic illum eligendi obcaecati culpa libero, quas, repellat blanditiis rem impedit
				reiciendis. Cupiditate, mollitia dolorum!
			</article>
		</section>
		<footer class="flex max-h-32 min-h-16 w-full items-center bg-gray-700 px-2 pb-4">footer</footer>
		<!-- <section class="relative isolate h-screen overflow-hidden bg-black p-5 text-white">

			<div class="noise pointer-events-none absolute inset-0 z-1"></div>


			<div
				class="absolute inset-0 z-0 bg-radial-[at_50%_250%] from-purple-700/30 via-purple-900/60 to-black"
			></div>

			<span class="text-white">XDDDD</span>
		</section> -->
	</main>
</div>

<style global>
	.noise {
		background:
			repeating-radial-gradient(
				circle at center,
				rgba(255, 255, 255, 0.02) 0,
				rgba(255, 255, 255, 0.02) 1px,
				transparent 1px,
				transparent 2px
			),
			repeating-radial-gradient(
				circle at center,
				rgba(255, 255, 255, 0.01) 0,
				rgba(255, 255, 255, 0.01) 2px,
				transparent 2px,
				transparent 4px
			);
		opacity: 0.2;
		mix-blend-mode: soft-light;
		filter: blur(0.5px) contrast(130%);
	}
	.noise {
		animation: grainShift 1s infinite alternate;
	}

	@keyframes grainShift {
		0% {
			transform: translate(0, 0);
		}
		100% {
			transform: translate(-1px, 1px);
		}
	}
</style>
