<script lang="ts">
    import "@friendofsvelte/tipex/styles/index.css";
    import "./showcase.css";
</script>

<svelte:head>
    <title>Tipex Editor Variants - Showcase</title>
    <meta name="description" content="Explore three distinct Tipex editor variants with unique themes and styles">
</svelte:head>

<div class="showcase-container">
    <header class="showcase-header">
        <div class="header-content">
            <h1 class="main-title">
                <span class="title-gradient">Tipex Editor</span>
                <span class="title-variants">Variants</span>
            </h1>
            <p class="main-description">
                Discover three unique editor experiences, each crafted with <strong>Tailwind CSS v4</strong> 
                and modern design principles. Choose the style that matches your workflow.
            </p>
        </div>
    </header>

    <main class="variants-grid">
        <!-- Minimal Dark Editor -->
        <article class="variant-card minimal-dark-card">
            <div class="card-preview">
                <div class="preview-window">
                    <div class="preview-header">
                        <div class="preview-dots">
                            <span class="dot"></span>
                            <span class="dot"></span>
                            <span class="dot"></span>
                        </div>
                        <span class="preview-title">Minimal Dark</span>
                    </div>
                    <div class="preview-content minimal-dark-preview">
                        <div class="preview-toolbar">
                            <button class="preview-btn">Save</button>
                            <div class="preview-utilities">
                                <button class="preview-util">B</button>
                                <button class="preview-util">I</button>
                                <button class="preview-util">&lt;/&gt;</button>
                            </div>
                        </div>
                        <div class="preview-editor">
                            <h3>Clean & Focused</h3>
                            <p>A distraction-free environment for pure writing...</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="card-content">
                <h2 class="card-title">Minimal Dark Editor</h2>
                <p class="card-description">
                    A clean, distraction-free writing environment with dark theme aesthetics. 
                    Perfect for focused writing sessions and long-form content creation.
                </p>
                
                <div class="card-features">
                    <div class="feature-tag">🌙 Dark Theme</div>
                    <div class="feature-tag">✨ Minimal UI</div>
                    <div class="feature-tag">⚡ Fast & Clean</div>
                </div>
                
                <a href="/minimal-dark" class="card-button minimal-dark-btn">
                    <span>Try Minimal Dark</span>
                    <iconify-icon icon="fa6-solid:arrow-right"></iconify-icon>
                </a>
            </div>
        </article>

        <!-- Vibrant Creative Editor -->
        <article class="variant-card vibrant-creative-card">
            <div class="card-preview">
                <div class="preview-window">
                    <div class="preview-header">
                        <div class="preview-dots">
                            <span class="dot"></span>
                            <span class="dot"></span>
                            <span class="dot"></span>
                        </div>
                        <span class="preview-title">Vibrant Creative</span>
                    </div>
                    <div class="preview-content vibrant-creative-preview">
                        <div class="preview-toolbar vibrant-toolbar">
                            <button class="preview-btn vibrant-btn">Export</button>
                            <div class="preview-stats">
                                <span>125 words</span>
                            </div>
                        </div>
                        <div class="preview-editor">
                            <h3 class="vibrant-heading">Creative & Colorful</h3>
                            <p>Express yourself with vibrant gradients and playful design...</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="card-content">
                <h2 class="card-title">Vibrant Creative Editor</h2>
                <p class="card-description">
                    A colorful, inspiring editor with gradients and playful animations. 
                    Designed for creative writers who love vibrant, energetic interfaces.
                </p>
                
                <div class="card-features">
                    <div class="feature-tag">🌈 Colorful Gradients</div>
                    <div class="feature-tag">🎨 Creative Design</div>
                    <div class="feature-tag">✨ Animations</div>
                </div>
                
                <a href="/vibrant-creative" class="card-button vibrant-creative-btn">
                    <span>Try Vibrant Creative</span>
                    <iconify-icon icon="fa6-solid:arrow-right"></iconify-icon>
                </a>
            </div>
        </article>

        <!-- Full-Screen Professional Editor -->
        <article class="variant-card fullscreen-pro-card">
            <div class="card-preview">
                <div class="preview-window">
                    <div class="preview-header">
                        <div class="preview-dots">
                            <span class="dot"></span>
                            <span class="dot"></span>
                            <span class="dot"></span>
                        </div>
                        <span class="preview-title">Full-Screen Pro</span>
                    </div>
                    <div class="preview-content fullscreen-pro-preview">
                        <div class="preview-status-bar">
                            <div class="status-stats">
                                <span>245 words</span>
                                <span>1,234 chars</span>
                                <span>2 min read</span>
                            </div>
                            <div class="status-actions">
                                <button class="status-btn">⌘S</button>
                                <button class="status-btn">⛶</button>
                            </div>
                        </div>
                        <div class="preview-editor pro-editor">
                            <h3>Professional Document</h3>
                            <p>Advanced features for serious writers and professionals...</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="card-content">
                <h2 class="card-title">Full-Screen Professional</h2>
                <p class="card-description">
                    A comprehensive editor with advanced features, keyboard shortcuts, 
                    and professional typography. Built for serious writers and content creators.
                </p>
                
                <div class="card-features">
                    <div class="feature-tag">⌨️ Keyboard Shortcuts</div>
                    <div class="feature-tag">📊 Advanced Stats</div>
                    <div class="feature-tag">🎯 Focus Mode</div>
                </div>
                
                <a href="/fullscreen-pro" class="card-button fullscreen-pro-btn">
                    <span>Try Full-Screen Pro</span>
                    <iconify-icon icon="fa6-solid:arrow-right"></iconify-icon>
                </a>
            </div>
        </article>
    </main>

    <footer class="showcase-footer">
        <div class="footer-content">
            <div class="tech-stack">
                <h3>Built With Modern Technology</h3>
                <div class="tech-tags">
                    <span class="tech-tag">
                        <iconify-icon icon="logos:svelte-icon"></iconify-icon>
                        Svelte 5 + Runes
                    </span>
                    <span class="tech-tag">
                        <iconify-icon icon="logos:tailwindcss-icon"></iconify-icon>
                        Tailwind CSS v4
                    </span>
                    <span class="tech-tag">
                        <iconify-icon icon="simple-icons:typescript"></iconify-icon>
                        TypeScript
                    </span>
                    <span class="tech-tag">
                        <iconify-icon icon="file-icons:owl"></iconify-icon>
                        ProseMirror
                    </span>
                </div>
            </div>
            
            <div class="footer-links">
                <a href="https://github.com/friendofsvelte/tipex" class="footer-link">
                    <iconify-icon icon="fa6-brands:github"></iconify-icon>
                    GitHub Repository
                </a>
                <a href="https://tipex.dev" class="footer-link">
                    <iconify-icon icon="fa6-solid:book"></iconify-icon>
                    Documentation
                </a>
            </div>
        </div>
    </footer>
</div>