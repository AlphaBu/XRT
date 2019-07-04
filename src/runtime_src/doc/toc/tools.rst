Tools and Utilities
-------------------

xbutil
~~~~~

Xilinx Board Utility Tool



xclbinutil
~~~~~

This utility operates on a xclbin produced by xocc.

*Note: Use "-h" option of xclbintil to get help about options.


Usecases:

1. For most users, the contents and how the xclbin was created is desired. This information can be obtained through the **--info** option and reports information on the xclbin, hardware platform, clocks, memory configuration, kernel, and how the xclbin was generated.

* Note: Optionally an output file can be specified.  If none is specified, then the output will go to the console.

**xclbinutil -i binary_container_1.xclbin --info=<FILE_NAME>**


2. Xclbin metadata controlling.
For example:
  1) Reporting xclbin information  : **xclbinutil --info --input binary_container_1.xclbin**
  2) Extracting the bitstream image: **xclbinutil --dump-section BITSTREAM:RAW:bitstream.bit --input binary_container_1.xclbin**
  3) Extracting the build metadata : **xclbinutil --dump-section BUILD_METADATA:HTML:buildMetadata.json --input binary_container_1.xclbin**
  4) Removing a section            : **xclbinutil --remove-section BITSTREAM --input binary_container_1.xclbin --output binary_container_modified.xclbin**


3. Digital signature of xclbin to secure download. Xclbinutil allow user to add or get signature from xclbin file, or remove signature from xclbin file. The secure download of xclbin is controlled by XRT management driver.

[Internal note: Refer http://jira.xilinx.com/browse/PR-13557]

**xclbinutil --add-signature <...> -i binary_container_1.xclbin -o output.xclbin**

**xclbinutil --get-signature -i output.xclbin**

**xclbinutil --remove-signature -i output.xclbin -o output_nosign.xclbin**

4. Upgrade xclbin file from older version  (compatible with new xclbin.h).

**xclbinutil --migrate-forward -i binary_container_1.xclbin -o output.xclbin**

5. Step-wise running of v++, and use xclbinutil to assemble xclbin file. Related commands:

**v++ --list_steps**

**v++ --from_step <...> --to_step <...>**

**xclbinutil <...>**
