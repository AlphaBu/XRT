Tools and Utilities
-------------------

xbutil
~~~~~

Xilinx Board Utility Tool



xclbinutil
~~~~~

This utility operates on a xclbin produced by xocc.

For example:
  1) Reporting xclbin information  : **xclbinutil --info --input binary_container_1.xclbin**
  2) Extracting the bitstream image: **xclbinutil --dump-section BITSTREAM:RAW:bitstream.bit --input binary_container_1.xclbin**
  3) Extracting the build metadata : **xclbinutil --dump-section BUILD_METADATA:HTML:buildMetadata.json --input binary_container_1.xclbin**
  4) Removing a section            : **xclbinutil --remove-section BITSTREAM --input binary_container_1.xclbin --output binary_container_modified.xclbin**

Command Line Options

..
  =========================== ===================================================================
  Option                      Description
  =========================== ===================================================================
  -h [ --help ]               Print help messages
  -i [ --input ] arg          Input file name. Reads xclbin into memory.
  -o [ --output ] arg         Output file name. Writes in memory xclbin image to a file.
  -v [ --verbose ]            Display verbose/debug information.
  -q [ --quiet ]              Minimize reporting information.
  --migrate-forward           Migrate the xclbin archive forward to the new binary format.
  --remove-section arg        Section name to remove.
  --add-section arg           Section name to add.  Format: <section>:<format>:<file>
  --dump-section arg          Section to dump. Format: <section>:<format>:<file>
  --replace-section arg       Section to replace.
  --key-value arg             Key value pairs.  Format: [USER|SYS]:<key>:<value>
  --remove-key arg            Removes the given user key from the xclbin archive.
  --add-signature arg         Adds a user defined signature to the given xclbin image.
  --remove-signature          Removes the signature from the xclbin image.
  --get-signature             Returns the user defined signature (if set) of the xclbin image.
  --info [=arg(=<console>)]   Report accelerator binary content.  Including: generation and packaging data, kernel signatures, connectivity, clocks, sections, etc. Note: Optionally an output file can be specified.  If none is specified, then the output will go to the console.
  --list-names                List all possible section names (Stand Alone Option)
  --version                   Version of this executable.
  --force                     Forces a file overwrite.
  =========================== ===================================================================


aaa

+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| Option                    | Description                                                                                                                             |
+===========================+=========================================================================================================================================+
| -h [ --help ]             | Print help messages                                                                                                                     |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| -i [ --input ] arg        | Input file name. Reads xclbin into memory.                                                                                              |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| -o [ --output ] arg       |    Output file name. Writes in memory xclbin image to a file.                                                                           |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| -v [ --verbose ]          |    Display verbose/debug information.                                                                                                   |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| -q [ --quiet ]            |    Minimize reporting information.                                                                                                      |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --migrate-forward         |    Migrate the xclbin archive forward to the new binary format.                                                                         |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --remove-section arg      |    Section name to remove.                                                                                                              |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --add-section arg         |    Section name to add.  Format: <section>:<format>:<file>                                                                              |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --dump-section arg        |    Section to dump. Format: <section>:<format>:<file>                                                                                   |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --replace-section arg     |    Section to replace.                                                                                                                  |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --key-value arg           |    Key value pairs.  Format: [USER|SYS]:<key>:<value>                                                                                   |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --remove-key arg          |    Removes the given user key from the xclbin archive.                                                                                  |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --add-signature arg       |    Adds a user defined signature to the given xclbin image.                                                                             |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --remove-signature        |    Removes the signature from the xclbin image.                                                                                         |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --get-signature           |    Returns the user defined signature (if set) of the xclbin image.                                                                     |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --info [=arg(=<console>)] |    Report accelerator binary content. Including: generation and packaging data, kernel signatures, connectivity, clocks, sections, etc. |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --list-names              |    List all possible section names (Stand Alone Option)                                                                                 |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --version                 |    Version of this executable.                                                                                                          |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| --force                   |    Forces a file overwrite.                                                                                                             |
+---------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+





  Note: Optionally an output file can be specified.  If none is specified, then the output will go to the console.



Addition Syntax Information

* Syntax: <section>:<format>:<file>

  * <section> - The section to add or dump (e.g., BUILD_METADATA, BITSTREAM, etc.) Note: If a JSON format is being used, this value can be empty.  If so, then the JSON metadata will determine the section it is associated with. In addition, only sections that are found in the JSON file will be reported.

  * <format>  - The format to be used.  Currently, there are three formats available: RAW: Binary Image; JSON: JSON file format; and HTML: Browser visible. Note: Only selected operations and sections supports these file types.

  * <file>    - The name of the input/output file to use.

  Used By: --add_section and --dump_section

  Example: xclbinutil --add-section BITSTREAM:RAW:mybitstream.bit


For most users, the contents and how the xclbin was created is desired. This information can be obtained through the --info option and reports information on the xclbin, hardware platform, clocks, memory configuration, kernel, and how the xclbin was generated.

**xclbinutil -i binary_container_1.xclbin --info**
