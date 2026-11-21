<img src="assets/logo.png" width="112" height="112" alt="TickStep logo">

# TickStep

Choose a covering linear tick lattice using steps 1, 2, 5 or 10 times a power of ten. This Blyx library is part of the numerics and visualization collection.

A constant series collapses a chart axis; raw decimal steps make labels hard to read. Expand the domain before choosing a tick lattice. [D3, ticks and steps](https://d3js.org/d3-array/ticks)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.1 https://github.com/Rahulchaube1/blyx-tickstep.git
cd blyx-tickstep
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-tickstep) · [Package page](https://www.blyx-lang.space/packages/tickstep) · [Handbook](https://doc.blyx-lang.space/guide/flamingo)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.1 https://github.com/Rahulchaube1/blyx-tickstep.git vendor/tickstep
```

```blyx
use vendor::tickstep::tickstep;

fn main() {
    let lo = -3.0;
    let hi = 11.0;
    let intervals = 4.0;
    let result = tickstep_cover(lo, hi, intervals);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
-5
15
5
5
```

## API

`tickstep_cover(lo, hi, intervals)`

Returns [first tick, last tick, step, tick count]. Interval count is a target. Supported raw steps range from 1e-100 to 1e100. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| lo | A finite number |
| hi | A finite number |
| intervals | A positive exact integer |

## In use

[Flamingo](https://github.com/Rahulchaube1/blyx-flamingo) uses this module to produce chart-ready axis limits and labeled tick spacing from raw data.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-tickstep/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
