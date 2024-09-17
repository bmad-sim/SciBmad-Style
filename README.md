# SciBmad-Style
Style/convention rules for SciBmad

1. Type stability as much as possible! Use the macro `@report_opt` in `JET.jl` to aid in writing good code
2. Two (2) spaces should be uses for tabs. No tab characters! (in most text editors you can set the tab length to two spaces
3. CamelCase for modules and structs
4. A file which contains a module should have the file name be the same as the module name: e.g. `Module MyModule` should be in `MyModule.jl`).
5. Non-module files should be snake_case
6. Global constants should be capitalized SNAKE_CASE
7. Longer function names should be snake_case, short ones could go either way (e.g. `set_units!` and `setunits!` are both ok, but `track_a_drift` should be used instead of `trackadrift`)
8. Bang (!) at end of function that mutates any argument per Julia standard
9. For functions with many arguments/keyword arguments, format the arguments like:
```julia
function Coords(n::Integer;
                d_x::Distribution=Normal(0,0), d_px::Distribution=Normal(0,0), 
                d_y::Distribution=Normal(0,0), d_py::Distribution=Normal(0,0), 
                d_z::Distribution=Normal(0,0), d_pz::Distribution=Normal(0,0) )

  # stuff
end
 ```
10. In struct definitions, use concrete-types as much as possible, and try to opt for parametric types if not fully possible. E.g. instead of `AbstractString`, use `String` and for `TPS` which could represent `Float64` or `ComplexF64`, using `TPS{Float64}` and `TPS{ComplexF64}` (parametric types) instead of two separate types
11. Avoid specifying types as much as possible unless that argument _must_ be a specific type. This is for composability with the rest of the Julia environment. Type-stable functions will then incur no cost. E.g., `AbstractString` should be used instead of `String` for function arguments (e.g. `function foo(mystring::AbstractString)` instead of `function foo(mystring::String)`
12. All exports should be included at the top of the main package file in the module. See `GTPSA.jl` for an example
13. File names should concisely represent what's in those files. E.g. a file containing all type definitions might be called `types.jl`, and a file containing all constructors for a type `Type` might be `type_ctors.jl` or just `ctors.jl`. Directory structure could be good too, `type/ctors.jl`
