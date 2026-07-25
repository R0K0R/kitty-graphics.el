# Kitty Graphics markdown test

Manual test for the markdown-mode integration.  Enable
`kitty-graphics-mode', then `M-x markdown-toggle-inline-images'
to render images, same command again to hide.

## Test inline images

Here is an inline image:

![img](test-image.png)

Some text after the image to verify overlay positioning.

## Subheading images (PR #43 repro)

### Plotting

![Plotting](./assets/test-image.png)

### Perlin Noise

![Perlin Noise](assets/test-image.png)

Expected: both images render directly below their headings.

## Hidden markup test

![img](test-image.png)

Steps: with images displayed, `C-c C-x C-m'
(`markdown-toggle-markup-hiding'), then toggle it back.
Expected: the image renders with markup hidden and with markup
shown.  markdown-mode marks all link markup with
`invisible=markdown-markup' — cosmetic hiding, must not be
treated as folding.

## Folded section test

![img](assets/test-image.png)

Steps: point on this heading, TAB (`markdown-cycle') to fold the
section, S-TAB to unfold everything.
Expected: no image while folded, image re-rendered after
unfolding.

## Commented image test

<!-- ![img](test-image.png) -->

Expected: no image and no reserved space — links inside HTML
comments are skipped.

## Relative path test

![img](./test-image.png)

![img](assets/test-image.png)

## Another section

This section has no images, just text to test scrolling behavior.

Line 1 Line 2 Line 3 Line 4 Line 5 Line 6 Line 7 Line 8 Line 9 Line 10

## LaTeX fragment preview test

Inline math: $E = mc^2$

Display math:

\begin{equation}
\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
\end{equation}

Another inline: $\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$

End of test file.
