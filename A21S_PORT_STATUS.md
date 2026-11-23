# A21s Linux 5.10 port status (not flashable)

Source: mustvfa/android_kernel_samsung_exynos850 (4.19.325)
Target: Rakesh3464/android_kernel_samsung_exynos850-5.10 (5.10.274)

Verified from uploaded GitHub Actions inventory archives:
- Reference defconfig: arch/arm64/configs/exynos850-a21snsxx_defconfig
- Target defconfig: arch/arm64/configs/exynos850-a12snsxx_defconfig
- Reference board DTS: arch/arm64/boot/dts/samsung/a21s/a21s_eur_open_w00_r{00,01,02,03,06}.dts
- Target board DTS includes arch/arm64/boot/dts/samsung/a12s/a12s_eur_open_w00_r00.dts and r01.
- Target SoC DTS: arch/arm64/boot/dts/exynos/s5e3830.dts

## Porting gates
1. Audit full reference and target config symbol differences; only enable options whose drivers exist in 5.10.
2. Compare board DTS includes, bindings, regulators, pinctrl, clocks, panel, touch, camera, storage, and modem; rewrite to match 5.10 binding/driver interfaces.
3. Update DTS Makefiles and DTBO rules only after identifying supported board revisions and compatible strings.
4. Compile Image and DTBs with a verified A21s defconfig. Resolve compiler, dtc and runtime dependencies.
5. Repack against the *matching A21s stock boot image*, preserving header version, page size, cmdline, ramdisk and partition size constraints.
6. Verify with device boot logs and hardware testing before declaring flash-ready.

Do not copy 4.19 drivers or DTS blindly into 5.10. This document is a source audit, not a working kernel or boot image.
