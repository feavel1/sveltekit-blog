<script lang="ts">
	import Subscription from '$lib/components/ui/Subscription.svelte';

	import type { PageData } from './$types';

	export let data: PageData;
	let { session, subscription, products } = data;
	$: ({ session } = data);
</script>

<Subscription {products} {subscription} {session} />
