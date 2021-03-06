# pyoutline

A python tracing decorator that times code and outlines nested calls showing args and results.

## Usage

Put ``@timed`` as a decorator before methods you want to time.
Then run your code with and environment variable TIMED containing
a regex which matches the ClassName.MethodName of the methods you
want to show timing for.  

The envar ``TIME_QUIETLY`` turns off lines like:

    pyoutline.timed() will time: function.get_frame_in_kb


## Example

    $ TIMED=.* python myscript.py
    TIMING:    20100505121116                 /-------------------- OnSaleThisWeek.run_when_store_object_recreated()
    TIMING:    20100505121116                 | /-------------------- ProductInStore.set_on_special_price_using_directive('20%')
    TIMED:     20100505121116        0.04 sec | \-------------------- ProductInStore.set_on_special_price_using_directive(...) ===>  None
    TIMED:     20100505121116        0.05 sec \-------------------- OnSaleThisWeek.run_when_store_object_recreated( [] ) ===>  None
    TIMING:    20100505121116                 /-------------------- OnSaleThisWeek.run_when_store_object_recreated()
    TIMING:    20100505121116                 | /-------------------- ProductInStore.set_on_special_price_using_directive('30%')
    TIMED:     20100505121116        0.04 sec | \-------------------- ProductInStore.set_on_special_price_using_directive(...) ===>  None
    TIMED:     20100505121116        0.05 sec \-------------------- OnSaleThisWeek.run_when_store_object_recreated( [] ) ===>  None

    $ TIMED=.*using.* python myscript.py
    TIMING:    20100505121116                 /-------------------- ProductInStore.set_on_special_price_using_directive('20%')
    TIMED:     20100505121116        0.04 sec \-------------------- ProductInStore.set_on_special_price_using_directive(...) ===>  None
    TIMING:    20100505121116                 /-------------------- ProductInStore.set_on_special_price_using_directive('30%')
    TIMED:     20100505121116        0.04 sec \-------------------- ProductInStore.set_on_special_price_using_directive(...) ===>  None

## Notes

Why call it ``pyoutline``?  To give it a unique name by playing on the synonym relationship 
with ``trace``, which is a more natural name for this kind of utility.

Just putting this up so I don't misplace it again!  Needs major cleanup.
