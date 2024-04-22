# Image Preview for Neovim

[DEV FORK - PLEASE USE UPSTREAM](https://github.com/adelarsq/image_preview.nvim)

Neovim plugin for image previews.

Requires one of the following terminals for support:

* [WezTerm](https://wezfurlong.org/wezterm/)
* [Kitty](https://sw.kovidgoyal.net/kitty/)

![image](https://user-images.githubusercontent.com/430272/194723584-3af9e272-b6b9-456a-af88-e1f79e5213e5.png)

## Installing

### Plug

```
Plug 'https://github.com/ejconlon/image_preview.nvim'
```

### Lazy

```lua
{
    'ejconlon/image_preview.nvim',
    event = 'VeryLazy',
    opts = {
        -- These are all optional:
        keybinds = {
            preview = '<Leader>p',
        },
    },
},
```

## Configuration

```lua
opts = {
    keybinds = {
        preview = '<Leader>p',
    },
}

require('image_preview').setup(opts)
```

### neo-tree.nvim

To use on [neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim) it's necessary to add a command on the setup, as shows bellow:

```lua
require("neo-tree").setup({
  filesystem = {
    window = {
      mappings = {
        ["<leader>p"] = "image_wezterm", -- " or another map
      },
    },
    commands = {
      image_wezterm = function(state)
        local node = state.tree:get_node()
        if node.type == "file" then
          require("image_preview").PreviewImage(node.path)
        end
      end,
    },
  },
}
```

Special thanks for @pysan3 for [point that](https://github.com/adelarsq/image_preview.nvim/issues/3#issuecomment-1560816413).

## Keybinds

- `<leader>p` - image preview for file under cursor

## Features

- [x] Terminals:
   - [x] [WezTerm](https://wezfurlong.org/wezterm/)
   - [x] [Kitty](https://sw.kovidgoyal.net/kitty/)
   - [ ] iTerm2
   - [ ] [Alacrity](https://github.com/alacritty/alacritty). Waiting for [pull/4763](https://github.com/alacritty/alacritty/pull/4763)
- [x] Environments:
   - [x] Windows
      - [x] PowerShell - WezTerm
      - [ ] DOS
      - [ ] WSL
   - [x] Linux - WezTerm
   - [x] macOS - WezTerm
- [x] Plugins:
   - [x] [nvim-tree.lua](https://github.com/kyazdani42/nvim-tree.lua)
   - [x] [neo-tree.nvim)](https://github.com/nvim-neo-tree/neo-tree.nvim)
   - [x] [oil.nvim](https://github.com/stevearc/oil.nvim)
   - [ ] NerdTree
- [x] Windows support. Depends on PowerShell
- [x] macOS support
- [x] Linux support
- [x] bmp, png and jpg
- [ ] svg

## Related Plugins

- [samodostal/image.nvim](https://github.com/samodostal/image.nvim)
- [nvim-telescope/telescope-media-files.nvim](https://github.com/nvim-telescope/telescope-media-files.nvim)

