# Firefox-Tweaks

Extensions: Download Statusbar, AdBlock Plus, Vimperator.

1.  Open Firefox, and type about:config in the address bar. Don’t worry
    about the warning that comes out.

2.  Use the filter above to find network.http.pipelining and set it to
    True by double clicking on it.

3.  Create a new boolean value named
    network.http.pipelining.firstrequest and set that to True, as well.

4.  Find network.http.pipelining.maxrequests, double click on it, and
    change its value to 8.

5.  Now look for network.http.proxy.pipelining and again set it to True.

6.  Create two new integers named nglayout.initialpaint.delay and
    content.notify.interval, setting them to 0.
