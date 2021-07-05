# cuckoohash

Hash map implementation using [cuckoo hashing](https://en.wikipedia.org/wiki/Cuckoo_hashing).


## Test

This project supports the Fortran package manager ([fpm](https://github.com/fortran-lang/fpm)) as build system.
To run the testsuite use

```
fpm test
```


## Usage

To use this map in your project add `cuckoohash` as dependency to your package manifest.

```toml
[dependencies]
cuckoohash.git = "https://github.com/awvwgk/cuckoohash"
```

The `map_cuckoohash` module becomes available and the `cuckoo_hash` type can be imported.

```f90
program demo_map
   use map_cuckoohash, only : cuckoo_hash, container_type, len
   implicit none
   type(cuckoo_hash) :: map
   type(container_type), pointer :: view

   map = cuckoo_hash()

   call map%insert("real-value", view)
   view%val = 1.0

   call map%insert("int-value", view)
   view%val = 42

   call map%get("real-value", view)
   select type(val => view%val)
   type is (real)
      print *, val
   end select

   call map%drop("int-value")

end program demo_map
```


## License

Licensed under the Apache License, Version 2.0 (the “License”);
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an *“as is” basis*,
*without warranties or conditions of any kind*, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

Unless you explicitly state otherwise, any contribution intentionally
submitted for inclusion in this project by you, as defined in the
Apache-2.0 license, shall be licensed as above, without any additional
terms or conditions.
