<script lang="ts">
	import TiptapEditor from '$lib/components/editor/tiptapEditor/TiptapEditor.svelte';

	// Skeleton
	// import File from '$lib/components/icons/File.svelte';
	// import { FileDropzone } from '@skeletonlabs/skeleton';

	//Skeleton
	// let files: FileList;
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

<div>
	<TiptapEditor />
</div>
