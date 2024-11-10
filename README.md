## Links

* Crates.io: https://crates.io/crates/egui-themes
* docs.rs: https://docs.rs/egui-themes
* Github: https://github.com/Resonanz/egui-themes

# egui-themes
Super-simple color theming for egui.

If dependencies in ```Cargo.toml``` need updating, or you have suggestions for improvements, please submit an issue on Github.

## Purpose

This crate provides super simple theming capability for egui projects.

The current theme colors are taken from Catppuccin (https://crates.io/keywords/catppuccin).

Additional color themes may be added. Please submit your own and I may incorporate them into this crate.

## Usage

In ```Cargo.toml``` add the following dependency:

```
[dependencies]
egui-themes = 0.1.0  <--- The latest version number can be found on Crates.io.
```

Or you could use the following if developing locally:
```
[dependencies]
egui-themes = { path = "/Github/egui-themes/" }
```

Import the crate using:

```use egui_themes::{StateMachine, MOCHA};```

### The following asumes you are using eframe_template:

Using the ```TemplateApp``` struct, define a ```run_once``` boolean and a ```StateMachine``` variable to hold the current theme:

```
pub struct TemplateApp {
    run_once: bool,
    my_theme: StateMachine,
}

impl Default for TemplateApp {
    fn default() -> Self {
        Self {
            run_once: false,
            my_theme: egui_themes::StateMachine::new(),
        }
    }
}
```

Inside ```fn update...``` set the startup theme state using the ```run_once``` boolean:

```
fn update(&mut self, ctx: &Context, _frame: &mut eframe::Frame) {
    /* ========================= Run once ======================== */
    if self.run_once == false {
        self.run_once = true;
        self.my_theme.set_theme(ctx, &MOCHA);
    }
    /* =========================================================== */
```


## Video
https://github.com/user-attachments/assets/ddcfce39-8377-440f-bce6-b98e7945c441
