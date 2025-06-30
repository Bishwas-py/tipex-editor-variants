<script lang="ts">
    import { Tipex, type TipexEditor } from '@friendofsvelte/tipex';
    import "@friendofsvelte/tipex/styles/index.css";
    import "./resources/fullscreen-pro.css";
    import { onMount } from 'svelte';
    
    let body = `<h1>Full-Screen Professional Editor</h1>
<p>Experience the ultimate <strong>distraction-free writing environment</strong>. This full-screen editor is designed for professionals who need to focus deeply on their content without any visual distractions.</p>
<blockquote>The best writing happens when you can focus completely on your thoughts and ideas.</blockquote>
<h2>Professional Features</h2>
<ul>
<li>Full-screen immersive experience</li>
<li>Keyboard shortcuts for everything</li>
<li>Auto-save functionality</li>
<li>Focus mode with dimmed UI</li>
<li>Professional typography</li>
<li>Advanced document statistics</li>
</ul>
<h3>Keyboard Shortcuts</h3>
<ul>
<li><code>Ctrl + S</code> - Save document</li>
<li><code>Ctrl + B</code> - Bold text</li>
<li><code>Ctrl + I</code> - Italic text</li>
<li><code>F11</code> - Toggle full-screen</li>
<li><code>Ctrl + /</code> - Show all shortcuts</li>
</ul>`;

    let editor = $state() as TipexEditor;
    let isFullscreen = $state(false);
    let isFocusMode = $state(false);
    let wordCount = $state(0);
    let charCount = $state(0);
    let readingTime = $state(0);
    let lastSaved = $state<Date | null>(null);
    let showShortcuts = $state(false);
    
    // Document statistics
    $effect(() => {
        if (editor) {
            const text = editor.getText?.() || '';
            wordCount = text.split(/\s+/).filter(word => word.length > 0).length;
            charCount = text.length;
            readingTime = Math.ceil(wordCount / 200); // 200 words per minute average
        }
    });
    
    // Auto-save functionality
    $effect(() => {
        if (editor) {
            const saveTimer = setTimeout(() => {
                handleAutoSave();
            }, 2000);
            
            return () => clearTimeout(saveTimer);
        }
    });
    
    // Keyboard shortcuts
    onMount(() => {
        function handleKeydown(e: KeyboardEvent) {
            // Ctrl + S for save
            if (e.ctrlKey && e.key === 's') {
                e.preventDefault();
                handleSave();
            }
            
            // F11 for fullscreen
            if (e.key === 'F11') {
                e.preventDefault();
                toggleFullscreen();
            }
            
            // Ctrl + / for shortcuts
            if (e.ctrlKey && e.key === '/') {
                e.preventDefault();
                showShortcuts = !showShortcuts;
            }
            
            // Escape to exit focus mode
            if (e.key === 'Escape') {
                if (isFocusMode) {
                    isFocusMode = false;
                }
                if (showShortcuts) {
                    showShortcuts = false;
                }
            }
        }
        
        document.addEventListener('keydown', handleKeydown);
        
        return () => {
            document.removeEventListener('keydown', handleKeydown);
        };
    });
    
    function toggleFullscreen() {
        if (!document.fullscreenElement) {
            document.documentElement.requestFullscreen();
            isFullscreen = true;
        } else {
            document.exitFullscreen();
            isFullscreen = false;
        }
    }
    
    function toggleFocusMode() {
        isFocusMode = !isFocusMode;
    }
    
    function handleSave() {
        if (editor) {
            const content = editor.getHTML?.();
            console.log('Saving content:', content);
            lastSaved = new Date();
            // Add your save logic here
        }
    }
    
    function handleAutoSave() {
        if (editor) {
            const content = editor.getHTML?.();
            console.log('Auto-saving content:', content);
            lastSaved = new Date();
            // Add your auto-save logic here
        }
    }
    
    function handleExport() {
        if (editor) {
            const content = editor.getHTML?.();
            const blob = new Blob([content], { type: 'text/html' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'document.html';
            a.click();
            URL.revokeObjectURL(url);
        }
    }
    
    function formatLastSaved(date: Date | null) {
        if (!date) return 'Never';
        const now = new Date();
        const diff = now.getTime() - date.getTime();
        const minutes = Math.floor(diff / 60000);
        
        if (minutes < 1) return 'Just now';
        if (minutes === 1) return '1 minute ago';
        return `${minutes} minutes ago`;
    }
</script>

<svelte:head>
    <title>Full-Screen Professional Editor - Tipex Variant</title>
    <meta name="description" content="A distraction-free full-screen editor for professional writing and content creation">
</svelte:head>

<div class="fullscreen-pro-container" class:fullscreen={isFullscreen} class:focus-mode={isFocusMode}>
    <!-- Status Bar -->
    <div class="status-bar" class:hidden={isFocusMode}>
        <div class="status-left">
            <div class="document-stats">
                <span class="stat-item">
                    <iconify-icon icon="fa6-solid:file-word"></iconify-icon>
                    {wordCount} words
                </span>
                <span class="stat-item">
                    <iconify-icon icon="fa6-solid:font"></iconify-icon>
                    {charCount} chars
                </span>
                <span class="stat-item">
                    <iconify-icon icon="fa6-solid:clock"></iconify-icon>
                    {readingTime} min read
                </span>
            </div>
        </div>
        
        <div class="status-center">
            <h1 class="document-title">Professional Document</h1>
        </div>
        
        <div class="status-right">
            <div class="save-status">
                <iconify-icon icon="fa6-solid:cloud" class="save-icon"></iconify-icon>
                <span class="save-text">Saved {formatLastSaved(lastSaved)}</span>
            </div>
            
            <div class="action-buttons">
                <button class="action-btn" onclick={handleSave} title="Save (Ctrl+S)" aria-label="Save">
                    <iconify-icon icon="fa6-solid:floppy-disk"></iconify-icon>
                </button>

				<button
					class="action-btn"
					onclick={handleExport}
					title="Export"
					aria-label="Export"
				>
					<iconify-icon icon="fa6-solid:download"></iconify-icon>
				</button>

                <button class="action-btn" onclick={toggleFocusMode} title="Focus Mode" aria-label="Focus Mode">
                    <iconify-icon icon="fa6-solid:eye"></iconify-icon>
                </button>
                
                <button class="action-btn" onclick={toggleFullscreen} title="Fullscreen (F11)" aria-label="Fullscreen">
                    <iconify-icon icon="fa6-solid:expand"></iconify-icon>
                </button>
                
                <button class="action-btn" onclick={() => showShortcuts = !showShortcuts} title="Shortcuts (Ctrl+/)" aria-label="Shortcuts">
                    <iconify-icon icon="fa6-solid:keyboard"></iconify-icon>
                </button>

				<a
					href="/"
					class="action-btn home-btn"
					title="Home"
					aria-label="Home"
				>
					<iconify-icon icon="fa-solid:home"></iconify-icon>
				</a>
			</div>
        </div>
    </div>
    
    <!-- Main Editor Area -->
    <main class="editor-area">
        <Tipex 
            bind:tipex={editor}
            {body} 
            floating 
            focal
            class="fullscreen-pro-editor"
        >
            {#snippet controlComponent(tipex)}
                <div class="pro-utilities">
                    <div class="utility-section">
                        <span class="section-label">Format</span>
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleBold?.()}
                            class:active={tipex?.isActive?.('bold')}
                            title="Bold (Ctrl+B)"
							aria-label="Bold"
						>
							<iconify-icon icon="fa6-solid:bold"></iconify-icon>
                        </button>
                        
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleItalic?.()}
                            class:active={tipex?.isActive?.('italic')}
                            title="Italic (Ctrl+I)"
							aria-label="Italic"
						>
							<iconify-icon icon="fa6-solid:italic"></iconify-icon>
                        </button>
                        
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleStrike?.()}
                            class:active={tipex?.isActive?.('strike')}
                            title="Strikethrough"
							aria-label="Strikethrough"
						>
							<iconify-icon icon="fa6-solid:strikethrough"></iconify-icon>
                        </button>
                    </div>
                    
                    <div class="utility-section">
                        <span class="section-label">Structure</span>
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleHeading?.({ level: 1 })}
                            class:active={tipex?.isActive?.('heading', { level: 1 })}
                            title="Heading 1"
                        >
                            H1
                        </button>
                        
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleHeading?.({ level: 2 })}
                            class:active={tipex?.isActive?.('heading', { level: 2 })}
                            title="Heading 2"
                        >
                            H2
                        </button>
                        
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleBlockquote?.()}
                            class:active={tipex?.isActive?.('blockquote')}
                            title="Quote"
							aria-label="Quote"
						>
							<iconify-icon icon="fa6-solid:quote-left"></iconify-icon>
                        </button>
                    </div>
                    
                    <div class="utility-section">
                        <span class="section-label">Lists</span>
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleBulletList?.()}
                            class:active={tipex?.isActive?.('bulletList')}
                            title="Bullet List"
							aria-label="Bullet List"
						>
							<iconify-icon icon="fa6-solid:list-ul"></iconify-icon>
                        </button>
                        
                        <button 
                            class="pro-utility-btn"
                            onclick={() => (tipex as any)?.commands?.toggleOrderedList?.()}
                            class:active={tipex?.isActive?.('orderedList')}
                            title="Numbered List"
							aria-label="Numbered List"
						>
							<iconify-icon icon="fa6-solid:list-ol"></iconify-icon>
                        </button>
                    </div>
                </div>
            {/snippet}
        </Tipex>
    </main>
    
    <!-- Keyboard Shortcuts Modal -->
    {#if showShortcuts}
        <div class="shortcuts-overlay" onclick={() => showShortcuts = false}>
            <div class="shortcuts-modal" onclick={(e) => e.stopPropagation()}>
                <div class="shortcuts-header">
                    <h3>Keyboard Shortcuts</h3>
                    <button class="close-btn" onclick={() => showShortcuts = false} aria-label="Close">
                        <iconify-icon icon="fa6-solid:xmark"></iconify-icon>
                    </button>
                </div>
                
                <div class="shortcuts-content">
                    <div class="shortcut-group">
                        <h4>Document</h4>
                        <div class="shortcut-item">
                            <span class="shortcut-keys">Ctrl + S</span>
                            <span class="shortcut-desc">Save document</span>
                        </div>
                        <div class="shortcut-item">
                            <span class="shortcut-keys">F11</span>
                            <span class="shortcut-desc">Toggle fullscreen</span>
                        </div>
                    </div>
                    
                    <div class="shortcut-group">
                        <h4>Formatting</h4>
                        <div class="shortcut-item">
                            <span class="shortcut-keys">Ctrl + B</span>
                            <span class="shortcut-desc">Bold text</span>
                        </div>
                        <div class="shortcut-item">
                            <span class="shortcut-keys">Ctrl + I</span>
                            <span class="shortcut-desc">Italic text</span>
                        </div>
                    </div>
                    
                    <div class="shortcut-group">
                        <h4>Interface</h4>
                        <div class="shortcut-item">
                            <span class="shortcut-keys">Ctrl + /</span>
                            <span class="shortcut-desc">Show shortcuts</span>
                        </div>
                        <div class="shortcut-item">
                            <span class="shortcut-keys">Escape</span>
                            <span class="shortcut-desc">Exit focus mode</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    {/if}
</div> 