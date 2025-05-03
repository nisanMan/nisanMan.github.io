---
title: Responsive Image Mode Home.html
date: 2025-05-03 10:00:00 +0300
categories: [Frontend, Jekyll]
tags: [liquid, html, class, yaml , mode]
render_with_liquid: false
description: "Display different images for light and dark mode using  .light and .dark classes. Works in the Home Page with Liquid."
light_image:
  path: /assets/img/images/day.webp
  lqip: data:image/webp;base64,UklGRqwAAABXRUJQVlA4IKAAAACQBACdASoUAAsAPm0skUWkIqGYBABABsSgCdMoMYLIBz/4DyTRxuxtCmrX1tAA/vCna/G73GB/pdnY23pAwkfN000+WuZqOShq506oqkTq6B/WyM6y4fROrbeQTEG/ZXL11T/NxBGfrgDG/gRJu7uea2fl6Bxti34BAId/CcH6gqQKaKtRFTIkrj+MonK/xkeDaU+gFDjptzhdEYHmGAAA
  alt: Image for Light Mode
dark_image:
  path: /assets/img/images/night.webp
  lqip: data:image/webp;base64,UklGRmwAAABXRUJQVlA4IGAAAADwAwCdASoUAAsAPm0sk0YkIqGhMAgAgA2JZwC7AB6JBTrfhf+C2KAoAP7vL1DW/2ltDbPwtjdiDYlS8QDKhV8vmF2YOkU5Vl+Pklg/xfHbTJI6tw+qO2aOZEqSTM6gAAA=
  alt: Image for Dark Mode
---

![Light mode only](/assets/img/images/day.webp){: .light }
![Dark mode only](/assets/img/images/night.webp){: .dark }

# 🖼️ Feature: Dynamic Post Image Light/Dark Mode Switching

## 1. YAML Front Matter Configuration
Add the following fields to the post's YAML front matter:

```yaml
light_image:
  path: /path/to/light-image.webp
  lqip: data:image/webp;base64,...
  alt: Alt text for light mode image
dark_image:
  path: /path/to/dark-image.webp
  lqip: data:image/webp;base64,...
  alt: Alt text for dark mode image
```
## 2.Layout Update

Inside the `_layouts` in `home.html`, within the `{% if post.image %}` block, insert the following code **after** `{% assign card_body_col = '7' %}` and **before** `{% endif %}`.

```liquid
    {% elsif post.light_image and post.dark_image %}
      <div class="col-md-5">
        <div class="preview-img  blur">
          <img
            data-src="{{ post.light_image.path }}"
            alt="{{ post.light_image.alt}}"
            data-lqip="true"
            src="{{ post.light_image.lqip }}"
            class="popup img-link light shimmer"
            loading="lazy"
          >
          <img
            data-src="{{ post.dark_image.path }}"
            alt="{{ post.dark_image.alt}}"
            data-lqip="true"
            src="{{ post.dark_image.lqip }}"
            class="popup img-link dark"
            loading="lazy"
          >
        </div>
      </div>

      {% assign card_body_col = '7' %}
    {% endif %}
```

### At the beginning of the post, use:

```markdown
![Light mode only](/path/to/light-image.webp){: .light }
![Dark mode only](/path/to/dark-image.webp){: .dark }
```

>Images can be PNG, not just WebP.
>Currently, this requires Liquid.
>If needed, it can be added in `home.html`.
{: .prompt-info }
