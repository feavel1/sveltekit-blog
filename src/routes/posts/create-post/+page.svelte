<script lang="ts">
	// Skeleton
	import File from '$lib/components/icons/File.svelte';
	import { FileDropzone } from '@skeletonlabs/skeleton';

	import MarkdownEditor from '$lib/components/editor/MarkdownEditor.svelte';

	//Skeleton
	let files: FileList;

	//Bytemd
	let value: string;

	function onValueChange(e: any) {
		value = e.detail.value;
	}
</script>

<!-- <FileDropzone name="files" bind:files>
	<svelte:fragment slot="lead">
		<span class="badge variant-filled">
			<File />
		</span>
	</svelte:fragment>
	<svelte:fragment slot="message">Upload post cover image</svelte:fragment>
	<svelte:fragment slot="meta">less than 5 mb</svelte:fragment>
</FileDropzone> -->

<MarkdownEditor {value} {onValueChange} />
