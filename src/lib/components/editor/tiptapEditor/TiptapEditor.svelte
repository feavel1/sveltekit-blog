<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import type { Readable } from 'svelte/store';
	import { createEditor, Editor, EditorContent } from 'svelte-tiptap';
	import StarterKit from '@tiptap/starter-kit';

	import { SvelteCounterExtension } from './SvelteExtension';

	let editor: Readable<Editor>;

	onMount(() => {
		editor = createEditor({
			extensions: [StarterKit, SvelteCounterExtension],
			content: `
        <p>This is still the text editor you’re used to, but enriched with node views.</p>
        <svelte-counter-component count="0"></svelte-counter-component>
        <p>Did you see that? That’s a Svelte component. We are really living in the future.</p>
      `
		});
	});
</script>

<EditorContent editor={$editor} />
