# Rust, Tokio, Axum, and Tauri

**Recommended alternative** for native services, desktop shells, command-line tools, multimedia pipelines, and performance-sensitive components where memory safety, predictable resource use, and small distributable binaries matter.

## Learn the language and toolchain

- [The Rust Programming Language](https://doc.rust-lang.org/book/)
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/)
- [The Cargo Book](https://doc.rust-lang.org/cargo/)
- [rustup](https://rust-lang.github.io/rustup/)
- [Clippy](https://doc.rust-lang.org/clippy/)
- [rustfmt](https://github.com/rust-lang/rustfmt)

Use `cargo fmt`, `cargo clippy`, and `cargo test` as baseline CI checks.

## Async and APIs

- [Tokio tutorial](https://tokio.rs/tokio/tutorial)
- [Axum documentation](https://docs.rs/axum/latest/axum/)
- [Tower](https://docs.rs/tower/latest/tower/)
- [Serde](https://serde.rs/)

Use Axum when building HTTP services on the Tokio ecosystem. Keep handlers thin, centralize application state deliberately, and use Tower middleware for cross-cutting HTTP behavior.

## Data

- [SQLx](https://docs.rs/sqlx/latest/sqlx/)
- [SeaORM](https://www.sea-ql.org/SeaORM/)
- [Diesel](https://diesel.rs/)

Preferred starting point: SQLx when explicit SQL and compile-time query checking fit the application. Consider an ORM only when its abstraction materially reduces complexity.

## Desktop and native application shell

- [Tauri v2](https://v2.tauri.app/start/)
- [Tauri security](https://v2.tauri.app/security/)
- [Tauri plugins](https://v2.tauri.app/plugin/)

Tauri is the preferred web-frontend + native-shell route in this handbook. Keep its command surface narrow and expose only the native capabilities the frontend actually requires.

## CLI applications

- [clap](https://docs.rs/clap/latest/clap/)
- [indicatif](https://docs.rs/indicatif/latest/indicatif/)
- [tracing](https://docs.rs/tracing/latest/tracing/)

## Testing and quality

- [Rust testing](https://doc.rust-lang.org/book/ch11-00-testing.html)
- [cargo-nextest](https://nexte.st/)
- [criterion.rs](https://bheisler.github.io/criterion.rs/book/)

Benchmark only code paths with a performance requirement. Avoid using microbenchmarks as a substitute for measuring complete system behavior.

## Multimedia and systems integration

- [FFmpeg documentation](https://ffmpeg.org/documentation.html)
- [GStreamer Rust bindings](https://gstreamer.freedesktop.org/documentation/rust/stable/latest/docs/gstreamer/)
- [OpenCV Rust bindings](https://github.com/twistedfall/opencv-rust)

Prefer invoking a stable command-line boundary when it keeps FFmpeg integration simpler and more maintainable than binding directly to native libraries.

## When not to choose this route

Do not choose Rust merely for theoretical performance. Prefer .NET or Python when delivery speed, team familiarity, libraries, and operational consistency matter more than native control. Introduce Rust at a bounded component boundary when its advantages are measurable.
