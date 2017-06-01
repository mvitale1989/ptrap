ptrap
=====

Script that lets you find out which process on your system is sending packets to a single `<ip>:<port>`. It supports both TCP/UDP packet monitoring, and the execution of a custom program in response. Depends on `tc`, `ip`, `iptables` and `lsof`.


Examples
--------

    # Monitor DNS requests to host 192.168.1.1 and print out the process tree,
    # highlighting the originating process and his ancestors
    ptrap -u -i 192.168.1.1 -p 53 -e "pstree -p -H"

    # Monitor new connections TCP connections to any port of 192.168.1.1, and
    # print out the originating process' name
    ptrap -t -c -i 192.168.1.1 -e "ps -o comm="


How it works
------------

*TODO*

### Limitations

*TODO*


Future work
-----------

- Drop explicit dependency on `/var/log/message`, implement parsing syslog
  messages from other sources
- Monitor other IP protocols (e.g. icmp)
- Check for existence of other tc rules at launch time, save&restore them
- Concurrent execution of multiple istances of this program
