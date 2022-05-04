**************
Numba
**************

It puts some decorators on top of the **python function** and makes it a lot faster.

Numba has few decorators:

* ``@jit``

* ``@njit``, it is the go-to decorator which is also the alias for ``@jit(nopython=True)``.

* ``@vectorize``: produces NumPy ``ufunc``

* ``@guvectorize``: produces general NumPy ``ufunc``

* ``@stencil``: declare a function as a kernel for stencil like operations

* ``@jitclass``: for jit classes

* ``@cfun``: declare a function for use as a native call back (from C/C++)

* ``@overload``: register your own implementation of a function for use in nopython mode, e.g. ``@overload(scipy.special.j0)``

Some extra options available in some decorators:

* ``parallel = True``: enables the automatic parallelization of the function
* ``fastmath = True``: enable fast-math behavior for the function.
  
