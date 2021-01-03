# cargo.el

Cargo mode for Emacs. This package gives you a set of key combinations to perform Cargo tasks within your Rust projects.

## NOTICE

Currently I'm not using Rust, nor will I in the (near) future. I've lost track
of all the Rust / Cargo features available and can't keep up-to-date with new
ones. I'll be doing selective bug fixes and continue reviewing / merging pull
requests.

## Installation

This package can be installed through [melpa](https://melpa.org/):

```
M-x package-install cargo
```

## Usage

Add cargo-minor-mode to your rust-mode-hook

```el
(add-hook 'rust-mode-hook 'cargo-minor-mode)
```

You will now have the following key combinations at your disposal:

 Keybinding             | Command
------------------------|----------------------
 <kbd>C-c d e</kbd>     |  cargo-process-bench
 <kbd>C-c d b</kbd>     |  cargo-process-build
 <kbd>C-c d l</kbd>     |  cargo-process-clean
 <kbd>C-c d d</kbd>     |  cargo-process-doc
 <kbd>C-c d v</kbd>     |  cargo-process-doc-open
 <kbd>C-c d n</kbd>     |  cargo-process-new
 <kbd>C-c d i</kbd>     |  cargo-process-init
 <kbd>C-c d r</kbd>     |  cargo-process-run
 <kbd>C-c d x</kbd>     |  cargo-process-run-example
 <kbd>C-c d s</kbd>     |  cargo-process-search
 <kbd>C-c d t</kbd>     |  cargo-process-test
 <kbd>C-c d u</kbd>     |  cargo-process-update
 <kbd>C-c d c</kbd>     |  cargo-process-repeat
 <kbd>C-c d f</kbd>     |  cargo-process-current-test
 <kbd>C-c d o</kbd>     |  cargo-process-current-file-tests
 <kbd>C-c d q</kbd>     |  cargo-process-outdated
 <kbd>C-c d m</kbd>     |  cargo-process-fmt
 <kbd>C-c d k</kbd>     |  cargo-process-check
 <kbd>C-c d z</kbd>     |  cargo-process-clippy
 <kbd>C-c d a</kbd>     |  cargo-process-add
 <kbd>C-c d w</kbd>     |  cargo-process-rm
 <kbd>C-c d g</kbd>     |  cargo-process-upgrade
 <kbd>C-c d y</kbd>     |  cargo-process-audit

Before executing the task, Emacs will prompt you to save any modified buffers
associated with the current Cargo project. Setting `compilation-ask-about-save`
to `nil` makes Emacs save modified buffers without asking.

To change prefix (default <kbd>C-c</kbd>) use:

```el
 (define-key cargo-mode-map (kbd ...) 'cargo-minor-mode-command-map)
```

## Variables

Commands can be adjusted by changing their command variable.
Here's a list of commands and their default value.

```el
(setq cargo-process--command-bench "bench")
(setq cargo-process--command-build "build")
(setq cargo-process--command-clean "clean")
(setq cargo-process--command-doc "doc")
(setq cargo-process--command-doc-open "doc --open")
(setq cargo-process--command-new "new")
(setq cargo-process--command-init "init")
(setq cargo-process--command-run "run")
(setq cargo-process--command-run-bin "run --bin")
(setq cargo-process--command-run-example "run --example")
(setq cargo-process--command-search "search")
(setq cargo-process--command-test "test")
(setq cargo-process--command-current-test "test")
(setq cargo-process--command-current-file-tests "test")
(setq cargo-process--command-update "update")
(setq cargo-process--command-fmt "fmt")
(setq cargo-process--command-check "check")
(setq cargo-process--command-clippy "clippy")
(setq cargo-process--command-add "add")
(setq cargo-process--command-rm "rm")
(setq cargo-process--command-upgrade "upgrade")
(setq cargo-process--command-audit "audit -f")
```

### Advanced usage

If you invoke the prefix argument <kbd>C-u</kbd> before calling any of
the functions, you may edit the Cargo command before it is run. This
allows you to add flags like `--release`, for example.

Processes run via Cargo mode make use of [compilation mode][]. This
mode provides features like jumping to errors or killing runaway
processes. By default, in `compilation mode`, <kbd>C-c C-k</kbd> is bound
to the command `kill-compilation`.

[compilation mode]: https://www.gnu.org/software/emacs/manual/html_node/emacs/Compilation-Mode.html

## Notes

In order to run `cargo-process-fmt` you need to have the `rustfmt` package installed.

```
rustup component add rustfmt-preview
```

In order to run `cargo-process-check` you need to have the `cargo-check` package installed.

```
cargo install cargo-check
```

In order to run `cargo-process-clippy` you need to have the `clippy` package installed.

```
cargo install clippy
```

In order to run `cargo-process-{add,rm,upgrade}` you need to have the `cargo-edit` package installed.

```
cargo install cargo-edit
```
For completion in `cargo-process-add`, configure `cargo-process-favorite-crates`.

In order to run `cargo-process-audit` you need to have the `audit` package installed.

```
cargo install cargo-audit
```
