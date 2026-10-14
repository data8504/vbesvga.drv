# Assembled-code regression tests

Build the drivers using the DDK procedures in the main README and retain their
matching linker maps. Tests require Python 3, `capstone` and `unicorn`:

```
python3 tests/test_service_dispatch.py --binary /path/to/VDDVBE.386 --map /path/to/VDDVGA.MAP
python3 tests/test_exclusion.py --binary /path/to/VBESVGA.DRV --map /path/to/VBESVGA.MAP
```

The tests execute instructions from your built binaries. The dispatcher test
models a successful VMM validation call at its OS boundary and checks valid
service destinations and invalid full-width service numbers. The exclusion
tests check acquired/unacquired cleanup branches and the Polyline stack-failure
exit. They do not emulate the VMM or GDI, or replace runtime application testing.
No proprietary binaries, DDK tools or Windows installation are needed to run
them once the drivers and matching maps have been built.
