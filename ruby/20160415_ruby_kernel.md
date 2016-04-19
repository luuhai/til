### Ruby's Kernel module

* The `puts` method (and `gets`, `chomp`, `sleep`, `rand`...) is a private method defined on `Kernel` module.
* `Kernel` is mixed into `Object` class, which means all method defined on this module are accesible to all Ruby objects, making them "global" functions.
