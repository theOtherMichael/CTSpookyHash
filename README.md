# Compile-Time SpookyHash

This is a version of Bob Jenkins' [SpookyHash hashing algorithm](http://burtleburtle.net/bob/hash/spooky.html) that can be evaluated at compile time.  The `Hash128`, `Hash64`, and `Hash32` functions are now all `constexpr` and can be used for things like switch case statements.  This is still a C++ implementation.

CTSpookyHash's output is identical to the original SpookyHash's, and performance is comparable when used in  run-time situations.  Just like the original SpookyHash, this code is in the public domain and can be used unconditionally.

## How to Use

1. Download `CTSpookyHash.h` and `CTSpookyHash.cpp`.
2. Add them to your project.
3. Use `CTSpookyHash::Hash128`, `CTSpookyHash::Hash64` or `CTSpookyHash::Hash32` in your code.
4. Profit.

## Notes

* This is an implementation of SpookyHash V2.
* C++11 is needed for `constexpr`.
* Just like the original SpookyHash, this code is not portable to big-endian processors.
* **SpookyHash is not cryptographic: do not use it in security scenarios.**
* Turning off `ALLOW_UNALIGNED_READS` will make all functions run-time only.
* Only messages that are smaller than 192 bytes (`sc_bufSize`) can be evaluated at compile time.  Larger messages must be hashed at run-time.
* The functions `CTSpookyHash::Init`, `CTSpookyHash::Update` and `CTSpookyHash::Final` are still run-time only.

Bob Jenkins' original version of SpookyHash is available at http://burtleburtle.net/bob/hash/spooky.html.