- Panoptisch scans your #Python file or module to find it's imports (aka dependencies) and recursively does so for all dependencies and sub-dependencies. It then generates a dependency tree in JSON for you to parse and enforce  import policies. Imports are resolved by mimicing Python's import system. It's completely static besides the importing of modules to find the location of its source file(s).
- https://github.com/R9295/panoptisch
-