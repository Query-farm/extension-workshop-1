---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: title.png
# some information about your slides (markdown enabled)
title: DuckDB Extension Workshop
info: |
  ## Learn how to build a DuckDB Extension
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: fade
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# duration of the presentation
duration: 2hrs
# addons
addons:
  - slidev-addon-excalidraw
---

<div class="flex flex-col items-center justify-center">
  <h1 class="title-text !text-6xl !font-bold !tracking-tight !leading-tight">
    DuckDB Extension Workshop
  </h1>

  <p class="subtitle-text text-2xl mt-4 font-medium tracking-wide">
    Learn how to build database extensions
  </p>

  <div class="mt-14 flex items-center gap-10 text-lg metadata-row">
    <div class="flex items-center gap-2">
      <carbon:calendar class="text-yellow-300" />
      <span>January 30, 2026</span>
    </div>
    <div class="flex items-center gap-2">
      <carbon:user class="text-yellow-300" />
      <span>Rusty Conover</span>
    </div>
    <a href="https://query.farm" class="flex items-center gap-2 hover:text-yellow-300 transition-colors">
      <carbon:link class="text-yellow-300" />
      <span>Query.Farm</span>
    </a>
  </div>
</div>

<div class="abs-bl m-8 text-sm hint-text">
  Press <kbd class="px-2 py-1 bg-black/40 rounded text-xs border border-white/20">Space</kbd> to continue
</div>

<style>
.title-text {
  color: #fff;
  text-shadow:
    0 2px 4px rgba(0,0,0,0.8),
    0 4px 20px rgba(0,0,0,0.6);
}

.subtitle-text {
  color: #fff;
  text-shadow:
    0 2px 4px rgba(0,0,0,0.9),
    0 4px 12px rgba(0,0,0,0.7);
}

.metadata-row {
  color: #fff;
  text-shadow: 0 2px 8px rgba(0,0,0,0.9);
}

.hint-text {
  color: rgba(255,255,255,0.8);
  text-shadow: 0 1px 4px rgba(0,0,0,0.8);
}
</style>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
class: px-16 py-12
---

# Workshop Agenda

<div class="grid grid-cols-2 gap-20 mt-10">
  <div>
    <h3 class="!text-yellow-500 !text-xl !font-semibold !mb-6 !border-b !border-yellow-600/40 !pb-2">Part 1 — Foundations</h3>
    <div class="space-y-5">
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-yellow-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:user-multiple class="text-yellow-500 text-lg" />
        </div>
        <span class="text-lg">Introductions</span>
      </div>
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-yellow-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:flow class="text-yellow-500 text-lg" />
        </div>
        <span class="text-lg">The Lifecycle of a SQL Query</span>
      </div>
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-yellow-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:data-structured class="text-yellow-500 text-lg" />
        </div>
        <span class="text-lg">LogicalTypes, Vectors & DataChunks</span>
      </div>
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-yellow-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:function class="text-yellow-500 text-lg" />
        </div>
        <span class="text-lg">Scalar Functions</span>
      </div>
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-yellow-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:test-tool class="text-yellow-500 text-lg" />
        </div>
        <span class="text-lg">Testing</span>
      </div>
    </div>
  </div>

  <div>
    <h3 class="!text-green-500 !text-xl !font-semibold !mb-6 !border-b !border-green-600/40 !pb-2">Part 2 — Deep Dive</h3>
    <div class="space-y-5">
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-green-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:table class="text-green-500 text-lg" />
        </div>
        <span class="text-lg">Table Functions</span>
      </div>
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-green-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:cloud-upload class="text-green-500 text-lg" />
        </div>
        <span class="text-lg">Publishing</span>
      </div>
      <div class="flex items-center gap-4">
        <div class="w-9 h-9 rounded-lg bg-green-700/20 flex items-center justify-center flex-shrink-0">
          <carbon:help class="text-green-500 text-lg" />
        </div>
        <span class="text-lg">Questions and Answers</span>
      </div>
    </div>
  </div>
</div>

---

# Hi, I’m Rusty 👋
## 🇺🇸 🇺🇳 🕊 𓍝 🗽

**Builder in the DuckDB ecosystem**

