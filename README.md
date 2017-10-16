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

Lattency	Nb. of occurencies (tasks) that have that accuracy
00000 		0000000
00001
...
00013		0000015 --> means that 15 tasks (occurancies) had 13ms as a latency
...

7) $sudo apt-get install gnuplot
	to plot latencies accuracies
	cyclictest turns on different tasks and measures latencies then generates for each launch the value of the latency : for each launch -> a latency
	using gnuplot to plot latency accuracies
8) launch gnuplot
	$gnuplot
	$gnuplot> 
9) We will use the bash file draw_hist.sh to draw on a png file.
NB: the .sh file must be chmoded to 777

EXAMPLE OF USE:
	$./draw_hist.sh title result-file result-name png-file
	$./draw_hist.sh "TEST NON-RTOS WITHOUT LOAD - Round Robin" test_no_load.txt "round_robin" test_non_rtos_no_load.png

10) a png file is generated and it's named 
test_non_rtos_no_load.png

11) charge the CPU and redo the tests
	$dd if=/dev/zero of=/dev/null
	$sudo ./cyclictest --quiet --mlockall --latency=0 --duration=1m --histogram=10000 --policy=rr --priority=99 --nanosleep --system > test_with_load.txt
	$./draw_hist.sh "TEST NON-RTOS FULLY LOADED - Round Robin" test_with_load.txt "round_robin" test_non_rtos_with_load.png

12) Now to give more details -> increase number of points to 100000
use draw_hist_100000pts.sh to draw the second one

