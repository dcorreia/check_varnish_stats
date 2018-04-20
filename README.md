Nagios/Icinga perl script to check varnish stats
================================================

Thank you
---------

First of all I want to say thank you to Thomas Weaver.

http://www.toms-blog.com/varnish-nagios-performance-plugin/

This is the base of this check script.

Usage
-----

check_varnish_stats.pl - Monitor and report on varnish usage

check_varnish_stats.pl [-c|--cache] [-b|--bin <varnishstatbinary>]
        [-d|--backend <total|ratio>] [-s|--stats <varnish statfield>]
        [-t|--technique <lt|gt>] [-w|--warning <number>]
        [-c|--critical <number>] [-h|--help]

DESCRIPTION

This script will report on various varnish stats including:
varnish cache hit ratio
backend error count (Total or Ratio)
Any other counter in varnishstat
If no counters are required the script will ensure the varnish binary is running

OPTIONS

  -a --cache - this will make the script output cache_hit ratio perfdata
  -b --bin <varnishstat> - to specify a different location of the default
                           varnishstat binary location. Default is
                           '/usr/bin/varnishstat'
  -d --backend <all|success|unhealthy|busy|fail|reuse|toolate|recycle|retry> -
                        specify script to output backend data you can
                        output ratio, total or both
  -h --help - output this message
  -w --warning <number> - specify the warning threshold. Required for cache and
                          backend checks
  -c --critical <number> - specify the critical threshold. Required for cache and
                           backend checks
  -s --stats <varnishstat field> - specify a comma seperated list of all the stats
                           you wish to check Critical and Warning can be specified
                           and all values will be compared to these values.
  -t --technique <lt|gt> - when specifying stats you can also specify what technique
                           you wish to use to compare the values to the thresholds.
                           specify lt for less than and gt for greater than.
                           Default is gt

EXAMPLES
  Check varnish is running
  ./check_varnish.pl

  Check varnish Cache Hit Ratio and warn if ratio is below 0.8
  ./check_varnish.pl -a -w 0.8 -c 0.6

  Check varnish Backends
  ./check_varnish.pl -d all

  Check varnish client requests and drops
  ./check_varnish.pl -s client_drop,client_req
  
 For more information check out [Webagentur sixhop.net](https://www.sixhop.net/webseiten-erstellung/).