- 🚜 ~30 DuckDB extensions in ~2 years
  → via founding **[Query.Farm](https://query.farm)**
- 🐣 First DuckDB GitHub issue: **2021-12-01** (#2663)
- 🎓 B.S. Computer Science — *Montana State University*
- ⏱ Contributed the **ETA prediction** in the DuckDB CLI (v1.4)

**Background**

- 📍 US East Coast: NYC · NJ · Miami · Savannah · now Richmond (VA)
- 📈 Quant finance (last decade):
  *Two Sigma · J.P. Morgan Chase · Schonfeld*

**Things I ❤️ working with**

- DuckDB · Apache Arrow · Python · SQL · C++ · Typescript · Julia · Prolog · Perl · LLMs · ☁️

---

# The Lifecycle of a SQL Query

<p class="text-gray-400 mb-4">Extensions can hook into each phase of query execution. Simplified for scalar and table functions.</p>

<div class="grid grid-cols-6 gap-3">
  <div class="p-4 rounded-lg bg-blue-500/20 border-t-4 border-blue-500">
    <p class="font-bold text-blue-400 text-lg h-7">Parse</p>
    <p class="text-sm text-gray-400 h-10">SQL → AST</p>
    <p class="text-sm text-blue-300">Extend parser (PEG), handle parse errors.</p>
  </div>
  <div class="p-4 rounded-lg bg-cyan-500/20 border-t-4 border-cyan-500">
    <p class="font-bold text-cyan-400 text-lg h-7">Bind</p>
    <p class="text-sm text-gray-400 h-10">Resolve names and types.</p>
    <p class="text-sm text-cyan-300"><tt>ANY types</tt>, parameter folding.</p>
  </div>
  <div class="p-4 rounded-lg bg-green-500/20 border-t-4 border-green-500">
    <p class="font-bold text-green-400 text-lg h-7">Optimize</p>
    <p class="text-sm text-gray-400 h-10">Rewrite plan</p>
    <p class="text-sm text-green-300">Custom optimizers</p>
  </div>
  <div class="p-4 rounded-lg bg-yellow-500/20 border-t-4 border-yellow-500">
    <p class="font-bold text-yellow-400 text-lg h-7">Init Global</p>
    <p class="text-sm text-gray-400 h-10">One-time setup</p>
    <p class="text-sm text-yellow-300">Shared state</p>
  </div>
  <div class="p-4 rounded-lg bg-orange-500/20 border-t-4 border-orange-500">
    <p class="font-bold text-orange-400 text-lg h-7">Init Local</p>
    <p class="text-sm text-gray-400 h-10">Per-thread</p>
    <p class="text-sm text-orange-300">Thread-local state</p>
  </div>
  <div class="p-4 rounded-lg bg-red-500/20 border-t-4 border-red-500">
    <p class="font-bold text-red-400 text-lg h-7">Execute</p>
    <p class="text-sm text-gray-400 h-10">Run operators</p>
    <p class="text-sm text-red-300">Produce results</p>
  </div>
</div>

<div class="flex items-center justify-center mt-4 text-gray-500 text-2xl">
  <span class="text-blue-400">●</span><span class="mx-1">→</span>
  <span class="text-cyan-400">●</span><span class="mx-1">→</span>
  <span class="text-green-400">●</span><span class="mx-1">→</span>
  <span class="text-yellow-400">●</span><span class="mx-1">→</span>
  <span class="text-orange-400">●</span><span class="mx-1">→</span>
  <span class="text-red-400">●</span>
</div>


---
transition: slide-up
class: px-16
---

# Follow Along

<p class="text-3xl text-gray-200 leading-relaxed mt-8 mb-12">Clone the workshop repository to get started.</p>

<div class="flex items-center gap-3 text-xl text-gray-400 mb-4">
<carbon:terminal class="text-green-500 text-2xl" />
<span>Clone the repository</span>
</div>

```bash
git clone --recursive https://github.com/Query-farm/workshop-1.git
```

<a href="https://github.com/Query-farm/workshop-1" target="_blank" class="inline-flex items-center gap-3 text-xl text-gray-400 hover:text-yellow-400 transition-colors mt-10">
<carbon:logo-github class="text-3xl" />
<span>Query-farm/workshop-1</span>
<carbon:arrow-up-right class="text-lg" />
</a>

<style>
.slidev-code, .shiki, pre code {
  font-size: 1.125rem !important;
  line-height: 1.75 !important;
}
</style>


---
class: px-12
---

# Extension Project Structure

<div class="grid grid-cols-2 gap-12 mt-6">
<div>

<p class="text-sm text-green-400 uppercase tracking-wide mb-3 font-semibold">Source Code</p>
<div class="space-y-3 text-lg">
  <div class="flex items-center gap-3 p-3 rounded-lg bg-green-500/15 border-l-4 border-green-500">
    <carbon:code class="text-green-400 text-2xl flex-shrink-0" />
    <div><span class="font-bold text-green-300">src/workshop_extension.cpp</span></div>
  </div>
  <div class="flex items-center gap-3 p-3 rounded-lg bg-green-500/15 border-l-4 border-green-500">
    <carbon:code class="text-green-400 text-2xl flex-shrink-0" />
    <div><span class="font-bold text-green-300">src/include/workshop_extension.hpp</span></div>
  </div>
</div>

<p class="text-sm text-purple-400 uppercase tracking-wide mb-3 mt-6 font-semibold">Tests</p>
<div class="space-y-3 text-lg">
  <div class="flex items-center gap-3 p-3 rounded-lg bg-purple-500/15 border-l-4 border-purple-500">
    <carbon:test-tool class="text-purple-400 text-2xl flex-shrink-0" />
    <div><span class="font-bold text-purple-300">test/sql/workshop.test</span></div>
  </div>
</div>

</div>
<div>

<p class="text-sm text-yellow-400 uppercase tracking-wide mb-3 font-semibold">Build Configuration</p>
<div class="space-y-2 text-base">
  <div class="flex items-center gap-3 p-2 rounded bg-yellow-500/10 border-l-4 border-yellow-500">
    <carbon:settings class="text-yellow-500 text-xl flex-shrink-0" />
    <div><span class="font-semibold text-yellow-400">CMakeLists.txt</span></div>
  </div>
  <div class="flex items-center gap-3 p-2 rounded bg-yellow-500/10 border-l-4 border-yellow-500">
    <carbon:settings class="text-yellow-500 text-xl flex-shrink-0" />
    <div><span class="font-semibold text-yellow-400">extension_config.cmake</span></div>
  </div>
  <div class="flex items-center gap-3 p-2 rounded bg-yellow-500/10 border-l-4 border-yellow-500">
    <carbon:settings class="text-yellow-500 text-xl flex-shrink-0" />
    <div><span class="font-semibold text-yellow-400">Makefile</span></div>
  </div>
  <div class="flex items-center gap-3 p-2 rounded bg-blue-500/10 border-l-4 border-blue-500">
    <carbon:package class="text-blue-400 text-xl flex-shrink-0" />
    <div><span class="font-semibold text-blue-400">vcpkg.json</span></div>
  </div>
</div>

<p class="text-sm text-gray-400 uppercase tracking-wide mb-3 mt-6 font-semibold">Documentation</p>
<div class="space-y-2 text-base">
  <div class="flex items-center gap-3 p-2 rounded bg-gray-500/10 border-l-4 border-gray-500">
    <carbon:document class="text-gray-400 text-xl flex-shrink-0" />
    <div><span class="font-semibold text-gray-300">docs/README.md</span></div>
  </div>
  <div class="flex items-center gap-3 p-2 rounded bg-gray-500/10 border-l-4 border-gray-500">
    <carbon:license class="text-gray-400 text-xl flex-shrink-0" />
    <div><span class="font-semibold text-gray-300">LICENSE</span></div>
  </div>
</div>

</div>
</div>

---
mdc: true
---

# Empty Extension

Run: ```git checkout step-1```

```c {14-18|7-10|3-5}{lines:true,startLine:1}
namespace duckdb {

  static void LoadInternal(ExtensionLoader &loader) {
    // Build your extension here.
  }

  void WorkshopExtension::Load(ExtensionLoader &loader) {
    LoadInternal(loader);
  }

  ...
} // namespace duckdb

extern "C" {
  DUCKDB_CPP_EXTENSION_ENTRY(workshop, loader) {
	  duckdb::LoadInternal(loader);
  }
}
```

<!-- Footer -->

Build with `GEN=ninja make debug`. Test with `./build/debug/duckdb`

<!-- Inline style -->
<style>
.footnotes-sep {
  @apply mt-5 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>


---

# What is the date of Easter for a particular year?

```sql
SELECT range, easter(range) AS easter_date FROM range(1980, 1990);

┌───────┬─────────────┐
│ range │ easter_date │
│ int64 │    date     │
├───────┼─────────────┤
│  1980 │ 1980-04-06  │
│  1981 │ 1981-04-19  │
│  1982 │ 1982-04-11  │
│  1983 │ 1983-04-03  │
│  1984 │ 1984-04-22  │
│  1985 │ 1985-04-07  │
│  1986 │ 1986-03-30  │
│  1987 │ 1987-04-19  │
│  1988 │ 1988-04-03  │
│  1989 │ 1989-03-26  │
├───────┴─────────────┤
│ 10 rows   2 columns │
└─────────────────────┘
```

---

# Scalar Functions

Produce a single value from inputs.  The `easter()` function takes a year and produces a date.

### Vectorized Execution

DuckDB processes data in **vectors**, not individual values.

$$\underbrace{f(x, y, z) \rightarrow r}_{\text{scalar: called n times}} \quad \longrightarrow \quad \underbrace{f(\vec{X}, \vec{Y}, \vec{Z}) \rightarrow \vec{R}}_{\text{vectorized: called once}}$$

Instead of calling your function once per row, DuckDB calls it once per **batch of rows**.

---

# Getting inside of DuckDB

Extensions interact with classes and types internal to DuckDB so you need to know some details.

Building my understanding of these classes has taken the most amount of time.

<div class="flex flex-col items-center">

<Excalidraw
  drawFilePath="./duckdb-type-coverage.excalidraw"
  class="w-[500px]"
  :darkMode="false"
  :background="false"
/>

</div>

---
layout: center
---


<div class="flex flex-col items-center">

# `LogicalType`

<Excalidraw
  drawFilePath="./duckdb-logical-type.excalidraw"
  class="w-[800px]"
  :darkMode="false"
  :background="false"
/>

</div>

---
layout: center
---


<div class="flex flex-col items-center">

# `Value`, `Vector` and `string_t`

<Excalidraw
  drawFilePath="./duckdb-value.excalidraw"
  class="w-[800px]"
  :darkMode="false"
  :background="false"
/>

</div>

---
layout: center
---


<div class="flex flex-col items-center">

# `DataChunk`, Vector Types

<Excalidraw
  drawFilePath="./duckdb-datachunks.excalidraw"
  class="w-[800px]"
  :darkMode="false"
  :background="false"
/>

</div>

---

# Calculating the Date of Easter

````md magic-move {lines: true}
```c {*}
static void LoadInternal(ExtensionLoader &loader) {
  // Build your extension here.
}
```

```c {10-20|13|14-16|17|18|1-8|2|3-7|3|4-7}{lines:true}
void EasterScalarFunc(DataChunk &args, ExpressionState &state, Vector &result) {
	auto &year_vector = args.data[0];
	UnaryExecutor::Execute<int64_t, date_t>
    (year_vector, result, args.size(), [&](int64_t year) {
          // Omitted code calculating the date of Easter.
		  return duckdb::Date::FromDate(year, month, day);
	});
}

static void LoadInternal(ExtensionLoader &loader) {
	loader.RegisterFunction(
      ScalarFunction(
        "easter",
        {
            LogicalType::BIGINT
        },
        LogicalType::DATE,
        EasterScalarFunc)
    );
}
```
````

---

# Update to step-2

If you're following along, update to the `step-2` `git` tag and build.

```sh
GEN=ninja make debug
./build/debug/duckdb
```

```
DuckDB v1.5.0-dev5760 (Development Version, 3f41e38ba7)
Enter ".help" for usage hints.
SELECT easter(3000);
```

---

# Vector Executors

<p class="text-xl text-gray-300 mb-6">Templated helpers that handle the complexity of vectorized execution for you.</p>

<div class="grid grid-cols-3 gap-6 mt-4">
  <div class="p-4 rounded-lg bg-blue-500/10 border border-blue-500/30">
    <p class="text-blue-400 font-bold text-lg mb-2">UnaryExecutor</p>
    <p class="text-gray-400 text-sm">1 input → 1 output</p>
    <p class="text-gray-500 text-xs mt-2 font-mono">f(x) → y</p>
  </div>
  <div class="p-4 rounded-lg bg-green-500/10 border border-green-500/30">
    <p class="text-green-400 font-bold text-lg mb-2">BinaryExecutor</p>
    <p class="text-gray-400 text-sm">2 inputs → 1 output</p>
    <p class="text-gray-500 text-xs mt-2 font-mono">f(x, y) → z</p>
  </div>
  <div class="p-4 rounded-lg bg-purple-500/10 border border-purple-500/30">
    <p class="text-purple-400 font-bold text-lg mb-2">GenericExecutor</p>
    <p class="text-gray-400 text-sm">N inputs → 1 output</p>
    <p class="text-gray-500 text-xs mt-2 font-mono">f(a, b, c, ...) → r</p>
  </div>
</div>

<div class="mt-8 text-base text-gray-300">

**They handle for you:** `SelectionVector` filtering, `ConstantVector` optimization, NULL propagation

**You write:** a simple lambda using C++ primitives (`int64_t`, `double`, `string_t`)

</div>

---

# Documenting Functions

If your function's not well documented it won't be called.

DuckDB offers a rich interface for documenting functions.

```sql
SELECT * FROM duckdb_functions() WHERE function_name = 'easter';
```
```
     schema_name = main
   function_name = easter
        alias_of = NULL
   function_type = scalar
     description = Calculates the date of Easter Sunday for a given year using
                   the Anonymous Gregorian algorithm. Valid for years between
                   1583 and 4098 (Gregorian calendar era).
         comment = NULL
            tags = {}
     return_type = DATE
      parameters = [year]
 parameter_types = [BIGINT]
has_side_effects = false
        examples = ['easter(2025)']
       stability = CONSISTENT
      categories = [date]
```

---

# Adding Documentation for `easter()`

````md magic-move {lines: true}
```c {*}
static void LoadInternal(ExtensionLoader &loader) {
	loader.RegisterFunction(
      ScalarFunction(
        "easter",
        {
            LogicalType::BIGINT
        },
        LogicalType::DATE,
        EasterScalarFunc)
    );
}
```

```c
static void LoadInternal(ExtensionLoader &loader) {
	ScalarFunction easter_func("easter", {LogicalType::BIGINT}, LogicalType::DATE, EasterScalarFunc);

	CreateScalarFunctionInfo easter_info(easter_func);
	FunctionDescription easter_desc;
	easter_desc.description =
	    "Calculates the date of Easter Sunday for a given year using the Anonymous Gregorian algorithm. "
	    "Valid for years between 1583 and 4098 (Gregorian calendar era).";
	easter_desc.examples = {"easter(2025)"};
	easter_desc.categories = {"date"};
	easter_desc.parameter_names = {"year"};
	easter_info.descriptions.push_back(easter_desc);
	loader.RegisterFunction(easter_info);
}
```
````

---

# Update to step-3

If you're following along, update to the `step-3` `git` tag and build.

```sh
GEN=ninja make debug
./build/debug/duckdb
```

```sql
.mode line
SELECT * from duckdb_functions where function_name = 'easter';
```

---

# Testing `easter()`

```sql [workshop.test]{5-9|11-12|14-18}{lines:true,startLine:1}
# name: test/sql/workshop.test
# description: test workshop extension
# group: [sql]

# Before we load the extension, this will fail
statement error
SELECT easter(2024);
----
Catalog Error: Scalar Function with name easter does not exist!

# Require statement will ensure this test is run with this extension loaded
require workshop

# Confirm the extension works
query I
SELECT easter(2026);
----
2026-04-05
```

---

# Testing `easter()` (continued)

```sql [workshop.test]{1|4-16|*}{lines:true,startLine:1}
query II
SELECT year, easter(year) FROM (SELECT * as year FROM range(1980, 2000));
----
1980	1980-04-06
1981	1981-04-19
1982	1982-04-11
1983	1983-04-03
1984	1984-04-22
1985	1985-04-07
1986	1986-03-30
1987	1987-04-19
1988	1988-04-03
1989	1989-03-26
1990	1990-04-15
1991	1991-03-31
1992	1992-04-19
```

---
transition: fade-out
layout: cover
background: take-a-break.png
backgroundColor: rgba(1.0, 0, 0, 0.5)
---

# Time for a Break!

<FlipClock :minutes="10" :seconds="0" />

<div class="mt-6 text-xl opacity-90">

### Remember to talk with the people next to you.
#### Tasks: Restrooms. Build on top of the extension.

</div>


---
transition: fade
---

# Questions and Answers

Questions on material covered so far.

---
transition: slide-up
---

# Common Points of Confusion

*A `ScalarFunction` can have multiple inputs and a single output.*

In C++ use smart pointers `unique_ptr` and `shared_ptr`.

DuckDB provides some classes like `vector` instead of `std::vector`.

Prefer the `debug` build target because it catches more problems early.

Use `lldb` with a breakpoint on the first C++ exception.

Strings are stored using `string_t` rather than `std::string`.  Everything is using UTF-8.

You can fold constant arguments for `ScalarFunction`s in the `bind` phase.

Look into `ScalarFunction`'s `NULL` handling and stability flags.

---
transition: slide-up
---

# Table Functions

Table functions are similar to scalar functions, but they can produce multiple rows.

Table functions finish when they produce a DataChunk that has a cardinality of zero.

We are going to need to use `bind` and `global_init` callbacks so that DuckDB knows the columns we will produce and we can coordinate global state and set the total number of parallel threads to use.

---


# Update to step-4

If you're following along, update to the `step-4` `git` tag and build.

```sh
GEN=ninja make debug
./build/debug/duckdb
```

---

# Table Function Example
We're going to re-implement `range()` called `incremental_sequence()`.

```sql
SELECT * from incremental_sequence(100, 110);
┌────────────────┐
│ sequence_value │
│     int64      │
├────────────────┤
│            100 │
│            101 │
│            102 │
│            103 │
│            104 │
│            105 │
│            106 │
│            107 │
│            108 │
│            109 │
├────────────────┤
│    10 rows     │
└────────────────┘
```

---

# `incremental_sequence()` Implementation
Start by defining the `TableFunction`

```c [workshop_extension.cpp]{1|4-9|5|6|7|8|9|4-11}{lines:true,startLine:1}
static void LoadInternal(ExtensionLoader &loader) {
  ...

	TableFunction incremental_sequence_func(
    "incremental_sequence",
		{LogicalType::BIGINT, LogicalType::BIGINT},
		IncrementalSequenceFunc,
		IncrementalSequenceFuncBind,
		IncrementalSequenceGlobalInit
	);
	loader.RegisterFunction(incremental_sequence_func);
}
```

---

# `incremental_sequence()` Bind Function

```c {10-20|12-13|14-16|17-18|19|1-8|2|3-5}{lines:true,startLine:1}
struct IncrementalSequenceBindData : public FunctionData {
	const int64_t start_value, end_value;
	IncrementalSequenceBindData(int64_t start_value_p, int64_t end_value_p)
	    : start_value(start_value_p), end_value(end_value_p) {
	}
	unique_ptr<FunctionData> Copy() const override { ... }
	bool Equals(const FunctionData &other_p) const override { ... }
};

unique_ptr<FunctionData> IncrementalSequenceFuncBind(ClientContext &context, TableFunctionBindInput &input,
                                                     vector<LogicalType> &return_types, vector<string> &names) {
	int64_t start_value = input.inputs[0].GetValue<int64_t>();
	int64_t end_value = input.inputs[1].GetValue<int64_t>();
	if (end_value < start_value) {
		throw InvalidInputException("End value must be greater than or equal to start value");
	}
	names.push_back("sequence_value");
	return_types.push_back(LogicalType::BIGINT);
	return make_uniq<IncrementalSequenceBindData>(start_value, end_value);
}
```

---

# `incremental_sequence()` Global Init Function

```c {9-15|13|1-7|4-6|2}{lines:true,startLine:1}
struct IncrementalSequenceGlobalState : public GlobalTableFunctionState {
	int64_t current_value;

	idx_t MaxThreads() const override {
		return 1;
	}
};

static unique_ptr<GlobalTableFunctionState> IncrementalSequenceGlobalInit(ClientContext &context,
                                                                          TableFunctionInitInput &input) {
	auto &bind_data = input.bind_data->Cast<IncrementalSequenceBindData>();
	auto state = make_uniq<IncrementalSequenceGlobalState>();
	state->current_value = bind_data.start_value;
	return state;
}
```

---

# `incremental_sequence()` Execution Function

```c {*|2-3|5-8|10-14}{lines:true,startLine:1}
void IncrementalSequenceFunc(ClientContext &context, TableFunctionInput &data, DataChunk &output) {
	auto &bind_data = data.bind_data->Cast<IncrementalSequenceBindData>();
	auto &global_state = data.global_state->Cast<IncrementalSequenceGlobalState>();

	if (global_state.current_value > bind_data.end_value) {
		output.SetCardinality(0);
		return;
	}

	int64_t remaining = bind_data.end_value - global_state.current_value;
	idx_t row_count = MinValue<idx_t>(remaining, STANDARD_VECTOR_SIZE);
	output.SetCardinality(row_count);
	output.data[0].Sequence(global_state.current_value, 1, row_count);
	global_state.current_value += row_count;
}
```

---

# `incremental_sequence()` FlatVector

````md magic-move {lines: true}
```c {13}{lines:true,startLine:1}
void IncrementalSequenceFunc(ClientContext &context, TableFunctionInput &data, DataChunk &output) {
	auto &bind_data = data.bind_data->Cast<IncrementalSequenceBindData>();
	auto &global_state = data.global_state->Cast<IncrementalSequenceGlobalState>();

	if (global_state.current_value > bind_data.end_value) {
		output.SetCardinality(0);
		return;
	}

	int64_t remaining = bind_data.end_value - global_state.current_value;
	idx_t row_count = MinValue<idx_t>(remaining, STANDARD_VECTOR_SIZE);
	output.SetCardinality(row_count);
	output.data[0].Sequence(global_state.current_value, 1, row_count);
	global_state.current_value += row_count;
}
```

```c {13-16}{lines:true,startLine:1}
void IncrementalSequenceFunc(ClientContext &context, TableFunctionInput &data, DataChunk &output) {
	auto &bind_data = data.bind_data->Cast<IncrementalSequenceBindData>();
	auto &global_state = data.global_state->Cast<IncrementalSequenceGlobalState>();

	if (global_state.current_value > bind_data.end_value) {
		output.SetCardinality(0);
		return;
	}

	int64_t remaining = bind_data.end_value - global_state.current_value;
	idx_t row_count = MinValue<idx_t>(remaining, STANDARD_VECTOR_SIZE);
	output.SetCardinality(row_count);
    auto &result = FlatVector::GetData<int64_t>(output.data[0])
    for(idx_t i = 0; i < row_count; i++) {
      result[i] = global_state.current_value + i;
    }
	global_state.current_value += row_count;
}
```
````

---

# `incremental_sequence()` Performance

```sql
EXPLAIN ANALYZE SELECT * FROM incremental_sequence(0, 100000000000);
┌───────────────────────────┐
│         TABLE_SCAN        │
│    ────────────────────   │
│         Function:         │
│    INCREMENTAL_SEQUENCE   │
│                           │
│                           │
│                           │
│    100,000,000,000 rows   │
│           2.58s           │
└───────────────────────────┘
```

---

# Update to step-5

If you're following along, update to the `step-5` `git` tag and build.

```sh
GEN=ninja make debug
./build/debug/duckdb
```

---
transition: slide-up
---

# `incremental_sequence()` Parallelism

Faster performance is possible by using threads.

We will now split the sequence's values up by the number of available threads, `GlobalInit` will now have a queue, and the `LocalInit` data will have the current item of work.

```c [workshop_extension.cpp]{10}{lines:true,startLine:1}
static void LoadInternal(ExtensionLoader &loader) {
  ...

	TableFunction incremental_sequence_func(
    "incremental_sequence",
		{LogicalType::BIGINT, LogicalType::BIGINT},
		IncrementalSequenceFunc,
		IncrementalSequenceFuncBind,
		IncrementalSequenceGlobalInit,
    IncrementalSequenceLocalInit
	);
	loader.RegisterFunction(incremental_sequence_func);
}
```

---

# `incremental_sequence()` Parallelism

Need to enhance the `bind`, `global` and `local` data for assigning work over the sequence

<div class="flex flex-col items-center">

<Excalidraw
  drawFilePath="./duckdb-incremental-sequence-threading-types.excalidraw"
  class="w-[600px]"
  :darkMode="false"
  :background="false"
/>

</div>

---

# `incremental_sequence()` Global State Changes

````md magic-move {lines: true}

```c {*}{lines:true,startLine:1}
struct IncrementalSequenceGlobalState : public GlobalTableFunctionState {
	int64_t current_value;

	idx_t MaxThreads() const override {
		return 1;
	}
};
```

```c {2-3|11-19|4-5|7-9|21-23}{lines:true,startLine:1}
struct IncrementalSequenceGlobalState : public GlobalTableFunctionState {
	std::queue<WorkItem> work_queue;
	std::mutex queue_mutex;
	std::atomic<idx_t> total_rows_returned {0};
	const int64_t total_rows;

	explicit IncrementalSequenceGlobalState(int64_t total_rows) : GlobalTableFunctionState(),
      total_rows(total_rows) {
	}

	bool GetWorkItem(WorkItem &item) {
		std::lock_guard<std::mutex> lock(queue_mutex);
		if (work_queue.empty()) {
			return false;
		}
		item = work_queue.front();
		work_queue.pop();
		return true;
	}

    idx_t MaxThreads() const override {
		return GlobalTableFunctionState::MAX_THREADS;
	}
};
```
````

---

# `incremental_sequence()` `GlobalInit`
The `GlobalInit` class will have a queue of work for threads to execute.

````md magic-move {lines: true}

```c
static unique_ptr<GlobalTableFunctionState> IncrementalSequenceGlobalInit(ClientContext &context,
                                                                          TableFunctionInitInput &input) {
	auto &bind_data = input.bind_data->Cast<IncrementalSequenceBindData>();
	auto state = make_uniq<IncrementalSequenceGlobalState>();
	state->current_value = bind_data.start_value;
	return state;
}
```

```c {3-4|6-8|9-17}{lines:true,startLine:1}
static unique_ptr<GlobalTableFunctionState> IncrementalSequenceGlobalInit(ClientContext &context,
                                                                          TableFunctionInitInput &input) {
	auto &bind_data = input.bind_data->Cast<IncrementalSequenceBindData>();
	auto state = make_uniq<IncrementalSequenceGlobalState>(bind_data.end_value - bind_data.start_value);

	int64_t num_threads = std::min(
        state->total_rows,
        (int64_t)TaskScheduler::GetScheduler(context).NumberOfThreads());
	auto current_start = bind_data.start_value;
	const auto values_per_chunk = state->total_rows / num_threads;
	const auto remainder = state->total_rows % num_threads;

	for (auto i = 0; i < num_threads; i++) {
		auto chunk_size = values_per_chunk + ((i == num_threads - 1) ? remainder : 0);
		state->work_queue.push({current_start, current_start + chunk_size});
		current_start += chunk_size;
	}

	return state;
}
```
````

---

# `incremental_sequence()` Local State
When a thread obtains a work item, it needs to be stored somewhere.

```c {2-4|5|7-10|13-18}{lines:true,startLine:1}
struct IncrementalSequenceLocalState : public LocalTableFunctionState {
	int64_t current_value = 1;
	int64_t end_value = 0;
	bool has_work = false;
	const int64_t thread_id;

	explicit IncrementalSequenceLocalState()
	    : LocalTableFunctionState(), has_work(false),
	      thread_id(std::hash<std::thread::id> {}(std::this_thread::get_id())) {
	}
};

static unique_ptr<LocalTableFunctionState> IncrementalSequenceLocalInit(ExecutionContext &context,
                                                                        TableFunctionInitInput &input,
                                                                        GlobalTableFunctionState *global_state_p) {
	return make_uniq<IncrementalSequenceLocalState>();
}
```

---

# `incremental_sequence()` Execute Function


````md magic-move {lines: true}
```c {*}{lines:true,startLine:1}
void IncrementalSequenceFunc(ClientContext &context, TableFunctionInput &data, DataChunk &output) {
	auto &bind_data = data.bind_data->Cast<IncrementalSequenceBindData>();
	auto &global_state = data.global_state->Cast<IncrementalSequenceGlobalState>();

	if (global_state.current_value > bind_data.end_value) {
		output.SetCardinality(0);
		return;
	}

	int64_t remaining = bind_data.end_value - global_state.current_value;
	idx_t row_count = MinValue<idx_t>(remaining, STANDARD_VECTOR_SIZE);
	output.SetCardinality(row_count);
    output.data[0].Sequence(global_state.current_value, 1, row_count);
	global_state.current_value += row_count;
}
```

```c {2-3|5-15|12-15|17-22|21|23}{lines:true,startLine:1}
void IncrementalSequenceFunc(ClientContext &context, TableFunctionInput &data, DataChunk &output) {
	auto &global_state = data.global_state->Cast<IncrementalSequenceGlobalState>();
	auto &local_state = data.local_state->Cast<IncrementalSequenceLocalState>();

	// Get new work if needed (end_value is exclusive)
	if (local_state.current_value >= local_state.end_value) {
		WorkItem item;
		if (!global_state.GetWorkItem(item)) {
			// No more work available
			output.SetCardinality(0);
			return;
		}
		local_state.current_value = item.start_value;
		local_state.end_value = item.end_value;
	}

	idx_t row_count = MinValue<idx_t>(local_state.end_value - local_state.current_value, STANDARD_VECTOR_SIZE);

	output.SetCardinality(row_count);
	output.data[0].Sequence(local_state.current_value, 1, row_count);
	output.data[1].Reference(Value::UBIGINT(local_state.thread_id));
	local_state.current_value += row_count;
	global_state.total_rows_returned.fetch_add(row_count, std::memory_order_relaxed);
}
```
````

---

# `incremental_sequence()` Progress & Cardinality

```c {7-8|11-17}{lines:true,startLine:1}
double IncrementalSequenceProgress(ClientContext &context, const FunctionData *bind_data_p,
                                   const GlobalTableFunctionState *global_state_p) {
	auto &global_state = global_state_p->Cast<IncrementalSequenceGlobalState>();
	if (global_state.total_rows == 0) {
		return 100.0;
	}
	return static_cast<double>(global_state.total_rows_returned.load(std::memory_order_relaxed)) /
	       static_cast<double>(global_state.total_rows) * 100.0;
}

unique_ptr<NodeStatistics>
IncrementalSequenceCardinality(ClientContext &context,
                               const FunctionData *bind_data_p) {
	auto &bind_data = bind_data_p->Cast<IncrementalSequenceBindData>();

	return make_uniq<NodeStatistics>(static_cast<idx_t>(bind_data.end_value - bind_data.start_value));
}
```

---

# `incremental_sequence()` Bind Changes

```c {10-13}{lines:true,startLine:1}
unique_ptr<FunctionData> IncrementalSequenceFuncBind(ClientContext &context, TableFunctionBindInput &input,
                                                     vector<LogicalType> &return_types, vector<string> &names) {
	int64_t start_value = input.inputs[0].GetValue<int64_t>();
	int64_t end_value = input.inputs[1].GetValue<int64_t>();

	if (end_value < start_value) {
		throw InvalidInputException("End value must be greater than or equal to start value");
	}

	names.push_back("value");
	names.push_back("thread_id");
	return_types.push_back(LogicalType::BIGINT);
	return_types.push_back(LogicalType::UBIGINT);
	return make_uniq<IncrementalSequenceBindData>(start_value, end_value);
}
```

---

# `incremental_sequence()` Threaded Performance
More threads means more throughput.

```sh
./build/release/duckdb -c "set threads=N; select sum(value) from incremental_sequence(0, 10000000000);"
```

| Threads | Real | User | System | Real Speedup |
|--------:|-----:|-----:|-------:|-------:|
| 1 |  8.72 | 8.64 | 0.02 | N/A |
| 2 | 4.58 | 8.91 | 0.03 | 1.9x |
| 4 | 2.42 | 9.26 | 0.04 | 3.6x |
| 8 | 1.75 | 12.66 | 0.04 | 4.9x |

---

# `incremental_sequence()` Work assignments

Even with a `LocalInit` run, you may not get work on that thread.

```sql
 select thread_id, count(*) from incremental_sequence(0, 10000000) group by thread_id;
┌──────────────────────┬──────────────┐
│      thread_id       │ count_star() │
│        uint64        │    int64     │
├──────────────────────┼──────────────┤
│  6950938171802196863 │      1250000 │
│  1343131948544273357 │      1250000 │
│ 13945140530531403299 │      2500000 │
│ 15180026542364114319 │      2500000 │
│ 11674478023736246472 │      2500000 │
└──────────────────────┴──────────────┘
```

---

# `incremental_sequence()` Column Statistics

Telling DuckDB about your result's columns is beneficial.

```c {6-10|12-15}{lines:true,startLine:1}
unique_ptr<BaseStatistics> IncrementalSequenceStatistics(ClientContext &context, const FunctionData *bind_data_ptr,
                                                         column_t column_index) {
	auto &bind_data = bind_data_ptr->Cast<IncrementalSequenceBindData>();

	if (column_index == 0) {
		auto r = NumericStats::CreateEmpty(LogicalType::BIGINT);
		NumericStats::SetMin(r, bind_data.start_value);
		NumericStats::SetMax(r, bind_data.end_value);
		r.SetHasNoNull();
		return r.ToUnique();
	} else if (column_index == 1) {
		auto r = NumericStats::CreateEmpty(LogicalType::UBIGINT);
		r.SetHasNoNull();
		r.SetDistinctCount((int64_t)TaskScheduler::GetScheduler(context).NumberOfThreads());
		return r.ToUnique();
	} else {
		throw InvalidInputException("Unknown column requested for statistics");
	}
}
```

---

# `incremental_sequence()` Column Statistics

Statistics help DuckDB skip work.

```sql
EXPLAIN SELECT * FROM incremental_sequence(100, 200) WHERE value= 50;

┌───────────────────────────┐
│        EMPTY_RESULT       │
└───────────────────────────┘

EXPLAIN SELECT * FROM incremental_sequence(100, 200) WHERE value is null;

┌───────────────────────────┐
│        EMPTY_RESULT       │
└───────────────────────────┘
```

---

# `incremental_sequence()` Column Statistics

Statistics facilitate filter predicate operations (pushdown is for another presentation)

```sql

EXPLAIN SELECT count(*) FROM
  incremental_sequence(0, 1000) a,
  incremental_sequence(500, 10000) b
WHERE a.value = b.value;

...
┌─────────────┴─────────────┐┌─────────────┴─────────────┐
│           FILTER          ││           FILTER          │
│    ────────────────────   ││    ────────────────────   │
│      (value <= 1000)      ││       (value >= 500)      │
│                           ││                           │
│        ~9,500 rows        ││        ~1,000 rows        │
└─────────────┬─────────────┘└─────────────┬─────────────┘
┌─────────────┴─────────────┐┌─────────────┴─────────────┐
│    INCREMENTAL_SEQUENCE   ││    INCREMENTAL_SEQUENCE   │
│    ────────────────────   ││    ────────────────────   │
│         Function:         ││         Function:         │
│    INCREMENTAL_SEQUENCE   ││    INCREMENTAL_SEQUENCE   │
│                           ││                           │
│        ~9,500 rows        ││        ~1,000 rows        │
└───────────────────────────┘└───────────────────────────┘
```

---

# Wrapping Up `TableFunction`

The API for `TableFunction` is much larger than the API for `ScalarFunction`.

Not covered on slides:

- **Projection** - Passing the columns of interest to a TableFunction and only having it produce those columns.
- **Filter pushdown** - Send the filters applied to a table function so it can optimize what data it produces.
- **Filter pruning** - Don't emit columns if the function can filter them.
- **Varargs** - Variable arguments
- **Named Arguments** - Optional named arguments for Table functions.

---
transition: slide-up
---

# Publishing Extensions

It is easy to publish a community extension—just open a PR.

<a href="https://github.com/duckdb/community-extensions" target="_blank" class="inline-flex items-center text-xl text-gray-400 hover:text-yellow-400">
<carbon:logo-github class="text-3xl" />
<span>duckdb/community-extensions</span>
<carbon:arrow-up-right class="text-lg" />
</a>


```yaml [extensions/workshop/description.yaml] {3-11|12-14}{lines:true,startLine:1}
docs:
  extended_description: This is an example extension from the DuckDB extension workshop.
extension:
  build: cmake
  description: Calculates the date of easter and a multithreaded incremental sequence.
  language: C++
  license: Apache-2.0
  maintainers:
  - rustyconover
  name: workshop
  version: '2026012501'
repo:
  github: query-farm/workshop
  ref: abcdefg1234567890
```


---
transition: fade
layout: center
class: text-center
---

# Thank You!

<p class="text-xl text-gray-400 mt-2 mb-10">Questions, comments, or ideas for extensions?</p>

<div class="flex flex-col items-center gap-8">
  <div class="flex items-center gap-4">
    <span class="text-6xl">🚜</span>
    <span class="text-5xl font-bold bg-gradient-to-r from-yellow-400 to-orange-500 bg-clip-text text-transparent">Query.Farm</span>
  </div>

  <p class="text-gray-400 text-lg max-w-lg">Building DuckDB extensions for the community</p>

  <div class="flex items-center gap-10 text-lg">
    <a href="https://query.farm" class="flex items-center gap-2 text-yellow-500 hover:text-yellow-300 transition-colors font-medium">
      <carbon:globe class="text-xl" />
      <span>query.farm</span>
    </a>
    <a href="https://github.com/Query-farm" class="flex items-center gap-2 text-gray-400 hover:text-yellow-400 transition-colors">
      <carbon:logo-github class="text-xl" />
      <span>Query-farm</span>
    </a>
    <a href="mailto:hello@query.farm" class="flex items-center gap-2 text-gray-400 hover:text-yellow-400 transition-colors">
      <carbon:email class="text-xl" />
      <span>hello@query.farm</span>
    </a>
  </div>
</div>

<div class="absolute bottom-8 left-0 right-0 flex justify-between px-12 text-sm text-gray-500">
  <span>Rusty Conover</span>
  <a href="https://github.com/Query-farm/workshop-1" class="text-yellow-600 hover:text-yellow-400">github.com/Query-farm/workshop-1</a>
</div>