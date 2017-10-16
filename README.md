# TP1_RTOS

TP1 - Notes
--------------

1) install VM with raspbian (vanilla) normal kernel
2) download rt-tests
4) make to compile files
	install libnuma-dev
	$sudo apt-get install libnuma-dev
	$make

goto rt-tests
5) Run CyclicTest
6) $sudo ./cyclictest --quiet --mlockall --latency=0 --duration=1m --histogram=10000 --policy=rr --priority=99 --nanosleep --system > test_no_load.txt

lockall -> interruptions locked
histogram of 10000 pts
policy Round Robin
max priority of 99
results are stored in a txt file to be plotted using gnu_plot

7) $sudo apt-get install gnuplot
	to plot latencies accuracies
	cyclictest turns on different tasks and measures latencies then generates for each launch the value of the latency : for each launch -> a latency
	using gnuplot to plot latency accuracies



