# glob

`glob` is an adaptation of Go's `path.Match` that is not specific to paths. `*`
will match any sequence of characters _including_ `/` and `?` will match any
character _including_ `/`.

Go's `path.Match` is significantly faster than existing Go `glob`
implementations (as well as `regexp`) if your usage pattern is to match against
a glob pattern once and then discard it (as opposed to matching against a glob
pattern many times in a tight loop):

```
# This package
BenchmarkMatch-8               2000000         297 ns/op         0 B/op         0 allocs/op

# Others
BenchmarkParseGlob-8            100000       14979 ns/op      5488 B/op       166 allocs/op
BenchmarkParseRegexp-8          200000        6752 ns/op      8024 B/op        61 allocs/op
BenchmarkAllGlobMatch-8       10000000         223 ns/op         0 B/op         0 allocs/op
BenchmarkAllRegexpMatch-8      1000000        1444 ns/op         0 B/op         0 allocs/op
```

For more information about `path.Match`'s algorithm: https://research.swtch.com/glob

# Original License

```
Copyright (c) 2009 The Go Authors. All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

   * Redistributions of source code must retain the above copyright
notice, this list of conditions and the following disclaimer.
   * Redistributions in binary form must reproduce the above
copyright notice, this list of conditions and the following disclaimer
in the documentation and/or other materials provided with the
distribution.
   * Neither the name of Google Inc. nor the names of its
contributors may be used to endorse or promote products derived from
this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```
