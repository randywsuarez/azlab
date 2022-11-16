<template>
	<q-layout view="rHh Lpr lFf">
		<q-header class="row justify-between" bordered>
			<q-toolbar class="col">
				<q-toolbar-title> <img src="~assets/logo.png" alt="" width="100px" /></q-toolbar-title>
			</q-toolbar>
			<div class="col row q-pa-md q-gutter-sm">
				<q-tabs class="col flex-center">
					<q-route-tab class="text-black" to="/page1" label="Home" />
					<q-route-tab class="text-black" to="/page2" label="About" />
					<q-route-tab class="text-black" to="/page3" label="Services" />
					<q-route-tab class="text-black" to="/page3" label="Contact" />
				</q-tabs>
				<q-btn flat rounded color="white" text-color="black" label="SIGN IN" />
				<q-btn outline rounded color="white" text-color="black" label="SIGN UP" />

				<q-btn
					flat
					dense
					class="text-black"
					icon="menu"
					aria-label="Menu"
					@click="leftDrawerOpen = !leftDrawerOpen"
				/>
			</div>
		</q-header>

		<q-drawer v-model="leftDrawerOpen" side="right" show-if-above bordered content-class="bg-grey-1">
			<q-list>
				<q-item-label header class="text-grey-8"> Essential Links </q-item-label>
				<EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
			</q-list>
		</q-drawer>

		<q-page-container>
			<router-view />
		</q-page-container>
	</q-layout>
</template>

<script>
	import EssentialLink from 'components/EssentialLink.vue'

	const linksData = [
		{
			title: 'Docs',
			caption: 'quasar.dev',
			icon: 'school',
			link: 'https://quasar.dev',
		},
		{
			title: 'Github',
			caption: 'github.com/quasarframework',
			icon: 'code',
			link: 'https://github.com/quasarframework',
		},
		{
			title: 'Discord Chat Channel',
			caption: 'chat.quasar.dev',
			icon: 'chat',
			link: 'https://chat.quasar.dev',
		},
		{
			title: 'Forum',
			caption: 'forum.quasar.dev',
			icon: 'record_voice_over',
			link: 'https://forum.quasar.dev',
		},
		{
			title: 'Twitter',
			caption: '@quasarframework',
			icon: 'rss_feed',
			link: 'https://twitter.quasar.dev',
		},
		{
			title: 'Facebook',
			caption: '@QuasarFramework',
			icon: 'public',
			link: 'https://facebook.quasar.dev',
		},
		{
			title: 'Quasar Awesome',
			caption: 'Community Quasar projects',
			icon: 'favorite',
			link: 'https://awesome.quasar.dev',
		},
	]

	export default {
		name: 'MainLayout',
		components: {
			EssentialLink,
		},
		data() {
			return {
				leftDrawerOpen: false,
				essentialLinks: linksData,
			}
		},
	}
</script>
