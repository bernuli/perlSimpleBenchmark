perlSimpleBenchmark is a quick way of benchmarking machines that have perl installed.  It is meant for comparisons between machines rather than to act as a dynamometer.  

The benchmark is the elapsed time perl takes to complete a foreach loop of  1,000,000,000 iterations.  This is known as the inner loop.

Because different versions of perl vary in speed executing the foreach loop, we will require version 5.18 of perl.  Although this script should work in most any perl version.

On the first pass, perlSimpleBenchmark times a single instance of the inner loop (0 .. 1000000000) and reports back the elapsed time.  On the second pass it forks 2 instances of the inner loop and measures the time to complete both loops in parallel.  Every following pass it adds 1 instance of the inner foreach loop, getting the elapsed time to complete all in parallel.   The default is 8 passes, which would be 8 threads running simultaneously.  On the 8th pass, you are measuring the time to complete 8 loops in parallel.  You can reduce the number of passes with the -l flag.  For instance, -l 3 would only do 3 passes, with the last pass running 3 loops in parallel. 

While running, status info is sent to STDOUT.

Upon completion of all passes, perlSimpleBenchmark will write results to a CSV file with all inner loop times as well as various other hardware and software info.
