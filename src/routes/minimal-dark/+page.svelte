<script lang="ts">
    import { Tipex, type TipexEditor } from '@friendofsvelte/tipex';
    import "@friendofsvelte/tipex/styles/index.css";
    import "./resources/minimal-dark.css";
    
    let body = `<h1>Minimal Dark Editor</h1>
<p>This is a clean, minimal dark theme editor perfect for distraction-free writing. The dark theme reduces eye strain and provides a professional coding environment feel.</p>
<blockquote>Focus on your content with this minimalist approach.</blockquote>
<ul>
<li>Clean typography</li>
<li>Subtle animations</li>
<li>Perfect contrast ratios</li>
</ul>`;

    let editor = $state() as TipexEditor;
    
    // Custom save function for demo
    function handleSave() {
        console.log('Saving content:', editor?.getHTML());
        // Add your save logic here
    }
</script>

<svelte:head>
    <title>Minimal Dark Editor - Tipex Variant</title>
    <meta name="description" content="A clean, minimal dark theme editor for distraction-free writing">
</svelte:head>

<div class="minimal-dark-container">
    <header class="minimal-header">
        <div class="header-content">
            <h1 class="editor-title">Minimal Dark Editor</h1>
            <div class="header-actions">
                <button class="save-btn" onclick={handleSave}>
                    <iconify-icon icon="fa6-solid:floppy-disk"></iconify-icon>
                    Save
                </button>
                <a href="/" class="back-btn">
                    <iconify-icon icon="fa6-solid:arrow-left"></iconify-icon>
                    Back
                </a>
            </div>
        </div>
    </header>
    
    <main class="editor-main">
        <Tipex 
            bind:tipex={editor}
            {body} 
            controls 
            floating 
            focal
            class="minimal-dark-editor"
        >
            {#snippet utilities(tipex)}
                <button 
                    class="utility-btn"
                    onclick={() => tipex.commands.toggleBold()}
                    class:active={tipex.isActive('bold')}
                    title="Bold (Ctrl+B)"
                >
                    <iconify-icon icon="fa6-solid:bold"></iconify-icon>
                </button>
                
                <button 
                    class="utility-btn"
                    onclick={() => tipex.commands.toggleItalic()}
                    class:active={tipex.isActive('italic')}
                    title="Italic (Ctrl+I)"
                >
                    <iconify-icon icon="fa6-solid:italic"></iconify-icon>
                </button>
                
                <button 
                    class="utility-btn"
                    onclick={() => tipex.commands.toggleCode()}
                    class:active={tipex.isActive('code')}
                    title="Inline Code"
                >
                    <iconify-icon icon="fa6-solid:code"></iconify-icon>
                </button>
            {/snippet}
        </Tipex>
    </main>
    
    <footer class="minimal-footer">
        <p>Minimal Dark Theme • Focus Mode Enabled</p>
    </footer>
</div> 