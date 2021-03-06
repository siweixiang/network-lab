Lab with Juniper vMX and full views
===================================

Each vMX will receive a eBGP fullview. This needs
[gobgp](https://github.com/osrg/gobgp) and an MRT dumpfile.

Due to the memory needed for a full view, this lab is not really using
a full view. Have a look at `./setup` and search for `start_gobgp` to
see what part of the full view is used.

There is also a tentative to not install all routes in FIB. vMX1 and
vMX2 are not using the same method to do so: vMX1 tries to use the
state of the default route (but this doesn't work). vMX2 only
discriminates on specific route attributes. You can look at the FIB
with `show route forwarding-table`.

MRT dump
--------

To get one, use:

    wget http://data.ris.ripe.net/rrc00/latest-bview.gz

gobgp
-----

Just use the following commands:

    export GOPATH=$TMP/gopath
    go get github.com/osrg/gobgp
    go get github.com/osrg/gobgpd
    ln -s $GOPATH/bin/gobgp
    ln -s $GOPATH/bin/gobgpd
