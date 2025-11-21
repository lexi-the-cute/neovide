# Commands

On startup, Neovide registers some commands for interacting
with the os and platform window. These are neovim commands
accessible via `:{command name}`.

## Register/Unregister Right Click

On windows you can register a right click context menu item
to edit a given file with Neovide. This can be done at any
time by running the `NeovideRegisterRightClick` command. This can
be undone with the `NeovideUnregisterRightClick` command.

## Focus Window

Running the `NeovideFocus` command will bring the platform
window containing Neovide to the front and activate it. This
is useful for tools like neovim_remote which can manipulate
neovim remotely or if long running tasks would like to
activate the Neovide window after finishing.

## Force Click (macOS)

On macOS, `:NeovideForceClick` triggers native force-click behaviours for whatever is under the
cursor. Plain text falls back to the usual “Look Up” popover; file paths open in the Quick Look
panel; URLs open in the system browser unless you enable
`g:neovide_force_click_url_preview` (see [Configuration](configuration.md#force-click-url-preview-macos-only)),
which makes them use Quick Look as well. Trackpad force presses call this command automatically,
and you can bind it manually if you want to trigger it from another input.

Mouse button:

```lua
vim.keymap.set("n", "<X1Mouse>", "<Cmd>NeovideForceClick<CR>", { silent = true })
```

Keyboard shortcut:

```lua
vim.keymap.set("n", "<leader>k", "<Cmd>NeovideForceClick<CR>", { silent = true })
```

Vimscript equivalents:

```vim
nnoremap <silent> <X1Mouse> :NeovideForceClick<CR>
nnoremap <silent> <leader>k :NeovideForceClick<CR>
```

## Open Config File (Unreleased yet)

Running the `NeovideConfig` command will open your Neovide
configuration file for editing. This provides a simple and
discoverable way to access your settings without needing to
know the platform-specific path to the file.
