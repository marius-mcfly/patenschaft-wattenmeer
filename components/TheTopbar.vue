<template>
	<nav
		class="fixed z-[1000] w-full flex items-center justify-center py-4 px-6 transition-all duration-500 ease-in-out bg-white shadow-2xl desktop:h-32 rounded-br-3xl rounded-bl-3xl desktop:rounded-br-[60px] desktop:rounded-bl-[60px] desktop:px-10"
		:class="isOpen ? 'h-screen py-20' : 'h-20'"
	>
		<div :class="['desktop:grid desktop:grid-cols-[max-content,1fr,max-content] desktop:items-center desktop:justify-center w-full desktop:max-w-7xl', {'h-auto': isOpen}, {'h-20': !isOpen}]">
			<NuxtLink to="/">
				<img class="top-4 z-50 left-8 fixed w-full max-w-[104px] desktop:ml-8 desktop:static desktop:max-w-[160px]" src="/svg/wattenmeer-logo.svg" alt="">
			</NuxtLink>
			<PageNavigation class="hidden desktop:grid justify-self-end items-center mt-[3px]" :navigation-items="navigationItems" />
			<NuxtLink to="/kontakt">
				<AppButton class="hidden desktop:block desktop:py-3" primary-button>
					Kontakt →
				</AppButton>
			</NuxtLink>
			<div
				class="flex items-center w-full justify-end fixed right-8 top-8 desktop:hidden z-0"
			>
				<IconMenu
					class=""
					:class="isOpen ? 'active' : ''"
					@click="toggleNav"
				/>
			</div>
			<PageNavigation
				class="flex-col items-center transition-all duration-[375ms] ease-in-out desktop:hidden"
				:class="isOpen ? 'opacity-100' : 'opacity-0 transform translate-y-[-480px]'"
				:navigation-items="navigationItems"
			/>
		</div>
	</nav>
</template>

<script>
export default {
	data () {
		return {
			isOpen: false,
			navigationItems: [
				{
					name: 'Nationalpark',
					routePath: '/'
				},

				{
					name: 'Projekte',
					routePath: '/projekte'
				},

				{
					name: 'Patenschaft',
					routePath: '/patenschaft'

				},

				{
					name: 'Mitmachen',
					routePath: '/mitmachen'
				},

				{
					name: 'Besuchen',
					routePath: '/'

				},

				{
					name: 'Presse',
					routePath: '/presse'
				},

				{
					name: 'Kontakt',
					routePath: '/kontakt'
				}
			]
		}
	},

	mounted () {
		this.$nextTick(() => {
			document.body.classList.remove('overflow-hidden')
		})
	},

	methods: {
		toggleNav () {
			this.isOpen = !this.isOpen
			if (this.isOpen) {
				document.body.classList.add('overflow-hidden')
			} else {
				document.body.className = document.body.className.replace('overflow-hidden', '')
			}
		}

	}

}
</script>

<style>

</style>
