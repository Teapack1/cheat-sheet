## Compilation

### Make
Compile software faster by using all CPU cores in parallel. <br>
*-j* - parallel compilation<br>
*$(nproc)* - A bash command substitution that returns the number of CPU cores<br>
*nproc* - command prints the number of available CPU cores<br>
`make -j$(nproc)`

### Build System Components
#### Configure Script:
A shell script that checks your system and prepares the build
Creates a custom Makefile tailored to YOUR system
```
CFLAGS="-O3 -march=native -mtune=native" \
CXXFLAGS="-O3 -march=native -mtune=native" \
./configure \
  --enable-cxx \
  --enable-python \
  --disable-java \
  PYTHON=python3
```
##### a) Compiler Flags:
Instructions that control HOW the compiler works
`CFLAGS="-O3 -march=native -mtune=native"`<br>
*CFLAGS* - Controls the C compiler (gcc) behavior
*CXXFLAGS* - Controls the C++ compiler (g++) behavior
*-03* - Optimization Level 3 (Maximum speed)
```
-O0 = No optimization (fast compile, slow execution)
-O1 = Basic optimization
-O2 = Recommended optimization (default in many projects)
-O3 = Aggressive optimization (slower compile, fastest execution)
```
Use Your CPU's Instruction Set:
`-march=native`<br>
```
-march=x86-64     # Generic x86 64-bit instructions only
-march=native     # Use EVERY feature your specific CPU has
```
Optimize for Your Specific CPU Model:
`-mtune=native`
```
-mtune=generic    # Generic scheduling for all CPUs
-mtune=native     # Optimize for YOUR specific CPU model
```
##### b) Configure Options:
Enable/disable installation of these APIs. app-specific arguments.
Enables building of C++ bindings (for SmuView):
`--enable-cxx`
Enables building of Python bindings (for automation):
`--enable-python`
Disables building of Java bindings (avoid build errors):
`--disable-java`
Tells configure which Python interpreter to use
`PYTHON=python3`



