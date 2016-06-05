# cases16-benchmarks

Benchmark suite used in our paper *'Speculative Disassembly of Binary Code'* which was accepted for CASES'16. Folder structure is as follows:
  - [Coremark Pro] - benchmarks were compiled using `arm-linux-gnueabihf-gcc-5.1`.
  - [Coreutils] - benchmarks were compiled using `arm-linux-gnueabihf-gcc-4.8`.

Both benchmark suites were compiled with optimization level `-O3`. Binaries contain symbol information. You might want to try `spedi` on a stripped version of the binaries.

# Usage

To easily reproduce our results you need to compile [Spedi] and feed it a binary. The following command will instruct `spedi`to speculatively disassemble the `.text` ELF section,

```sh
$ ./spedi -t -s -f $FILE > speculative.inst
```
Use the following command to instruct `spedi` to disassemble the `.text` section based on ARM code mapping symbols which provides the ground truth about correct instructions,

```sh
$ ./spedi -t -f $FILE > correct.inst
```
The easiest way to compare both outputs is by using, 

```sh
$ diff -y correct.inst speculative.inst |less
```
# License
Public domain.

   [Spedi]: <https://github.com/abenkhadra/spedi>
   [Coremark Pro]: <http://www.eembc.org/coremark/about.php?b=pro>
   [Coreutils]: <http://www.gnu.org/software/coreutils/coreutils.html>
 

