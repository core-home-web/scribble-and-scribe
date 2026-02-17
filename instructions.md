# Scribble & Scribe - Project Instructions

## Project Overview

Scribble & Scribe is a Webflow export project for a stationery brand website. This project will periodically receive new exports from Webflow, which may add new files or overwrite existing ones.

**Project Purpose**: Showcase stationery products (planners, pens & pencils, notepads) with an interactive drawing canvas feature.

## Project Structure

```
scribbleandscribe.webflow/
├── index.html              # Main homepage with canvas drawing feature
├── 404.html                # 404 error page
├── 401.html                # 401 error page
├── old-home*.html          # Archived versions of homepage
├── color-effect.html       # Color effect demo page
├── fade-effect.html        # Fade effect demo page
├── css/
│   ├── normalize.css      # CSS reset/normalize
│   ├── components.css     # Webflow component styles
│   └── scribbleandscribe.css  # Main stylesheet with CSS variables
├── js/
│   └── scribbleandscribe.js   # Webflow interactions & custom JS
└── images/                # All image assets (SVG, WebP, JPG)
```

## Key Features

### 1. Interactive Canvas Drawing
- **Location**: `index.html` (embedded script, lines ~213-308)
- **Functionality**: 
  - Interactive drawing canvas on tablet mockup
  - Random color generation on each stroke
  - Right-click to clear canvas
  - Responsive sizing based on container
- **Custom Code**: This is custom JavaScript added to the Webflow export

### 2. Product Gallery
- Three tabs: Planners, Pens & Pencils, Notepads
- Image sliders for each category
- Webflow slider component with navigation

### 3. Responsive Design
- Tablet mockup animations
- Mobile-responsive navigation
- Responsive image sets (multiple sizes per image)

## Handling Periodic Webflow Exports

### Workflow for New Exports

1. **Backup Current Version**
   ```bash
   git add .
   git commit -m "Backup before Webflow export [DATE]"
   ```

2. **Review New Export**
   - Compare file structure
   - Identify new files
   - Identify modified files
   - Check for removed files

3. **Identify Custom Modifications**
   - **Custom Canvas Code**: Located in `index.html` around lines 213-308
   - Any other custom JavaScript or CSS additions
   - Custom image optimizations

4. **Merge Strategy**
   - **Standard Webflow Files**: Safe to overwrite (HTML structure, CSS, JS)
   - **Custom Code Sections**: Preserve and re-apply if overwritten
   - **New Files**: Add all new files
   - **Removed Files**: Archive if needed, then remove

5. **Test After Merge**
   - Verify canvas drawing functionality
   - Check all navigation links
   - Test responsive design
   - Verify image loading

### Files That May Contain Custom Code

- `index.html` - Contains custom canvas drawing script
- `js/scribbleandscribe.js` - May contain custom modifications
- `css/scribbleandscribe.css` - May have custom CSS additions

### Files Safe to Overwrite

- `404.html`, `401.html` - Standard error pages
- `css/normalize.css`, `css/components.css` - Webflow-generated
- Most image files (unless manually optimized)

## Development Workflow

### Making Custom Changes

1. **Identify the Change Type**
   - Webflow content change → Update in Webflow, re-export
   - Custom feature addition → Add to project, document clearly
   - Bug fix → Fix in project, note for future exports

2. **Document Changes**
   - Add comments: `<!-- CUSTOM: [description] -->`
   - Update this `instructions.md` if adding major features
   - Update `.cursorrules` if establishing new patterns

3. **Commit Changes**
   ```bash
   git add .
   git commit -m "Description of changes"
   git push origin main
   ```

### Testing Checklist

After each Webflow export or custom change:
- [ ] Canvas drawing works on desktop
- [ ] Canvas drawing works on mobile/tablet
- [ ] Navigation menu functions correctly
- [ ] Product gallery tabs switch properly
- [ ] Image sliders work in all tabs
- [ ] Responsive design works on multiple screen sizes
- [ ] All images load correctly
- [ ] No console errors

## Git Repository

- **Remote**: `https://github.com/core-home-web/scribble-and-scribe.git`
- **Branch**: `main`
- **Initial Commit**: Contains complete Webflow export

### Git Best Practices

- Commit Webflow exports separately from custom modifications
- Use descriptive commit messages
- Tag major versions if needed
- Keep `old-*` files for reference but don't commit unnecessary duplicates

## Technical Details

### Dependencies
- jQuery (loaded via Webflow CDN)
- Webflow Interactions library
- Google Fonts (Archivo)

### Browser Support
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)

### Performance Considerations
- Images are provided in multiple sizes (responsive images)
- WebP format used where available
- Canvas resizing optimized for performance

## Custom Code Reference

### Canvas Drawing Implementation

The canvas drawing feature is implemented directly in `index.html`. Key components:

- **Canvas Element**: `#draw` (line ~51)
- **Initialization**: `DOMContentLoaded` event listener (line ~213)
- **Drawing Logic**: Mouse event handlers (lines ~292-307)
- **Color Generation**: Random HSL colors (line ~280, ~295)
- **Clear Function**: Right-click handler (lines ~304-307)

To preserve this feature during Webflow exports:
1. Locate the canvas element in the new export
2. Copy the custom script section
3. Ensure canvas ID matches (`#draw`)
4. Test functionality

## Troubleshooting

### Canvas Not Drawing
- Check if canvas element exists: `document.querySelector("canvas")`
- Verify canvas context: `canvas.getContext("2d")`
- Check for JavaScript errors in console
- Ensure canvas container (`.ipad-screen`) is visible

### Styles Not Applying
- Check CSS file paths in HTML
- Verify CSS custom properties are defined
- Check for conflicting Webflow styles

### Images Not Loading
- Verify image paths are correct
- Check file extensions match (case-sensitive)
- Ensure images are committed to repository

## Future Considerations

- Consider extracting custom JavaScript to separate file
- May want to add build process for optimization
- Could add environment variables for configuration
- May need to add analytics or tracking code

## Contact & Maintenance

This project is maintained by the development team. For questions about Webflow exports or custom modifications, refer to this documentation or the `.cursorrules` file.
