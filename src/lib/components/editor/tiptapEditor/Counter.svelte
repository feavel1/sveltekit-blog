<script lang="ts">
	import type { NodeViewProps } from '@tiptap/core';
	import cx from 'clsx';
	import { NodeViewWrapper } from 'svelte-tiptap';

	export let node: NodeViewProps['node'];
	export let updateAttributes: NodeViewProps['updateAttributes'];
	export let selected: NodeViewProps['selected'] = false;

	const handleClick = () => {
		updateAttributes({ count: node.attrs.count + 1 });
	};
</script>

<NodeViewWrapper class={cx('svelte-component', { selected })}>
	<span class="label">Svelte Component</span>

	<div class="content">
		<button on:click={handleClick} type="button">
			This button has been clicked {node.attrs.count} times.
		</button>
	</div>
</NodeViewWrapper>
