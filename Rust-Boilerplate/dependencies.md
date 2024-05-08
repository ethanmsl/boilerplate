[workspace]
members = ["claps", "datapop", "derives"]
resolver = "2"

# [package]
# name = "exemplars"
# version = "0.1.0"
# edition = "2021"


[workspace.dependencies]
# Error Handling
# <see_below>     derive_more::error

# Logging
async-backtrace
# = "0.2.0"  # RUSTFLAGS="--cfg tokio_unstable" -- alteranate tracing subscriber that also works with tokio-console
** console-subscriber
# keep secrets out of logs
** secrecy
** tracing
tracing-appender
tracing-error
tracing-flame
tracing-forest
** tracing-subscriber --features=env-filter,serde,json,chrono,tracing-serde
tracing-timing

# Ergonomics
## Data Structure Behavior
derive_builder
** derive_more
derive-new
educe
strum
variantly
## Struct Populators
** serde --features=derive
serde_json
validator --features=derive,phone

## General Methods
** itertools
tap

# File System
assert_fs
csv
dirs
dotenvy
tempfile
toml
walkdir

# Time
chrono --features=serde,arbitrary
hifitime --features=reqwest,serde

# http
## tokio::semaphore
backon
governor
** reqwest --features=serde_json
** reqwest-retry

# DataFrames
** polars --features=lazy
                ,ndarray,serde,json,docs-selection
## Surreal
# Visualization
plotters

# Parallelism (logical)
** rayon
** tokio --fatures=features,macros,fs,time
        ,sync
        ,full
        ,test-util

# Parsing
logos
regex
winnow --features=debug

# CLI
clap --features=derive,wrap_help
                ,env,unicode,string,debug
dialoguer --features=fuzzy-matcher,fuzzy-select,history,completion
indicatif --features=rayon,tokio

# WASM
egui
** eframe
tracing-wasm

# Math
faer --features=rayon,sere,perf-warn
nalgebra
ndarray --features=rayon,serde,docs,test
petgraph --features=serde,generate,quickcheck,serde_derive
rand --features=serde
raphtory --features=vectors,io,search
rustworkx-core
uom --features=
        serde,
        u8,
        u16,
        u32,
        u64,
        i64,
        complex64,
        rational64,


# Other
** enum_dispatch
** fakeit
** once_cell
** indoc


# [dev-dependencies]
# Testing
arbitrary --features=derive
pretty_assertions 
** quickcheck
** quickcheck_macros
insta --features=
        csv,
        json,
        regex,
        serde,
        toml,
        walkdir,
        yaml,
wiremock

# Profilers
##dhat
##divan
##flamegraph

# for use with "console-subsriber"
[build]
rustflags = ["--cfg", "tokio_unstable"]
