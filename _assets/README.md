# Assets Directory for Wiki.js

This directory contains all visual assets used in the eCozy Identity Guidelines Wiki.js documentation.

## Directory Structure

### 📁 `_assets/`
Root directory for all media assets. The underscore prefix prevents Wiki.js from treating this as a documentation page.

### 📂 Subdirectories

#### `images/`
General images used throughout the documentation:
- Screenshots
- Diagrams
- Product images
- UI/UX examples

**Naming convention:** `descriptive-name.png` or `section-name-image.jpg`

#### `logos/`
eCozy logo files and variations:
- Full logo (color, monochrome, reversed)
- Logomark
- Tagline versions
- Different file formats (SVG, PNG, PDF)

**Naming convention:** `ecozy-logo-[variant]-[color].svg`
Example: `ecozy-logo-full-color.svg`, `ecozy-logomark-white.png`

#### `icons/`
Icons and icon sets:
- UI icons
- System icons
- Product category icons
- Social media icons

**Naming convention:** `icon-[name]-[size].svg`
Example: `icon-thermostat-24px.svg`, `icon-sensor-32px.png`

#### `photos/`
Photography and lifestyle images:
- Product photography
- Lifestyle photos
- Team photos
- Office/location photos

**Naming convention:** `photo-[description]-[resolution].jpg`
Example: `photo-thermostat-lifestyle-2000px.jpg`

#### `illustrations/`
Illustrations and graphic elements:
- Brand illustrations
- Technical diagrams
- Infographics
- Decorative elements

**Naming convention:** `illustration-[name].svg`
Example: `illustration-smart-home-ecosystem.svg`

## Usage in Markdown

### Relative Path
From any `.md` file in the repository:
```markdown
![Alt text](/_assets/images/example.png)
```

### With Caption
```markdown
![eCozy Thermostat](/_assets/photos/photo-thermostat-lifestyle-2000px.jpg)
*eCozy Smart Thermostat in a modern living room*
```

### Inline Image
```markdown
The eCozy logo ![logo](/_assets/logos/ecozy-logomark-color.svg) represents...
```

## File Requirements

### Image Formats
- **Logos/Icons:** SVG (preferred), PNG with transparency
- **Photos:** JPG (optimized), PNG if transparency needed
- **Diagrams:** SVG (preferred), PNG

### File Size Guidelines
- **Icons:** < 50 KB
- **Logos:** < 200 KB
- **Photos:** < 500 KB (compress for web)
- **Illustrations:** < 300 KB

### Resolution
- **Web display:** 72-96 DPI
- **Print-ready:** 300 DPI (store in separate print-assets folder if needed)
- **Max width:** 2000px for full-width images

## Optimization

Before adding images:
1. Compress JPEG images (use tools like TinyPNG, ImageOptim)
2. Optimize SVG files (remove unnecessary metadata)
3. Use appropriate format (SVG for logos/icons, JPEG for photos)
4. Add descriptive alt text in Markdown for accessibility

## Git LFS (Optional)

For large binary assets, consider using Git LFS:
```bash
git lfs track "*.psd"
git lfs track "*.ai"
git lfs track "_assets/**/*.jpg"
```

## Wiki.js Integration

Wiki.js automatically serves files from this directory. The `_assets` prefix:
- ✅ Prevents Wiki.js from indexing these as pages
- ✅ Makes assets accessible via direct URL
- ✅ Allows referencing in any markdown file

**Example URL:** `https://your-wiki.com/_assets/images/example.png`

## Maintenance

- Review and optimize images quarterly
- Remove unused assets
- Update this README when adding new subdirectories
- Keep consistent naming conventions

---

**Last updated:** 2025-12-19
