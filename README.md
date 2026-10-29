# Vector-Spaces-and-Linear-Transformations
This repository contains animations that I use in course I teach at IE University on Linear Algebra and Geometry.

# Linear Algebra and Geometry: interactive animations

Interactive, browser-based animations for the Linear Algebra and Geometry courses at the School of Science & Technology, IE University. Students can move vectors, change matrices and watch the plane (or space) respond, with nothing to install.

**Open the collection:** `https://<github-username>.github.io/<repository-name>/`
(replace with the real address once GitHub Pages is enabled, see [Publishing the site](#publishing-the-site))

## Animations

| Animation | Course | What students do |
|---|---|---|
| [Linear transformations of the plane](linear_transformations_activity.html) | Linear Algebra | Choose a 2 × 2 matrix *A* and a figure (a preset, a polygon they draw, or an uploaded picture) and watch every point *x* move to *Ax*, reading off the determinant, area change and inverse. A second mode, the mystery matrix challenge, asks them to find a hidden matrix from where it sends a grid of coloured dots. |
| [Euclidean spaces, seen](euclidean_spaces_interactive.html) | Geometry | An interactive companion to Chapter 2 of the course notes, in four parts: inner products on the plane and the Gram matrix (§2.1, §2.3.1), orthogonal decomposition (§2.4.1, §2.4.3), the Frobenius inner product on 2 × 2 matrices (§2.1, Example 2.1.1), and orthogonal projection onto a plane in 3D (§2.4.4). |

## For students

Open the collection link above and choose an animation. Each one runs entirely in your browser; your work is not saved or sent anywhere.

You can also download the repository (**Code → Download ZIP**), unzip it and open `index.html` or any animation file directly. An internet connection is still needed for the fonts, the IE University logo and, in some animations, the rendering of formulas.

The animations work in recent versions of Chrome, Edge, Firefox and Safari, on computers and tablets. A phone works too, though the larger screen is more comfortable. All controls can be used with the keyboard as well as the mouse or touch.

## Repository structure

```
.
├── index.html                              Landing page that lists every animation
├── README.md                               This file
├── linear_transformations_activity.html    Linear transformations of the plane
└── euclidean_spaces_interactive.html       Euclidean spaces, seen
```

Each animation is a single, self-contained HTML file (its CSS and JavaScript are inside it). The only external resources are Google Fonts, the IE University logo from `static.ie.edu` and, where needed, KaTeX from `cdnjs.cloudflare.com`.

## Publishing the site

The collection is served with GitHub Pages, so students only need a link.

1. In the repository on GitHub, go to **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to *Deploy from a branch*.
3. Choose the `main` branch and the `/ (root)` folder, then select **Save**.
4. After a minute or two the site is available at `https://<github-username>.github.io/<repository-name>/`. Update the link at the top of this README.

GitHub Pages serves public content. If the repository needs to stay private, check which Pages options your GitHub plan allows for private repositories.

## Adding a new animation

1. **Add the file.** Put the new `.html` file in the root of the repository. Use a descriptive, lowercase name with underscores, such as `eigenvectors_explorer.html`, and keep everything in one file.
2. **List it on the landing page.** Open `index.html`, find the `ANIMATIONS` list near the top of the `<script>` and add an entry:

   ```js
   {
     file: "eigenvectors_explorer.html",          // path to the animation
     title: "Eigenvectors of a 2 × 2 matrix",     // shown as the heading
     course: "linear-algebra",                    // an id from the COURSES list
     summary: "Drag a vector and find the directions that A only stretches.",
     parts: [                                      // optional: tabs or sections
       { name: "Find the eigenvectors", ref: "Notes §5.1" }
     ],
     keywords: "eigenvalue eigenvector characteristic polynomial", // optional: extra search words
     figure: "grid"                                // optional: small drawing on the card
   }
   ```

   Entries are grouped by course in the order of the `COURSES` list. To add a course, add `{ id, name, note }` to `COURSES`. Entries whose course is not in that list appear under “More animations”.

   The `figure` value picks one of the small decorative drawings in the `FIGURES` object (`transform`, `projection` or the plain `grid`). You can add a new drawing there as a fragment of SVG on a 200 × 200 canvas with the origin at (70, 130).

   Set `REPO_URL` in the same script to show a “Source code on GitHub” link in the footer.
3. **Add a row to the table** in the [Animations](#animations) section of this README.
4. **Check it.** Open `index.html` locally, search for the new animation and follow its link.

### Conventions for new animations

The existing animations share a look and a level of accessibility that new ones should keep:

- IE University design tokens: Ocean Blue `#000066` for headings and primary buttons, Montserrat for the interface and PT Serif for explanatory text. The IE University logo is at least 60 px high at the top of the page.
- WCAG 2.1 AA, as required by the European Accessibility Act: text contrast of at least 4.5:1, a visible keyboard focus, labels on every input, nothing communicated by colour alone, and a layout that still works at 200% zoom and 320 px width.
- Light and dark mode through `prefers-color-scheme`, and respect for `prefers-reduced-motion`.
- Notation and section references that follow the course notes.

## Credits

Developed for the Linear Algebra and Geometry courses, School of Science & Technology, IE University.

<!-- Add authors, contact details and a license here, for example:
     Author: Name Surname (name@ie.edu)
     License: CC BY-NC-SA 4.0 -->
