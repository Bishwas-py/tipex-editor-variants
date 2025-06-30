<script lang="ts">
	import { Tipex, type TipexEditor } from '@friendofsvelte/tipex';
	import '@friendofsvelte/tipex/styles/index.css';
	import './resources/vibrant-creative.css';

	let body = `<h1>🎨 Vibrant Creative Editor</h1>
<p>Welcome to the <strong>most colorful</strong> and <em>creative</em> editor experience! This theme is designed for artists, designers, and creative minds who want their writing environment to inspire creativity.</p>
<blockquote>✨ "Creativity is intelligence having fun" - Albert Einstein</blockquote>
<h2>🌈 Features</h2>
<ul>
<li>🎨 Beautiful gradient backgrounds</li>
<li>🌟 Animated hover effects</li>
<li>💫 Smooth transitions</li>
<li>🎯 Focus-enhancing colors</li>
</ul>
<h3>💡 Perfect for:</h3>
<ol>
<li>Creative writing</li>
<li>Blog posts</li>
<li>Marketing content</li>
<li>Social media captions</li>
</ol>`;

	let editor = $state() as TipexEditor;
	let wordCount = $state(0);

	// Update word count
	$effect(() => {
		if (editor) {
			const text = editor.getText?.() || '';
			wordCount = text.split(/\s+/).filter((word) => word.length > 0).length;
		}
	});

	function handleExport() {
		if (editor) {
			const content = editor.getHTML?.();
			console.log('Exporting content:', content);
			// Add your export logic here
		}
	}

	function insertEmoji(emoji: string) {
		if (editor) {
			editor.commands?.insertContent?.(emoji);
		}
	}
</script>

<svelte:head>
	<title>Vibrant Creative Editor - Tipex Variant</title>
	<meta
		name="description"
		content="A colorful, creative editor with vibrant gradients and playful design elements"
	/>
</svelte:head>

<div class="vibrant-creative-container">
	<div class="gradient-bg"></div>

	<header class="vibrant-header">
		<div class="header-content">
			<div class="title-section">
				<h1 class="editor-title">
					<span class="title-icon">🎨</span>
					Vibrant Creative Editor
				</h1>
				<div class="word-counter">
					<span class="counter-label">Words:</span>
					<span class="counter-value">{wordCount}</span>
				</div>
			</div>
			<div class="header-actions">
				<button class="export-btn" onclick={handleExport}>
					<iconify-icon icon="fa6-solid:download"></iconify-icon>
					Export
				</button>
				<a href="/" class="back-btn">
					<iconify-icon icon="fa6-solid:home"></iconify-icon>
					Home
				</a>
			</div>
		</div>
	</header>

	<main class="editor-main">
		<div class="emoji-palette">
			<button class="emoji-btn" onclick={() => insertEmoji('✨')}>✨</button>
			<button class="emoji-btn" onclick={() => insertEmoji('🎨')}>🎨</button>
			<button class="emoji-btn" onclick={() => insertEmoji('🌟')}>🌟</button>
			<button class="emoji-btn" onclick={() => insertEmoji('💡')}>💡</button>
			<button class="emoji-btn" onclick={() => insertEmoji('🚀')}>🚀</button>
			<button class="emoji-btn" onclick={() => insertEmoji('💫')}>💫</button>
			<button class="emoji-btn" onclick={() => insertEmoji('🎯')}>🎯</button>
			<button class="emoji-btn" onclick={() => insertEmoji('🌈')}>🌈</button>
		</div>

		<Tipex bind:tipex={editor} {body} floating focal class="vibrant-creative-editor">
			{#snippet controlComponent(tipex)}
				{#if tipex}
					<div class="utility-groups-container">
						<div class="utility-group">
							<button
								class="utility-btn format-btn"
								aria-label="Bold"
								onclick={() => tipex.chain?.().focus().toggleBold().run()}
								class:active={tipex.isActive?.('bold')}
								title="Bold"
							>
								<iconify-icon icon="fa6-solid:bold"></iconify-icon>
							</button>

							<button
								class="utility-btn format-btn"
								aria-label="Italic"
								onclick={() => tipex.chain?.().focus().toggleItalic().run()}
								class:active={tipex.isActive?.('italic')}
								title="Italic"
							>
								<iconify-icon icon="fa6-solid:italic"></iconify-icon>
							</button>

							<button
								class="utility-btn format-btn"
								aria-label="Strikethrough"
								onclick={() => tipex.chain?.().focus().toggleStrike().run()}
								class:active={tipex.isActive?.('strike')}
								title="Strikethrough"
							>
								<iconify-icon icon="fa6-solid:strikethrough"></iconify-icon>
							</button>
						</div>

						<div class="utility-group">
							<button
								class="utility-btn heading-btn"
								aria-label="Heading 1"
								onclick={() => tipex.chain?.().focus().toggleHeading({ level: 1 }).run()}
								class:active={tipex.isActive?.('heading', { level: 1 })}
								title="Heading 1"
							>
								H1
							</button>

							<button
								class="utility-btn heading-btn"
								aria-label="Heading 2"
								onclick={() => tipex.chain?.().focus().toggleHeading({ level: 2 }).run()}
								class:active={tipex.isActive?.('heading', { level: 2 })}
								title="Heading 2"
							>
								H2
							</button>
						</div>

						<div class="utility-group">
							<button
								class="utility-btn list-btn"
								onclick={() => tipex.chain?.().focus().toggleBulletList().run()}
								class:active={tipex.isActive?.('bulletList')}
								title="Bullet List"
							>
								<iconify-icon icon="fa6-solid:list-ul"></iconify-icon>
							</button>

							<button
								class="utility-btn list-btn"
								onclick={() => tipex.chain?.().focus().toggleOrderedList().run()}
								class:active={tipex.isActive?.('orderedList')}
								title="Numbered List"
							>
								<iconify-icon icon="fa6-solid:list-ol"></iconify-icon>
							</button>
						</div>
					</div>
				{/if}
			{/snippet}
		</Tipex>
	</main>

	<footer class="vibrant-footer">
		<div class="footer-content">
			<p>🎨 Vibrant Creative Theme • Unleash Your Creativity</p>
			<div class="theme-credits">
				<span>Made with</span>
				<span class="heart">💖</span>
				<span>for creative minds</span>
			</div>
		</div>
	</footer>
</div>
