# Known issues and upstream status

Last updated: 2026-11-12. Facts only; each statement is dated or tied to a recorded check.

## Maintenance policy

This fork is kept compatible with the **newest ELRepo `kernel-ml`** on EL10. A scheduled check run on the maintainer's
own server (not a workflow of this repository) builds `main` against the latest `kernel-ml-devel` and records the result.
Compile checks are clean (two toolchain warnings) on kernel-ml 7.2.8 and 7.2.13, and, since release `5.12.5.2-fork.2`,
on **7.3.4**. See [VALIDATION.md](VALIDATION.md) for what was only compiled and what was boot-tested.

## Upstream / distribution status

| Item | Status (2026-11-12) |
|---|---|
| In-kernel `rtw88_8821au` in ELRepo `kernel-ml` | **Present as a module in kernel-ml 7.3.1 and 7.3.4** (`CONFIG_RTW88_8821AU=m`); **not present in 7.2.8** (`# CONFIG_RTW88_8821AU is not set`). See [ELRepo bug 0001612](https://elrepo.org/bugs/view.php?id=1612). |
| `kmod-rtw88_usb` (ELRepo) | Reported by the ELRepo maintainers (2026-10-28) as available for the **stock EL10 kernel** (not for `kernel-ml`); includes RTW88_8821AU/8821CU/8812AU/8814AU/8822CU. Not re-verified since. |
| This fork on `kernel-ml` | Works as an out-of-tree DKMS module. On kernel 7.3 and newer, **prefer the in-kernel driver where it works for you**; this fork stays maintained for 7.2.x and older kernels and as a fallback. |

## Known issues

- **5 GHz DHCP lease loss observed on kernel 7.2.13 (not on 7.2.8)**; see [issue 6](https://github.com/BenkiNew/8821au-maintained/issues/6).
  One boot per kernel version, not isolated to the driver versus the kernel or network stack; no claim of causality. Reports from other setups are welcome.
- **7.3.x is compile-tested only** for this fork (no boot test); see [VALIDATION.md](VALIDATION.md).

## How this file is maintained

Updated when ELRepo publishes a kernel-ml that changes the driver availability, or when a new reproducible problem is confirmed.
