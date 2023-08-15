<script lang="ts">
	import markdownText from './mok.md?raw';

	import {
		Composer,
		ContentEditable,
		ToolbarRichText,
		ActionBar,
		RichTextPlugin,
		HistoryPlugin,
		ListPlugin,
		CheckListPlugin,
		HorizontalRulePlugin,
		ImagePlugin
	} from 'svelte-lexical';
	import PlaygroundEditorTheme from './themes/PlaygroundEditorTheme';
	import {
		HeadingNode,
		QuoteNode,
		ListNode,
		ListItemNode,
		HorizontalRuleNode,
		ImageNode
	} from 'svelte-lexical';
	import './lexical.css';

	import {
		$getRoot as getRoot,
		$createTextNode as createTextNode,
		$createParagraphNode as createParagraphNode
	} from 'svelte-lexical';

	const initialConfig = {
		theme: PlaygroundEditorTheme,
		nodes: [HeadingNode, ListNode, ListItemNode, QuoteNode, HorizontalRuleNode, ImageNode],
		onError: (error: any) => {
			throw error;
		},
		editorState: () => {
			const root = getRoot();
			if (root.getFirstChild() === null) {
				const paragraph = createParagraphNode();
				paragraph.append(
					createTextNode('This demo environment is built with '),
					createTextNode('svelte-lexical').toggleFormat('code'),
					createTextNode('.'),
					createTextNode(' Try typing in '),
					createTextNode('some text').toggleFormat('bold'),
					createTextNode(' with '),
					createTextNode('different').toggleFormat('italic'),
					createTextNode(' formats.')
				);
				root.append(paragraph);
			}
		}
	};
</script>

<Composer {initialConfig}>
	<div class="editor-shell font-sans">
		<ToolbarRichText />
		<div class="editor-container">
			<div class="editor-scroller">
				<div class="editor">
					<ContentEditable />
				</div>
			</div>
			<RichTextPlugin />
			<HistoryPlugin />
			<ListPlugin />
			<CheckListPlugin />
			<HorizontalRulePlugin />
			<ImagePlugin />

			<ActionBar />
		</div>
	</div>
</Composer>
