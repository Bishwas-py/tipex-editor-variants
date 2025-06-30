<script lang="ts">
    import "@friendofsvelte/tipex/styles/index.css";
    import "./showcase.css";
</script>

<svelte:head>
    <title>Tipex Editor Variants - Modern Rich Text Editor</title>
    <meta name="description" content="Explore three beautifully crafted Tipex editor variants with unique themes and professional styling">
</svelte:head>

<div class="showcase-container">
    <!-- Hero Section -->
    <section class="hero-section">
        <div class="hero-background">
            <div class="hero-grid"></div>
            <div class="hero-glow"></div>
        </div>
        
        <div class="hero-content">
            <div class="hero-badge">
                <iconify-icon icon="fa6-solid:sparkles"></iconify-icon>
                <span>Powered by Tailwind CSS v4</span>
            </div>
            
            <h1 class="hero-title">
                <span class="title-line">Beautiful</span>
                <span class="title-line title-gradient">Tipex Editors</span>
                <span class="title-line">for Every Need</span>
            </h1>
            
            <p class="hero-description">
                Three meticulously crafted editor experiences that blend functionality with stunning design. 
                Choose your perfect writing companion.
            </p>
            
            <div class="hero-stats">
                <div class="stat-item">
                    <iconify-icon icon="fa6-solid:palette"></iconify-icon>
                    <span>3 Unique Themes</span>
                </div>
                <div class="stat-item">
                    <iconify-icon icon="fa6-solid:bolt"></iconify-icon>
                    <span>Lightning Fast</span>
                </div>
                <div class="stat-item">
                    <iconify-icon icon="fa6-solid:mobile-screen"></iconify-icon>
                    <span>Fully Responsive</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Editor Variants Section -->
    <section class="variants-section">
        <div class="section-header">
            <h2 class="section-title">Choose Your Editor Experience</h2>
            <p class="section-description">
                Each variant is carefully designed for different use cases and aesthetic preferences
            </p>
        </div>

        <div class="variants-container">
            <!-- Minimal Dark Editor -->
            <article class="editor-card minimal-card">
                <div class="card-glow minimal-glow"></div>
                
                <div class="card-header">
                    <div class="card-icon minimal-icon">
                        <iconify-icon icon="fa6-solid:moon"></iconify-icon>
                    </div>
                    <div class="card-meta">
                        <h3 class="card-title">Minimal Dark</h3>
                        <p class="card-subtitle">Focus-First Design</p>
                    </div>
                </div>

                <div class="card-preview">
                    <div class="preview-frame">
                        <div class="preview-header">
                            <div class="window-controls">
                                <span class="control-dot red"></span>
                                <span class="control-dot yellow"></span>
                                <span class="control-dot green"></span>
                            </div>
                            <span class="window-title">Document.md</span>
                        </div>
                        
                        <div class="preview-body minimal-preview">
                            <div class="editor-toolbar">
                                <button class="tool-btn">Save</button>
                                <div class="tool-group">
                                    <button class="tool-icon">B</button>
                                    <button class="tool-icon">I</button>
                                    <button class="tool-icon">&lt;/&gt;</button>
                                </div>
                            </div>
                            <div class="editor-content">
                                <h4>Clean Writing Experience</h4>
                                <p>Distraction-free environment with elegant dark aesthetics...</p>
                                <ul>
                                    <li>Minimal interface</li>
                                    <li>Dark theme optimized</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="card-features">
                    <div class="feature-list">
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:eye"></iconify-icon>
                            <span>Distraction-Free</span>
                        </div>
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:moon"></iconify-icon>
                            <span>Dark Theme</span>
                        </div>
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:zap"></iconify-icon>
                            <span>Ultra Clean</span>
                        </div>
                    </div>
                </div>

                <a href="/minimal-dark" class="card-action minimal-action">
                    <span>Try Minimal Dark</span>
                    <iconify-icon icon="fa6-solid:arrow-right"></iconify-icon>
                </a>
            </article>

            <!-- Vibrant Creative Editor -->
            <article class="editor-card creative-card featured">
                <div class="card-glow creative-glow"></div>
                <div class="featured-badge">
                    <iconify-icon icon="fa6-solid:star"></iconify-icon>
                    <span>Most Popular</span>
                </div>
                
                <div class="card-header">
                    <div class="card-icon creative-icon">
                        <iconify-icon icon="fa6-solid:palette"></iconify-icon>
                    </div>
                    <div class="card-meta">
                        <h3 class="card-title">Vibrant Creative</h3>
                        <p class="card-subtitle">Colorful & Inspiring</p>
                    </div>
                </div>

                <div class="card-preview">
                    <div class="preview-frame">
                        <div class="preview-header">
                            <div class="window-controls">
                                <span class="control-dot red"></span>
                                <span class="control-dot yellow"></span>
                                <span class="control-dot green"></span>
                            </div>
                            <span class="window-title">Creative.html</span>
                        </div>
                        
                        <div class="preview-body creative-preview">
                            <div class="editor-toolbar creative-toolbar">
                                <button class="tool-btn creative-btn">Export</button>
                                <div class="word-counter">
                                    <iconify-icon icon="fa6-solid:chart-line"></iconify-icon>
                                    <span>142 words</span>
                                </div>
                            </div>
                            <div class="editor-content">
                                <h4 class="creative-heading">Unleash Your Creativity</h4>
                                <p>Express yourself with vibrant colors and smooth animations...</p>
                                <div class="emoji-toolbar">
                                    <button class="emoji-btn">😊</button>
                                    <button class="emoji-btn">🎨</button>
                                    <button class="emoji-btn">✨</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="card-features">
                    <div class="feature-list">
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:rainbow"></iconify-icon>
                            <span>Colorful Gradients</span>
                        </div>
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:magic-wand-sparkles"></iconify-icon>
                            <span>Smooth Animations</span>
                        </div>
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:heart"></iconify-icon>
                            <span>Creative Tools</span>
                        </div>
                    </div>
                </div>

                <a href="/vibrant-creative" class="card-action creative-action">
                    <span>Try Vibrant Creative</span>
                    <iconify-icon icon="fa6-solid:arrow-right"></iconify-icon>
                </a>
            </article>

            <!-- Full-Screen Professional Editor -->
            <article class="editor-card professional-card">
                <div class="card-glow professional-glow"></div>
                
                <div class="card-header">
                    <div class="card-icon professional-icon">
                        <iconify-icon icon="fa6-solid:briefcase"></iconify-icon>
                    </div>
                    <div class="card-meta">
                        <h3 class="card-title">Full-Screen Pro</h3>
                        <p class="card-subtitle">Advanced Features</p>
                    </div>
                </div>

                <div class="card-preview">
                    <div class="preview-frame">
                        <div class="preview-header">
                            <div class="window-controls">
                                <span class="control-dot red"></span>
                                <span class="control-dot yellow"></span>
                                <span class="control-dot green"></span>
                            </div>
                            <span class="window-title">Professional.docx</span>
                        </div>
                        
                        <div class="preview-body professional-preview">
                            <div class="status-bar">
                                <div class="status-left">
                                    <span class="status-item">245 words</span>
                                    <span class="status-item">1,234 chars</span>
                                    <span class="status-item">2 min read</span>
                                </div>
                                <div class="status-right">
                                    <button class="status-action">⌘S</button>
                                    <button class="status-action">⛶</button>
                                </div>
                            </div>
                            <div class="editor-content">
                                <h4>Professional Document</h4>
                                <p>Advanced editing with comprehensive tools and shortcuts...</p>
                                <blockquote>Perfect for serious writers and content creators.</blockquote>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="card-features">
                    <div class="feature-list">
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:keyboard"></iconify-icon>
                            <span>Keyboard Shortcuts</span>
                        </div>
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:chart-bar"></iconify-icon>
                            <span>Advanced Stats</span>
                        </div>
                        <div class="feature-item">
                            <iconify-icon icon="fa6-solid:expand"></iconify-icon>
                            <span>Full-Screen Mode</span>
                        </div>
                    </div>
                </div>

                <a href="/fullscreen-pro" class="card-action professional-action">
                    <span>Try Full-Screen Pro</span>
                    <iconify-icon icon="fa6-solid:arrow-right"></iconify-icon>
                </a>
            </article>
        </div>
    </section>

    <!-- Technology Section -->
    <section class="tech-section">
        <div class="tech-content">
            <h2 class="tech-title">Built with Modern Technology</h2>
            <p class="tech-description">
                Leveraging the latest web technologies for optimal performance and developer experience
            </p>
            
            <div class="tech-grid">
                <div class="tech-card">
                    <iconify-icon icon="logos:svelte-icon"></iconify-icon>
                    <h3>Svelte 5</h3>
                    <p>Latest runes and reactive system</p>
                </div>
                <div class="tech-card">
                    <iconify-icon icon="logos:tailwindcss-icon"></iconify-icon>
                    <h3>Tailwind v4</h3>
                    <p>Modern CSS architecture</p>
                </div>
                <div class="tech-card">
                    <iconify-icon icon="logos:typescript-icon"></iconify-icon>
                    <h3>TypeScript</h3>
                    <p>Type-safe development</p>
                </div>
                <div class="tech-card">
                    <iconify-icon icon="simple-icons:prosemirror"></iconify-icon>
                    <h3>ProseMirror</h3>
                    <p>Powerful rich text editing</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="showcase-footer">
        <div class="footer-content">
            <div class="footer-brand">
                <h3>Tipex Editor Variants</h3>
                <p>Beautiful, functional, and modern rich text editing experiences.</p>
            </div>
            
            <div class="footer-links">
                <a href="https://github.com/friendofsvelte/tipex" class="footer-link">
                    <iconify-icon icon="fa6-brands:github"></iconify-icon>
                    <span>View on GitHub</span>
                </a>
                <a href="https://tipex.dev" class="footer-link">
                    <iconify-icon icon="fa6-solid:globe"></iconify-icon>
                    <span>Documentation</span>
                </a>
            </div>
        </div>
    </footer>
</div>