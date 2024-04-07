# AMD Radeon F32 Processor Module for Ghidra

Based on the information in [radeon-tools][radeon-tools] and [this
presentation][33c3].

**NOTE**: This is a work-in-progress, and is largely unfinished. Because of
this, any aspect of this plugin could change at any time. Consider yourself
warned!

To do:

* Verify that the disassembly output matches that generated by `f32dis.py`.
* Refactor instruction decoding since it's kind of a mess right now.
* Add semantics for push/pop instructions to make the stack work.
* Handle memory accesses to the different memory spaces (define custom
  operations?).
* Add file loader to automatically identify old-style vs. new-style firmware
  images, and load without/with a 0x100 offset and with big-endian/little-endian
  instructions accordingly.
* Enable the file loader to add labels for the branch addresses listed in the
  table at the end of the firmware image.
* Adjust calling convention to match observed calling convention.
* Confirm instruction semantics on real hardware (how?).
* Confirm the register sizes and 32-bit/64-bit behavior.
  * Maybe it would be better to use register aliasing with separate, aliased
    register names for 32/64-bit operations?
* Confirm memory byte ordering.


## Build and Install

```
$ git clone https://github.com/cyrozap/ghidra-radeon-f32.git
$ cd ghidra-radeon-f32
$ gradle
```

The `dist` directory will now contain the extension zip file that you can
install into Ghidra.


[radeon-tools]: https://github.com/fail0verflow/radeon-tools
[33c3]: https://media.ccc.de/v/33c3-7946-console_hacking_2016#t=1914