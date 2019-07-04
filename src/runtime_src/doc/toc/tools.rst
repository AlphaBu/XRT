Tools and Utilities
-------------------

xbutil
~~~~~

Xilinx Board Utility Tool

Refer to UG1279 <https://www.xilinx.com/support/documentation/sw_manuals/xilinx2018_3/ug1279-sdx-command-utility-reference-guide.pdf>


xclbinutil
~~~~~

This utility operates on a xclbin produced by xocc.

*Note: Use "-h" option of xclbintil to get help about options.


Usecases
~~~~~~~~

Get info from xclbin file
.........................

Various information can be obtained through the **--info** option, including information on the date, hardware platform, clocks, memory configuration, kernel, and how the xclbin was generated.

* Note: Optionally an output file can be specified.  If none is specified, then the output will go to the console.

**xclbinutil -i binary_container_1.xclbin --info=<FILE_NAME>**


Xclbin metadata controlling
...........................

For example:
  1) Reporting xclbin information  : **xclbinutil --info --input binary_container_1.xclbin**
  2) Extracting the bitstream image: **xclbinutil --dump-section BITSTREAM:RAW:bitstream.bit --input binary_container_1.xclbin**
  3) Extracting the build metadata : **xclbinutil --dump-section BUILD_METADATA:HTML:buildMetadata.json --input binary_container_1.xclbin**
  4) Removing a section            : **xclbinutil --remove-section BITSTREAM --input binary_container_1.xclbin --output binary_container_modified.xclbin**


Digital signature of xclbin to secure download
..............................................

Xclbinutil allow user to add or get signature from xclbin file, or remove signature from xclbin file. The secure download of xclbin is controlled by XRT management driver.

[Internal note: Refer http://jira.xilinx.com/browse/PR-13557]

**xclbinutil --add-signature <...> -i binary_container_1.xclbin -o output.xclbin**

**xclbinutil --get-signature -i output.xclbin**

**xclbinutil --remove-signature -i output.xclbin -o output_nosign.xclbin**


Upgrade xclbin file from older version
......................................

To be compatible with new xclbin.h.

**xclbinutil --migrate-forward -i binary_container_1.xclbin -o output.xclbin**


Assemble xclbin file
....................

Step-wise running of v++, and use xclbinutil to assemble xclbin file. Related commands:

**v++ --list_steps**

**v++ --from_step <...> --to_step <...>**

**xclbinutil <...>**
