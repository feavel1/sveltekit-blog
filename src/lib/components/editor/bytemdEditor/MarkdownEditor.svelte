<script lang="ts">
	import markdownText from './mok.md?raw';
	import 'bytemd/dist/index.css';

	// Bytemd plugins
	import gfm from '@bytemd/plugin-gfm';
	import frontmatter from '@bytemd/plugin-frontmatter';
	import gemoji from '@bytemd/plugin-gemoji';
	import math from '@bytemd/plugin-math';
	import mermaid from '@bytemd/plugin-mermaid';
	import highlight from '@bytemd/plugin-highlight';

	// Import Bytemd editor
	import Editor from 'bytemd/svelte/editor.svelte';

	import 'github-markdown-css';
	import 'highlight.js/styles/github-dark.css';

	export let value: string = markdownText;
	export let onValueChange: any;

	//Bytemd
	const plugins = [
		gfm(),
		highlight(),
		frontmatter(),
		math()
		// gemoji(),
		// mermaid()
	];

	let mode = 'auto';
</script>

<Editor {mode} {value} {plugins} on:change={onValueChange} />

<!-- uploadImages={(files) => {
		return Promise.all(
			files.map((file) => {
				return {
					url: 'https://picsum.photos/300'
				};
			})
		);
	}} -->

<style>
	:global(.bytemd) {
		height: calc(87vh - 100px);
	}
	:global(.medium-zoom-overlay) {
		z-index: 1000;
	}
	:global(.medium-zoom-image--opened) {
		z-index: 101;
	}
</style>
