# 0x0Test: a MiniScript / GreyScript testing library

This project aims to provide developers with the ability to write simple and maintainable
tests that can be ran on-demand during the development cycle.

<img alt="gh_test_library" src="https://github.com/user-attachments/assets/9578d14e-56fc-4c8c-b698-c07c8f160375" />

## Requirements

This project requires that you use the extension Greybel VS (`ayecue.greybel-vs`).

If you're savvy enough you may be able to get this working with just the `build/test.src`.

## How do I use this for my project?

Include this repository or `build/test.src` into your own project.

For good results, ensure the scripts you're testing don't automatically execute anything.

If this is unclear, look at how the examples are constructed (in `examples/` folder)

```
#import test from ../../src/test.src
#include number_incrementor.src

test("Number Incrementor").expect("Adds 1 to 0 equals 1").is = function(assert)
    assert.equals(number_incrementor(0), 1)
end function
test("Number Incrementor").expect("Adds 1 to string equals null").is = function(assert)
    assert.equals(number_incrementor("invalid"), null)
end function
test("Test Library").expect("FAIL with custom message").is = function(assert)
    assert.equals(true, false, "Custom error")
end function
test("Test Library").expect("FAIL").is = function(assert)
    assert.equals(true, false)
end function
test()
```

outputs (when ran)

```
Number Incrementor
  Adds 1 to 0 equals 1...[PASSED]
  Adds 1 to string equals null...[PASSED]
Test Library
  FAIL with custom message...[FAILED]
    (failed_assertion): Custom error
  FAIL...[FAILED]
    (failed_assertion): Asserting 1 equals 0.
```

## Why not just use [MiniTest](https://github.com/Olipro/MiniTest)?

I'm actively encouraging you to use [MiniTest](https://github.com/Olipro/MiniTest).

This testing library is a fun project idea of mine to use in my own tools. I've got
nothing against MiniTest at all. It's way more portable than this project, and is more
likely than not more performant.
