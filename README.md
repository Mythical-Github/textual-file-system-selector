# Textual File System Selector

This is a generic file system selector screen for textual apps.\
Only tested on Windows 10/11 as of now.

---

## Video Example


---

## Code Example

```python
class SelectGameDirectoryButton(Static):
    def compose(self) -> ComposeResult:
        self.select_game_directory_button = BaseButton(
                button_text="··",
                button_width='6',
                button_border=("none", "black")
            )
        yield self.select_game_directory_button

    def on_mount(self):
        self.styles.width = '6'
        self.select_game_directory_button.styles.padding = 0
        self.select_game_directory_button.styles.margin = 0


    def on_button_pressed(self) -> None:
        from shoal.main_app import app
        app.push_screen(game_directory_screen.SelectionScreen(
            starting_directory='',
            extensions=[],
            selection_filter=SelectionFilter.DIRECTORY,
            cancel_function=cancel_was_hit, 
            confirm_function=confirm_was_hit,
            widgets_to_refresh_on_screen_pop=[app.game_dir_select]
            )
        )
```

---

## Adding to Project Example
```bash
uv add git+https://github.com/Mythical-Github/textual-file-system-selector
```

