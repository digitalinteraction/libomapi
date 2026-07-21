# libomapi

Open Movement API library: *OMAPI*, natively:

* [C language](src) (builds to a static, or dynamic library)

...this repository includes language bindings for:

* [C#/.NET](bindings/csharp)
* [Java](bindings/java)
* [JavaScript Node FFI](bindings/node-ffi) & [JavaScript Node NAPI](bindings/node-napi)
* [Python](bindings/python-untested) (untested)
* [Rust](bindings/rust-untested) (untested)

...and there are external bindings for:

* [R](https://axr.circadia-lab.uk/) (from [circadia-lab.uk](https://axr.circadia-lab.uk/))

See also:

* [Documentation for libOMAPI](https://openmovement.dev/omapi/html/)
* [AX Device Technical Documentation](https://github.com/digitalinteraction/openmovement/blob/master/Docs/ax3/ax3-technical.md)
* [AX Research: Data Analysis](https://github.com/digitalinteraction/openmovement/blob/master/Docs/ax3/ax3-research.md#data-analysis)

**Note:** This repository has been split from various parts of the OpenMovement mono-repo, and some inter-library paths may need repairing.

<!--

## Ports

```
# Windows
\\.\COM123
```

```
# Mac OS
/dev/tty.usbserial-*
## ioreg -p IOUSB -l -b | grep -E "@|PortNum|USB Serial Number"
```

```
# Ubuntu 16
/dev/serial/by-id/usb-Newcastle_University_AX3_Composite_Device_1.7_CWA17_22529-if01

/dev/sdb1
/media/$USER/AX317_?????/
```

```
# Raspian
/dev/serial/by-id/usb-Newcastle_University_AX3_Composite_Device_1.7_CWA17_22529-if01
mount /dev/sda1 /mnt/usb
```

---

-->

<!--

gcc -o test -I./include -Dtest_main=main ./examples/test.c -L. -lomapi -ludev -lpthread

-->
