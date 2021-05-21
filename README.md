[![Made with Doom Emacs](https://img.shields.io/badge/Made_with-Doom_Emacs-blueviolet.svg?style=flat-square&logo=GNU%20Emacs&logoColor=white)](https://github.com/hlissner/doom-emacs)
![Release tag](https://img.shields.io/github/tag/hlissner/emacs-solaire-mode.svg?label=release&style=flat-square)
[![MIT](https://img.shields.io/badge/license-MIT-green.svg)](./LICENSE)
[![MELPA](http://melpa.org/packages/solaire-mode-badge.svg)](http://melpa.org/#/solaire-mode)

# Solaire mode

If only certain buffers could be so grossly incandescent.

<a href="https://winkla12.deviantart.com/art/Grossly-Incandescent-438305072">
  <img src="/../screenshots/praise.jpg" width="100%" />
</a>

`solaire-mode` is an aesthetic plugin that helps visually distinguish
file-visiting windows from other types of windows (like popups or sidebars) by
giving them a slightly different -- often brighter -- background.

Praise the sun.

**Note:**
+ Uses `face-remapping-alist`, which other plugins may overwrite.
+ Tested mainly on Emacs 25.1+
+ This was once a part of [doom-themes] as `doom-buffer-mode`
+ Try jumping.

## Screenshot

![solaire-mode at work](/../screenshots/screenshot.png)

## Install

Solaire-mode is available on MELPA: `M-x package-install RET solaire-mode`

### Doom Emacs

Doom installs this package as part of the `:ui doom` module. No additional
configuration is needed.


## Configuration

Activate `solaire-global-mode` _before_ you load your theme.

```emacs-lisp
(solaire-global-mode +1)
```

Here are some example `use-package` configs for `solaire-mode`:

```emacs-lisp
;; A simple config:
(use-package solaire-mode
  :config (solaire-global-mode +1))
```

### Doom Emacs

Doom users only need to enable its `:ui doom` module. It installs and configures solaire-mode for you; no additional work needed!


## Configuration
+ By default, `solaire-mode`'s effects will be invisible. Its faces must be
  defined:

  + `solaire-default-face`
  + `solaire-minibuffer-face`
  + `solaire-line-number-face`
  + `solaire-hl-line-face`
  + `solaire-org-hide-face`
  + `solaire-mode-line-face`
  + `solaire-mode-line-inactive-face`

+ What faces get remapped is controlled by `solaire-mode-remap-faces` and
  `solaire-mode-remap-modeline`.

  By default, these faces are affected:

  + `default`
  + `hl-line`
  + `linum`
  + `org-hide`
  + `mode-line`
  + `mode-line-inactive`

+ The function in `solaire-mode-real-buffer-fn` determines if a buffer should be
  brightened or not.

+ `solaire-mode-remap-fringe` controls whether the fringe's background is
  changed (and maintained) when solaire-mode is active. Setting it to `nil` will
  disable this behavior. To change what background it is changed to, modify the
  `solaire-fringe-face` face's `:background`.

## Themes that support solaire-mode out of the box
  The only (known) themes to support solaire-mode are:

  + [doom-themes]
  + [spacemacs-theme]
  + [wilmersdorf-theme]
  + [modus-themes]

## Jolly cooperation with other plugins
+ By default, `solaire-mode` remaps the mode-line faces. This interferes with
  certain mode-line packages like telephone-line or powerline, but works fine
  for doom-modeline. To disable this behavior use:

  ```emacs-lisp
  (setq solaire-mode-remap-modeline nil)
  ```
+ When `persp-mode` loads a perspective from file, it doesn't restore
  solaire-mode. The function `solaire-mode-restore-persp-mode-buffers` is
  available for this:

  ```emacs-lisp
  (advice-add #'persp-load-state-from-file :after #'solaire-mode-restore-persp-mode-buffers)
  ```
+ Don't trust Patches!


[doom-themes]: https://github.com/hlissner/emacs-doom-themes
[spacemacs-theme]: https://github.com/nashamri/spacemacs-theme
[wilmersdorf-theme]: https://github.com/ianpan870102/wilmersdorf-emacs-theme
[modus-themes]: https://gitlab.com/protesilaos/modus-themes
